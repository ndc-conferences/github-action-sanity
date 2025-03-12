# NDC Conferences fork of Sanity IO github action

The vercel-ndc-sanity project (which deploys the schema and data config
for NDC's Sanity websites) was deployed using v0.5-alpha of the
sanity-io/github-action-sanity build action.

In March 2025, it stopped working:

https://github.com/ndc-conferences/vercel-ndc-sanity/actions/runs/13749756794/job/38518955926#step:2:108

Best guess as to why is:

* `github-action-sanity` uses a Dockerfile build that's based on node:18
* `github-action-sanity` depends on @sanity/runtime-cli but doesn't specify a version for the dependency
* Sanity released an updated runtime-cli that no longer supports node 18.

As an interim fix, I've duplicated the code from sanity-io/github-action-sanity@v0.5-alpha and edited the Dockerfile nodeJS version so it's the exact same code but using node 20 instead of 18.






