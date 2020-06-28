# pam-haskell

Haskell bindings for PAM. This is a fork of [Evgeny Tarasov's package on Hackage](https://hackage.haskell.org/package/pam) with the changes listed below.

##### Implemented Changes:
- `authenticate` function now returns `MonadIO m => m PamRetCode` rather than `IO (Either Int ())`
- `authSuccess :: PamRetCode -> Bool` added which checks if the given `PamRetCode` is `PamSuccess` or not
- `whenSuccess :: MonadIO m => PamRetCode -> m PamRetCode -> m PamRetCode` added, which returns the second argument if the given response code is `PamSuccess`, otherwise it returns the given response code (useful for continuing only if the PAM action succeeded).

##### Planned Changes:
- Document and refactoring the code (started)
- Work out what `checkAccount` does and implement it
- Add ability to give multiple passwords (for 2FA systems) (see [#2](https://github.com/oscar-h64/pam-haskell/issues/2))
- Add functions that do the prompting rather than being given details - useful as if a program using the library is intended to be distributed the number of prompts will not be known (see [#3](https://github.com/oscar-h64/pam-haskell/issues/3))
- Add functions to allow writing PAM modules in Haskell

## Contributing:

See [here](CONTRIBUTING.md) for more information

## Usage:

To authenticate a user `test` using the `system-local-login` PAM configuration:
```haskell
authenticate "system-local-login" "test" "PASSWORD"
```
If authentication was successful then `PamSuccess` will be returned, otherwise `PamCode a`, where `a` represents the reason for the failure.

`pamCodeToMessage`, `pamCodeToCDefine` and `pamCodeDetails` can be used to get further details about the response, and `authSuccess` can be used to check is authentication was successful. See the Haddock documentation for more details on these functions.
