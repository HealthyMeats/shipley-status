# Shipley Farms system status

> **Frozen since 2026-09-29.** This mirror has not been republished since its only commit,
> `status: 2026-09-29T01:18:11Z`. Every file here, including `status.json`, `status.txt` and
> the board's "operational" banner, describes the store as it was at 2026-09-29 00:37 UTC.
> Treat nothing here as current. The live board is <https://shipleyfarmsbeef.com/status>,
> with machine-readable files at <https://shipleyfarmsbeef.com/files/status.json> and
> <https://shipleyfarmsbeef.com/files/status.txt>.
>
> This repository is not retired: it is still the publishing target for the off-origin
> mirror, and the next republish replaces this whole file, banner included.

The status board for the Shipley Farms online store lives at
**<https://shipleyfarmsbeef.com/status>**.

This repository is its **off-origin mirror**, served at
<https://healthymeats.github.io/shipley-status>. It exists because a status page served by the
application it monitors goes down with it, which is precisely when someone needs to read it.
Measured during a routine deploy on 2026-09-28: the storefront and the board both returned
503 while the board's own JSON still read `operational`.

Everything here is generated output, republished as a single commit each cycle. The mirror
names the main board as its canonical, so it does not compete with it in search results.

## For machines

Read these from the main site, which is canonical:

| File | Contents |
|---|---|
| [`status.json`](https://shipleyfarmsbeef.com/files/status.json) | Current status per component, with 90 day uptime. The canonical resource. |
| [`status.txt`](https://shipleyfarmsbeef.com/files/status.txt) | The same reading in plain text. The first line is a single token. |
| [`status-uptime.json`](https://shipleyfarmsbeef.com/files/status-uptime.json) | Per day, per component check counts across the window. |
| [`status-feed.xml`](https://shipleyfarmsbeef.com/files/status-feed.xml) | Atom feed of incidents, open and resolved. |
| [`status-schema.json`](https://shipleyfarmsbeef.com/files/status-schema.json) | JSON Schema for `status.json`. |
| [`status-llms.txt`](https://shipleyfarmsbeef.com/files/status-llms.txt) | How to consume all of the above. |

```bash
curl -s https://shipleyfarmsbeef.com/files/status.txt | head -1
```

If the main site is unreachable, the same files are here, without the `status-` prefix:
`https://healthymeats.github.io/shipley-status/status.json`, `https://healthymeats.github.io/shipley-status/status.txt`, and so on.

Poll these files rather than scraping the board. Check `stale_after` before believing
anything else: they are static, so a reading that was fresh when it was written keeps being
served unchanged after the probe behind it has stopped.

`id` is stable and `name` is not. Branch on `severity`.

## Also here

[`essentials.html`](https://healthymeats.github.io/shipley-status/essentials.html) carries the farm store hours, address and
phone in a single self-contained file, for when the main site is unreachable.

## Corrections

Something wrong with this data, or a component you wish were covered:
<beef@shipleyfarmsbeef.com>

Measurements are taken by an unauthenticated probe making ordinary GET requests to public
pages. Nothing here is self-reported by the store. A green reading means pages load; it is
not evidence that a card can be charged.
