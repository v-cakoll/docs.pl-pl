---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: cef34a8836c7b17fe9a85cac190090f42653df14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919255"
---
# <a name="declaredtypes"></a><span data-ttu-id="2abca-101">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="2abca-101">\<declaredTypes></span></span>
<span data-ttu-id="2abca-102">Zawiera znane typy <xref:System.Runtime.Serialization.DataContractSerializer> używane podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="2abca-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="2abca-103">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="2abca-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="2abca-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="2abca-104">system.runtime.serialization</span></span>  
<span data-ttu-id="2abca-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="2abca-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="2abca-106">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="2abca-106">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2abca-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2abca-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2abca-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2abca-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2abca-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2abca-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2abca-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2abca-110">Attributes</span></span>  
 <span data-ttu-id="2abca-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="2abca-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2abca-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2abca-112">Child Elements</span></span>  
  
|<span data-ttu-id="2abca-113">Element</span><span class="sxs-lookup"><span data-stu-id="2abca-113">Element</span></span>|<span data-ttu-id="2abca-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2abca-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2abca-115">\<add></span><span class="sxs-lookup"><span data-stu-id="2abca-115">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="2abca-116">Dodaje typy, które wymagają znanych typów.</span><span class="sxs-lookup"><span data-stu-id="2abca-116">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2abca-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2abca-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2abca-118">Element</span><span class="sxs-lookup"><span data-stu-id="2abca-118">Element</span></span>|<span data-ttu-id="2abca-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2abca-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2abca-120">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="2abca-120">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="2abca-121">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2abca-121">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2abca-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2abca-122">Remarks</span></span>  
 <span data-ttu-id="2abca-123">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2abca-123">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2abca-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="2abca-124">Example</span></span>  
 <span data-ttu-id="2abca-125">Poniższy kod XML przedstawia zadeklarowane typy i znane typy dodawane do `DataContractSerializer` elementu.</span><span class="sxs-lookup"><span data-stu-id="2abca-125">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="2abca-126">W przykładzie pokazano trzy typy, które są dodawane.</span><span class="sxs-lookup"><span data-stu-id="2abca-126">The example shows three types being added.</span></span> <span data-ttu-id="2abca-127">Pierwszy jest typem niestandardowym o nazwie "Orders", który używa znanego typu o nazwie "Item".</span><span class="sxs-lookup"><span data-stu-id="2abca-127">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="2abca-128">Drugi zadeklarowany typ jest <xref:System.Collections.Generic.List%601> wykorzystywany `Item` jako typ znany.</span><span class="sxs-lookup"><span data-stu-id="2abca-128">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="2abca-129">Na koniec trzeci zadeklarowany typ to <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="2abca-129">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="2abca-130">Typ <xref:System.Collections.Generic.Dictionary%602> klasy jest typem ogólnym z dwoma parametrami typu.</span><span class="sxs-lookup"><span data-stu-id="2abca-130">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="2abca-131">Pierwszy reprezentuje klucz, a drugi reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="2abca-131">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="2abca-132">Poniższy przykład dodaje <xref:System.Collections.Generic.List%601> typ sekundy (wartość) do listy znanych typów.</span><span class="sxs-lookup"><span data-stu-id="2abca-132">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="2abca-133">Należy użyć atrybutu, `index` aby określić, który parametr typu ma być używany w znanym typie.</span><span class="sxs-lookup"><span data-stu-id="2abca-133">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="2abca-134">W takim przypadku typ wartości jest wskazywany przez atrybut indeksu ustawiony na wartość "1" (kolekcja jest różna od zera).</span><span class="sxs-lookup"><span data-stu-id="2abca-134">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2abca-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2abca-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="2abca-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="2abca-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="2abca-137">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="2abca-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="2abca-138">\<add></span><span class="sxs-lookup"><span data-stu-id="2abca-138">\<add></span></span>](add-of-declaredtypes-element.md)
