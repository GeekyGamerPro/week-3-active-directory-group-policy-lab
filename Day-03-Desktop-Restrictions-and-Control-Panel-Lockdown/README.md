# Week 3 – Day 3: Desktop Restrictions and System Lockdown

## Objective
Implement Group Policy-based restrictions to control user access to system tools and desktop functionality.

---

## Environment
- DC01 (Domain Controller)
- CLIENT01 (Domain-joined machine)
- Domain: corp.geekytech.local

---

## Steps Completed

### 1. Created GPO
- Created new Group Policy Object:
  Desktop-Restrictions-GPO

---

### 2. Linked GPO
- Linked GPO to domain:
  corp.geekytech.local

---

### 3. Configured CMD Restriction
- Enabled "Prevent access to the command prompt"
- Disabled script processing

---

### 4. Disabled Run Command
- Enabled "Remove Run menu from Start Menu"

---

### 5. Disabled Task Manager
- Enabled "Remove Task Manager" policy

---

### 6. Applied Policy
- Ran `gpupdate /force` on CLIENT01

---

### 7. Validation Results
- Run command disabled (Win + R blocked)
- Command Prompt access denied with administrator message
- Task Manager access restricted
- Control Panel access previously blocked (Day 1 policy still active)

---

## Key Concepts Learned
- Endpoint security via Group Policy
- User interface restrictions
- Execution control (CMD and scripts)
- System tool lockdown techniques
- Centralized desktop environment management

---

## Outcome
Successfully implemented a full desktop restriction policy using Group Policy, demonstrating enterprise-level control over user environments in an Active Directory domain.