# front-end-play

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### What I used to build it
I've used Vue CLI and installed Vue.js 2 + Vue Router + Lint, I've also installed Bootstrap 5 via npm.

### Code version control and branch/development life-cycle  
I would use either typical git or git-flow. I am more onto using git-flow way though. 
We would have `master` and it's ideal latest copy `develop` 
We would branch off `develop` and create branches in following way `feature/branch-name` 
Once in a time we would merge `develop` into `feature/branch-name` if necessary get rid of 
conflicts and push it. We would use some kind of software similar to Jira/Trello in order 
to change the `status` of the ticket, create PR (Pull Request) and await reviews of the code. 
After the code review we would merge it to `develop`. Once in a while we would make a new release 
candidate, hence we would merge `develop` into `master`. During the development process we might 
need to do `hotfixes` - if it went live but we've got some bug/error.  

P.S. `branch-name` could consist of some numbering such as `x.y.z`, for same reason `tags` could be used

I would consider following steps for development life-cycle:
1. Planning (Brain Storm)
2. Analysis and Discussion (Brain Storm)
3. Design
4. Code / Implementation
5. Testing
6. It went live and nothing can stop this!

In the above list I would note that some steps might loop, especially somewhere between point 3-5.

### Animations CSS/JS
For this particular project I've added just a tiny CSS animation, for more complex and fun animations I would highly
likely use frameworks such as GASP (GreenSock) and ScrollJs. Nevertheless, using CSS is fun as well.

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
