---
title: '&lt;Typ knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: b2445f12f1eaac03b3f3ab66f3d13a5f465a1133
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753329"
---
# <a name="ltknowntypegt"></a><span data-ttu-id="baa80-102">&lt;Typ knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="baa80-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="baa80-103">Określa typ, który będzie używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="baa80-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="baa80-104">Element "znanego typu" Określa, który jest zwracany przez pole lub właściwość "zadeklarowanym typem".</span><span class="sxs-lookup"><span data-stu-id="baa80-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="baa80-105">Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="baa80-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="baa80-106">\<System.Runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="baa80-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="baa80-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="baa80-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="baa80-108">\<declaredTypes > — Element</span><span class="sxs-lookup"><span data-stu-id="baa80-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="baa80-109">\<Dodaj > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="baa80-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="baa80-110">\<Typ knownType > — Element</span><span class="sxs-lookup"><span data-stu-id="baa80-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baa80-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="baa80-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="baa80-112">Typ</span><span class="sxs-lookup"><span data-stu-id="baa80-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baa80-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="baa80-113">Attributes and Elements</span></span>  
 <span data-ttu-id="baa80-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="baa80-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baa80-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="baa80-115">Attributes</span></span>  
  
|<span data-ttu-id="baa80-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="baa80-116">Attribute</span></span>|<span data-ttu-id="baa80-117">Opis</span><span class="sxs-lookup"><span data-stu-id="baa80-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="baa80-118">— typ</span><span class="sxs-lookup"><span data-stu-id="baa80-118">type</span></span>|<span data-ttu-id="baa80-119">Określa typ (włącznie z przestrzenią nazw), nazwę zestawu, wersję, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="baa80-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="baa80-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="baa80-120">Child Elements</span></span>  
  
|<span data-ttu-id="baa80-121">Element</span><span class="sxs-lookup"><span data-stu-id="baa80-121">Element</span></span>|<span data-ttu-id="baa80-122">Opis</span><span class="sxs-lookup"><span data-stu-id="baa80-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baa80-123">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="baa80-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="baa80-124">Określa indeks parametru, gdy deklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="baa80-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="baa80-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="baa80-125">Parent Elements</span></span>  
  
|<span data-ttu-id="baa80-126">Element</span><span class="sxs-lookup"><span data-stu-id="baa80-126">Element</span></span>|<span data-ttu-id="baa80-127">Opis</span><span class="sxs-lookup"><span data-stu-id="baa80-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baa80-128">\<add></span><span class="sxs-lookup"><span data-stu-id="baa80-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="baa80-129">Dodaje deklarowany typ do kolekcji zadeklarowanych typów.</span><span class="sxs-lookup"><span data-stu-id="baa80-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baa80-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="baa80-130">Remarks</span></span>  
 <span data-ttu-id="baa80-131">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="baa80-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="baa80-132">Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) przykład za pomocą tego elementu.</span><span class="sxs-lookup"><span data-stu-id="baa80-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baa80-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="baa80-133">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="baa80-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="baa80-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="baa80-135">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="baa80-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="baa80-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="baa80-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="baa80-137">\<add></span><span class="sxs-lookup"><span data-stu-id="baa80-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
