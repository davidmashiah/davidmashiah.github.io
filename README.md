# davidmashiah.github.io

This repository exists only to retire the old address.

`davidmashiah.github.io` is a GitHub **user site**, which GitHub serves
only from a repository named exactly `<username>.github.io`. That
repository was renamed to `davidmashiah.com`, which orphaned the site:
it kept serving a build from before the rename and stopped tracking any
branch. That stale copy was still ranking, and still claiming a
canonical it could not satisfy.

So this repo takes the name back and hands the address on.

**`CNAME`** is the real mechanism. With a custom domain set, GitHub
Pages answers `davidmashiah.github.io/*` with a 301 to the same path on
`davidmashiah.com`. That is a genuine redirect and it passes ranking
signals, which is the entire point — the old address is older than the
new one and should hand over its position rather than compete with it.

GitHub will warn that the domain does not resolve to GitHub Pages. That
warning is expected and correct: DNS points at Vercel, which is what
serves the site. GitHub does not need to serve `davidmashiah.com`, it
only needs to redirect away from `davidmashiah.github.io`.

**The HTML files are a fallback.** If Pages refuses to keep the CNAME,
delete it and these take over: canonical plus a zero-delay meta refresh
plus a JS `location.replace`. Weaker than a 301 but still read as a
redirect. `404.html` catches every path that is not listed explicitly.

Nothing here should ever be indexed; every page is `noindex, follow`, so
crawlers drop the URL but still follow the link to the replacement.