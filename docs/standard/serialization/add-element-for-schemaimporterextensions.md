---
title: <add>, element dla <schemaImporterExtensions>
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 89196b094d5631c9e243a51a718e53f9c06db20d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794982"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="360b9-102">\<add> Element for \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="360b9-102">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="360b9-103">Dodaje typy używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> do mapowania typów XSD typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="360b9-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="360b9-104">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="360b9-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="360b9-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="360b9-105">\<configuration></span></span>  
<span data-ttu-id="360b9-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="360b9-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="360b9-107">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="360b9-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="360b9-108">\<add></span><span class="sxs-lookup"><span data-stu-id="360b9-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="360b9-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="360b9-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="360b9-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="360b9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="360b9-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="360b9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="360b9-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="360b9-112">Attributes</span></span>  
  
|<span data-ttu-id="360b9-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="360b9-113">Attribute</span></span>|<span data-ttu-id="360b9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="360b9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="360b9-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="360b9-115">**name**</span></span>|<span data-ttu-id="360b9-116">Prosta nazwa jest używana do znajdowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="360b9-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="360b9-117">**type**</span><span class="sxs-lookup"><span data-stu-id="360b9-117">**type**</span></span>|<span data-ttu-id="360b9-118">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="360b9-118">Required.</span></span> <span data-ttu-id="360b9-119">Określa klasę rozszerzenia schematu do dodania.</span><span class="sxs-lookup"><span data-stu-id="360b9-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="360b9-120">**Typu** wartość atrybutu musi być w jednym wierszu i zawierać w pełni kwalifikowana nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="360b9-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="360b9-121">Gdy zestawu znajduje się w globalnej pamięci podręcznej zestawów (GAC), to również obejmować wersji, kulturę i token klucza publicznego zestawu podpisem.</span><span class="sxs-lookup"><span data-stu-id="360b9-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="360b9-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="360b9-122">Child Elements</span></span>  
 <span data-ttu-id="360b9-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="360b9-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="360b9-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="360b9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="360b9-125">Element</span><span class="sxs-lookup"><span data-stu-id="360b9-125">Element</span></span>|<span data-ttu-id="360b9-126">Opis</span><span class="sxs-lookup"><span data-stu-id="360b9-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="360b9-127">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="360b9-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="360b9-128">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="360b9-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="360b9-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="360b9-129">Example</span></span>  
 <span data-ttu-id="360b9-130">Poniższy przykład kodu dodaje typ rozszerzenia, które XmlSchemaImporter można używać podczas mapowania typów.</span><span class="sxs-lookup"><span data-stu-id="360b9-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="360b9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="360b9-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="360b9-132">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="360b9-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="360b9-133">\<schemaImporterExtensions> Element</span><span class="sxs-lookup"><span data-stu-id="360b9-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
