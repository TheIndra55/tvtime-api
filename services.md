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