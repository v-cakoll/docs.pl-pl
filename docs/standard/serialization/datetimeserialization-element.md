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
# <a name="datetimeserialization-element"></a><span data-ttu-id="a3139-103">\<dateTimeSerialization> Element</span><span class="sxs-lookup"><span data-stu-id="a3139-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="a3139-104">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a3139-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="a3139-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3139-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3139-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a3139-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a3139-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a3139-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3139-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a3139-108">Attributes</span></span>  
  
|<span data-ttu-id="a3139-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a3139-109">Attributes</span></span>|<span data-ttu-id="a3139-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a3139-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="a3139-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a3139-111">Optional.</span></span> <span data-ttu-id="a3139-112">Określa tryb serializacji.</span><span class="sxs-lookup"><span data-stu-id="a3139-112">Specifies the serialization mode.</span></span> <span data-ttu-id="a3139-113">Jedną z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="a3139-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="a3139-114">Wartość domyślna to **roundtrip**.</span><span class="sxs-lookup"><span data-stu-id="a3139-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3139-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a3139-115">Child Elements</span></span>  
 <span data-ttu-id="a3139-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="a3139-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3139-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a3139-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a3139-118">Element</span><span class="sxs-lookup"><span data-stu-id="a3139-118">Element</span></span>|<span data-ttu-id="a3139-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a3139-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3139-120">System.XML.serialization</span><span class="sxs-lookup"><span data-stu-id="a3139-120">system.xml.serialization</span></span>|<span data-ttu-id="a3139-121">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="a3139-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3139-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3139-122">Remarks</span></span>  
 <span data-ttu-id="a3139-123">W wersji 1,0, 1,1, 2,0 i nowszych wersji .NET Framework, gdy ta właściwość ma wartość **Local**, <xref:System.DateTime> obiekty są zawsze sformatowane jako czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="a3139-123">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="a3139-124">Oznacza to, że informacje o strefie czas lokalny zawsze jest zawarte w danych serializacji.</span><span class="sxs-lookup"><span data-stu-id="a3139-124">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="a3139-125">Ustaw tę właściwość na wartość **Local** , aby zapewnić zgodność ze starszymi wersjami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3139-125">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a3139-126">W wersji 2,0 i nowszych .NET Framework, dla których ta właściwość ma ustawioną wartość **roundtrip**, <xref:System.DateTime> obiekty są sprawdzane w celu określenia, czy znajdują się w lokalnej, UTC lub nieokreślonej strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="a3139-126">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="a3139-127"><xref:System.DateTime> Obiekty są następnie serializowany w taki sposób, że jest zachowywany tych informacji.</span><span class="sxs-lookup"><span data-stu-id="a3139-127">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="a3139-128">Jest to zachowanie domyślne i jest to zalecane zachowanie dla wszystkich nowych aplikacji, które nie komunikują się ze starszymi wersjami platformy.</span><span class="sxs-lookup"><span data-stu-id="a3139-128">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3139-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3139-129">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="a3139-130">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a3139-130">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a3139-131">\<schemaImporterExtensions>Postaci</span><span class="sxs-lookup"><span data-stu-id="a3139-131">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="a3139-132">\<add>Element dla\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="a3139-132">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="a3139-133">\<system.xml.serialization>Postaci</span><span class="sxs-lookup"><span data-stu-id="a3139-133">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
