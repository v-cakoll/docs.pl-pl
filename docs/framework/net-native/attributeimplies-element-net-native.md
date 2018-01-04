---
title: Element &lt;AttributeImplies&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92a886ab09978aef6694c37d74af49b27c37c6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltattributeimpliesgt-element-net-native"></a><span data-ttu-id="c07c5-102">Element &lt;AttributeImplies&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="c07c5-102">&lt;AttributeImplies&gt; Element (.NET Native)</span></span>
<span data-ttu-id="c07c5-103">Definiuje zasady dla elementów kodu, zawierającego atrybut jest stosowany do.</span><span class="sxs-lookup"><span data-stu-id="c07c5-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c07c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c07c5-104">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c07c5-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c07c5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c07c5-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c07c5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c07c5-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c07c5-107">Attributes</span></span>  
  
|<span data-ttu-id="c07c5-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c07c5-108">Attribute</span></span>|<span data-ttu-id="c07c5-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="c07c5-109">Attribute type</span></span>|<span data-ttu-id="c07c5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c07c5-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="c07c5-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="c07c5-111">Reflection</span></span>|<span data-ttu-id="c07c5-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-112">Optional attribute.</span></span> <span data-ttu-id="c07c5-113">Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="c07c5-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="c07c5-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="c07c5-114">Reflection</span></span>|<span data-ttu-id="c07c5-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-115">Optional attribute.</span></span> <span data-ttu-id="c07c5-116">Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="c07c5-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="c07c5-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="c07c5-117">Reflection</span></span>|<span data-ttu-id="c07c5-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-118">Optional attribute.</span></span> <span data-ttu-id="c07c5-119">Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="c07c5-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="c07c5-120">Serializacja</span><span class="sxs-lookup"><span data-stu-id="c07c5-120">Serialization</span></span>|<span data-ttu-id="c07c5-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-121">Optional attribute.</span></span> <span data-ttu-id="c07c5-122">Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="c07c5-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="c07c5-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="c07c5-123">Serialization</span></span>|<span data-ttu-id="c07c5-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-124">Optional attribute.</span></span> <span data-ttu-id="c07c5-125">Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="c07c5-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="c07c5-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="c07c5-126">Serialization</span></span>|<span data-ttu-id="c07c5-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-127">Optional attribute.</span></span> <span data-ttu-id="c07c5-128">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="c07c5-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="c07c5-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="c07c5-129">Serialization</span></span>|<span data-ttu-id="c07c5-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-130">Optional attribute.</span></span> <span data-ttu-id="c07c5-131">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="c07c5-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="c07c5-132">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c07c5-132">Interop</span></span>|<span data-ttu-id="c07c5-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-133">Optional attribute.</span></span> <span data-ttu-id="c07c5-134">Zasady kontroli przekazywanie typów referencyjnych do środowiska wykonawczego systemu Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c07c5-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="c07c5-135">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c07c5-135">Interop</span></span>|<span data-ttu-id="c07c5-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-136">Optional attribute.</span></span> <span data-ttu-id="c07c5-137">Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="c07c5-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="c07c5-138">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c07c5-138">Interop</span></span>|<span data-ttu-id="c07c5-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-139">Optional attribute.</span></span> <span data-ttu-id="c07c5-140">Określa zasady dla przekazywanie typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="c07c5-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="c07c5-141">Wszystkie atrybuty</span><span class="sxs-lookup"><span data-stu-id="c07c5-141">All attributes</span></span>  
  
|<span data-ttu-id="c07c5-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="c07c5-142">Value</span></span>|<span data-ttu-id="c07c5-143">Opis</span><span class="sxs-lookup"><span data-stu-id="c07c5-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c07c5-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="c07c5-144">*policy_setting*</span></span>|<span data-ttu-id="c07c5-145">Ustawienia do zastosowania dla tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="c07c5-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="c07c5-146">Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="c07c5-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="c07c5-147">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="c07c5-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c07c5-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c07c5-148">Child Elements</span></span>  
 <span data-ttu-id="c07c5-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="c07c5-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c07c5-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c07c5-150">Parent Elements</span></span>  
  
|<span data-ttu-id="c07c5-151">Element</span><span class="sxs-lookup"><span data-stu-id="c07c5-151">Element</span></span>|<span data-ttu-id="c07c5-152">Opis</span><span class="sxs-lookup"><span data-stu-id="c07c5-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c07c5-153">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="c07c5-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="c07c5-154">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c07c5-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c07c5-155">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c07c5-155">Remarks</span></span>  
 <span data-ttu-id="c07c5-156">`<AttributeImplies>` Element jest używany, jeśli jej typ zawierający jest atrybut (to znaczy klasą pochodną <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="c07c5-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="c07c5-157">Jeśli atrybut jest stosowany do elementu określonego programu, zasady zdefiniowane przez `<AttributeImplies>` element ma zastosowanie do tego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="c07c5-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="c07c5-158">Odbicie serializacji i atrybutów międzyoperacyjności są wszystkie opcjonalne, mimo że co najmniej jeden powinien być obecny.</span><span class="sxs-lookup"><span data-stu-id="c07c5-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07c5-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c07c5-159">See Also</span></span>  
 [<span data-ttu-id="c07c5-160">\<Typ > — Element</span><span class="sxs-lookup"><span data-stu-id="c07c5-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="c07c5-161">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="c07c5-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="c07c5-162">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c07c5-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="c07c5-163">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c07c5-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
