# Show

Documentation about endpoints related to shows.

## Get a show

Gets a show. This will only return the name, see endpoint below of information about a show.

```
GET /show/{show_id}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |

Example response:
```jsonc
{
  "id": 398096,
  "name": "Moonshine ",
  "needs_lazy_loading": false,
  "app_version": 0
}
```

## Get show details

Gets information about a show.

```
GET /show/{show_id}/details/{language}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |
| language | integer | yes | The language to return the results in |

## Search a show

Search for a show.

```
GET /show?q={query}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| query | string | yes | The search query |
| seasons_data | boolean | no | Whether to populate the `seasons` property |
| limit | integer | no | The amount of results to return |
| page | integer | no | The current page of search results |

## Get show seasons

Gets all the seasons of a show.

```
GET /show/{show_id}/seasons
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |

Example response:
```jsonc
{
  "id": "367083",
  "seasons": [
    {
      "number": 1,
      "nb_episodes": 12,
      "seen_episodes": 0
    },
    {
      "number": 2,
      "nb_episodes": 12,
      "seen_episodes": 0
    }
  ]
}
```

`seen_episodes` will always be 0 even when authenticated.

## Get show season

Gets episodes of a single season of a show.

```
GET /show/{show_id}/seasons/{season_number}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |
| season_number | integer | yes | The number of the season |
| lang | string | no | The language to return episode names in |

Example response:
```jsonc
// jq .[] | { id, name, number }

{
  "id": "8266777",
  "name": "Alcohol Prohibition",
  "number": 1
}
{
  "id": "8685325",
  "name": "Liquor In a Wagon",
  "number": 2
}
{
  "id": "8685326",
  "name": "Buddha's Birthday",
  "number": 3
}
```

## Get episode

Gets an episode.

```
GET /episode/{episode_id}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| episode_id | integer | yes | The ID of the episode |

Example response:
```jsonc
{
  "id": 8685325,
  "name": "Liquor In a Wagon",
  "season": {
    "id": "398096_S1",
    "number": 1,
    "episode_count": 16
  },
  "number": 2,
  "is_special": false,
  "show": {
    "id": 398096,
    "name": "Moonshine "
  }
}
```

## Get show actors

Gets a list of all actors and their roles for a show.

```
GET /show/{show_id}/actors
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |

Example response:
```jsonc
// jq .[] | { name, role, actor_id }

{
  "name": "Yoo Seung-ho",
  "role": "Nam Young",
  "actor_id": "45636"
}
{
  "name": "Lee Hye-ri",
  "role": "Kang Ro-seo",
  "actor_id": "152157"
}
{
  "name": "Kang Mi-na",
  "role": "Han Ae-jin",
  "actor_id": "102294"
}
```

## Get show images

Gets a list of banners and others images of a show.

```
GET /show/{show_id}/images
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |
| type | string | no | The type of images (poster, banner, fanart) |

## Get episode votes

Gets the votes for an episode such as mood, favorite actor and watched on.

```
GET /show/{show_id}/episode/{episode_id}/social_stats
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |
| episode_id | integer | yes | The ID of the episode |

Example response:
```jsonc
// jq .emotions[] | { id, name, times_felt }

{
  "id": 8,
  "name": "OK",
  "times_felt": 46
}
{
  "id": 1,
  "name": "Good",
  "times_felt": 98
}
{
  "id": 3,
  "name": "Wow",
  "times_felt": 305
}

// jq .watched_on_sources[] | { id, name, count}

{
  "id": 1,
  "name": "Phone",
  "count": 26
}
{
  "id": 2,
  "name": "Tablet",
  "count": 5
}
{
  "id": 3,
  "name": "Computer",
  "count": 36
}
{
  "id": 4,
  "name": "TV",
  "count": 16
}

// jq .cast[] | { actor_id, role, nb_votes}

{
  "actor_id": 152157,
  "role": "Kang Ro-seo",
  "nb_votes": 328
}
{
  "actor_id": 45636,
  "role": "Nam Young",
  "nb_votes": 48
}
{
  "actor_id": 154842,
  "role": "Lee Pyo",
  "nb_votes": 33
}
```