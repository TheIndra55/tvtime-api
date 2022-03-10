# User

Documentation about endpoints related to users.

## Get a user

Gets a user.

```
GET /user/{user_id}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| user_id | integer | yes | The ID of the user |

## Get a user profile

Gets a user profile.

```
GET /user/{user_id}/profile
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| user_id | integer | yes | The ID of the user |
| include_shows | boolean | no | Whether to populate the `shows` property |

## Get a user's badges

Gets badges of a user.

```
GET /user/{user_id}/badges
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| user_id | integer | yes | The ID of the user |

## Get user show progress

Gets the progress of a user for a show.

```
GET /user/{user_id}/show_progress?show_id={show_id}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| user_id | integer | yes | The ID of the user |
| show_id | integer | yes | The id of the show |

## Get user followers

Gets all followers of a user.

```
GET /user/{user_id}/followers
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| user_id | integer | yes | The ID of the user |
| limit | integer | no | The number of results to return |
| page | integer | no | The current page |

## Get user following

Gets all users the user is following.

```
GET /user/{user_id}/following
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| user_id | integer | yes | The ID of the user |
| limit | integer | no | The number of results to return |
| page | integer | no | The current page |

## Get user friends

Gets all user friends.

```
GET /user/{user_id}/friends
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| user_id | integer | yes | The ID of the user |

## Get a user's followed shows

```
GET /user/{user_id}/followed_shows
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| user_id | integer | yes | The ID of the user |
| limit | integer | no | The number of results to return |
| page | integer | no | The current page |
| include_seasons_data | boolean | no | Whether to populate the `seasons` property |
| include_episodes | boolean | no | Whether to populate the `episodes` property, this will include all episodes |

## Watch episode

**This endpoint requires authentication** \
Marks an episode as watched.

```
POST /watched_episodes/episode/{episode_id}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| episode_id | integer | yes | The ID of the episode |
| is_rewatch | boolean | no | Whether this is a rewatch |

## Unwatch episode

**This endpoint requires authentication** \
Marks an episode as not watched

```
DELETE /watched_episodes/episode/{episode_id}
```

Parameters:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| episode_id | integer | yes | The ID of the episode |