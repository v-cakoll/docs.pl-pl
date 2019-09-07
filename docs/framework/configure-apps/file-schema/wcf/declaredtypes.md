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
ms.openlocfilehash: c45a4e67d0a2d98c0e9c1a91e07f25b81370244c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398062"
---
# <a name="declaredtypes"></a><span data-ttu-id="8628d-101">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="8628d-101">\<declaredTypes></span></span>
<span data-ttu-id="8628d-102">Zawiera znane typy <xref:System.Runtime.Serialization.DataContractSerializer> używane podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="8628d-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="8628d-103">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="8628d-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="8628d-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8628d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8628d-105">&nbsp;&nbsp;[ **\<> System. Runtime. Serialization**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="8628d-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="8628d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="8628d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="8628d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<declaredTypes >**</span><span class="sxs-lookup"><span data-stu-id="8628d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8628d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="8628d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8628d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8628d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8628d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8628d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8628d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8628d-111">Attributes</span></span>  
 <span data-ttu-id="8628d-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="8628d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8628d-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8628d-113">Child Elements</span></span>  
  
|<span data-ttu-id="8628d-114">Element</span><span class="sxs-lookup"><span data-stu-id="8628d-114">Element</span></span>|<span data-ttu-id="8628d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8628d-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8628d-116">\<add></span><span class="sxs-lookup"><span data-stu-id="8628d-116">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="8628d-117">Dodaje typy, które wymagają znanych typów.</span><span class="sxs-lookup"><span data-stu-id="8628d-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8628d-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8628d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8628d-119">Element</span><span class="sxs-lookup"><span data-stu-id="8628d-119">Element</span></span>|<span data-ttu-id="8628d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="8628d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8628d-121">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="8628d-121">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="8628d-122">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8628d-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8628d-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8628d-123">Remarks</span></span>  
 <span data-ttu-id="8628d-124">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8628d-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8628d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="8628d-125">Example</span></span>  
 <span data-ttu-id="8628d-126">Poniższy kod XML przedstawia zadeklarowane typy i znane typy dodawane do `DataContractSerializer` elementu.</span><span class="sxs-lookup"><span data-stu-id="8628d-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="8628d-127">W przykładzie pokazano trzy typy, które są dodawane.</span><span class="sxs-lookup"><span data-stu-id="8628d-127">The example shows three types being added.</span></span> <span data-ttu-id="8628d-128">Pierwszy jest typem niestandardowym o nazwie "Orders", który używa znanego typu o nazwie "Item".</span><span class="sxs-lookup"><span data-stu-id="8628d-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="8628d-129">Drugi zadeklarowany typ jest <xref:System.Collections.Generic.List%601> wykorzystywany `Item` jako typ znany.</span><span class="sxs-lookup"><span data-stu-id="8628d-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="8628d-130">Na koniec trzeci zadeklarowany typ to <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="8628d-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="8628d-131">Typ <xref:System.Collections.Generic.Dictionary%602> klasy jest typem ogólnym z dwoma parametrami typu.</span><span class="sxs-lookup"><span data-stu-id="8628d-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="8628d-132">Pierwszy reprezentuje klucz, a drugi reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="8628d-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="8628d-133">Poniższy przykład dodaje <xref:System.Collections.Generic.List%601> typ sekundy (wartość) do listy znanych typów.</span><span class="sxs-lookup"><span data-stu-id="8628d-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="8628d-134">Należy użyć atrybutu, `index` aby określić, który parametr typu ma być używany w znanym typie.</span><span class="sxs-lookup"><span data-stu-id="8628d-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="8628d-135">W takim przypadku typ wartości jest wskazywany przez atrybut indeksu ustawiony na wartość "1" (kolekcja jest różna od zera).</span><span class="sxs-lookup"><span data-stu-id="8628d-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8628d-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8628d-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="8628d-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="8628d-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="8628d-138">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="8628d-138">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="8628d-139">\<add></span><span class="sxs-lookup"><span data-stu-id="8628d-139">\<add></span></span>](add-of-declaredtypes-element.md)
