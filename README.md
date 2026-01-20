# CRTBASH - Certificate Transparency Log Search Tool

A Bash script for querying [crt.sh](https://crt.sh) to discover subdomains and certificates associated with a domain or organization. Useful for reconnaissance during penetration testing and bug bounty hunting.

## Prerequisites

Ensure the following tools are installed on your system:

| Tool | Purpose | Installation (Kali/Debian) |
|------|---------|----------------------------|
| `curl` | HTTP requests | `sudo apt install curl` |
| `jq` | JSON parsing | `sudo apt install jq` |
| `sed` | Text processing | Pre-installed |
| `sort` | Sorting/deduplication | Pre-installed |

### Quick Install (Kali Linux / Debian / Ubuntu)

```bash
sudo apt update && sudo apt install -y curl jq
```

## Installation

```bash
git clone https://github.com/AkashMadanu/crtbash.git
cd crtbash
chmod +x crtbash
```

### Add to PATH (Optional)

Adding to PATH allows you to run `crtbash` from any directory without specifying the full path (e.g., `crtbash -d example.com` instead of `/path/to/crtbash -d example.com`).

**Option 1: System-wide installation (`/usr/local/bin`)**

```bash
sudo cp crtbash /usr/local/bin/crtbash
```

- Requires sudo (root privileges)
- Available to ALL users on the system
- Survives user account changes
- Standard location for manually installed system-wide executables

**Option 2: User-specific installation (`~/.local/bin`)**

```bash
mkdir -p ~/.local/bin
cp crtbash ~/.local/bin/crtbash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

- No sudo required
- Available ONLY to your user account
- Portable with your home directory
- Standard location for user-specific executables

## Usage

```bash
./crtbash [OPTION] [ARGUMENT]
```

### Options

| Option | Description | Example |
|--------|-------------|---------|
| `-h` | Display help menu | `./crtbash -h` |
| `-d` | Search by domain name | `./crtbash -d example.com` |
| `-o` | Search by organization name | `./crtbash -o example+inc` |

### Examples

```bash
# Find all subdomains for a domain
./crtbash -d hackerone.com

# Search by organization name (use + for spaces)
./crtbash -o hackerone+inc

# Save results to a file
./crtbash -d example.com > subdomains.txt
```

## Troubleshooting

**"jq: command not found"**
```bash
sudo apt install jq
```

**"curl: command not found"**
```bash
sudo apt install curl
```

**"Permission denied"**
```bash
chmod +x crtbash
```

## License

This project is open source and available under the MIT License.
