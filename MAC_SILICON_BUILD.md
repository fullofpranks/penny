# Mac Silicon Build Instructions

This document provides instructions for building Pennywise for Mac Silicon (Apple Silicon) and Intel Macs.

## Prerequisites

- Node.js 18+ (recommended: Node.js 20+)
- Yarn package manager
- Xcode Command Line Tools (for native dependencies)

## Building for Mac Silicon

### 1. Install Dependencies

```bash
yarn install
```

### 2. Build Options

#### Build for Mac Silicon only (ARM64)
```bash
yarn build:mac-arm64
```

#### Build for Intel Macs only (x64)
```bash
yarn build:mac --x64
```

#### Build Universal Binary (both Intel and Apple Silicon)
```bash
yarn build:mac-universal
```

#### Build for all Mac architectures
```bash
yarn build:mac
```

### 3. Development

To run the app in development mode:

```bash
yarn start
```

## Architecture Support

- **ARM64 (Apple Silicon)**: M1, M2, M3, M4 Macs
- **x64 (Intel)**: Intel-based Macs
- **Universal**: Single binary that runs on both architectures

## Build Output

The built applications will be available in the `dist` folder:
- `Pennywise-0.7.0-arm64.dmg` - Apple Silicon version
- `Pennywise-0.7.0-x64.dmg` - Intel version
- `Pennywise-0.7.0-universal.dmg` - Universal binary

## Troubleshooting

### Code Signing Issues
If you encounter code signing issues, you can disable it by setting:
```bash
export CSC_IDENTITY_AUTO_DISCOVERY=false
```

### Notarization
Notarization is disabled by default. To enable it, you'll need to:
1. Set up Apple Developer account
2. Configure notarization credentials
3. Update the `notarize` setting in `package.json`

### Native Dependencies
Some native dependencies might need to be rebuilt for Apple Silicon:
```bash
yarn rebuild
```

## Performance Notes

- Apple Silicon builds are optimized for M-series chips
- Universal binaries are larger but provide maximum compatibility
- ARM64 builds typically offer better performance on Apple Silicon Macs
