---
type: example
summary: Return JSON directly from a Worker script, useful for building APIs and
  middleware.
demo: https://returning-json.workers-sites-examples.workers.dev
tags:
  - JSON
  - Originless
pcx_content_type: configuration
title: Return JSON
weight: 2
layout: example
---


{{<tabs labels="js/esm | js/sw">}}
{{<tab label="js/esm" default="true">}}

```js
export default {
	async fetch(request) {

		const data = {
			hello: 'world',
		};

		const json = JSON.stringify(data, null, 2);

		return new Response(json, {
			headers: {
				'content-type': 'application/json;charset=UTF-8',
			},
		});
	},
};
```

{{</tab>}}
{{<tab label="js/sw">}}

```js
addEventListener('fetch', event => {
  const data = {
    hello: 'world',
  };

  const json = JSON.stringify(data, null, 2);

  return event.respondWith(
    new Response(json, {
      headers: {
        'content-type': 'application/json;charset=UTF-8',
      },
    })
  );
});
```
{{</tab>}}
{{</tabs>}}
