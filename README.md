# Apex domains and Azure CDN endpoints

In Azure, platform (PaaS) services provide a higher level of abstraction than infrastructure services. PaaS services allow a customer faster time to market and reduced operational overhead and so are often the first choice for delivering an application or service.

PaaS services usually expose the individual services as fully-qualified domain names (FQDN) under a set of common IP addresses for all users of that service in that location. Azure CDN is one such example. Because the services often share a limited set of IP addresses, these services *must* be accessed via the service FQDN and not their IP address.

Customers often need to use a more friendly domain name and therefore use DNS services to provide a custom domain. CNAME records may be used for this service. So a CNAME record for a custom domain is created which points to the FQDN of the PaaS service. With some configuration at the PaaS service (and generally the registration of an SSL certificate), a service can be quickly delivered against custom domain names.

## Conventional domains
This works pretty smoothly with a conventional domain. In my example www.metronzone.com. 
![www domain](www-domain-simple.png)

You create a DNS CNAME pointing to the CDN endpoint
![DNS to CNAME](dns-to-cdn.png)

and then make sure your CDN is aware of this DNS name.
![CDN to domain](cdn-to-dns.png)

## Example flow
![Example flow](apex-domain.png)
