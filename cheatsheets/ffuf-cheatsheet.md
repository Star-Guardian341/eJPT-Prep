# 💻 FFUF Cheatsheet

`ffuf` (Fuzz Faster U Fool) is a fast web fuzzer used for discovering hidden files, directories, subdomains, and virtual hosts. This cheatsheet provides practical examples and flag usage.

---

## 🔎 Basic Directory/File Fuzzing

```bash
ffuf -u http://TARGET/FUZZ -w /path/to/wordlist.txt
```

## File Extension Discovery
```bash
ffuf -u http://TARGET/FUZZ.php -w /path/to/wordlist.txt -e .php,.html,.bak
```

## Subdomain Enumeration via Host Header

```bash
ffuf -w /path/to/wordlist.txt -u http://TARGET -H "Host: FUZZ.domain.com"
```

## Filtering Unwanted Results

```bash
ffuf -u http://TARGET/FUZZ -w /wordlist.txt -fs 4242
```
-  -fs – Filter by response size (e.g., filter all responses that return 4242 bytes)
-  -fc – Filter by status code (e.g., -fc 404)
-  -mc – Match only specific status codes (e.g., -mc 200,403)

## Output Options

```bash
ffuf -u http://TARGET/FUZZ -w /wordlist.txt -o results.json -of json
```
-  -o – Output file path
-  -of – Output format (json, csv, html)

## URL Parameter Fuzzing

```bash
ffuf -u "http://TARGET/page.php?param=FUZZ" -w /wordlist.txt
```

