# Erlang Google OAuth 2.0 API client to generate API token for Google S2S requests

## Version 2.1.0

### Migrated to `rebar3`
### Updated dependencies and build
### Added suppport from inline configuration from [2600hz/erlang-google-oauth](https://github.com/2600hz/erlang-google-oauth)

## How to compile:

`google_oauth` uses `reba3` as make system. To compile

```
$ rebar3 compile
```

To generate release

```
$ rebar3 release
```

### How to use with rebar:

You can use `google_oauth` as a dependency in your rebar.config:

```
{deps , [
    {google_oauth, ".*", {git, "https://github.com/pankajsoni19/google_oauth.git", {tag, "3.0.0"}}}
]}.
```

### How to run the application fcm-erlang:

`rebar3 release` will create a release under `_build/default/rel/google_oauth` directory.

```
$ cd _build/default/rel/google_oauth
$ bin/google_oauth console
```

### Request Token

```
{ok, Result} = google_oauth:get_access_token({file, "service_account_file_path.json"}, SCOPE)

Result = 
#{
        access_token    => binary()
        expires_in      => integer() :: seconds, :: < 3600
        token_type      => binary() :: <<"Bearer">>
}
```

for push notification

```
google_oauth:get_access_token("service_account_file_path.json", <<"https://www.googleapis.com/auth/firebase.messaging">>)
```
