---
title: <ImpliesType> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ef238a2cb852ecd7fa3f0e2dbe4048ff03a4139
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868631"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="989d8-102">\<ImpliesType > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="989d8-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="989d8-103">W przypadku zasad do typu, że zasady zostały zastosowane do zawierający typ lub metoda.</span><span class="sxs-lookup"><span data-stu-id="989d8-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="989d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="989d8-104">Syntax</span></span>  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
             Browse="policy_type"  
             Dynamic="policy_type"  
             Serialize="policy_type"   
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="989d8-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="989d8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="989d8-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="989d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="989d8-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="989d8-107">Attributes</span></span>  
  
|<span data-ttu-id="989d8-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="989d8-108">Attribute</span></span>|<span data-ttu-id="989d8-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="989d8-109">Attribute type</span></span>|<span data-ttu-id="989d8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="989d8-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="989d8-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="989d8-111">General</span></span>|<span data-ttu-id="989d8-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="989d8-112">Required attribute.</span></span> <span data-ttu-id="989d8-113">Określa nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="989d8-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="989d8-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="989d8-114">Reflection</span></span>|<span data-ttu-id="989d8-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-115">Optional attribute.</span></span> <span data-ttu-id="989d8-116">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="989d8-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="989d8-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="989d8-117">Reflection</span></span>|<span data-ttu-id="989d8-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-118">Optional attribute.</span></span> <span data-ttu-id="989d8-119">Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="989d8-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="989d8-120">Odbicie</span><span class="sxs-lookup"><span data-stu-id="989d8-120">Reflection</span></span>|<span data-ttu-id="989d8-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-121">Optional attribute.</span></span> <span data-ttu-id="989d8-122">Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="989d8-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="989d8-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="989d8-123">Serialization</span></span>|<span data-ttu-id="989d8-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-124">Optional attribute.</span></span> <span data-ttu-id="989d8-125">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="989d8-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="989d8-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="989d8-126">Serialization</span></span>|<span data-ttu-id="989d8-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-127">Optional attribute.</span></span> <span data-ttu-id="989d8-128">Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="989d8-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="989d8-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="989d8-129">Serialization</span></span>|<span data-ttu-id="989d8-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-130">Optional attribute.</span></span> <span data-ttu-id="989d8-131">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="989d8-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="989d8-132">Serializacja</span><span class="sxs-lookup"><span data-stu-id="989d8-132">Serialization</span></span>|<span data-ttu-id="989d8-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-133">Optional attribute.</span></span> <span data-ttu-id="989d8-134">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="989d8-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="989d8-135">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="989d8-135">Interop</span></span>|<span data-ttu-id="989d8-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-136">Optional attribute.</span></span> <span data-ttu-id="989d8-137">Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="989d8-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="989d8-138">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="989d8-138">Interop</span></span>|<span data-ttu-id="989d8-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-139">Optional attribute.</span></span> <span data-ttu-id="989d8-140">Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="989d8-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="989d8-141">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="989d8-141">Interop</span></span>|<span data-ttu-id="989d8-142">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="989d8-142">Optional attribute.</span></span> <span data-ttu-id="989d8-143">Określa zasady dla marshaling typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="989d8-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="989d8-144">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="989d8-144">Name attribute</span></span>  
  
|<span data-ttu-id="989d8-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="989d8-145">Value</span></span>|<span data-ttu-id="989d8-146">Opis</span><span class="sxs-lookup"><span data-stu-id="989d8-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="989d8-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="989d8-147">*type_name*</span></span>|<span data-ttu-id="989d8-148">Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="989d8-148">The type name.</span></span> <span data-ttu-id="989d8-149">Jeśli typ reprezentowany przez ten `<ImpliesType>` element znajduje się w tej samej przestrzeni nazw jako jego zawierający `<Type>` elementu *type_name* można uwzględnić nazwę typu bez jego przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="989d8-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="989d8-150">W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowana nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="989d8-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="989d8-151">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="989d8-151">All other attributes</span></span>  
  
|<span data-ttu-id="989d8-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="989d8-152">Value</span></span>|<span data-ttu-id="989d8-153">Opis</span><span class="sxs-lookup"><span data-stu-id="989d8-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="989d8-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="989d8-154">*policy_setting*</span></span>|<span data-ttu-id="989d8-155">Ustawienia do zastosowania do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="989d8-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="989d8-156">Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="989d8-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="989d8-157">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="989d8-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="989d8-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="989d8-158">Child Elements</span></span>  
 <span data-ttu-id="989d8-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="989d8-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="989d8-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="989d8-160">Parent Elements</span></span>  
  
|<span data-ttu-id="989d8-161">Element</span><span class="sxs-lookup"><span data-stu-id="989d8-161">Element</span></span>|<span data-ttu-id="989d8-162">Opis</span><span class="sxs-lookup"><span data-stu-id="989d8-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="989d8-163">\<Type></span><span class="sxs-lookup"><span data-stu-id="989d8-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="989d8-164">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="989d8-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="989d8-165">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="989d8-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="989d8-166">Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="989d8-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="989d8-167">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="989d8-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="989d8-168">Zastosowanie zasad odbicia do metody.</span><span class="sxs-lookup"><span data-stu-id="989d8-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="989d8-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="989d8-169">Remarks</span></span>  
 <span data-ttu-id="989d8-170">`<ImpliesType>` Element jest przeznaczona głównie do użytku przez biblioteki.</span><span class="sxs-lookup"><span data-stu-id="989d8-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="989d8-171">Dotyczy on następujący scenariusz:</span><span class="sxs-lookup"><span data-stu-id="989d8-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="989d8-172">Jeśli procedura wymaga zastanowić się nad jednego typu, niekoniecznie musi na zastanowienie się nad drugiego typu.</span><span class="sxs-lookup"><span data-stu-id="989d8-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="989d8-173">Metadane dla wystąpienia dorozumianych drugi typ jest niedostępna, w przeciwnym razie w przypadku, ponieważ analizy statycznej nie oznacza, że jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="989d8-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="989d8-174">Najczęściej są dwa typy ogólnych instancji z argumentami typu udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="989d8-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="989d8-175">`<ImpliesType>` Element został zdefiniowany przy założeniu, że na potrzeby odbicia na typ określony przez jego elementu nadrzędnego oznacza potrzebę odbicia dla typu określonego przez `<ImpliesType>` elementu.</span><span class="sxs-lookup"><span data-stu-id="989d8-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="989d8-176">Na przykład, zastosuj następujące dyrektywy odbicia do dwóch typów `Explicit<T>` i `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="989d8-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="989d8-177">Ta dyrektywa nie obowiązuje, chyba że egzemplarz o `Explicit` ma zdefiniowanych `Dynamic` ustawienie zasad.</span><span class="sxs-lookup"><span data-stu-id="989d8-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="989d8-178">Na przykład, jeśli tak jest aby uzyskać `Explicit<Int32>`, `Implicit<Int32>` jest utworzone za pomocą jego publiczny dostęp do konta root członków i ich metadanych jest dostępne dla programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="989d8-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="989d8-179">Oto przykład świata rzeczywistego, który ma zastosowanie do co najmniej jeden element serializujący.</span><span class="sxs-lookup"><span data-stu-id="989d8-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="989d8-180">Dyrektywy przechwytywania wymogu, że rozważania na temat coś wpisać jako `IList<` *coś* `>` obejmuje również odzwierciedlenie w odpowiedniej `List<` *coś* `>` typu bez konieczności żadnej adnotacji poszczególnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="989d8-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="989d8-181">`<ImpliesType>` Element może znajdować się również w `<Method>` elementu, ponieważ w niektórych przypadkach tworzenia wystąpienia metody rodzajowej oznacza rozważania na temat wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="989d8-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="989d8-182">Na przykład Wyobraź sobie metody ogólnej `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` który danej biblioteki będzie miał dostęp dynamicznie wraz z skojarzonego <xref:System.Collections.Generic.List%601> i <xref:System.Array> typów.</span><span class="sxs-lookup"><span data-stu-id="989d8-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="989d8-183">Może to być wyrażona jako:</span><span class="sxs-lookup"><span data-stu-id="989d8-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="989d8-184">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="989d8-184">See also</span></span>

- [<span data-ttu-id="989d8-185">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="989d8-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="989d8-186">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="989d8-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="989d8-187">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="989d8-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
