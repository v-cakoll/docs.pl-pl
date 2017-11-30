---
title: '&lt;Dodaj&gt; elementu &lt;xmlSchemaImporterExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <xmlSchemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 766d04dd792534f0da33116ed959d81ff376e026
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-ltxmlschemaimporterextensionsgt"></a><span data-ttu-id="713c4-102">&lt;Dodaj&gt; elementu &lt;xmlSchemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="713c4-102">&lt;add&gt; Element for &lt;xmlSchemaImporterExtensions&gt;</span></span>
<span data-ttu-id="713c4-103">Dodaje typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do mapowania typów XSD typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="713c4-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="713c4-104">Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="713c4-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="713c4-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="713c4-105">\<configuration></span></span>  
<span data-ttu-id="713c4-106">\<System.XML.serialization ></span><span class="sxs-lookup"><span data-stu-id="713c4-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="713c4-107">\<XmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="713c4-107">\<XmlSchemaImporterExtensions></span></span>  
<span data-ttu-id="713c4-108">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="713c4-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713c4-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="713c4-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="713c4-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="713c4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="713c4-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="713c4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="713c4-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="713c4-112">Attributes</span></span>  
  
|<span data-ttu-id="713c4-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="713c4-113">Attribute</span></span>|<span data-ttu-id="713c4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="713c4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="713c4-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="713c4-115">**name**</span></span>|<span data-ttu-id="713c4-116">Prosta nazwa jest używana do znajdowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="713c4-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="713c4-117">**Typ**</span><span class="sxs-lookup"><span data-stu-id="713c4-117">**type**</span></span>|<span data-ttu-id="713c4-118">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="713c4-118">Required.</span></span> <span data-ttu-id="713c4-119">Określa klasę rozszerzenia schematu do dodania.</span><span class="sxs-lookup"><span data-stu-id="713c4-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="713c4-120">**Typu** wartość atrybutu musi być w jednym wierszu i zawierać pełni kwalifikowaną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="713c4-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="713c4-121">Jeśli zestaw znajduje się w globalnej pamięci podręcznej zestawów (GAC), musi także obejmować wersję, kulturę i token klucza publicznego zestawu podpisem.</span><span class="sxs-lookup"><span data-stu-id="713c4-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="713c4-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="713c4-122">Child Elements</span></span>  
 <span data-ttu-id="713c4-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="713c4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="713c4-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="713c4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="713c4-125">Element</span><span class="sxs-lookup"><span data-stu-id="713c4-125">Element</span></span>|<span data-ttu-id="713c4-126">Opis</span><span class="sxs-lookup"><span data-stu-id="713c4-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="713c4-127">\<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="713c4-127">\<xmlSchemaImporterExtensions></span></span>|<span data-ttu-id="713c4-128">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="713c4-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="713c4-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="713c4-129">Example</span></span>  
 <span data-ttu-id="713c4-130">Poniższy przykładowy kod dodaje typ rozszerzenia, które XmlSchemaImporter można użyć w przypadku mapowania typów.</span><span class="sxs-lookup"><span data-stu-id="713c4-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="713c4-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="713c4-131">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 [<span data-ttu-id="713c4-132">\<System.XML.serialization > — Element</span><span class="sxs-lookup"><span data-stu-id="713c4-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="713c4-133">\<schemaImporterExtensions > — Element</span><span class="sxs-lookup"><span data-stu-id="713c4-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
