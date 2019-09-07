---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397875"
---
# <a name="knowntype"></a><span data-ttu-id="2263c-101">\<> knownType</span><span class="sxs-lookup"><span data-stu-id="2263c-101">\<knownType></span></span>
<span data-ttu-id="2263c-102">Określa typ, który ma być używany <xref:System.Runtime.Serialization.DataContractSerializer> przez program podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="2263c-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="2263c-103">Element określa "znany typ", który jest zwracany przez pole lub właściwość "zadeklarowanego typu".</span><span class="sxs-lookup"><span data-stu-id="2263c-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="2263c-104">Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="2263c-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="2263c-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2263c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2263c-106">&nbsp;&nbsp;[ **\<> System. Runtime. Serialization**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="2263c-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="2263c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="2263c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="2263c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="2263c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="2263c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Dodaj >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="2263c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="2263c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> knownType**</span><span class="sxs-lookup"><span data-stu-id="2263c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2263c-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="2263c-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="2263c-112">Typ</span><span class="sxs-lookup"><span data-stu-id="2263c-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2263c-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2263c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2263c-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2263c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2263c-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2263c-115">Attributes</span></span>  
  
|<span data-ttu-id="2263c-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2263c-116">Attribute</span></span>|<span data-ttu-id="2263c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="2263c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2263c-118">— typ</span><span class="sxs-lookup"><span data-stu-id="2263c-118">type</span></span>|<span data-ttu-id="2263c-119">Określa typ (w tym przestrzeń nazw), nazwę zestawu, wersję, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="2263c-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2263c-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2263c-120">Child Elements</span></span>  
  
|<span data-ttu-id="2263c-121">Element</span><span class="sxs-lookup"><span data-stu-id="2263c-121">Element</span></span>|<span data-ttu-id="2263c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="2263c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2263c-123">\<> parametru</span><span class="sxs-lookup"><span data-stu-id="2263c-123">\<parameter></span></span>](parameter.md)|<span data-ttu-id="2263c-124">Określa indeks parametru, gdy zadeklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="2263c-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2263c-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2263c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2263c-126">Element</span><span class="sxs-lookup"><span data-stu-id="2263c-126">Element</span></span>|<span data-ttu-id="2263c-127">Opis</span><span class="sxs-lookup"><span data-stu-id="2263c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2263c-128">\<add></span><span class="sxs-lookup"><span data-stu-id="2263c-128">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="2263c-129">Dodaje zadeklarowany typ do kolekcji zadeklarowanych typów.</span><span class="sxs-lookup"><span data-stu-id="2263c-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2263c-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2263c-130">Remarks</span></span>  
 <span data-ttu-id="2263c-131">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2263c-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="2263c-132">Zobacz [ \<> DataContractSerializer](datacontractserializer-element.md) , aby zapoznać się z przykładem użycia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="2263c-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2263c-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="2263c-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2263c-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2263c-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="2263c-135">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="2263c-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="2263c-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="2263c-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="2263c-137">\<add></span><span class="sxs-lookup"><span data-stu-id="2263c-137">\<add></span></span>](add-of-declaredtypes-element.md)
