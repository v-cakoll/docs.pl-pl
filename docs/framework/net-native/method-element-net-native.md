---
title: <Method>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180988"
---
# <a name="method-element-net-native"></a><span data-ttu-id="5b3dc-102">\<Metoda> element (.NET native)</span><span class="sxs-lookup"><span data-stu-id="5b3dc-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="5b3dc-103">Stosuje zasady odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b3dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b3dc-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b3dc-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5b3dc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5b3dc-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b3dc-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5b3dc-107">Attributes</span></span>  
  
|<span data-ttu-id="5b3dc-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5b3dc-108">Attribute</span></span>|<span data-ttu-id="5b3dc-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="5b3dc-109">Attribute type</span></span>|<span data-ttu-id="5b3dc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5b3dc-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="5b3dc-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="5b3dc-111">General</span></span>|<span data-ttu-id="5b3dc-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-112">Required attribute.</span></span> <span data-ttu-id="5b3dc-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="5b3dc-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="5b3dc-114">General</span></span>|<span data-ttu-id="5b3dc-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-115">Optional attribute.</span></span> <span data-ttu-id="5b3dc-116">Określa podpis metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-116">Specifies the method signature.</span></span> <span data-ttu-id="5b3dc-117">Jeśli istnieje wiele parametrów, są one oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="5b3dc-118">Na przykład następujący `<Method>` element definiuje zasady <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> dla metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="5b3dc-119">Jeśli atrybut jest nieobecny, dyrektywy środowiska uruchomieniowego stosuje się do wszystkich przeciążeń metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="5b3dc-120">Odbicie</span><span class="sxs-lookup"><span data-stu-id="5b3dc-120">Reflection</span></span>|<span data-ttu-id="5b3dc-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-121">Optional attribute.</span></span> <span data-ttu-id="5b3dc-122">Steruje wykonywaniem zapytań o informacje o metodzie lub wyliczanie, ale nie włącza żadnych wywołań dynamicznych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="5b3dc-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="5b3dc-123">Reflection</span></span>|<span data-ttu-id="5b3dc-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-124">Optional attribute.</span></span> <span data-ttu-id="5b3dc-125">Steruje dostępem środowiska wykonawczego do konstruktora lub metody, aby włączyć programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="5b3dc-126">Ta zasada gwarantuje, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="5b3dc-127">Atrybut Nazwa</span><span class="sxs-lookup"><span data-stu-id="5b3dc-127">Name attribute</span></span>  
  
|<span data-ttu-id="5b3dc-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="5b3dc-128">Value</span></span>|<span data-ttu-id="5b3dc-129">Opis</span><span class="sxs-lookup"><span data-stu-id="5b3dc-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5b3dc-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="5b3dc-130">*method_name*</span></span>|<span data-ttu-id="5b3dc-131">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-131">The method name.</span></span> <span data-ttu-id="5b3dc-132">Typ metody jest zdefiniowany przez [ \<](type-element-net-native.md) element nadrzędny Typ>lub [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="5b3dc-133">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="5b3dc-133">Signature attribute</span></span>  
  
|<span data-ttu-id="5b3dc-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="5b3dc-134">Value</span></span>|<span data-ttu-id="5b3dc-135">Opis</span><span class="sxs-lookup"><span data-stu-id="5b3dc-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5b3dc-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="5b3dc-136">*method_signature*</span></span>|<span data-ttu-id="5b3dc-137">Typy parametrów, które tworzą podpis metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="5b3dc-138">Wiele parametrów jest oddzielonych przecinkami, `"System.String,System.Int32,System.Int32)"`na przykład .</span><span class="sxs-lookup"><span data-stu-id="5b3dc-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="5b3dc-139">Nazwy typów parametrów powinny być w pełni kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="5b3dc-140">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="5b3dc-140">All other attributes</span></span>  
  
|<span data-ttu-id="5b3dc-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="5b3dc-141">Value</span></span>|<span data-ttu-id="5b3dc-142">Opis</span><span class="sxs-lookup"><span data-stu-id="5b3dc-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5b3dc-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="5b3dc-143">*policy_setting*</span></span>|<span data-ttu-id="5b3dc-144">Ustawienie, które ma zastosowanie do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="5b3dc-145">Możliwe wartości `Auto` `Excluded`to `Included`, `Required`, i .</span><span class="sxs-lookup"><span data-stu-id="5b3dc-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="5b3dc-146">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5b3dc-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b3dc-147">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5b3dc-147">Child Elements</span></span>  
  
|<span data-ttu-id="5b3dc-148">Element</span><span class="sxs-lookup"><span data-stu-id="5b3dc-148">Element</span></span>|<span data-ttu-id="5b3dc-149">Opis</span><span class="sxs-lookup"><span data-stu-id="5b3dc-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b3dc-150">\<>parametrów</span><span class="sxs-lookup"><span data-stu-id="5b3dc-150">\<Parameter></span></span>](parameter-element-net-native.md)|<span data-ttu-id="5b3dc-151">Stosuje zasady do typu argumentu przekazanego do metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="5b3dc-152">\<>genericparameter</span><span class="sxs-lookup"><span data-stu-id="5b3dc-152">\<GenericParameter></span></span>](genericparameter-element-net-native.md)|<span data-ttu-id="5b3dc-153">Stosuje zasady do typu parametru typu lub metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="5b3dc-154">\<ImpType></span><span class="sxs-lookup"><span data-stu-id="5b3dc-154">\<ImpliesType></span></span>](impliestype-element-net-native.md)|<span data-ttu-id="5b3dc-155">Stosuje zasady do typu, jeśli ta zasada została zastosowana do `<Method>` metody reprezentowane przez element zawierający.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="5b3dc-156">\<>typuParameter</span><span class="sxs-lookup"><span data-stu-id="5b3dc-156">\<TypeParameter></span></span>](typeparameter-element-net-native.md)|<span data-ttu-id="5b3dc-157">Stosuje zasady do typu reprezentowanego <xref:System.Type> przez argument przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b3dc-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5b3dc-158">Parent Elements</span></span>  
  
|<span data-ttu-id="5b3dc-159">Element</span><span class="sxs-lookup"><span data-stu-id="5b3dc-159">Element</span></span>|<span data-ttu-id="5b3dc-160">Opis</span><span class="sxs-lookup"><span data-stu-id="5b3dc-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b3dc-161">\<Typ></span><span class="sxs-lookup"><span data-stu-id="5b3dc-161">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="5b3dc-162">Stosuje zasady odbicia do typu i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="5b3dc-163">\<>typu></span><span class="sxs-lookup"><span data-stu-id="5b3dc-163">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="5b3dc-164">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b3dc-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b3dc-165">Remarks</span></span>  
 <span data-ttu-id="5b3dc-166">Element `<Method>` metody rodzajowej stosuje swoje zasady do wszystkich wystąpienia, które nie mają własnych zasad.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="5b3dc-167">Za pomocą `Signature` atrybutu można określić zasady dla przeciążenia określonej metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="5b3dc-168">W przeciwnym `Signature` razie jeśli atrybut jest nieobecny, dyrektywy środowiska uruchomieniowego stosuje się do wszystkich przeciążeń metody.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="5b3dc-169">Nie można zdefiniować zasady odbicia środowiska wykonawczego `<Method>` dla konstruktora przy użyciu elementu.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="5b3dc-170">Zamiast tego należy `Activate` użyć atrybutu [ \<>zestawu ](assembly-element-net-native.md), [ \<>obszaru nazw ](namespace-element-net-native.md), [ \<Type>](type-element-net-native.md)lub [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-170">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b3dc-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b3dc-171">Example</span></span>  
 <span data-ttu-id="5b3dc-172">Metoda `Stringify` w poniższym przykładzie jest metoda formatowania ogólnego przeznaczenia, który używa odbicia do konwersji obiektu do jego reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="5b3dc-173">Oprócz wywoływania domyślnej `ToString` metody obiektu, metoda może utworzyć sformatowany ciąg `ToString` wynik, przekazując <xref:System.IFormatProvider> metodę obiektu ciąg formatu, implementacji lub obu.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="5b3dc-174">Można również wywołać <xref:System.Convert.ToString%2A?displayProperty=nameWithType> jeden z przeciążeń, który konwertuje liczbę do jego binarne, szesnastkowe lub ósemkowe reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="5b3dc-175">Metoda `Stringify` może być wywoływana przez kod, jak następujące:</span><span class="sxs-lookup"><span data-stu-id="5b3dc-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="5b3dc-176">Jednak po skompilowaniu z .NET Native, przykład może zgłosić <xref:System.NullReferenceException> szereg wyjątków w czasie wykonywania, w tym i `Stringify` [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) wyjątki, Dzieje się tak, ponieważ metoda jest przeznaczona głównie do obsługi dynamicznego formatowania typów pierwotnych w bibliotece klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="5b3dc-177">Jednak ich metadane nie są udostępniane przez domyślny plik dyrektyw.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="5b3dc-178">Nawet wtedy, gdy ich metadane są udostępniane, jednak w przykładzie zgłasza [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) wyjątki, ponieważ odpowiednie `ToString` implementacje nie zostały uwzględnione w kodzie macierzystym.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="5b3dc-179">Wyjątki te można wyeliminować za pomocą [ \<Type>](type-element-net-native.md) element do definiowania typów, których metadane muszą być obecne i dodając `<Method>` elementy, aby upewnić się, że implementacja przeciążenia metody, które mogą być wywoływane dynamicznie jest również obecny.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-179">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="5b3dc-180">Poniżej znajduje się plik default.rd.xml, który eliminuje te wyjątki i umożliwia wykonanie przykładu bez błędu.</span><span class="sxs-lookup"><span data-stu-id="5b3dc-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b3dc-181">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b3dc-181">See also</span></span>

- [<span data-ttu-id="5b3dc-182">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="5b3dc-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="5b3dc-183">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5b3dc-183">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="5b3dc-184">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5b3dc-184">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="5b3dc-185">\<Element> metody</span><span class="sxs-lookup"><span data-stu-id="5b3dc-185">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
