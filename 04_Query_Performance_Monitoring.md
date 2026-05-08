# 04. Query Performance Monitoring

## Key Commands to Monitor Performance

```spl
| rest /services/search/jobs
| search title="*your search name*"
```

## Important Fields to Check
- `dispatch.duration`
- `resultCount`
- `scanCount`
- `droppedEvents`

## Using Job Inspector

Best tool for understanding why a query is slow.

## Next
→ [05. Detection Engineering Workflow](./05_Detection_Engineering_Workflow.md)