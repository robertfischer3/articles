# **Finding the Balance: Aligning Authentication Strategies with NIST's Authenticator Assurance Levels**

## **Robert Fischer, fischer³.net**

April 2025

## **Introduction**

In today's digital landscape, security professionals face a constant challenge: how to implement robust authentication systems without creating friction that drives users to circumvent them. The friction plays out daily and is often seen with users who access an organization's most sensitive operations. 

**The Authentication Fatigue Problem**

Authentication fatigue occurs when users are forced to repeatedly verify their identity throughout their workday. Research that shows how many times a day the average employee needs to navigate was not found. However, the general consensus found in researching this article supports the idea that it can lead to decreased productivity and increased frustration. When authentication barriers interrupt workflow too frequently, users develop workarounds that ultimately compromise the security these systems aim to protect.

## **Shifting the Paradigm: From Authentication to Authorization**

A more effective approach lies in understanding the distinction between authentication (proving who you are) and authorization (verifying what you're permitted to do). Organizations can create security systems that protect sensitive resources without hampering productivity by implementing thoughtful authentication strategies paired with granular authorization controls.

The National Institute of Standards and Technology (NIST) Special Publication 800-63B provides a comprehensive framework for authentication through its Authenticator Assurance Levels (AALs), offering guidance that balances security with usability. Using this framework, this article presents four strategies to reduce fatigue while aligning with the Special Publication 800-63B 

## **Understanding NIST's Authenticator Assurance Levels**

NIST SP 800-63B defines three Authenticator Assurance Levels that provide increasing levels of security:

* **AAL1**: Permits single-factor authentication using memorized secrets (passwords) or physical authenticators.  
* **AAL2**: Requires multi-factor authentication with two different authentication factors.  
* **AAL3**: Requires multi-factor authentication with a hardware-based authenticator and verifier impersonation resistance.

Each AAL establishes specific requirements not for the authenticators themselves, but for the authentication sessions, since combinations of authenticators used together can achieve higher assurance levels than individually (Grassi et al., 2017).

## **Aligning Authentication Strategies with NIST Guidelines**

### **1\. Context-Aware Authentication Periods and AAL Requirements**

**Strategy**: Extend authentication sessions for read-only tasks while requiring more substantial verification for sensitive operations.

**NIST Alignment**: This strategy directly relates to NIST SP 800-63B's session management requirements. The guidelines recognize that pre-authentication checks may be used to lower misauthentication risks, such as authentication from unexpected locations. These checks can prompt additional risk-based controls without changing a transaction's AAL.

**Implementation Considerations**: At AAL1, longer session timeouts may be appropriate for low-risk, read-only operations. However, when moving to operations requiring AAL2 or AAL3 (such as accessing personally identifiable information), the system should prompt for additional authentication factors, maintaining compliance with NIST's reauthentication requirements.

### **2\. Task-Based Authorization Over Repeated Authentication**

**Strategy**: Implement proper authorization checks at critical security points rather than forcing users to re-authenticate multiple times.

**NIST Alignment**: This aligns with NIST's verifier requirements in Section 5, which focus on verification of the authentication process rather than repeated identity confirmation. The emphasis shifts from "who you are" to "what you're permitted to do," similar to how NIST structures its guidelines around what level of assurance is required for specific operations.

**Implementation Considerations**: Organizations can implement this strategy by mapping specific system operations to the appropriate AAL based on risk, rather than requiring the same level of authentication for all actions. This creates a more nuanced approach that reduces authentication fatigue while maintaining security boundaries.

### **3\. Single Sign-On with Stepped Verification**

**Strategy**: Implement SSO for basic access, with additional verification only triggered when users attempt actions requiring elevated privileges.

**NIST Alignment**: This approach aligns with NIST's federated identity guidelines, where authentication assertions can be used across services. The result of an authentication process "may be used locally by the system performing the authentication or may be asserted elsewhere in a federated identity system." (Grassi et al., 2017)(Grassi et al., 2023\)

**Implementation Considerations**: An adequately implemented SSO system should maintain awareness of the AAL achieved during initial authentication and prompt for additional factors when operations requiring higher AALs are attempted, ensuring compliance with NIST's requirements for each assurance level.

### **4\. Align Authentication Timeouts with Task Completion Requirements**

**Strategy**: Study how long users typically need to complete common workflows and set session timeouts accordingly.

**NIST Alignment**: This directly addresses the reauthentication requirements in NIST SP 800-63B sections 4.1.3, 4.2.3, and 4.3.3. These requirements are "intended to mitigate situations where a user's device is left logged in but unattended," and the timeout values are "based on both past versions of 800-63 as well as common industry practices for accessing sensitive information." (Grassi, Fenton, et al., 2017)(Grassi et al., 2023\)

**Implementation Considerations**: While implementing longer timeouts for usability, organizations must still comply with NIST's maximum session duration requirements. For highly sensitive operations (AAL3), additional controls such as continuous authentication or device monitoring might be necessary to balance usability with security.

Here's a paragraph on the latest developments in the SP 800-63 revision process:

## **Emerging Authentication Technologies in NIST SP 800-63 Revision 4 (Draft)**

The latest NIST SP 800-63 Revision 4 draft, which was open for public comment until October 7, 2024, introduces significant updates that address evolving authentication challenges. In my research, I have not yet found a finalized document. Two considerable additions stand out in the draft: integrated syncable authenticators and user-controlled wallets. Syncable authenticators (like passkeys) represent a breakthrough in usability by allowing credentials to synchronize across a user's devices while maintaining strong security. Meanwhile, digital wallets and credentials (termed "attribute bundles") are gaining traction as a federated identity approach that gives users greater control over their digital identities. (Grassi et al., 2023\) These technologies directly address authentication fatigue by reducing the cognitive burden of managing multiple credentials while also enhancing security. Organizations planning authentication strategies should monitor these emerging standards, as they represent NIST's recognition that usability and security must evolve together to effectively combat authentication fatigue.

## **Conclusion**

The most successful authentication systems recognize that security isn't just about preventing unauthorized access—it's about enabling authorized users to work efficiently. By aligning authentication strategies with NIST's Authenticator Assurance Levels, organizations can build security systems that protect their assets while supporting users' productivity needs. The key is developing a nuanced understanding of both the NIST guidelines and your users' workflows. This allows for implementing authentication that applies the appropriate level of security at the right moment, creating a secure and usable system.

Bob 

If you have any questions or recommendations, feel free to email me at robert@fischer3.net

---

## **Sources for Further Research:**

NIST Publications are arguably challenging to read. Having spent many years reviewing their publications, I recommend reading the table of contents and then picking one or two sections that interest you. Do not try to read the entire document in one sitting; it won’t benefit you. Instead, as you expand your cybersecurity knowledge, you will remember topics from the table of contents and return to see what NIST has to say.  Here are NIST documents you might want to consider for a deeper understanding. 

1. NIST Special Publication 800-63B: "Digital Identity Guidelines: Authentication and Lifecycle Management" \- The current edition, along with the draft Revision 4 (available for public comment until October 2024\)

2. NIST SP 800-63-3 Implementation Resources: Contains detailed explanations of the Authenticator Assurance Levels and implementation guidance

3. NIST SP 800-63 Digital Identity Guidelines FAQ: Provides answers to common questions about implementing the guidelines, including specifics about timeout requirements and memorized secrets

   ### References

   Grassi, P. A., Fenton, J. L., Newton, E. M., Perlner, R. A., Regenscheid, A. R., Burr, W. E., Richer, J. P., Lefkovitz, N. B., Danker, J. M., Choong, Y., Greene, K. K., & Theofanos, M. F. (2017). Digital Identity Guidelines: Authentication and Lifecycle Management. In *NIST*. https://doi.org/10.6028/nist.sp.800-63b  
   Grassi, P. A., Garcia, M. E., & Fenton, J. L. (2023). *Digital identity guidelines: revision 3*. https://doi.org/10.6028/nist.sp.800-63-3  
   *NIST SP 800-63 Digital Identity Guidelines-FAQ*. (n.d.). https://pages.nist.gov/800-63-FAQ/  
   Temoshok, D. (2024). *Digital Identity Guidelines:* https://doi.org/10.6028/nist.sp.800-63b-4.2pd  
 


