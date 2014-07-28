# Using this module as is

Copy `bin/wordpress` into your playbook's `library` directory. Invoke like any other module. You must uncomment the `_require_ansible_php()` function. And for all tasks you *must* specify the `ansible_php` key which is a path to where AnsiblePhp source code is.

See [ansible-php](https://github.com/Appdynamics/ansible-php#example-module) for more information.

# Using a PHAR file

## Not so fast

Wait for https://github.com/ansible/ansible/pull/6374 to get resolved completely.

## Building

### Install Composer and dependencies

```bash
curl -sS https://getcomposer.org/installer | php -- --install-dir=bin
./bin/composer.phar update
```

### Install Box

```bash
cd bin
curl -LSs http://box-project.org/installer.php | php
cd ..
```

### Building the PHAR

```bash
./bin/box build
```

### Simple local testing

1. Create a Ansible arguments file as Ansible would do. For anything complex, encode the value to JSON. Do not quote values, even if they contain spaces.

   ```bash
   echo 'host=www.hostname.of.the.site.com work_dir=/where-the-site-lives' > args
   ```

2. Run the PHAR:

   ```bash
   php wordpress.phar args
   ```
