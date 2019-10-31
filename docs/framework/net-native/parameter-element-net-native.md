---
title: Element <Parameter> (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: c6dfc347d44a794ee8496c45ca879f9daab12b22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128197"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="3ed30-102">\<> parametru elementu (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="3ed30-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="3ed30-103">Stosuje zasady odbicia do typu argumentu przesłanego do metody.</span><span class="sxs-lookup"><span data-stu-id="3ed30-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ed30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ed30-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ed30-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ed30-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3ed30-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3ed30-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ed30-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ed30-107">Attributes</span></span>  
  
|<span data-ttu-id="3ed30-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3ed30-108">Attribute</span></span>|<span data-ttu-id="3ed30-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="3ed30-109">Attribute type</span></span>|<span data-ttu-id="3ed30-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3ed30-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="3ed30-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="3ed30-111">General</span></span>|<span data-ttu-id="3ed30-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3ed30-112">Required attribute.</span></span> <span data-ttu-id="3ed30-113">Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="3ed30-113">The parameter name.</span></span> <span data-ttu-id="3ed30-114">Na przykład w przypadku `String.CompareTo(Object value)`sygnatury metody wartość atrybutu `Name` ma wartość "value".</span><span class="sxs-lookup"><span data-stu-id="3ed30-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="3ed30-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="3ed30-115">Reflection</span></span>|<span data-ttu-id="3ed30-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-116">Optional attribute.</span></span> <span data-ttu-id="3ed30-117">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="3ed30-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="3ed30-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="3ed30-118">Reflection</span></span>|<span data-ttu-id="3ed30-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-119">Optional attribute.</span></span> <span data-ttu-id="3ed30-120">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3ed30-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="3ed30-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="3ed30-121">Reflection</span></span>|<span data-ttu-id="3ed30-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-122">Optional attribute.</span></span> <span data-ttu-id="3ed30-123">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="3ed30-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="3ed30-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="3ed30-124">Serialization</span></span>|<span data-ttu-id="3ed30-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-125">Optional attribute.</span></span> <span data-ttu-id="3ed30-126">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="3ed30-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="3ed30-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="3ed30-127">Serialization</span></span>|<span data-ttu-id="3ed30-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-128">Optional attribute.</span></span> <span data-ttu-id="3ed30-129">Kontroluje zasady dla serializacji korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ed30-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="3ed30-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="3ed30-130">Serialization</span></span>|<span data-ttu-id="3ed30-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-131">Optional attribute.</span></span> <span data-ttu-id="3ed30-132">Kontroluje zasady dla serializacji JSON korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ed30-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="3ed30-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="3ed30-133">Serialization</span></span>|<span data-ttu-id="3ed30-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-134">Optional attribute.</span></span> <span data-ttu-id="3ed30-135">Kontroluje zasady dla serializacji XML, która używa klasy <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ed30-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="3ed30-136">Interop</span><span class="sxs-lookup"><span data-stu-id="3ed30-136">Interop</span></span>|<span data-ttu-id="3ed30-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-137">Optional attribute.</span></span> <span data-ttu-id="3ed30-138">Kontroluje zasady dotyczące organizowania typów odwołań do WinRT i COM.</span><span class="sxs-lookup"><span data-stu-id="3ed30-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="3ed30-139">Interop</span><span class="sxs-lookup"><span data-stu-id="3ed30-139">Interop</span></span>|<span data-ttu-id="3ed30-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-140">Optional attribute.</span></span> <span data-ttu-id="3ed30-141">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="3ed30-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="3ed30-142">Interop</span><span class="sxs-lookup"><span data-stu-id="3ed30-142">Interop</span></span>|<span data-ttu-id="3ed30-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-143">Optional attribute.</span></span> <span data-ttu-id="3ed30-144">Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="3ed30-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="3ed30-145">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="3ed30-145">Name attribute</span></span>  
  
|<span data-ttu-id="3ed30-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="3ed30-146">Value</span></span>|<span data-ttu-id="3ed30-147">Opis</span><span class="sxs-lookup"><span data-stu-id="3ed30-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ed30-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="3ed30-148">*parameter_name*</span></span>|<span data-ttu-id="3ed30-149">Nazwa parametru metody, do którego zastosowano zasady.</span><span class="sxs-lookup"><span data-stu-id="3ed30-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="3ed30-150">Na przykład w przypadku `String.CompareTo(Object value)`sygnatury metody wartość atrybutu `Name` ma wartość "value".</span><span class="sxs-lookup"><span data-stu-id="3ed30-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="3ed30-151">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ed30-151">All other attributes</span></span>  
  
|<span data-ttu-id="3ed30-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="3ed30-152">Value</span></span>|<span data-ttu-id="3ed30-153">Opis</span><span class="sxs-lookup"><span data-stu-id="3ed30-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ed30-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="3ed30-154">*policy_setting*</span></span>|<span data-ttu-id="3ed30-155">Ustawienie, które ma zostać zastosowane do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="3ed30-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="3ed30-156">Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="3ed30-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="3ed30-157">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3ed30-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ed30-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ed30-158">Child Elements</span></span>  
 <span data-ttu-id="3ed30-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="3ed30-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ed30-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ed30-160">Parent Elements</span></span>  
  
|<span data-ttu-id="3ed30-161">Element</span><span class="sxs-lookup"><span data-stu-id="3ed30-161">Element</span></span>|<span data-ttu-id="3ed30-162">Opis</span><span class="sxs-lookup"><span data-stu-id="3ed30-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ed30-163">> metody\<</span><span class="sxs-lookup"><span data-stu-id="3ed30-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="3ed30-164">Stosuje zasady odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="3ed30-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ed30-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ed30-165">Remarks</span></span>  
 <span data-ttu-id="3ed30-166">Element `<Parameter>` jest elementem podrzędnym [metody\<](method-element-net-native.md) elementu i służy do stosowania zasad do określonego parametru metody.</span><span class="sxs-lookup"><span data-stu-id="3ed30-166">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="3ed30-167">Konkretny parametr metody jest określony według nazwy, a nie według typu.</span><span class="sxs-lookup"><span data-stu-id="3ed30-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="3ed30-168">Musi być obecny co najmniej jeden atrybut reprezentujący typ zasad, taki jak `Activate` lub `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3ed30-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed30-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ed30-169">See also</span></span>

- [<span data-ttu-id="3ed30-170">Element >\<metody</span><span class="sxs-lookup"><span data-stu-id="3ed30-170">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="3ed30-171">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3ed30-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3ed30-172">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3ed30-172">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="3ed30-173">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3ed30-173">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
