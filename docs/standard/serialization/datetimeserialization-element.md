---
title: <dateTimeSerialization> Element
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 180a4942dd4b701b56fe4788d5f8cd8607faaedd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459262"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="a9295-102">\<element > dateTimeSerialization</span><span class="sxs-lookup"><span data-stu-id="a9295-102">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="a9295-103">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a9295-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="a9295-104">> konfiguracji \<</span><span class="sxs-lookup"><span data-stu-id="a9295-104">\<configuration></span></span>  
<span data-ttu-id="a9295-105">\<dateTimeSerialization ></span><span class="sxs-lookup"><span data-stu-id="a9295-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9295-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9295-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9295-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a9295-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a9295-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a9295-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9295-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a9295-109">Attributes</span></span>  
  
|<span data-ttu-id="a9295-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a9295-110">Attributes</span></span>|<span data-ttu-id="a9295-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a9295-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="a9295-112">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a9295-112">Optional.</span></span> <span data-ttu-id="a9295-113">Określa tryb serializacji.</span><span class="sxs-lookup"><span data-stu-id="a9295-113">Specifies the serialization mode.</span></span> <span data-ttu-id="a9295-114">Jedną z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="a9295-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="a9295-115">Wartość domyślna to **roundtrip**.</span><span class="sxs-lookup"><span data-stu-id="a9295-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9295-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a9295-116">Child Elements</span></span>  
 <span data-ttu-id="a9295-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="a9295-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9295-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a9295-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a9295-119">Element</span><span class="sxs-lookup"><span data-stu-id="a9295-119">Element</span></span>|<span data-ttu-id="a9295-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a9295-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9295-121">System.XML.serialization</span><span class="sxs-lookup"><span data-stu-id="a9295-121">system.xml.serialization</span></span>|<span data-ttu-id="a9295-122">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="a9295-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9295-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9295-123">Remarks</span></span>  
 <span data-ttu-id="a9295-124">W wersji 1,0, 1,1, 2,0 i nowszych wersji .NET Framework, gdy ta właściwość ma wartość **Local**, obiekty <xref:System.DateTime> są zawsze sformatowane jako czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="a9295-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="a9295-125">Oznacza to, że informacje o strefie czas lokalny zawsze jest zawarte w danych serializacji.</span><span class="sxs-lookup"><span data-stu-id="a9295-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="a9295-126">Ustaw tę właściwość na wartość **Local** , aby zapewnić zgodność ze starszymi wersjami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9295-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a9295-127">W wersji 2,0 i nowszych .NET Framework, dla których ta właściwość ma ustawioną wartość **roundtrip**, <xref:System.DateTime> obiekty są badane w celu określenia, czy znajdują się one w lokalnej, UTC lub w nieokreślonej strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="a9295-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="a9295-128"><xref:System.DateTime> Obiekty są następnie serializowany w taki sposób, że jest zachowywany tych informacji.</span><span class="sxs-lookup"><span data-stu-id="a9295-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="a9295-129">Jest to zachowanie domyślne i jest to zalecane zachowanie dla wszystkich nowych aplikacji, które nie komunikują się ze starszymi wersjami platformy.</span><span class="sxs-lookup"><span data-stu-id="a9295-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9295-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9295-130">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="a9295-131">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a9295-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a9295-132">\<element > schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="a9295-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="a9295-133">\<dodać > elementu \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="a9295-133">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="a9295-134">\<element > System. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="a9295-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
