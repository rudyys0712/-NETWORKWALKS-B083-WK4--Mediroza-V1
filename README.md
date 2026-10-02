# -NETWORKWALKS-B083-WK4--Mediroza-V1
# 🔒 Mediroza Hospital - Penetration Testing Report

![Security Assessment](https://img.shields.io/badge/Security-Critical%20Vulnerabilities%20Found-red)
![Date](https://img.shields.io/badge/Assessment%20Date-October%202026-blue)
![Status](https://img.shields.io/badge/Status-Report%20Submitted-yellow)

## 📋 Executive Summary

**Target:** https://medirozahospital.com  
**Assessment Type:** Web Application Penetration Testing  
**Date:** October 2026  
**Risk Level:** 🔴 **CRITICAL**

This penetration test was conducted on the Mediroza Hospital website to identify security vulnerabilities. The assessment revealed **multiple critical security flaws** including SQL Injection vulnerabilities, exposed sensitive files, and leaked database credentials. Immediate remediation is strongly recommended to prevent data breaches and unauthorized access to patient information.

---

## 🎯 Scope

| Target | URL | Status |
|--------|-----|--------|
| Primary Website | https://medirozahospital.com | Vulnerable |
| Legacy Directory | https://medirozahospital.com/old/ | Exposed |

---

## 🚨 Critical Findings

### 1. SQL Injection Vulnerability
- **Severity:** 🔴 Critical
- **Location:** https://medirozahospital.com
- **Impact:** Database compromise, data exfiltration
- **Status:** Open

### 2. Exposed Legacy Directory
- **Severity:** 🔴 Critical
- **Location:** https://medirozahospital.com/old/
- **Impact:** Access to deprecated files and backups
- **Status:** Open

### 3. Database Backup Exposure
- **Severity:** 🔴 Critical
- **Location:** `/old/*.sql`
- **Impact:** Complete database compromise, patient PII exposure
- **Status:** Open

### 4. PDF Document Vulnerabilities
- **Severity:** 🟠 High
- **Files Found:** 3 PDF documents
- **Impact:** Confidential document access
- **Status:** Passwords Cracked ✅

---

## 🔐 Password Hash Analysis

### Extracted PDF Password Hashes

| # | Hash | Cracked Password | Strength |
|---|------|------------------|----------|
| 1 | `$pdf$2*3*128*4294967292*1*32*3361663365326235643333353531613238303137316238333238373763353339*32*ef16c52ab8efce2c18c79e9d28895b5928bf4e5e4e758a4164004e56fffa0108*32*c431fab9cc5ef7b59c244b61b745f71ac5ba427b1b9102da468e77127f1e69d6` | `123456` | 🔴 Very Weak |
| 2 | `$pdf$2*3*128*4294967292*1*32*3166346338373236356437626464363834663737303265633666363264616463*32*39f4e6b0aedf12344c340ffb39f8905528bf4e5e4e758a4164004e56fffa0108*32*408b37bcf12da873d7f2840f3c1b917a023961ded4c8164d38e46e9655e66775` | `password` | 🔴 Very Weak |
| 3 | `$pdf$2*3*128*4294967292*1*32*3261393066326130336634386337323631306164373264323130316137616538*32*5090fa0a5dba99cb97c9d140cd23119428bf4e5e4e758a4164004e56fffa0108*32*58e03d692cf37b50b0b5eaa189fcbd372260a949c8992ad7b44fd13e2b40c1f8` | `!@#$%^&` | 🟡 Weak |

### Password Analysis
- **Hash Type:** PDF 2.3 (Acrobat) - AES 128-bit encryption
- **Format:** John the Ripper `$pdf$` format
- **Common Patterns:** Dictionary words, sequential characters
- **Recommendation:** Implement strong password policy (min 12 chars, mixed case, symbols, no dictionary words)

---

## ## 🛠️ Tools Used

### Online Tools
| Tool | Purpose | URL |
|------|---------|-----|
| PDF Hash Extractor | Extract hashes from PDF files | https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php |
| Network Walks Password Cracker | Online hash cracking | https://networkwalks.com/password-cracker/ |

### Local Tools (Alternative)
| Tool | Purpose | Version |
|------|---------|---------|
| SQLMap | SQL Injection detection | Latest |
| pdf2john.py | PDF hash extraction (local) | Latest |
| John the Ripper | Password cracking (local) | 1.9.0+ |
| Hashcat | GPU password cracking (local) | v6.0+ |
| Dirb/Dirbuster | Directory enumeration | Latest |
---
