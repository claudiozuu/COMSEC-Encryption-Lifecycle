# DAX Measures (Risk Logic)

***Days Until Expiration***
```DAX
Days Until Expiration =
DATEDIFF ( TODAY(), 'Clean Data'[Expire Date], DAY )

Expired Flag =
IF ( [Days Until Expiration] < 0, "Expired", "Active" )


Risk Category =
SWITCH(
TRUE(),
[Days Until Expiration] < 0, "Expired",
[Days Until Expiration] <= 7, "High",
[Days Until Expiration] <= 30, "Medium",
"Low"
)


Keys Expiring ≤ 7 Days =
CALCULATE(
COUNTROWS('Clean Data'),
[Days Until Expiration] <= 7
) 
