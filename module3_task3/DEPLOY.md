## What is in the archive and how to unarchive it? WIP

-What are the commands to start and stop the application? WIP
-How to customize where the application logs are written? WIP
-How to “quickly” verify that the application is running (healthcheck)? WIP

-A workflow run triggered by a a git tag name 1.0.0 should:

Create a GitHub Release using the “softprops/gh-release” GitHub Action named
1.0.0 and pointing to the tag 1.0.0,
Add the archive awesome-website.zip to the release 1.0.0,
Add the content of the file DEPLOY.md as text for the relase.
