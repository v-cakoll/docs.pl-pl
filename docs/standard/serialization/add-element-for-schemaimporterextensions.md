---
title: '&lt;Dodaj&gt; elementu &lt;schemaImporterExtensions&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 48deb8684e53f583e3ff4a5407fadd112d45f749
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196832"
---
# <a name="ltaddgt-element-for-ltschemaimporterextensionsgt"></a><span data-ttu-id="5490e-102">&lt;Dodaj&gt; elementu &lt;schemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="5490e-102">&lt;add&gt; Element for &lt;schemaImporterExtensions&gt;</span></span>
<span data-ttu-id="5490e-103">Dodaje typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do mapowania typów XSD typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5490e-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="5490e-104">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="5490e-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="5490e-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="5490e-105">\<configuration></span></span>  
<span data-ttu-id="5490e-106">\<System.XML.serialization ></span><span class="sxs-lookup"><span data-stu-id="5490e-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="5490e-107">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="5490e-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="5490e-108">\<add></span><span class="sxs-lookup"><span data-stu-id="5490e-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5490e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5490e-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5490e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5490e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5490e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5490e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5490e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5490e-112">Attributes</span></span>  
  
|<span data-ttu-id="5490e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5490e-113">Attribute</span></span>|<span data-ttu-id="5490e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5490e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5490e-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="5490e-115">**name**</span></span>|<span data-ttu-id="5490e-116">Prosta nazwa jest używana do znajdowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5490e-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="5490e-117">**Typ**</span><span class="sxs-lookup"><span data-stu-id="5490e-117">**type**</span></span>|<span data-ttu-id="5490e-118">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="5490e-118">Required.</span></span> <span data-ttu-id="5490e-119">Określa klasę rozszerzenia schematu do dodania.</span><span class="sxs-lookup"><span data-stu-id="5490e-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="5490e-120">**Typu** wartość atrybutu musi być w jednym wierszu i zawierać w pełni kwalifikowana nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="5490e-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="5490e-121">Gdy zestawu znajduje się w globalnej pamięci podręcznej zestawów (GAC), to również obejmować wersji, kulturę i token klucza publicznego zestawu podpisem.</span><span class="sxs-lookup"><span data-stu-id="5490e-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5490e-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5490e-122">Child Elements</span></span>  
 <span data-ttu-id="5490e-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="5490e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5490e-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5490e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5490e-125">Element</span><span class="sxs-lookup"><span data-stu-id="5490e-125">Element</span></span>|<span data-ttu-id="5490e-126">Opis</span><span class="sxs-lookup"><span data-stu-id="5490e-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5490e-127">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="5490e-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="5490e-128">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="5490e-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5490e-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="5490e-129">Example</span></span>  
 <span data-ttu-id="5490e-130">Poniższy przykład kodu dodaje typ rozszerzenia, które XmlSchemaImporter można używać podczas mapowania typów.</span><span class="sxs-lookup"><span data-stu-id="5490e-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5490e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5490e-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>  
- [<span data-ttu-id="5490e-132">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="5490e-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
- [<span data-ttu-id="5490e-133">\<schemaImporterExtensions > Element</span><span class="sxs-lookup"><span data-stu-id="5490e-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
