# Using the Application Security Verification Standard (ASVS)

As noted in the preface, the ASVS is a standard that defines the functional and non-functional security requirements for modern web applications and web services. It focuses on the security of an application's content. Refer to [OWASP SAMM](https://owaspsamm.org/) if you need information on secure development processes.

The ASVS should be useful to anyone trying to:

* Develop and maintain the content of secure applications.
* Evaluate the security of content inside applications.

This chapter will provide an overview of how the ASVS should be employed, including coverage of its risk-based approach and different use cases for the ASVS.

## Overview of ASVS Levels for Securing an Application's Content

The Application Security Verification Standard provides three verification levels for securing content and each level increases in sophistication and depth.

* ASVS Level 1 is for low assurance levels and is completely verifiable through penetration testing. (NOT RECOMMENDED)
* ASVS Level 2 is for applications that contain sensitive data, which requires protection and is the recommended level for most apps.
* ASVS Level 3 is intended for the most critical applications, such as those handling high-value transactions, containing sensitive medical data, or any application that demands the highest level of trust.

Each ASVS level contains a list of security requirements, and each of these requirements can be mapped to the security-specific features and capabilities that developers should add into their applications.

### Why Application Security Should Not Be Based on ASVS Level 1 (Low Assurance Content) 

Level 1 does not perform effective assurance activities and it should be actively discouraged, even though it is completely verifiable by penetration testing. Most penetration tests are over within a couple of weeks, but malicious attackers have a great deal of time. Defenders face limited resources and time to incorporate security controls, protect, find and resolve all weaknesses, then detect and respond to malicious actors. Black box testing, often performed at the end of development, quickly, or not at all, is completely unable to cope with this asymmetry, while malicious actors have essentially infinite time and only require a single porous defense, a single weakness, or missing detection to succeed. 

#### ASVS Level 1: The Weaknesses of Black Box Testing

Over the last 30+ years, black box testing has proven over and over again to miss critical security issues that led directly to ever more massive breaches. We strongly encourage the use of a wide range of security assurance and verification, including replacing penetration tests with source code-led (hybrid) penetration tests at Level 1, with full access to developers and documentation throughout the development process. Financial regulators do not tolerate external financial audits with no access to the books, sample transactions, or the people performing the controls, and industry and governments must demand the same standard of transparency in the software engineering field.

We strongly encourage the use of security tools within the development process itself. DAST and SAST tools, when continuously implemented in the build pipeline, can effectively identify and address straightforward security issues that should never exist.

Automated tools and online scans are unable to complete more than half of the ASVS without human assistance. If comprehensive test automation for each build is required, then a combination of custom unit and integration tests, along with build-initiated online scans are used. Business logic flaws and access control testing are only possible using human assistance. These should be turned into unit and integration tests.

## How To Use This Application Standard

We recommend that you use the Application Security Verification Standard as a blueprint to create your own Secure Coding Checklist that designed for to your application, platform or organization. The ASVS should be applied to your use cases and help your developers focus on the security requirements that are most important to your projects and environments.

### ASVS Level 1 - Meant for Very First Steps, Automated Testing, or View of the Whole Portfolio

An application achieves ASVS Level 1 if it adequately defends against application security vulnerabilities that are easy to discover and included in the OWASP Top 10 and other similar checklists.

Level 1 is the bare minimum that all applications should strive for. It is also useful as a first step in a multi-phase effort or when applications do not store or handle sensitive data and therefore do not need the more rigorous controls of Level 2 or 3. Level 1 controls can be checked either automatically by tools or simply manually without access to the source code. We consider Level 1 the minimum required for all applications.

This level protects your application from attackers who are using simple and low-effort techniques to identify easy-to-find and easy-to-exploit vulnerabilities. However, ASVS Level 1 will not protect your application from a determined attacker who will focus their energy on specifically targeting the application. If you value your data, you would rarely want to stop at a Level 1 review.

### ASVS Level 2 - Designed for Most Applications

An application achieves ASVS Level 2 (or Standard) if it adequately defends against most of the risks associated with software today. We recommend that projects use Level 2 for most applications.

Level 2 ensures that security controls are in place, effective, and used within the application. Level 2 is typically appropriate for applications that handle significant business-to-business transactions, including those that process healthcare information, implement business-critical or sensitive functions, or process other sensitive assets, or industries where integrity is a critica part of protecting their business, such as the game industry's needs to thwart cheaters and other game hacks. 

The most likely threats to Level 2 applications will typically be from skilled and motivated attackers focusing on specific targets using tools and techniques that are highly practiced and effective at discovering and exploiting weaknesses within applications.

### Level 3 - Designed for High Value, High Assurance, and High Safety

ASVS Level 3 is the highest level of verification within the ASVS. This level is typically reserved for applications that require significant levels of security, such as the military, critical infrastructure, health and safety, etc.

You may choose ASVS Level 3 if your organization has applications that perform critical functions and failure could significantly impact the organization's operations and even your organization's survivability. Example guidance on the application of ASVS Level 3 is provided below. An application achieves ASVS Level 3 (or Advanced) if it adequately defends against advanced application security vulnerabilities and also demonstrates principles of good security design.

An application at ASVS Level 3 requires more in-depth analysis of architecture, coding, and testing than all the other levels. A secure application is modularized in a meaningful way (to facilitate resiliency, scalability, and most of all, layers of security), and each module (separated by network connection and/or physical instance) takes care of its own security responsibilities (defense in depth), that need to be properly documented. Responsibilities include controls for ensuring confidentiality (e.g. encryption), integrity (e.g. transactions, input validation), availability (e.g. handling load gracefully), authentication (including between systems), authorization, and auditing (logging).

## How to Reference ASVS Requirements

Each requirement has an identifier which uses the format `<chapter>.<section>.<requirement>` and each element is a number, for example, `1.11.3`.

* The `<chapter>` value is the chapter where requirement is from--for example, all `1.#.#` requirements are from the `Architecture` chapter.
* The `<section>` value refers to the section within the referred chapter where the requirement appears. For example, all `1.11.#` requirements are in Chapter 1, Section 11, which in this case is the `Business Logic Architectural Requirements` section of the `Architecture` chapter.
* The `<requirement>` value identifies the specific requirement within a section, for example, `1.11.3` which as of ASVS Version 4.0.2 is:

> Verify that all high-value business logic flows, including authentication, session management and access control are thread safe and resistant to time-of-check and time-of-use race conditions.

We strongly recommend that you use the following format: `v<version>-<chapter>.<section>.<requirement>`, where: 'version' is the ASVS version tag, because identifiers may change between versions of the standard. For example: `v4.0.2-1.11.3` would refer to the 3rd requirement in the 'Business Logic Architectural Requirements' section of the 'Architecture' chapter from version 4.0.2. (This could be summarized as `v<version>-<requirement_identifier>`.)

IMPORTANT: The `v` preceding the version number in the format should always be lowercase.

If  an identifiers are used without including the `v<version>` element, then they should refer to the latest Application Security Verification Standard release. Sincce ASVS will grow and change in the future, writers or developers should always include the version element.

ASVS requirement lists are made available in CSV, JSON, and other formats which may be useful for reference or programmatic use.

## Forking the ASVS

We expect organizations can benefit by adopting the ASVS and choosing one of the three levels or by forking ASVS and changing requirements for an organization's application risk level in a domain-specific way. We encourage this type of forking as long as traceability is maintained so that if an app has passed requirement 4.1.1, this means the same thing for forked copies of the standard as it evolves.

Ideally, every organization should have its own forked ASVS and select tailor-fitted requirements. So if the organization is not using GraphQL, Websockets, or SOAP web service on their applications, they should drop those sections from their forked branch of the ASVS. Each organization's forking process must start with ASVS level 1 requirements as a baseline and then they should gradually move into ASVS level 2 or 3 based on their application's risk level.

## Other ASVS Use Cases: A Guide

While ASVS is often used to assess the security of an application (which is explored in more depth in the next chapter), we have identified several other potential uses for the ASVS (or a forked version).

### Potential ASVS Use Case: As Detailed Security Architecture Guidance

One of the more common uses for the Application Security Verification Standard is as a resource for security architects. The Sherwood Applied Business Security Architecture (SABSA) is missing a great deal of information that is necessary to complete a thorough application security architecture review. ASVS can be used to fill in those gaps by allowing security architects to choose better controls for common problems, such as data protection patterns and input validation strategies.

### Potential ASVS Use Case: As a Specialized Secure Coding Checklist

The ASVS can be used as a secure coding checklist for secure application development, helping developers to make sure that they keep security in mind when they build software. The secure coding checklist should be unified, clear, and applicable to all development teams. It should ideally be prepared based on guidance from security engineers or security architects.

### Potential ASVS Use Case: As a Guide for Automated unit and Integration Tests

The ASVS is designed to be highly testable, with the sole exception of architectural and malicious code requirements. By building unit and integration tests that test for specific and relevant fuzz and abuse cases, the application becomes nearly self-verifying with each and every build. For example, additional tests can be crafted for the test suite for a login controller, testing the username parameter for common default usernames, account enumeration, brute forcing, LDAP and SQL injection, and XSS. Similarly, a test on the password parameter should include common passwords, password length, null byte injection, removing the parameter, XSS, and more.

### Potential ASVS Use Case: Secure Development Training

ASVS can also be used to define the characteristics of secure software. Many “secure coding” courses are simply ethical hacking courses with a light smear of coding tips. This may not necessarily help developers to write more secure code. Instead, secure development courses can use the ASVS with a strong focus on the proactive controls found in the ASVS, rather than the Top 10 negative things not to do.

### Potential ASVS Use Case: As a Driver for Agile Application Security

ASVS can be used in an agile development process as a framework to define specific tasks that need to be implemented by the team to have a secure product. One approach might be: Starting with Level 1, verify the specific application or system according to ASVS requirements for the specified level, find what controls are missing and raise specific tickets/tasks in the backlog. This helps with the prioritization of specific tasks (or grooming) and makes security visible in the agile process. This approach can also be employed to prioritize auditing and review tasks within the organization. A specific ASVS requirement can drive a review, refactor, or audit for a particular team member, and be visible as 'debt' in the backlog that must eventually be addressed.

### Potential ASVS Use Case: As a Framework for Guiding the Procurement of Secure Software

ASVS is a great framework to help with secure software procurement or procurement of custom development services. The buyer can simply set a requirement that the software they wish to procure must be developed at ASVS level X, and request that the seller proves that the software satisfies ASVS level X. This works well when combined with the OWASP Secure Software Contract Annex

## Applying ASVS in Practice

Different threats usually have different motivations. Some industries have unique information and technology assets and domain-specific regulatory compliance requirements. All organizations are strongly encouraged to look deeply at their unique risk characteristics that are generated by the nature of their business, and determine the appropriate ASVS level based upon that risk and business requirements.

We have received feedback from various members of the community on how they implement the standard in practice:

### Feedback from Users of ASVS

#### From Matthew Hackling:

* Drives pen test scope and test cases
* Drives security requirements for designs help
* Populates an ISO27034 organisational normative framework aka requirements library.

#### From Dominique Righetto:

* Used for code review and as a checklist when performing web application vulnerability assessments.

#### From Giovanni Cruz:

* In the last OWASP Latam Tour Bogotá 2019, a training course was prepared totally based on ASVS. All the content was created with a vulnerable platform for training to assist developers. It got a great feedback because they showed them how to use it and what levels of security they might want to achieve based on some standard.

#### From Sebastien Giorias:

* Some customers use it as a basis for mandatory requirements to perform secure design and coding.

#### From Riotaro Okada:

* In recent years, some banks in Japan have included ASVS into their RFP as a mandatory requirement for security testing services. They wanted proposals where security vendors would fit appropriate ASVS levels.
* A local software vendor in Japan that sells SFA related packages received customer requests to check whether their products would fit ASVS, and which levels the product aligned to. (It was a good start for the vendor to introduce secure development and verifications into their teams)

#### From John Patrick Lita:

* Uses ASVS and integrates it in their CI/CD activity

### Use within other projects and tools:

* OWASP Defectdojo has built-in ASVS support https://www.defectdojo.org/
* A few weeks after the ASVS 4 release, RIPS added support for it: https://blog.ripstech.com/2019/rips-3.1-adds-teamcity-ldap-jsp-support/
