# Password Management

Maintaining open source software often means juggling a variety of responsibilities—from ensuring code quality to building a thriving community of contributors. Projects often find themselves juggling accounts on a variety of platforms like code repositories domain providers, and container repositories, all while trying to control access to the right set of individuals. This is often messy and a source of vulnerability.

This post aims to help open source maintainers understand:

1. The value of using a password manager for both personal and project credentials.
2. How to scan for accidentally committed secrets using open source tools like [TruffleHog](https://github.com/trufflesecurity/trufflehog).
3. Techniques for setting up pre-commit hooks and CI scans to ensure secrets do not leak into your repositories.

---

## Risks of Insecure Password Management

Hardcoded passwords, API keys, and other secrets in your repository can expose your project to risks like:

- **Account Takeover**: Exposed credentials can allow unauthorized access to critical services (e.g., package registries, CI/CD systems, or infrastructure).
- **Reputation Damage**: A security breach can harm your project's reputation, deterring potential collaborators or users.
- **User Supply Chain Risk**: With unauthorized access, attackers can push harmful content to your users. Most often, this is simply defacement or malicious binaries (like cryptojackers), but can sometimes be more insidious.

Ensuring that passwords and other sensitive credentials remain secure is essential for any project that wants to maintain trust and protect both its developers and users.

---

## Best Practices for Secret Handling

1. **Never store passwords or tokens directly in your repository.** Use something like GitHub Secrets to manage your secrets during CI/CD.
2. **Limit Credential Scope**: Give each service or token the least privileges possible. Avoid reusing passwords across multiple services.
3. **Rotate Credentials Regularly**: If you accidentally expose a secret, be prepared to revoke or rotate it immediately.
4. **Educate Contributors**: Let your community know about these security measures. Provide clear guidelines for how they should handle secrets.

---

## Using a Password Manager

One of the easiest ways to ensure secrets stay secure is to use a password manager. Password managers offer:

- **Encrypted Storage**: Passwords are stored in an encrypted vault, reducing the risk of accidental exposure.  
- **Secure Sharing**: Share credentials safely among project maintainers without resorting to email or plaintext messages.  
- **Strong, Unique Passwords**: Automatically generate strong passwords for each service to minimize the damage if one account is compromised.

If you’re looking for a managed solution, [1Password](https://github.com/1Password/for-open-source) provides a **free Teams account for Open Source Projects**. An open source alternative is [Bitwarden](https://github.com/bitwarden/).

---

## Scanning for Secrets

Even with a password manager, mistakes can happen. You or a contributor might accidentally commit a password, API key, or other credentials to the repository. Fortunately, tools like [TruffleHog](https://github.com/trufflesecurity/trufflehog) can help detect these secrets before they make their way into production or public repositories.

For usage details, see the official [Trufflehog documentation](https://github.com/trufflesecurity/trufflehog).

When evaluating a secret scanning tool, there are several key features to look for:

1. **Relevance**: The relevance to the secrets your project uses. Most of these tools use regular expressions to identify the service associated with the credential. Some also test the credential to determine if it's still active, which helps reduce false positives. Review their documentation to make sure that the services you use are monitored.
2. **Pre-commit hooks**: The best time to catch a mistake is before it happens. If you can configure the tool into [pre-commit hooks](https://pre-commit.com/), you can detect the secrets _before you can commit them locally and subsequently push changes to the remote repository_.
3. **CI/CD**: We work in distributed teams and building checks into our automated processes will help protect everyone.

The Security Committee has found that TruffleHog fits nicely because it is open source, supports a wide range of detectors, and has convenient pre-commit hooks and CI integrations.

---

## Conclusion

Password management is a foundational security practice for any open source project, including those under NumFOCUS. By leveraging password managers such as [1Password](https://github.com/1Password/for-open-source) (with its free Teams account for eligible OSS projects) and incorporating secret scanning tools like [TruffleHog](https://github.com/trufflesecurity/trufflehog) into your workflow, you can significantly reduce the risk of accidental credential leaks and protect your maintainers and users.

For additional reading on security best practices beyond password management and around project-specific recommendations, please refer to [Scientific Python - SPEC 6 — "Keys to the Castle"](https://scientific-python.org/specs/spec-0006/).