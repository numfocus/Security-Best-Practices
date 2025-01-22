# Securing Open Source Software: A Shared Responsibility

NumFOCUS-supported projects occupy a unique and critical position in the scientific and data-driven ecosystem. The tools and libraries we develop are relied upon by researchers, analysts, and engineers across academia, industry, and government. These projects often serve as the computational backbone for groundbreaking work, making them an essential part of the software supply chain. While we may not operate production systems directly, the widespread use of our software makes it an attractive target for attackers. Our role in this ecosystem bestows a certain responsibility to safeguard the secure and integrity of our work.

## Lessons from Recent Incidents

Two recent events highlight the importance of security in open source development:

1. **Ultralytics Package Compromise**  
   In late 2024, the Python package [ultralytics](https://github.com/ultralytics/ultralytics) was the target of a supply chain attack. Attackers exploited GitHub Actions workflows and an exposed PyPI API token to publish malicious versions, which were downloaded before being identified and removed. This incident underscores the need for secure workflows and credential management. PyPI posted a great review of the [incident here](https://blog.pypi.org/posts/2024-12-11-ultralytics-attack-analysis/) including recommendations for PyPI publishers.

2. **XZ Utils Backdoor**  
   Earlier in 2024, versions of XZ Utils were found to contain a backdoor. This code allowed attackers with a specific cryptographic key to execute remote commands and was given the maximum CVSS score of 10.0. The insertion of this backdoor into most Linux distributions took approximately three years and was based in social engineering. Read more [here](https://www.akamai.com/blog/security-research/critical-linux-backdoor-xz-utils-discovered-what-to-know).

## Read More to Improve Security

Your goal should be to adopt best practices to reduce risk, and we're here to help! The NumFOCUS Security Committee has collected these best practices and is focused on distilling the plethora of security-information into actionable guidance for NumFOCUS projects, acknowledging your unique placement in the supply chain, requirements, and constraints.