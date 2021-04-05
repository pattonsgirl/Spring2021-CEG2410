# Quiz 3

1. HTTP connections are secure and enforce encryption of traffic.
    - False.  HTTPS

2. I have a an organization with a domain of griffin.com  I have a set of resources I would only like a select group of people to access.  I would also like allow the group to have its own administrator.  Would it be better to create them their own domain or their own organizational unit inside my domain?
    - Organizational Unit

3. Browsers inherently trust self-signed certs.
    - False.  Browsers will not trust self-signed certs.  Much like an invalid cert, the user will need to accept the potential security risk.  Browsers will trust certificates with domain validation, which could be done using Let's Encrypt or a certificate authority.

4. Users on a directory service must have a unique identification.
    - True

5. What Powershell module is aliased to `ls`?
    - Get-ChildItem / gci
    - also accepted `dir` on a technicality