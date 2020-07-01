# pam

![Haskell CI](https://github.com/oscar-h64/pam-haskell/workflows/Haskell%20CI/badge.svg)
![Hackage](https://img.shields.io/hackage/v/pam.svg)

Haskell bindings for PAM. Note that this does not currently include the required bindings to write PAM modules

## Usage:

To authenticate a user `test` using the `system-local-login` PAM configuration:
```haskell
authenticate "system-local-login" "test" "PASSWORD"
```

To check if a user `test` exists using the `system-auth` PAM configuration:
```haskell
checkAccount "system-auth" "test"
```

If the operation was successful then `PamSuccess` will be returned, otherwise `PamCode a`, where `a` represents the reason for the failure.

`pamCodeToMessage`, `pamCodeToCDefine` and `pamCodeDetails` can be used to get further details about the response, and `isSuccess` can be used to check if the operation was successful. See the Haddock documentation for more details on these functions.

## Documentation:

The documentation is available on [Hackage](https://hackage.haskell.org/package/pam)

## Changes in v0.2.0.0:
- `authenticate` function now returns `MonadIO m => m PamRetCode` rather than `IO (Either Int ())`
- `authSuccess :: PamRetCode -> Bool` added which checks if the given `PamRetCode` is `PamSuccess` or not
- `whenSuccess :: MonadIO m => PamRetCode -> m PamRetCode -> m PamRetCode` added, which returns the second argument if the given response code is `PamSuccess`, otherwise it returns the given response code (useful for continuing only if the PAM action succeeded).
- `pamCodeToMessage`, `pamCodeToCDefine` and `pamCodeDetails` now take a `PamRetCode` rather than an `Int`
- `checkAccount` function has now been implemented

## Planned Changes:
- Document and refactoring the code (started)
- Add ability to give multiple passwords (for 2FA systems) (see [#2](https://github.com/oscar-h64/pam-haskell/issues/2))
- Add functions that do the prompting rather than being given details - useful as if a program using the library is intended to be distributed the number of prompts will not be known (see [#3](https://github.com/oscar-h64/pam-haskell/issues/3))
- Add functions to allow writing PAM modules in Haskell (see [#8](https://github.com/oscar-h64/pam-haskell/issues/8))

## Contributing:

See [here](https://github.com/oscar-h64/pam-haskell/blob/master/CONTRIBUTING.md) for more information
