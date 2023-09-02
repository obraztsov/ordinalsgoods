# 🛠 Examples

```html
<!-- Example of the minimal valid DAO deploy inscription -->
<!DOCTYPE html>
<html>
    <head>
        <title>{}</title>
        <link rel="stylesheet" href="/content/53a495bffcc7a68bcc8cb0121e42f1304dae1aba08b76da1dfbc102b7c140440i0"/>
        <script id="goods" type="application/xml">
            <goods:deploy xmlns:goods="goods/1.0">
                <goods:name>{}</goods:name>
                <goods:id>{}</goods:id>
                <goods:addr>{}</goods:addr>
                <goods:burn>{}</goods:burn>
            </goods:deploy>
        </script>
    </head>
    <body>
        <!-- Link to the inscription with the DAO logo -->
        <img src="/content/{}"/>
    </body>
</html>

<!-- Example of the minimal valid product inscription -->
<!DOCTYPE html>
<html>
    <head>
        <title>{}</title>
        <link rel="stylesheet" href="/content/53a495bffcc7a68bcc8cb0121e42f1304dae1aba08b76da1dfbc102b7c140440i0"/>
        <script id="goods" type="application/xml">
            <goods:product xmlns:goods="goods/1.0" >
                <goods:dao>/content/{}</goods:dao>
                <goods:name>{}</goods:name>
                <goods:desc>{}</goods:desc>
	    </goods:product>
        </script>
    </head>
    <body>
        <!-- Link to the inscription with the product logo -->
        <img src="/content/{}"/>
    </body>
</html>

<!-- Example of the typical subscription inscription -->
<!DOCTYPE html>
<html>
    <head>
        <title>{}</title>
        <link rel="stylesheet" href="/content/53a495bffcc7a68bcc8cb0121e42f1304dae1aba08b76da1dfbc102b7c140440i0"/>
        <script id="goods" type="application/xml">
            <goods:subscription xmlns:goods="goods/1.0" >
                <goods:num>{}</goods:num>
                <goods:blk>{}</goods:blk>
	    </goods:subscription>
        </script>
    </head>
    <body>
        <!-- Link to the product inscription -->
        <iframe src="/content/{}"/>
    </body>
</html>

<!-- Example of the goods inscription tied to a subscription -->
<!DOCTYPE html>
<html>
    <head>
        <title>{}</title>
        <link rel="stylesheet" href="/content/53a495bffcc7a68bcc8cb0121e42f1304dae1aba08b76da1dfbc102b7c140440i0"/>
        <script id="goods" type="application/xml">
            <goods:item xmlns:goods="goods/1.0" >
                <goods:sub>/content/{}</goods:sub>
                <goods:num>{}</goods:sub>
	    </goods:item>
        </script>
    </head>
    <body>
        <!-- Link to the product inscription -->
        <iframe src="/content/{}"/>
    </body>
</html>

<!-- Example of the goods inscription not tied to a subscription -->
<!DOCTYPE html>
<html>
    <head>
        <title>{}</title>
        <link rel="stylesheet" href="/content/53a495bffcc7a68bcc8cb0121e42f1304dae1aba08b76da1dfbc102b7c140440i0"/>
        <script id="goods" type="application/xml">
            <goods:item xmlns:goods="goods/1.0" />
        </script>
    </head>
    <body>
        <!-- Link to the product inscription -->
        <iframe src="/content/{}"/>
    </body>
</html>

<!-- Example of the certificate inscription -->
<!DOCTYPE html>
<html>
    <head>
        <title>{}</title>
        <link rel="stylesheet" href="/content/53a495bffcc7a68bcc8cb0121e42f1304dae1aba08b76da1dfbc102b7c140440i0"/>
        <script id="goods" type="application/xml">
            <goods:cert xmlns:goods="/content/{}" />
                <goods:key>redeemed</goods:key>
            </goods:cert>
        </script>
    </head>
    <body>
        <!-- Link to the item inscription -->
        <iframe src="/content/{}"/>
    </body>
</html>
```
