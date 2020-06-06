---
title: <Method>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180988"
---
# <a name="method-element-net-native"></a><span data-ttu-id="9f136-102">\<Method>— Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="9f136-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="9f136-103">Stosuje zasady odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f136-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f136-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f136-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9f136-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9f136-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9f136-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f136-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9f136-107">Attributes</span></span>  
  
|<span data-ttu-id="9f136-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9f136-108">Attribute</span></span>|<span data-ttu-id="9f136-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="9f136-109">Attribute type</span></span>|<span data-ttu-id="9f136-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9f136-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="9f136-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="9f136-111">General</span></span>|<span data-ttu-id="9f136-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9f136-112">Required attribute.</span></span> <span data-ttu-id="9f136-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="9f136-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="9f136-114">General</span></span>|<span data-ttu-id="9f136-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9f136-115">Optional attribute.</span></span> <span data-ttu-id="9f136-116">Określa sygnaturę metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-116">Specifies the method signature.</span></span> <span data-ttu-id="9f136-117">Jeśli istnieją wiele parametrów, są one oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9f136-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="9f136-118">Na przykład poniższy `<Method>` element definiuje zasady dla <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="9f136-119">Jeśli atrybut jest nieobecny, dyrektywa Runtime stosuje się do wszystkich przeciążeń metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="9f136-120">Odbicie</span><span class="sxs-lookup"><span data-stu-id="9f136-120">Reflection</span></span>|<span data-ttu-id="9f136-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9f136-121">Optional attribute.</span></span> <span data-ttu-id="9f136-122">Kontroluje wykonywanie zapytań dotyczących informacji na temat lub wyliczanie metody, ale nie włącza żadnego dynamicznego wywołania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9f136-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="9f136-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="9f136-123">Reflection</span></span>|<span data-ttu-id="9f136-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9f136-124">Optional attribute.</span></span> <span data-ttu-id="9f136-125">Kontroluje dostęp środowiska uruchomieniowego do konstruktora lub metody w celu włączenia programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="9f136-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="9f136-126">Te zasady zapewniają, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9f136-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="9f136-127">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="9f136-127">Name attribute</span></span>  
  
|<span data-ttu-id="9f136-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="9f136-128">Value</span></span>|<span data-ttu-id="9f136-129">Opis</span><span class="sxs-lookup"><span data-stu-id="9f136-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f136-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="9f136-130">*method_name*</span></span>|<span data-ttu-id="9f136-131">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-131">The method name.</span></span> <span data-ttu-id="9f136-132">Typ metody jest zdefiniowany przez [\<Type>](type-element-net-native.md) element nadrzędny lub [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="9f136-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="9f136-133">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="9f136-133">Signature attribute</span></span>  
  
|<span data-ttu-id="9f136-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="9f136-134">Value</span></span>|<span data-ttu-id="9f136-135">Opis</span><span class="sxs-lookup"><span data-stu-id="9f136-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f136-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="9f136-136">*method_signature*</span></span>|<span data-ttu-id="9f136-137">Typy parametrów, które tworzą sygnaturę metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="9f136-138">Wiele parametrów jest oddzielonych przecinkami, na przykład `"System.String,System.Int32,System.Int32)"` .</span><span class="sxs-lookup"><span data-stu-id="9f136-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="9f136-139">Nazwy typów parametrów powinny być w pełni kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="9f136-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="9f136-140">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="9f136-140">All other attributes</span></span>  
  
|<span data-ttu-id="9f136-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="9f136-141">Value</span></span>|<span data-ttu-id="9f136-142">Opis</span><span class="sxs-lookup"><span data-stu-id="9f136-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f136-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="9f136-143">*policy_setting*</span></span>|<span data-ttu-id="9f136-144">Ustawienie, które ma zostać zastosowane do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="9f136-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="9f136-145">Możliwe wartości to `Auto` , `Excluded` , `Included` , i `Required` .</span><span class="sxs-lookup"><span data-stu-id="9f136-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="9f136-146">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9f136-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f136-147">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9f136-147">Child Elements</span></span>  
  
|<span data-ttu-id="9f136-148">Element</span><span class="sxs-lookup"><span data-stu-id="9f136-148">Element</span></span>|<span data-ttu-id="9f136-149">Opis</span><span class="sxs-lookup"><span data-stu-id="9f136-149">Description</span></span>|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|<span data-ttu-id="9f136-150">Stosuje zasady do typu argumentu przesłanego do metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-150">Applies policy to the type of the argument passed to a method.</span></span>|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="9f136-151">Stosuje zasady do typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-151">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="9f136-152">Stosuje zasady do typu, jeśli te zasady zostały zastosowane do metody reprezentowanej przez `<Method>` element zawierający.</span><span class="sxs-lookup"><span data-stu-id="9f136-152">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|<span data-ttu-id="9f136-153">Stosuje zasady do typu reprezentowanego przez <xref:System.Type> argument przesłany do metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-153">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f136-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9f136-154">Parent Elements</span></span>  
  
|<span data-ttu-id="9f136-155">Element</span><span class="sxs-lookup"><span data-stu-id="9f136-155">Element</span></span>|<span data-ttu-id="9f136-156">Opis</span><span class="sxs-lookup"><span data-stu-id="9f136-156">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="9f136-157">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="9f136-157">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="9f136-158">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="9f136-158">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f136-159">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f136-159">Remarks</span></span>  
 <span data-ttu-id="9f136-160">`<Method>`Element metody ogólnej stosuje swoje zasady do wszystkich wystąpień, które nie mają własnych zasad.</span><span class="sxs-lookup"><span data-stu-id="9f136-160">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="9f136-161">Możesz użyć atrybutu, `Signature` Aby określić zasady dla konkretnego przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-161">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="9f136-162">W przeciwnym razie, jeśli `Signature` atrybut jest nieobecny, dyrektywa Runtime stosuje się do wszystkich przeciążeń metody.</span><span class="sxs-lookup"><span data-stu-id="9f136-162">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="9f136-163">Nie można zdefiniować zasad odbicia środowiska uruchomieniowego dla konstruktora przy użyciu `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9f136-163">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="9f136-164">Zamiast tego należy użyć `Activate` atrybutu [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) elementu,, [\<Type>](type-element-net-native.md) , lub [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="9f136-164">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f136-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f136-165">Example</span></span>  
 <span data-ttu-id="9f136-166">`Stringify`Metoda w poniższym przykładzie jest metodą formatowania ogólnego zastosowania, która używa odbicia do przekonwertowania obiektu na jego reprezentację w postaci ciągu.</span><span class="sxs-lookup"><span data-stu-id="9f136-166">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="9f136-167">Oprócz wywoływania domyślnej `ToString` metody obiektu Metoda może utworzyć sformatowany ciąg wynikowy przez przekazanie `ToString` metody obiektu ciągu formatu, <xref:System.IFormatProvider> implementacji lub obu.</span><span class="sxs-lookup"><span data-stu-id="9f136-167">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="9f136-168">Może również wywołać jedno z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> przeciążeń, które konwertuje liczbę na jej reprezentację binarną, szesnastkową lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="9f136-168">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="9f136-169">`Stringify`Metoda może być wywoływana przez kod podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="9f136-169">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="9f136-170">Jednak podczas kompilowania z .NET Native przykład może zgłosić liczbę wyjątków w czasie wykonywania, w tym <xref:System.NullReferenceException> wyjątki i [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , dzieje się tak, ponieważ `Stringify` Metoda jest zaprojektowana głównie do obsługi dynamicznego formatowania typów pierwotnych w bibliotece klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f136-170">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="9f136-171">Jednak ich metadane nie są udostępniane przez domyślny plik dyrektyw.</span><span class="sxs-lookup"><span data-stu-id="9f136-171">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="9f136-172">Jednak w przypadku udostępnienia ich metadanych przykład zgłasza wyjątki [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , ponieważ odpowiednie `ToString` implementacje nie zostały uwzględnione w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="9f136-172">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="9f136-173">Te wyjątki można usunąć za pomocą [\<Type>](type-element-net-native.md) elementu, aby zdefiniować typy, których metadane muszą być obecne, i przez dodanie elementów, `<Method>` Aby upewnić się, że implementacja przeciążeń metody, które mogą być wywołane dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="9f136-173">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="9f136-174">Poniżej znajduje się domyślny plik. Rd. XML, który eliminuje te wyjątki i pozwala na wykonywanie przykładu bez błędu.</span><span class="sxs-lookup"><span data-stu-id="9f136-174">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f136-175">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f136-175">See also</span></span>

- [<span data-ttu-id="9f136-176">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9f136-176">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9f136-177">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9f136-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="9f136-178">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9f136-178">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="9f136-179">\<MethodInstantiation>Postaci</span><span class="sxs-lookup"><span data-stu-id="9f136-179">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
