---
title: '&lt;System.XML.serialization&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: e26a12facb92147d7660ae266ea5e1b090d7e198
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583776"
---
# <a name="ltsystemxmlserializationgt-element"></a>&lt;System.XML.serialization&gt; — Element
Element najwyższego poziomu do sterowania serializacji XML. Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<Konfiguracja >  
\<System.XML.serialization >  
  
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
|[\<dateTimeSerialization > — Element](../../../docs/standard/serialization/datetimeserialization-element.md)|Określa tryb serializacji <xref:System.DateTime> obiektów.|  
|[\<schemaImporterExtensions > — Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)|Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Konfiguracja > — Element](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Element główny w każdym pliku konfiguracyjnym, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób określić tryb serializacji <xref:System.DateTime> obiektu oraz dodanie typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów .NET Framework.  
  
```xml  
<system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
    <dateTimeSerialization mode = "Local" />  
    <schemaImporterExtensions>  
        <add   
        name = "MobileCapabilities"   
        type = "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neuutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.sxml.serialization>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<dateTimeSerialization > — Element](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [\<schemaImporterExtensions > — Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<Dodaj > elementu \<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)
