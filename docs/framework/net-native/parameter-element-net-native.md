---
title: <Parameter> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d2dbff544f991712ad26f2cb12d638801b5a3fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867059"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="3273f-102">\<Parametr > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="3273f-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="3273f-103">Zastosowanie zasad odbicia do typu argumentu przekazanego do metody.</span><span class="sxs-lookup"><span data-stu-id="3273f-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3273f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3273f-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3273f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3273f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3273f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3273f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3273f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3273f-107">Attributes</span></span>  
  
|<span data-ttu-id="3273f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3273f-108">Attribute</span></span>|<span data-ttu-id="3273f-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="3273f-109">Attribute type</span></span>|<span data-ttu-id="3273f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3273f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="3273f-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="3273f-111">General</span></span>|<span data-ttu-id="3273f-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3273f-112">Required attribute.</span></span> <span data-ttu-id="3273f-113">Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="3273f-113">The parameter name.</span></span> <span data-ttu-id="3273f-114">Na przykład dla sygnatury metody `String.CompareTo(Object value)`, wartość `Name` atrybut jest "value".</span><span class="sxs-lookup"><span data-stu-id="3273f-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="3273f-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="3273f-115">Reflection</span></span>|<span data-ttu-id="3273f-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-116">Optional attribute.</span></span> <span data-ttu-id="3273f-117">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="3273f-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="3273f-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="3273f-118">Reflection</span></span>|<span data-ttu-id="3273f-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-119">Optional attribute.</span></span> <span data-ttu-id="3273f-120">Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3273f-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="3273f-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="3273f-121">Reflection</span></span>|<span data-ttu-id="3273f-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-122">Optional attribute.</span></span> <span data-ttu-id="3273f-123">Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="3273f-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="3273f-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="3273f-124">Serialization</span></span>|<span data-ttu-id="3273f-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-125">Optional attribute.</span></span> <span data-ttu-id="3273f-126">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="3273f-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="3273f-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="3273f-127">Serialization</span></span>|<span data-ttu-id="3273f-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-128">Optional attribute.</span></span> <span data-ttu-id="3273f-129">Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="3273f-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="3273f-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="3273f-130">Serialization</span></span>|<span data-ttu-id="3273f-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-131">Optional attribute.</span></span> <span data-ttu-id="3273f-132">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="3273f-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="3273f-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="3273f-133">Serialization</span></span>|<span data-ttu-id="3273f-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-134">Optional attribute.</span></span> <span data-ttu-id="3273f-135">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="3273f-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="3273f-136">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="3273f-136">Interop</span></span>|<span data-ttu-id="3273f-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-137">Optional attribute.</span></span> <span data-ttu-id="3273f-138">Określa zasady dla marshaling typów referencyjnych WinRT i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3273f-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="3273f-139">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="3273f-139">Interop</span></span>|<span data-ttu-id="3273f-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-140">Optional attribute.</span></span> <span data-ttu-id="3273f-141">Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="3273f-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="3273f-142">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="3273f-142">Interop</span></span>|<span data-ttu-id="3273f-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3273f-143">Optional attribute.</span></span> <span data-ttu-id="3273f-144">Określa zasady dla marshaling typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="3273f-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="3273f-145">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="3273f-145">Name attribute</span></span>  
  
|<span data-ttu-id="3273f-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="3273f-146">Value</span></span>|<span data-ttu-id="3273f-147">Opis</span><span class="sxs-lookup"><span data-stu-id="3273f-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3273f-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="3273f-148">*parameter_name*</span></span>|<span data-ttu-id="3273f-149">Nazwa parametru metody, do którego zastosowano zasady.</span><span class="sxs-lookup"><span data-stu-id="3273f-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="3273f-150">Na przykład dla sygnatury metody `String.CompareTo(Object value)`, wartość `Name` atrybut jest "value".</span><span class="sxs-lookup"><span data-stu-id="3273f-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="3273f-151">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="3273f-151">All other attributes</span></span>  
  
|<span data-ttu-id="3273f-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="3273f-152">Value</span></span>|<span data-ttu-id="3273f-153">Opis</span><span class="sxs-lookup"><span data-stu-id="3273f-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3273f-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="3273f-154">*policy_setting*</span></span>|<span data-ttu-id="3273f-155">Ustawienia do zastosowania do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="3273f-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="3273f-156">Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="3273f-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="3273f-157">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3273f-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3273f-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3273f-158">Child Elements</span></span>  
 <span data-ttu-id="3273f-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="3273f-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3273f-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3273f-160">Parent Elements</span></span>  
  
|<span data-ttu-id="3273f-161">Element</span><span class="sxs-lookup"><span data-stu-id="3273f-161">Element</span></span>|<span data-ttu-id="3273f-162">Opis</span><span class="sxs-lookup"><span data-stu-id="3273f-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3273f-163">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="3273f-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="3273f-164">Ma zastosowanie zasad odbicia środowiska uruchomieniowego do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="3273f-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3273f-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3273f-165">Remarks</span></span>  
 <span data-ttu-id="3273f-166">`<Parameter>` Element jest elementem podrzędnym [ \<metody >](../../../docs/framework/net-native/method-element-net-native.md) elementu i służy do stosowania zasad do parametru konkretnych metod.</span><span class="sxs-lookup"><span data-stu-id="3273f-166">The `<Parameter>` element is a child of the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="3273f-167">Parametr określonej metody jest określony przez nazwę, a nie według typu.</span><span class="sxs-lookup"><span data-stu-id="3273f-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="3273f-168">Co najmniej jeden atrybut, który reprezentuje typ zasad, takich jak `Activate` lub `Dynamic`, musi być obecny.</span><span class="sxs-lookup"><span data-stu-id="3273f-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3273f-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3273f-169">See also</span></span>

- [<span data-ttu-id="3273f-170">\<Metoda > Element</span><span class="sxs-lookup"><span data-stu-id="3273f-170">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="3273f-171">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3273f-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3273f-172">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3273f-172">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="3273f-173">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3273f-173">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
