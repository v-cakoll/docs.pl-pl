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
ms.workload: dotnet
ms.openlocfilehash: c888bf806744c5c62d130ec00b89838c52f67d0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="fa3cc-102">Element &lt;MethodInstantiation&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="fa3cc-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="fa3cc-103">Stosuje zasad wykonywania odbicia do skonstruowanego metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa3cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa3cc-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa3cc-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fa3cc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fa3cc-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa3cc-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fa3cc-107">Attributes</span></span>  
  
|<span data-ttu-id="fa3cc-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fa3cc-108">Attribute</span></span>|<span data-ttu-id="fa3cc-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="fa3cc-109">Attribute type</span></span>|<span data-ttu-id="fa3cc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fa3cc-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="fa3cc-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="fa3cc-111">General</span></span>|<span data-ttu-id="fa3cc-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-112">Required attribute.</span></span> <span data-ttu-id="fa3cc-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="fa3cc-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="fa3cc-114">General</span></span>|<span data-ttu-id="fa3cc-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-115">Optional attribute.</span></span> <span data-ttu-id="fa3cc-116">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="fa3cc-117">Wiele nazwanych parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="fa3cc-118">`Signature` Atrybut służy do rozróżnienia przeciążonej metody.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="fa3cc-119">Ogólne</span><span class="sxs-lookup"><span data-stu-id="fa3cc-119">General</span></span>|<span data-ttu-id="fa3cc-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-120">Required attribute.</span></span> <span data-ttu-id="fa3cc-121">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="fa3cc-122">Jeśli podano wiele argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="fa3cc-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="fa3cc-123">Reflection</span></span>|<span data-ttu-id="fa3cc-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-124">Optional attribute.</span></span> <span data-ttu-id="fa3cc-125">Określa, czy podczas badania informacji dotyczących metody wyliczania, jednak nie wszystkie wywołania dynamicznej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="fa3cc-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="fa3cc-126">Reflection</span></span>|<span data-ttu-id="fa3cc-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-127">Optional attribute.</span></span> <span data-ttu-id="fa3cc-128">Sterowanie dostępem środowiska uruchomieniowego do konstruktora lub metody, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="fa3cc-129">Ta zasada zapewnia, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="fa3cc-130">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="fa3cc-130">Name attribute</span></span>  
  
|<span data-ttu-id="fa3cc-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="fa3cc-131">Value</span></span>|<span data-ttu-id="fa3cc-132">Opis</span><span class="sxs-lookup"><span data-stu-id="fa3cc-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fa3cc-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="fa3cc-133">*method_name*</span></span>|<span data-ttu-id="fa3cc-134">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-134">The method name.</span></span> <span data-ttu-id="fa3cc-135">Typ metody jest określany przez element nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="fa3cc-136">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="fa3cc-136">Signature attribute</span></span>  
  
|<span data-ttu-id="fa3cc-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="fa3cc-137">Value</span></span>|<span data-ttu-id="fa3cc-138">Opis</span><span class="sxs-lookup"><span data-stu-id="fa3cc-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fa3cc-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="fa3cc-139">*method_signature*</span></span>|<span data-ttu-id="fa3cc-140">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="fa3cc-141">Jeśli podano wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="fa3cc-142">Argumentów atrybutu</span><span class="sxs-lookup"><span data-stu-id="fa3cc-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="fa3cc-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="fa3cc-143">Value</span></span>|<span data-ttu-id="fa3cc-144">Opis</span><span class="sxs-lookup"><span data-stu-id="fa3cc-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fa3cc-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="fa3cc-145">*method_arguments*</span></span>|<span data-ttu-id="fa3cc-146">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="fa3cc-147">Jeśli podano wiele argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="fa3cc-148">Każdy argument musi zawierać nazwę FQDN typu.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="fa3cc-149">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="fa3cc-149">All other attributes</span></span>  
  
|<span data-ttu-id="fa3cc-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="fa3cc-150">Value</span></span>|<span data-ttu-id="fa3cc-151">Opis</span><span class="sxs-lookup"><span data-stu-id="fa3cc-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fa3cc-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="fa3cc-152">*policy_setting*</span></span>|<span data-ttu-id="fa3cc-153">To ustawienie, aby zastosować do tego typu w metodzie.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="fa3cc-154">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="fa3cc-155">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="fa3cc-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa3cc-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fa3cc-156">Child Elements</span></span>  
 <span data-ttu-id="fa3cc-157">Brak.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa3cc-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fa3cc-158">Parent Elements</span></span>  
  
|<span data-ttu-id="fa3cc-159">Element</span><span class="sxs-lookup"><span data-stu-id="fa3cc-159">Element</span></span>|<span data-ttu-id="fa3cc-160">Opis</span><span class="sxs-lookup"><span data-stu-id="fa3cc-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa3cc-161">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="fa3cc-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="fa3cc-162">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="fa3cc-163">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="fa3cc-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="fa3cc-164">Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa3cc-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa3cc-165">Remarks</span></span>  
 <span data-ttu-id="fa3cc-166">`<MethodInstantiation>` Element zastępuje zasad odbicia wykonywania odpowiednich Otwórz metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa3cc-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa3cc-167">See Also</span></span>  
 [<span data-ttu-id="fa3cc-168">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="fa3cc-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="fa3cc-169">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fa3cc-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="fa3cc-170">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fa3cc-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="fa3cc-171">\<Metoda > — Element</span><span class="sxs-lookup"><span data-stu-id="fa3cc-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
