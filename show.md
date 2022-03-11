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

## Get show season

Get a single season of a show.

```
GET /show/{show_id}/seasons/{season_number}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |
| season_number | integer | yes | The number of the season |
| lang | string | no | yes | The language to return episode names in |

## Get episode

Gets an episode.

```
GET /episode/{episode_id}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| episode_id | integer | yes | The ID of the episode |

## Get show actors

Gets a list of all actors and their roles for a show.

```
GET /show/{show_id}/actors
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| show_id | integer | yes | The ID of the show |

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