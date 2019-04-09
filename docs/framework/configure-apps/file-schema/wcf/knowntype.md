---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148840"
---
# <a name="knowntype"></a><span data-ttu-id="fe413-101">\<Element knownType ></span><span class="sxs-lookup"><span data-stu-id="fe413-101">\<knownType></span></span>
<span data-ttu-id="fe413-102">Określa typ, który ma być używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fe413-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="fe413-103">Element określa "znany typ" zwracanym przez pole lub właściwość "type zadeklarowany".</span><span class="sxs-lookup"><span data-stu-id="fe413-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="fe413-104">Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="fe413-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="fe413-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="fe413-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="fe413-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="fe413-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="fe413-107">\<declaredTypes > Element</span><span class="sxs-lookup"><span data-stu-id="fe413-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="fe413-108">\<Dodaj > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="fe413-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="fe413-109">\<knownType> Element</span><span class="sxs-lookup"><span data-stu-id="fe413-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe413-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe413-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="fe413-111">Typ</span><span class="sxs-lookup"><span data-stu-id="fe413-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe413-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fe413-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fe413-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fe413-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe413-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fe413-114">Attributes</span></span>  
  
|<span data-ttu-id="fe413-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fe413-115">Attribute</span></span>|<span data-ttu-id="fe413-116">Opis</span><span class="sxs-lookup"><span data-stu-id="fe413-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe413-117">— typ</span><span class="sxs-lookup"><span data-stu-id="fe413-117">type</span></span>|<span data-ttu-id="fe413-118">Określa typ (włącznie z przestrzenią nazw), nazwę zestawu, wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="fe413-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe413-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fe413-119">Child Elements</span></span>  
  
|<span data-ttu-id="fe413-120">Element</span><span class="sxs-lookup"><span data-stu-id="fe413-120">Element</span></span>|<span data-ttu-id="fe413-121">Opis</span><span class="sxs-lookup"><span data-stu-id="fe413-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe413-122">\<parameter></span><span class="sxs-lookup"><span data-stu-id="fe413-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="fe413-123">Określa indeks parametru, gdy deklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="fe413-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe413-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fe413-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fe413-125">Element</span><span class="sxs-lookup"><span data-stu-id="fe413-125">Element</span></span>|<span data-ttu-id="fe413-126">Opis</span><span class="sxs-lookup"><span data-stu-id="fe413-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe413-127">\<add></span><span class="sxs-lookup"><span data-stu-id="fe413-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="fe413-128">Dodaje deklarowany typ do kolekcji typów zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="fe413-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe413-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe413-129">Remarks</span></span>  
 <span data-ttu-id="fe413-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fe413-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="fe413-131">Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) na przykład przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="fe413-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe413-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe413-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe413-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe413-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="fe413-134">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="fe413-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="fe413-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="fe413-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="fe413-136">\<add></span><span class="sxs-lookup"><span data-stu-id="fe413-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
