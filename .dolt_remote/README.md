# Dolt Git Remote

This directory contains a [Dolt](https://doltdb.com) database stored as a Git remote.

## Important

**Do not modify the contents of this directory directly.**

The files in `data/` are managed by Dolt and should only be modified through Dolt commands.
Direct modifications may corrupt the database or cause sync conflicts.

## Usage

To clone this database:

```bash
dolt clone git://github.com/YOUR_USER/YOUR_REPO.git --git-ref=dolt-data
```

To add as a remote to an existing Dolt database:

```bash
dolt remote add origin git://github.com/YOUR_USER/YOUR_REPO.git --git-ref=dolt-data
dolt push origin main
```

## Structure

- `data/` - Contains the actual Dolt database files (chunks, manifest, etc.)
- `data/.dolt-git-remote` - Marker file identifying this as a Dolt remote
- `data/.dolt-version` - Dolt format version

## Git Branch

Dolt data is stored on the `dolt-data` branch to keep it separate from your source code.
You can specify a different branch using the `--git-ref` flag.

## Size Limitations

Git remotes work best for small to medium databases:

- **GitHub**: 100MB max file size, 1GB recommended repo size
- **GitLab**: 100MB max file size (varies by plan)
- **Bitbucket**: 100MB max file size

For databases larger than 500MB, consider using:
- [DoltHub](https://dolthub.com) - Purpose-built for Dolt databases
- Cloud storage remotes (aws://, gs://) - Better for large datasets

## Learn More

- [Dolt Documentation](https://docs.dolthub.com)
- [DoltHub](https://dolthub.com)
