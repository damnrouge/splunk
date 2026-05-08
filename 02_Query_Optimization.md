# 02. Query Optimization for Detection Engineering

## Why Query Optimization Matters

Slow queries = delayed detections, high CPU/memory usage on search heads, and poor user experience.

## Core Optimization Principles

1. **Use specific index and sourcetype constraints first**
2. **Filter as early as possible**
3. **Avoid unnecessary field extractions**
4. **Use `tstats` whenever possible**
5. **Limit time range aggressively**

## Best Practices

```spl
# Bad
index=* sourcetype=* "failed login"

# Good
index=security OR index=endpoint sourcetype=win:security OR sourcetype=linux:auth "failed login" OR "Failed password"
```

## Using tstats (Most Important for Detections)

```spl
| tstats count from datamodel=Authentication where Authentication.action="failure" by Authentication.user
```

## Common Bottlenecks
- Using `eval` and `rex` too early
- Using `join` instead of `appendcols` or `map`
- Not using `map` or `multisearch` when appropriate

## Next
→ [03. Data Format Handling](./03_Data_Format_Handling.md)
