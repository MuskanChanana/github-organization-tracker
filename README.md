## GitHub Organization Tracker
---

For calculating score of all members of any github organisation and top contributors of all repositories.

<br/>

### Some features

- [X] GitHub Graph API
- [X] Interchangable organization leaderboard
- [X] Top contributors for organizations
- [X] Repository specific metadata for organizations
- [X] Pluggable caching layer 
- [X] Automatic Scheduled cache update
- [X] Manual cache update
- [X] GitHub Oauth
- [X] Repository specific analysis
- [X] Cache refresh for repo specific analysis

<br/>

### Getting Started

You can use this application easily just by changing the following credentials..

* Redis server url (optional)
* Name of the organization
* Github api key

This project uses `.env`. To configure, simply make a file named *.env* in the root of your project and add the following lines to it.

```
ORGANIZATION=<Name of the organization as specified in GitHub>
REDIS_URL=<your redis url>
GITHUB_CLIENT_ID=<your-id>
GITHUB_CLIENT_SECRET=<your-secret>
TOKEN=<your-github-personal-access-token>
```

<br/>

### Ways to run

*	**Regular mode**: run this if you do not want a caching layer in your application. Will drastically increase response time but save the cost of having a caching service

```
$ ./app
```

<br/>

* **Caching mode**: run this if you want a caching layer in your application. Will drastically decrease response latency.

```
$ ./app --with-cache
```
<br/>

### Clean
Uninstall all requirements that were installed while making this project. 
```
$ make clean
```

<br/>

### Linting
Lint the code according to pep8 heuristics. Good for contributing
```
$ make lint
```

<br/>

### Generate docs
Generate documentation based on comment descriptions on the APIs. This uses `apidoc` and requires `npm`.
```
$ make docs
```
<br/>

### Limitations

* Only 30 repositories can be fetched from the API at one time.
* Only 10 requests can be made to the API per minute.

<br/>

### Mitigation

* Pluggable caching layer
* Manual cache seed
* CRON-ed cache seed

<br/>

### Getting GitHub tokens and secrets

* Go [here](https://github.com/settings/developers) and create a new github app with redirect URL as `<Your base URL>/oauth`. Your base and redirect URL can be localhost also. You'll get a client ID and client secret from here.

* Now go [here](https://github.com/settings/tokens) and create a personal access token with read access to everything. Here youll get your token.

* `Note`: For heroku, the callback URL should be http

Made with :love: by Sheryl
