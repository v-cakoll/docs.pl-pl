---
title: Element &lt;MethodInstantiation&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 37e3ff3e792b8067b6d9409d799cf6e30350606a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="443dd-102">Element &lt;MethodInstantiation&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="443dd-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="443dd-103">Stosuje zasad wykonywania odbicia do skonstruowanego metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="443dd-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="443dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="443dd-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="443dd-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="443dd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="443dd-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="443dd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="443dd-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="443dd-107">Attributes</span></span>  
  
|<span data-ttu-id="443dd-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="443dd-108">Attribute</span></span>|<span data-ttu-id="443dd-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="443dd-109">Attribute type</span></span>|<span data-ttu-id="443dd-110">Opis</span><span class="sxs-lookup"><span data-stu-id="443dd-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="443dd-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="443dd-111">General</span></span>|<span data-ttu-id="443dd-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="443dd-112">Required attribute.</span></span> <span data-ttu-id="443dd-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="443dd-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="443dd-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="443dd-114">General</span></span>|<span data-ttu-id="443dd-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="443dd-115">Optional attribute.</span></span> <span data-ttu-id="443dd-116">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="443dd-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="443dd-117">Wiele nazwanych parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="443dd-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="443dd-118">`Signature` Atrybut służy do rozróżnienia przeciążonej metody.</span><span class="sxs-lookup"><span data-stu-id="443dd-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="443dd-119">Ogólne</span><span class="sxs-lookup"><span data-stu-id="443dd-119">General</span></span>|<span data-ttu-id="443dd-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="443dd-120">Required attribute.</span></span> <span data-ttu-id="443dd-121">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="443dd-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="443dd-122">Jeśli podano wiele argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="443dd-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="443dd-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="443dd-123">Reflection</span></span>|<span data-ttu-id="443dd-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="443dd-124">Optional attribute.</span></span> <span data-ttu-id="443dd-125">Określa, czy podczas badania informacji dotyczących metody wyliczania, jednak nie wszystkie wywołania dynamicznej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="443dd-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="443dd-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="443dd-126">Reflection</span></span>|<span data-ttu-id="443dd-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="443dd-127">Optional attribute.</span></span> <span data-ttu-id="443dd-128">Sterowanie dostępem środowiska uruchomieniowego do konstruktora lub metody, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="443dd-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="443dd-129">Ta zasada zapewnia, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="443dd-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="443dd-130">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="443dd-130">Name attribute</span></span>  
  
|<span data-ttu-id="443dd-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="443dd-131">Value</span></span>|<span data-ttu-id="443dd-132">Opis</span><span class="sxs-lookup"><span data-stu-id="443dd-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="443dd-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="443dd-133">*method_name*</span></span>|<span data-ttu-id="443dd-134">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="443dd-134">The method name.</span></span> <span data-ttu-id="443dd-135">Typ metody jest określany przez element nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="443dd-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="443dd-136">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="443dd-136">Signature attribute</span></span>  
  
|<span data-ttu-id="443dd-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="443dd-137">Value</span></span>|<span data-ttu-id="443dd-138">Opis</span><span class="sxs-lookup"><span data-stu-id="443dd-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="443dd-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="443dd-139">*method_signature*</span></span>|<span data-ttu-id="443dd-140">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="443dd-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="443dd-141">Jeśli podano wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="443dd-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="443dd-142">Argumentów atrybutu</span><span class="sxs-lookup"><span data-stu-id="443dd-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="443dd-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="443dd-143">Value</span></span>|<span data-ttu-id="443dd-144">Opis</span><span class="sxs-lookup"><span data-stu-id="443dd-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="443dd-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="443dd-145">*method_arguments*</span></span>|<span data-ttu-id="443dd-146">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="443dd-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="443dd-147">Jeśli podano wiele argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="443dd-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="443dd-148">Każdy argument musi zawierać nazwę FQDN typu.</span><span class="sxs-lookup"><span data-stu-id="443dd-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="443dd-149">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="443dd-149">All other attributes</span></span>  
  
|<span data-ttu-id="443dd-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="443dd-150">Value</span></span>|<span data-ttu-id="443dd-151">Opis</span><span class="sxs-lookup"><span data-stu-id="443dd-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="443dd-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="443dd-152">*policy_setting*</span></span>|<span data-ttu-id="443dd-153">To ustawienie, aby zastosować do tego typu w metodzie.</span><span class="sxs-lookup"><span data-stu-id="443dd-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="443dd-154">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="443dd-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="443dd-155">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="443dd-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="443dd-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="443dd-156">Child Elements</span></span>  
 <span data-ttu-id="443dd-157">Brak.</span><span class="sxs-lookup"><span data-stu-id="443dd-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="443dd-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="443dd-158">Parent Elements</span></span>  
  
|<span data-ttu-id="443dd-159">Element</span><span class="sxs-lookup"><span data-stu-id="443dd-159">Element</span></span>|<span data-ttu-id="443dd-160">Opis</span><span class="sxs-lookup"><span data-stu-id="443dd-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="443dd-161">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="443dd-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="443dd-162">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="443dd-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="443dd-163">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="443dd-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="443dd-164">Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="443dd-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="443dd-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="443dd-165">Remarks</span></span>  
 <span data-ttu-id="443dd-166">`<MethodInstantiation>` Element zastępuje zasad odbicia wykonywania odpowiednich Otwórz metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="443dd-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443dd-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="443dd-167">See Also</span></span>  
 [<span data-ttu-id="443dd-168">Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="443dd-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="443dd-169">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="443dd-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="443dd-170">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="443dd-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="443dd-171">\<Metoda > — Element</span><span class="sxs-lookup"><span data-stu-id="443dd-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
