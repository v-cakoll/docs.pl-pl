---
title: '&lt;schemaImporterExtensions&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c9f4f6800c2718c3b2c2b9b5b2b6d97e1114dbcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581332"
---
# <a name="ltschemaimporterextensionsgt-element"></a>&lt;schemaImporterExtensions&gt; — Element
Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework. Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dodaj > elementu \<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> można utworzyć mapowania.|  
  
## <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)|Element najwyższego poziomu do sterowania serializacji XML.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób dodawania typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów .NET Framework.  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<dateTimeSerialization > — Element](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [\<Dodaj > elementu \<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)
