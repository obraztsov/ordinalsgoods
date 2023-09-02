# 🖥 Schema specification

{% hint style="info" %}
Schemas are deployed to Ordinals protocol as an XSD document, that should be referenced by all protocol inscriptions
{% endhint %}

Inscription id acts in fact as a version of the protocol and is required in every inscription. The protocol's indexer tracks only inscriptions of the protocols it supports.

<table><thead><tr><th width="192">Version</th><th>Inscription id</th><th data-hidden></th></tr></thead><tbody><tr><td>goods/1.0</td><td>52714953ebbcf3126a4e25ed0e7c6d0136d7ec3624c106bf43b72a667331f794i0</td><td></td></tr></tbody></table>

## XSD document

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema
   xmlns:xsd="http://www.w3.org/2001/XMLSchema"
   targetNamespace="goods/1.0"
   elementFormDefault="qualified">
   <xsd:element name="deploy">
      <xsd:complexType>
         <xsd:sequence>
            <xsd:element name="name" type="xsd:string"/>
            <xsd:element name="id" type="xsd:string"/>
            <xsd:element name="addr" type="xsd:string"/>
            <xsd:element name="burn" type="xsd:string"/>
            <xsd:element name="url" type="xsd:string" minOccurs="0"/>
         </xsd:sequence>
     </xsd:complexType>
   </xsd:element>
   <xsd:element name="product">
      <xsd:complexType>
         <xsd:sequence>
            <xsd:element name="dao" type="xsd:string"/>
            <xsd:element name="parent" type="xsd:string" minOccurs="0"/>
            <xsd:element name="name" type="xsd:string"/>
            <xsd:element name="desc" type="xsd:string"/>
            <xsd:element name="burn" type="xsd:boolean" minOccurs="0" default="true"/>
            <xsd:element name="redeemable" type="xsd:boolean" minOccurs="0" default="true"/>
            <xsd:element name="weight" type="xsd:integer" minOccurs="0" default="1"/>
            <xsd:element name="url" type="xsd:string" minOccurs="0"/>
         </xsd:sequence>
     </xsd:complexType>
   </xsd:element>
   <xsd:element name="subscription">
      <xsd:complexType>
         <xsd:sequence>
            <xsd:element name="num" type="xsd:integer"/>
            <xsd:element name="blk" type="xsd:integer"/>
            <xsd:element name="blt" type="xsd:integer" minOccurs="0"/>
            <xsd:element name="lvl" type="xsd:integer" minOccurs="0" default="0"/>
         </xsd:sequence>
     </xsd:complexType>
   </xsd:element>
   <xsd:element name='item'>
      <xsd:complexType>
         <xsd:sequence>
            <xsd:element name="sub" type="xsd:string" minOccurs="0"/>
            <xsd:element name="num" type="xsd:integer" minOccurs="0" default="1"/>
         </xsd:sequence>
     </xsd:complexType>
   </xsd:element>
   <xsd:element name='cert'>
      <xsd:complexType>
         <xsd:sequence>
            <xsd:element name="type" type="xsd:string" minOccurs="0"/>
            <xsd:element name="key" type="xsd:string" minOccurs="1"/>
            <xsd:element name="v" type="xsd:string" minOccurs="0"/>
         </xsd:sequence>
     </xsd:complexType>
   </xsd:element>
</xsd:schema>
```
