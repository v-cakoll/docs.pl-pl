---
title: <TypeParameter>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
ms.openlocfilehash: c69b535f3a01c287d30189138130066fc10a77e2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128925"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="8f4ac-102">\<TypeParameter>— Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="8f4ac-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="8f4ac-103">Stosuje zasady do typu reprezentowanego przez argument typu przekazaną do metody.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f4ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f4ac-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f4ac-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8f4ac-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8f4ac-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f4ac-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8f4ac-107">Attributes</span></span>  
  
|<span data-ttu-id="8f4ac-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8f4ac-108">Attribute</span></span>|<span data-ttu-id="8f4ac-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="8f4ac-109">Attribute type</span></span>|<span data-ttu-id="8f4ac-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8f4ac-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="8f4ac-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="8f4ac-111">General</span></span>|<span data-ttu-id="8f4ac-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-112">Required attribute.</span></span> <span data-ttu-id="8f4ac-113">Nazwa parametru typu <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="8f4ac-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="8f4ac-114">Na przykład dla sygnatury metody `Type.GetInterfaceMap(Type interfaceType)` wartość `Name` atrybutu to "InterfaceType".</span><span class="sxs-lookup"><span data-stu-id="8f4ac-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="8f4ac-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="8f4ac-115">Reflection</span></span>|<span data-ttu-id="8f4ac-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-116">Optional attribute.</span></span> <span data-ttu-id="8f4ac-117">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="8f4ac-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="8f4ac-118">Reflection</span></span>|<span data-ttu-id="8f4ac-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-119">Optional attribute.</span></span> <span data-ttu-id="8f4ac-120">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="8f4ac-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="8f4ac-121">Reflection</span></span>|<span data-ttu-id="8f4ac-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-122">Optional attribute.</span></span> <span data-ttu-id="8f4ac-123">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="8f4ac-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="8f4ac-124">Serialization</span></span>|<span data-ttu-id="8f4ac-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-125">Optional attribute.</span></span> <span data-ttu-id="8f4ac-126">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="8f4ac-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="8f4ac-127">Serialization</span></span>|<span data-ttu-id="8f4ac-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-128">Optional attribute.</span></span> <span data-ttu-id="8f4ac-129">Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="8f4ac-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="8f4ac-130">Serialization</span></span>|<span data-ttu-id="8f4ac-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-131">Optional attribute.</span></span> <span data-ttu-id="8f4ac-132">Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="8f4ac-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="8f4ac-133">Serialization</span></span>|<span data-ttu-id="8f4ac-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-134">Optional attribute.</span></span> <span data-ttu-id="8f4ac-135">Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="8f4ac-136">Interop</span><span class="sxs-lookup"><span data-stu-id="8f4ac-136">Interop</span></span>|<span data-ttu-id="8f4ac-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-137">Optional attribute.</span></span> <span data-ttu-id="8f4ac-138">Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="8f4ac-139">Interop</span><span class="sxs-lookup"><span data-stu-id="8f4ac-139">Interop</span></span>|<span data-ttu-id="8f4ac-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-140">Optional attribute.</span></span> <span data-ttu-id="8f4ac-141">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="8f4ac-142">Interop</span><span class="sxs-lookup"><span data-stu-id="8f4ac-142">Interop</span></span>|<span data-ttu-id="8f4ac-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-143">Optional attribute.</span></span> <span data-ttu-id="8f4ac-144">Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="8f4ac-145">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="8f4ac-145">Name attribute</span></span>  
  
|<span data-ttu-id="8f4ac-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="8f4ac-146">Value</span></span>|<span data-ttu-id="8f4ac-147">Opis</span><span class="sxs-lookup"><span data-stu-id="8f4ac-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f4ac-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="8f4ac-148">*parameter_name*</span></span>|<span data-ttu-id="8f4ac-149">Nazwa parametru typu <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="8f4ac-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="8f4ac-150">Na przykład dla sygnatury metody `Type.GetInterfaceMap(Type interfaceType)` wartość `Name` atrybutu to "InterfaceType".</span><span class="sxs-lookup"><span data-stu-id="8f4ac-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="8f4ac-151">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="8f4ac-151">All other attributes</span></span>  
  
|<span data-ttu-id="8f4ac-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="8f4ac-152">Value</span></span>|<span data-ttu-id="8f4ac-153">Opis</span><span class="sxs-lookup"><span data-stu-id="8f4ac-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f4ac-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="8f4ac-154">*policy_setting*</span></span>|<span data-ttu-id="8f4ac-155">Ustawienie, które ma zostać zastosowane do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="8f4ac-156">Możliwe wartości to `All` , `Public` , `PublicAndInternal` , `Required Public` , `Required PublicAndInternal` i `Required All` .</span><span class="sxs-lookup"><span data-stu-id="8f4ac-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="8f4ac-157">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8f4ac-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f4ac-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8f4ac-158">Child Elements</span></span>  
 <span data-ttu-id="8f4ac-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f4ac-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8f4ac-160">Parent Elements</span></span>  
  
|<span data-ttu-id="8f4ac-161">Element</span><span class="sxs-lookup"><span data-stu-id="8f4ac-161">Element</span></span>|<span data-ttu-id="8f4ac-162">Opis</span><span class="sxs-lookup"><span data-stu-id="8f4ac-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="8f4ac-163">Stosuje zasady odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-163">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f4ac-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f4ac-164">Remarks</span></span>  
 <span data-ttu-id="8f4ac-165">`<TypeParameter>`Element jest podobny do [\<Parameter>](parameter-element-net-native.md) elementu, z tą różnicą, że może być stosowany tylko do parametrów typu <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="8f4ac-165">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="8f4ac-166">Stosuje zasady do dowolnego typu reprezentowanego w czasie wykonywania przez argument typu określony przez `Name` atrybut.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-166">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="8f4ac-167">Na przykład serializator JSON NewtonSoft zawiera metodę statyczną `JsonConvert.DeserializeObject(String value, Type type)` .</span><span class="sxs-lookup"><span data-stu-id="8f4ac-167">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="8f4ac-168">Następujące dyrektywy odbicia:</span><span class="sxs-lookup"><span data-stu-id="8f4ac-168">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="8f4ac-169">Określ, że metadane dla typu środowiska uruchomieniowego reprezentowane przez `type` argument powinny zostać udostępnione do serializacji.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-169">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="8f4ac-170">Jeśli te dyrektywy środowiska uruchomieniowego dotyczą projektu, który zawiera następujący kod źródłowy:</span><span class="sxs-lookup"><span data-stu-id="8f4ac-170">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="8f4ac-171">dyrektywy odbicia tworzą metadane dla `StockQuote` typu dostępnego dla serializatora JSON Newtonsoft w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8f4ac-171">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f4ac-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f4ac-172">See also</span></span>

- [<span data-ttu-id="8f4ac-173">\<Method>Postaci</span><span class="sxs-lookup"><span data-stu-id="8f4ac-173">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="8f4ac-174">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="8f4ac-174">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8f4ac-175">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8f4ac-175">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="8f4ac-176">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8f4ac-176">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
