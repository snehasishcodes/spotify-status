<p align="center">
    <img width="75" height="75" src="https://raw.githubusercontent.com/snehasishlol/spotify-status/main/assets/spotify-status.png">
</p>


# Spotify Status

Expose your currently playing track on Spotify, alongside Spotify profile, recently played tracks and top items, to a public API. You can then use the API to grab the information without having to authenticate any further. This minimizes the pain-in-the-ass to work with Spotify Authorization and thus all you need is your Spotify User ID. (Not open source)


### Base URL
```
https://spotify-status-api.onrender.com
```

Spotify Status API is hosted on [Render.com](https://render.com). The base URL is given above.

---

### Authorization
The API needs you to authorize/login once using your Spotify Account. We will handle the rest of authentication for you!

The complete step-by-step process is given below.

---

## How to Use (Step-by-Step)

### Step 1 - Login to the API

Go to https://spotify-status-api.onrender.com/login and login to the API using your Spotify Account. We handle the rest of authentication, like: periodically refreshing your access token after it has expired and stuff.

It asks for the following permissions:
- Your email address (always kept private)
- Subscription type, country and explicit content filter (always kept private)
- Display name, username, profile picture, followers and public playlists (only display name, username, profile picture is shared)
- Recently played tracks and artists (shared in the `/users/:id/recents` endpoint)
- Currently playing track (shared in the `/users/:id/status` endpoint)
- Top artists and tracks (shared in the `/users/:id/top/:type` endpoint)

We do not ask for any private permissions. You can check the permissions in the authorization page itself.

<p align="center">
    <img src="https://i.imgur.com/JVs3ze3.png" alt="spotify authorization" />
</p>


### Step 2 - Grab your Spotify User ID
You will be automatically redirected to your Spotify User Profile information endpoint, immediately after the authorization/login has been successful.
Grab your Spotify User ID from there. We will use the ID to access other endpoints from now on.

<p align="center">
    <img src="https://i.imgur.com/9ubHh7t_d.webp?maxwidth=760&fidelity=grand" alt="user information" />
</p>


### Step 3 - Just send the GET requests! ez right?
Once you have grabbed your Spotify account user ID, you just need to send the required `GET` requests to our endpoints. 

**E N D P O I N T S**

1. Profile Information
> ```
> GET /users/[USER_ID]
> ```
> 
> Params:
> - `[USER_ID]`: Your Spotify Account User ID. [^](#step-2---grab-your-spotify-user-id)
>
> Response: https://developer.spotify.com/documentation/web-api/reference/get-current-users-profile
> Note: `email`, `country`, `explicit_content`, `product` are not shared.

2. Currently Playing Track
> ```
> GET /users/[USER_ID]/status
> ```
> 
> Params:
> - `[USER_ID]`: Your Spotify Account User ID. [^](#step-2---grab-your-spotify-user-id)
>
> Response: https://developer.spotify.com/documentation/web-api/reference/get-the-users-currently-playing-track

3. Recently Played Tracks
> ```
> GET /users/[USER_ID]/recents
> ```
>
> Params:
> - `[USER_ID]`: Your Spotify Account User ID. [^](#step-2---grab-your-spotify-user-id)
>
> Query:
> - `limit`: (integer) The maximum number of items to return.
> - `after`: (integer) A Unix timestamp in milliseconds. Returns all items after (but not including) this cursor position. If `after` is specified, `before` must not be specified.
> - `before`: (integer) A Unix timestamp in milliseconds. Returns all items before (but not including) this cursor position. If `before` is specified, `after` must not be specified.
> 
> Response: https://developer.spotify.com/documentation/web-api/reference/get-recently-played

4. Top Tracks/Artists
> ```
> GET /users/[USER_ID]/top/[TYPE]
> ```
>
> Params: 
> - `[USER_ID]`: Your Spotify Account User ID. [^](#step-2---grab-your-spotify-user-id)
> - `[TYPE]`: Must be any one of the two values:
>   - `artists`: Get top artists
>   - `tracks`: Get top tracks
>
> Query:
> - `time_range`: (string) Over what time frame the affinities are computed. Valid values: long_term (calculated from several years of data and including all new data as it becomes available), medium_term (approximately last 6 months), short_term (approximately last 4 weeks).
> - `limit`: (integer) The maximum number of items to return.
> - `offset`: (integer) The index of the first item to return. Default: 0 (the first item). Use with limit to get the next set of items.
>
> Response: https://developer.spotify.com/documentation/web-api/reference/get-users-top-artists-and-tracks


---

That's it lol. GGEZ!

### Made with 💗 and 💻 by [@sneh](https://sneh.is-a.dev) - [☕ Ko-fi](https://ko-fi.com/snehasishlol)







