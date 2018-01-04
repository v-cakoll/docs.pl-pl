---
title: Element &lt;TypeParameter&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee88d7692abb1f640b6e50d845691adf8938f841
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lttypeparametergt-element-net-native"></a><span data-ttu-id="13366-102">Element &lt;TypeParameter&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="13366-102">&lt;TypeParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="13366-103">Stosuje zasady do typu reprezentowanego przez argument typu przekazana do metody.</span><span class="sxs-lookup"><span data-stu-id="13366-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13366-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13366-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13366-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="13366-105">Attributes and Elements</span></span>  
 <span data-ttu-id="13366-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="13366-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13366-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="13366-107">Attributes</span></span>  
  
|<span data-ttu-id="13366-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="13366-108">Attribute</span></span>|<span data-ttu-id="13366-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="13366-109">Attribute type</span></span>|<span data-ttu-id="13366-110">Opis</span><span class="sxs-lookup"><span data-stu-id="13366-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="13366-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="13366-111">General</span></span>|<span data-ttu-id="13366-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="13366-112">Required attribute.</span></span> <span data-ttu-id="13366-113">Nazwa parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="13366-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="13366-114">Na przykład w podpisie metody `Type.GetInterfaceMap(Type interfaceType)`, wartość `Name` atrybutu jest "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="13366-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="13366-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="13366-115">Reflection</span></span>|<span data-ttu-id="13366-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-116">Optional attribute.</span></span> <span data-ttu-id="13366-117">Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="13366-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="13366-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="13366-118">Reflection</span></span>|<span data-ttu-id="13366-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-119">Optional attribute.</span></span> <span data-ttu-id="13366-120">Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="13366-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="13366-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="13366-121">Reflection</span></span>|<span data-ttu-id="13366-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-122">Optional attribute.</span></span> <span data-ttu-id="13366-123">Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="13366-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="13366-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="13366-124">Serialization</span></span>|<span data-ttu-id="13366-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-125">Optional attribute.</span></span> <span data-ttu-id="13366-126">Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="13366-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="13366-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="13366-127">Serialization</span></span>|<span data-ttu-id="13366-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-128">Optional attribute.</span></span> <span data-ttu-id="13366-129">Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="13366-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="13366-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="13366-130">Serialization</span></span>|<span data-ttu-id="13366-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-131">Optional attribute.</span></span> <span data-ttu-id="13366-132">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="13366-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="13366-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="13366-133">Serialization</span></span>|<span data-ttu-id="13366-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-134">Optional attribute.</span></span> <span data-ttu-id="13366-135">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="13366-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="13366-136">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="13366-136">Interop</span></span>|<span data-ttu-id="13366-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-137">Optional attribute.</span></span> <span data-ttu-id="13366-138">Zasady kontroli przekazywanie typów referencyjnych do środowiska wykonawczego systemu Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="13366-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="13366-139">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="13366-139">Interop</span></span>|<span data-ttu-id="13366-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-140">Optional attribute.</span></span> <span data-ttu-id="13366-141">Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="13366-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="13366-142">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="13366-142">Interop</span></span>|<span data-ttu-id="13366-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13366-143">Optional attribute.</span></span> <span data-ttu-id="13366-144">Określa zasady dla przekazywanie typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="13366-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="13366-145">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="13366-145">Name attribute</span></span>  
  
|<span data-ttu-id="13366-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="13366-146">Value</span></span>|<span data-ttu-id="13366-147">Opis</span><span class="sxs-lookup"><span data-stu-id="13366-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13366-148">*nazwa_parametru*</span><span class="sxs-lookup"><span data-stu-id="13366-148">*parameter_name*</span></span>|<span data-ttu-id="13366-149">Nazwa parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="13366-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="13366-150">Na przykład w podpisie metody `Type.GetInterfaceMap(Type interfaceType)`, wartość `Name` atrybutu jest "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="13366-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="13366-151">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="13366-151">All other attributes</span></span>  
  
|<span data-ttu-id="13366-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="13366-152">Value</span></span>|<span data-ttu-id="13366-153">Opis</span><span class="sxs-lookup"><span data-stu-id="13366-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13366-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="13366-154">*policy_setting*</span></span>|<span data-ttu-id="13366-155">Ustawienia do zastosowania dla tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="13366-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="13366-156">Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="13366-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="13366-157">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="13366-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13366-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="13366-158">Child Elements</span></span>  
 <span data-ttu-id="13366-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="13366-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13366-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="13366-160">Parent Elements</span></span>  
  
|<span data-ttu-id="13366-161">Element</span><span class="sxs-lookup"><span data-stu-id="13366-161">Element</span></span>|<span data-ttu-id="13366-162">Opis</span><span class="sxs-lookup"><span data-stu-id="13366-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13366-163">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="13366-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="13366-164">Zastosowanie zasad wykonywania odbicia do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="13366-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13366-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13366-165">Remarks</span></span>  
 <span data-ttu-id="13366-166">`<TypeParameter>` Element jest podobny do [ \<parametru >](../../../docs/framework/net-native/parameter-element-net-native.md) element, z wyjątkiem, że mogą być stosowane tylko do parametrów typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="13366-166">The `<TypeParameter>` element is similar to the [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="13366-167">Ma zastosowanie zasad do jakiegokolwiek rodzaju jest reprezentowana w czasie wykonywania przez określony przez argument typu `Name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="13366-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="13366-168">Na przykład serializator NewtonSoft JSON zawiera statycznego `JsonConvert.DeserializeObject(String value, Type type)` metody.</span><span class="sxs-lookup"><span data-stu-id="13366-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="13366-169">Następujące dyrektywy odbicia:</span><span class="sxs-lookup"><span data-stu-id="13366-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="13366-170">Określ tych metadanych dla typu środowiska uruchomieniowego reprezentowany przez `type` argument powinna zostać udostępniona do serializacji.</span><span class="sxs-lookup"><span data-stu-id="13366-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="13366-171">Jeśli te dyrektyw środowiska uruchomieniowego stosuje się do projektu, który zawiera następujący kod źródłowy:</span><span class="sxs-lookup"><span data-stu-id="13366-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="13366-172">dyrektywy odbicia udostępnić metadanych dla `StockQuote` typu dostępne dla serializator NewtonSoft JSON w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="13366-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13366-173">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13366-173">See Also</span></span>  
 [<span data-ttu-id="13366-174">\<Metoda > — Element</span><span class="sxs-lookup"><span data-stu-id="13366-174">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="13366-175">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="13366-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="13366-176">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="13366-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="13366-177">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="13366-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
