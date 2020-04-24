# Notes
I will need to skip this part as following issues regardign permissions is just so annoying and using basic volumes works fine. Optional part where you would bind redis data-dir to local directory works with similar issues.

It seems to stem from postgres images flow where they step down from root user to postgres user with less power. This could be probably be solved by adding more own shell scripts into postgres service but it is what it is. A excerpt from logs is provided below. A discussion on docker github https://github.com/docker-library/postgres/issues/558#issuecomment-472234418 backs this up and pretty much renders this exercise moot.

	db_1        | selecting default time zone ... UTC
	db_1        | creating configuration files ... ok
	db_1        | running bootstrap script ... 2020-04-24 10:00:23.812 UTC [51] FATAL:  data directory "/var/lib/postgresql/data" has wrong ownership
	db_1        | 2020-04-24 10:00:23.812 UTC [51] HINT:  The server must be started by the user that owns the data directory.
	db_1        | child process exited with exit code 1
	db_1        | initdb: removing contents of data directory "/var/lib/postgresql/data"
	devopsdocker2019_db_1 exited with code 1
	backend_1   |
	backend_1   | > backend-example-docker@1.0.0 start /
	backend_1   | > cross-env NODE_ENV=production node index.js
	backend_1   |
	frontend_1  | Browserslist: caniuse-lite is outdated. Please run next command `npm update caniuse-lite browserslist`
	backend_1   | Browserslist: caniuse-lite is outdated. Please run next command `npm update caniuse-lite browserslist`
	frontend_1  | Browserslist: caniuse-lite is outdated. Please run next command `npm update`
	backend_1   | [BABEL] Note: The code generator has deoptimised the styling of /node_modules/lodash/lodash.js as it exceeds the max of 500KB.
	backend_1   | Fri, 24 Apr 2020 10:00:33 GMT sequelize deprecated String based operators are now deprecated. Please use Symbol based operators for better security, read more at http://docs.sequelizejs.com/manual/tutorial/querying.html#operators at node_modules/sequelize/lib/sequelize.js:260:13
	backend_1   | Testing database connection
	backend_1   | Redis connection, initating..
	backend_1   | Trying to set cache
	backend_1   | Cache set successfully
	backend_1   | Started on port 8000
	backend_1   | HostNotFoundError [SequelizeHostNotFoundError]: getaddrinfo ENOTFOUND db
	backend_1   |     at /node_modules/sequelize/lib/dialects/postgres/connection-manager.js:119:24
	backend_1   |     at Connection.callback (/node_modules/pg/lib/client.js:140:14)
	backend_1   |     at Connection.emit (events.js:315:20)
	backend_1   |     at Socket.emit (/node_modules/pg/lib/connection.js:71:10)
	backend_1   |     at Socket.emit (events.js:315:20)
	backend_1   |     at emitErrorNT (internal/streams/destroy.js:84:8)
	backend_1   |     at processTicksAndRejections (internal/process/task_queues.js:84:21) {
	backend_1   |   name: 'SequelizeHostNotFoundError',
	backend_1   |   parent: Error: getaddrinfo ENOTFOUND db
	backend_1   |       at GetAddrInfoReqWrap.onlookup [as oncomplete] (dns.js:66:26) {
	backend_1   |     errno: -3008,
	backend_1   |     code: 'ENOTFOUND',
	backend_1   |     syscall: 'getaddrinfo',
	backend_1   |     hostname: 'db'
	backend_1   |   },
	backend_1   |   original: Error: getaddrinfo ENOTFOUND db
	backend_1   |       at GetAddrInfoReqWrap.onlookup [as oncomplete] (dns.js:66:26) {
	backend_1   |     errno: -3008,
	backend_1   |     code: 'ENOTFOUND',
	backend_1   |     syscall: 'getaddrinfo',
	backend_1   |     hostname: 'db'
	backend_1   |   }
	backend_1   | } Connection to database database failed, tries left 5 trying again in 3 seconds
