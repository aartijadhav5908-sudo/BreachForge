# Day 08 — Understanding Cause and Effect in Security
## Scenario 1 - Shared Password
### Problem

Several employees are using the same password to access an important company account. This means multiple people have access through one shared login.

### Possible Underlying Cause

The organization may not be providing separate accounts for each employee, or employees may not be following a proper password-sharing policy.

### Possible Result

If the password is exposed, unauthorized people could potentially access the account. It would also be difficult to identify which employee performed a particular action.

### Basic Prevention

Give each employee their own account and make sure passwords are not shared. Using multi-factor authentication can also provide an additional layer of protection.

## Scenario 2 - Unnecessary Access
### Problem

An employee has changed their role but still has access to systems and information that are no longer needed for their new responsibilities.

### Possible Underlying Cause

The organization may not have a proper process for reviewing and updating employee access when their roles change.

### Possible Result

The employee could accidentally or intentionally access information that they are no longer supposed to use. Unnecessary access can increase the risk of sensitive information being exposed or misused.

### Basic Prevention

Review user permissions whenever an employee changes roles and remove access that is no longer required. Access should be given based on the employee's current responsibilities.

## Scenario 3 - Ignored Updates
### Problem

The company has delayed important software updates for a long period of time.

### Possible Underlying Cause

The organization may not have a regular patch management process, or updates may be postponed because of concerns about downtime or compatibility.

### Possible Result

The software may continue to contain known security weaknesses. If those weaknesses are exploited, attackers could potentially gain unauthorized access or affect the company's systems.

### Basic Prevention

Keep software and operating systems updated regularly. The company should have a process for identifying important security updates and applying them in a timely manner.

## Scenario 4 - Public Information
### Problem

Internal company documents have accidentally been made accessible to everyone instead of only authorized employees.

### Possible Underlying Cause

The access permissions or sharing settings were configured incorrectly.

### Possible Result

Unauthorized people could view or download information that was intended to remain internal. This could lead to the exposure of sensitive company information.

### Basic Prevention

Review access permissions carefully and make sure internal documents are restricted to the people who actually need them. Regular permission reviews can also help detect accidental public access.

## Scenario 5 - Unknown Email
### Problem

An employee opens an unexpected email attachment without checking who sent it or whether the attachment is safe.

### Possible Underlying Cause

The employee may not have received enough security awareness training, or the organization may not have strong procedures for handling suspicious emails and attachments.

### Possible Result

The attachment could contain malicious content that may put the employee's device or company information at risk.

### Basic Prevention

Employees should verify unexpected emails and avoid opening suspicious attachments. Organizations should also provide regular phishing and security awareness training and use appropriate email security controls.

## What I Learned

From this task, I learned that a security problem and its root cause are not always the same thing. The problem describes what is happening, while the underlying cause helps explain why it happened.

I also learned that identifying the cause is important because simply fixing the visible problem may not prevent it from happening again. For example, removing unnecessary access from one account is useful, but having a proper access-review process is a better long-term solution.

Another important lesson is that we should not assume a root cause without evidence. In real security research, the cause should be treated as a possibility until it can be supported by reliable information or an authorized investigation.

Overall, this exercise helped me understand how to look at security situations in terms of problem -> cause -> result -> prevention and how basic security controls can reduce risk.
