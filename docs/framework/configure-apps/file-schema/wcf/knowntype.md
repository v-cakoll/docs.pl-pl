---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: a0794314cfcb87df00d66b6832356fb130787eba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928869"
---
# <a name="knowntype"></a><span data-ttu-id="7eb26-101">\<> knownType</span><span class="sxs-lookup"><span data-stu-id="7eb26-101">\<knownType></span></span>
<span data-ttu-id="7eb26-102">Określa typ, który ma być używany <xref:System.Runtime.Serialization.DataContractSerializer> przez program podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="7eb26-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="7eb26-103">Element określa "znany typ", który jest zwracany przez pole lub właściwość "zadeklarowanego typu".</span><span class="sxs-lookup"><span data-stu-id="7eb26-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="7eb26-104">Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="7eb26-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="7eb26-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="7eb26-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="7eb26-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="7eb26-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="7eb26-107">\<declaredTypes, element ></span><span class="sxs-lookup"><span data-stu-id="7eb26-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="7eb26-108">\<Dodawanie > \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="7eb26-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="7eb26-109">\<Element > knownType</span><span class="sxs-lookup"><span data-stu-id="7eb26-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb26-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="7eb26-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="7eb26-111">Typ</span><span class="sxs-lookup"><span data-stu-id="7eb26-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7eb26-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7eb26-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7eb26-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7eb26-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7eb26-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7eb26-114">Attributes</span></span>  
  
|<span data-ttu-id="7eb26-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7eb26-115">Attribute</span></span>|<span data-ttu-id="7eb26-116">Opis</span><span class="sxs-lookup"><span data-stu-id="7eb26-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7eb26-117">— typ</span><span class="sxs-lookup"><span data-stu-id="7eb26-117">type</span></span>|<span data-ttu-id="7eb26-118">Określa typ (w tym przestrzeń nazw), nazwę zestawu, wersję, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="7eb26-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7eb26-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7eb26-119">Child Elements</span></span>  
  
|<span data-ttu-id="7eb26-120">Element</span><span class="sxs-lookup"><span data-stu-id="7eb26-120">Element</span></span>|<span data-ttu-id="7eb26-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7eb26-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eb26-122">\<> parametru</span><span class="sxs-lookup"><span data-stu-id="7eb26-122">\<parameter></span></span>](parameter.md)|<span data-ttu-id="7eb26-123">Określa indeks parametru, gdy zadeklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="7eb26-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7eb26-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7eb26-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7eb26-125">Element</span><span class="sxs-lookup"><span data-stu-id="7eb26-125">Element</span></span>|<span data-ttu-id="7eb26-126">Opis</span><span class="sxs-lookup"><span data-stu-id="7eb26-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eb26-127">\<add></span><span class="sxs-lookup"><span data-stu-id="7eb26-127">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="7eb26-128">Dodaje zadeklarowany typ do kolekcji zadeklarowanych typów.</span><span class="sxs-lookup"><span data-stu-id="7eb26-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7eb26-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7eb26-129">Remarks</span></span>  
 <span data-ttu-id="7eb26-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7eb26-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="7eb26-131">Zobacz [ \<> DataContractSerializer](datacontractserializer-element.md) , aby zapoznać się z przykładem użycia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="7eb26-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7eb26-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="7eb26-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7eb26-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7eb26-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="7eb26-134">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="7eb26-134">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="7eb26-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="7eb26-135">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="7eb26-136">\<add></span><span class="sxs-lookup"><span data-stu-id="7eb26-136">\<add></span></span>](add-of-declaredtypes-element.md)
