# Merge requests

## List merge requests

Get all merge requests for this project.
The `state` parameter can be used to get only merge requests with a given state (`opened`, `closed`, or `merged`) or all of them (`all`).
The pagination parameters `page` and `per_page` can be used to restrict the list of merge requests.

```
GET /projects/:id/merge_requests
GET /projects/:id/merge_requests?state=opened
GET /projects/:id/merge_requests?state=all
GET /projects/:id/merge_requests?iid=42
```

Parameters:

- `id` (required) - The ID of a project
- `iid` (optional) - Return the request having the given `iid`
- `state` (optional) - Return `all` requests or just those that are `merged`, `opened` or `closed`
- `order_by` (optional) - Return requests ordered by `created_at` or `updated_at` fields. Default is `created_at`
- `sort` (optional) - Return requests sorted in `asc` or `desc` order. Default is `desc`

```json
[
  {
    "id": 1,
    "iid": 1,
    "target_branch": "master",
    "source_branch": "test1",
    "project_id": 3,
    "title": "test1",
    "state": "opened",
    "upvotes": 0,
    "downvotes": 0,
    "author": {
      "id": 1,
      "username": "admin",
      "email": "admin@example.com",
      "name": "Administrator",
      "state": "active",
      "created_at": "2012-04-29T08:46:00Z"
    },
    "assignee": {
      "id": 1,
      "username": "admin",
      "email": "admin@example.com",
      "name": "Administrator",
      "state": "active",
      "created_at": "2012-04-29T08:46:00Z"
    },
    "source_project_id": "2",
    "target_project_id": "3",
    "labels": [ ],
    "description":"fixed login page css paddings",
    "work_in_progress": false,
    "milestone": {
      "id": 5,
      "iid": 1,
      "project_id": 3,
      "title": "v2.0",
      "description": "Assumenda aut placeat expedita exercitationem labore sunt enim earum.",
      "state": "closed",
      "created_at": "2015-02-02T19:49:26.013Z",
      "updated_at": "2015-02-02T19:49:26.013Z",
      "due_date": null
    },
    "merge_when_build_succeeds": true,
    "merge_status": "can_be_merged",
    "subscribed" : false,
    "user_notes_count": 1
  }
]
```

## Get single MR

Shows information about a single merge request.

```
GET /projects/:id/merge_requests/:merge_request_id
```

Parameters:

- `id` (required) - The ID of a project
- `merge_request_id` (required) - The ID of MR

```json
{
  "id": 1,
  "iid": 1,
  "target_branch": "master",
  "source_branch": "test1",
  "project_id": 3,
  "title": "test1",
  "state": "merged",
  "upvotes": 0,
  "downvotes": 0,
  "author": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "assignee": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "source_project_id": "2",
  "target_project_id": "3",
  "labels": [ ],
  "description":"fixed login page css paddings",
  "work_in_progress": false,
  "milestone": {
    "id": 5,
    "iid": 1,
    "project_id": 3,
    "title": "v2.0",
    "description": "Assumenda aut placeat expedita exercitationem labore sunt enim earum.",
    "state": "closed",
    "created_at": "2015-02-02T19:49:26.013Z",
    "updated_at": "2015-02-02T19:49:26.013Z",
    "due_date": null
  },
  "merge_when_build_succeeds": true,
  "merge_status": "can_be_merged",
  "subscribed" : true,
  "user_notes_count": 1
}
```

## Get single MR commits

Get a list of merge request commits.

```
GET /projects/:id/merge_requests/:merge_request_id/commits
```

Parameters:

- `id` (required) - The ID of a project
- `merge_request_id` (required) - The ID of MR


```json
[
  {
    "id": "ed899a2f4b50b4370feeea94676502b42383c746",
    "short_id": "ed899a2f4b5",
    "title": "Replace sanitize with escape once",
    "author_name": "Dmitriy Zaporozhets",
    "author_email": "dzaporozhets@sphereconsultinginc.com",
    "created_at": "2012-09-20T11:50:22+03:00",
    "message": "Replace sanitize with escape once"
  },
  {
    "id": "6104942438c14ec7bd21c6cd5bd995272b3faff6",
    "short_id": "6104942438c",
    "title": "Sanitize for network graph",
    "author_name": "randx",
    "author_email": "dmitriy.zaporozhets@gmail.com",
    "created_at": "2012-09-20T09:06:12+03:00",
    "message": "Sanitize for network graph"
  }
]
```

## Get single MR changes

Shows information about the merge request including its files and changes.

```
GET /projects/:id/merge_requests/:merge_request_id/changes
```

Parameters:

- `id` (required) - The ID of a project
- `merge_request_id` (required) - The ID of MR

```json
{
  "id": 21,
  "iid": 1,
  "project_id": 4,
  "title": "Blanditiis beatae suscipit hic assumenda et molestias nisi asperiores repellat et.",
  "state": "reopened",
  "created_at": "2015-02-02T19:49:39.159Z",
  "updated_at": "2015-02-02T20:08:49.959Z",
  "target_branch": "secret_token",
  "source_branch": "version-1-9",
  "upvotes": 0,
  "downvotes": 0,
  "author": {
    "name": "Chad Hamill",
    "username": "jarrett",
    "id": 5,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/b95567800f828948baf5f4160ebb2473?s=40&d=identicon"
  },
  "assignee": {
    "name": "Administrator",
    "username": "root",
    "id": 1,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/e64c7d89f26bd1972efa854d13d7dd61?s=40&d=identicon"
  },
  "source_project_id": 4,
  "target_project_id": 4,
  "labels": [ ],
  "description": "Qui voluptatibus placeat ipsa alias quasi. Deleniti rem ut sint. Optio velit qui distinctio.",
  "work_in_progress": false,
  "milestone": {
    "id": 5,
    "iid": 1,
    "project_id": 4,
    "title": "v2.0",
    "description": "Assumenda aut placeat expedita exercitationem labore sunt enim earum.",
    "state": "closed",
    "created_at": "2015-02-02T19:49:26.013Z",
    "updated_at": "2015-02-02T19:49:26.013Z",
    "due_date": null
  },
  "merge_when_build_succeeds": true,
  "merge_status": "can_be_merged",
  "subscribed" : true,
  "user_notes_count": 1,
  "changes": [
    {
    "old_path": "VERSION",
    "new_path": "VERSION",
    "a_mode": "100644",
    "b_mode": "100644",
    "diff": "--- a/VERSION\ +++ b/VERSION\ @@ -1 +1 @@\ -1.9.7\ +1.9.8",
    "new_file": false,
    "renamed_file": false,
    "deleted_file": false
    }
  ]
}
```

## Create MR

Creates a new merge request.
```
POST /projects/:id/merge_requests
```

Parameters:

- `id` (required)                - The ID of a project
- `source_branch` (required)     - The source branch
- `target_branch` (required)     - The target branch
- `assignee_id` (optional)       - Assignee user ID
- `title` (required)             - Title of MR
- `description` (optional)       - Description of MR
- `target_project_id` (optional) - The target project (numeric id)
- `labels` (optional)            - Labels for MR as a comma-separated list
- `milestone_id` (optional)      - Milestone ID

```json
{
  "id": 1,
  "target_branch": "master",
  "source_branch": "test1",
  "project_id": 3,
  "title": "test1",
  "state": "opened",
  "upvotes": 0,
  "downvotes": 0,
  "author": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "assignee": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "source_project_id": 4,
  "target_project_id": 4,
  "labels": [ ],
  "description":"fixed login page css paddings",
  "work_in_progress": false,
  "milestone": {
    "id": 5,
    "iid": 1,
    "project_id": 4,
    "title": "v2.0",
    "description": "Assumenda aut placeat expedita exercitationem labore sunt enim earum.",
    "state": "closed",
    "created_at": "2015-02-02T19:49:26.013Z",
    "updated_at": "2015-02-02T19:49:26.013Z",
    "due_date": null
  },
  "merge_when_build_succeeds": true,
  "merge_status": "can_be_merged",
  "subscribed" : true,
  "user_notes_count": 0
}
```

If the operation is successful, 200 and the newly created merge request is returned.
If an error occurs, an error number and a message explaining the reason is returned.

## Update MR

Updates an existing merge request. You can change the target branch, title, or even close the MR.

```
PUT /projects/:id/merge_requests/:merge_request_id
```

Parameters:

- `id` (required)               - The ID of a project
- `merge_request_id` (required) - ID of MR
- `target_branch`               - The target branch
- `assignee_id`                 - Assignee user ID
- `title`                       - Title of MR
- `description`                 - Description of MR
- `state_event`                 - New state (close|reopen|merge)
- `labels` (optional)           - Labels for MR as a comma-separated list
- `milestone_id` (optional)     - Milestone ID

```json
{
  "id": 1,
  "target_branch": "master",
  "project_id": 3,
  "title": "test1",
  "state": "opened",
  "upvotes": 0,
  "downvotes": 0,
  "author": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "assignee": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "source_project_id": 4,
  "target_project_id": 4,
  "labels": [ ],
  "description": "description1",
  "work_in_progress": false,
  "milestone": {
    "id": 5,
    "iid": 1,
    "project_id": 4,
    "title": "v2.0",
    "description": "Assumenda aut placeat expedita exercitationem labore sunt enim earum.",
    "state": "closed",
    "created_at": "2015-02-02T19:49:26.013Z",
    "updated_at": "2015-02-02T19:49:26.013Z",
    "due_date": null
  },
  "merge_when_build_succeeds": true,
  "merge_status": "can_be_merged",
  "subscribed" : true,
  "user_notes_count": 1
}
```

If the operation is successful, 200 and the updated merge request is returned.
If an error occurs, an error number and a message explaining the reason is returned.

## Delete a merge request

Only for admins and project owners. Soft deletes the merge request in question.
If the operation is successful, a status code `200` is returned. In case you cannot
destroy this merge request, or it is not present, code `404` is given.

```
DELETE /projects/:id/merge_requests/:merge_request_id
```

| Attribute | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| `id`            | integer | yes | The ID of a project |
| `merge_request_id` | integer | yes | The ID of a project's merge request |

```bash
curl -X DELETE -H "PRIVATE-TOKEN: 9koXpg98eAheJpvBs5tK" https://gitlab.example.com/api/v3/projects/4/merge_request/85
```

## Accept MR

Merge changes submitted with MR using this API.

If the merge succeeds you'll get a `200 OK`.

If it has some conflicts and can not be merged - you'll get a 405 and the error message 'Branch cannot be merged'

If merge request is already merged or closed - you'll get a 406 and the error message 'Method Not Allowed'

If the `sha` parameter is passed and does not match the HEAD of the source - you'll get a 409 and the error message 'SHA does not match HEAD of source branch'

If you don't have permissions to accept this merge request - you'll get a 401

```
PUT /projects/:id/merge_requests/:merge_request_id/merge
```

Parameters:

- `id` (required)                           - The ID of a project
- `merge_request_id` (required)             - ID of MR
- `merge_commit_message` (optional)         - Custom merge commit message
- `should_remove_source_branch` (optional)  - if `true` removes the source branch
- `merged_when_build_succeeds` (optional)   - if `true` the MR is merged when the build succeeds
- `sha` (optional)                          - if present, then this SHA must match the HEAD of the source branch, otherwise the merge will fail

```json
{
  "id": 1,
  "target_branch": "master",
  "source_branch": "test1",
  "project_id": 3,
  "title": "test1",
  "state": "merged",
  "upvotes": 0,
  "downvotes": 0,
  "author": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "assignee": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "source_project_id": 4,
  "target_project_id": 4,
  "labels": [ ],
  "description":"fixed login page css paddings",
  "work_in_progress": false,
  "milestone": {
    "id": 5,
    "iid": 1,
    "project_id": 4,
    "title": "v2.0",
    "description": "Assumenda aut placeat expedita exercitationem labore sunt enim earum.",
    "state": "closed",
    "created_at": "2015-02-02T19:49:26.013Z",
    "updated_at": "2015-02-02T19:49:26.013Z",
    "due_date": null
  },
  "merge_when_build_succeeds": true,
  "merge_status": "can_be_merged",
  "subscribed" : true,
  "user_notes_count": 1
}
```

## Cancel Merge When Build Succeeds

If successful you'll get `200 OK`.

If you don't have permissions to accept this merge request - you'll get a 401

If the merge request is already merged or closed - you get 405 and error message 'Method Not Allowed'

In case the merge request is not set to be merged when the build succeeds, you'll also get a 406 error.
```
PUT /projects/:id/merge_requests/:merge_request_id/cancel_merge_when_build_succeeds
```
Parameters:

- `id` (required)                           - The ID of a project
- `merge_request_id` (required)             - ID of MR

```json
{
  "id": 1,
  "target_branch": "master",
  "source_branch": "test1",
  "project_id": 3,
  "title": "test1",
  "state": "opened",
  "upvotes": 0,
  "downvotes": 0,
  "author": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "assignee": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "name": "Administrator",
    "state": "active",
    "created_at": "2012-04-29T08:46:00Z"
  },
  "source_project_id": 4,
  "target_project_id": 4,
  "labels": [ ],
  "description":"fixed login page css paddings",
  "work_in_progress": false,
  "milestone": {
    "id": 5,
    "iid": 1,
    "project_id": 4,
    "title": "v2.0",
    "description": "Assumenda aut placeat expedita exercitationem labore sunt enim earum.",
    "state": "closed",
    "created_at": "2015-02-02T19:49:26.013Z",
    "updated_at": "2015-02-02T19:49:26.013Z",
    "due_date": null
  },
  "merge_when_build_succeeds": true,
  "merge_status": "can_be_merged",
  "subscribed" : true,
  "user_notes_count": 1
}
```

## Comments on merge requests

Comments are done via the [notes](notes.md) resource.

## List issues that will close on merge

Get all the issues that would be closed by merging the provided merge request.

```
GET /projects/:id/merge_requests/:merge_request_id/closes_issues
```

| Attribute | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| `id`      | integer | yes   | The ID of a project |
| `merge_request_id` | integer | yes   | The ID of the merge request |

```bash
curl -H "PRIVATE-TOKEN: 9koXpg98eAheJpvBs5tK" https://gitlab.example.com/api/v3/projects/76/merge_requests/1/closes_issues
```

Example response:

```json
[
   {
      "state" : "opened",
      "description" : "Ratione dolores corrupti mollitia soluta quia.",
      "author" : {
         "state" : "active",
         "id" : 18,
         "web_url" : "https://gitlab.example.com/u/eileen.lowe",
         "name" : "Alexandra Bashirian",
         "avatar_url" : null,
         "username" : "eileen.lowe"
      },
      "milestone" : {
         "project_id" : 1,
         "description" : "Ducimus nam enim ex consequatur cumque ratione.",
         "state" : "closed",
         "due_date" : null,
         "iid" : 2,
         "created_at" : "2016-01-04T15:31:39.996Z",
         "title" : "v4.0",
         "id" : 17,
         "updated_at" : "2016-01-04T15:31:39.996Z"
      },
      "project_id" : 1,
      "assignee" : {
         "state" : "active",
         "id" : 1,
         "name" : "Administrator",
         "web_url" : "https://gitlab.example.com/u/root",
         "avatar_url" : null,
         "username" : "root"
      },
      "updated_at" : "2016-01-04T15:31:51.081Z",
      "id" : 76,
      "title" : "Consequatur vero maxime deserunt laboriosam est voluptas dolorem.",
      "created_at" : "2016-01-04T15:31:51.081Z",
      "iid" : 6,
      "labels" : [],
      "user_notes_count": 1
   },
]
```

## Subscribe to a merge request

Subscribes the authenticated user to a merge request to receive notification. If
the operation is successful, status code `201` together with the updated merge
request is returned. If the user is already subscribed to the merge request, the
status code `304` is returned. If the project or merge request is not found,
status code `404` is returned.

```
POST /projects/:id/merge_requests/:merge_request_id/subscription
```

| Attribute | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| `id` | integer | yes | The ID of a project |
| `merge_request_id` | integer | yes   | The ID of the merge request |

```bash
curl -X POST -H "PRIVATE-TOKEN: 9koXpg98eAheJpvBs5tK" https://gitlab.example.com/api/v3/projects/5/merge_requests/17/subscription
```

Example response:

```json
{
  "id": 17,
  "iid": 1,
  "project_id": 5,
  "title": "Et et sequi est impedit nulla ut rem et voluptatem.",
  "description": "Consequatur velit eos rerum optio autem. Quia id officia quaerat dolorum optio. Illo laudantium aut ipsum dolorem.",
  "state": "opened",
  "created_at": "2016-04-05T21:42:23.233Z",
  "updated_at": "2016-04-05T22:11:52.900Z",
  "target_branch": "ui-dev-kit",
  "source_branch": "version-1-9",
  "upvotes": 0,
  "downvotes": 0,
  "author": {
    "name": "Eileen Skiles",
    "username": "leila",
    "id": 19,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/39ce4a2822cc896933ffbd68c1470e55?s=80&d=identicon",
    "web_url": "https://gitlab.example.com/u/leila"
  },
  "assignee": {
    "name": "Celine Wehner",
    "username": "carli",
    "id": 16,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/f4cd5605b769dd2ce405a27c6e6f2684?s=80&d=identicon",
    "web_url": "https://gitlab.example.com/u/carli"
  },
  "source_project_id": 5,
  "target_project_id": 5,
  "labels": [],
  "work_in_progress": false,
  "milestone": {
    "id": 7,
    "iid": 1,
    "project_id": 5,
    "title": "v2.0",
    "description": "Corrupti eveniet et velit occaecati dolorem est rerum aut.",
    "state": "closed",
    "created_at": "2016-04-05T21:41:40.905Z",
    "updated_at": "2016-04-05T21:41:40.905Z",
    "due_date": null
  },
  "merge_when_build_succeeds": false,
  "merge_status": "cannot_be_merged",
  "subscribed": true
}
```

## Unsubscribe from a merge request

Unsubscribes the authenticated user from a merge request to not receive
notifications from that merge request. If the operation is successful, status
code `200` together with the updated merge request is returned. If the user is
not subscribed to the merge request, the status code `304` is returned. If the
project or merge request is not found, status code `404` is returned.

```
DELETE /projects/:id/merge_requests/:merge_request_id/subscription
```

| Attribute | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| `id` | integer | yes | The ID of a project |
| `merge_request_id` | integer | yes   | The ID of the merge request |

```bash
curl -X DELETE -H "PRIVATE-TOKEN: 9koXpg98eAheJpvBs5tK" https://gitlab.example.com/api/v3/projects/5/merge_requests/17/subscription
```

Example response:

```json
{
  "id": 17,
  "iid": 1,
  "project_id": 5,
  "title": "Et et sequi est impedit nulla ut rem et voluptatem.",
  "description": "Consequatur velit eos rerum optio autem. Quia id officia quaerat dolorum optio. Illo laudantium aut ipsum dolorem.",
  "state": "opened",
  "created_at": "2016-04-05T21:42:23.233Z",
  "updated_at": "2016-04-05T22:11:52.900Z",
  "target_branch": "ui-dev-kit",
  "source_branch": "version-1-9",
  "upvotes": 0,
  "downvotes": 0,
  "author": {
    "name": "Eileen Skiles",
    "username": "leila",
    "id": 19,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/39ce4a2822cc896933ffbd68c1470e55?s=80&d=identicon",
    "web_url": "https://gitlab.example.com/u/leila"
  },
  "assignee": {
    "name": "Celine Wehner",
    "username": "carli",
    "id": 16,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/f4cd5605b769dd2ce405a27c6e6f2684?s=80&d=identicon",
    "web_url": "https://gitlab.example.com/u/carli"
  },
  "source_project_id": 5,
  "target_project_id": 5,
  "labels": [],
  "work_in_progress": false,
  "milestone": {
    "id": 7,
    "iid": 1,
    "project_id": 5,
    "title": "v2.0",
    "description": "Corrupti eveniet et velit occaecati dolorem est rerum aut.",
    "state": "closed",
    "created_at": "2016-04-05T21:41:40.905Z",
    "updated_at": "2016-04-05T21:41:40.905Z",
    "due_date": null
  },
  "merge_when_build_succeeds": false,
  "merge_status": "cannot_be_merged",
  "subscribed": false
}
```
