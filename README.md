# Transmission with openvpn on Kubernetes

The files here are intended to be a reference point for setting up transmission with openvpn
 on a kubernetes cluster. I provide these as-is, with less absolute zero support. If you'd like 
 to make an improvement to the resources or documentation, PRs are certainly welcome. 
 
This setup uses the [haugene/transmission-openvpn](https://github.com/haugene/docker-transmission-openvpn) docker 
image which has over 10 million downloads on docker hub. I have found to be quite stable and have been using for 
at least a year. You can find documentation (worth reading) for that project in their 
[github repo](https://github.com/haugene/docker-transmission-openvpn). 

## Using these examples

**Applying the examples here as-is will not work.**

I've scrubbed out configuration unique to the two clusters I'm running transmission in. You'll need to look through 
the examples and edit where appropriate. This example uses a central NFS server to host all Transmission data. 
you could of course use any other volume type available in your cluster. The ingress example does not configure TLS
 and is restricted to a local IP subnet. 

Some specific things you should adjust or confirm for your purposes:

* Ingress
  * Hostname
  * Service Name 
  * IP restrictions 
* Service
  * Name
  * Type
* Deployment
  * Secret name
  * Config name
  * data volume type, server, path
* Config
  * openvpn provider (see docs [here](https://github.com/haugene/docker-transmission-openvpn))
  * local network 
  * openvpn config
* Secret (will need to be base64 encoded)
  * username
  * password
  
  


## FAQ


#### Have you considered making this a helm chart?

Briefly. Not going to. I don't have the time to maintain a helm chart for this. I only provide this in hopes 
of saving someone time by having a working example to consult. 

#### Are there other ways to do this? 

Yes. 

#### Can you help me install this on my cluster? 

No. 

#### It doesn't work. 

Ok. 

#### I used these examples, can I make a tweak to make it easier for the next person to use? 

Absolutely. PRs are welcome. 