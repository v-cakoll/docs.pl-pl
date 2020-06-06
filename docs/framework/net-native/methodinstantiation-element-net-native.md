---
title: <MethodInstantiation>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: f19bd3c20088431bcbbafac298398b82a664bee9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128329"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="0b6d8-102">\<MethodInstantiation>— Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0b6d8-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="0b6d8-103">Stosuje zasady odbicia środowiska uruchomieniowego do skonstruowanej metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b6d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b6d8-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b6d8-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0b6d8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0b6d8-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b6d8-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0b6d8-107">Attributes</span></span>  
  
|<span data-ttu-id="0b6d8-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0b6d8-108">Attribute</span></span>|<span data-ttu-id="0b6d8-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="0b6d8-109">Attribute type</span></span>|<span data-ttu-id="0b6d8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0b6d8-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0b6d8-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="0b6d8-111">General</span></span>|<span data-ttu-id="0b6d8-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-112">Required attribute.</span></span> <span data-ttu-id="0b6d8-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="0b6d8-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="0b6d8-114">General</span></span>|<span data-ttu-id="0b6d8-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-115">Optional attribute.</span></span> <span data-ttu-id="0b6d8-116">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="0b6d8-117">Wiele parametrów nazwanych są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="0b6d8-118">Ten `Signature` atrybut jest używany do odróżniania przeciążonych metod.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="0b6d8-119">Ogólne</span><span class="sxs-lookup"><span data-stu-id="0b6d8-119">General</span></span>|<span data-ttu-id="0b6d8-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-120">Required attribute.</span></span> <span data-ttu-id="0b6d8-121">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="0b6d8-122">Jeśli istnieją wiele argumentów, są one oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="0b6d8-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="0b6d8-123">Reflection</span></span>|<span data-ttu-id="0b6d8-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-124">Optional attribute.</span></span> <span data-ttu-id="0b6d8-125">Kontroluje wykonywanie zapytań dotyczących informacji na temat lub wyliczanie metody, ale nie włącza żadnego dynamicznego wywołania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="0b6d8-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="0b6d8-126">Reflection</span></span>|<span data-ttu-id="0b6d8-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-127">Optional attribute.</span></span> <span data-ttu-id="0b6d8-128">Kontroluje dostęp środowiska uruchomieniowego do konstruktora lub metody w celu włączenia programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="0b6d8-129">Te zasady zapewniają, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0b6d8-130">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="0b6d8-130">Name attribute</span></span>  
  
|<span data-ttu-id="0b6d8-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="0b6d8-131">Value</span></span>|<span data-ttu-id="0b6d8-132">Opis</span><span class="sxs-lookup"><span data-stu-id="0b6d8-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0b6d8-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="0b6d8-133">*method_name*</span></span>|<span data-ttu-id="0b6d8-134">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-134">The method name.</span></span> <span data-ttu-id="0b6d8-135">Typ metody jest zdefiniowany przez [\<Type>](type-element-net-native.md) element nadrzędny lub [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0b6d8-135">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="0b6d8-136">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="0b6d8-136">Signature attribute</span></span>  
  
|<span data-ttu-id="0b6d8-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="0b6d8-137">Value</span></span>|<span data-ttu-id="0b6d8-138">Opis</span><span class="sxs-lookup"><span data-stu-id="0b6d8-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0b6d8-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="0b6d8-139">*method_signature*</span></span>|<span data-ttu-id="0b6d8-140">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="0b6d8-141">Jeśli istnieją wiele parametrów, są one oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="0b6d8-142">Arguments — atrybut</span><span class="sxs-lookup"><span data-stu-id="0b6d8-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="0b6d8-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="0b6d8-143">Value</span></span>|<span data-ttu-id="0b6d8-144">Opis</span><span class="sxs-lookup"><span data-stu-id="0b6d8-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0b6d8-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="0b6d8-145">*method_arguments*</span></span>|<span data-ttu-id="0b6d8-146">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="0b6d8-147">Jeśli istnieją wiele argumentów, są one oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="0b6d8-148">Każdy argument musi składać się z w pełni kwalifikowanej nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0b6d8-149">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="0b6d8-149">All other attributes</span></span>  
  
|<span data-ttu-id="0b6d8-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="0b6d8-150">Value</span></span>|<span data-ttu-id="0b6d8-151">Opis</span><span class="sxs-lookup"><span data-stu-id="0b6d8-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0b6d8-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0b6d8-152">*policy_setting*</span></span>|<span data-ttu-id="0b6d8-153">Ustawienie, które ma zostać zastosowane do tego typu zasad dla metody.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="0b6d8-154">Możliwe wartości to `Auto` , `Excluded` , `Included` , i `Required` .</span><span class="sxs-lookup"><span data-stu-id="0b6d8-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="0b6d8-155">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0b6d8-155">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b6d8-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0b6d8-156">Child Elements</span></span>  
 <span data-ttu-id="0b6d8-157">Brak.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b6d8-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0b6d8-158">Parent Elements</span></span>  
  
|<span data-ttu-id="0b6d8-159">Element</span><span class="sxs-lookup"><span data-stu-id="0b6d8-159">Element</span></span>|<span data-ttu-id="0b6d8-160">Opis</span><span class="sxs-lookup"><span data-stu-id="0b6d8-160">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="0b6d8-161">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-161">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="0b6d8-162">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-162">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b6d8-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b6d8-163">Remarks</span></span>  
 <span data-ttu-id="0b6d8-164">`<MethodInstantiation>`Element zastępuje zasady odbicia środowiska uruchomieniowego odpowiadającej jej otwartej metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="0b6d8-164">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b6d8-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b6d8-165">See also</span></span>

- [<span data-ttu-id="0b6d8-166">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0b6d8-166">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0b6d8-167">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0b6d8-167">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="0b6d8-168">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0b6d8-168">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="0b6d8-169">\<Method>Postaci</span><span class="sxs-lookup"><span data-stu-id="0b6d8-169">\<Method> Element</span></span>](method-element-net-native.md)
