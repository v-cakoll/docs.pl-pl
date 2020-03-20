---
title: <ImpliesType>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181015"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="08ebe-102">\<Element imptype> (natywny.NET)</span><span class="sxs-lookup"><span data-stu-id="08ebe-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="08ebe-103">Stosuje zasady do typu, jeśli ta zasada została zastosowana do typu lub metody zawierającej.</span><span class="sxs-lookup"><span data-stu-id="08ebe-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08ebe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08ebe-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08ebe-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="08ebe-105">Attributes and Elements</span></span>  
 <span data-ttu-id="08ebe-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="08ebe-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08ebe-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="08ebe-107">Attributes</span></span>  
  
|<span data-ttu-id="08ebe-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="08ebe-108">Attribute</span></span>|<span data-ttu-id="08ebe-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="08ebe-109">Attribute type</span></span>|<span data-ttu-id="08ebe-110">Opis</span><span class="sxs-lookup"><span data-stu-id="08ebe-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="08ebe-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="08ebe-111">General</span></span>|<span data-ttu-id="08ebe-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="08ebe-112">Required attribute.</span></span> <span data-ttu-id="08ebe-113">Określa nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="08ebe-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="08ebe-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="08ebe-114">Reflection</span></span>|<span data-ttu-id="08ebe-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-115">Optional attribute.</span></span> <span data-ttu-id="08ebe-116">Steruje dostępem środowiska wykonawczego do konstruktorów, aby włączyć aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="08ebe-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="08ebe-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="08ebe-117">Reflection</span></span>|<span data-ttu-id="08ebe-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-118">Optional attribute.</span></span> <span data-ttu-id="08ebe-119">Steruje wykonywaniem zapytań o informacje o elementach programu, ale nie włącza dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="08ebe-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="08ebe-120">Odbicie</span><span class="sxs-lookup"><span data-stu-id="08ebe-120">Reflection</span></span>|<span data-ttu-id="08ebe-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-121">Optional attribute.</span></span> <span data-ttu-id="08ebe-122">Steruje dostępem środowiska uruchomieniowego do wszystkich elementów członkowskich typu, w tym konstruktorów, metod, pól, właściwości i zdarzeń, aby włączyć programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="08ebe-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="08ebe-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="08ebe-123">Serialization</span></span>|<span data-ttu-id="08ebe-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-124">Optional attribute.</span></span> <span data-ttu-id="08ebe-125">Steruje dostępem środowiska wykonawczego do konstruktorów, pól i właściwości, aby umożliwić serializowanie i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON firmy Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="08ebe-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="08ebe-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="08ebe-126">Serialization</span></span>|<span data-ttu-id="08ebe-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-127">Optional attribute.</span></span> <span data-ttu-id="08ebe-128">Steruje zasadami serializacji, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> która używa klasy.</span><span class="sxs-lookup"><span data-stu-id="08ebe-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="08ebe-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="08ebe-129">Serialization</span></span>|<span data-ttu-id="08ebe-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-130">Optional attribute.</span></span> <span data-ttu-id="08ebe-131">Steruje zasadami serializacji JSON, która używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="08ebe-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="08ebe-132">Serializacja</span><span class="sxs-lookup"><span data-stu-id="08ebe-132">Serialization</span></span>|<span data-ttu-id="08ebe-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-133">Optional attribute.</span></span> <span data-ttu-id="08ebe-134">Steruje zasadami serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> tej klasy.</span><span class="sxs-lookup"><span data-stu-id="08ebe-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="08ebe-135">Interop</span><span class="sxs-lookup"><span data-stu-id="08ebe-135">Interop</span></span>|<span data-ttu-id="08ebe-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-136">Optional attribute.</span></span> <span data-ttu-id="08ebe-137">Steruje zasadami organizowania typów odwołań do środowiska wykonawczego systemu Windows i środowiska COM.</span><span class="sxs-lookup"><span data-stu-id="08ebe-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="08ebe-138">Interop</span><span class="sxs-lookup"><span data-stu-id="08ebe-138">Interop</span></span>|<span data-ttu-id="08ebe-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-139">Optional attribute.</span></span> <span data-ttu-id="08ebe-140">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="08ebe-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="08ebe-141">Interop</span><span class="sxs-lookup"><span data-stu-id="08ebe-141">Interop</span></span>|<span data-ttu-id="08ebe-142">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08ebe-142">Optional attribute.</span></span> <span data-ttu-id="08ebe-143">Steruje zasadami organizowania typów wartości do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="08ebe-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="08ebe-144">Atrybut Nazwa</span><span class="sxs-lookup"><span data-stu-id="08ebe-144">Name attribute</span></span>  
  
|<span data-ttu-id="08ebe-145">Wartość</span><span class="sxs-lookup"><span data-stu-id="08ebe-145">Value</span></span>|<span data-ttu-id="08ebe-146">Opis</span><span class="sxs-lookup"><span data-stu-id="08ebe-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08ebe-147">*Type_name*</span><span class="sxs-lookup"><span data-stu-id="08ebe-147">*type_name*</span></span>|<span data-ttu-id="08ebe-148">Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="08ebe-148">The type name.</span></span> <span data-ttu-id="08ebe-149">Jeśli typ reprezentowany `<ImpliesType>` przez ten element znajduje się w `<Type>` tej samej przestrzeni nazw co jego element zawierający, *type_name* może zawierać nazwę typu bez jego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="08ebe-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="08ebe-150">W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowaną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="08ebe-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="08ebe-151">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="08ebe-151">All other attributes</span></span>  
  
|<span data-ttu-id="08ebe-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="08ebe-152">Value</span></span>|<span data-ttu-id="08ebe-153">Opis</span><span class="sxs-lookup"><span data-stu-id="08ebe-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08ebe-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="08ebe-154">*policy_setting*</span></span>|<span data-ttu-id="08ebe-155">Ustawienie, które ma zastosowanie do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="08ebe-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="08ebe-156">Możliwe wartości `All` `Auto`to `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , i .</span><span class="sxs-lookup"><span data-stu-id="08ebe-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="08ebe-157">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="08ebe-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08ebe-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="08ebe-158">Child Elements</span></span>  
 <span data-ttu-id="08ebe-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="08ebe-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08ebe-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="08ebe-160">Parent Elements</span></span>  
  
|<span data-ttu-id="08ebe-161">Element</span><span class="sxs-lookup"><span data-stu-id="08ebe-161">Element</span></span>|<span data-ttu-id="08ebe-162">Opis</span><span class="sxs-lookup"><span data-stu-id="08ebe-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08ebe-163">\<Typ></span><span class="sxs-lookup"><span data-stu-id="08ebe-163">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="08ebe-164">Stosuje zasady odbicia do typu i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="08ebe-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="08ebe-165">\<>typu></span><span class="sxs-lookup"><span data-stu-id="08ebe-165">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="08ebe-166">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="08ebe-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="08ebe-167">\<Metoda></span><span class="sxs-lookup"><span data-stu-id="08ebe-167">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="08ebe-168">Stosuje zasady odbicia do metody.</span><span class="sxs-lookup"><span data-stu-id="08ebe-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08ebe-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08ebe-169">Remarks</span></span>  
 <span data-ttu-id="08ebe-170">Element `<ImpliesType>` jest przeznaczony głównie do użytku przez biblioteki.</span><span class="sxs-lookup"><span data-stu-id="08ebe-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="08ebe-171">Dotyczy następującego scenariusza:</span><span class="sxs-lookup"><span data-stu-id="08ebe-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="08ebe-172">Jeśli procedura musi zastanowić się nad jednym typem, musi koniecznie zastanowić się nad drugim typem.</span><span class="sxs-lookup"><span data-stu-id="08ebe-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="08ebe-173">Metadane dla dorozumianego wystąpienia drugiego typu jest w przeciwnym razie niedostępne, ponieważ analiza statyczna nie wskazuje, że jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="08ebe-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="08ebe-174">Najczęściej dwa typy są ogólne wystąpienia z argumentami typu udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="08ebe-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="08ebe-175">Element `<ImpliesType>` został zdefiniowany przy założeniu, że potrzeba odbicia na typ określony przez jego element nadrzędny implikuje potrzebę odbicia na typ określony przez `<ImpliesType>` element.</span><span class="sxs-lookup"><span data-stu-id="08ebe-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="08ebe-176">Na przykład następujące dyrektywy refleksji mają `Explicit<T>` zastosowanie `Implicit<T>`do dwóch typów i .</span><span class="sxs-lookup"><span data-stu-id="08ebe-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="08ebe-177">Ta dyrektywa nie ma wpływu, `Explicit` chyba że `Dynamic` wystąpienie ma zdefiniowane ustawienie zasad.</span><span class="sxs-lookup"><span data-stu-id="08ebe-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="08ebe-178">Na przykład jeśli tak jest `Explicit<Int32>`w `Implicit<Int32>` przypadku , jest tworzone z jego elementów publicznych elementów członkowskich zakorzenione, a ich metadane są dostępne dla programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="08ebe-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="08ebe-179">Poniżej przedstawiono przykład w świecie rzeczywistym, który ma zastosowanie do co najmniej jednego serializatora.</span><span class="sxs-lookup"><span data-stu-id="08ebe-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="08ebe-180">Dyrektywy przechwytywania wymóg, że refleksja na `IList<`coś wpisane jako *coś* `>` obejmuje również refleksji na odpowiedni `List<`typ *coś* `>` bez konieczności żadnych adnotacji na aplikację.</span><span class="sxs-lookup"><span data-stu-id="08ebe-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="08ebe-181">Element `<ImpliesType>` może również pojawić `<Method>` się w elemencie, ponieważ w niektórych przypadkach tworzenie wystąpienia metody rodzajowej oznacza odzwierciedlenia na wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="08ebe-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="08ebe-182">Na przykład wyobraź sobie `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` metodę rodzajową, że dana biblioteka <xref:System.Collections.Generic.List%601> <xref:System.Array> będzie uzyskać dostęp dynamicznie wraz z skojarzonych i typów.</span><span class="sxs-lookup"><span data-stu-id="08ebe-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="08ebe-183">Może to być wyrażone jako:</span><span class="sxs-lookup"><span data-stu-id="08ebe-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08ebe-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08ebe-184">See also</span></span>

- [<span data-ttu-id="08ebe-185">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="08ebe-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="08ebe-186">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="08ebe-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="08ebe-187">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="08ebe-187">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
