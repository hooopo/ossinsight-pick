

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

<LineChart data={star_history} />

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

<BarChart data={stars_per_month} />

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

<BarChart data={stars7days} />