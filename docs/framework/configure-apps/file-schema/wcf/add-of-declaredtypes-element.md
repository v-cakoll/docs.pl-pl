---
title: '&lt;add&gt; w &lt;declaredTypes&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71f9c2b45f631eb2d9021254d2866f0092ebb079
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a><span data-ttu-id="40a79-102">&lt;add&gt; w &lt;declaredTypes&gt;, element</span><span class="sxs-lookup"><span data-stu-id="40a79-102">&lt;add&gt; of &lt;declaredTypes&gt; Element</span></span>
<span data-ttu-id="40a79-103">Dodaje typ używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="40a79-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="40a79-104">Każdego rodzaju zawiera znane typy, które zostaną zwrócone jako pole lub właściwość deklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="40a79-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="40a79-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="40a79-105">system.runtime.serialization</span></span>  
<span data-ttu-id="40a79-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="40a79-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="40a79-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="40a79-107">\<declaredTypes></span></span>  
<span data-ttu-id="40a79-108">\<Dodaj > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="40a79-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40a79-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="40a79-109">Syntax</span></span>  
  
```xml  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40a79-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="40a79-110">Attributes and Elements</span></span>  
 <span data-ttu-id="40a79-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="40a79-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40a79-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="40a79-112">Attributes</span></span>  
  
|<span data-ttu-id="40a79-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="40a79-113">Attribute</span></span>|<span data-ttu-id="40a79-114">Opis</span><span class="sxs-lookup"><span data-stu-id="40a79-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="40a79-115">— typ</span><span class="sxs-lookup"><span data-stu-id="40a79-115">type</span></span>|<span data-ttu-id="40a79-116">Atrybut wymaganych parametrów.</span><span class="sxs-lookup"><span data-stu-id="40a79-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="40a79-117">Określa nazwę typu (włącznie z przestrzenią nazw), nazwę zestawu, numer wersji, kultury i tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="40a79-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40a79-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="40a79-118">Child Elements</span></span>  
  
|<span data-ttu-id="40a79-119">Element</span><span class="sxs-lookup"><span data-stu-id="40a79-119">Element</span></span>|<span data-ttu-id="40a79-120">Opis</span><span class="sxs-lookup"><span data-stu-id="40a79-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40a79-121">\<Typ knownType ></span><span class="sxs-lookup"><span data-stu-id="40a79-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="40a79-122">Określa typ znanego deklarowanego typu, który jest dodawany.</span><span class="sxs-lookup"><span data-stu-id="40a79-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="40a79-123">Gdy deklarowany typ jest typem ogólnym, a następnie musi również dodany element parametru `<knownType>` element, aby określić, które parametru ogólnego służy do zwracania znanego typu.</span><span class="sxs-lookup"><span data-stu-id="40a79-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40a79-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="40a79-124">Parent Elements</span></span>  
  
|<span data-ttu-id="40a79-125">Element</span><span class="sxs-lookup"><span data-stu-id="40a79-125">Element</span></span>|<span data-ttu-id="40a79-126">Opis</span><span class="sxs-lookup"><span data-stu-id="40a79-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40a79-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="40a79-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="40a79-128">Zawiera typy, które wymagają znane typy podczas deserializacji przez <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="40a79-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40a79-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40a79-129">Remarks</span></span>  
 <span data-ttu-id="40a79-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="40a79-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="40a79-131">Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) przykład za pomocą tego elementu.</span><span class="sxs-lookup"><span data-stu-id="40a79-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40a79-132">Jeśli dodasz <xref:System.Object> wpisać jako `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="40a79-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="40a79-133">Jest to spowodowane <xref:System.Object> typu nie można użyć jako deklarowanego typu w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="40a79-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a79-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="40a79-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40a79-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40a79-135">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="40a79-136">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="40a79-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="40a79-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="40a79-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="40a79-138">\<Dodaj > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="40a79-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
