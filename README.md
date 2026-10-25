# CS 305 Software Security Portfolio

**Ehigie Ekata — Southern New Hampshire University**

## Project artifact

[Artemis Financial Practices for Secure Software Report](CS305_Project_Two_Report_Ekata.docx)

This Project Two report documents the checksum implementation, HTTPS configuration, certificate generation, dependency assessment, and testing. It includes screenshots of the application and its results.

## Client and software requirements

Artemis Financial is a consulting company that creates individualized financial plans covering savings, retirement, investments, and insurance. The company wanted to modernize its web application while protecting customer and financial information. The project focused on adding checksum verification and secure communication. My submitted application demonstrates SHA-256 verification of a unique data string over HTTPS; it does not implement a complete customer file-transfer service.

## Identifying vulnerabilities and coding securely

One strength of this project was checking the dependency findings instead of assuming that a successful build meant the application was secure. The original dependency assessment identified 150 distinct CVEs. After updating dependencies and testing the refactored application, the final scan reported zero known vulnerabilities within its documented coverage. Secure coding matters because software can run correctly while still exposing information or allowing misuse. For Artemis Financial, reducing those risks helps protect customer trust, avoid service interruptions, and limit the cost of recovering from a security incident.

## Challenges and useful parts of the assessment

Getting the dependency scan to complete and interpreting its output were challenging. Earlier attempts encountered vulnerability-data download and API configuration problems. This helped me understand the difference between a failed scan and a completed scan that found no vulnerabilities. Comparing the original and updated reports was useful because it made the effect of the dependency changes visible. I also learned to read analyzer warnings and coverage limitations before drawing conclusions from a report.

## Adding layers of security

The application combines several controls: SHA-256 checksums, HTTPS with TLS 1.2 and 1.3, certificate and hostname validation, external keystore configuration, and updated dependencies. The checksum service validates expected digest values, while the endpoint returns plain text and avoids exposing stack traces. These controls address different risks: a checksum detects changes against a trusted reference, and TLS protects information in transit. For future work, I would combine dependency scanning with manual code review and tests based on the application's threats. I would prioritize mitigations using severity, exploitability, affected functionality, and potential business impact, then retest the changes.

## Checking functionality and security after refactoring

The final build passed 11 automated tests with no failures, errors, or skipped tests. These tests covered hashing behavior, changed data, invalid reference values, and HTTP endpoint behavior. A separate HTTPS check confirmed a matching checksum, rejected an untrusted certificate and incorrect hostname, and checked that plaintext communication was not accepted. I also ran the updated application on my Windows computer and captured its startup and browser output. A repeat dependency scan reported zero vulnerable dependencies and zero suppressed vulnerabilities. That result applies to the scan's data and coverage; it does not prove the application has no undiscovered weaknesses.

## Resources and practices for future work

Eclipse, Maven, Java Keytool, OWASP Dependency-Check, and Java's MessageDigest API were useful resources. The vulnerability assessment process flow helped organize review of the architecture, input handling, APIs, cryptography, client/server communication, error handling, code quality, and encapsulation. Practices I would reuse include explicit UTF-8 encoding, keeping secrets outside source code, using established cryptographic libraries, testing failure cases, and preserving scan reports and test logs. I would also keep hashing and encryption separate in my design because they solve different problems.

## Demonstrating skills to employers

I would show an employer the attached report and selected examples from the checksum service, HTTPS configuration, and tests. The before-and-after dependency results demonstrate how security findings led to changes, while the screenshots and logs provide evidence that the updated application worked. I would explain the limits of the demonstration and the additional authentication, authorization, and certificate management needed for a production financial service. This project gives me a concrete example of assessing a security problem, implementing controls, and verifying the result.

