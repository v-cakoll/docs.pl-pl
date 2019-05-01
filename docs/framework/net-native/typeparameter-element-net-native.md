---
title: <TypeParameter> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b03c87c70fa1bfcd331f468d369632f4164300bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982465"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="40739-102">\<TypeParameter > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="40739-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="40739-103">Stosuje zasady na typ reprezentowany przez argument typu przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="40739-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40739-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40739-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40739-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="40739-105">Attributes and Elements</span></span>  
 <span data-ttu-id="40739-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="40739-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40739-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="40739-107">Attributes</span></span>  
  
|<span data-ttu-id="40739-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="40739-108">Attribute</span></span>|<span data-ttu-id="40739-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="40739-109">Attribute type</span></span>|<span data-ttu-id="40739-110">Opis</span><span class="sxs-lookup"><span data-stu-id="40739-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="40739-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="40739-111">General</span></span>|<span data-ttu-id="40739-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="40739-112">Required attribute.</span></span> <span data-ttu-id="40739-113">Nazwa parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="40739-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="40739-114">Na przykład dla sygnatury metody `Type.GetInterfaceMap(Type interfaceType)`, wartość `Name` atrybut jest "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="40739-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="40739-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="40739-115">Reflection</span></span>|<span data-ttu-id="40739-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-116">Optional attribute.</span></span> <span data-ttu-id="40739-117">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="40739-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="40739-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="40739-118">Reflection</span></span>|<span data-ttu-id="40739-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-119">Optional attribute.</span></span> <span data-ttu-id="40739-120">Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="40739-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="40739-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="40739-121">Reflection</span></span>|<span data-ttu-id="40739-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-122">Optional attribute.</span></span> <span data-ttu-id="40739-123">Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="40739-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="40739-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="40739-124">Serialization</span></span>|<span data-ttu-id="40739-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-125">Optional attribute.</span></span> <span data-ttu-id="40739-126">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="40739-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="40739-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="40739-127">Serialization</span></span>|<span data-ttu-id="40739-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-128">Optional attribute.</span></span> <span data-ttu-id="40739-129">Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="40739-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="40739-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="40739-130">Serialization</span></span>|<span data-ttu-id="40739-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-131">Optional attribute.</span></span> <span data-ttu-id="40739-132">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="40739-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="40739-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="40739-133">Serialization</span></span>|<span data-ttu-id="40739-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-134">Optional attribute.</span></span> <span data-ttu-id="40739-135">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="40739-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="40739-136">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="40739-136">Interop</span></span>|<span data-ttu-id="40739-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-137">Optional attribute.</span></span> <span data-ttu-id="40739-138">Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="40739-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="40739-139">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="40739-139">Interop</span></span>|<span data-ttu-id="40739-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-140">Optional attribute.</span></span> <span data-ttu-id="40739-141">Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="40739-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="40739-142">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="40739-142">Interop</span></span>|<span data-ttu-id="40739-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40739-143">Optional attribute.</span></span> <span data-ttu-id="40739-144">Określa zasady dla marshaling typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="40739-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="40739-145">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="40739-145">Name attribute</span></span>  
  
|<span data-ttu-id="40739-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="40739-146">Value</span></span>|<span data-ttu-id="40739-147">Opis</span><span class="sxs-lookup"><span data-stu-id="40739-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40739-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="40739-148">*parameter_name*</span></span>|<span data-ttu-id="40739-149">Nazwa parametru typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="40739-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="40739-150">Na przykład dla sygnatury metody `Type.GetInterfaceMap(Type interfaceType)`, wartość `Name` atrybut jest "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="40739-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="40739-151">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="40739-151">All other attributes</span></span>  
  
|<span data-ttu-id="40739-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="40739-152">Value</span></span>|<span data-ttu-id="40739-153">Opis</span><span class="sxs-lookup"><span data-stu-id="40739-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40739-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="40739-154">*policy_setting*</span></span>|<span data-ttu-id="40739-155">Ustawienia do zastosowania do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="40739-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="40739-156">Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="40739-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="40739-157">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="40739-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40739-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="40739-158">Child Elements</span></span>  
 <span data-ttu-id="40739-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="40739-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40739-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="40739-160">Parent Elements</span></span>  
  
|<span data-ttu-id="40739-161">Element</span><span class="sxs-lookup"><span data-stu-id="40739-161">Element</span></span>|<span data-ttu-id="40739-162">Opis</span><span class="sxs-lookup"><span data-stu-id="40739-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40739-163">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="40739-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="40739-164">Ma zastosowanie zasad odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="40739-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40739-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40739-165">Remarks</span></span>  
 <span data-ttu-id="40739-166">`<TypeParameter>` Element jest podobny do [ \<parametr >](../../../docs/framework/net-native/parameter-element-net-native.md) elementu, z wyjątkiem, że można zastosować tylko do parametrów typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="40739-166">The `<TypeParameter>` element is similar to the [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="40739-167">Ma zastosowanie zasad do jakiegokolwiek rodzaju jest reprezentowany w czasie wykonywania przez argument typu określonego przez `Name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="40739-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="40739-168">Na przykład serializator NewtonSoft JSON obejmuje statyczne `JsonConvert.DeserializeObject(String value, Type type)` metody.</span><span class="sxs-lookup"><span data-stu-id="40739-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="40739-169">Następujące dyrektywy odbicia:</span><span class="sxs-lookup"><span data-stu-id="40739-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="40739-170">Określ tych metadanych dla typu środowiska uruchomieniowego, reprezentowane przez `type` argument powinny być udostępnione do serializacji.</span><span class="sxs-lookup"><span data-stu-id="40739-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="40739-171">Jeśli te dyrektywy środowiska uruchomieniowego stosują się do projektu, który zawiera następujący kod źródłowy:</span><span class="sxs-lookup"><span data-stu-id="40739-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="40739-172">dyrektywy odbicia, że metadane dla `StockQuote` typu dostępne dla serializator NewtonSoft JSON w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40739-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40739-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40739-173">See also</span></span>

- [<span data-ttu-id="40739-174">\<Metoda > Element</span><span class="sxs-lookup"><span data-stu-id="40739-174">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="40739-175">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="40739-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="40739-176">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="40739-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="40739-177">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="40739-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
