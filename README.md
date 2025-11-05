# Big Blocklist

A DNS blocklist that combines multiple trusted sources into one list. Updated automatically every day.

## 🚀 Subscribe

**One-Click Subscribe:**

[📥 Subscribe to Big Blocklist](abp:subscribe?location=https://cdn.jsdelivr.net/gh/NinePlusOne/adguard-hostcompiler@main/compiled.txt&title=Big%20Blocklist)

**Manual URL:**
```
https://cdn.jsdelivr.net/gh/NinePlusOne/adguard-hostcompiler@main/compiled.txt
```

Copy the URL above and add it to your adblocker's custom filter lists.

---

## 📋 What's Included

This blocklist combines the following sources:

### Main Sources
- **[1Hosts (Lite)](https://github.com/badmojr/1Hosts)** - Balanced ads and tracking protection
- **[OISD Big](https://oisd.nl)** - Comprehensive domain blocklist

### Hagezi's Protection Lists
- **[Ultimate](https://github.com/hagezi/dns-blocklists)** - Aggressive ad and tracker blocking
- **[Threat Intelligence Feeds](https://github.com/hagezi/dns-blocklists)** - Malware and phishing protection
- **[DynDNS](https://github.com/hagezi/dns-blocklists)** - Blocks dynamic DNS providers used by malware
- **[Hoster](https://github.com/hagezi/dns-blocklists)** - Blocks free hosting services often used for spam
- **[Spam TLDs](https://github.com/hagezi/dns-blocklists)** - Blocks spam-heavy top-level domains
- **[DNS Rebind Protection](https://github.com/hagezi/dns-blocklists)** - Prevents DNS rebinding attacks
- **[Gambling](https://github.com/hagezi/dns-blocklists)** - Blocks gambling sites

### Custom Rules
- **custom-rules.txt** - Manually added blocking rules
- **deny.txt** - Additional domains to block
- **allow.txt** - Whitelist for false positives

---

## 🛠️ For Developers

### How It Works
1. GitHub Actions runs daily at 2 AM UTC
2. Downloads and combines all sources
3. Removes duplicates and validates rules
4. Publishes the updated list to this repository
5. CDN serves the list globally with low latency

### Local Testing
```bash
npm install -g @adguard/hostlist-compiler
hostlist-compiler --config config.json --output compiled.txt
```

### Add Your Own Rules
Edit these files and commit:
- `custom-rules.txt` - Add blocking rules (format: `||example.com^`)
- `allow.txt` - Add exceptions (format: `@@||example.com^`)
- `deny.txt` - Add more domains to block

---

## 📄 License

GPL-3.0 - See [LICENSE](LICENSE) file for details

---

## 🔗 Links

- [AdGuard HostlistCompiler](https://github.com/AdguardTeam/HostlistCompiler)
- [Report Issues](https://github.com/NinePlusOne/adguard-hostcompiler/issues)