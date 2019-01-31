---
title: <MethodInstantiation> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccc8cd22c3175a2b6456f71d9dc773ce85848949
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275067"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="ecb1d-102">\<MethodInstantiation > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="ecb1d-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="ecb1d-103">Ma zastosowanie zasad odbicia środowiska uruchomieniowego do skonstruowanego metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecb1d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecb1d-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecb1d-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ecb1d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ecb1d-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecb1d-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ecb1d-107">Attributes</span></span>  
  
|<span data-ttu-id="ecb1d-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ecb1d-108">Attribute</span></span>|<span data-ttu-id="ecb1d-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="ecb1d-109">Attribute type</span></span>|<span data-ttu-id="ecb1d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ecb1d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ecb1d-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="ecb1d-111">General</span></span>|<span data-ttu-id="ecb1d-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-112">Required attribute.</span></span> <span data-ttu-id="ecb1d-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="ecb1d-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="ecb1d-114">General</span></span>|<span data-ttu-id="ecb1d-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-115">Optional attribute.</span></span> <span data-ttu-id="ecb1d-116">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="ecb1d-117">Wiele parametry nazwane są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="ecb1d-118">`Signature` Atrybut jest używany do odróżnienia przeciążonych metod.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="ecb1d-119">Ogólne</span><span class="sxs-lookup"><span data-stu-id="ecb1d-119">General</span></span>|<span data-ttu-id="ecb1d-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-120">Required attribute.</span></span> <span data-ttu-id="ecb1d-121">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="ecb1d-122">Jeśli podano wiele argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="ecb1d-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="ecb1d-123">Reflection</span></span>|<span data-ttu-id="ecb1d-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-124">Optional attribute.</span></span> <span data-ttu-id="ecb1d-125">Określa wykonanie zapytania dotyczącego informacji o wyliczanie metody, ale nie uwzględnia żadnych wywołanie dynamiczne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="ecb1d-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="ecb1d-126">Reflection</span></span>|<span data-ttu-id="ecb1d-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-127">Optional attribute.</span></span> <span data-ttu-id="ecb1d-128">Dostęp do środowiska uruchomieniowego formanty do konstruktora lub metody, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="ecb1d-129">Te zasady zapewniają, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ecb1d-130">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="ecb1d-130">Name attribute</span></span>  
  
|<span data-ttu-id="ecb1d-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="ecb1d-131">Value</span></span>|<span data-ttu-id="ecb1d-132">Opis</span><span class="sxs-lookup"><span data-stu-id="ecb1d-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecb1d-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="ecb1d-133">*method_name*</span></span>|<span data-ttu-id="ecb1d-134">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-134">The method name.</span></span> <span data-ttu-id="ecb1d-135">Typ metody jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="ecb1d-136">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="ecb1d-136">Signature attribute</span></span>  
  
|<span data-ttu-id="ecb1d-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="ecb1d-137">Value</span></span>|<span data-ttu-id="ecb1d-138">Opis</span><span class="sxs-lookup"><span data-stu-id="ecb1d-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecb1d-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="ecb1d-139">*method_signature*</span></span>|<span data-ttu-id="ecb1d-140">Określa nazwane parametry metody.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="ecb1d-141">Jeśli podano wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="ecb1d-142">Argumenty atrybutu</span><span class="sxs-lookup"><span data-stu-id="ecb1d-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="ecb1d-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="ecb1d-143">Value</span></span>|<span data-ttu-id="ecb1d-144">Opis</span><span class="sxs-lookup"><span data-stu-id="ecb1d-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecb1d-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="ecb1d-145">*method_arguments*</span></span>|<span data-ttu-id="ecb1d-146">Określa argumenty typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="ecb1d-147">Jeśli podano wiele argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="ecb1d-148">Każdy argument musi zawierać w pełni kwalifikowana nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ecb1d-149">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="ecb1d-149">All other attributes</span></span>  
  
|<span data-ttu-id="ecb1d-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="ecb1d-150">Value</span></span>|<span data-ttu-id="ecb1d-151">Opis</span><span class="sxs-lookup"><span data-stu-id="ecb1d-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecb1d-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ecb1d-152">*policy_setting*</span></span>|<span data-ttu-id="ecb1d-153">Ustawienia do zastosowania do tego typu zasad dla metody.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="ecb1d-154">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="ecb1d-155">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ecb1d-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecb1d-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ecb1d-156">Child Elements</span></span>  
 <span data-ttu-id="ecb1d-157">Brak.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecb1d-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ecb1d-158">Parent Elements</span></span>  
  
|<span data-ttu-id="ecb1d-159">Element</span><span class="sxs-lookup"><span data-stu-id="ecb1d-159">Element</span></span>|<span data-ttu-id="ecb1d-160">Opis</span><span class="sxs-lookup"><span data-stu-id="ecb1d-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecb1d-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="ecb1d-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="ecb1d-162">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="ecb1d-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="ecb1d-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="ecb1d-164">Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecb1d-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecb1d-165">Remarks</span></span>  
 <span data-ttu-id="ecb1d-166">`<MethodInstantiation>` Element zastąpienia zasad odbicia środowiska uruchomieniowego odpowiedniego Otwórz metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="ecb1d-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb1d-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecb1d-167">See also</span></span>
- [<span data-ttu-id="ecb1d-168">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="ecb1d-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ecb1d-169">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ecb1d-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="ecb1d-170">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ecb1d-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="ecb1d-171">\<Metoda > Element</span><span class="sxs-lookup"><span data-stu-id="ecb1d-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
