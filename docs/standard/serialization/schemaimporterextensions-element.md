---
title: "&lt;schemaImporterExtensions&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0296b207af0ed439c90374eb6db21fe11e00dd42
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="ed458-102">&lt;schemaImporterExtensions&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="ed458-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="ed458-103">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed458-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="ed458-104">Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="ed458-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed458-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed458-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="ed458-106">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ed458-106">Child Elements</span></span>  
  
|<span data-ttu-id="ed458-107">Element</span><span class="sxs-lookup"><span data-stu-id="ed458-107">Element</span></span>|<span data-ttu-id="ed458-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ed458-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed458-109">\<Dodaj > elementu \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="ed458-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="ed458-110">Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> można utworzyć mapowania.</span><span class="sxs-lookup"><span data-stu-id="ed458-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="ed458-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ed458-111">Parent Elements</span></span>  
  
|<span data-ttu-id="ed458-112">Element</span><span class="sxs-lookup"><span data-stu-id="ed458-112">Element</span></span>|<span data-ttu-id="ed458-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ed458-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed458-114">\<System.XML.serialization > — Element</span><span class="sxs-lookup"><span data-stu-id="ed458-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="ed458-115">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="ed458-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ed458-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed458-116">Example</span></span>  
 <span data-ttu-id="ed458-117">Poniższy przykładowy kod przedstawia sposób dodawania typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed458-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed458-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed458-118">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="ed458-119">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ed458-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ed458-120">\<dateTimeSerialization > — Element</span><span class="sxs-lookup"><span data-stu-id="ed458-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="ed458-121">\<Dodaj > elementu \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="ed458-121">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="ed458-122">\<System.XML.serialization > — Element</span><span class="sxs-lookup"><span data-stu-id="ed458-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
