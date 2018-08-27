---
title: '&lt;dateTimeSerialization&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 15fad472288a72a079991f41e6c2859776d78cca
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930090"
---
# <a name="ltdatetimeserializationgt-element"></a>&lt;dateTimeSerialization&gt; — Element
Określa tryb serializacji <xref:System.DateTime> obiektów.  
  
 \<Konfiguracja >  
\<dateTimeSerialization >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybuty|Opis|  
|----------------|-----------------|  
|`mode`|Parametr opcjonalny. Określa tryb serializacji. Jedną z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> wartości. Wartość domyślna to **komunikacja dwukierunkowa**.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|System.XML.serialization|Element najwyższego poziomu do sterowania serializacji XML.|  
  
## <a name="remarks"></a>Uwagi  
 W wersjach 1.0, 1.1, 2.0 i nowszych wersjach programu .NET Framework, gdy ta właściwość ma wartość **lokalnego**, <xref:System.DateTime> obiekty są zawsze formatowane jako czas lokalny. Oznacza to, że informacje o strefie czas lokalny zawsze jest zawarte w danych serializacji. Ustaw tę właściwość na **lokalnego** zapewnienie zgodności z poprzednimi wersjami programu .NET Framework.  
  
 W wersji 2.0 i nowszych wersjach .NET Framework, które mają tę właściwość ustawioną na **komunikacja dwukierunkowa**, <xref:System.DateTime> obiekty są sprawdzane w celu określenia, czy znajdują się w lokalnym, UTC lub nieokreślonej strefy czasowej. <xref:System.DateTime> Obiekty są następnie serializowany w taki sposób, że jest zachowywany tych informacji. To jest domyślne zachowanie i zalecane zachowania w przypadku wszystkich nowych aplikacji, które nie komunikują się ze starszymi wersjami programu framework.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.DateTime>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<schemaImporterExtensions > Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<Dodaj >, Element dla \<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)  
 [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)
