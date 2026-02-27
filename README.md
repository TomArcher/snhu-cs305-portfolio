# SNHU CS-305-10473-M01 Software Security

This repo houses some of my CS-305 projects, including:

## Key Links

- [Artemis Financial Practices for Secure Software Report (Project Two)](./CS 305 Project Two - Thomas Archer.docx)

## Questions and Answers

**Briefly summarize your client, Artemis Financial, and its software requirements. Who was the client? What issue did the company want you to address?**

Artemis Financial is a consulting company that develops individualized financial plans for its customers, including savings, retirement, investments, and insurance. The company wanted to modernize its operations and strengthen its software security. Specifically, Artemis Financial needed a file verification step added to its web application to ensure secure communications. This required implementing a data verification mechanism in the form of a checksum, converting the application to use HTTPS for encrypted communications, and generating SSL/TLS certificates to secure client-server interactions.

**What did you do well when you found your client's software security vulnerabilities? Why is it important to code securely? What value does software security add to a company's overall well-being?**

I identified the security gaps in the original application through a manual code review. The original code had no data verification mechanism, placeholder values for SSL configuration, and outdated dependencies with known vulnerabilities. I addressed these by implementing a SHA-256 cryptographic hash algorithm for data verification and configuring HTTPS with a self-signed SSL/TLS certificate. Secure coding is critical because vulnerabilities can be exploited to access sensitive data, disrupt services, or compromise systems. For a financial consulting firm like Artemis Financial, which handles sensitive client data including savings, retirement, and investment information, a security breach could result in regulatory penalties, loss of client trust, and significant financial liability. Software security adds value by protecting the company's reputation, ensuring regulatory compliance, and maintaining the trust that clients place in the organization.

**Which part of the vulnerability assessment was challenging or helpful to you?**

The most helpful part was running the OWASP dependency-check tool before and after refactoring. This process made the scope of existing vulnerabilities in the third-party dependencies very tangible. Seeing 13 vulnerable dependencies with 148 CVEs in a project as small as this demonstrated how much risk is inherited through transitive dependencies alone. The most challenging part was understanding the distinction between false positives and genuine vulnerabilities in the dependency-check results. Some CVEs flagged against a dependency may not actually apply to the way that dependency is used in the application, and making that determination requires careful analysis of each vulnerability's description and the application's actual configuration.

**How did you increase layers of security? In the future, what would you use to assess vulnerabilities and decide which mitigation techniques to use?**

I increased layers of security through multiple complementary measures. First, I implemented SHA-256 cryptographic hashing to provide data integrity verification. Second, I configured HTTPS with an SSL/TLS certificate using RSA 2048-bit encryption to protect data in transit. Third, I used the OWASP dependency-check tool to perform static analysis on all third-party dependencies. This layered approach ensures that no single point of failure can compromise the entire system. In the future, I would continue to use the OWASP dependency-check tool for static analysis and would also incorporate the OWASP Top Ten framework as a guide for prioritizing which vulnerabilities to address first. For deciding on mitigation techniques, I would reference the Vulnerability Assessment Process Flow Diagram, which provides a structured approach to evaluating security across seven areas: Input Validation, APIs, Cryptography, Client/Server, Code Error, Code Quality, and Encapsulation.

**How did you make certain the code and software application were functional and secure? After refactoring the code, how did you check to see whether you introduced new vulnerabilities?**

I verified functionality by compiling and running the application, confirming that it started without errors, and testing the `/hash` endpoint in the browser to ensure it returned the correct checksum output over HTTPS. To check for newly introduced vulnerabilities, I ran the OWASP dependency-check tool both before and after refactoring and compared the results. The before and after reports showed the same 13 vulnerable dependencies and 148 CVEs, confirming that my code changes did not introduce any new security vulnerabilities. I also performed a manual code review to identify any syntactical, logical, or security issues in the refactored code.

**What resources, tools, or coding practices did you use that might be helpful in future assignments or tasks?**

Several resources and tools proved valuable during this project. Java's built-in `java.security.MessageDigest` library provided a secure, well-tested implementation for cryptographic hashing without requiring custom code. Java's keytool utility enabled certificate generation and management from the command line. The OWASP dependency-check Maven plugin automated the identification of known vulnerabilities in third-party dependencies. Spring Boot's annotation-based configuration simplified the creation of secure REST endpoints. As a coding practice, relying on established, vetted cryptographic libraries rather than writing custom implementations is a principle I will carry forward into all future development work.

**Employers sometimes ask for examples of work that you have successfully completed to show your skills, knowledge, and experience. What might you show future employers from this assignment?**

This assignment demonstrates several skills that are directly relevant to professional software development. It shows my ability to implement cryptographic algorithms using industry-standard libraries, configure secure HTTPS communications with SSL/TLS certificates, perform static analysis testing to identify vulnerabilities in third-party dependencies, and document technical decisions with appropriate justification. The Practices for Secure Software Report itself serves as an example of professional technical writing, and the refactored code base demonstrates practical application of secure coding principles. Together, these artifacts show that I can not only write functional code but also evaluate and strengthen its security posture.
