# Services

Not all data is available from the regular API, you will have to query other services to retrieve this data. Be careful these services have a different base url than the regular API.

## Request

A request to these services is different than from the regular API, you are required to specify two headers.

| Header |  Description |
|--------|--------------|
| x-api-key | A generic API key used by everyone, see below for latest known |
| Authorization | Authorization header with your tvst_access_token, see [Authentication](auth.md) |

The latest API key is `LhqxB7GE9a95beFHqiNC85GHdrX8hNi34H2uQ7QG`.

## WhereDoYouWatch Service

Service with information about where to watch and where people watched a show.

### Base URL

```
https://msapi2.tvtime.com/prod/v1/wdyw
```

### Get episode sources

Get the sources to watch an episode of a show.

```
GET /sources/show/{show_id}/episode/{episode_id}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |
| episode_id | integer | yes | The ID of the episode |

Example response:
```jsonc
// jq .data.sources[] | {app_name, network_id}

{
  "app_name": "Netflix",
  "network_id": "1d33411c-0c2a-46fa-8b6c-8cd0ea6f53ef"
}
{
  "app_name": "jTBC",
  "network_id": "b488d617-df6c-4176-8115-927eb9b155ab"
}
{
  "app_name": "Other",
  "network_id": "01109d08-7513-4ddd-8990-6799d11004b8"
}
{
  "app_name": "Unofficial",
  "network_id": "5dea16e9-fe85-4c85-83a1-b3ba4dc14a30"
}
```


### Get episode votes

Get the number of votes on sources for an episode

```
GET /votes/show/{show_id}/episode/{episode_id}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |
| episode_id | integer | yes | The ID of the episode |

Example response:
```jsonc
// jq .data.episode_votes[] | {name_slug,  network_id, vote_count}

{
  "name_slug": "jtbc-b488d617-df6c-4176-8115-927eb9b155ab",
  "network_id": "b488d617-df6c-4176-8115-927eb9b155ab",
  "vote_count": 0
}
{
  "name_slug": "netflix-9f86c327-bce0-489f-83eb-8a042d2ea6cb",
  "network_id": "9f86c327-bce0-489f-83eb-8a042d2ea6cb",
  "vote_count": 18
}
{
  "name_slug": "netflix-638cad1e-d955-4f03-b975-113dda4c1e10",
  "network_id": "638cad1e-d955-4f03-b975-113dda4c1e10",
  "vote_count": 4
}
{
  "name_slug": "unofficial-5dea16e9-fe85-4c85-83a1-b3ba4dc14a30",
  "network_id": "5dea16e9-fe85-4c85-83a1-b3ba4dc14a30",
  "vote_count": 12
}
{
  "name_slug": "other-01109d08-7513-4ddd-8990-6799d11004b8",
  "network_id": "01109d08-7513-4ddd-8990-6799d11004b8",
  "vote_count": 18
}
```