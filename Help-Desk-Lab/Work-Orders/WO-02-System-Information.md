# WO-02 - Collect System Information

## Objective

Gather workstation hardware, operating system, and network information using PowerShell to verify the configuration of a newly deployed Windows 11 virtual machine.

---

## Ticket

A newly deployed Windows 11 workstation requires an inventory check to document the operating system, hardware specifications, storage, and network configuration.

---

## Environment

| Item | Value |
|------|------|
| Host Platform | VirtualBox |
| Operating System | Windows 11 Enterprise Evaluation |
| Computer Name | HELPDESK-PC01 |
| User | Maizel |

---

## Commands Used

### 1. Verify Computer Name

```powershell
hostname
```

**Result**

The workstation hostname is **HELPDESK-PC01**.

This confirms the computer has been properly renamed according to the organization's workstation naming convention.

---

### 2. Verify Operating System

```powershell
Get-ComputerInfo
```

**Result**

- Operating System: Windows 11 Enterprise Evaluation
- Display Version: 25H2
- Build Number: 26100
- Installation Type: Client
- BIOS: VirtualBox (UEFI)

The workstation is running the latest Windows 11 Enterprise Evaluation image inside a VirtualBox virtual machine.

---

### 3. Verify Processor

```powershell
Get-CimInstance Win32_Processor
```

**Result**

The workstation is configured with:

- Intel Core i9-9880H
- Base Clock Speed: 2.30 GHz

The virtual machine successfully recognizes the allocated processor.

---

### 4. Verify Installed Memory

```powershell
Get-CimInstance Win32_ComputerSystem
```

**Result**

Installed RAM:

- 4 GB (4,274,917,376 bytes)

The workstation has sufficient memory allocated for basic Windows administration and help desk exercises.

---

### 5. Verify Storage

```powershell
Get-Volume
```

**Result**

The workstation contains:

- Primary C: drive
- Approximately 63 GB total capacity
- Approximately 25 GB of free storage remaining

The Guest Additions ISO (D:) is also mounted as a virtual CD-ROM.

Storage health is reported as **Healthy**.

---

### 6. Verify Network Configuration

```powershell
ipconfig
```

**Result**

The workstation successfully obtained a network configuration.

- IPv4 Address: **10.0.2.15**
- Subnet Mask: **255.255.255.0**
- Default Gateway: **10.0.2.2**

This confirms the workstation has network connectivity through the VirtualBox NAT adapter.

---

### 7. Verify Network Adapter

```powershell
Get-NetAdapter
```

**Result**

Active Network Adapter:

- Intel PRO/1000 MT Desktop Adapter
- Status: **Up**
- Link Speed: **1 Gbps**

The network adapter is functioning normally.

---

## Verification

Successfully verified:

- Computer name
- Windows installation
- CPU
- Installed memory
- Storage
- IP configuration
- Network adapter status

All workstation components are functioning as expected.

---

## Lessons Learned

PowerShell provides a fast and efficient method for collecting workstation inventory information. Instead of navigating multiple Windows settings menus, system administrators can retrieve hardware, operating system, storage, and network details using a few commands. These commands are commonly used during workstation deployment, troubleshooting, and asset inventory.

---

## Skills Demonstrated

- Windows 11 Administration
- PowerShell
- Workstation Inventory
- System Verification
- Network Configuration
- Technical Documentation
