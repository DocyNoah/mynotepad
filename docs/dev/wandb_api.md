---
title: W&B API
layout: default
nav_order:
grand_parent:
parent: Dev
has_children:
permalink:
---


# W&B API
{: .no_toc}

***

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

***

## Run

```python
import wandb
api = wandb.Api()
r = api.run("PROJECT/RUN_ID")
```

***

## Runs

```python
import wandb
api = wandb.Api()
rs = api.runs("PROJECT")
for r in rs:
    ...
```

***

## How to use it

### Change group of one run
```python
import wandb
api = wandb.Api()
r = api.run("PROJECT/RUN_ID")
r.group = "NEW_GROUP"
r.update()
```

### Change group of runs in old group
```python
import wandb
api = wandb.Api()
rs = api.runs("PROJECT", filters={"group": "OLD_GROUP"})
for r in rs:
    r.group = "NEW_GROUP"
    r.update()
```

## References
- <https://github.com/wandb/wandb/issues/753>
- <https://docs.wandb.ai/ref/python/public-api/api#run>
- <https://docs.wandb.ai/ref/python/public-api/api#runs>
- <https://docs.wandb.ai/ref/python/public-api/run>
