# branch-builds
Example for demonstrating branch builds using the repository dispatch event and actions/checkout@v2.

## Usage

* Press [`Use this template`](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template).
* Open your command line interface of choice and run this script. Be sure to replace the following values:
  * `$TOKEN` with a personal access token with `public_repo` or `repo` scope
  * `$OWNER` and `$REPO` with the appropriate values.

```shell
curl -v \
  -H "Accept: application/vnd.github.everest-preview+json" \
  -H "Authorization: token $TOKEN" \
  https://api.github.com/repos/$OWNER/$REPO/dispatches \
  -X POST -d '{"event_type":"trigger", "client_payload": {"branch":"a"}}'
```

* The value of `event_type` can be any non-empty string and does not affect the build output in any way.
* The `client_payload` field expects a JSON object with zero or more key-value pairs. The workflow file that triggers for the `repository_dispatch` event looks for a `branch` to build, so this example request sends a repository dispatch event that "builds" branch `a`.

## Resources

* [GitHub Developer | create a repository dispatch event](https://developer.github.com/v3/repos/#create-a-repository-dispatch-event)
* [GitHub Help | Events that trigger workflows / External Events: `repository_dispatch`](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/events-that-trigger-workflows#external-events-repository_dispatch)
