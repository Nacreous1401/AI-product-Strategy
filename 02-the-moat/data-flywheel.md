# Data Flywheel Map

## Flywheel Loops

### Loop 1: Correction Loop
**Score: 3/5**
*When your AI gets something wrong, what happens to that correction?*  
The copilot suggests a fix, say, switch a SIM to a different carrier. The ops engineer overrides it. Right now that override disappears. It should be saved as a labelled training example: what the AI said, what the human did instead, and why. The network-layer context makes these corrections uniquely valuable — no generic model has this data.

### Loop 2: Preference loop
**Score: 3/5**
*Does the product learn individual/team preferences over time?*  
Every team has operational policies baked into how they work — preferred carriers per region, risk tolerance, manual vs automated fixes. Today the copilot treats every session as a blank slate. Capturing those patterns builds a team profile that makes the product feel like it knows you — and makes switching feel like starting over.

### Loop 3: Domain context loop
**Score: 4/5**
*Does usage in one area improve quality in adjacent areas?*  
A failure pattern spotted on a roaming partner in Germany instantly improves detection for every other customer using that same partner — in any country, any industry. This cross-domain transfer happens automatically because emnify owns the core network and all roaming data flows through it. AWS cannot buy this. Cisco cannot replicate it. It gets stronger with every new fleet that joins.

### Loop 4: Network loop
**Score: 2/5**
*Does each new user/team make the product better for everyone?*  
New customers passively add data volume, which quietly improves baselines — but they don't visibly make the product better for existing users. No benchmarking, no "fleets like yours" comparisons, no shared intelligence surfaced to customers. The network effect is real under the hood but invisible in the product. Making it visible is a product decision, not an infrastructure one.


**Total Flywheel Score: 13/20**  
**Weakest Loop: Network (2/5)**  
**Fix for weakest loop:**  
Surface fleet benchmarking in the copilot so new customers visibly benefit existing ones

---

## Competitive Positioning

**Axis X:**  
Generic cloud IoT platform → Telecom-native connectivity intelligence

**Axis Y:**  
Reactive dashboarding → Proactive AI-assisted resolution

| Competitor | X Position | Y Position | Notes |
|-----------|-----------|-----------|-------|
| Your product | Telecom-native connectivity intelligence | Proactive AI-assisted resolution | Uses SIM/eSIM, roaming, carrier, and incident data to recommend actions |
| AWS IoT | Generic cloud IoT platform | Reactive / partially proactive | Strong cloud distribution, but weaker telecom-specific visibility |
| Cisco IoT Control Center | Telecom / carrier connectivity management | Mostly reactive dashboarding | Strong CMP competitor, but less differentiated AI copilot layer |
| 1NCE | Connectivity-first IoT platform | Mostly reactive management | Strong simple connectivity offer, but less advanced operational intelligence |

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*

**Attacker:**  
AWS  
**Attack vector:**  
Bundles SIM Management into AWS IoT Core. Offers it free to existing enterprise customers.   
**Time to threat**    
18-24 months - Carrier deals take time   
**Your defense:**    
Show what AWS can't see-  SS7, roaming failures, inter-carrier data. Make "good enough" feel risky.  
