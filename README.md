`dimmaryanto93.oracle_java`
=========

Repository ini digunakan untuk menginstall [Oracle JDK](https://www.oracle.com/java/technologies/java-se-glance.html) 11 atau terbaru untuk Linux

Support platform

- Debian
- Ubuntu
- CentOS


Ansible - User Guide
------------

Persiapan yang harus di lalukan, diantaranya

1. Create new user on your server, Recomend using **very-very Strong Password** or using password generator. 
  ```bash
  adduser <username>
  ```

2. Granted to sudoers with NOPASSWD, using `visudo`
  ```ini
  username    ALL=(ALL) NOPASSWD:ALL
  ```

3. Authenticate with private-key for login ssh, generate ssh key on your local machine then use `ssh-copy-id user@your-ip-server` to copy public key to your server.


Requirements
------------

Untuk menggunakan role ini, kita membutuhkan Installer/package oracle jdk itu sendiri. kita perlu download dari [official website oracle](https://www.oracle.com/java/technologies/downloads/)

Setelah kita download, misalnya nama filenya `jdk-11.0.12_linux-x64_bin.rpm` sekarang kita simpan dalam folder `files` dalam strusture project ansible roles anda. sebagai contoh seperti berikut:

```bash
➜  ansible-role-oracle-java git:(master) tree .
.
├── README.md
├── files
│   └── jdk-11.0.12_linux-x64_bin.rpm
├── tests
│   ├── inventory
│   └── test.yml
└── vars
```

Role Variables
--------------

Ada beberapa variable yang temen-temen bisa gunakan untuk install oracle jdk, diantaranya seperti berikut:

| Variable name          | Example value | Description |
| :---                   | :---          | :---        |
| `oracle_java_version`  | `11.0.12`     | Variable digunakan untuk menginstall version ter-tentu dari oracle jdk |

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```ansible
- hosts: ["all"]
  become: true
  roles: 
    - role: dimmaryanto93.oracle_java
      vars: 
      ## specify your jdk version here!
        oracle_java_version: '11.0.12'
```

License
-------

MIT
