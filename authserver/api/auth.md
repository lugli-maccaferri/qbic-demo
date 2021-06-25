# Base endpoint `/auth`

#### POST `/login`
This request is used to obtain a signed JWT that you can then use to authorize requests to Qbic instances.
##### Parameters
|Name  |Type   | Description | Mandatory |
|--|--| -- | -- |
| `username ` | `string`  | The user's username | ✅|
| `password ` | `string`  | The user's password | ✅|
##### Example response (success):
```
{
    "success": true,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpc19hZG1pbiI6IjEiLCJ1c2VyX2lkIjoiY2MxNzg5NzEtZWI5Zi00MTZjLWI1YzMtNmM5YjdmZjUzNjZlIiwiZWRpdF9mcyI6IjEiLCJpc3MiOiJxYmljIiwiZWRpdF9vdGhlcnMiOiIxIiwiZXhwIjoxNjI0NjU2MTIyLCJpYXQiOjE2MjQ2NDg5MjIsInVzZXJuYW1lIjoicm9vdCJ9.a73475GN-DfzU9LwzfqfkHo7_vOuacPCi5btf0wLZHPz5Ps0jr116OHOh0kpsvb4Hym_6-7U8-dr-XhlFcG49VH2DzPdT7yilnlmrYi1PiUCZ6mEwheWvMAr_2JLjTK9AkNGZE5f2R3yjQaj1CijXKQsi9s5LsrW2FZ1D1U0AErt3MGKmRHKVRH_yjYNMFq9E9C89ozMWkTTW8TB1c0-0esBrl8GDqNwud89flDCsaEoALMwDKRmAGjugI7SceYQPpa8oOuMB77PKilDPVGEPUjx2EZ_ScpqjfjoGH-PFTSGSscnnGCTY3hm63YE9kja5Fu3lc01i_sSLCEWqkxdKQ"
}
```
