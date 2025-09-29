```mermaid
graph TD
    A[Start] --> B{File exists?}
    B -->|Yes| D[Process File]
    B -->|No| C[File Not Found]
    C --> E[End]
    D --> E[End]
```
