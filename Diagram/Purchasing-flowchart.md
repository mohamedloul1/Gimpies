flowchart TD
    A[Start Application] --> B[Show Login Screen]
    B --> C[Enter Username & Password]
    C --> D{Credentials Valid?}
    D -- No --> E[Show Error Message]
    E --> F[Increase Attempt Count]
    F --> G{Attempts >= 3?}
    G -- Yes --> H[Exit Application]
    G -- No --> C
    D -- Yes --> I[Show Purchaser Menu]
    
    I --> J{Select Action}
    J -- "View Stock" --> K[Display Shoe Inventory] --> I
    J -- "Purchase Shoes" --> L[Select Shoe + Quantity]
    L --> M[Update Inventory] --> I
    J -- "Logout" --> Z[Return to Login Screen]
