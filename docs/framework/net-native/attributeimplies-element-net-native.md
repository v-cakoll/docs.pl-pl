---
title: <AttributeImplies> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d59f1f48be19a21ccc7ee5bb73cebfffc387fec2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165064"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="35b29-102">\<AttributeImplies > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="35b29-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="35b29-103">Definiuje zasady dla elementów kodu, który zawierającego atrybut jest stosowany do.</span><span class="sxs-lookup"><span data-stu-id="35b29-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35b29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35b29-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35b29-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="35b29-105">Attributes and Elements</span></span>  
 <span data-ttu-id="35b29-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="35b29-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35b29-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="35b29-107">Attributes</span></span>  
  
|<span data-ttu-id="35b29-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="35b29-108">Attribute</span></span>|<span data-ttu-id="35b29-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="35b29-109">Attribute type</span></span>|<span data-ttu-id="35b29-110">Opis</span><span class="sxs-lookup"><span data-stu-id="35b29-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="35b29-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="35b29-111">Reflection</span></span>|<span data-ttu-id="35b29-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-112">Optional attribute.</span></span> <span data-ttu-id="35b29-113">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="35b29-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="35b29-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="35b29-114">Reflection</span></span>|<span data-ttu-id="35b29-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-115">Optional attribute.</span></span> <span data-ttu-id="35b29-116">Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="35b29-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="35b29-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="35b29-117">Reflection</span></span>|<span data-ttu-id="35b29-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-118">Optional attribute.</span></span> <span data-ttu-id="35b29-119">Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="35b29-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="35b29-120">Serializacja</span><span class="sxs-lookup"><span data-stu-id="35b29-120">Serialization</span></span>|<span data-ttu-id="35b29-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-121">Optional attribute.</span></span> <span data-ttu-id="35b29-122">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="35b29-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="35b29-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="35b29-123">Serialization</span></span>|<span data-ttu-id="35b29-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-124">Optional attribute.</span></span> <span data-ttu-id="35b29-125">Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="35b29-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="35b29-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="35b29-126">Serialization</span></span>|<span data-ttu-id="35b29-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-127">Optional attribute.</span></span> <span data-ttu-id="35b29-128">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="35b29-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="35b29-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="35b29-129">Serialization</span></span>|<span data-ttu-id="35b29-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-130">Optional attribute.</span></span> <span data-ttu-id="35b29-131">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="35b29-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="35b29-132">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="35b29-132">Interop</span></span>|<span data-ttu-id="35b29-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-133">Optional attribute.</span></span> <span data-ttu-id="35b29-134">Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="35b29-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="35b29-135">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="35b29-135">Interop</span></span>|<span data-ttu-id="35b29-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-136">Optional attribute.</span></span> <span data-ttu-id="35b29-137">Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="35b29-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="35b29-138">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="35b29-138">Interop</span></span>|<span data-ttu-id="35b29-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35b29-139">Optional attribute.</span></span> <span data-ttu-id="35b29-140">Określa zasady dla marshaling typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="35b29-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="35b29-141">Wszystkie atrybuty</span><span class="sxs-lookup"><span data-stu-id="35b29-141">All attributes</span></span>  
  
|<span data-ttu-id="35b29-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="35b29-142">Value</span></span>|<span data-ttu-id="35b29-143">Opis</span><span class="sxs-lookup"><span data-stu-id="35b29-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35b29-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="35b29-144">*policy_setting*</span></span>|<span data-ttu-id="35b29-145">Ustawienia do zastosowania do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="35b29-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="35b29-146">Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="35b29-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="35b29-147">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="35b29-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35b29-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="35b29-148">Child Elements</span></span>  
 <span data-ttu-id="35b29-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="35b29-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35b29-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35b29-150">Parent Elements</span></span>  
  
|<span data-ttu-id="35b29-151">Element</span><span class="sxs-lookup"><span data-stu-id="35b29-151">Element</span></span>|<span data-ttu-id="35b29-152">Opis</span><span class="sxs-lookup"><span data-stu-id="35b29-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35b29-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="35b29-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="35b29-154">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="35b29-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35b29-155">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35b29-155">Remarks</span></span>  
 <span data-ttu-id="35b29-156">`<AttributeImplies>` Element jest używany, jeśli jej typ zawierający jest atrybutem (to znaczy, klasę pochodną <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="35b29-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="35b29-157">Jeśli ten atrybut jest stosowany do elementu określonego programu, zasady zdefiniowane przez `<AttributeImplies>` element ma zastosowanie do tego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="35b29-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="35b29-158">Odbicia, serializacja i atrybutów międzyoperacyjności są wszystkie opcjonalne, ale co najmniej jeden powinien być obecny.</span><span class="sxs-lookup"><span data-stu-id="35b29-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b29-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35b29-159">See also</span></span>

- [<span data-ttu-id="35b29-160">\<Typ > Element</span><span class="sxs-lookup"><span data-stu-id="35b29-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="35b29-161">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="35b29-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="35b29-162">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="35b29-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="35b29-163">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="35b29-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
