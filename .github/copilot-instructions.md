# OpenSSL Windows Installer Hashes - AI Agent Instructions

This repository maintains a canonical source of cryptographic hashes for Windows OpenSSL installers provided by Shining Light Productions.

## Project Overview

- Purpose: Provide verified cryptographic hashes (MD5, SHA1, SHA256, SHA512) for Windows OpenSSL installers
- Primary file: `win32_openssl_hashes.json` - contains all installer metadata and hashes
- Data source: Official Windows OpenSSL installers from https://slproweb.com/products/Win32OpenSSL.html

## JSON Structure

The `win32_openssl_hashes.json` file follows this schema:

```json
{
  "info": {
    "title": String,
    "description": String,
    "source": String,
    "alt_source": String,
    "website": String
  },
  "files": {
    [filename]: {
      "basever": String,      // Base version (e.g. "3.6.0")
      "subver": String,       // Sub-version (e.g. "w" or "")
      "arch": String,         // Architecture ("INTEL", "ARM", "Universal")
      "bits": Number,         // 32, 64, or -1 for Universal
      "light": Boolean,       // Whether this is a "Light" installer
      "installer": String,    // Installer type ("exe" or "msi")
      "url": String,         // Download URL
      "size": Number,        // File size in bytes
      "md5": String,        // MD5 hash
      "sha1": String,       // SHA1 hash 
      "sha256": String,     // SHA256 hash
      "sha512": String      // SHA512 hash
    }
  }
}
```

## Key Patterns

1. File Naming Convention: 
   - Format: `[Architecture]OpenSSL[-Light]-[Version].[installer]`
   - Examples: 
     - `Win64OpenSSL-3_6_0.exe`
     - `Win32OpenSSL_Light-3_5_4.msi`
     - `Win64ARMOpenSSL-3_4_3.exe`

2. Version Pattern:
   - Major versions: 1.1.1 and 3.x.x
   - Version numbers in filenames use underscores (e.g., `3_6_0`)
   - Legacy 1.1.1 includes sub-versions (e.g., `1_1_1w`)

## Important Considerations

1. JSON Updates:
   - Each file entry requires all hash types (MD5, SHA1, SHA256, SHA512)
   - File sizes must be verified and included
   - URLs should match the Shining Light Productions domain pattern

2. Architecture Support:
   - Win32 (32-bit x86)
   - Win64 (64-bit x86_64)
   - Win64ARM (64-bit ARM)
   - Universal (Combined installer)

3. Installer Variants:
   - Full installers (larger size, complete package)
   - Light installers (minimal installation)
   - Both .exe and .msi formats available

## Resources

- Download Page: https://slproweb.com/products/Win32OpenSSL.html
- Raw JSON URL: https://github.com/slproweb/opensslhashes/raw/master/win32_openssl_hashes.json