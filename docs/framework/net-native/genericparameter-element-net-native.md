---
title: Element &lt;GenericParameter&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 601118d2dcc42f9e35da0e24c782b218efd7a025
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltgenericparametergt-element-net-native"></a><span data-ttu-id="0b4be-102">Element &lt;GenericParameter&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="0b4be-102">&lt;GenericParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="0b4be-103">Stosuje zasady do typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="0b4be-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b4be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b4be-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type" />  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b4be-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0b4be-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0b4be-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0b4be-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b4be-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0b4be-107">Attributes</span></span>  
  
|<span data-ttu-id="0b4be-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0b4be-108">Attribute</span></span>|<span data-ttu-id="0b4be-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="0b4be-109">Attribute type</span></span>|<span data-ttu-id="0b4be-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0b4be-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0b4be-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="0b4be-111">General</span></span>|<span data-ttu-id="0b4be-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0b4be-112">Required attribute.</span></span> <span data-ttu-id="0b4be-113">Nazwa parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="0b4be-113">The name of the generic parameter.</span></span> <span data-ttu-id="0b4be-114">Na przykład w przypadku Delegat ogólny <xref:System.Func%603>, wartość `Name` atrybutu jest "TResult" do stosowania zasad środowiska uruchomieniowego dla wartości zwracanej delegata.</span><span class="sxs-lookup"><span data-stu-id="0b4be-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="0b4be-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="0b4be-115">Reflection</span></span>|<span data-ttu-id="0b4be-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-116">Optional attribute.</span></span> <span data-ttu-id="0b4be-117">Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0b4be-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="0b4be-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="0b4be-118">Reflection</span></span>|<span data-ttu-id="0b4be-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-119">Optional attribute.</span></span> <span data-ttu-id="0b4be-120">Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="0b4be-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="0b4be-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="0b4be-121">Reflection</span></span>|<span data-ttu-id="0b4be-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-122">Optional attribute.</span></span> <span data-ttu-id="0b4be-123">Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="0b4be-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="0b4be-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="0b4be-124">Serialization</span></span>|<span data-ttu-id="0b4be-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-125">Optional attribute.</span></span> <span data-ttu-id="0b4be-126">Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="0b4be-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="0b4be-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="0b4be-127">Serialization</span></span>|<span data-ttu-id="0b4be-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-128">Optional attribute.</span></span> <span data-ttu-id="0b4be-129">Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b4be-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="0b4be-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="0b4be-130">Serialization</span></span>|<span data-ttu-id="0b4be-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-131">Optional attribute.</span></span> <span data-ttu-id="0b4be-132">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b4be-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="0b4be-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="0b4be-133">Serialization</span></span>|<span data-ttu-id="0b4be-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-134">Optional attribute.</span></span> <span data-ttu-id="0b4be-135">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b4be-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="0b4be-136">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="0b4be-136">Interop</span></span>|<span data-ttu-id="0b4be-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-137">Optional attribute.</span></span> <span data-ttu-id="0b4be-138">Zasady kontroli przekazywanie typów referencyjnych do środowiska wykonawczego systemu Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0b4be-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="0b4be-139">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="0b4be-139">Interop</span></span>|<span data-ttu-id="0b4be-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-140">Optional attribute.</span></span> <span data-ttu-id="0b4be-141">Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="0b4be-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="0b4be-142">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="0b4be-142">Interop</span></span>|<span data-ttu-id="0b4be-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0b4be-143">Optional attribute.</span></span> <span data-ttu-id="0b4be-144">Określa zasady dla przekazywanie typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="0b4be-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0b4be-145">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="0b4be-145">Name attribute</span></span>  
  
|<span data-ttu-id="0b4be-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="0b4be-146">Value</span></span>|<span data-ttu-id="0b4be-147">Opis</span><span class="sxs-lookup"><span data-stu-id="0b4be-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0b4be-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="0b4be-148">*generic_parameter_name*</span></span>|<span data-ttu-id="0b4be-149">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0b4be-149">Required attribute.</span></span> <span data-ttu-id="0b4be-150">Nazwa parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="0b4be-150">The name of the generic type parameter.</span></span> <span data-ttu-id="0b4be-151">Na przykład w przypadku Delegat ogólny <xref:System.Func%603>, *generic_parameter_name* wartość "TResult" dotyczy delegata zwracana wartość zasad wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0b4be-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0b4be-152">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="0b4be-152">All other attributes</span></span>  
  
|<span data-ttu-id="0b4be-153">Wartość</span><span class="sxs-lookup"><span data-stu-id="0b4be-153">Value</span></span>|<span data-ttu-id="0b4be-154">Opis</span><span class="sxs-lookup"><span data-stu-id="0b4be-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0b4be-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0b4be-155">*policy_setting*</span></span>|<span data-ttu-id="0b4be-156">Ustawienia do zastosowania dla tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="0b4be-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="0b4be-157">Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="0b4be-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="0b4be-158">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0b4be-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b4be-159">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0b4be-159">Child Elements</span></span>  
 <span data-ttu-id="0b4be-160">Brak.</span><span class="sxs-lookup"><span data-stu-id="0b4be-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b4be-161">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0b4be-161">Parent Elements</span></span>  
  
|<span data-ttu-id="0b4be-162">Element</span><span class="sxs-lookup"><span data-stu-id="0b4be-162">Element</span></span>|<span data-ttu-id="0b4be-163">Opis</span><span class="sxs-lookup"><span data-stu-id="0b4be-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b4be-164">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="0b4be-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="0b4be-165">Zastosowanie zasad wykonywania odbicia do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="0b4be-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="0b4be-166">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="0b4be-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="0b4be-167">Zastosowanie zasad wykonywania odbicia do określonego typu, takich jak klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0b4be-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b4be-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b4be-168">Remarks</span></span>  
 <span data-ttu-id="0b4be-169">`<GenericParameter>` Element jest elementem podrzędnym albo [ \<metody >](../../../docs/framework/net-native/method-element-net-native.md) lub [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) element i jest używana do stosowania zasad do parametru określonego typu ogólnego, który jest określony przez jego nazwę w ogólnym typie lub metodzie sygnaturze.</span><span class="sxs-lookup"><span data-stu-id="0b4be-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="0b4be-170">`<GenericParameter>` Element jest najbardziej przydatna, gdy jest używany z serializatorów.</span><span class="sxs-lookup"><span data-stu-id="0b4be-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="0b4be-171">W poniższym przykładzie użyto `<GenericParameter>` elementu, aby zastosować zasady do typu `T` w wywołaniach serializator NewtonSoft JSON [JsonConvert.DeserializeObject\<T > (ciąg)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="0b4be-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b4be-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b4be-172">See Also</span></span>  
 [<span data-ttu-id="0b4be-173">\<Metoda > — Element</span><span class="sxs-lookup"><span data-stu-id="0b4be-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="0b4be-174">\<Typ > — Element</span><span class="sxs-lookup"><span data-stu-id="0b4be-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="0b4be-175">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0b4be-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="0b4be-176">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0b4be-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="0b4be-177">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0b4be-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
