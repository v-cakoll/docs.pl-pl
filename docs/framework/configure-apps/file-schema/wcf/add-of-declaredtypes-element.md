---
title: <add><declaredTypes> elementu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400656"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="50281-102">\<Dodaj > \<elementu declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="50281-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="50281-103">Dodaje typ używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="50281-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="50281-104">Każdy zadeklarowany typ zawiera znane typy, które będą zwracane jako pole lub właściwość zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="50281-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
<span data-ttu-id="50281-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="50281-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="50281-106">&nbsp;&nbsp;[ **\<> System. Runtime. Serialization**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="50281-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="50281-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="50281-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="50281-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="50281-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="50281-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="50281-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50281-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="50281-110">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50281-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="50281-111">Attributes and Elements</span></span>  
 <span data-ttu-id="50281-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="50281-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50281-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="50281-113">Attributes</span></span>  
  
|<span data-ttu-id="50281-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="50281-114">Attribute</span></span>|<span data-ttu-id="50281-115">Opis</span><span class="sxs-lookup"><span data-stu-id="50281-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50281-116">— typ</span><span class="sxs-lookup"><span data-stu-id="50281-116">type</span></span>|<span data-ttu-id="50281-117">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="50281-117">Required string attribute.</span></span><br /><br /> <span data-ttu-id="50281-118">Określa nazwę typu (w tym przestrzeń nazw), nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="50281-118">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50281-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="50281-119">Child Elements</span></span>  
  
|<span data-ttu-id="50281-120">Element</span><span class="sxs-lookup"><span data-stu-id="50281-120">Element</span></span>|<span data-ttu-id="50281-121">Opis</span><span class="sxs-lookup"><span data-stu-id="50281-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50281-122">\<> knownType</span><span class="sxs-lookup"><span data-stu-id="50281-122">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="50281-123">Określa znany typ zadeklarowanego typu, który jest dodawany.</span><span class="sxs-lookup"><span data-stu-id="50281-123">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="50281-124">Jeśli zadeklarowany typ jest typem ogólnym, należy również dodać element parametru do `<knownType>` elementu, aby określić, który parametr generyczny jest używany do zwrócenia znanego typu.</span><span class="sxs-lookup"><span data-stu-id="50281-124">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50281-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="50281-125">Parent Elements</span></span>  
  
|<span data-ttu-id="50281-126">Element</span><span class="sxs-lookup"><span data-stu-id="50281-126">Element</span></span>|<span data-ttu-id="50281-127">Opis</span><span class="sxs-lookup"><span data-stu-id="50281-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50281-128">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="50281-128">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="50281-129">Zawiera typy, które wymagają znanych typów podczas deserializacji przez <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="50281-129">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50281-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50281-130">Remarks</span></span>  
 <span data-ttu-id="50281-131">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="50281-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="50281-132">Zobacz [ \<> DataContractSerializer](datacontractserializer-element.md) , aby zapoznać się z przykładem użycia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="50281-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50281-133">Jeśli <xref:System.Object> typ zostanie dodany `<declaredType>`jako, <xref:System.Configuration.ConfigurationErrorsException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="50281-133">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="50281-134">Dzieje się tak, <xref:System.Object> ponieważ typ nie może być używany jako zadeklarowany typ w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="50281-134">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50281-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="50281-135">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="50281-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50281-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="50281-137">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="50281-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="50281-138">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="50281-138">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="50281-139">\<Dodawanie > \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="50281-139">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
