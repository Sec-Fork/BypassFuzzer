# 403fuzzer
Fuzz 403ing endpoints for bypasses

## Follow me on twitter! @intrudir

This tool will check the endpoint with a couple of headers such as `X-Forwarded-For`

It will also apply different payloads typically used in dir traversals, path normalization etc. to each endpoint on the path.
<br> e.g. `/%2e/test/test2` `/test/%2e/test2` `/test;/test2/`

# Usage
```bash
usage: 403fuzzer.py [-h] [-u URL] [-c COOKIES] [-p PROXY] [-hc HC] [-hl HL]

use this script to fuzz endpoints that return a 401/403

optional arguments:
  -h, --help            show this help message and exit
  -u URL, --url URL     Specify the target URL
  -c COOKIES, --cookies COOKIES
                        Specify cookies to use in requests. (e.g., --cookies "cookie1=blah; cookie2=blah")
  -p PROXY, --proxy PROXY
                        Specify a proxy to use for requests (e.g., http://localhost:8080)
  -hc HC                Hide response code from output, single or comma separated
  -hl HL                Hide response length from output, single or comma separated
```
<br>

## Basic examples
```bash
python3 403fuzzer.py -u http://example.com/test1/test2/test3/forbidden.html
```
![image](https://user-images.githubusercontent.com/24526564/90268769-7ec1ae80-de25-11ea-859f-6d49593a0608.png)
<br>

### Specify cookies to use in requests:
Examples:
```bash
--cookies "cookie1=blah"
-c "cookie1=blah; cookie2=blah"
```
<br>

### Specify a proxy to use
Useful if you wanna proxy through Burp
```bash
--proxy http://localhost:8080
```
<br>

### Hide responses
Provide comma delimited lists without spaces.
Examples:
```bash
-hc 403,404,400  # Hide response codes
-hl 638  # Hide response lengths of 638
```
