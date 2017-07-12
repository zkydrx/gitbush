## Is it possible to create a remote repo on GitHub from the CLI without opening browser

- curl  -u 'zkydrx:PASSWORD'  https://api.github.com/user/repos -d '{"name":"work"}'

  1. curl is a unix command (above works on mac too) that retrieves and interacts with URLs. It is commonly already installed.
  2. "-u" is a curl parameter that specifies the user name and password to use for server authentication.
     - If you just give the user name (as shown in example above) curl will prompt for a password.
     - If you do not want to have to type in the password, see githubs api documentation on [Authentication](https://developer.github.com/v3/#authentication)
  3. "-d" is a curl parameter that allows you to send POST data with the request
     - You are sending POST data in githubs [defined API format](https://developer.github.com/v3/repos/#create)
  4. "name" is the only POST data required; I like to also include "description"
  5. I found that it was good to quote all POST data with single quotes ' '

- git remote add origin git@github.com:zkydrx/projectname.git

  1. add definition for location and existance of connected (remote) repo on github
  2. "origin" is a default name used by git for where the source came from
     - technically didnt come from github, but now the github repo will be the source of record
  3. "git@github.com:nyeates" is a ssh connection that assumes you have already setup a trusted ssh keypair with github.

- git push origin master

  1. push to the origin remote (github) from the master local branch

  ​