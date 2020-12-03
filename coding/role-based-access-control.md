## Role Based Access Control
## source:https://csrc.nist.gov/projects/role-based-access-control
## source:https://en.wikipedia.org/wiki/Role-based_access_control

git.exe filter-branch --force --index-filter \
  'git rm -r --cached --ignore-unmatch ./vendor/' \
  --prune-empty --tag-name-filter cat -- --all