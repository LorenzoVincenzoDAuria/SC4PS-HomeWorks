# SC4PS-HomeWorks
This repo contains homeworks and codes from Scientific Computing for Physics Student PhD course at Unviersity of Padova

# Guide: Setting Up a Linux Machine on CloudVeneto for C/C++

This guide outlines the steps required to configure a Linux virtual machine (Debian/Ubuntu-based) hosted on CloudVeneto to compile and run C code.

## 1. Prerequisites
* An active virtual machine on [CloudVeneto](https://cloudveneto.it/).
* The public IP address of your instance.
* The private key file (`.pem` or `id_rsa`) for SSH access.

## 2. Accessing the Virtual Machine
Open your terminal (or PowerShell on Windows) and connect to the machine via SSH:

```bash
# Replace the path and IP address with your actual data
ssh -i /path/to/your/key.pem ubuntu@<CLOUDVENETO_IP_ADDRESS>
```

> **Note:** If your machine uses a different operating system, the default user might be `centos`, `debian`, or `fedora` instead of `ubuntu`.

## 3. Updating the System
Once logged into the virtual machine, it is a best practice to update the package lists and upgrade the system before installing new software:

```bash
sudo apt update
sudo apt upgrade -y
```

## 4. Installing the C Compiler (GCC)
To compile C code on Linux, you need the `build-essential` package. This will install the `gcc` compiler, the `make` tool, and other standard libraries:

```bash
sudo apt install build-essential -y
```

To verify that the installation was successful, check the installed version of GCC:

```bash
gcc --version
```

## 5. Writing Your First C Program
The environment is now ready. Let's create a test file using a terminal text editor, such as `nano`:

```bash
nano hello.c
```

Inside the editor, type the following simple program:

```c
#include <stdio.h>

int main() {
    printf("Hello CloudVeneto! The C setup is working.\n");
    return 0;
}
```
Save the file and exit the editor (in `nano`: press `CTRL+O`, `Enter`, then `CTRL+X`).

## 6. Compilation and Execution
Compile the `hello.c` source file to create an executable named `hello`:

```bash
gcc hello.c -o hello
```

Finally, run the executable:

```bash
./hello
```
If you see the greeting message printed on your screen, your machine is correctly configured!
