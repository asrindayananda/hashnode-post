---
title: Create a database table in Magento 2
tags: software development, web development, magento, software engineering, coding
cover: https://images.unsplash.com/photo-1565791380713-1756b9a05343?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1760&q=80
domain: blog.azcodez.com
---
Below are steps I went though to create a new database table in Magento 2 / Adobe Commerce

## Create a module
You can add to your existing module or [follow this blog to create a module](https://blog.azcodez.com/magento-2-create-a-module-in-magento-2)

## Create a db schema 
- Refernce https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/db-schema.html
- Path will be similar path to this
app\code\AzCodez\CustomerViewing\etc\db_schema.xml

- Add this code to setup your table. Modify table names, columns, types to suit your own
```
<?xml version="1.0"?>
<!-- Database schema -->
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema. xsd">
    <table name="az_codez_followers" resource="default" engine="innodb" comment="Azcodez followers">
        <column xsi:type="int" name="follower_id" padding="19" unsigned="true" nullable="false" identity="true" comment="Follower id"/>
        <column xsi:type="text" name="name" nullable="false" comment="Follower Name"/>
        <column xsi:type="text" name="email" nullable="false" comment="Follower Contact"/>
        <constraint xsi:type="primary" referenceId="PRIMARY">
            <column name="follower_id"/>
        </constraint>
    </table>
</schema>
```

## Generate  generate db_schema_whitelist.json
```
docker-compose run --rm deploy magento-command setup:db-declaration:generate-whitelist
```

## Redeploy

## Find your table and see if it worked eg.
```
Select * From az_codez_followers;
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646408394493/fzvAB2a3I.png)

# Shameless Plugs 
- [Join me and invest commission-free with Freetrade. Get started with a free share worth £3-£200.](https://magic.freetrade.io/join/asrin/447192e9)
- [Start a blog on Hashnode](https://hashnode.com/@azcodez/joinme)
- [Transfer money internationally with Wise](https://wise.com/invite/ath/asrind)

# Credits
- [Header image](https://unsplash.com/photos/nME9TubZtSo)
- [Adobe Magento Commence Documentation](https://devdocs.magento.com)

Feel free to comment with questions or feedback✌️

Happy coding,

Az 👨🏾‍💻