---
title: '&lt;dateTimeSerialization&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: cd275cdbc51c86b1d774058db839c38349b319a6
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597800"
---
# <a name="ltdatetimeserializationgt-element"></a><span data-ttu-id="eb1f3-102">&lt;dateTimeSerialization&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="eb1f3-102">&lt;dateTimeSerialization&gt; Element</span></span>
<span data-ttu-id="eb1f3-103">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="eb1f3-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="eb1f3-104">\<configuration></span></span>  
<span data-ttu-id="eb1f3-105">\<dateTimeSerialization ></span><span class="sxs-lookup"><span data-stu-id="eb1f3-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb1f3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb1f3-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb1f3-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eb1f3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="eb1f3-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb1f3-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eb1f3-109">Attributes</span></span>  
  
|<span data-ttu-id="eb1f3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eb1f3-110">Attributes</span></span>|<span data-ttu-id="eb1f3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="eb1f3-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="eb1f3-112">Parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-112">Optional.</span></span> <span data-ttu-id="eb1f3-113">Określa tryb serializacji.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-113">Specifies the serialization mode.</span></span> <span data-ttu-id="eb1f3-114">Jedną z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="eb1f3-115">Wartość domyślna to **komunikacja dwukierunkowa**.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb1f3-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eb1f3-116">Child Elements</span></span>  
 <span data-ttu-id="eb1f3-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb1f3-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eb1f3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="eb1f3-119">Element</span><span class="sxs-lookup"><span data-stu-id="eb1f3-119">Element</span></span>|<span data-ttu-id="eb1f3-120">Opis</span><span class="sxs-lookup"><span data-stu-id="eb1f3-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb1f3-121">System.XML.serialization</span><span class="sxs-lookup"><span data-stu-id="eb1f3-121">system.xml.serialization</span></span>|<span data-ttu-id="eb1f3-122">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb1f3-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb1f3-123">Remarks</span></span>  
 <span data-ttu-id="eb1f3-124">W wersjach 1.0, 1.1, 2.0 i nowszych wersjach programu .NET Framework, gdy ta właściwość ma wartość **lokalnego**, <xref:System.DateTime> obiekty są zawsze formatowane jako czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="eb1f3-125">Oznacza to, że informacje o strefie czas lokalny zawsze jest zawarte w danych serializacji.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="eb1f3-126">Ustaw tę właściwość na **lokalnego** zapewnienie zgodności z poprzednimi wersjami programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="eb1f3-127">W wersji 2.0 i nowszych wersjach .NET Framework, które mają tę właściwość ustawioną na **komunikacja dwukierunkowa**, <xref:System.DateTime> obiekty są sprawdzane w celu określenia, czy znajdują się w lokalnym, UTC lub nieokreślonej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="eb1f3-128"><xref:System.DateTime> Obiekty są następnie serializowany w taki sposób, że jest zachowywany tych informacji.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="eb1f3-129">To jest domyślne zachowanie i zalecane zachowania w przypadku wszystkich nowych aplikacji, które nie komunikują się ze starszymi wersjami programu framework.</span><span class="sxs-lookup"><span data-stu-id="eb1f3-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb1f3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb1f3-130">See also</span></span>

- <xref:System.DateTime>  
- <xref:System.Xml.Serialization.XmlSchemaImporter>  
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
- [<span data-ttu-id="eb1f3-131">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eb1f3-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="eb1f3-132">\<schemaImporterExtensions > Element</span><span class="sxs-lookup"><span data-stu-id="eb1f3-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
- [<span data-ttu-id="eb1f3-133">\<Dodaj >, Element dla \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="eb1f3-133">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)  
- [<span data-ttu-id="eb1f3-134">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="eb1f3-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
