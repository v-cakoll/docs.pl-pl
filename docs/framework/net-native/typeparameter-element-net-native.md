---
title: Element <TypeParameter> (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
ms.openlocfilehash: c69b535f3a01c287d30189138130066fc10a77e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128925"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="678c0-102">\<element > TypeParameter (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="678c0-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="678c0-103">Stosuje zasady do typu reprezentowanego przez argument typu przekazaną do metody.</span><span class="sxs-lookup"><span data-stu-id="678c0-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="678c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="678c0-104">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="678c0-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="678c0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="678c0-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="678c0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="678c0-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="678c0-107">Attributes</span></span>  
  
|<span data-ttu-id="678c0-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="678c0-108">Attribute</span></span>|<span data-ttu-id="678c0-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="678c0-109">Attribute type</span></span>|<span data-ttu-id="678c0-110">Opis</span><span class="sxs-lookup"><span data-stu-id="678c0-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="678c0-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="678c0-111">General</span></span>|<span data-ttu-id="678c0-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="678c0-112">Required attribute.</span></span> <span data-ttu-id="678c0-113">Nazwa parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="678c0-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="678c0-114">Na przykład w przypadku `Type.GetInterfaceMap(Type interfaceType)`sygnatury metody wartość atrybutu `Name` to "InterfaceType".</span><span class="sxs-lookup"><span data-stu-id="678c0-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="678c0-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="678c0-115">Reflection</span></span>|<span data-ttu-id="678c0-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-116">Optional attribute.</span></span> <span data-ttu-id="678c0-117">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="678c0-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="678c0-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="678c0-118">Reflection</span></span>|<span data-ttu-id="678c0-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-119">Optional attribute.</span></span> <span data-ttu-id="678c0-120">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="678c0-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="678c0-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="678c0-121">Reflection</span></span>|<span data-ttu-id="678c0-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-122">Optional attribute.</span></span> <span data-ttu-id="678c0-123">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="678c0-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="678c0-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="678c0-124">Serialization</span></span>|<span data-ttu-id="678c0-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-125">Optional attribute.</span></span> <span data-ttu-id="678c0-126">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="678c0-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="678c0-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="678c0-127">Serialization</span></span>|<span data-ttu-id="678c0-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-128">Optional attribute.</span></span> <span data-ttu-id="678c0-129">Kontroluje zasady dla serializacji korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="678c0-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="678c0-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="678c0-130">Serialization</span></span>|<span data-ttu-id="678c0-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-131">Optional attribute.</span></span> <span data-ttu-id="678c0-132">Kontroluje zasady dla serializacji JSON korzystającej z klasy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="678c0-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="678c0-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="678c0-133">Serialization</span></span>|<span data-ttu-id="678c0-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-134">Optional attribute.</span></span> <span data-ttu-id="678c0-135">Kontroluje zasady dla serializacji XML, która używa klasy <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="678c0-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="678c0-136">Interop</span><span class="sxs-lookup"><span data-stu-id="678c0-136">Interop</span></span>|<span data-ttu-id="678c0-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-137">Optional attribute.</span></span> <span data-ttu-id="678c0-138">Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.</span><span class="sxs-lookup"><span data-stu-id="678c0-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="678c0-139">Interop</span><span class="sxs-lookup"><span data-stu-id="678c0-139">Interop</span></span>|<span data-ttu-id="678c0-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-140">Optional attribute.</span></span> <span data-ttu-id="678c0-141">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="678c0-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="678c0-142">Interop</span><span class="sxs-lookup"><span data-stu-id="678c0-142">Interop</span></span>|<span data-ttu-id="678c0-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="678c0-143">Optional attribute.</span></span> <span data-ttu-id="678c0-144">Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="678c0-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="678c0-145">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="678c0-145">Name attribute</span></span>  
  
|<span data-ttu-id="678c0-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="678c0-146">Value</span></span>|<span data-ttu-id="678c0-147">Opis</span><span class="sxs-lookup"><span data-stu-id="678c0-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="678c0-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="678c0-148">*parameter_name*</span></span>|<span data-ttu-id="678c0-149">Nazwa parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="678c0-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="678c0-150">Na przykład w przypadku `Type.GetInterfaceMap(Type interfaceType)`sygnatury metody wartość atrybutu `Name` to "InterfaceType".</span><span class="sxs-lookup"><span data-stu-id="678c0-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="678c0-151">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="678c0-151">All other attributes</span></span>  
  
|<span data-ttu-id="678c0-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="678c0-152">Value</span></span>|<span data-ttu-id="678c0-153">Opis</span><span class="sxs-lookup"><span data-stu-id="678c0-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="678c0-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="678c0-154">*policy_setting*</span></span>|<span data-ttu-id="678c0-155">Ustawienie, które ma zostać zastosowane do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="678c0-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="678c0-156">Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="678c0-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="678c0-157">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="678c0-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="678c0-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="678c0-158">Child Elements</span></span>  
 <span data-ttu-id="678c0-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="678c0-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="678c0-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="678c0-160">Parent Elements</span></span>  
  
|<span data-ttu-id="678c0-161">Element</span><span class="sxs-lookup"><span data-stu-id="678c0-161">Element</span></span>|<span data-ttu-id="678c0-162">Opis</span><span class="sxs-lookup"><span data-stu-id="678c0-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="678c0-163">> metody\<</span><span class="sxs-lookup"><span data-stu-id="678c0-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="678c0-164">Stosuje zasady odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="678c0-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="678c0-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="678c0-165">Remarks</span></span>  
 <span data-ttu-id="678c0-166">Element `<TypeParameter>` jest podobny do [parametru\<](parameter-element-net-native.md) elementu, z tą różnicą, że może być stosowany tylko do parametrów typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="678c0-166">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="678c0-167">Stosuje zasady do dowolnego typu, który jest reprezentowany w czasie wykonywania przez argument typu określony przez atrybut `Name`.</span><span class="sxs-lookup"><span data-stu-id="678c0-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="678c0-168">Na przykład serializator JSON NewtonSoft zawiera statyczną metodę `JsonConvert.DeserializeObject(String value, Type type)`.</span><span class="sxs-lookup"><span data-stu-id="678c0-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="678c0-169">Następujące dyrektywy odbicia:</span><span class="sxs-lookup"><span data-stu-id="678c0-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="678c0-170">Określ, że metadane dla typu środowiska uruchomieniowego reprezentowane przez argument `type` powinny zostać udostępnione do serializacji.</span><span class="sxs-lookup"><span data-stu-id="678c0-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="678c0-171">Jeśli te dyrektywy środowiska uruchomieniowego dotyczą projektu, który zawiera następujący kod źródłowy:</span><span class="sxs-lookup"><span data-stu-id="678c0-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="678c0-172">dyrektywy odbicia tworzą metadane dla typu `StockQuote` dostępnego dla serializatora JSON NewtonSoft w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="678c0-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678c0-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="678c0-173">See also</span></span>

- [<span data-ttu-id="678c0-174">Element >\<metody</span><span class="sxs-lookup"><span data-stu-id="678c0-174">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="678c0-175">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="678c0-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="678c0-176">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="678c0-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="678c0-177">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="678c0-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
