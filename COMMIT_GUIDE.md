# Scrapemate Fork - Commit and Push Guide

## Changes Made

### Browser Launch Arguments Support
1. Added `BrowserArgs` and `ReplaceDefaultArgs` to `jsOptions` in `scrapemateapp/config.go`
2. Added `WithBrowserArgs()` and `ReplaceDefaultArgs()` option functions
3. Updated `JSFetcherOptions` struct in `adapters/fetchers/jshttp/jshttp.go`
4. Updated `newBrowser()` function to accept and use custom browser args
5. **Removed `--single-process` from default browser args** (critical Windows fix)

## Commit Messages

### For scrapemate submodule:
```bash
cd backend/submodules/scrapemate

git add .
git commit -m "feat: Add browser launch arguments support and remove --single-process for Windows compatibility

- Add WithBrowserArgs() and ReplaceDefaultArgs() option functions
- Update JSFetcherOptions to support custom browser args
- Remove --single-process from default args (causes Windows crashes)
- Allow custom args to append or replace default browser launch arguments"
```

### Push to fork:
```bash
git push origin main
```

## For Google Maps Scraper Submodule

The scraper now uses the local scrapemate via `go.mod replace` directive:
```go
replace github.com/gosom/scrapemate v0.9.6 => ../scrapemate
```

When committing google-maps-scraper changes:
```bash
cd backend/submodules/google-maps-scraper

git add .
git commit -m "feat: Use local scrapemate fork with browser args support

- Update go.mod to use local scrapemate submodule
- Add Windows detection and browser args configuration
- Enhanced debug logging for browser launch issues"
```

## Best Practices

1. **Always commit scrapemate changes first** before committing google-maps-scraper
2. **Test thoroughly** on Windows before pushing
3. **Update go.mod** in google-maps-scraper if scrapemate version changes
4. **Document any breaking changes** in scrapemate fork

