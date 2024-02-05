# Assessment and Certification

## OWASP's Stance on ASVS Certifications and Trust Marks

Since OWASP is a vendor-neutral not-for-profit organization, it does not currently certify any vendors, verifiers or software.

All organizations need to be cautious of trusting any third party or trust mark that states or implies ASVS certification. There are no assurance assertions, trust marks, or certifications that are officially vetted, registered, or certified by OWASP.

Organizations can offer assurance services as long as they do not claim official OWASP certification.

## Guidance for ASVS Certifying Organizations

The Application Security Verification Standard can serve as an open book verification of a target application, including open and unfettered access to key resources such as architects and developers, project documentation, source code, authenticated access to test systems (including access to one or more accounts in each role), particularly for L2 and L3 verifications.

While penetration testing and secure code reviews have historically included issues “by exception” - that is only failed tests appear in the final report, this is not the case with ASVS. An ASVS certifying organization must include the scope of the verification in any report (particularly if a key component is out of scope, such as SSO authentication) as well as a summary of verification findings, including passed and failed tests, with clear indications of how to resolve the failed tests.

Some ASVS verification requirements might not apply to the specific application that is being tested. For example, if you provide a stateless service layer API without a client implementation to your customers, many of the requirements in V3 Session Management are not directly applicable. In such cases, a certifying organization may still claim full ASVS compliance, but they must clearly indicate in any report a reason for non-applicability of such excluded verification requirements.

Certifying organizations that keep detailed work papers, screenshots or movies, have scripts that reliably and repeatedly exploit an issue, and maintain electronic records of testing, such as intercepting proxy logs and associated notes such as a cleanup list, are following standard industry practice and this evidence can be really useful as proof of the findings for the most doubtful developers. It is not sufficient to simply run a tool and report on the failures for certifying with ASVS; this does not (at all) provide sufficient evidence that all issues at a certifying level have been tested and tested thoroughly. In case of dispute, there should be sufficient assurance evidence to demonstrate each verified requirement has indeed been tested.

### Testing Methods for ASVS

Certifying organizations are free to choose the appropriate testing method(s), but should provide substantial documentation of their approaches in a report.

Depending on the application under test and the verification requirement, different testing methods may be used by a certifying organization to gain similar confidence in the results. For example, validating the effectiveness of an application's input verification mechanisms can be assessed either through a manual penetration test or by conducting source code analysis.

#### Using Automated Security Testing Tools in ASVS

All certifying organizations are encouraged to use automated penetration testing tools to provide as much coverage as possible. However, it is not possible to fully complete ASVS verification using such tools alone. Whilst a large majority of requirements in L1 can be performed using automated tests, the overall majority of requirements in ASVS are not amenable to automated penetration testing.

Note that the lines between automated and manual testing have blurred as the application security industry matures. Automated tools are often manually tuned by experts and manual testers often employ a wide variety of automated tools.

#### The Role of Penetration Testing in ASVS

In version 4.0, we decided to make L1 completely penetration testable without access to source code, documentation, or developers. Two logging items, which are required to comply with OWASP Top 10 2017 A10, will require interviews, screenshots or other evidence collection, just as they do in the OWASP Top 10 2017. However, employing penetration tests without access to necessary information is not an ideal method of security verification, as it misses out on the possibility of reviewing the source, identifying threats and missing controls, and performing a far more thorough test in a shorter timeframe.

When performing a L2 or L3 Assessment, certifying organizations are required to have access to the target's developers, documentation, and code, as well as access to a test application with non-production data. Penetration testing done at L2 and L3 Assessments requires this level of access, which we call "hybrid reviews" or "hybrid penetration tests".
