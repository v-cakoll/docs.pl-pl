---
title: <add>, element dla <schemaImporterExtensions>
description: <add>Element dodaje typy używane przez klasę XmlSchemaImporter do mapowania typów XSD na typy .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 401d1ba9cc2f97e93d7851f96f73b552e6ed6356
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378479"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="d1761-103">\<Dodaj element> dla \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d1761-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="d1761-104">Dodaje typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do mapowania typów XSD typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1761-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="d1761-105">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1761-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="d1761-106">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d1761-106">\<configuration></span></span>  
<span data-ttu-id="d1761-107">\<> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="d1761-107">\<system.xml.serialization></span></span>  
<span data-ttu-id="d1761-108">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d1761-108">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="d1761-109">\<Dodaj></span><span class="sxs-lookup"><span data-stu-id="d1761-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1761-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1761-110">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1761-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d1761-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d1761-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d1761-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1761-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d1761-113">Attributes</span></span>  
  
|<span data-ttu-id="d1761-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d1761-114">Attribute</span></span>|<span data-ttu-id="d1761-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d1761-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1761-116">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="d1761-116">**name**</span></span>|<span data-ttu-id="d1761-117">Prosta nazwa używana do znajdowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d1761-117">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="d1761-118">**Wprowadź**</span><span class="sxs-lookup"><span data-stu-id="d1761-118">**type**</span></span>|<span data-ttu-id="d1761-119">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="d1761-119">Required.</span></span> <span data-ttu-id="d1761-120">Określa klasę rozszerzenia schematu do dodania.</span><span class="sxs-lookup"><span data-stu-id="d1761-120">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="d1761-121">Wartość atrybutu **typu** musi znajdować się w jednym wierszu i zawierać w pełni kwalifikowaną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="d1761-121">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="d1761-122">Gdy zestaw znajduje się w globalnej pamięci podręcznej zestawów (GAC), musi również zawierać wersję, kulturę i token klucza publicznego podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d1761-122">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1761-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d1761-123">Child Elements</span></span>  
 <span data-ttu-id="d1761-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="d1761-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1761-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d1761-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d1761-126">Element</span><span class="sxs-lookup"><span data-stu-id="d1761-126">Element</span></span>|<span data-ttu-id="d1761-127">Opis</span><span class="sxs-lookup"><span data-stu-id="d1761-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1761-128">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d1761-128">\<schemaImporterExtensions></span></span>|<span data-ttu-id="d1761-129">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="d1761-129">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d1761-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1761-130">Example</span></span>  
 <span data-ttu-id="d1761-131">Poniższy przykład kodu dodaje typ rozszerzenia, którego XmlSchemaImporter może używać podczas mapowania typów.</span><span class="sxs-lookup"><span data-stu-id="d1761-131">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1761-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1761-132">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="d1761-133">\<Element> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="d1761-133">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="d1761-134">\<schemaImporterExtensions, element></span><span class="sxs-lookup"><span data-stu-id="d1761-134">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
