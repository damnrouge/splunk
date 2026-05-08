# 03. Data Format Handling in Splunk

## Common Data Formats

- JSON
- XML
- CSV
- Syslog
- Windows Event Logs
- CEF

## Best Practices for JSON

```spl
index=network sourcetype=json
| spath path=event.action output=action
| spath path=user.id output=user
```

Use `INDEXED_EXTRACTIONS = json` in props.conf when possible for better performance.

## Auto KV vs Manual Parsing

When to use `| kv` vs manual `rex` / `spath`.

## Next
→ [04. Query Performance Monitoring](./04_Query_Performance_Monitoring.md)