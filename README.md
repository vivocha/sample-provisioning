# Vivocha user provisioning sample

This **sample** shows how to use the on-behalf-of login API to do the provisioning of the agents on Vivocha. See more on: [On-behalf-of login](http://docs.vivocha.com/display/VVCJ/On-behalf-of+login) 

### Installation

```sh
$ git clone [git-repo-url] sample-provisioning
$ cd sample-provisioning
$ npm install
```

And then you can add/edit the users in the users.js module.

| Parameter  | Required | Description |
| ---------- |:--------:| --- |
| onBehalfOf | YES      | Agent user id on behalf of we want to login (if the agent does not exists in our database it will be created otherwise it will be updated) |
| keep       | NO       | Keeps the values on the Vivocha database instead of the values (this value is ignored for the password property that is always updated) |
| media      | NO       | Media allowed for the agent (chat,voip,video) |
| nickname   | NO       | Nickname |
| firstname  | NO       | First name |
| surname    | NO       | Last name |
| email      | NO       | Email |
| tags       | NO       | Agent tags separated by commas (i.e. "tag1,tag2,tagx"), the tags are used to limit the service availability to the agents with the same set of tags |
| password   | NO       | Agent password |
| logout     | NO       | Url in which the agent will be redirected after the logout |

Example:

``` JavaScript
module.exports = [{
  id: "agent1",
  media: "chat",
  nickname: "AgentOne",
  firstname: "Name",
  surname: "Surname",
  email: "agent1@example.com",
  //lang: "en",
  tags: "one,two"
}];
```

### Usage:
```sh
./provisioning -a <accountid> -u <userid> -p <password>
```

### More:
For a list of all available options run `provisioning -h`:
```sh
$ ./provisioning -h

  Usage: provisioning [options]

  Options:

    -h, --help                 output usage information
    -V, --version              output the version number
    -a, --account <account>    Vivocha account
    -u, --user <user>          Vivocha user (must be an admin user)
    -p, --password <password>  Vivocha user password
```