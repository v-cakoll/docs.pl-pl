---
title: "&lt;System.XML.serialization&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d673c76e57ffb8315e97b1695dbcbc1f4fe0aab9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="ltsystemxmlserializationgt-element"></a><span data-ttu-id="ef732-102">&lt;System.XML.serialization&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="ef732-102">&lt;system.xml.serialization&gt; Element</span></span>
<span data-ttu-id="ef732-103">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="ef732-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="ef732-104">Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef732-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="ef732-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ef732-105">\<configuration></span></span>  
<span data-ttu-id="ef732-106">\<System.XML.serialization ></span><span class="sxs-lookup"><span data-stu-id="ef732-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef732-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef732-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef732-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ef732-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ef732-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ef732-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef732-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ef732-110">Attributes</span></span>  
 <span data-ttu-id="ef732-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="ef732-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ef732-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ef732-112">Child Elements</span></span>  
  
|<span data-ttu-id="ef732-113">Element</span><span class="sxs-lookup"><span data-stu-id="ef732-113">Element</span></span>|<span data-ttu-id="ef732-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ef732-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef732-115">\<dateTimeSerialization > — Element</span><span class="sxs-lookup"><span data-stu-id="ef732-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="ef732-116">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ef732-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|[<span data-ttu-id="ef732-117">\<schemaImporterExtensions > — Element</span><span class="sxs-lookup"><span data-stu-id="ef732-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="ef732-118">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef732-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef732-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ef732-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ef732-120">Element</span><span class="sxs-lookup"><span data-stu-id="ef732-120">Element</span></span>|<span data-ttu-id="ef732-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ef732-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef732-122">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="ef732-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="ef732-123">Element główny w każdym pliku konfiguracyjnym, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef732-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ef732-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef732-124">Example</span></span>  
 <span data-ttu-id="ef732-125">Poniższy przykładowy kod przedstawia sposób określić tryb serializacji <xref:System.DateTime> obiektu oraz dodanie typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef732-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef732-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef732-126">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="ef732-127">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ef732-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ef732-128">\<dateTimeSerialization > — Element</span><span class="sxs-lookup"><span data-stu-id="ef732-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="ef732-129">\<schemaImporterExtensions > — Element</span><span class="sxs-lookup"><span data-stu-id="ef732-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [<span data-ttu-id="ef732-130">\<Dodaj > elementu \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="ef732-130">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)
