---
title: <schemaImporterExtensions> Element
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5ed80ac370e34d6b62bb2b601cb7bd978228a302
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159822"
---
# <a name="schemaimporterextensions-element"></a>\<element > schemaImporterExtensions
Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework. Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dodać > elementu \<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do tworzenia mapowań.|  
  
## <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<element > System. XML. Serialization](../../../docs/standard/serialization/system-xml-serialization-element.md)|Element najwyższego poziomu do sterowania serializacji XML.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje sposób dodawania typów, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD na typy .NET Framework.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<element > dateTimeSerialization](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<dodać > elementu \<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<element > System. XML. Serialization](../../../docs/standard/serialization/system-xml-serialization-element.md)
