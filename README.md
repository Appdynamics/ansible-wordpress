# Building

## Install Composer and dependencies

```bash
curl -sS https://getcomposer.org/installer | php -- --install-dir=bin
./bin/composer.phar update
```

## Install Box

```bash
cd bin
curl -LSs http://box-project.org/installer.php | php
cd ..
```

## Building the PHAR

```bash
./bin/box build
```

## Simple testing

1. Create a Ansible arguments file as Ansible would do. For anything complex, encode the value to JSON. Do not quote values, even if they contain spaces.

   ```bash
   echo 'host=www.hostname.of.the.site.com work_dir=/where-the-site-lives' > args
   ```

2. Run the PHAR:

   ```bash
   php wordpress.phar args
   ```
