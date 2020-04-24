---
title: <schemaImporterExtensions>, element
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5ed80ac370e34d6b62bb2b601cb7bd978228a302
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159822"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="f6ef4-102">\<schemaImporterExtensions, element></span><span class="sxs-lookup"><span data-stu-id="f6ef4-102">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="f6ef4-103">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6ef4-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="f6ef4-104">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="f6ef4-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6ef4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6ef4-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="f6ef4-106">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6ef4-106">Child Elements</span></span>  
  
|<span data-ttu-id="f6ef4-107">Element</span><span class="sxs-lookup"><span data-stu-id="f6ef4-107">Element</span></span>|<span data-ttu-id="f6ef4-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f6ef4-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6ef4-109">\<Dodaj element> dla \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f6ef4-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="f6ef4-110">Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> program do tworzenia mapowań.</span><span class="sxs-lookup"><span data-stu-id="f6ef4-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="f6ef4-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6ef4-111">Parent Elements</span></span>  
  
|<span data-ttu-id="f6ef4-112">Element</span><span class="sxs-lookup"><span data-stu-id="f6ef4-112">Element</span></span>|<span data-ttu-id="f6ef4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f6ef4-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6ef4-114">\<Element> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="f6ef4-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="f6ef4-115">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="f6ef4-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f6ef4-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6ef4-116">Example</span></span>  
 <span data-ttu-id="f6ef4-117">Poniższy przykład kodu ilustruje sposób dodawania typów, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD na typy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6ef4-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6ef4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6ef4-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="f6ef4-119">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f6ef4-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f6ef4-120">\<dateTimeSerialization, element></span><span class="sxs-lookup"><span data-stu-id="f6ef4-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="f6ef4-121">\<Dodaj element> dla \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f6ef4-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="f6ef4-122">\<Element> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="f6ef4-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
