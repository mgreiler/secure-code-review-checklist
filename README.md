Secure Code Review Checklist

## [ ] Does this code open the software up for security vulnerabilities?
- [ ] OWASP Top 10

## [ ] Are authorization and authentication handled in the right way?
- [ ] Are sessions handled correctly
## [ ] Is sensitive data like user data, credit card information securely handled and stored?
## [ ] Is the right encryption used?
## [ ] Does this code change reveal some secret information like keys, passwords, or usernames?
## [ ] If code deals with user input, does it address security vulnerabilities such as cross-site scripting, SQL injection, does it do input sanitization and validation?
  - [ ] Are inputs from external sources validated?
## [ ] Is data retrieved from external APIs or libraries checked accordingly?


## Exception handling
- [ ] Do all methods have appropriate exceptions?
- [ ] Does the error shown to users open us up for attacks, ie. includes stack trace, ids, etc? 
- [ ] 
