# Meteor Tips

## Create New Meteor Project
To setup new project: 
`bash cmr.sh new_project_name`

## Edit new Sublime Text snippet:
cmd-shift-p -> PackageResourceViewer: Open Resource -> User

## Snippets

`flrt` - new Flow Router
`nrc`  - new React Component
`nrcm` - new Meteor React Component
`nrcf` - full React Component
`rpa`  - new React.propTypes.array
`rpai` - React.propTypes.array.isRequired

## [Security](https://themeteorchef.com/blog/securing-meteor-applications/)

1. Remove autopublish & insecure packages

2. Use methods and not allow/deny
```
Meteor.call( 'insertDocument', document, ( error ) => {
  if ( error ) {
    alert( error.reason );
  } 
});
```

3. Add `check` and `audit-arguments-checks` packages
   * `meteor add check`
   * `meteor add audit-argument-checks`


4. Add allow & deny rules to your collections
```
Documents = new Meteor.Collection( 'documents' );

Documents.allow({
  insert() { return false; },
  update() { return false; },
  remove() { return false; }
});

Documents.deny({
  insert() { return true; },
  update() { return true; },
  remove() { return true; }
});
```

5. Don't forget about users 
```
Meteor.users.allow({
  insert() { return false; },
  update() { return false; },
  remove() { return false; }
});

Meteor.users.deny({
  insert() { return true; },
  update() { return true; },
  remove() { return true; }
});
```

5. Browser policy 