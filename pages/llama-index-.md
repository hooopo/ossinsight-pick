

# Llama Index

LangChain is flexible abstractions and extensive toolkit enables developers to harness the power of LLMs.

* GitHub: https://github.com/jerryjliu/llama_index
* Twitter: https://twitter.com/llama_index
* OSS Insight: https://ossinsight.io/analyze/jerryjliu/llama_index#overview
* Category: [LLM Tools](https://ossinsight.io/collections/llm-tools)


## Stars History

 **Star History** is the record of stars a GitHub repository has garnered over time. It serves as an indicator of project popularity and community engagement. 

```star_history_llama_index
SELECT t.Month,
    SUM(t.Stars) OVER (ORDER BY t.Month) as CumulativeStars
FROM (SELECT 
        DATE_FORMAT(starred_at, "%Y-%m-01") as Month, 
        COUNT(*) as Stars
     FROM 
        llama_index.starred_repos
     GROUP BY 
        Month) t
ORDER BY 
    t.Month ASC;
```

<LineChart chartAreaHeight=320 data={star_history_llama_index} />

## Stars per Month

**Stars per Month** refers to the count of stars received by a GitHub repository each month. It represents project popularity and community engagement. By tracking stars per month, it's easy to observe which month gained the most attention for a particular project.

```stars_per_month_llama_index
SELECT 
    DATE_FORMAT(starred_at, "%Y-%m-01") AS Month, 
    COUNT(*) AS Stars
FROM 
    llama_index.starred_repos
GROUP BY 
    Month
ORDER BY 
    Month ASC;
```

<BarChart chartAreaHeight=320 data={stars_per_month_llama_index} />

## Stars increased per day in last 7 days

```stars7days_llama_index
SELECT 
    DATE_FORMAT(starred_at, '%Y-%m-%d') AS Day, 
    COUNT(*) AS Stars
FROM 
    llama_index.starred_repos
WHERE 
    starred_at >= CURDATE() - INTERVAL 7 DAY
GROUP BY 
    Day
ORDER BY 
    Day ASC;
```

<BarChart chartAreaHeight=320 data={stars7days_llama_index} />

## Contribution 

**Monthly active contributors**

```contributors_per_month_llama_index
SELECT 
    DATE_FORMAT(created_at, "%Y-%m-01") AS Month, 
    COUNT(distinct author) AS Contributors
FROM llama_index.pull_requests
WHERE 
    merged = 1
GROUP BY 1
ORDER BY 1 ASC;
```

<BarChart data={contributors_per_month_llama_index}
chartAreaHeight=320 >
<ReferenceLine y=20 color=green labelPosition=aboveStart hideValue=true label="Early signals of Product-Community Fit(20-50)"/>
<ReferenceLine y=50 color=yellow labelPosition=aboveStart hideValue=true label="Strong emerging signals of Product-Communit Fit(51-100)" />
<ReferenceLine y=100 color=blue labelPosition=aboveStart hideValue=true label="Great Product-Communit Fit(101-200)" />
<ReferenceLine  y=200 color=red labelPosition=aboveStart hideValue=true label="Scale beyond Product-Communit Fit(200+)" />

</BarChart>

## Pypi package downloads

```downloads_per_day_llama_index

SELECT 
    DATE_FORMAT(date, '%Y-%m-%d') AS Day, 
    sum(downloads) AS Downloads
FROM llama_index.pypi_downloads
GROUP BY date
order by date asc;
```

<LineChart chartAreaHeight=320 data={downloads_per_day_llama_index} />
