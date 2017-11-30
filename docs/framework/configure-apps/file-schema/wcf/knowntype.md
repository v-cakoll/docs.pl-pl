---
title: '&lt;Typ knownType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ccb7152197a021821936e178e0de77b9dfabce45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltknowntypegt"></a><span data-ttu-id="91f0a-102">&lt;Typ knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="91f0a-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="91f0a-103">Określa typ, który będzie używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="91f0a-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="91f0a-104">Element "znanego typu" Określa, który jest zwracany przez pole lub właściwość "zadeklarowanym typem".</span><span class="sxs-lookup"><span data-stu-id="91f0a-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="91f0a-105">Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="91f0a-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="91f0a-106">\<System.Runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="91f0a-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="91f0a-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="91f0a-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="91f0a-108">\<declaredTypes > — Element</span><span class="sxs-lookup"><span data-stu-id="91f0a-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="91f0a-109">\<Dodaj > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="91f0a-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="91f0a-110">\<Typ knownType > — Element</span><span class="sxs-lookup"><span data-stu-id="91f0a-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91f0a-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="91f0a-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="91f0a-112">Typ</span><span class="sxs-lookup"><span data-stu-id="91f0a-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91f0a-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="91f0a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="91f0a-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="91f0a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91f0a-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="91f0a-115">Attributes</span></span>  
  
|<span data-ttu-id="91f0a-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="91f0a-116">Attribute</span></span>|<span data-ttu-id="91f0a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="91f0a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91f0a-118">— typ</span><span class="sxs-lookup"><span data-stu-id="91f0a-118">type</span></span>|<span data-ttu-id="91f0a-119">Określa typ (włącznie z przestrzenią nazw), nazwę zestawu, wersję, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="91f0a-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91f0a-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="91f0a-120">Child Elements</span></span>  
  
|<span data-ttu-id="91f0a-121">Element</span><span class="sxs-lookup"><span data-stu-id="91f0a-121">Element</span></span>|<span data-ttu-id="91f0a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="91f0a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91f0a-123">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="91f0a-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="91f0a-124">Określa indeks parametru, gdy deklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="91f0a-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91f0a-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="91f0a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="91f0a-126">Element</span><span class="sxs-lookup"><span data-stu-id="91f0a-126">Element</span></span>|<span data-ttu-id="91f0a-127">Opis</span><span class="sxs-lookup"><span data-stu-id="91f0a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91f0a-128">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="91f0a-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="91f0a-129">Dodaje deklarowany typ do kolekcji zadeklarowanych typów.</span><span class="sxs-lookup"><span data-stu-id="91f0a-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91f0a-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91f0a-130">Remarks</span></span>  
 <span data-ttu-id="91f0a-131">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="91f0a-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="91f0a-132">Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) przykład za pomocą tego elementu.</span><span class="sxs-lookup"><span data-stu-id="91f0a-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91f0a-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="91f0a-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91f0a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91f0a-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="91f0a-135">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="91f0a-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="91f0a-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="91f0a-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="91f0a-137">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="91f0a-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
