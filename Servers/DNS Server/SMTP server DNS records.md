



### DKIM records
 DKIM, which stands for DomainKeys Identified Mail, is an email authentication and anti-phishing technology. DKIM records are DNS (Domain Name System) records that are used to digitally sign outgoing email messages, allowing the recipient's email server to verify that the email indeed comes from an authorized source and hasn't been tampered with during transit.

To obtain DKIM records for your domain, follow these general steps:

1. **Generate a DKIM Key Pair:** Use a tool like OpenSSL or specialized DKIM key generation tools to create a DKIM key pair. OpenSSL is a common choice for this purpose.
    
    To generate a DKIM private key using OpenSSL, you can use a command like this:
    
    `openssl genpkey -algorithm RSA -out private.pem -aes256`
    
    This command generates a private key in the "private.pem" file.
    
2. **Extract the Public Key:** Once you have the private key, extract the public key portion that will be used in the DKIM DNS record. You can do this using OpenSSL as well. For example:
    `openssl rsa -pubout -in private.pem`
    
    This command will print the public key to the terminal. You can copy it and save it for later use in your DNS records.
    
3. **Create the DKIM DNS Record:** In your domain's DNS settings, create a DKIM record (TXT record) containing the public key. The record typically includes the "v" version tag, the "k" key type tag, the "p" public key tag, and a "t" flags tag (for testing, it can be omitted in production).
    
    A typical DKIM DNS record might look like this:
    `v=DKIM1; k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCWawXI6JDyq7l5RvwIDAQAB`
    
    The `p` tag contains the public key you extracted in step 2.
    
4. **Publish the DKIM DNS Record:** Once you've created the DKIM DNS record, you need to publish it in your domain's DNS configuration. The method for doing this depends on your DNS hosting provider or the service you use. You usually add a new TXT record with the DKIM information.
    

The "selector" in the DKIM generator section is a user-defined label that helps distinguish between different DKIM key pairs for the same domain. You can think of it as a unique identifier for the DKIM key pair. You might have multiple selectors for different email services or different servers within your domain. For example, you might use selectors like "s1._domainkey" and "s2._domainkey" to differentiate between DKIM keys for different purposes.

When you create the DKIM DNS record, you specify the selector as part of the subdomain. For example, if your selector is "s1," your DKIM DNS record might look like this:
`s1._domainkey.example.com. IN TXT "v=DKIM1; k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCWawXI6JDyq7l5RvwIDAQAB"`

The receiving email server will use this selector to look up the correct DKIM public key in your DNS records to verify the authenticity of your emails.