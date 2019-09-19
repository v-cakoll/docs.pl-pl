---
title: <GenericParameter>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2898d804f7a351045b2fbce42042f9fd322ebb0a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049746"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="78086-102">\<GenericParameter, element > (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="78086-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="78086-103">Stosuje zasady do typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="78086-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78086-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78086-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78086-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="78086-105">Attributes and Elements</span></span>  
 <span data-ttu-id="78086-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="78086-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78086-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="78086-107">Attributes</span></span>  
  
|<span data-ttu-id="78086-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="78086-108">Attribute</span></span>|<span data-ttu-id="78086-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="78086-109">Attribute type</span></span>|<span data-ttu-id="78086-110">Opis</span><span class="sxs-lookup"><span data-stu-id="78086-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="78086-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="78086-111">General</span></span>|<span data-ttu-id="78086-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="78086-112">Required attribute.</span></span> <span data-ttu-id="78086-113">Nazwa parametru generycznego.</span><span class="sxs-lookup"><span data-stu-id="78086-113">The name of the generic parameter.</span></span> <span data-ttu-id="78086-114">Na przykład dla delegata <xref:System.Func%603>ogólnego wartość `Name` atrybutu jest "TResult", aby zastosować zasady środowiska uruchomieniowego do wartości zwracanej przez delegata.</span><span class="sxs-lookup"><span data-stu-id="78086-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="78086-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="78086-115">Reflection</span></span>|<span data-ttu-id="78086-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-116">Optional attribute.</span></span> <span data-ttu-id="78086-117">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="78086-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="78086-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="78086-118">Reflection</span></span>|<span data-ttu-id="78086-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-119">Optional attribute.</span></span> <span data-ttu-id="78086-120">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="78086-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="78086-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="78086-121">Reflection</span></span>|<span data-ttu-id="78086-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-122">Optional attribute.</span></span> <span data-ttu-id="78086-123">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="78086-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="78086-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="78086-124">Serialization</span></span>|<span data-ttu-id="78086-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-125">Optional attribute.</span></span> <span data-ttu-id="78086-126">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="78086-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="78086-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="78086-127">Serialization</span></span>|<span data-ttu-id="78086-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-128">Optional attribute.</span></span> <span data-ttu-id="78086-129">Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="78086-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="78086-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="78086-130">Serialization</span></span>|<span data-ttu-id="78086-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-131">Optional attribute.</span></span> <span data-ttu-id="78086-132">Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="78086-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="78086-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="78086-133">Serialization</span></span>|<span data-ttu-id="78086-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-134">Optional attribute.</span></span> <span data-ttu-id="78086-135">Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="78086-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="78086-136">Interop</span><span class="sxs-lookup"><span data-stu-id="78086-136">Interop</span></span>|<span data-ttu-id="78086-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-137">Optional attribute.</span></span> <span data-ttu-id="78086-138">Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.</span><span class="sxs-lookup"><span data-stu-id="78086-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="78086-139">Interop</span><span class="sxs-lookup"><span data-stu-id="78086-139">Interop</span></span>|<span data-ttu-id="78086-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-140">Optional attribute.</span></span> <span data-ttu-id="78086-141">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="78086-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="78086-142">Interop</span><span class="sxs-lookup"><span data-stu-id="78086-142">Interop</span></span>|<span data-ttu-id="78086-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78086-143">Optional attribute.</span></span> <span data-ttu-id="78086-144">Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="78086-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="78086-145">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="78086-145">Name attribute</span></span>  
  
|<span data-ttu-id="78086-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="78086-146">Value</span></span>|<span data-ttu-id="78086-147">Opis</span><span class="sxs-lookup"><span data-stu-id="78086-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="78086-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="78086-148">*generic_parameter_name*</span></span>|<span data-ttu-id="78086-149">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="78086-149">Required attribute.</span></span> <span data-ttu-id="78086-150">Nazwa parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="78086-150">The name of the generic type parameter.</span></span> <span data-ttu-id="78086-151">Na przykład dla delegata <xref:System.Func%603>generycznego wartość *generic_parameter_name* "TResult" stosuje zasady środowiska uruchomieniowego do wartości zwracanej przez delegata.</span><span class="sxs-lookup"><span data-stu-id="78086-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="78086-152">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="78086-152">All other attributes</span></span>  
  
|<span data-ttu-id="78086-153">Wartość</span><span class="sxs-lookup"><span data-stu-id="78086-153">Value</span></span>|<span data-ttu-id="78086-154">Opis</span><span class="sxs-lookup"><span data-stu-id="78086-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="78086-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="78086-155">*policy_setting*</span></span>|<span data-ttu-id="78086-156">Ustawienie, które ma zostać zastosowane do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="78086-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="78086-157">Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public` ,i`Required All`. `Required PublicAndInternal`</span><span class="sxs-lookup"><span data-stu-id="78086-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="78086-158">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="78086-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78086-159">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="78086-159">Child Elements</span></span>  
 <span data-ttu-id="78086-160">Brak.</span><span class="sxs-lookup"><span data-stu-id="78086-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78086-161">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="78086-161">Parent Elements</span></span>  
  
|<span data-ttu-id="78086-162">Element</span><span class="sxs-lookup"><span data-stu-id="78086-162">Element</span></span>|<span data-ttu-id="78086-163">Opis</span><span class="sxs-lookup"><span data-stu-id="78086-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78086-164">\<> Metody</span><span class="sxs-lookup"><span data-stu-id="78086-164">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="78086-165">Stosuje zasady odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="78086-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="78086-166">\<Type></span><span class="sxs-lookup"><span data-stu-id="78086-166">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="78086-167">Stosuje zasady odbicia środowiska uruchomieniowego do określonego typu, takiego jak Klasa lub struktura.</span><span class="sxs-lookup"><span data-stu-id="78086-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78086-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78086-168">Remarks</span></span>  
 <span data-ttu-id="78086-169">Element jest elementem podrzędnym [ \<metody >](method-element-net-native.md) lub [ \<typu >](type-element-net-native.md) elementu i służy do stosowania zasad do określonego parametru typu ogólnego, który jest określony przez jego nazwę w typie ogólnym lub metodzie. `<GenericParameter>` podpisane.</span><span class="sxs-lookup"><span data-stu-id="78086-169">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="78086-170">Element `<GenericParameter>` jest najbardziej przydatny, gdy jest używany z serializatorami.</span><span class="sxs-lookup"><span data-stu-id="78086-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="78086-171">Poniższy przykład używa elementu, `<GenericParameter>` aby zastosować zasady do typu `T` w wywołaniach Newtonsoft [JsonConvert. deserializacjiobject\<T > (String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="78086-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78086-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78086-172">See also</span></span>

- [<span data-ttu-id="78086-173">\<Element > metody</span><span class="sxs-lookup"><span data-stu-id="78086-173">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="78086-174">\<Typ > element</span><span class="sxs-lookup"><span data-stu-id="78086-174">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="78086-175">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="78086-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="78086-176">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="78086-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="78086-177">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="78086-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
