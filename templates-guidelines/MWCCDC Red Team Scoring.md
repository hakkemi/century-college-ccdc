# **MWCCDC Red Team Scoring**

# **Context**

A minimal version of the spreadsheet red team uses for scoring can be found [here](https://docs.google.com/spreadsheets/d/1iaPo-4Ur6B6esEY8nxmfqSVrmc-Lx_qqSpW5WtrMb_o/).

Before the competition:

1. Black team creates the vulnerable infrastructure. Vulnerabilities in the infrastructure created by black team that red team leverages will be referred to as **“Exploits”** or “Attacks”  
2. Red team has a few days to implement “persistence mechanisms” that assist them in retaining environment access. Persistence mechanisms added by red team will be referred to as **“Persistence”**

An **“attack narrative”** is a group of **exploits** run in succession. For example,

1. Upload a PHP web shell  
2. Use the web shell to run commands  
3. Escalate privileges locally to root

During the competition, red team will:

* Run **attack narratives** uniformly across all teams, to the best of their ability, and take services down if the narrative is successful  
* Leverage **persistence** to take services down uniformly across all teams

For each successful **exploit** in an attack narrative, red team will keep track of the following.

* exploit  
* team number  
* affected host  
* timestamp

Red team does not keep track of service takedowns nor persistence removal. This is reflected in the team’s service score.

# **Exploits**

Each exploit in an attack narrative has an associated point value. Exploits that are easier to prevent have higher point values. Each blue team that the red team successfully exploits will lose the corresponding number of points.

If a team restores their services but does not fix the vulnerability, red team will rerun the same exploit, resulting in another point deduction. This means that for the highest red team score, it is best to fully fix a vulnerability prior to bringing services back online.

Teams can submit a PDF **“IR report”** to regain up to *all* (100%) points lost from a successful red team attack narrative. IR reports will be graded according to the rubric referenced below. IR reports do not have to be professionally written nor look pretty, and aside from collecting evidence, they should typically take no more than a couple minutes to write.

# **Persistence**

Each persistence mechanism has an associated point value. Persistence mechanisms that are more difficult to find and eradicate have higher point values. All red team points for eradicating a persistence mechanism are earned through IR reports.

Teams can submit a PDF **“IR report”** to gain up to the number of points associated with that persistence mechanism. IR reports will be graded according to the rubric referenced below. IR reports do not have to be professionally written nor look pretty, and aside from collecting evidence, they should typically take no more than a couple minutes to write.

# **Incident Response (IR) Reports**

IR reports are used for two things:

* regaining points from exploits  
* gaining points for persistence removal

IR reports are graded according to [this rubric](https://docs.google.com/document/d/1XrfaIcIDtY86Uw6-GMa6taEvpec9rpGybclNPaYDux4/), and [here is an example of a good IR report](https://docs.google.com/document/d/1vqQawM2_QwiPH5Ny841iCTLyPocChknyWqPwStPG4RU/). You are encouraged to use the example report as a template.

Each IR report should cover a *single* attack narrative or persistence mechanism. If an IR report covers multiple, it will only be scored for the one that would award the most points.

An IR report that demonstrates “hardening” (configuration) steps taken alone will not incur a point penalty, but it also won’t provide teams points, unless the hardening steps impacted a prior exploit or persistence mechanism. Hardening may help you in preventing a future attack but doesn’t need to be documented in an IR report.

IR reports will result in a point *deduction* (negative points) under the following conditions:

* The IR report is an exact duplicate from another competition round  
* The IR report clearly provides no value: eg. “we got nyan catted, no idea how”  
* The IR report wrongly attributes benign OS behaviour to a red team attack

# **Final Score**

In summary, teams are awarded negative points for each successful red team exploit in an attack narrative, which they can regain through an IR report. Teams are awarded positive points for each persistence removal accurately documented in an IR report.

The final raw red team scores may be positive or negative for each team. These scores will be normalized using [min-max normalization](https://en.wikipedia.org/wiki/Feature_scaling) to produce appropriately distributed values between 0 and 1\. These values are then uniformly multiplied so that the highest scoring team gets full points and the lowest scoring team gets 0 or another minimum, as decided by red team based on student performance.