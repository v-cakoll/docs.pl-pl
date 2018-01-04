---
title: Element &lt;Parameter&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 820c36abda104bbf748e5b3a7838f3c7715048e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltparametergt-element-net-native"></a><span data-ttu-id="5d2a1-102">Element &lt;Parameter&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="5d2a1-102">&lt;Parameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="5d2a1-103">Stosuje odbicia zasady do typu argumentu przekazanego do metody.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d2a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d2a1-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d2a1-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5d2a1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5d2a1-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d2a1-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5d2a1-107">Attributes</span></span>  
  
|<span data-ttu-id="5d2a1-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5d2a1-108">Attribute</span></span>|<span data-ttu-id="5d2a1-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="5d2a1-109">Attribute type</span></span>|<span data-ttu-id="5d2a1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5d2a1-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="5d2a1-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="5d2a1-111">General</span></span>|<span data-ttu-id="5d2a1-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-112">Required attribute.</span></span> <span data-ttu-id="5d2a1-113">Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-113">The parameter name.</span></span> <span data-ttu-id="5d2a1-114">Na przykład w podpisie metody `String.CompareTo(Object value)`, wartość `Name` atrybutu jest "value".</span><span class="sxs-lookup"><span data-stu-id="5d2a1-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="5d2a1-115">Odbicie</span><span class="sxs-lookup"><span data-stu-id="5d2a1-115">Reflection</span></span>|<span data-ttu-id="5d2a1-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-116">Optional attribute.</span></span> <span data-ttu-id="5d2a1-117">Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="5d2a1-118">Odbicie</span><span class="sxs-lookup"><span data-stu-id="5d2a1-118">Reflection</span></span>|<span data-ttu-id="5d2a1-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-119">Optional attribute.</span></span> <span data-ttu-id="5d2a1-120">Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="5d2a1-121">Odbicie</span><span class="sxs-lookup"><span data-stu-id="5d2a1-121">Reflection</span></span>|<span data-ttu-id="5d2a1-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-122">Optional attribute.</span></span> <span data-ttu-id="5d2a1-123">Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="5d2a1-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="5d2a1-124">Serialization</span></span>|<span data-ttu-id="5d2a1-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-125">Optional attribute.</span></span> <span data-ttu-id="5d2a1-126">Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="5d2a1-127">Serializacja</span><span class="sxs-lookup"><span data-stu-id="5d2a1-127">Serialization</span></span>|<span data-ttu-id="5d2a1-128">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-128">Optional attribute.</span></span> <span data-ttu-id="5d2a1-129">Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="5d2a1-130">Serializacja</span><span class="sxs-lookup"><span data-stu-id="5d2a1-130">Serialization</span></span>|<span data-ttu-id="5d2a1-131">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-131">Optional attribute.</span></span> <span data-ttu-id="5d2a1-132">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="5d2a1-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="5d2a1-133">Serialization</span></span>|<span data-ttu-id="5d2a1-134">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-134">Optional attribute.</span></span> <span data-ttu-id="5d2a1-135">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="5d2a1-136">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="5d2a1-136">Interop</span></span>|<span data-ttu-id="5d2a1-137">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-137">Optional attribute.</span></span> <span data-ttu-id="5d2a1-138">Określa zasady dla przekazywanie typów referencyjnych do środowiska WinRT i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="5d2a1-139">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="5d2a1-139">Interop</span></span>|<span data-ttu-id="5d2a1-140">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-140">Optional attribute.</span></span> <span data-ttu-id="5d2a1-141">Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="5d2a1-142">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="5d2a1-142">Interop</span></span>|<span data-ttu-id="5d2a1-143">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-143">Optional attribute.</span></span> <span data-ttu-id="5d2a1-144">Określa zasady dla przekazywanie typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="5d2a1-145">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="5d2a1-145">Name attribute</span></span>  
  
|<span data-ttu-id="5d2a1-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="5d2a1-146">Value</span></span>|<span data-ttu-id="5d2a1-147">Opis</span><span class="sxs-lookup"><span data-stu-id="5d2a1-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d2a1-148">*nazwa_parametru*</span><span class="sxs-lookup"><span data-stu-id="5d2a1-148">*parameter_name*</span></span>|<span data-ttu-id="5d2a1-149">Nazwa parametru metody, do której są stosowane zasady.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="5d2a1-150">Na przykład w podpisie metody `String.CompareTo(Object value)`, wartość `Name` atrybutu jest "value".</span><span class="sxs-lookup"><span data-stu-id="5d2a1-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="5d2a1-151">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="5d2a1-151">All other attributes</span></span>  
  
|<span data-ttu-id="5d2a1-152">Wartość</span><span class="sxs-lookup"><span data-stu-id="5d2a1-152">Value</span></span>|<span data-ttu-id="5d2a1-153">Opis</span><span class="sxs-lookup"><span data-stu-id="5d2a1-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d2a1-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="5d2a1-154">*policy_setting*</span></span>|<span data-ttu-id="5d2a1-155">Ustawienia do zastosowania dla tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="5d2a1-156">Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="5d2a1-157">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5d2a1-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d2a1-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5d2a1-158">Child Elements</span></span>  
 <span data-ttu-id="5d2a1-159">Brak.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d2a1-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5d2a1-160">Parent Elements</span></span>  
  
|<span data-ttu-id="5d2a1-161">Element</span><span class="sxs-lookup"><span data-stu-id="5d2a1-161">Element</span></span>|<span data-ttu-id="5d2a1-162">Opis</span><span class="sxs-lookup"><span data-stu-id="5d2a1-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d2a1-163">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="5d2a1-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="5d2a1-164">Zastosowanie zasad wykonywania odbicia do konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d2a1-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d2a1-165">Remarks</span></span>  
 <span data-ttu-id="5d2a1-166">`<Parameter>` Element jest elementem podrzędnym [ \<metody >](../../../docs/framework/net-native/method-element-net-native.md) element i służy do stosowania zasad do konkretnej metody parametru.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-166">The `<Parameter>` element is a child of the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="5d2a1-167">Według nazwy, a nie według typu, jest określony parametr dla określonej metody.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="5d2a1-168">Co najmniej jeden atrybut, który reprezentuje typ zasad, takich jak `Activate` lub `Dynamic`, musi być obecny.</span><span class="sxs-lookup"><span data-stu-id="5d2a1-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d2a1-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d2a1-169">See Also</span></span>  
 [<span data-ttu-id="5d2a1-170">\<Metoda > — Element</span><span class="sxs-lookup"><span data-stu-id="5d2a1-170">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="5d2a1-171">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="5d2a1-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="5d2a1-172">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5d2a1-172">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="5d2a1-173">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5d2a1-173">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
