# Terraform GCP VM Lab

## Project Overview

This project provisions a hardened Linux Virtual Machine in Google Cloud Platform using Terraform. The goal is to demonstrate basic Infrastructure-as-Code practices together with simple server hardening. Terraform is used to automatically create and configure the VM, while security measures such as UFW and Fail2Ban are installed to reduce exposure to common attacks like brute-force login attempts. The repository shows how infrastructure can be reproducible, version controlled, and deployed consistently.

---

## How to Run the Project

Before running Terraform, make sure you have:

* Terraform installed
* Access to a Google Cloud project
* Authentication configured (`gcloud auth application-default login`)

Run the following commands inside the repository directory.

### 1. Initialize Terraform

```bash
terraform init
```

This downloads the required providers and prepares the working directory.

### 2. Review the Infrastructure Plan

```bash
terraform plan
```

Terraform will show what resources will be created or changed before applying them.

### 3. Apply the Configuration

```bash
terraform apply
```

Confirm with `yes` when prompted. Terraform will then create the VM in Google Cloud.

---

## CI/CD Pipeline Result

Below is a screenshot showing the pipeline successfully running and validating the Terraform configuration.

<img width="1545" height="480" alt="image" src="https://github.com/user-attachments/assets/760a95ba-6ea9-48d9-ad54-afd0aa665e85" />


## VM Running in Google Cloud

The screenshot below shows the created VM instance inside the Google Cloud Console.

*(Insert screenshot here)*

---

## Security Decisions

Several security choices were made to reduce risk and follow basic hardening practices.

### UFW (Uncomplicated Firewall)

UFW is used to restrict network access to the VM. Only necessary ports are opened (such as SSH). This reduces the attack surface by blocking unnecessary inbound traffic.

### Fail2Ban

Fail2Ban protects the server from brute-force login attempts. It monitors authentication logs and temporarily blocks IP addresses that repeatedly fail login attempts.

### Minimal Exposure

The VM only exposes required services and avoids unnecessary packages. Limiting installed software helps reduce potential vulnerabilities.

### Infrastructure as Code

Using Terraform ensures that infrastructure is defined in code and can be recreated consistently. This improves transparency, auditing, and repeatability of deployments.

---

## Summary

This lab demonstrates how Terraform can be used to provision a VM in Google Cloud while applying basic security hardening techniques. The project shows a simple workflow where infrastructure is created, validated through a pipeline, and deployed in a reproducible way.
