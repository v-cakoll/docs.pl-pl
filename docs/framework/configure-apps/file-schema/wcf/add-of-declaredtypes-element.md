---
title: <add><declaredTypes> elementu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 1ea008dcc72d555b00e9648ace95bb9522ffc2c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920186"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="a07d1-102">\<Dodaj > \<elementu declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="a07d1-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="a07d1-103">Dodaje typ używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="a07d1-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="a07d1-104">Każdy zadeklarowany typ zawiera znane typy, które będą zwracane jako pole lub właściwość zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="a07d1-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="a07d1-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="a07d1-105">system.runtime.serialization</span></span>  
<span data-ttu-id="a07d1-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="a07d1-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="a07d1-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="a07d1-107">\<declaredTypes></span></span>  
<span data-ttu-id="a07d1-108">\<Dodawanie > \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="a07d1-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a07d1-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a07d1-109">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a07d1-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a07d1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a07d1-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a07d1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a07d1-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a07d1-112">Attributes</span></span>  
  
|<span data-ttu-id="a07d1-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a07d1-113">Attribute</span></span>|<span data-ttu-id="a07d1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a07d1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a07d1-115">— typ</span><span class="sxs-lookup"><span data-stu-id="a07d1-115">type</span></span>|<span data-ttu-id="a07d1-116">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="a07d1-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="a07d1-117">Określa nazwę typu (w tym przestrzeń nazw), nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="a07d1-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a07d1-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a07d1-118">Child Elements</span></span>  
  
|<span data-ttu-id="a07d1-119">Element</span><span class="sxs-lookup"><span data-stu-id="a07d1-119">Element</span></span>|<span data-ttu-id="a07d1-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a07d1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a07d1-121">\<> knownType</span><span class="sxs-lookup"><span data-stu-id="a07d1-121">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="a07d1-122">Określa znany typ zadeklarowanego typu, który jest dodawany.</span><span class="sxs-lookup"><span data-stu-id="a07d1-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="a07d1-123">Jeśli zadeklarowany typ jest typem ogólnym, należy również dodać element parametru do `<knownType>` elementu, aby określić, który parametr generyczny jest używany do zwrócenia znanego typu.</span><span class="sxs-lookup"><span data-stu-id="a07d1-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a07d1-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a07d1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a07d1-125">Element</span><span class="sxs-lookup"><span data-stu-id="a07d1-125">Element</span></span>|<span data-ttu-id="a07d1-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a07d1-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a07d1-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="a07d1-127">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="a07d1-128">Zawiera typy, które wymagają znanych typów podczas deserializacji przez <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a07d1-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a07d1-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a07d1-129">Remarks</span></span>  
 <span data-ttu-id="a07d1-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a07d1-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="a07d1-131">Zobacz [ \<> DataContractSerializer](datacontractserializer-element.md) , aby zapoznać się z przykładem użycia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="a07d1-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a07d1-132">Jeśli <xref:System.Object> typ zostanie dodany `<declaredType>`jako, <xref:System.Configuration.ConfigurationErrorsException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="a07d1-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="a07d1-133">Dzieje się tak, <xref:System.Object> ponieważ typ nie może być używany jako zadeklarowany typ w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a07d1-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a07d1-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="a07d1-134">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="a07d1-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a07d1-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="a07d1-136">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="a07d1-136">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="a07d1-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="a07d1-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="a07d1-138">\<Dodawanie > \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="a07d1-138">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
