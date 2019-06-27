---
title: <system.xml.serialization>, element
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 02027a238bc9a2f82963ea841584d2bb3c6446c6
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410545"
---
# <a name="systemxmlserialization-element"></a>\<system.xml.serialization> Element

Element najwyższego poziomu do sterowania serializacji XML. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).

\<Konfiguracja > \
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
|[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)|Określa tryb serializacji <xref:System.DateTime> obiektów.|
|[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)|Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<Konfiguracja > Element](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.|

## <a name="example"></a>Przykład

Poniższy przykład kodu przedstawia sposób określić tryb serializacji <xref:System.DateTime> obiektu i dodatkowych, używany przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów programu .NET Framework.

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
- [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<add> Element for \<schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
