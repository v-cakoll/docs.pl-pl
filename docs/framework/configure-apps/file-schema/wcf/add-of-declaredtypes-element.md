---
title: <add><declaredTypes>elementu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400656"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="0c0a2-102">\<add>\<declaredTypes>elementu</span><span class="sxs-lookup"><span data-stu-id="0c0a2-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="0c0a2-103">Dodaje typ używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="0c0a2-104">Każdy zadeklarowany typ zawiera znane typy, które będą zwracane jako pole lub właściwość zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="0c0a2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c0a2-105">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c0a2-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0c0a2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0c0a2-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c0a2-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0c0a2-108">Attributes</span></span>  
  
|<span data-ttu-id="0c0a2-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0c0a2-109">Attribute</span></span>|<span data-ttu-id="0c0a2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0c0a2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c0a2-111">typ</span><span class="sxs-lookup"><span data-stu-id="0c0a2-111">type</span></span>|<span data-ttu-id="0c0a2-112">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="0c0a2-113">Określa nazwę typu (w tym przestrzeń nazw), nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-113">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c0a2-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0c0a2-114">Child Elements</span></span>  
  
|<span data-ttu-id="0c0a2-115">Element</span><span class="sxs-lookup"><span data-stu-id="0c0a2-115">Element</span></span>|<span data-ttu-id="0c0a2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0c0a2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="0c0a2-117">Określa znany typ zadeklarowanego typu, który jest dodawany.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-117">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="0c0a2-118">Jeśli zadeklarowany typ jest typem ogólnym, należy również dodać element parametru do `<knownType>` elementu, aby określić, który parametr generyczny jest używany do zwrócenia znanego typu.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-118">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c0a2-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0c0a2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0c0a2-120">Element</span><span class="sxs-lookup"><span data-stu-id="0c0a2-120">Element</span></span>|<span data-ttu-id="0c0a2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0c0a2-121">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="0c0a2-122">Zawiera typy, które wymagają znanych typów podczas deserializacji przez <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0c0a2-122">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c0a2-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c0a2-123">Remarks</span></span>  
 <span data-ttu-id="0c0a2-124">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0c0a2-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="0c0a2-125">Zobacz, [\<dataContractSerializer>](datacontractserializer-element.md) Aby zapoznać się z przykładem użycia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-125">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c0a2-126">Jeśli typ zostanie dodany <xref:System.Object> jako `<declaredType>` , <xref:System.Configuration.ConfigurationErrorsException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-126">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="0c0a2-127">Dzieje się tak, ponieważ <xref:System.Object> Typ nie może być używany jako zadeklarowany typ w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0c0a2-127">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c0a2-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c0a2-128">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c0a2-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c0a2-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="0c0a2-130">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="0c0a2-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="0c0a2-131">\<add>z\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="0c0a2-131">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
