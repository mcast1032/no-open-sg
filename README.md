# Block Open Security Groups
This lab involves writing a policy that blocks open security group rules, like allowing the entire internet (0.0.0.0/0) to access sensitive ports such as SSH (22) or RDP (3389). These are among the most common and dangerous misconfigurations in cloud environments and are frequently exploited in attacks. 

Wrote a policy using Rego, tested it with Conftest, and ran everything inside GitHub Codespaces, with the intent of understanding why open security group rules are dangerous. 

Once I installed Terraform and Conftest again in the Codespace, and ran the codes, I was able to block one of the most common cloud misconfigurations using policy as code. This type of check can be added to the CI/CD pipeline to stope insecure deployments before they hit production. 

The lesson from the first part of the lab:

Open security groups are comparable to leaving your front door wide open to the world. Even if you don't intend to expose critical systems, attackers constantly scan for these entry points. Not addressing open security groups can lead to:

Remote shell access from malicious actors
Ransomware planted directly on cloud instances
Non-compliance with standards like NIST, FedRAMP, SOC 2
Loss of customer trust and public credibility
Usually this is an accidental misconfiguration, but it's one that policy as code could block before it ever goes live. 

The final part of the lab is to mitigate and retest.

This policy directly addresses critical security and compliance objectives by satisfying the following NIST SP 800-53 controls: 

AC-4 – Information Flow Enforcement: This policy prevents unauthorized traffic by explicitly blocking open ingress rules. It enforces controlled access at the infrastructure layer, stopping unrestricted data flow into sensitive systems.

AC-6(9) – Least Privilege: Limitation on Access by Port: By denying public access to ports 22 (SSH) and 3389 (RDP), the policy ensures that only authorized and minimal access is granted, reducing attack surface.

SC-7 – Boundary Protection: The policy enforces clear network boundaries by preventing open exposure to external sources. This is critical for segmenting systems and protecting internal components.

SC-7(3) – Access Points: Deny by Default: Rather than allowing traffic by default, this policy requires explicit safe configuration. It aligns with deny-by-default principles foundational to zero-trust architectures.

SI-4(20) – System Monitoring for Unauthorized Communications: While not a monitoring tool, the policy acts as a preventative measure by blocking high-risk misconfigurations before they occur—supporting broader monitoring and detection goals.
