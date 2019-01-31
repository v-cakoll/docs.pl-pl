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
ms.openlocfilehash: d347afb183b23410359a0972d7fd3b1f851971bd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264998"
---
# <a name="declaredtypes"></a><span data-ttu-id="0530d-101">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="0530d-101">\<declaredTypes></span></span>
<span data-ttu-id="0530d-102">Zawiera znane typy, które <xref:System.Runtime.Serialization.DataContractSerializer> używa podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="0530d-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="0530d-103">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="0530d-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="0530d-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="0530d-104">system.runtime.serialization</span></span>  
<span data-ttu-id="0530d-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="0530d-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="0530d-106">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="0530d-106">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0530d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0530d-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0530d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0530d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0530d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0530d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0530d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0530d-110">Attributes</span></span>  
 <span data-ttu-id="0530d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="0530d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0530d-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0530d-112">Child Elements</span></span>  
  
|<span data-ttu-id="0530d-113">Element</span><span class="sxs-lookup"><span data-stu-id="0530d-113">Element</span></span>|<span data-ttu-id="0530d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0530d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0530d-115">\<add></span><span class="sxs-lookup"><span data-stu-id="0530d-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="0530d-116">Dodaje typy, które wymagają znane typy.</span><span class="sxs-lookup"><span data-stu-id="0530d-116">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0530d-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0530d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0530d-118">Element</span><span class="sxs-lookup"><span data-stu-id="0530d-118">Element</span></span>|<span data-ttu-id="0530d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="0530d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0530d-120">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="0530d-120">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="0530d-121">Zawierająca dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0530d-121">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0530d-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0530d-122">Remarks</span></span>  
 <span data-ttu-id="0530d-123">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0530d-123">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0530d-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="0530d-124">Example</span></span>  
 <span data-ttu-id="0530d-125">Następujący kod XML przedstawiono typy zadeklarowane i znanych typów, które dodano do `DataContractSerializer` elementu.</span><span class="sxs-lookup"><span data-stu-id="0530d-125">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="0530d-126">W przykładzie pokazano trzy typy dodawany.</span><span class="sxs-lookup"><span data-stu-id="0530d-126">The example shows three types being added.</span></span> <span data-ttu-id="0530d-127">Pierwszy to typ niestandardowy o nazwie "Orders", który używa znany typ o nazwie "Item".</span><span class="sxs-lookup"><span data-stu-id="0530d-127">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="0530d-128">Drugi zadeklarowany typ jest <xref:System.Collections.Generic.List%601> , który używa `Item` jako znanego typu.</span><span class="sxs-lookup"><span data-stu-id="0530d-128">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="0530d-129">Na koniec trzeciego zadeklarowany typ jest <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="0530d-129">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="0530d-130"><xref:System.Collections.Generic.Dictionary%602> Typem klasy jest typ ogólny, z parametrami typu dwa.</span><span class="sxs-lookup"><span data-stu-id="0530d-130">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="0530d-131">Pierwszy reprezentuje klucz, a druga wartość.</span><span class="sxs-lookup"><span data-stu-id="0530d-131">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="0530d-132">W poniższym przykładzie dodano <xref:System.Collections.Generic.List%601> drugiego typu (wartość) do listy znanych typów.</span><span class="sxs-lookup"><span data-stu-id="0530d-132">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="0530d-133">Należy użyć `index` atrybutu, aby określić które parametr typu do użycia w znanego typu.</span><span class="sxs-lookup"><span data-stu-id="0530d-133">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="0530d-134">W tym przypadku typ wartości jest wskazywany przez indeks atrybut ustawiony na wartość "1" (kolekcja jest liczony od zera).</span><span class="sxs-lookup"><span data-stu-id="0530d-134">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0530d-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0530d-135">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="0530d-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="0530d-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="0530d-137">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="0530d-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="0530d-138">\<add></span><span class="sxs-lookup"><span data-stu-id="0530d-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
