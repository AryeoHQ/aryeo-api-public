# Authentication

The Aryeo Company API uses API keys to authenticate requests. You can view and manage your API keys in the Aryeo dashboard.

Your API keys may grant access to updating a number of resources in the Aryeo system, so make sure to keep them secure! Do not share your API keys in publicly accessible areas such as GitHub, client-side code, and so forth.

Authentication with a given API key is performed via bearer authentication. The token should be supplied in the authorization header: `Authorization: Bearer {token}`.