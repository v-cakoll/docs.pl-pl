---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 138bc800625a8334d692bd46a3ceb7dfe2ea4ae1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdeclaredtypesgt"></a><span data-ttu-id="3ddb3-102">&lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="3ddb3-102">&lt;declaredTypes&gt;</span></span>
<span data-ttu-id="3ddb3-103">Zawiera znane typy, które <xref:System.Runtime.Serialization.DataContractSerializer> używa podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-103">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="3ddb3-104">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="3ddb3-104">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="3ddb3-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="3ddb3-105">system.runtime.serialization</span></span>  
<span data-ttu-id="3ddb3-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3ddb3-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="3ddb3-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="3ddb3-107">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ddb3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ddb3-108">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
                <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ddb3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ddb3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3ddb3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ddb3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ddb3-111">Attributes</span></span>  
 <span data-ttu-id="3ddb3-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ddb3-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ddb3-113">Child Elements</span></span>  
  
|<span data-ttu-id="3ddb3-114">Element</span><span class="sxs-lookup"><span data-stu-id="3ddb3-114">Element</span></span>|<span data-ttu-id="3ddb3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3ddb3-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ddb3-116">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="3ddb3-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="3ddb3-117">Dodaje typy, które wymagają znanych typów.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ddb3-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ddb3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3ddb3-119">Element</span><span class="sxs-lookup"><span data-stu-id="3ddb3-119">Element</span></span>|<span data-ttu-id="3ddb3-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3ddb3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ddb3-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3ddb3-121">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="3ddb3-122">Zawiera dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ddb3-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ddb3-123">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="3ddb3-124">znane typy, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-124"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ddb3-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ddb3-125">Example</span></span>  
 <span data-ttu-id="3ddb3-126">Następujący kod XML zawiera typy zadeklarowane i znanych typów dodane do `DataContractSerializer` elementu.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="3ddb3-127">W przykładzie trzy typy dodawany.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-127">The example shows three types being added.</span></span> <span data-ttu-id="3ddb3-128">Pierwsza to typ niestandardowy o nazwie "Zamówienia" używającej znanego typu o nazwie "Item".</span><span class="sxs-lookup"><span data-stu-id="3ddb3-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="3ddb3-129">Drugi zadeklarowany typ jest <xref:System.Collections.Generic.List%601> używającą `Item` jako znanego typu.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="3ddb3-130">Na koniec trzeci zadeklarowany jako typ jest <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="3ddb3-131"><xref:System.Collections.Generic.Dictionary%602> Typu klasy jest typem ogólnym, dwa typy parametrów.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="3ddb3-132">Pierwszy reprezentuje klucz, a druga wartość.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="3ddb3-133">W poniższym przykładzie dodano <xref:System.Collections.Generic.List%601> drugiego typu (wartość) do listy znanych typów.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="3ddb3-134">Należy użyć `index` atrybutu, aby określić, którego parametr typu do użycia w znanym typem.</span><span class="sxs-lookup"><span data-stu-id="3ddb3-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="3ddb3-135">W takim przypadku typ wartości jest określane przez atrybut indeksu, ustaw wartość "1" (kolekcja jest liczony od zera).</span><span class="sxs-lookup"><span data-stu-id="3ddb3-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
            <parameter index="1"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ddb3-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ddb3-136">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="3ddb3-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3ddb3-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="3ddb3-138">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="3ddb3-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="3ddb3-139">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="3ddb3-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
