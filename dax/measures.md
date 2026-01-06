# DAX Measures (Risk Logic)

***Days Until Expiration***
```DAX
Days Until Expiration =
DATEDIFF ( TODAY(), 'Clean Data'[Expire Date], DAY )
