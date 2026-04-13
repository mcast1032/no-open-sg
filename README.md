# no-open-sg
This lab involves writing a policy that blocks open security group rules, like allowing the entire internet (0.0.0.0/0) to access sensitive ports such as SSH (22) or RDP (3389). These are among the most common and dangerous misconfigurations in cloud environments and are frequently exploited in attacks. 

Wrote a policy using Rego, tested it with Conftest, and ran everything inside GitHub Codespaces, with the intent of understanding why open security group rules are dangerous. 
