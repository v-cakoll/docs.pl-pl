---
title: <schemaImporterExtensions> Element
description: <schemaImporterExtensions>Element zawiera typy, które są używane przez XmlSchemaImporter do mapowania typów XSD na typy .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c46c5cb6e01463723f0f2ce3873fb4a6ec0b4e60
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84278405"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="467bc-103">\<schemaImporterExtensions> Element</span><span class="sxs-lookup"><span data-stu-id="467bc-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="467bc-104">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="467bc-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="467bc-105">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="467bc-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="467bc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="467bc-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="467bc-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="467bc-107">Child Elements</span></span>  
  
|<span data-ttu-id="467bc-108">Element</span><span class="sxs-lookup"><span data-stu-id="467bc-108">Element</span></span>|<span data-ttu-id="467bc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="467bc-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="467bc-110">\<add>Element dla\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="467bc-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="467bc-111">Dodaje typy, które są używane przez program <xref:System.Xml.Serialization.XmlSchemaImporter> do tworzenia mapowań.</span><span class="sxs-lookup"><span data-stu-id="467bc-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="467bc-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="467bc-112">Parent Elements</span></span>  
  
|<span data-ttu-id="467bc-113">Element</span><span class="sxs-lookup"><span data-stu-id="467bc-113">Element</span></span>|<span data-ttu-id="467bc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="467bc-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="467bc-115">\<system.xml.serialization>Postaci</span><span class="sxs-lookup"><span data-stu-id="467bc-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="467bc-116">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="467bc-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="467bc-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="467bc-117">Example</span></span>  
 <span data-ttu-id="467bc-118">Poniższy przykład kodu ilustruje sposób dodawania typów, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD na typy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="467bc-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="467bc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="467bc-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="467bc-120">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="467bc-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="467bc-121">\<dateTimeSerialization>Postaci</span><span class="sxs-lookup"><span data-stu-id="467bc-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="467bc-122">\<add>Element dla\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="467bc-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="467bc-123">\<system.xml.serialization>Postaci</span><span class="sxs-lookup"><span data-stu-id="467bc-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
