---
title: '&lt;Dodaj&gt; elementu &lt;schemaImporterExtensions&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 3d3c72fd64042032d44c49ebde867d111ce03b94
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43453092"
---
# <a name="ltaddgt-element-for-ltschemaimporterextensionsgt"></a><span data-ttu-id="33488-102">&lt;Dodaj&gt; elementu &lt;schemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="33488-102">&lt;add&gt; Element for &lt;schemaImporterExtensions&gt;</span></span>
<span data-ttu-id="33488-103">Dodaje typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do mapowania typów XSD typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="33488-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="33488-104">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="33488-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="33488-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="33488-105">\<configuration></span></span>  
<span data-ttu-id="33488-106">\<System.XML.serialization ></span><span class="sxs-lookup"><span data-stu-id="33488-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="33488-107">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="33488-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="33488-108">\<add></span><span class="sxs-lookup"><span data-stu-id="33488-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33488-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="33488-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33488-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="33488-110">Attributes and Elements</span></span>  
 <span data-ttu-id="33488-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="33488-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33488-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="33488-112">Attributes</span></span>  
  
|<span data-ttu-id="33488-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="33488-113">Attribute</span></span>|<span data-ttu-id="33488-114">Opis</span><span class="sxs-lookup"><span data-stu-id="33488-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33488-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="33488-115">**name**</span></span>|<span data-ttu-id="33488-116">Prosta nazwa jest używana do znajdowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="33488-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="33488-117">**Typ**</span><span class="sxs-lookup"><span data-stu-id="33488-117">**type**</span></span>|<span data-ttu-id="33488-118">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="33488-118">Required.</span></span> <span data-ttu-id="33488-119">Określa klasę rozszerzenia schematu do dodania.</span><span class="sxs-lookup"><span data-stu-id="33488-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="33488-120">**Typu** wartość atrybutu musi być w jednym wierszu i zawierać w pełni kwalifikowana nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="33488-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="33488-121">Gdy zestawu znajduje się w globalnej pamięci podręcznej zestawów (GAC), to również obejmować wersji, kulturę i token klucza publicznego zestawu podpisem.</span><span class="sxs-lookup"><span data-stu-id="33488-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33488-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="33488-122">Child Elements</span></span>  
 <span data-ttu-id="33488-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="33488-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33488-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="33488-124">Parent Elements</span></span>  
  
|<span data-ttu-id="33488-125">Element</span><span class="sxs-lookup"><span data-stu-id="33488-125">Element</span></span>|<span data-ttu-id="33488-126">Opis</span><span class="sxs-lookup"><span data-stu-id="33488-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33488-127">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="33488-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="33488-128">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="33488-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="33488-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="33488-129">Example</span></span>  
 <span data-ttu-id="33488-130">Poniższy przykład kodu dodaje typ rozszerzenia, które XmlSchemaImporter można używać podczas mapowania typów.</span><span class="sxs-lookup"><span data-stu-id="33488-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="33488-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33488-131">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 [<span data-ttu-id="33488-132">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="33488-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="33488-133">\<schemaImporterExtensions > Element</span><span class="sxs-lookup"><span data-stu-id="33488-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
