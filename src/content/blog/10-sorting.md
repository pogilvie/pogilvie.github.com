---
title:  "Gettting the blog articles to sort correctly"
description: "It was putting the oldest articles first"
pubDate:   Aug 08 2023
categories: serverless
---

in pages/blob/index.astro we query the collection and sort it.

```
onst posts = (await getCollection('blog')).sort(
	(a, b) => b.data.pubDate.valueOf() - a.data.pubDate.valueOf()
);
console.log(posts.length);
```

I switched the order of the a and b to fix the sorting problem.


