---
title: <schemaImporterExtensions>, element
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 43f8439708c73e8e5241a923360caf549bf09d8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017970"
---
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions> Element
Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add> Element for \<schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> można utworzyć mapowania.|  
  
## <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)|Element najwyższego poziomu do sterowania serializacji XML.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób dodawania typów, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów programu .NET Framework.  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<add> Element for \<schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)
