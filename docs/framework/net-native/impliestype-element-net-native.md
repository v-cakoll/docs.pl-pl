---
title: <ImpliesType>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181015"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="eadff-102">\<ImpliesType>— Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="eadff-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="eadff-103">Stosuje zasady do typu, jeśli te zasady zostały zastosowane do zawierającego je typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="eadff-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eadff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eadff-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eadff-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eadff-105">Attributes and Elements</span></span>  
 <span data-ttu-id="eadff-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eadff-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eadff-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eadff-107">Attributes</span></span>  
  
|<span data-ttu-id="eadff-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="eadff-108">Attribute</span></span>|<span data-ttu-id="eadff-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="eadff-109">Attribute type</span></span>|<span data-ttu-id="eadff-110">Opis</span><span class="sxs-lookup"><span data-stu-id="eadff-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="eadff-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="eadff-111">General</span></span>|<span data-ttu-id="eadff-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="eadff-112">Required attribute.</span></span> <span data-ttu-id="eadff-113">Określa nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="eadff-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="eadff-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="eadff-114">Reflection</span></span>|<span data-ttu-id="eadff-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-115">Optional attribute.</span></span> <span data-ttu-id="eadff-116">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="eadff-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="eadff-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="eadff-117">Reflection</span></span>|<span data-ttu-id="eadff-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-118">Optional attribute.</span></span> <span data-ttu-id="eadff-119">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="eadff-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="eadff-120">Odbicie</span><span class="sxs-lookup"><span data-stu-id="eadff-120">Reflection</span></span>|<span data-ttu-id="eadff-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-121">Optional attribute.</span></span> <span data-ttu-id="eadff-122">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="eadff-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="eadff-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="eadff-123">Serialization</span></span>|<span data-ttu-id="eadff-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-124">Optional attribute.</span></span> <span data-ttu-id="eadff-125">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="eadff-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="eadff-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="eadff-126">Serialization</span></span>|<span data-ttu-id="eadff-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-127">Optional attribute.</span></span> <span data-ttu-id="eadff-128">Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="eadff-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="eadff-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="eadff-129">Serialization</span></span>|<span data-ttu-id="eadff-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-130">Optional attribute.</span></span> <span data-ttu-id="eadff-131">Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="eadff-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="eadff-132">Serializacja</span><span class="sxs-lookup"><span data-stu-id="eadff-132">Serialization</span></span>|<span data-ttu-id="eadff-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-133">Optional attribute.</span></span> <span data-ttu-id="eadff-134">Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="eadff-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="eadff-135">Interop</span><span class="sxs-lookup"><span data-stu-id="eadff-135">Interop</span></span>|<span data-ttu-id="eadff-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-136">Optional attribute.</span></span> <span data-ttu-id="eadff-137">Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.</span><span class="sxs-lookup"><span data-stu-id="eadff-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="eadff-138">Interop</span><span class="sxs-lookup"><span data-stu-id="eadff-138">Interop</span></span>|<span data-ttu-id="eadff-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-139">Optional attribute.</span></span> <span data-ttu-id="eadff-140">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="eadff-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="eadff-141">Interop</span><span class="sxs-lookup"><span data-stu-id="eadff-141">Interop</span></span>|<span data-ttu-id="eadff-142">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eadff-142">Optional attribute.</span></span> <span data-ttu-id="eadff-143">Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="eadff-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="eadff-144">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="eadff-144">Name attribute</span></span>  
  
|<span data-ttu-id="eadff-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="eadff-145">Value</span></span>|<span data-ttu-id="eadff-146">Opis</span><span class="sxs-lookup"><span data-stu-id="eadff-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eadff-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="eadff-147">*type_name*</span></span>|<span data-ttu-id="eadff-148">Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="eadff-148">The type name.</span></span> <span data-ttu-id="eadff-149">Jeśli typ reprezentowany przez ten element znajduje się `<ImpliesType>` w tej samej przestrzeni nazw co element zawierający `<Type>` , *TYPE_NAME* może zawierać nazwę typu bez jego przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="eadff-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="eadff-150">W przeciwnym razie *TYPE_NAME* musi zawierać w pełni kwalifikowaną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="eadff-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="eadff-151">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="eadff-151">All other attributes</span></span>  
  
|<span data-ttu-id="eadff-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="eadff-152">Value</span></span>|<span data-ttu-id="eadff-153">Opis</span><span class="sxs-lookup"><span data-stu-id="eadff-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eadff-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="eadff-154">*policy_setting*</span></span>|<span data-ttu-id="eadff-155">Ustawienie, które ma zostać zastosowane do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="eadff-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="eadff-156">Możliwe wartości to `All` , `Auto` ,,,,, `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` i `Required All` .</span><span class="sxs-lookup"><span data-stu-id="eadff-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="eadff-157">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="eadff-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eadff-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eadff-158">Child Elements</span></span>  
 <span data-ttu-id="eadff-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="eadff-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eadff-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eadff-160">Parent Elements</span></span>  
  
|<span data-ttu-id="eadff-161">Element</span><span class="sxs-lookup"><span data-stu-id="eadff-161">Element</span></span>|<span data-ttu-id="eadff-162">Opis</span><span class="sxs-lookup"><span data-stu-id="eadff-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="eadff-163">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="eadff-163">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="eadff-164">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="eadff-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="eadff-165">Stosuje zasady odbicia do metody.</span><span class="sxs-lookup"><span data-stu-id="eadff-165">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eadff-166">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eadff-166">Remarks</span></span>  
 <span data-ttu-id="eadff-167">`<ImpliesType>`Element jest przeznaczony głównie do użytku przez biblioteki.</span><span class="sxs-lookup"><span data-stu-id="eadff-167">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="eadff-168">Dotyczy to następujących scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="eadff-168">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="eadff-169">Jeśli procedura musi być odzwierciedlona na jednym typie, konieczna jest potrzeba odbicia w drugim typie.</span><span class="sxs-lookup"><span data-stu-id="eadff-169">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="eadff-170">Metadane dla implikowanego wystąpienia drugiego typu są w inny sposób niedostępne, ponieważ analiza statyczna nie wskazuje, że jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="eadff-170">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="eadff-171">Najczęściej istnieją dwa typy to ogólne wystąpienia z argumentami typu współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="eadff-171">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="eadff-172">`<ImpliesType>`Element został zdefiniowany z założeniem, że potrzeba odbicia w typie określonym przez jego element nadrzędny oznacza potrzebę odbicia w typie określonym przez `<ImpliesType>` element.</span><span class="sxs-lookup"><span data-stu-id="eadff-172">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="eadff-173">Na przykład następujące dyrektywy odbicia mają zastosowanie do dwóch typów `Explicit<T>` i `Implicit<T>` .</span><span class="sxs-lookup"><span data-stu-id="eadff-173">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="eadff-174">Ta dyrektywa nie działa, chyba że w przypadku wystąpienia `Explicit` ma zdefiniowane `Dynamic` ustawienie zasad.</span><span class="sxs-lookup"><span data-stu-id="eadff-174">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="eadff-175">Na przykład, jeśli jest to przypadek dla `Explicit<Int32>` , `Implicit<Int32>` zostanie utworzone wystąpienie z publicznymi składowymi, a ich metadane są udostępniane do programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="eadff-175">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="eadff-176">Poniżej znajduje się przykład rzeczywistego, który ma zastosowanie do co najmniej jednego serializatora.</span><span class="sxs-lookup"><span data-stu-id="eadff-176">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="eadff-177">Dyrektywy przechwytują wymaganie, które odzwierciedlają coś, co zostało wpisane, ponieważ `IList<` *something* `>` zawiera również odzwierciedlenie odpowiedniego `List<` *something* `>` typu, bez konieczności adnotacji dla poszczególnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eadff-177">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="eadff-178">`<ImpliesType>`Element może również znajdować się w obrębie `<Method>` elementu, ponieważ w niektórych przypadkach wystąpienie metody ogólnej implikuje odzwierciedlenie w wystąpieniu typu.</span><span class="sxs-lookup"><span data-stu-id="eadff-178">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="eadff-179">Załóżmy na przykład, że metoda ogólna `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` , do której dana biblioteka będzie uzyskiwać dostęp dynamicznie wraz ze skojarzonymi <xref:System.Collections.Generic.List%601> i <xref:System.Array> typami.</span><span class="sxs-lookup"><span data-stu-id="eadff-179">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="eadff-180">Może to być wyrażone jako:</span><span class="sxs-lookup"><span data-stu-id="eadff-180">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eadff-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eadff-181">See also</span></span>

- [<span data-ttu-id="eadff-182">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="eadff-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="eadff-183">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="eadff-183">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="eadff-184">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="eadff-184">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
