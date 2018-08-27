---
title: '&lt;System.XML.serialization&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: bf84c412c2d5e3c75cfdc752eeb70239f23d9245
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933832"
---
# <a name="ltsystemxmlserializationgt-element"></a><span data-ttu-id="54a52-102">&lt;System.XML.serialization&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="54a52-102">&lt;system.xml.serialization&gt; Element</span></span>
<span data-ttu-id="54a52-103">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="54a52-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="54a52-104">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="54a52-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="54a52-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="54a52-105">\<configuration></span></span>  
<span data-ttu-id="54a52-106">\<System.XML.serialization ></span><span class="sxs-lookup"><span data-stu-id="54a52-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54a52-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="54a52-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54a52-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="54a52-108">Attributes and Elements</span></span>  
 <span data-ttu-id="54a52-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="54a52-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54a52-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="54a52-110">Attributes</span></span>  
 <span data-ttu-id="54a52-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="54a52-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54a52-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="54a52-112">Child Elements</span></span>  
  
|<span data-ttu-id="54a52-113">Element</span><span class="sxs-lookup"><span data-stu-id="54a52-113">Element</span></span>|<span data-ttu-id="54a52-114">Opis</span><span class="sxs-lookup"><span data-stu-id="54a52-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54a52-115">\<dateTimeSerialization > Element</span><span class="sxs-lookup"><span data-stu-id="54a52-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="54a52-116">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="54a52-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|[<span data-ttu-id="54a52-117">\<schemaImporterExtensions > Element</span><span class="sxs-lookup"><span data-stu-id="54a52-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="54a52-118">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54a52-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54a52-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="54a52-119">Parent Elements</span></span>  
  
|<span data-ttu-id="54a52-120">Element</span><span class="sxs-lookup"><span data-stu-id="54a52-120">Element</span></span>|<span data-ttu-id="54a52-121">Opis</span><span class="sxs-lookup"><span data-stu-id="54a52-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54a52-122">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="54a52-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="54a52-123">Element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54a52-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="54a52-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="54a52-124">Example</span></span>  
 <span data-ttu-id="54a52-125">Poniższy przykład kodu przedstawia sposób określić tryb serializacji <xref:System.DateTime> obiektu i dodatkowych, używany przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54a52-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54a52-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54a52-126">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="54a52-127">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="54a52-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="54a52-128">\<dateTimeSerialization > Element</span><span class="sxs-lookup"><span data-stu-id="54a52-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="54a52-129">\<schemaImporterExtensions > Element</span><span class="sxs-lookup"><span data-stu-id="54a52-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [<span data-ttu-id="54a52-130">\<Dodaj >, Element dla \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="54a52-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
