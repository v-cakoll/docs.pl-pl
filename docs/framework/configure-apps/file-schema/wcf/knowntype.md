---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760691"
---
# <a name="knowntype"></a><span data-ttu-id="dc513-101">\<Element knownType ></span><span class="sxs-lookup"><span data-stu-id="dc513-101">\<knownType></span></span>
<span data-ttu-id="dc513-102">Określa typ, który ma być używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="dc513-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="dc513-103">Element określa "znany typ" zwracanym przez pole lub właściwość "type zadeklarowany".</span><span class="sxs-lookup"><span data-stu-id="dc513-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="dc513-104">Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="dc513-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="dc513-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="dc513-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="dc513-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="dc513-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="dc513-107">\<declaredTypes > Element</span><span class="sxs-lookup"><span data-stu-id="dc513-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="dc513-108">\<Dodaj > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="dc513-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="dc513-109">\<knownType> Element</span><span class="sxs-lookup"><span data-stu-id="dc513-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc513-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc513-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="dc513-111">Typ</span><span class="sxs-lookup"><span data-stu-id="dc513-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc513-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dc513-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dc513-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dc513-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc513-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dc513-114">Attributes</span></span>  
  
|<span data-ttu-id="dc513-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dc513-115">Attribute</span></span>|<span data-ttu-id="dc513-116">Opis</span><span class="sxs-lookup"><span data-stu-id="dc513-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc513-117">— typ</span><span class="sxs-lookup"><span data-stu-id="dc513-117">type</span></span>|<span data-ttu-id="dc513-118">Określa typ (włącznie z przestrzenią nazw), nazwę zestawu, wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="dc513-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc513-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dc513-119">Child Elements</span></span>  
  
|<span data-ttu-id="dc513-120">Element</span><span class="sxs-lookup"><span data-stu-id="dc513-120">Element</span></span>|<span data-ttu-id="dc513-121">Opis</span><span class="sxs-lookup"><span data-stu-id="dc513-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc513-122">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="dc513-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="dc513-123">Określa indeks parametru, gdy deklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="dc513-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc513-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dc513-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dc513-125">Element</span><span class="sxs-lookup"><span data-stu-id="dc513-125">Element</span></span>|<span data-ttu-id="dc513-126">Opis</span><span class="sxs-lookup"><span data-stu-id="dc513-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc513-127">\<add></span><span class="sxs-lookup"><span data-stu-id="dc513-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="dc513-128">Dodaje deklarowany typ do kolekcji typów zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="dc513-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc513-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc513-129">Remarks</span></span>  
 <span data-ttu-id="dc513-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="dc513-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="dc513-131">Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) na przykład przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="dc513-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc513-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc513-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc513-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc513-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="dc513-134">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="dc513-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="dc513-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="dc513-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="dc513-136">\<add></span><span class="sxs-lookup"><span data-stu-id="dc513-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
