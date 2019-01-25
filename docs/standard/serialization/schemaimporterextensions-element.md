---
title: '&lt;schemaImporterExtensions&gt; Element'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: dbe85ea817a597db84ddad530d67b1c2b7953f75
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535375"
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="f92e6-102">&lt;schemaImporterExtensions&gt; Element</span><span class="sxs-lookup"><span data-stu-id="f92e6-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="f92e6-103">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f92e6-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="f92e6-104">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="f92e6-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f92e6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f92e6-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="f92e6-106">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f92e6-106">Child Elements</span></span>  
  
|<span data-ttu-id="f92e6-107">Element</span><span class="sxs-lookup"><span data-stu-id="f92e6-107">Element</span></span>|<span data-ttu-id="f92e6-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f92e6-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f92e6-109">\<add> Element for \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f92e6-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="f92e6-110">Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> można utworzyć mapowania.</span><span class="sxs-lookup"><span data-stu-id="f92e6-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="f92e6-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f92e6-111">Parent Elements</span></span>  
  
|<span data-ttu-id="f92e6-112">Element</span><span class="sxs-lookup"><span data-stu-id="f92e6-112">Element</span></span>|<span data-ttu-id="f92e6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f92e6-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f92e6-114">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="f92e6-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="f92e6-115">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="f92e6-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f92e6-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f92e6-116">Example</span></span>  
 <span data-ttu-id="f92e6-117">Poniższy przykładowy kod przedstawia sposób dodawania typów, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f92e6-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f92e6-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f92e6-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="f92e6-119">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f92e6-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f92e6-120">\<dateTimeSerialization> Element</span><span class="sxs-lookup"><span data-stu-id="f92e6-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="f92e6-121">\<add> Element for \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f92e6-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="f92e6-122">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="f92e6-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
