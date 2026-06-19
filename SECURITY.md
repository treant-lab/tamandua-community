# Security Policy

## Supported Versions

The following versions of Tamandua EDR receive security updates:

| Component | Version | Supported |
| --------- | ------- | --------- |
| tamandua_agent | 1.x.x | Yes |
| tamandua_server | 1.x.x | Yes |
| tamandua_ml | 1.x.x | Yes |
| tamandua_ctl | 1.x.x | Yes |

Only the latest minor release of each major version receives security patches. We recommend always running the most recent version.

## Reporting a Vulnerability

**Please do not report security vulnerabilities through public GitHub issues, discussions, or pull requests.**

Instead, please report security vulnerabilities by emailing:

**security@treant.io**

Please include as much of the following information as possible to help us better understand and resolve the issue:

- **Type of vulnerability** (e.g., buffer overflow, privilege escalation, authentication bypass, injection, etc.)
- **Affected component(s)** (agent, server, ML service, CLI)
- **Full paths of source file(s)** related to the vulnerability
- **Step-by-step instructions** to reproduce the issue
- **Proof-of-concept or exploit code** (if available)
- **Impact assessment** of the vulnerability and potential attack scenarios
- **Any special configuration** required to reproduce the issue
- **Your suggested fix** (if any)

## Response Timeline

We are committed to responding to security reports in a timely manner:

| Action | Target Timeline |
| ------ | --------------- |
| Initial acknowledgment | 48 hours |
| Preliminary assessment | 7 days |
| Status update (if investigation ongoing) | Every 14 days |
| Fix development | Dependent on severity |
| Public disclosure (coordinated) | 90 days from report, or upon fix release |

For critical vulnerabilities affecting production deployments, we will work to develop and release a fix as quickly as possible, typically within 7-14 days.

## Scope

The following components and areas are in scope for security reports:

### In Scope

- **Tamandua Agent** (`tamandua_agent`)
  - Privilege escalation vulnerabilities
  - Authentication/authorization bypasses
  - Remote code execution
  - Memory safety issues (buffer overflows, use-after-free)
  - Cryptographic weaknesses
  - Insecure defaults or configurations

- **Tamandua Server** (`tamandua_server`)
  - Authentication and session management flaws
  - Authorization bypasses
  - SQL injection, command injection, or other injection attacks
  - Cross-site scripting (XSS) and cross-site request forgery (CSRF)
  - Insecure direct object references
  - Server-side request forgery (SSRF)
  - Information disclosure

- **Tamandua ML Service** (`tamandua_ml`)
  - Model poisoning or adversarial attacks
  - API authentication bypasses
  - Injection vulnerabilities
  - Insecure deserialization

- **Tamandua CLI** (`tamandua_ctl`)
  - Command injection
  - Credential exposure
  - Privilege escalation

- **Infrastructure**
  - WebSocket protocol vulnerabilities
  - mTLS implementation weaknesses
  - JWT handling issues
  - Certificate validation bypasses

## Out of Scope

The following are explicitly out of scope:

- **Social engineering attacks** against Tamandua employees, contractors, or users
- **Physical attacks** against Tamandua infrastructure or user systems
- **Denial of Service (DoS/DDoS)** attacks
- **Spam or phishing** attacks
- **Vulnerabilities in third-party dependencies** (report these to the respective maintainers, but you may inform us so we can update)
- **Vulnerabilities requiring unlikely user interaction** (e.g., requiring a user to install malware)
- **Clickjacking** on pages with no sensitive actions
- **Missing security headers** that do not lead to direct exploitation
- **Software version disclosure** without demonstrable impact
- **Issues in unsupported versions**
- **Vulnerabilities in test/development environments** that do not affect production configurations

## Safe Harbor

We consider security research and vulnerability disclosure activities conducted consistent with this policy to be:

- Authorized concerning any applicable anti-hacking laws
- Authorized concerning any relevant anti-circumvention laws
- Exempt from restrictions in our Terms of Service that would interfere with conducting security research

We will not pursue civil action or initiate a complaint to law enforcement for accidental, good-faith violations of this policy. We consider activities conducted consistent with this policy to constitute "authorized" conduct.

You are expected, as always, to comply with all applicable laws. If legal action is initiated by a third party against you and you have complied with this policy, we will take steps to make it known that your actions were conducted in compliance with this policy.

If at any time you have concerns or are uncertain whether your security research is consistent with this policy, please submit a report through the email address above before going any further.

## Recognition

We believe in recognizing the contributions of security researchers who help keep Tamandua and its users safe.

With your permission, we will:

- Publicly acknowledge your contribution in our security advisories
- Add your name (or alias) to our Security Hall of Fame
- Provide a letter of acknowledgment upon request

We do not currently offer monetary bounties, but we are deeply grateful for responsible disclosure and may consider rewards on a case-by-case basis for exceptional findings.

## PGP Key

For sensitive communications, you may encrypt your message using our PGP public key:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----

[PGP KEY PLACEHOLDER - Contact security@treant.io for current key]

-----END PGP PUBLIC KEY BLOCK-----
```

Alternatively, request our current PGP key by emailing security@treant.io with the subject line "PGP Key Request".

## Security Updates

Security advisories will be published through:

- GitHub Security Advisories
- Release notes for affected versions
- Direct notification to enterprise customers

## Hardened Production Builds

For maximum security in production environments, we provide hardened agent binaries built with additional security features.

### Security Features in Hardened Builds

The `release-hardened` profile includes:

**Memory Protection:**
- **ASLR (Address Space Layout Randomization)** - Randomizes memory addresses to prevent exploitation
- **DEP/NX (Data Execution Prevention)** - Prevents code execution from data segments
- **Stack Canaries** - Detects stack buffer overflows (nightly builds)
- **Integer Overflow Checks** - Runtime detection of arithmetic overflows

**Windows-Specific:**
- **High-Entropy ASLR (HEVA)** - 64-bit address space randomization
- **Control Flow Guard (CFG)** - Validates indirect call targets
- **Safe SEH** - Structured exception handling protection

**Linux-Specific:**
- **Full RELRO** - Read-only relocations with immediate binding
- **Non-executable Stack** - Stack memory marked as non-executable
- **Position Independent Executable (PIE)** - Enables full ASLR

**macOS-Specific:**
- **PIE (Position Independent Executable)** - Full address randomization
- **Dead Code Stripping** - Removes unused code to reduce attack surface
- **Hardened Runtime** - Additional runtime protections

**Build Optimizations:**
- **Panic Abort** - No unwinding on panic (smaller attack surface)
- **Full LTO** - Link-time optimization and code obfuscation
- **Symbol Stripping** - Removes debugging symbols (anti-reverse engineering)
- **Size Optimization** - Smaller binaries = reduced attack surface

### Building Hardened Binaries Locally

#### Windows

```powershell
cd apps/tamandua_agent
.\scripts\build-hardened.ps1

# With specific features
.\scripts\build-hardened.ps1 -Features "yara,ml,compression"

# Clean build
.\scripts\build-hardened.ps1 -Clean
```

#### Linux/macOS

```bash
cd apps/tamandua_agent
./scripts/build-hardened.sh

# With specific features
./scripts/build-hardened.sh x86_64-unknown-linux-gnu "yara,ml,compression"

# Clean build
./scripts/build-hardened.sh x86_64-unknown-linux-gnu "" clean
```

#### Manual Build

```bash
# Set platform-specific hardening flags
export RUSTFLAGS="-C relocation-model=pic -C link-arg=-Wl,-z,relro -C link-arg=-Wl,-z,now"

# Build with hardened profile
cargo build --profile release-hardened --features "yara,ml,compression"
```

### Verifying Security Features

#### Linux

```bash
# Install checksec
sudo apt-get install pax-utils

# Verify hardening
checksec --file=target/x86_64-unknown-linux-gnu/release-hardened/tamandua-agent
```

Expected output:
```
RELRO           STACK CANARY      NX            PIE             RPATH      RUNPATH
Full RELRO      Canary found      NX enabled    PIE enabled     No RPATH   No RUNPATH
```

#### Windows

```powershell
# Requires Visual Studio Build Tools
dumpbin /headers target\x86_64-pc-windows-msvc\release-hardened\tamandua-agent.exe | Select-String -Pattern "(Dynamic base|NX compatible|Guard|High Entropy)"
```

Expected output should show:
- `Dynamic base` - ASLR enabled
- `NX compatible` - DEP enabled
- `Guard` - Control Flow Guard enabled
- `High Entropy` - High-entropy ASLR enabled

#### macOS

```bash
# Check PIE and hardened runtime
otool -hv target/x86_64-apple-darwin/release-hardened/tamandua-agent | grep PIE
otool -I target/x86_64-apple-darwin/release-hardened/tamandua-agent | grep stack_chk
```

### CI/CD Hardened Builds

Official releases include hardened binaries for production deployments:

- `tamandua-agent-linux-x86_64-hardened.tar.gz`
- `tamandua-agent-windows-x86_64-hardened.exe.zip`
- `tamandua-agent-macos-x86_64-hardened.tar.gz`

These binaries include full security features and are recommended for production use.

### Deployment Recommendations

For production environments:

1. **Use hardened binaries** from official releases or build with `release-hardened` profile
2. **Verify checksums** (SHA256) before deployment
3. **Enable code signing** for additional trust verification
4. **Run with least privilege** - agent should run as a dedicated service account
5. **Enable OS-level security features** - AppArmor/SELinux (Linux), Gatekeeper (macOS), WDAC (Windows)
6. **Monitor for tampering** - use file integrity monitoring on agent binaries
7. **Keep updated** - apply security patches promptly

### Performance Impact

Hardened builds may have minimal performance overhead:

- **Startup time:** +5-10ms (ASLR, CFG initialization)
- **Runtime overhead:** <1% (overflow checks, stack canaries)
- **Binary size:** -10-15% (symbol stripping, size optimization)

The security benefits far outweigh the negligible performance impact for production deployments.

## Additional Resources

- [GitHub Security Advisories](https://github.com/treant-lab/tamandua-community/security/advisories)
- [Tamandua Documentation](https://docs.treant.io/tamandua)
- [Build Scripts](apps/tamandua_agent/scripts/)
- [Cargo Profile Documentation](apps/tamandua_agent/Cargo.toml)

---

Thank you for helping keep Tamandua EDR and our users safe.
