# CUPS HTTP PDF Backend

This repository provides a CUPS backend named `http-pdf` that forwards print jobs (PDF) to an HTTP(S) endpoint via POST.

> ⚠️ **Notice**: This service was primarily built with GitHub Copilot assistance but includes extensive human adjustments and testing. While tested, there may be edge cases or issues that haven't been identified. **Always test in a non-production environment first** and ensure you have complete backups before running on production systems. There is jank in the code, feel free to PR :)

## URI Format
```
http-pdf://host:port/path?query
http-pdf+ssl://host:port/path?query   # for HTTPS
```

## Install (Manual)
```
sudo install -m 755 backend/http-pdf /usr/lib/cups/backend/http-pdf
sudo chown root:root /usr/lib/cups/backend/http-pdf
```

Then add a printer in CUPS using a device URI like:
```
http-pdf://127.0.0.1:8888/print?printer=Office
```

## Debian Package Build
A Debian package is provided via GitHub Actions. After each commit to `main`, a new versioned package and GitHub Release are created.

To build locally:
```
debuild -us -uc
```
Resulting `.deb` will be in the parent directory.

## License
MIT
