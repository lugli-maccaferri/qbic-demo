# Qbic instance REST API
**Important**: provide the JWT with every request you make, because the instance needs to know who you are and which your permissions are!<br>
Once you make a login request to the authserver store the JWT you get from the response and send it in the `Authorization` header as a *bearer token*.
<br>
Example (pseudo http client setup):
```
{
	headers: {
		Authorization: "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpc19hZG1pbiI6IjEiLCJ1c2VyX2lkIjoiY2MxNzg5NzEtZWI5Zi00MTZjLWI1YzMtNmM5YjdmZjUzNjZlIiwiZWRpdF9mcyI6IjEiLCJpc3MiOiJxYmljIiwiZWRpdF9vdGhlcnMiOiIxIiwiZXhwIjoxNjI0NjU2MTIyLCJpYXQiOjE2MjQ2NDg5MjIsInVzZXJuYW1lIjoicm9vdCJ9.a73475GN-DfzU9LwzfqfkHo7_vOuacPCi5btf0wLZHPz5Ps0jr116OHOh0kpsvb4Hym_6-7U8-dr-XhlFcG49VH2DzPdT7yilnlmrYi1PiUCZ6mEwheWvMAr_2JLjTK9AkNGZE5f2R3yjQaj1CijXKQsi9s5LsrW2FZ1D1U0AErt3MGKmRHKVRH_yjYNMFq9E9C89ozMWkTTW8TB1c0-0esBrl8GDqNwud89flDCsaEoALMwDKRmAGjugI7SceYQPpa8oOuMB77PKilDPVGEPUjx2EZ_ScpqjfjoGH-PFTSGSscnnGCTY3hm63YE9kja5Fu3lc01i_sSLCEWqkxdKQ"
	}
}
```

# API methods
- [`/auth`](https://github.com/lugli-maccaferri/qbic-demo/blob/main/instance/api/auth.md)
-  [`/server`](https://github.com/lugli-maccaferri/qbic-demo/blob/main/instance/api/server.md)
