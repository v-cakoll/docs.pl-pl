---
title: <Method> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 008a61a75aa96faad801e6da8bb0f8a86f65829c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288083"
---
# <a name="method-element-net-native"></a><span data-ttu-id="7fb4a-102">\<Metoda > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="7fb4a-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="7fb4a-103">Ma zastosowanie zasad odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fb4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fb4a-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fb4a-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7fb4a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7fb4a-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fb4a-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7fb4a-107">Attributes</span></span>  
  
|<span data-ttu-id="7fb4a-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7fb4a-108">Attribute</span></span>|<span data-ttu-id="7fb4a-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="7fb4a-109">Attribute type</span></span>|<span data-ttu-id="7fb4a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="7fb4a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="7fb4a-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="7fb4a-111">General</span></span>|<span data-ttu-id="7fb4a-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-112">Required attribute.</span></span> <span data-ttu-id="7fb4a-113">Określa nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="7fb4a-114">Ogólne</span><span class="sxs-lookup"><span data-stu-id="7fb4a-114">General</span></span>|<span data-ttu-id="7fb4a-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-115">Optional attribute.</span></span> <span data-ttu-id="7fb4a-116">Określa podpis metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-116">Specifies the method signature.</span></span> <span data-ttu-id="7fb4a-117">Jeśli podano wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="7fb4a-118">Na przykład następująca `<Method>` element definiuje zasady dla <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="7fb4a-119">Jeśli ten atrybut jest nieobecne, dyrektyw środowiska uruchomieniowego ma zastosowanie do wszystkich przeciążeń metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="7fb4a-120">Odbicie</span><span class="sxs-lookup"><span data-stu-id="7fb4a-120">Reflection</span></span>|<span data-ttu-id="7fb4a-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-121">Optional attribute.</span></span> <span data-ttu-id="7fb4a-122">Określa wykonanie zapytania dotyczącego informacji o wyliczanie metody, ale nie uwzględnia żadnych wywołanie dynamiczne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="7fb4a-123">Odbicie</span><span class="sxs-lookup"><span data-stu-id="7fb4a-123">Reflection</span></span>|<span data-ttu-id="7fb4a-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-124">Optional attribute.</span></span> <span data-ttu-id="7fb4a-125">Dostęp do środowiska uruchomieniowego formanty do konstruktora lub metody, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="7fb4a-126">Te zasady zapewniają, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="7fb4a-127">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="7fb4a-127">Name attribute</span></span>  
  
|<span data-ttu-id="7fb4a-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="7fb4a-128">Value</span></span>|<span data-ttu-id="7fb4a-129">Opis</span><span class="sxs-lookup"><span data-stu-id="7fb4a-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7fb4a-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="7fb4a-130">*method_name*</span></span>|<span data-ttu-id="7fb4a-131">Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-131">The method name.</span></span> <span data-ttu-id="7fb4a-132">Typ metody jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-132">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="7fb4a-133">Atrybut podpisu</span><span class="sxs-lookup"><span data-stu-id="7fb4a-133">Signature attribute</span></span>  
  
|<span data-ttu-id="7fb4a-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="7fb4a-134">Value</span></span>|<span data-ttu-id="7fb4a-135">Opis</span><span class="sxs-lookup"><span data-stu-id="7fb4a-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7fb4a-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="7fb4a-136">*method_signature*</span></span>|<span data-ttu-id="7fb4a-137">Typy parametrów, które tworzą podpis metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="7fb4a-138">Wiele parametrów są oddzielone przecinkami, na przykład `"System.String,System.Int32,System.Int32)"`.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="7fb4a-139">Nazwami typu parametru powinna być w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="7fb4a-140">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="7fb4a-140">All other attributes</span></span>  
  
|<span data-ttu-id="7fb4a-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="7fb4a-141">Value</span></span>|<span data-ttu-id="7fb4a-142">Opis</span><span class="sxs-lookup"><span data-stu-id="7fb4a-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7fb4a-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7fb4a-143">*policy_setting*</span></span>|<span data-ttu-id="7fb4a-144">Ustawienia do zastosowania do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="7fb4a-145">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="7fb4a-146">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7fb4a-146">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fb4a-147">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7fb4a-147">Child Elements</span></span>  
  
|<span data-ttu-id="7fb4a-148">Element</span><span class="sxs-lookup"><span data-stu-id="7fb4a-148">Element</span></span>|<span data-ttu-id="7fb4a-149">Opis</span><span class="sxs-lookup"><span data-stu-id="7fb4a-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fb4a-150">\<Parameter></span><span class="sxs-lookup"><span data-stu-id="7fb4a-150">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)|<span data-ttu-id="7fb4a-151">Stosuje zasady do typu argumentu przekazanego do metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="7fb4a-152">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="7fb4a-152">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|<span data-ttu-id="7fb4a-153">Stosuje zasady do typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="7fb4a-154">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="7fb4a-154">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)|<span data-ttu-id="7fb4a-155">Stosuje zasady do typu, jeśli te zasady zostały doliczone do metody reprezentowanej przez zawierający `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="7fb4a-156">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="7fb4a-156">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|<span data-ttu-id="7fb4a-157">Stosuje zasady na typ reprezentowany przez <xref:System.Type> argument przekazywany do metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7fb4a-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7fb4a-158">Parent Elements</span></span>  
  
|<span data-ttu-id="7fb4a-159">Element</span><span class="sxs-lookup"><span data-stu-id="7fb4a-159">Element</span></span>|<span data-ttu-id="7fb4a-160">Opis</span><span class="sxs-lookup"><span data-stu-id="7fb4a-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fb4a-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="7fb4a-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="7fb4a-162">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="7fb4a-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="7fb4a-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="7fb4a-164">Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fb4a-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fb4a-165">Remarks</span></span>  
 <span data-ttu-id="7fb4a-166">Element `<Method>` elementu metody ogólnej stosuje swoje zasady do wszystkich wystąpień, które nie mają własnych zasad.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="7fb4a-167">Możesz użyć `Signature` atrybutu, aby określić zasady dla przeciążeń określonej metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="7fb4a-168">W przeciwnym razie, jeśli `Signature` atrybut jest nieobecne, dyrektyw środowiska uruchomieniowego ma zastosowanie do wszystkich przeciążeń metody.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="7fb4a-169">Nie można zdefiniować zasady odbicia środowiska uruchomieniowego dla konstruktora przy użyciu `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="7fb4a-170">Zamiast tego należy użyć `Activate` atrybutu [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md), lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-170">Instead, use the `Activate` attribute of the  [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), [\<Type>](../../../docs/framework/net-native/type-element-net-native.md), or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fb4a-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="7fb4a-171">Example</span></span>  
 <span data-ttu-id="7fb4a-172">`Stringify` Metody w poniższym przykładzie jest metodą formatowania ogólnego przeznaczenia, która używa odbicia w celu konwersji obiektu na jego reprezentację ciągu.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="7fb4a-173">Oprócz wywołanie domyślnego obiektu `ToString` metody, metoda może wygenerować sformatowany ciąg wynikowy przez przekazanie obiektu `ToString` metoda ciąg formatu <xref:System.IFormatProvider> implementacji i / lub.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="7fb4a-174">Można też wywołać jedną z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> przeciążenia, które konwertuje liczbę na jego reprezentację binarnym, szesnastkowym lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="7fb4a-175">`Stringify` Metoda może być wywoływana przez kod, podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="7fb4a-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="7fb4a-176">Jednak, gdy skompilowano z architekturą .NET Native, przykładu może zgłosić liczba wyjątków w czasie wykonywania, w tym <xref:System.NullReferenceException> i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, dzieje się tak dlatego `Stringify` jest — metoda przeznaczona głównie w celu obsługi dynamicznie formatowanie typów pierwotnych w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="7fb4a-177">Jednak ich metadanych nie zostanie udostępniony przez domyślny plik dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="7fb4a-178">Nawet wtedy, gdy ich metadane są udostępniane, jednak przykład generuje [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątków ponieważ odpowiednie `ToString` nie zostały zawiera implementacji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="7fb4a-179">Wyjątki te mogą wszystkie zostać usunięte przy użyciu [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu, aby zdefiniować typy, których metadane muszą być obecne, a przez dodanie `<Method>` elementy, aby zapewnić, że implementacja przeciążenia metody którą można wywołać dynamicznie również jest obecny.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-179">These exceptions can all be eliminated by using the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="7fb4a-180">Poniżej znajduje się plik default.rd.xml eliminuje tych wyjątków i zezwala na przykład można wykonać bez błędów.</span><span class="sxs-lookup"><span data-stu-id="7fb4a-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7fb4a-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fb4a-181">See also</span></span>
- [<span data-ttu-id="7fb4a-182">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7fb4a-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7fb4a-183">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7fb4a-183">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="7fb4a-184">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7fb4a-184">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="7fb4a-185">\<MethodInstantiation > Element</span><span class="sxs-lookup"><span data-stu-id="7fb4a-185">\<MethodInstantiation> Element</span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)
