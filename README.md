# Dialog Flow Server

This is the server of the frontend application [dialog flow](https://github.com/evolvable-by-design/dialog-flow/).

Dialog Flow is an application developed by [lauchness](https://github.com/lauchness). It implements one API change (see details below) that I use as a use-case to evaluate the evolvable-by-design approach that I created.

In this repository, the evolvable-by-design approach is implemented. Other projects are used as use cases, see the [evolvable-by-design organization](https://github.com/evolvable-by-design/).

## Repositories

Here is a list of all the repositories linked to this use-case.

- Original client: [lauchness/dialog-flow](https://github.com/lauchness/dialog-flow/commit/929dd1f84dde381d2e393a5f76a34cf95112054f)
- Client [fork with the evolvable-by-design implementation](https://github.com/evolvable-by-design/dialog-flow) (here)
- Original server: [lauchness/dialog-flow-server](https://github.com/lauchness/dialog-flow-server)
- Server [fork with the evolvable-by-design implementation](https://github.com/evolvable-by-design/dialog-flow-server)

**Amount of changes:** 1

**Type of change:** change model of returned data (n°3)

### Change 1: change returned model

**Description of the change:** do an API change (change returned model) while moving the API call to the server, see UI commit (https://github.com/lauchness/dialog-flow/commit/929dd1f84dde381d2e393a5f76a34cf95112054f) and server commit (https://github.com/lauchness/dialog-flow-server/commit/2b8b301d4909a6dbbbbda674ebe20989956118e2)

**Description of the work done:**

1. Fork both the client and the server
2. Remove the model change from the API to create a first version returning a model that is equal to the model previously used on the frontend (see [server commit](https://github.com/evolvable-by-design/dialog-flow-server/commit/a60e5c540f8d1640ec8d291ef5612635b5f42192))
3. Create the API documentation and serve it from the backend on OPTIONS {baseApiUrl}/ (see the three commits: [b2dd491](https://github.com/evolvable-by-design/dialog-flow-server/commit/b2dd491991a073c83546a50c9f06acc9d4bd25a1), [e3cc2ba](https://github.com/evolvable-by-design/dialog-flow-server/commit/e3cc2baf6aa5a1689cfe1529b918c9ccd96bc504) and [c53c7a2](https://github.com/evolvable-by-design/dialog-flow-server/commit/c53c7a2436fa68006e4869f07269f665e80958a5))
4. Modify the frontend to use the first version of the API (see [frontend commit](https://github.com/evolvable-by-design/dialog-flow/commit/8b3cb5f427f76483bb563e0a2d3e89efb4b97a9b))
5. Create the proper accounts on Google Cloud Console and Google API Console to get the dialog flow API credentials
6. Implement the evolvable-by-design approach into the frontend, [in a single commit](https://github.com/evolvable-by-design/dialog-flow/commit/560dc4de7e1a7db36510151ed67c01fcad16039f)
7. Replay the API evolution (see [server commit](https://github.com/evolvable-by-design/dialog-flow-server/commit/32d5c6bb363c7673a53c959e49554a7c920bcbb5))
8. Verify that the client code does not need to be modified in order to continue working -> **SUCCESS**

### Report

- How many evolutions? ➜ 1
- Types of evolutions ➜ change type of return value (n°3)
- One or several commits? ➜ 1
- How many lines per commit for the original evolution? ➜ 2 (for a 721 lines program)
- How many lines of code to implement the approach on the frontend? ➜ 43 lines changed
- One or several developers ➜ 1
- If tests, broken? ➜ no tests
- Covered or not covered? Covered

## How to test the evolution

1. Clone this repository
2. Go back to the commit before the evolution `git checkout before-evolution`
3. Start the server `npm start`
4. Start the [frontend](https://github.com/evolvable-by-design/dialog-flow/)
5. Play with it
6. Stop the server `ctrl + c` in the bash session
7. Move to the server commit implementing the evolution `git checkout after-evaluation`
8. Start the server back `npm start`
9. Refresh the frontend and play with it, it is still working while the code has not changed