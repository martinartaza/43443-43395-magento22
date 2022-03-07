# Patch for bug 43443 - 43395 to magento 2.2.*
For the following bugs 

https://support.magento.com/hc/en-us/articles/4426353041293-Security-updates-available-for-Adobe-Commerce-APSB22-12-

To use the automated patch system, update your magento root project's `composer.json`:

**Step 1.** Add the following to the requires node:

```json
     "require": {
        // ...
        "cweagans/composer-patches": "^1.7"
        // ...
    },
```

**Step 2.** Add the `extra`, with setting and `patcher` with the module `magento/module-email` for example:  

```json
     "extra": {
        // ...
        "enable-patching": true,
        "magento-force": "override",
        "composer-exit-on-patch-failure": true,
        "patches": {
            "magento/module-email": {
                "Apply MDVA-43443-43395": "patches/MDVA-43443-43395-CE22.patch"
            }
        }
    }
```

**Step 3.** In your root folder magento add folder patches `patches` :

**Step 4.** Test locally: `composer install` first time install plugin `cweagans/composer-patches` again `composer install` install patch.

```text
Gathering patches for dependencies. This might take a minute.
  - Installing magento/module-email (100.2.2): Downloading (100%)         
  - Applying patches for magento/module-email
    patches/MDVA-43443-43395-CE22.patch (Apply MDVA-43443-43395)

```

**Done!**

