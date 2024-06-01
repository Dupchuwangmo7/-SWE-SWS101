- These vulnerabilities can be exploited by attackers to gain unauthorized access, steal user data, or impersonate legitimate users.
- It works based on two different ways
  - DOM-based Manipulation : This exploits how web browsers render web pages using the Document Object Model (DOM).
  - Attackers can use this and steal session tokens or change user settings.
  - Cookie Poisoning : this involves planting malicious data into cookie. 
  - Attackers can achieve this through various means, like tricking a user into viviring a malicious website or exploiting vulnerabilities in web applications. 

- Consequences
   - Identity thief : malicious manipulation can steal login credentials, names, email addresses or other personal information to commit crime.
   - Account Takeover : Attackers can hijack accounts by stealing session cookies.
   - Financial Loss :  If attackers take over the financial account through session cookies, they can steal money or make unauthorized transactions.
   - Malware Infection : attackers can also download or install malware putting data and privacy at future risk.


 Remediation For cookie Manipulation

- Set the HttpOnly flag on all cookies to prevent attackers from being accessed by client-side scripts and set secure flag on all cookies to ensure they are transmitted only over HTTPS connections.
- Implement secure session management practices to avoid relying solely on cookies for the authentication.
- Regular system monitoring.
