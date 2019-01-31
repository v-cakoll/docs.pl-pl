---
title: <GenericParameter> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db9876727244d528ec3b7f1c3c9875bb5ca645b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257775"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="67f3f-102">\<GenericParameter> Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="67f3f-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="67f3f-103">Stosuje zasady do typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="67f3f-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67f3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67f3f-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67f3f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="67f3f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="67f3f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="67f3f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67f3f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="67f3f-107">Attributes</span></span>  
  
|<span data-ttu-id="67f3f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="67f3f-108">Attribute</span></span>|<span data-ttu-id="67f3f-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="67f3f-109">Attribute type</span></span>|<span data-ttu-id="67f3f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="67f3f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="67f3f-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="67f3f-111">General</span></span>|<span data-ttu-id="67f3f-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="67f3f-112">Required attribute.</span></span> <span data-ttu-id="67f3f-113">Nazwa parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="67f3f-113">The name of the generic parameter.</span></span> <span data-ttu-id="67f3f-114">Na przykład Delegat ogólny <xref:System.Func%603>, wartość `Name` atrybut to "TResult" Aby zastosować zasadę środowiska uruchomieniowego do wartości zwracanej delegata.</span><span class="sxs-lookup"><span data-stu-id="67f3f-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="67f3f-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="67f3f-115">Reflection</span></span>|<span data-ttu-id="67f3f-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-116">Optional attribute.</span></span> <span data-ttu-id="67f3f-117">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="67f3f-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="67f3f-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="67f3f-118">Reflection</span></span>|<span data-ttu-id="67f3f-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-119">Optional attribute.</span></span> <span data-ttu-id="67f3f-120">Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="67f3f-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="67f3f-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="67f3f-121">Reflection</span></span>|<span data-ttu-id="67f3f-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-122">Optional attribute.</span></span> <span data-ttu-id="67f3f-123">Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="67f3f-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="67f3f-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="67f3f-124">Serialization</span></span>|<span data-ttu-id="67f3f-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-125">Optional attribute.</span></span> <span data-ttu-id="67f3f-126">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="67f3f-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="67f3f-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="67f3f-127">Serialization</span></span>|<span data-ttu-id="67f3f-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-128">Optional attribute.</span></span> <span data-ttu-id="67f3f-129">Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="67f3f-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="67f3f-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="67f3f-130">Serialization</span></span>|<span data-ttu-id="67f3f-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-131">Optional attribute.</span></span> <span data-ttu-id="67f3f-132">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="67f3f-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="67f3f-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="67f3f-133">Serialization</span></span>|<span data-ttu-id="67f3f-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-134">Optional attribute.</span></span> <span data-ttu-id="67f3f-135">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="67f3f-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="67f3f-136">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="67f3f-136">Interop</span></span>|<span data-ttu-id="67f3f-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-137">Optional attribute.</span></span> <span data-ttu-id="67f3f-138">Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="67f3f-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="67f3f-139">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="67f3f-139">Interop</span></span>|<span data-ttu-id="67f3f-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-140">Optional attribute.</span></span> <span data-ttu-id="67f3f-141">Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="67f3f-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="67f3f-142">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="67f3f-142">Interop</span></span>|<span data-ttu-id="67f3f-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67f3f-143">Optional attribute.</span></span> <span data-ttu-id="67f3f-144">Określa zasady dla marshaling typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="67f3f-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="67f3f-145">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="67f3f-145">Name attribute</span></span>  
  
|<span data-ttu-id="67f3f-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="67f3f-146">Value</span></span>|<span data-ttu-id="67f3f-147">Opis</span><span class="sxs-lookup"><span data-stu-id="67f3f-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="67f3f-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="67f3f-148">*generic_parameter_name*</span></span>|<span data-ttu-id="67f3f-149">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="67f3f-149">Required attribute.</span></span> <span data-ttu-id="67f3f-150">Nazwa parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="67f3f-150">The name of the generic type parameter.</span></span> <span data-ttu-id="67f3f-151">Na przykład Delegat ogólny <xref:System.Func%603>, *generic_parameter_name* wartość "TResult" dotyczy wartości zwracanej pełnomocnika zasad wykonywania.</span><span class="sxs-lookup"><span data-stu-id="67f3f-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="67f3f-152">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="67f3f-152">All other attributes</span></span>  
  
|<span data-ttu-id="67f3f-153">Wartość</span><span class="sxs-lookup"><span data-stu-id="67f3f-153">Value</span></span>|<span data-ttu-id="67f3f-154">Opis</span><span class="sxs-lookup"><span data-stu-id="67f3f-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="67f3f-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="67f3f-155">*policy_setting*</span></span>|<span data-ttu-id="67f3f-156">Ustawienia do zastosowania do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="67f3f-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="67f3f-157">Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="67f3f-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="67f3f-158">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="67f3f-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67f3f-159">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="67f3f-159">Child Elements</span></span>  
 <span data-ttu-id="67f3f-160">Brak.</span><span class="sxs-lookup"><span data-stu-id="67f3f-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67f3f-161">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="67f3f-161">Parent Elements</span></span>  
  
|<span data-ttu-id="67f3f-162">Element</span><span class="sxs-lookup"><span data-stu-id="67f3f-162">Element</span></span>|<span data-ttu-id="67f3f-163">Opis</span><span class="sxs-lookup"><span data-stu-id="67f3f-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67f3f-164">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="67f3f-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="67f3f-165">Ma zastosowanie zasad odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="67f3f-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="67f3f-166">\<Type></span><span class="sxs-lookup"><span data-stu-id="67f3f-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="67f3f-167">Ma zastosowanie zasad odbicia środowiska uruchomieniowego do określonego typu, takie jak klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="67f3f-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67f3f-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67f3f-168">Remarks</span></span>  
 <span data-ttu-id="67f3f-169">`<GenericParameter>` Element jest elementem podrzędnym jednej [ \<metody >](../../../docs/framework/net-native/method-element-net-native.md) lub [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu i jest używana do stosowania zasad do parametru określonego typu ogólnego, który jest określony przez jego nazwę w podpisie ogólnego typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="67f3f-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="67f3f-170">`<GenericParameter>` Element jest najbardziej użyteczna, gdy serializatory.</span><span class="sxs-lookup"><span data-stu-id="67f3f-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="67f3f-171">W poniższym przykładzie użyto `<GenericParameter>` element, aby zastosować zasady do typu `T` w wywołaniach serializator NewtonSoft JSON [JsonConvert.DeserializeObject\<T > (ciąg)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="67f3f-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="67f3f-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67f3f-172">See also</span></span>
- [<span data-ttu-id="67f3f-173">\<Metoda > Element</span><span class="sxs-lookup"><span data-stu-id="67f3f-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="67f3f-174">\<Typ > Element</span><span class="sxs-lookup"><span data-stu-id="67f3f-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="67f3f-175">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="67f3f-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="67f3f-176">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="67f3f-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="67f3f-177">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="67f3f-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
