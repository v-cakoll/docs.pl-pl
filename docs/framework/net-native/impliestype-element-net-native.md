---
title: Element &lt;ImpliesType&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90e079b593ed124da79f5f87b5189d199bc4572a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltimpliestypegt-element-net-native"></a><span data-ttu-id="d5ec4-102">Element &lt;ImpliesType&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="d5ec4-102">&lt;ImpliesType&gt; Element (.NET Native)</span></span>
<span data-ttu-id="d5ec4-103">Stosuje zasady do typu, o ile tej zasady zostały zastosowane do typu zawierającego lub metody.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5ec4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5ec4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5ec4-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d5ec4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d5ec4-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5ec4-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d5ec4-107">Attributes</span></span>  
  
|<span data-ttu-id="d5ec4-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d5ec4-108">Attribute</span></span>|<span data-ttu-id="d5ec4-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="d5ec4-109">Attribute type</span></span>|<span data-ttu-id="d5ec4-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d5ec4-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="d5ec4-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="d5ec4-111">General</span></span>|<span data-ttu-id="d5ec4-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-112">Required attribute.</span></span> <span data-ttu-id="d5ec4-113">Określa nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="d5ec4-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="d5ec4-114">Reflection</span></span>|<span data-ttu-id="d5ec4-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-115">Optional attribute.</span></span> <span data-ttu-id="d5ec4-116">Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="d5ec4-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="d5ec4-117">Reflection</span></span>|<span data-ttu-id="d5ec4-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-118">Optional attribute.</span></span> <span data-ttu-id="d5ec4-119">Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="d5ec4-120">Odbicie</span><span class="sxs-lookup"><span data-stu-id="d5ec4-120">Reflection</span></span>|<span data-ttu-id="d5ec4-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-121">Optional attribute.</span></span> <span data-ttu-id="d5ec4-122">Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="d5ec4-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="d5ec4-123">Serialization</span></span>|<span data-ttu-id="d5ec4-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-124">Optional attribute.</span></span> <span data-ttu-id="d5ec4-125">Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="d5ec4-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="d5ec4-126">Serialization</span></span>|<span data-ttu-id="d5ec4-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-127">Optional attribute.</span></span> <span data-ttu-id="d5ec4-128">Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="d5ec4-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="d5ec4-129">Serialization</span></span>|<span data-ttu-id="d5ec4-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-130">Optional attribute.</span></span> <span data-ttu-id="d5ec4-131">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="d5ec4-132">Serializacja</span><span class="sxs-lookup"><span data-stu-id="d5ec4-132">Serialization</span></span>|<span data-ttu-id="d5ec4-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-133">Optional attribute.</span></span> <span data-ttu-id="d5ec4-134">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="d5ec4-135">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d5ec4-135">Interop</span></span>|<span data-ttu-id="d5ec4-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-136">Optional attribute.</span></span> <span data-ttu-id="d5ec4-137">Zasady kontroli przekazywanie typów referencyjnych do środowiska wykonawczego systemu Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="d5ec4-138">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d5ec4-138">Interop</span></span>|<span data-ttu-id="d5ec4-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-139">Optional attribute.</span></span> <span data-ttu-id="d5ec4-140">Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="d5ec4-141">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d5ec4-141">Interop</span></span>|<span data-ttu-id="d5ec4-142">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-142">Optional attribute.</span></span> <span data-ttu-id="d5ec4-143">Określa zasady dla przekazywanie typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="d5ec4-144">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="d5ec4-144">Name attribute</span></span>  
  
|<span data-ttu-id="d5ec4-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="d5ec4-145">Value</span></span>|<span data-ttu-id="d5ec4-146">Opis</span><span class="sxs-lookup"><span data-stu-id="d5ec4-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d5ec4-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="d5ec4-147">*type_name*</span></span>|<span data-ttu-id="d5ec4-148">Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-148">The type name.</span></span> <span data-ttu-id="d5ec4-149">Jeśli typ reprezentowany przez to `<ImpliesType>` element znajduje się w tej samej przestrzeni nazw jako jego zawierający `<Type>` elementu *type_name* mogą obejmować nazwę typu bez jego przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="d5ec4-150">W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowaną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="d5ec4-151">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="d5ec4-151">All other attributes</span></span>  
  
|<span data-ttu-id="d5ec4-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="d5ec4-152">Value</span></span>|<span data-ttu-id="d5ec4-153">Opis</span><span class="sxs-lookup"><span data-stu-id="d5ec4-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d5ec4-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="d5ec4-154">*policy_setting*</span></span>|<span data-ttu-id="d5ec4-155">Ustawienia do zastosowania dla tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="d5ec4-156">Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="d5ec4-157">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="d5ec4-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5ec4-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d5ec4-158">Child Elements</span></span>  
 <span data-ttu-id="d5ec4-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5ec4-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d5ec4-160">Parent Elements</span></span>  
  
|<span data-ttu-id="d5ec4-161">Element</span><span class="sxs-lookup"><span data-stu-id="d5ec4-161">Element</span></span>|<span data-ttu-id="d5ec4-162">Opis</span><span class="sxs-lookup"><span data-stu-id="d5ec4-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5ec4-163">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="d5ec4-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="d5ec4-164">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="d5ec4-165">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="d5ec4-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="d5ec4-166">Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="d5ec4-167">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="d5ec4-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="d5ec4-168">Stosuje zasady odbicia do metody.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5ec4-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5ec4-169">Remarks</span></span>  
 <span data-ttu-id="d5ec4-170">`<ImpliesType>` Element jest przeznaczony głównie do użytku przez biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="d5ec4-171">Dotyczy on następujący scenariusz:</span><span class="sxs-lookup"><span data-stu-id="d5ec4-171">It addresses the following scenario:</span></span>  
  
-   <span data-ttu-id="d5ec4-172">Jeśli procedura wymaga do uwzględnienia w jednym typie, niekoniecznie musi w drugim typu.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
-   <span data-ttu-id="d5ec4-173">Metadane dla domyślnych podczas tworzenia wystąpienia typu drugi jest niedostępny, w przeciwnym razie ponieważ analizy statycznej nie oznacza, że jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="d5ec4-174">Najczęściej są dwa typy ogólnych utworzonych wystąpieniach z argumentami typu udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="d5ec4-175">`<ImpliesType>` Element został zdefiniowany przy założeniu, że potrzeba odbicia w typie określonym przez jego elementu nadrzędnego oznacza potrzebę odbicia w typie określonym przez `<ImpliesType>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="d5ec4-176">Na przykład następujące dyrektywy odbicia dotyczą dwa typy `Explicit<T>` i `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="d5ec4-177">Ta dyrektywa jest nieskuteczne, chyba że tworzenie wystąpienia elementu `Explicit` ma zdefiniowane `Dynamic` ustawienie zasad.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="d5ec4-178">Na przykład, jeśli jest to w przypadku `Explicit<Int32>`, `Implicit<Int32>` zostanie uruchomiony z jego publicznych umieszczone elementy członkowskie, a ich metadanych jest dostępne dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="d5ec4-179">Poniżej przedstawiono przykład rzeczywistych, która ma zastosowanie do co najmniej jeden element serializujący.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="d5ec4-180">Dyrektywy przechwytywania wymagania, które odzwierciedlający na coś wpisane jako `IList<` *coś* `>` obejmuje również odbicia w odpowiedniej `List<` *coś* `>` typu bez konieczności żadnej adnotacji dla poszczególnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="d5ec4-181">`<ImpliesType>` Element może również zostać wyświetlony w `<Method>` elementu, ponieważ w niektórych przypadkach tworzenia wystąpienia metody ogólnej oznacza odzwierciedlający na wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="d5ec4-182">Załóżmy na przykład metoda ogólna `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` dostępnym dla danej biblioteki będzie dynamicznie wraz ze skojarzonym <xref:System.Collections.Generic.List%601> i <xref:System.Array> typów.</span><span class="sxs-lookup"><span data-stu-id="d5ec4-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="d5ec4-183">Można to wyrazić jako:</span><span class="sxs-lookup"><span data-stu-id="d5ec4-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5ec4-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5ec4-184">See Also</span></span>  
 [<span data-ttu-id="d5ec4-185">Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="d5ec4-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="d5ec4-186">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d5ec4-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="d5ec4-187">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d5ec4-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
