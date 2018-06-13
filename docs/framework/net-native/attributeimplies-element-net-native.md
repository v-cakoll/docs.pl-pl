---
title: Element &lt;AttributeImplies&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 960ee5716b9760ab82628a8d21728cd6675e5215
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395443"
---
# <a name="ltattributeimpliesgt-element-net-native"></a><span data-ttu-id="deeef-102">Element &lt;AttributeImplies&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="deeef-102">&lt;AttributeImplies&gt; Element (.NET Native)</span></span>
<span data-ttu-id="deeef-103">Definiuje zasady dla elementów kodu, zawierającego atrybut jest stosowany do.</span><span class="sxs-lookup"><span data-stu-id="deeef-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deeef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="deeef-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="deeef-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="deeef-105">Attributes and Elements</span></span>  
 <span data-ttu-id="deeef-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="deeef-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="deeef-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="deeef-107">Attributes</span></span>  
  
|<span data-ttu-id="deeef-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="deeef-108">Attribute</span></span>|<span data-ttu-id="deeef-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="deeef-109">Attribute type</span></span>|<span data-ttu-id="deeef-110">Opis</span><span class="sxs-lookup"><span data-stu-id="deeef-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="deeef-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="deeef-111">Reflection</span></span>|<span data-ttu-id="deeef-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-112">Optional attribute.</span></span> <span data-ttu-id="deeef-113">Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="deeef-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="deeef-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="deeef-114">Reflection</span></span>|<span data-ttu-id="deeef-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-115">Optional attribute.</span></span> <span data-ttu-id="deeef-116">Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="deeef-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="deeef-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="deeef-117">Reflection</span></span>|<span data-ttu-id="deeef-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-118">Optional attribute.</span></span> <span data-ttu-id="deeef-119">Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="deeef-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="deeef-120">Serializacja</span><span class="sxs-lookup"><span data-stu-id="deeef-120">Serialization</span></span>|<span data-ttu-id="deeef-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-121">Optional attribute.</span></span> <span data-ttu-id="deeef-122">Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="deeef-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="deeef-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="deeef-123">Serialization</span></span>|<span data-ttu-id="deeef-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-124">Optional attribute.</span></span> <span data-ttu-id="deeef-125">Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="deeef-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="deeef-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="deeef-126">Serialization</span></span>|<span data-ttu-id="deeef-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-127">Optional attribute.</span></span> <span data-ttu-id="deeef-128">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="deeef-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="deeef-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="deeef-129">Serialization</span></span>|<span data-ttu-id="deeef-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-130">Optional attribute.</span></span> <span data-ttu-id="deeef-131">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="deeef-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="deeef-132">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="deeef-132">Interop</span></span>|<span data-ttu-id="deeef-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-133">Optional attribute.</span></span> <span data-ttu-id="deeef-134">Zasady kontroli przekazywanie typów referencyjnych do środowiska wykonawczego systemu Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="deeef-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="deeef-135">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="deeef-135">Interop</span></span>|<span data-ttu-id="deeef-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-136">Optional attribute.</span></span> <span data-ttu-id="deeef-137">Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="deeef-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="deeef-138">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="deeef-138">Interop</span></span>|<span data-ttu-id="deeef-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="deeef-139">Optional attribute.</span></span> <span data-ttu-id="deeef-140">Określa zasady dla przekazywanie typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="deeef-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="deeef-141">Wszystkie atrybuty</span><span class="sxs-lookup"><span data-stu-id="deeef-141">All attributes</span></span>  
  
|<span data-ttu-id="deeef-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="deeef-142">Value</span></span>|<span data-ttu-id="deeef-143">Opis</span><span class="sxs-lookup"><span data-stu-id="deeef-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="deeef-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="deeef-144">*policy_setting*</span></span>|<span data-ttu-id="deeef-145">Ustawienia do zastosowania dla tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="deeef-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="deeef-146">Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="deeef-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="deeef-147">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="deeef-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="deeef-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="deeef-148">Child Elements</span></span>  
 <span data-ttu-id="deeef-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="deeef-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="deeef-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="deeef-150">Parent Elements</span></span>  
  
|<span data-ttu-id="deeef-151">Element</span><span class="sxs-lookup"><span data-stu-id="deeef-151">Element</span></span>|<span data-ttu-id="deeef-152">Opis</span><span class="sxs-lookup"><span data-stu-id="deeef-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="deeef-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="deeef-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="deeef-154">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="deeef-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="deeef-155">Uwagi</span><span class="sxs-lookup"><span data-stu-id="deeef-155">Remarks</span></span>  
 <span data-ttu-id="deeef-156">`<AttributeImplies>` Element jest używany, jeśli jej typ zawierający jest atrybut (to znaczy klasą pochodną <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="deeef-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="deeef-157">Jeśli atrybut jest stosowany do elementu określonego programu, zasady zdefiniowane przez `<AttributeImplies>` element ma zastosowanie do tego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="deeef-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="deeef-158">Odbicie serializacji i atrybutów międzyoperacyjności są wszystkie opcjonalne, mimo że co najmniej jeden powinien być obecny.</span><span class="sxs-lookup"><span data-stu-id="deeef-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deeef-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="deeef-159">See Also</span></span>  
 [<span data-ttu-id="deeef-160">\<Typ > — Element</span><span class="sxs-lookup"><span data-stu-id="deeef-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="deeef-161">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="deeef-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="deeef-162">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="deeef-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="deeef-163">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="deeef-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
