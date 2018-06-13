---
title: '&lt;Dodaj&gt; elementu &lt;xmlSchemaImporterExtensions&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <xmlSchemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 6e14c478e33c465d2ea3d10158f856dc5ca6c49a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581745"
---
# <a name="ltaddgt-element-for-ltxmlschemaimporterextensionsgt"></a><span data-ttu-id="e09ab-102">&lt;Dodaj&gt; elementu &lt;xmlSchemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="e09ab-102">&lt;add&gt; Element for &lt;xmlSchemaImporterExtensions&gt;</span></span>
<span data-ttu-id="e09ab-103">Dodaje typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do mapowania typów XSD typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e09ab-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="e09ab-104">Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="e09ab-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="e09ab-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="e09ab-105">\<configuration></span></span>  
<span data-ttu-id="e09ab-106">\<System.XML.serialization ></span><span class="sxs-lookup"><span data-stu-id="e09ab-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="e09ab-107">\<XmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="e09ab-107">\<XmlSchemaImporterExtensions></span></span>  
<span data-ttu-id="e09ab-108">\<add></span><span class="sxs-lookup"><span data-stu-id="e09ab-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09ab-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e09ab-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e09ab-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e09ab-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e09ab-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e09ab-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e09ab-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e09ab-112">Attributes</span></span>  
  
|<span data-ttu-id="e09ab-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e09ab-113">Attribute</span></span>|<span data-ttu-id="e09ab-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e09ab-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e09ab-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="e09ab-115">**name**</span></span>|<span data-ttu-id="e09ab-116">Prosta nazwa jest używana do znajdowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e09ab-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="e09ab-117">**Typ**</span><span class="sxs-lookup"><span data-stu-id="e09ab-117">**type**</span></span>|<span data-ttu-id="e09ab-118">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e09ab-118">Required.</span></span> <span data-ttu-id="e09ab-119">Określa klasę rozszerzenia schematu do dodania.</span><span class="sxs-lookup"><span data-stu-id="e09ab-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="e09ab-120">**Typu** wartość atrybutu musi być w jednym wierszu i zawierać pełni kwalifikowaną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="e09ab-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="e09ab-121">Jeśli zestaw znajduje się w globalnej pamięci podręcznej zestawów (GAC), musi także obejmować wersję, kulturę i token klucza publicznego zestawu podpisem.</span><span class="sxs-lookup"><span data-stu-id="e09ab-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e09ab-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e09ab-122">Child Elements</span></span>  
 <span data-ttu-id="e09ab-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="e09ab-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e09ab-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e09ab-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e09ab-125">Element</span><span class="sxs-lookup"><span data-stu-id="e09ab-125">Element</span></span>|<span data-ttu-id="e09ab-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e09ab-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e09ab-127">\<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="e09ab-127">\<xmlSchemaImporterExtensions></span></span>|<span data-ttu-id="e09ab-128">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="e09ab-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e09ab-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="e09ab-129">Example</span></span>  
 <span data-ttu-id="e09ab-130">Poniższy przykładowy kod dodaje typ rozszerzenia, które XmlSchemaImporter można użyć w przypadku mapowania typów.</span><span class="sxs-lookup"><span data-stu-id="e09ab-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSchemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </xmlSchemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e09ab-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e09ab-131">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 [<span data-ttu-id="e09ab-132">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="e09ab-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="e09ab-133">\<schemaImporterExtensions > — Element</span><span class="sxs-lookup"><span data-stu-id="e09ab-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
