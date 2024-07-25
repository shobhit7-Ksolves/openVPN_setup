# Installing and Configuring OpenVPN on an AWS Instance

## Introduction
OpenVPN is a robust and highly flexible VPN solution. This guide will walk you through the steps to install and configure OpenVPN on an AWS instance.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Launch an AWS Instance](#launch-an-aws-instance)
- [Connect to Your Instance](#connect-to-your-instance)
- [Install OpenVPN](#install-openvpn)
- [Configure OpenVPN](#configure-openvpn)
- [Start OpenVPN Service and Set Up Client Configurations](#start-openvpn-service-and-set-up-client-configurations)

## Prerequisites
- AWS account with necessary permissions to create and manage instances.
- Basic knowledge of AWS EC2 and SSH.


## Launch an AWS Instance

1. **Log in to your AWS Management Console.**
2. **Navigate to the EC2 Dashboard.**
3. **Click on 'Launch Instance'.**
4. **Choose an Amazon Machine Image (AMI):**
   - Select an Ubuntu Server (e.g., Ubuntu Server 20.04 LTS).
5. **Choose an Instance Type:**
   - A t2.micro instance type is sufficient for basic setups.
6. **Configure Instance Details:**
   - Ensure the instance is in the desired VPC and subnet.
   - Configure Auto-assign Public IP to 'Enable' if needed.
7. **Add Storage:**
   - The default settings are usually sufficient.
8. **Add Tags:**
   - Optionally add tags for easier identification.
9. **Configure Security Group:**
   - Add rules to allow SSH (port 22) and OpenVPN (port 1194).
10. **Review and Launch:**
    - Review your settings and click 'Launch'.
    - Select an existing key pair or create a new one to access your instance.

## Connect to Your Instance

1. **Download the Key Pair (if you created a new one).**
2. **Set permissions for the key file:**
```bash
chmod 400 your-key-pair.pem
```
3.Connect to your instance via SSH:
```bash
ssh -i "your-key-pair.pem" ubuntu@your-instance-public-dns
```

## Install OpenVPN

1. **Update your package list:**
```bash
sudo apt-get update
sudo apt-get upgrade
```

2. **Install OpenVPN**
```bash
bash <(curl -fsS https://as-repository.openvpn.net/as/install.sh)
```

3. **After installing the openvpn-as package, take note of the Admin UI and Client UI addresses as well as the randomly generated password for your administrative user openvpn.**
  These details will display on screen similar to this example:
