# Change Log:

## v0.2.0.0:
- `authenticate` function now returns `MonadIO m => m PamRetCode` rather than `IO (Either Int ())`
- `authSuccess :: PamRetCode -> Bool` added which checks if the given `PamRetCode` is `PamSuccess` or not
- `whenSuccess :: MonadIO m => PamRetCode -> m PamRetCode -> m PamRetCode` added, which returns the second argument if the given response code is `PamSuccess`, otherwise it returns the given response code (useful for continuing only if the PAM action succeeded).
- `pamCodeToMessage`, `pamCodeToCDefine` and `pamCodeDetails` now take a `PamRetCode` rather than an `Int`
- `checkAccount` function has now been implemented
- Switched to PVP versioning
- Some documentation added

## v0.1:
Initial release
