---
title: <dateTimeSerialization>, element
description: W tym artykule opisano <dateTimeSerialization> element, który określa tryb serializacji obiektów DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289645"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="aff78-103">\<dateTimeSerialization>, element</span><span class="sxs-lookup"><span data-stu-id="aff78-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="aff78-104">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="aff78-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="aff78-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="aff78-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aff78-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aff78-106">Attributes and Elements</span></span>  
 <span data-ttu-id="aff78-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aff78-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aff78-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aff78-108">Attributes</span></span>  
  
|<span data-ttu-id="aff78-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aff78-109">Attributes</span></span>|<span data-ttu-id="aff78-110">Opis</span><span class="sxs-lookup"><span data-stu-id="aff78-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="aff78-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="aff78-111">Optional.</span></span> <span data-ttu-id="aff78-112">Określa tryb serializacji.</span><span class="sxs-lookup"><span data-stu-id="aff78-112">Specifies the serialization mode.</span></span> <span data-ttu-id="aff78-113">Jedną z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="aff78-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="aff78-114">Wartość domyślna to **roundtrip**.</span><span class="sxs-lookup"><span data-stu-id="aff78-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aff78-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aff78-115">Child Elements</span></span>  
 <span data-ttu-id="aff78-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="aff78-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aff78-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aff78-117">Parent Elements</span></span>  
  
|<span data-ttu-id="aff78-118">Element</span><span class="sxs-lookup"><span data-stu-id="aff78-118">Element</span></span>|<span data-ttu-id="aff78-119">Opis</span><span class="sxs-lookup"><span data-stu-id="aff78-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aff78-120">System.XML.serialization</span><span class="sxs-lookup"><span data-stu-id="aff78-120">system.xml.serialization</span></span>|<span data-ttu-id="aff78-121">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="aff78-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aff78-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aff78-122">Remarks</span></span>  
 <span data-ttu-id="aff78-123">W wersji 1,0, 1,1, 2,0 i nowszych wersji .NET Framework, gdy ta właściwość ma wartość **Local**, <xref:System.DateTime> obiekty są zawsze sformatowane jako czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="aff78-123">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="aff78-124">Oznacza to, że informacje o strefie czas lokalny zawsze jest zawarte w danych serializacji.</span><span class="sxs-lookup"><span data-stu-id="aff78-124">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="aff78-125">Ustaw tę właściwość na wartość **Local** , aby zapewnić zgodność ze starszymi wersjami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aff78-125">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="aff78-126">W wersji 2,0 i nowszych .NET Framework, dla których ta właściwość ma ustawioną wartość **roundtrip**, <xref:System.DateTime> obiekty są sprawdzane w celu określenia, czy znajdują się w lokalnej, UTC lub nieokreślonej strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="aff78-126">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="aff78-127"><xref:System.DateTime> Obiekty są następnie serializowany w taki sposób, że jest zachowywany tych informacji.</span><span class="sxs-lookup"><span data-stu-id="aff78-127">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="aff78-128">Jest to zachowanie domyślne i jest to zalecane zachowanie dla wszystkich nowych aplikacji, które nie komunikują się ze starszymi wersjami platformy.</span><span class="sxs-lookup"><span data-stu-id="aff78-128">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff78-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aff78-129">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="aff78-130">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="aff78-130">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="aff78-131">\<schemaImporterExtensions>Postaci</span><span class="sxs-lookup"><span data-stu-id="aff78-131">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="aff78-132">\<add>Element dla\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="aff78-132">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="aff78-133">\<system.xml.serialization>Postaci</span><span class="sxs-lookup"><span data-stu-id="aff78-133">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
