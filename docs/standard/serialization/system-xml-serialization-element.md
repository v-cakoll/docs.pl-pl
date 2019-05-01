---
title: <system.xml.serialization>, element
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: f41e3811fc6bab8a354f75f46b0ac79c0ce42f99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018089"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="e1e23-102">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="e1e23-102">\<system.xml.serialization> Element</span></span>
<span data-ttu-id="e1e23-103">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="e1e23-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="e1e23-104">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="e1e23-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="e1e23-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="e1e23-105">\<configuration></span></span>  
<span data-ttu-id="e1e23-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="e1e23-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e23-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1e23-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1e23-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e1e23-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e1e23-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e1e23-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1e23-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e1e23-110">Attributes</span></span>  
 <span data-ttu-id="e1e23-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="e1e23-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1e23-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e1e23-112">Child Elements</span></span>  
  
|<span data-ttu-id="e1e23-113">Element</span><span class="sxs-lookup"><span data-stu-id="e1e23-113">Element</span></span>|<span data-ttu-id="e1e23-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e1e23-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1e23-115">\<dateTimeSerialization> Element</span><span class="sxs-lookup"><span data-stu-id="e1e23-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="e1e23-116">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e1e23-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|[<span data-ttu-id="e1e23-117">\<schemaImporterExtensions> Element</span><span class="sxs-lookup"><span data-stu-id="e1e23-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="e1e23-118">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1e23-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1e23-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e1e23-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e1e23-120">Element</span><span class="sxs-lookup"><span data-stu-id="e1e23-120">Element</span></span>|<span data-ttu-id="e1e23-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e1e23-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1e23-122">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="e1e23-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="e1e23-123">Element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1e23-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1e23-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1e23-124">Example</span></span>  
 <span data-ttu-id="e1e23-125">Poniższy przykład kodu przedstawia sposób określić tryb serializacji <xref:System.DateTime> obiektu i dodatkowych, używany przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1e23-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1e23-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1e23-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="e1e23-127">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e1e23-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="e1e23-128">\<dateTimeSerialization> Element</span><span class="sxs-lookup"><span data-stu-id="e1e23-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="e1e23-129">\<schemaImporterExtensions> Element</span><span class="sxs-lookup"><span data-stu-id="e1e23-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="e1e23-130">\<add> Element for \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="e1e23-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
