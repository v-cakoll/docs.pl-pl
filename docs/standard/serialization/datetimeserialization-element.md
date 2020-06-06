---
title: <dateTimeSerialization> Element
description: W tym artykule opisano <dateTimeSerialization> element, który określa tryb serializacji obiektów DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289645"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization> Element
Określa tryb serializacji <xref:System.DateTime> obiektów.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybuty|Opis|  
|----------------|-----------------|  
|`mode`|Opcjonalny. Określa tryb serializacji. Jedną z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> wartości. Wartość domyślna to **roundtrip**.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|System.XML.serialization|Element najwyższego poziomu do sterowania serializacji XML.|  
  
## <a name="remarks"></a>Uwagi  
 W wersji 1,0, 1,1, 2,0 i nowszych wersji .NET Framework, gdy ta właściwość ma wartość **Local**, <xref:System.DateTime> obiekty są zawsze sformatowane jako czas lokalny. Oznacza to, że informacje o strefie czas lokalny zawsze jest zawarte w danych serializacji. Ustaw tę właściwość na wartość **Local** , aby zapewnić zgodność ze starszymi wersjami .NET Framework.  
  
 W wersji 2,0 i nowszych .NET Framework, dla których ta właściwość ma ustawioną wartość **roundtrip**, <xref:System.DateTime> obiekty są sprawdzane w celu określenia, czy znajdują się w lokalnej, UTC lub nieokreślonej strefie czasowej. <xref:System.DateTime> Obiekty są następnie serializowany w taki sposób, że jest zachowywany tych informacji. Jest to zachowanie domyślne i jest to zalecane zachowanie dla wszystkich nowych aplikacji, które nie komunikują się ze starszymi wersjami platformy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schemat pliku konfiguracji](../../framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions>Postaci](schemaimporterextensions-element.md)
- [\<add>Element dla\<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization>Postaci](system-xml-serialization-element.md)
