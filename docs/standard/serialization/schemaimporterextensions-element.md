---
title: '&lt;schemaImporterExtensions&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c9f4f6800c2718c3b2c2b9b5b2b6d97e1114dbcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="21287-102">&lt;schemaImporterExtensions&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="21287-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="21287-103">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21287-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="21287-104">Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="21287-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21287-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="21287-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="21287-106">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="21287-106">Child Elements</span></span>  
  
|<span data-ttu-id="21287-107">Element</span><span class="sxs-lookup"><span data-stu-id="21287-107">Element</span></span>|<span data-ttu-id="21287-108">Opis</span><span class="sxs-lookup"><span data-stu-id="21287-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21287-109">\<Dodaj > elementu \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="21287-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="21287-110">Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> można utworzyć mapowania.</span><span class="sxs-lookup"><span data-stu-id="21287-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="21287-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="21287-111">Parent Elements</span></span>  
  
|<span data-ttu-id="21287-112">Element</span><span class="sxs-lookup"><span data-stu-id="21287-112">Element</span></span>|<span data-ttu-id="21287-113">Opis</span><span class="sxs-lookup"><span data-stu-id="21287-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21287-114">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="21287-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="21287-115">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="21287-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="21287-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="21287-116">Example</span></span>  
 <span data-ttu-id="21287-117">Poniższy przykładowy kod przedstawia sposób dodawania typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD do typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21287-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21287-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21287-118">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="21287-119">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="21287-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="21287-120">\<dateTimeSerialization > — Element</span><span class="sxs-lookup"><span data-stu-id="21287-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="21287-121">\<Dodaj > elementu \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="21287-121">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="21287-122">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="21287-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
