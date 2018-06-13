---
title: Element &lt;MethodInstantiation&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d741e8df8f2b8c6d90a1d867c73495a2ffd1304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397796"
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="20e6f-102">Element &lt;MethodInstantiation&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="20e6f-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="20e6f-103">Stosuje zasad wykonywania odbicia do skonstruowanego metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="20e6f-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e6f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20e6f-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20e6f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="20e6f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="20e6f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="20e6f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20e6f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="20e6f-107">Attributes</span></span>  
  
|<span data-ttu-id="20e6f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="20e6f-108">Attribute</span></span>|<span data-ttu-id="20e6f-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="20e6f-109">Attribute type</span></span>|<span data-ttu-id="20e6f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="20e6f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="20e6f-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="20e6f-111">General</span></span>|<span data-ttu-id="20e6f-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="20e6f-112">Required attribute.</span></span> <span data-ttu-id="20e6f-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="20e6f-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="20e6f-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="20e6f-114">General</span></span>|<span data-ttu-id="20e6f-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="20e6f-115">Optional attribute.</span></span> <span data-ttu-id="20e6f-116">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="20e6f-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="20e6f-117">Wiele nazwanych parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="20e6f-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="20e6f-118">`Signature` Atrybut służy do rozróżnienia przeciążonej metody.</span><span class="sxs-lookup"><span data-stu-id="20e6f-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="20e6f-119">Ogólne</span><span class="sxs-lookup"><span data-stu-id="20e6f-119">General</span></span>|<span data-ttu-id="20e6f-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="20e6f-120">Required attribute.</span></span> <span data-ttu-id="20e6f-121">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="20e6f-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="20e6f-122">Jeśli podano wiele argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="20e6f-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="20e6f-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="20e6f-123">Reflection</span></span>|<span data-ttu-id="20e6f-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="20e6f-124">Optional attribute.</span></span> <span data-ttu-id="20e6f-125">Określa, czy podczas badania informacji dotyczących metody wyliczania, jednak nie wszystkie wywołania dynamicznej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="20e6f-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="20e6f-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="20e6f-126">Reflection</span></span>|<span data-ttu-id="20e6f-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="20e6f-127">Optional attribute.</span></span> <span data-ttu-id="20e6f-128">Sterowanie dostępem środowiska uruchomieniowego do konstruktora lub metody, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="20e6f-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="20e6f-129">Ta zasada zapewnia, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="20e6f-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="20e6f-130">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="20e6f-130">Name attribute</span></span>  
  
|<span data-ttu-id="20e6f-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="20e6f-131">Value</span></span>|<span data-ttu-id="20e6f-132">Opis</span><span class="sxs-lookup"><span data-stu-id="20e6f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20e6f-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="20e6f-133">*method_name*</span></span>|<span data-ttu-id="20e6f-134">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="20e6f-134">The method name.</span></span> <span data-ttu-id="20e6f-135">Typ metody jest określany przez element nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="20e6f-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="20e6f-136">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="20e6f-136">Signature attribute</span></span>  
  
|<span data-ttu-id="20e6f-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="20e6f-137">Value</span></span>|<span data-ttu-id="20e6f-138">Opis</span><span class="sxs-lookup"><span data-stu-id="20e6f-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20e6f-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="20e6f-139">*method_signature*</span></span>|<span data-ttu-id="20e6f-140">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="20e6f-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="20e6f-141">Jeśli podano wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="20e6f-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="20e6f-142">Argumentów atrybutu</span><span class="sxs-lookup"><span data-stu-id="20e6f-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="20e6f-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="20e6f-143">Value</span></span>|<span data-ttu-id="20e6f-144">Opis</span><span class="sxs-lookup"><span data-stu-id="20e6f-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20e6f-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="20e6f-145">*method_arguments*</span></span>|<span data-ttu-id="20e6f-146">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="20e6f-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="20e6f-147">Jeśli podano wiele argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="20e6f-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="20e6f-148">Każdy argument musi zawierać nazwę FQDN typu.</span><span class="sxs-lookup"><span data-stu-id="20e6f-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="20e6f-149">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="20e6f-149">All other attributes</span></span>  
  
|<span data-ttu-id="20e6f-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="20e6f-150">Value</span></span>|<span data-ttu-id="20e6f-151">Opis</span><span class="sxs-lookup"><span data-stu-id="20e6f-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20e6f-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="20e6f-152">*policy_setting*</span></span>|<span data-ttu-id="20e6f-153">To ustawienie, aby zastosować do tego typu w metodzie.</span><span class="sxs-lookup"><span data-stu-id="20e6f-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="20e6f-154">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="20e6f-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="20e6f-155">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="20e6f-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20e6f-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="20e6f-156">Child Elements</span></span>  
 <span data-ttu-id="20e6f-157">Brak.</span><span class="sxs-lookup"><span data-stu-id="20e6f-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20e6f-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="20e6f-158">Parent Elements</span></span>  
  
|<span data-ttu-id="20e6f-159">Element</span><span class="sxs-lookup"><span data-stu-id="20e6f-159">Element</span></span>|<span data-ttu-id="20e6f-160">Opis</span><span class="sxs-lookup"><span data-stu-id="20e6f-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20e6f-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="20e6f-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="20e6f-162">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="20e6f-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="20e6f-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="20e6f-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="20e6f-164">Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="20e6f-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20e6f-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20e6f-165">Remarks</span></span>  
 <span data-ttu-id="20e6f-166">`<MethodInstantiation>` Element zastępuje zasad odbicia wykonywania odpowiednich Otwórz metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="20e6f-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e6f-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20e6f-167">See Also</span></span>  
 [<span data-ttu-id="20e6f-168">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="20e6f-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="20e6f-169">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="20e6f-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="20e6f-170">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="20e6f-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="20e6f-171">\<Metoda > — Element</span><span class="sxs-lookup"><span data-stu-id="20e6f-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
