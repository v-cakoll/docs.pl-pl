---
title: <dateTimeSerialization>, element
description: W tym artykule opisano <dateTimeSerialization> element, który określa tryb serializacji obiektów DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375822"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="a1eb5-103">\<dateTimeSerialization, element></span><span class="sxs-lookup"><span data-stu-id="a1eb5-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="a1eb5-104">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="a1eb5-105">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a1eb5-105">\<configuration></span></span>  
<span data-ttu-id="a1eb5-106">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="a1eb5-106">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1eb5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1eb5-107">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1eb5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a1eb5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a1eb5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1eb5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a1eb5-110">Attributes</span></span>  
  
|<span data-ttu-id="a1eb5-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a1eb5-111">Attributes</span></span>|<span data-ttu-id="a1eb5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a1eb5-112">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="a1eb5-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-113">Optional.</span></span> <span data-ttu-id="a1eb5-114">Określa tryb serializacji.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-114">Specifies the serialization mode.</span></span> <span data-ttu-id="a1eb5-115">Jedną z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-115">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="a1eb5-116">Wartość domyślna to **roundtrip**.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-116">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1eb5-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a1eb5-117">Child Elements</span></span>  
 <span data-ttu-id="a1eb5-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1eb5-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a1eb5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a1eb5-120">Element</span><span class="sxs-lookup"><span data-stu-id="a1eb5-120">Element</span></span>|<span data-ttu-id="a1eb5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="a1eb5-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1eb5-122">System.XML.serialization</span><span class="sxs-lookup"><span data-stu-id="a1eb5-122">system.xml.serialization</span></span>|<span data-ttu-id="a1eb5-123">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-123">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1eb5-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1eb5-124">Remarks</span></span>  
 <span data-ttu-id="a1eb5-125">W wersji 1,0, 1,1, 2,0 i nowszych wersji .NET Framework, gdy ta właściwość ma wartość **Local**, <xref:System.DateTime> obiekty są zawsze sformatowane jako czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-125">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="a1eb5-126">Oznacza to, że informacje o strefie czas lokalny zawsze jest zawarte w danych serializacji.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-126">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="a1eb5-127">Ustaw tę właściwość na wartość **Local** , aby zapewnić zgodność ze starszymi wersjami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-127">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a1eb5-128">W wersji 2,0 i nowszych .NET Framework, dla których ta właściwość ma ustawioną wartość **roundtrip**, <xref:System.DateTime> obiekty są sprawdzane w celu określenia, czy znajdują się w lokalnej, UTC lub nieokreślonej strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-128">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="a1eb5-129"><xref:System.DateTime> Obiekty są następnie serializowany w taki sposób, że jest zachowywany tych informacji.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-129">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="a1eb5-130">Jest to zachowanie domyślne i jest to zalecane zachowanie dla wszystkich nowych aplikacji, które nie komunikują się ze starszymi wersjami platformy.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-130">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1eb5-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1eb5-131">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="a1eb5-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a1eb5-132">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a1eb5-133">\<schemaImporterExtensions, element></span><span class="sxs-lookup"><span data-stu-id="a1eb5-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="a1eb5-134">\<Dodaj element> dla \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="a1eb5-134">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="a1eb5-135">\<Element> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="a1eb5-135">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
