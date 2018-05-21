# HelloWorld

define suffix=dc=cac,dc=com
define maildomain=creditacceptance.com
define numusers=20

branch: [suffix]
objectClass: top
objectClass: domain

branch: ou=poc,[suffix]
objectClass: top
objectClass: organizationalUnit
subordinateTemplate: person:[numusers]

template: person
rdnAttr: uid
objectClass: top
objectClass: extensibleObject
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
givenName: <first>
sn: <last>
cn: {givenName} {sn}
uid: {givenName}
initials: {givenName:1}<random:chars:ABCDEFGHIJKLMNOPQRSTUVWXYZ:1>{sn:1}
employeeNumber: <sequential:0>
uid: user.{employeeNumber}
mail: {uid}@[maildomain]
userPassword: test123
description: This is the description for {cn}.
ds-pwp-account-disabled: false
