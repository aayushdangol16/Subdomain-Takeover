# Subdomain-Takeover
## Introduction
Subdomain takeover is a security vulnerability that occurs when an attacker is able to control a subdomain of a target website. This usually happens because the subdomain is pointing to a service (like a content delivery network, cloud service, or third-party hosting service) that has been decommissioned or is not properly configured. Here's a step-by-step explanation:
### 1. Understanding DNS and Subdomains
<b>Domain Name System (DNS)</b>: DNS is like the phonebook of the internet. It translates human-readable domain names (like example.com) into IP addresses that computers use to identify each other on the network.<br><br>
<b>Subdomains</b>: A subdomain is a part of a larger domain. For example, blog.example.com is a subdomain of example.com.
### 2. DNS Records
<b>A Record</b>: Points a domain or subdomain to an IP address.<br><br>
<b>CNAME Record</b>: Points a domain or subdomain to another domain name. It's often used to point subdomains to external services (e.g., shop.example.com pointing to shopify.com).
### 3. Third-Party Services and Subdomains
Organizations often use third-party services to handle specific tasks. For instance, they might use GitHub Pages for hosting static websites, Amazon S3 for storing assets, or Heroku for running applications. These services are linked to the organization's subdomain via CNAME or A records.
### 4. Decommissioning Services
When an organization stops using a third-party service, they may forget to remove the corresponding DNS records. The subdomain still points to the third-party service, but the service itself no longer exists.
### 5. The Subdomain Takeover Process
<b>Identify Vulnerable Subdomains</b>: An attacker identifies a subdomain that points to a decommissioned third-party service.

<b>Claim the Service</b>: The attacker registers the decommissioned service using the same name or path. For example, if assets.example.com was pointing to an Amazon S3 bucket that has been deleted, the attacker can create a new S3 bucket with the same name.

<b>Take Control</b>: Once the service is registered, the attacker now controls the subdomain. Any traffic to assets.example.com is now directed to the attacker's service.
### 6. Consequences
<b>Phishing</b>: Attackers can create phishing pages to steal user credentials.<br><br>
<b>Malware Distribution</b>: Malicious files can be hosted on the subdomain.<br><br>
<b>Brand Damage</b>: Users might lose trust in the organization if they encounter malicious content on what they think is a legitimate subdomain.
## Example
### 1. Initial Setup: ``` fallora.com ``` points to a GitHub Pages site.
``` fallora.com ``` is set up as a domain to serve documentation or any other content hosted on GitHub Pages. GitHub Pages allows users to host static websites directly from GitHub repositories.
### 2. Decommissioning: The organization stops using GitHub Pages but forgets to remove the DNS CNAME record.
The organization may decides to stop using GitHub Pages to host their documentation. However, they mistakenly overlook removing or updating the DNS CNAME record that points ``` fallora.com ``` to their GitHub repository's Pages site.

Due to this oversight, the DNS still resolves ``` fallora.com ``` to the GitHub Pages service, even though the organization no longer maintains the GitHub repository or updates its content.
### 3. Attacker's Action: The attacker registers a GitHub Pages site with the same name.
Seeing that ``` fallora.com ``` is vulnerable (pointing to a non-existent or inactive GitHub repository), the attacker decides to exploit this opportunity.

The attacker creates a new GitHub repository or uses an existing repository they control. They configure this repository to host content that could potentially harm users, such as phishing pages or malware.
### 4. Takeover: The attacker now controls ``` fallora.com ``` and can serve any content they want.
By setting up their GitHub repository with the same name , and configuring GitHub Pages to serve content from this repository, the attacker effectively takes control of ``` fallora.com ```.

Any visitor accessing ``` fallora.com ``` will now be directed to the attacker's GitHub Pages site instead of the legitimate one that was previously hosted by the organization.
