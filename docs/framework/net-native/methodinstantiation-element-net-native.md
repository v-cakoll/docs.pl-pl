---
title: <MethodInstantiation>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2c0354853e4725ba3e673fb9142c4a7a85d2121
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049617"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="3071f-102">\<MethodInstantiation, element > (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="3071f-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="3071f-103">Stosuje zasady odbicia środowiska uruchomieniowego do skonstruowanej metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="3071f-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3071f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3071f-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3071f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3071f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3071f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3071f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3071f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3071f-107">Attributes</span></span>  
  
|<span data-ttu-id="3071f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3071f-108">Attribute</span></span>|<span data-ttu-id="3071f-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="3071f-109">Attribute type</span></span>|<span data-ttu-id="3071f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3071f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="3071f-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="3071f-111">General</span></span>|<span data-ttu-id="3071f-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3071f-112">Required attribute.</span></span> <span data-ttu-id="3071f-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="3071f-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="3071f-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="3071f-114">General</span></span>|<span data-ttu-id="3071f-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3071f-115">Optional attribute.</span></span> <span data-ttu-id="3071f-116">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="3071f-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="3071f-117">Wiele parametrów nazwanych są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="3071f-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="3071f-118">Ten `Signature` atrybut jest używany do odróżniania przeciążonych metod.</span><span class="sxs-lookup"><span data-stu-id="3071f-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="3071f-119">Ogólne</span><span class="sxs-lookup"><span data-stu-id="3071f-119">General</span></span>|<span data-ttu-id="3071f-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3071f-120">Required attribute.</span></span> <span data-ttu-id="3071f-121">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3071f-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="3071f-122">Jeśli istnieją wiele argumentów, są one oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="3071f-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="3071f-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="3071f-123">Reflection</span></span>|<span data-ttu-id="3071f-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3071f-124">Optional attribute.</span></span> <span data-ttu-id="3071f-125">Kontroluje wykonywanie zapytań dotyczących informacji na temat lub wyliczanie metody, ale nie włącza żadnego dynamicznego wywołania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3071f-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="3071f-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="3071f-126">Reflection</span></span>|<span data-ttu-id="3071f-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3071f-127">Optional attribute.</span></span> <span data-ttu-id="3071f-128">Kontroluje dostęp środowiska uruchomieniowego do konstruktora lub metody w celu włączenia programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="3071f-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="3071f-129">Te zasady zapewniają, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3071f-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="3071f-130">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="3071f-130">Name attribute</span></span>  
  
|<span data-ttu-id="3071f-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="3071f-131">Value</span></span>|<span data-ttu-id="3071f-132">Opis</span><span class="sxs-lookup"><span data-stu-id="3071f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3071f-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="3071f-133">*method_name*</span></span>|<span data-ttu-id="3071f-134">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="3071f-134">The method name.</span></span> <span data-ttu-id="3071f-135">Typ metody jest definiowany przez [ \<typ nadrzędny >](type-element-net-native.md) lub [ \<element > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3071f-135">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="3071f-136">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="3071f-136">Signature attribute</span></span>  
  
|<span data-ttu-id="3071f-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="3071f-137">Value</span></span>|<span data-ttu-id="3071f-138">Opis</span><span class="sxs-lookup"><span data-stu-id="3071f-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3071f-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="3071f-139">*method_signature*</span></span>|<span data-ttu-id="3071f-140">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="3071f-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="3071f-141">Jeśli istnieją wiele parametrów, są one oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="3071f-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="3071f-142">Arguments — atrybut</span><span class="sxs-lookup"><span data-stu-id="3071f-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="3071f-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="3071f-143">Value</span></span>|<span data-ttu-id="3071f-144">Opis</span><span class="sxs-lookup"><span data-stu-id="3071f-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3071f-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="3071f-145">*method_arguments*</span></span>|<span data-ttu-id="3071f-146">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3071f-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="3071f-147">Jeśli istnieją wiele argumentów, są one oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="3071f-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="3071f-148">Każdy argument musi składać się z w pełni kwalifikowanej nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="3071f-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="3071f-149">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="3071f-149">All other attributes</span></span>  
  
|<span data-ttu-id="3071f-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="3071f-150">Value</span></span>|<span data-ttu-id="3071f-151">Opis</span><span class="sxs-lookup"><span data-stu-id="3071f-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3071f-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="3071f-152">*policy_setting*</span></span>|<span data-ttu-id="3071f-153">Ustawienie, które ma zostać zastosowane do tego typu zasad dla metody.</span><span class="sxs-lookup"><span data-stu-id="3071f-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="3071f-154">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="3071f-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="3071f-155">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3071f-155">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3071f-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3071f-156">Child Elements</span></span>  
 <span data-ttu-id="3071f-157">Brak.</span><span class="sxs-lookup"><span data-stu-id="3071f-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3071f-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3071f-158">Parent Elements</span></span>  
  
|<span data-ttu-id="3071f-159">Element</span><span class="sxs-lookup"><span data-stu-id="3071f-159">Element</span></span>|<span data-ttu-id="3071f-160">Opis</span><span class="sxs-lookup"><span data-stu-id="3071f-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3071f-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="3071f-161">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="3071f-162">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="3071f-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="3071f-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="3071f-163">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="3071f-164">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="3071f-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3071f-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3071f-165">Remarks</span></span>  
 <span data-ttu-id="3071f-166">`<MethodInstantiation>` Element zastępuje zasady odbicia środowiska uruchomieniowego odpowiadającej jej otwartej metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="3071f-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3071f-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3071f-167">See also</span></span>

- [<span data-ttu-id="3071f-168">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3071f-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3071f-169">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3071f-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="3071f-170">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3071f-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="3071f-171">\<Element > metody</span><span class="sxs-lookup"><span data-stu-id="3071f-171">\<Method> Element</span></span>](method-element-net-native.md)
