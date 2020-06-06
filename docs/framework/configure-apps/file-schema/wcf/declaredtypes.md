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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398062"
---
# \<declaredTypes>
<span data-ttu-id="395ec-101">Zawiera znane typy <xref:System.Runtime.Serialization.DataContractSerializer> używane podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="395ec-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="395ec-102">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="395ec-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="395ec-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="395ec-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="395ec-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="395ec-104">Attributes and Elements</span></span>  
 <span data-ttu-id="395ec-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="395ec-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="395ec-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="395ec-106">Attributes</span></span>  
 <span data-ttu-id="395ec-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="395ec-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="395ec-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="395ec-108">Child Elements</span></span>  
  
|<span data-ttu-id="395ec-109">Element</span><span class="sxs-lookup"><span data-stu-id="395ec-109">Element</span></span>|<span data-ttu-id="395ec-110">Opis</span><span class="sxs-lookup"><span data-stu-id="395ec-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="395ec-111">Dodaje typy, które wymagają znanych typów.</span><span class="sxs-lookup"><span data-stu-id="395ec-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="395ec-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="395ec-112">Parent Elements</span></span>  
  
|<span data-ttu-id="395ec-113">Element</span><span class="sxs-lookup"><span data-stu-id="395ec-113">Element</span></span>|<span data-ttu-id="395ec-114">Opis</span><span class="sxs-lookup"><span data-stu-id="395ec-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="395ec-115">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="395ec-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="395ec-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="395ec-116">Remarks</span></span>  
 <span data-ttu-id="395ec-117">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="395ec-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="395ec-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="395ec-118">Example</span></span>  
 <span data-ttu-id="395ec-119">Poniższy kod XML przedstawia zadeklarowane typy i znane typy dodawane do `DataContractSerializer` elementu.</span><span class="sxs-lookup"><span data-stu-id="395ec-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="395ec-120">W przykładzie pokazano trzy typy, które są dodawane.</span><span class="sxs-lookup"><span data-stu-id="395ec-120">The example shows three types being added.</span></span> <span data-ttu-id="395ec-121">Pierwszy jest typem niestandardowym o nazwie "Orders", który używa znanego typu o nazwie "Item".</span><span class="sxs-lookup"><span data-stu-id="395ec-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="395ec-122">Drugi zadeklarowany typ jest <xref:System.Collections.Generic.List%601> wykorzystywany `Item` jako typ znany.</span><span class="sxs-lookup"><span data-stu-id="395ec-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="395ec-123">Na koniec trzeci zadeklarowany typ to <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="395ec-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="395ec-124"><xref:System.Collections.Generic.Dictionary%602>Typ klasy jest typem ogólnym z dwoma parametrami typu.</span><span class="sxs-lookup"><span data-stu-id="395ec-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="395ec-125">Pierwszy reprezentuje klucz, a drugi reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="395ec-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="395ec-126">Poniższy przykład dodaje <xref:System.Collections.Generic.List%601> Typ sekundy (wartość) do listy znanych typów.</span><span class="sxs-lookup"><span data-stu-id="395ec-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="395ec-127">Należy użyć atrybutu, `index` Aby określić, który parametr typu ma być używany w znanym typie.</span><span class="sxs-lookup"><span data-stu-id="395ec-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="395ec-128">W takim przypadku typ wartości jest wskazywany przez atrybut indeksu ustawiony na wartość "1" (kolekcja jest różna od zera).</span><span class="sxs-lookup"><span data-stu-id="395ec-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="395ec-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="395ec-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="395ec-130">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="395ec-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
