Secure Code Review Checklist

## What security vulnerabilities do you think is this code susceptible to?
- [ ] Thinking about the OWASP Top 10, or CWE top 25, which parts of the code do you think are more at risks?
- [ ] Which potential attacks can you envision attacking this part of the code?

## Are authorization and authentication handled in the right way?
- [ ] Are sessions handled correctly?
- [ ] Are failure messages for invalid usernames or passwords leak information?
- [ ] Are invalid passwords logged (which can leak sensitive pwd & user name combis)?
- [ ] Are the pwd requriements (lenghts/complexity) approriated?
- [ ] Are invalid login attempts correctly handelded with lockouts, and rate limit?
- [ ] Does the "forgot pwd" routine leak information, vulnerable to spamming, or is the pwd send in plain text via email?
- [ ] How and where are pwd and usernames stored, and are appropriate mechanisms such as hashing, salts, encryption in place?
## Is sensitive data like user data, credit card information securely handled and stored?
## Is the right encryption used?
- [ ] Are the encryption algorithms used state-of-the art and compliant with standards such as FIPS-140?
- [ ] Minimum key sizes to be supported
- [ ] What types of data must be encrypted
• Is the right type of cryptographic algorithm being used, is data being hashed that should be encrypted with a
symmetric key? If there is no way to safely transfer the symmetric key to the other party, is public key cryptographic
algorithms being employed?
• In any cryptographic system the protection of the key is the most important aspect. Exposure of the symmetric or
private key means the encrypted data is no longer private. Tightly control who has access to enter or view the keys,
and how the keys are used within applications.
• Any code implementing cryptographic processes and algorithms should be reviewed and audited against a set of
company or regulatory specifications. High level decisions need to be made (and continually revisited) as to what an
organization considers ‘strong encryption’ to be, and all implementation instances should adhere to this standard.
• Cryptographic modules must be tested under high load with multithreaded implementations, and each piece of
encrypted data should be checked to ensure it was encrypted and decrypted correctly.
## Does this code change reveal some secret information like keys, passwords, or usernames?
## If code deals with user input, does it address security vulnerabilities such as cross-site scripting, SQL injection, does it do input sanitization and validation?
  - [ ] Are inputs from external sources validated?
  - [ ] Is user input validated by testing type, length, format, and range, and by enforcing appropriate limits?
  - [ ] Are exact match approaches used whenever possible? If exact match is not possible, is the content of string variables checked for only expected values (whitelist)? If withelisting is not feasable, are entries rejected that contain inapproriated values such as binary data, escape sequences, and comment characters?
- [ ] Are XML documents validate against their schemas?
- [ ] Do you see string concatenations for user input? 
- [ ]  Are SQL statements dynamically created by using user input?

## Is data retrieved from external APIs or libraries checked accordingly?


## Exception handling
- [ ] Do all methods have appropriate exceptions?
- [ ] Does the error shown to users open us up for attacks, ie. includes stack trace, ids, etc? 

## Reducing the attack surface
- [ ] Are there any alarms or monitoring to spot if they are accessing sensitive data that they shouldn’t be? This could
apply to all types of users, not only administrators
- [ ] Is the function going to be available to non-authenticated users? If no authentication is necessary for the function
to be invoked, then the risk of attackers using the interface is increased. Does the function invoke a backend task that
could be used to deny services to other legitimate users? E.g. if the function writes to a file, 
or sends an SMS, or causes a CPU intensive calculation, could an attacker write a
script to call the function many times per second and prevent legitimate users access to that task?
- [ ] Are searches controlled? Search is a risky operation as it typically queries the database for some criteria and returns
the results, if attacker can inject SQL into query then they could access more data than intended.
- [ ] Is important data stored separately from trivial data (in DB, file storage, etc). Is the change going to allow unauthenticated
users to search for publicly available store locations in a database table in the same partition as the username/
password table? Should this store location data be put into a different database, or different partition, to reduce the
risk to the database information?
- [ ] If file uploads are allowed, are they be authenticated? Is there rate limiting? Is there a maximum file size for each
upload or aggregate for each user? Does the application restrict the file uploads to certain types of file (by checking
MIME data or file suffix). Is the application is going to run virus checking?
- [ ] If you have administration users with high privilege, are their actions logged/tracked in such a way that they a) can’t
erase/modify the log and b) can’t deny their actions?
- [ ] Are there any alarms or monitoring to spot if they are accessing sensitive data that they shouldn’t be? This could
apply to all types of users, not only administrators.
- [ ] Will changes be compatible with existing countermeasures, or security code, or will new code/countermeasures
need to be developed?
- [ ] Is the change attempting to introduce some non-centralized security code module, instead of re-using or extending
an existing security module?
- [ ] Is the change adding unnecessary user levels or entitlements that will complicate the attack surface.
- [ ] If the change is storing PII or confidential data, is all of the new information absolutely necessary? There is little value
in increasing the risk to an application by storing the social security numbers of millions of people, if the data is never
used.
- [ ] Does application configuration cause the attack surface to vary greatly depending on configuration settings, and is
that configuration simple to use and alert the administrator when the attack surface is being expanded?
- [ ] Could the change be done in a different way that would reduce the attack surface, i.e instead of making help items
searchable and storing help item text in a database table beside the main username/password store, providing static
help text on HTML pages reduces the risk through the ‘help’ interface.
- [ ] Is information stored on the client that should be stored on the server?
