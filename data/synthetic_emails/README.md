# Synthetic Email Lab Pack

This lab pack contains 4 complex synthetic `.eml` files for defensive SOC phishing triage practice.

Safety design:
- Synthetic training data only
- Fake domains ending in `.example.invalid`
- Documentation-style IP ranges
- Defanged URLs using `hxxps` and `[.]`
- No live malicious links
- No credential collection
- No malware, macros, or real executables
- Attachments are inert HTML/CSV/ICS/TXT/JSON training placeholders

Use cases:
- PhishTool analysis
- Header analysis
- IOC extraction and defanging
- YARA rule testing
- VirusTotal/Talos/URLScan notes
- Shuffle SOAR automation testing
- Portfolio SOC write-up

Cases:
1. CASE-01 Okta MFA reset lure
2. CASE-02 SharePoint document review lure
3. CASE-03 Payroll direct deposit verification lure
4. CASE-04 Vendor bank change / BEC invoice lure
