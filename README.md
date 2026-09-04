# DroppedNeedle for LazyCat

LazyCat LPK v2 packaging for [DroppedNeedle](https://github.com/DroppedNeedle/DroppedNeedle), a music request, discovery, library-management, and download-orchestration application.

## Runtime

- Multi-instance: every LazyCat user receives an independent DroppedNeedle instance.
- The current user's private `DroppedNeedle` document folder is mounted at `/data`; configure `/data/music` as the library root and keep completed slskd/SABnzbd downloads beneath the same mount for efficient moves.
- Configuration, SQLite state, upgrade backups, caches, and plugins remain in instance-isolated `/lzcapp/var` storage.
- The first administrator is created through DroppedNeedle's native `/setup` page. Successful setup or login credentials are captured for later `/login` autofill.
- Browser upload/download entry points use the LazyCat file-picker injection.
- The original healthcheck is preserved with its ten-minute upgrade grace period.

The supplied logo is preserved as a 512×512 PNG.

## Build

```sh
lzc-cli project release -o dist/application.lpk
```

## GitHub Actions

The scheduled workflow follows stable SemVer tags for `droppedneedle/droppedneedle`, creates a versioned GitHub Release asset, and publishes only to the MiaoMiao private store.

Required repository or organization Secrets:

- `APPSTORE_URL`
- `APPSTORE_TOKEN`

Optional Secrets:

- `APP_ID`
- `PRIVATE_STORE_GROUP_CODES`
