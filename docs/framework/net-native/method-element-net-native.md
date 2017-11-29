---
title: Element &lt;Method&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6d70fd560cb7b164460eb3882cac88ed733d788
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmethodgt-element-net-native"></a><span data-ttu-id="358bf-102">Element &lt;Method&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="358bf-102">&lt;Method&gt; Element (.NET Native)</span></span>
<span data-ttu-id="358bf-103">Zastosowanie zasad wykonywania odbicia do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="358bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="358bf-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="358bf-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="358bf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="358bf-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="358bf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="358bf-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="358bf-107">Attributes</span></span>  
  
|<span data-ttu-id="358bf-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="358bf-108">Attribute</span></span>|<span data-ttu-id="358bf-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="358bf-109">Attribute type</span></span>|<span data-ttu-id="358bf-110">Opis</span><span class="sxs-lookup"><span data-stu-id="358bf-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="358bf-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="358bf-111">General</span></span>|<span data-ttu-id="358bf-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="358bf-112">Required attribute.</span></span> <span data-ttu-id="358bf-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="358bf-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="358bf-114">General</span></span>|<span data-ttu-id="358bf-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="358bf-115">Optional attribute.</span></span> <span data-ttu-id="358bf-116">Określa podpis metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-116">Specifies the method signature.</span></span> <span data-ttu-id="358bf-117">Jeśli podano wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="358bf-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="358bf-118">Na przykład następująca `<Method>` element definiuje zasady dla <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="358bf-119">Jeśli ten atrybut jest nieobecne, dyrektyw środowiska uruchomieniowego ma zastosowanie do wszystkich przeciążeń metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="358bf-120">Odbicie</span><span class="sxs-lookup"><span data-stu-id="358bf-120">Reflection</span></span>|<span data-ttu-id="358bf-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="358bf-121">Optional attribute.</span></span> <span data-ttu-id="358bf-122">Określa, czy podczas badania informacji dotyczących metody wyliczania, jednak nie wszystkie wywołania dynamicznej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="358bf-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="358bf-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="358bf-123">Reflection</span></span>|<span data-ttu-id="358bf-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="358bf-124">Optional attribute.</span></span> <span data-ttu-id="358bf-125">Sterowanie dostępem środowiska uruchomieniowego do konstruktora lub metody, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="358bf-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="358bf-126">Ta zasada zapewnia, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="358bf-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="358bf-127">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="358bf-127">Name attribute</span></span>  
  
|<span data-ttu-id="358bf-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="358bf-128">Value</span></span>|<span data-ttu-id="358bf-129">Opis</span><span class="sxs-lookup"><span data-stu-id="358bf-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="358bf-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="358bf-130">*method_name*</span></span>|<span data-ttu-id="358bf-131">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-131">The method name.</span></span> <span data-ttu-id="358bf-132">Typ metody jest określany przez element nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="358bf-132">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="358bf-133">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="358bf-133">Signature attribute</span></span>  
  
|<span data-ttu-id="358bf-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="358bf-134">Value</span></span>|<span data-ttu-id="358bf-135">Opis</span><span class="sxs-lookup"><span data-stu-id="358bf-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="358bf-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="358bf-136">*method_signature*</span></span>|<span data-ttu-id="358bf-137">Typy parametrów, które tworzą podpis metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="358bf-138">Wiele parametrów są oddzielone przecinkami, na przykład `"System.String,System.Int32,System.Int32)"`.</span><span class="sxs-lookup"><span data-stu-id="358bf-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="358bf-139">Nazwy parametrów typu powinny być w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="358bf-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="358bf-140">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="358bf-140">All other attributes</span></span>  
  
|<span data-ttu-id="358bf-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="358bf-141">Value</span></span>|<span data-ttu-id="358bf-142">Opis</span><span class="sxs-lookup"><span data-stu-id="358bf-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="358bf-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="358bf-143">*policy_setting*</span></span>|<span data-ttu-id="358bf-144">Ustawienia do zastosowania dla tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="358bf-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="358bf-145">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="358bf-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="358bf-146">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="358bf-146">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="358bf-147">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="358bf-147">Child Elements</span></span>  
  
|<span data-ttu-id="358bf-148">Element</span><span class="sxs-lookup"><span data-stu-id="358bf-148">Element</span></span>|<span data-ttu-id="358bf-149">Opis</span><span class="sxs-lookup"><span data-stu-id="358bf-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="358bf-150">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="358bf-150">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)|<span data-ttu-id="358bf-151">Stosuje zasady do typu argumentu przekazanego do metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="358bf-152">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="358bf-152">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|<span data-ttu-id="358bf-153">Stosuje zasady do typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="358bf-154">\<ImpliesType ></span><span class="sxs-lookup"><span data-stu-id="358bf-154">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)|<span data-ttu-id="358bf-155">Stosuje zasady do typu, o ile tej zasady zostały zastosowane do metody reprezentowany przez zawierający `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="358bf-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="358bf-156">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="358bf-156">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|<span data-ttu-id="358bf-157">Stosuje zasady do typu reprezentowanego przez <xref:System.Type> argument przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="358bf-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="358bf-158">Parent Elements</span></span>  
  
|<span data-ttu-id="358bf-159">Element</span><span class="sxs-lookup"><span data-stu-id="358bf-159">Element</span></span>|<span data-ttu-id="358bf-160">Opis</span><span class="sxs-lookup"><span data-stu-id="358bf-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="358bf-161">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="358bf-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="358bf-162">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="358bf-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="358bf-163">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="358bf-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="358bf-164">Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="358bf-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="358bf-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="358bf-165">Remarks</span></span>  
 <span data-ttu-id="358bf-166">A `<Method>` element metody rodzajowej dotyczy wszystkich wystąpień, które nie mają własnych zasad polityki.</span><span class="sxs-lookup"><span data-stu-id="358bf-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="358bf-167">Można użyć `Signature` atrybutu, aby określić zasady przeciążenia konkretnej metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="358bf-168">W przeciwnym razie, jeśli `Signature` nie jest obecny atrybut, dyrektyw środowiska uruchomieniowego mają zastosowanie do wszystkich przeciążeń metody.</span><span class="sxs-lookup"><span data-stu-id="358bf-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="358bf-169">Nie można zdefiniować zasady odbicia środowiska uruchomieniowego dla konstruktora przy użyciu `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="358bf-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="358bf-170">Zamiast tego należy użyć `Activate` atrybutu [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md), lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="358bf-170">Instead, use the `Activate` attribute of the  [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), [\<Type>](../../../docs/framework/net-native/type-element-net-native.md), or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="358bf-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="358bf-171">Example</span></span>  
 <span data-ttu-id="358bf-172">`Stringify` Metoda w poniższym przykładzie jest metodę formatowania ogólnego przeznaczenia, która używa odbicia do konwersji obiektu do reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="358bf-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="358bf-173">Oprócz wywoływania domyślnego obiektu `ToString` metody, metody powodują ciąg sformatowany wynik przez przekazanie obiektu `ToString` metody ciąg formatu <xref:System.IFormatProvider> implementacji lub oba.</span><span class="sxs-lookup"><span data-stu-id="358bf-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="358bf-174">Można również wywoływanie jednego z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> przeciążeń, które konwertuje liczbę na jej reprezentację binarnego, szesnastkową lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="358bf-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="358bf-175">`Stringify` Metoda może być wywoływany przez kod podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="358bf-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="358bf-176">Jednak gdy skompilowano z platformą .NET Native, przykładzie może zgłosić liczba wyjątków w czasie wykonywania, w tym <xref:System.NullReferenceException> i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, dzieje się tak dlatego `Stringify` jest — metoda przeznaczony głównie do obsługi dynamicznie pierwotne typy formatowania w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="358bf-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="358bf-177">Jednak ich metadanych nie zostanie udostępniony przez domyślny plik dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="358bf-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="358bf-178">Nawet wtedy, gdy metadane są udostępniane, jednak przykładzie zgłasza [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki ponieważ odpowiednie `ToString` ma zostały zawiera implementacji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="358bf-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="358bf-179">Wyjątki te wszystkie można wyeliminować za pomocą [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) elementu, aby zdefiniować typy, których metadane muszą być obecne, a przez dodanie `<Method>` elementy, aby zapewnić, że implementacja przeciążenia metody można dynamicznie wywołać który również jest obecny.</span><span class="sxs-lookup"><span data-stu-id="358bf-179">These exceptions can all be eliminated by using the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="358bf-180">Poniżej znajduje się plik default.rd.xml eliminuje tych wyjątków i zezwala na przykład aby zostanie wykonane bez błędów.</span><span class="sxs-lookup"><span data-stu-id="358bf-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="358bf-181">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="358bf-181">See Also</span></span>  
 [<span data-ttu-id="358bf-182">Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="358bf-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="358bf-183">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="358bf-183">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="358bf-184">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="358bf-184">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="358bf-185">\<MethodInstantiation > — Element</span><span class="sxs-lookup"><span data-stu-id="358bf-185">\<MethodInstantiation> Element</span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)
