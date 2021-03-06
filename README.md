Example
-------
For an example of how to use this plugin, see the [Liquibase Workshop](https://github.com/tlberglund/liquibase-workshop) repo. That project contains a `build.gradle` showing exactly how to configure the plugin, and an example directory setup as well.

News
----
Users of the latest version (0.7) of the Liquibase plugin need to change the
way the plugin is configured in their projects.  Basically, the Liquibase
configuration now goes in a ```liquibase``` block, instead of separate blocks,
and the defaultChangeLogs variable has gone away.

For example:

```groovy
changelogs {
  main {
    file = file('src/main/db/changelogs.groovy')
  }
}

databases {
  myDB {
    url = 'jdbc:mysql://localhost:3306/my_db'
	username= 'myusername'
	password = 'mypassword'
  }
defaultDatabase = databases.myDB
defaultChangeLogs = changelogs
```

Becomes:

```groovy
liquibase {
  changelogs {
    main {
      file = file('src/main/db/changelogs.groovy')
    }
  }
  
  databases {
    myDB {
      url = 'jdbc:mysql://localhost:3306/my_db'
	  username= 'myusername'
	  password = 'mypassword'
    }
  defaultDatabase = databases.myDB
}
```

