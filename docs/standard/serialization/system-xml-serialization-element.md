---
title: <system.xml.serialization>, element
description: W tym artykule opisano element < System. XML. Serialization >, który jest elementem najwyższego poziomu służącego do kontrolowania serializacji XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: f69e80592e9321de64421b977a63b83d8be2ad9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289489"
---
# <a name="systemxmlserialization-element"></a>\<system.xml.serialization> Element

Element najwyższego poziomu do sterowania serializacji XML. Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../framework/configure-apps/file-schema/index.md).

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a>Składnia

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<dateTimeSerialization>Postaci](datetimeserialization-element.md)|Określa tryb serializacji <xref:System.DateTime> obiektów.|
|[\<schemaImporterExtensions>Postaci](schemaimporterextensions-element.md)|Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<configuration>Postaci](../../framework/configure-apps/file-schema/configuration-element.md)|Element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje sposób określania trybu serializacji <xref:System.DateTime> obiektu i dodawania typów używanych przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD na typy .NET Framework.

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schemat pliku konfiguracji](../../framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization>Postaci](datetimeserialization-element.md)
- [\<schemaImporterExtensions>Postaci](schemaimporterextensions-element.md)
- [\<add>Element dla\<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
