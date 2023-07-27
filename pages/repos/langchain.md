

# Langchain

LangChain is flexible abstractions and extensive toolkit enables developers to harness the power of LLMs.

* GitHub Address: https://github.com/langchain-ai/langchain
* Twitter: https://twitter.com/LangChainAI
* OSS Insight: https://ossinsight.io/analyze/langchain-ai/langchain#overview
* Category: [LLM Tools](https://ossinsight.io/collections/llm-tools)


## Stars History

 **Star History** is the record of stars a GitHub repository has garnered over time. It serves as an indicator of project popularity and community engagement. 

```star_history
SELECT t.Month,
    SUM(t.Stars) OVER (ORDER BY t.Month) as CumulativeStars
FROM (SELECT 
        DATE_FORMAT(starred_at, "%Y-%m-01") as Month, 
        COUNT(*) as Stars
     FROM 
        starred_repos
     GROUP BY 
        Month) t
ORDER BY 
    t.Month ASC;
```

<LineChart chartAreaHeight=320 data={star_history} />

## Stars per Month

**Stars per Month** refers to the count of stars received by a GitHub repository each month. It represents project popularity and community engagement. By tracking stars per month, it's easy to observe which month gained the most attention for a particular project.

```stars_per_month
SELECT 
    DATE_FORMAT(starred_at, "%Y-%m-01") AS Month, 
    COUNT(*) AS Stars
FROM 
    starred_repos
GROUP BY 
    Month
ORDER BY 
    Month ASC;
```

<BarChart chartAreaHeight=320 data={stars_per_month} />

## Stars increased per day in last 7 days

```stars7days
SELECT 
    DATE_FORMAT(starred_at, '%Y-%m-%d') AS Day, 
    COUNT(*) AS Stars
FROM 
    starred_repos
WHERE 
    starred_at >= CURDATE() - INTERVAL 7 DAY
GROUP BY 
    Day
ORDER BY 
    Day ASC;
```

<BarChart chartAreaHeight=320 data={stars7days} />

## Contribution 

**Monthly active contributors**

```contributors_per_month
SELECT 
    DATE_FORMAT(created_at, "%Y-%m-01") AS Month, 
    COUNT(distinct author) AS Contributors
FROM pull_requests
WHERE 
    merged = 1
GROUP BY 1
ORDER BY 1 ASC;
```

<BarChart data={contributors_per_month}
chartAreaHeight=320 >
<ReferenceLine y=20 color=green labelPosition=aboveStart hideValue=true label="Early signals of Product-Community Fit(20-50)"/>
<ReferenceLine y=50 color=yellow labelPosition=aboveStart hideValue=true label="Strong emerging signals of Product-Communit Fit(51-100)" />
<ReferenceLine y=100 color=blue labelPosition=aboveStart hideValue=true label="Great Product-Communit Fit(101-200)" />
<ReferenceLine  y=200 color=red labelPosition=aboveStart hideValue=true label="Scale beyond Product-Communit Fit(200+)" />

</BarChart>

**Avg. monthly contributors**