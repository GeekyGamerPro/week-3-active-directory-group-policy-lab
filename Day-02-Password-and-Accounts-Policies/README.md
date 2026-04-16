# Week 3 – Day 2: Password and Account Lockout Policies

## Objective
Configure and enforce domain-wide password and account lockout policies using Group Policy.

---

## Environment
- DC01 (Domain Controller)
- CLIENT01 (Domain-joined machine)
- Domain: corp.geekytech.local

---

## Steps Completed

### 1. Opened Default Domain Policy
- Accessed Group Policy Management Console (GPMC)
- Opened Default Domain Policy for editing

---

### 2. Configured Password Policy
- Set Minimum password length to 8 characters  
- Enabled password complexity requirements  
- Set Maximum password age to 30 days  

---

### 3. Configured Account Lockout Policy
- Set account lockout threshold to 5 failed attempts  
- Set lockout duration to 15 minutes  
- Set reset counter to 15 minutes  

---

### 4. Applied Policy on Client Machine
- Ran `gpupdate /force` on CLIENT01  

---

### 5. Validation Test
- Attempted multiple failed logins  
- Account successfully locked after 5 attempts  
- Verified lockout enforcement message  

---

## Key Concepts Learned
- Domain-level password policy enforcement  
- Account lockout as a security control  
- Protection against brute-force attacks  
- Centralized authentication management via GPO  
- Policy validation through real login testing  

---

## Outcome
Successfully implemented and validated domain-wide password and account lockout policies, ensuring secure authentication practices within the Active Directory environment.