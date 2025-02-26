# Darkside

![image](https://github.com/ph4nt0mbyt3/Darkside/assets/137841478/afb2bed5-0cf2-427a-9002-f88ff01eecf0)






This is a C# AV/EDR Killer using Rogue Anti-Malware Driver 3.3. This driver is not present in the loldrivers or Windows blocklist at the time of this writing. The only reason I'm making this public is because the company has already published a fix in version 3.4, and Microsoft will likely block this driver soon.
This driver can be used in Windows 23H2 with HVCI enabled, loldrivers blocklist, or WDAC enabled. HVCI is designed to ensure the integrity of code executed in the kernel, but it cannot protect against all possible vulnerabilities or actions that can be performed through drivers or system interfaces.

# Steps

1) Load and start the driver:

```
sc create TrueSight binPath="c:\path\to\truesight.sys" type= kernel start= demand
sc start TrueSight
```

2) Start Darkside

```
Darkside.exe -p PID
```

# Recommendations

1) Block this driver through WDAC or wait till Microsoft do it (at your own risk)
3) Limit local privileges, audit and prevent privesc attacks.

## Automated Builds with GitHub Actions

This repository is configured with GitHub Actions to automatically build and release the Darkside binary for multiple platforms (Windows, macOS, and Linux) when a new version tag is pushed.

### Build and Release Process

The automated build process includes:

1. Building Darkside for multiple platforms (Windows, macOS, Linux)
2. Packaging the binaries into compressed archives
3. Creating a GitHub release with the binaries attached

### How to Release a New Version

To release a new version:

1. Update your code with the desired changes
2. Push your changes to the main branch
3. Create and push a new tag with a version number:

```bash
git tag v1.0.0
git push origin v1.0.0
```

The GitHub Actions workflow will automatically trigger, build the binaries for all platforms, and create a release with the binaries attached.

### Manual Trigger

You can also manually trigger the build and release process from the "Actions" tab in the GitHub repository.

### Downloaded Binaries

The released binaries can be downloaded directly from the "Releases" section of the GitHub repository. These are ready-to-use executables that don't require additional installation steps.
