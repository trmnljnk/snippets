

```bash
find . -name "*.flac" -exec sh -c 'xld --profile "AAC Preferred Profile" -o "$(dirname "{}")" "{}"' \;
```
