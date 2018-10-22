- JSONDecodeError:
  - json_str = json.loads(jsonString, strict=False)
  - If strict is false (True is the default), then control characters will be allowed inside strings. Control characters in this context are those with character codes in the 0–31 range, including '\t' (tab), '\n', '\r' and '\0'.

- UnicodeDecodeError: 'utf8' codec can't decode byte
  - str = unicode(str, errors='replace')
  - str = unicode(str, errors='ignore')
