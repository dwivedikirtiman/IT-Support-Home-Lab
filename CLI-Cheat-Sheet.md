```markdown
# IT Support Home Lab - Command Line & Scripting Reference

This repository asset serves as the dedicated technical documentation for the command-line overrides, programmatic automation scripts, and administrative shortcuts engineered during the provisioning and management of the `kdlab.local` sandbox infrastructure.

---

## 1. Automated OS Deployment & Bypasses

### Bypass Windows 11 Out-of-Box Experience (OOBE) Mandatory Requirements
During the initial staging of the workplace endpoint (`Client-01`), the operating system enforces mandatory internet connectivity and Microsoft Account authentication. This command modifies the registry session state to bypass these deployment gates.

* **Command:**
  ```cmd
  OOBE\BYPASSNRO

```

* **Execution Environment:** Windows Setup OOBE Administrative Command Prompt (accessed via `Shift + F10` during the network setup phase).
* **Technical Function:** Instructs the deployment engine to clear the mandatory network flag, forcing an immediate system restart and unlocking the option to provision a traditional offline local administrator profile.

---

## 2. Active Directory Identity Management

### Workstation-Side Programmatic Password Modification (ADSI Method)

To simulate real-world Tier 1 helpdesk workflows without installing heavy Active Directory management tools locally on an endpoint, this script leverages the Active Directory Service Interfaces (ADSI) provider over LDAP.

* **PowerShell Script:**
```powershell
$Searcher = [adsisearcher]"(&(objectCategory=user)(sAMAccountName=Rani))"
$User = $Searcher.FindOne().GetDirectoryEntry()$User.Invoke("SetPassword", "Dell@123456")

```


* **Execution Environment:** Elevated PowerShell console on `Client-01`, executing under an identity with explicitly delegated administrative rights over the target Organizational Unit.
* **Technical Function:** Initializes an LDAP directory searcher using a precise `sAMAccountName` filter. Once the object reference is located in the global catalog, it opens an unencrypted ADSI directory entry object and programmatically invokes the administrative password override API.

---

## 3. Centralized Policy Engineering

### Forced Client-Side Group Policy Update

When Group Policy Objects (GPOs) are created or modified on the Domain Controller, local endpoints do not ingest them immediately due to standard background propagation delays. This tool enforces instant compliance.

* **Command:**
```cmd
gpupdate /force

```


* **Execution Environment:** Standard Command Prompt or PowerShell terminal on any domain-joined endpoint or server.
* **Technical Function:** Triggers the local Group Policy engine to query the Active Directory SYSVOL share, download the latest registry templates, and immediately overwrite local machine and user-space policy hives without requiring a system logoff or reboot.

---

## 4. Network Layer Diagnostics

### ICMP Namespace Resolution Verification

Before execution of an Active Directory domain join, network paths must be verified across both Layer 3 (IP routing) and Layer 7 (DNS/Application name resolution).

* **Command:**
```cmd
ping kdlab.local

```


* **Execution Environment:** Client-side terminal interface.
* **Technical Function:** Transmits standard ICMP Echo Request packets to the string domain identifier. This forces the local network interface to query its configured primary DNS server (`192.168.56.10`), map the namespace string to the host IP, and verify continuous network line stability.

---

## 5. Administrative Console Run Shortcuts

These shortcut execution commands bypass multiple nested layers of the graphical user interface, allowing an IT systems administrator to rapidly launch management snap-ins directly via the Windows Run framework (`Win + R`) or an elevated terminal shell.

| Shortcut Execution String | Target Administrative Management Tool | Technical Scope of Operations |
| --- | --- | --- |
| `dsa.msc` | Active Directory Users and Computers | Provisioning user profiles, structural security groups, computer objects, and custom OUs. |
| `gpmc.msc` | Group Policy Management Console | Structuring, creating, modifying, and linking global GPO rules across specific directory containers. |
| `sysdm.cpl` | Advanced System Properties | Modifying local machine hostnames, managing system environment variables, and executing domain joins. |
| `compmgmt.msc` | Computer Management Console | Auditing local endpoint security groups, viewing system event logs, and managing storage drive configurations. |

```

```