Secure Code Review Checklist

## Security and Data Privacy
- [ ] Does this code open the software up for
security vulnerabilities?
- [ ] Are authorization and authentication handled
in the right way?
- [ ] Is sensitive data like user data, credit card
information securely handled and stored?
- [ ] Is the right encryption used?
- [ ] Does this code change reveal some secret
information like keys, passwords, or usernames?
- [ ] If code deals with user input, does it address
security vulnerabilities such as cross-site
scripting, SQL injection, does it do input
sanitization and validation?
- [ ] Is data retrieved from external APIs or libraries
checked accordingly?
