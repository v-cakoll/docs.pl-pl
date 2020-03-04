---
title: <add>, element dla <schemaImporterExtensions>
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 4f47623aa305ae6e98625acc3d199a76e27d2ea5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159939"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="2f822-102">\<dodać > elementu \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="2f822-102">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="2f822-103">Dodaje typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do mapowania typów XSD typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2f822-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="2f822-104">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="2f822-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="2f822-105">> konfiguracji \<</span><span class="sxs-lookup"><span data-stu-id="2f822-105">\<configuration></span></span>  
<span data-ttu-id="2f822-106">> \<system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="2f822-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="2f822-107">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="2f822-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="2f822-108">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="2f822-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f822-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f822-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f822-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2f822-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2f822-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2f822-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f822-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2f822-112">Attributes</span></span>  
  
|<span data-ttu-id="2f822-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2f822-113">Attribute</span></span>|<span data-ttu-id="2f822-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2f822-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f822-115">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="2f822-115">**name**</span></span>|<span data-ttu-id="2f822-116">Prosta nazwa używana do znajdowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2f822-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="2f822-117">**type**</span><span class="sxs-lookup"><span data-stu-id="2f822-117">**type**</span></span>|<span data-ttu-id="2f822-118">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2f822-118">Required.</span></span> <span data-ttu-id="2f822-119">Określa klasę rozszerzenia schematu do dodania.</span><span class="sxs-lookup"><span data-stu-id="2f822-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="2f822-120">Wartość atrybutu **typu** musi znajdować się w jednym wierszu i zawierać w pełni kwalifikowaną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="2f822-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="2f822-121">Gdy zestaw znajduje się w globalnej pamięci podręcznej zestawów (GAC), musi również zawierać wersję, kulturę i token klucza publicznego podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2f822-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f822-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2f822-122">Child Elements</span></span>  
 <span data-ttu-id="2f822-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="2f822-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f822-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2f822-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2f822-125">Element</span><span class="sxs-lookup"><span data-stu-id="2f822-125">Element</span></span>|<span data-ttu-id="2f822-126">Opis</span><span class="sxs-lookup"><span data-stu-id="2f822-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f822-127">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="2f822-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="2f822-128">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="2f822-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2f822-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f822-129">Example</span></span>  
 <span data-ttu-id="2f822-130">Poniższy przykład kodu dodaje typ rozszerzenia, którego XmlSchemaImporter może używać podczas mapowania typów.</span><span class="sxs-lookup"><span data-stu-id="2f822-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f822-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f822-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="2f822-132">\<element > System. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="2f822-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="2f822-133">\<element > schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="2f822-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
