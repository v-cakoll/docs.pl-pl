---
title: <add> z <declaredTypes> — Element
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 9b280a63e85beac3231bc1a414430239bea4a1f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701115"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="d2c64-102">\<Dodaj > z \<declaredTypes > Element</span><span class="sxs-lookup"><span data-stu-id="d2c64-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="d2c64-103">Dodaje typ używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d2c64-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="d2c64-104">Każdy typ zadeklarowany zawiera znane typy, które zostaną zwrócone jako pole lub właściwość zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="d2c64-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="d2c64-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="d2c64-105">system.runtime.serialization</span></span>  
<span data-ttu-id="d2c64-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d2c64-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="d2c64-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="d2c64-107">\<declaredTypes></span></span>  
<span data-ttu-id="d2c64-108">\<Dodaj > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="d2c64-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c64-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2c64-109">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2c64-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d2c64-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d2c64-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d2c64-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2c64-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d2c64-112">Attributes</span></span>  
  
|<span data-ttu-id="d2c64-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d2c64-113">Attribute</span></span>|<span data-ttu-id="d2c64-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d2c64-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2c64-115">— typ</span><span class="sxs-lookup"><span data-stu-id="d2c64-115">type</span></span>|<span data-ttu-id="d2c64-116">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="d2c64-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="d2c64-117">Określa nazwę typu (włącznie z przestrzenią nazw), nazwę zestawu, numer wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="d2c64-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2c64-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d2c64-118">Child Elements</span></span>  
  
|<span data-ttu-id="d2c64-119">Element</span><span class="sxs-lookup"><span data-stu-id="d2c64-119">Element</span></span>|<span data-ttu-id="d2c64-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d2c64-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2c64-121">\<Element knownType ></span><span class="sxs-lookup"><span data-stu-id="d2c64-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="d2c64-122">Określa typ znany deklarowany typ, który jest dodawany.</span><span class="sxs-lookup"><span data-stu-id="d2c64-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="d2c64-123">Gdy deklarowany typ jest typem ogólnym, a następnie element parametru należy także dodać `<knownType>` elementu, aby określić, które parametrów ogólnych służy do zwracania znanego typu.</span><span class="sxs-lookup"><span data-stu-id="d2c64-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2c64-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d2c64-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d2c64-125">Element</span><span class="sxs-lookup"><span data-stu-id="d2c64-125">Element</span></span>|<span data-ttu-id="d2c64-126">Opis</span><span class="sxs-lookup"><span data-stu-id="d2c64-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2c64-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="d2c64-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="d2c64-128">Zawiera typy, które wymagają znanych typów podczas deserializacji, <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d2c64-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2c64-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2c64-129">Remarks</span></span>  
 <span data-ttu-id="d2c64-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d2c64-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d2c64-131">Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) na przykład przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="d2c64-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2c64-132">Jeśli dodasz <xref:System.Object> wpisać jako `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="d2c64-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="d2c64-133">Jest to spowodowane <xref:System.Object> typ nie może być używany jako zadeklarowanym typem w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d2c64-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2c64-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2c64-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2c64-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2c64-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="d2c64-136">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="d2c64-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="d2c64-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d2c64-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="d2c64-138">\<Dodaj > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="d2c64-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
