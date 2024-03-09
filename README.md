<p align="center">
    <img width="75" height="75" src="https://raw.githubusercontent.com/snehasishlol/spotify-status/main/assets/spotify-status.png">
</p>


# Spotify Status

Expose your currently playing track on Spotify, alongside Spotify profile, recently played tracks and top items, to a public API. You can then use the API to grab the information without having to authenticate any further. This minimizes the pain-in-the-ass to work with Spotify Authorization and thus all you need is your Spotify User ID.


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

Go to https://spotify-status-api.onrender.com/login and login to the API using your Spotify Account.

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













