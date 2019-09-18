---
title: <AttributeImplies>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d15d572ee70e9c7a8cb29010d6debbd1874e5ae2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049899"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="a5e9a-102">\<AttributeImplies, element > (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="a5e9a-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="a5e9a-103">Definiuje zasady dla elementów kodu, do których jest stosowany atrybut zawierający.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5e9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5e9a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5e9a-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5e9a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a5e9a-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5e9a-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5e9a-107">Attributes</span></span>  
  
|<span data-ttu-id="a5e9a-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a5e9a-108">Attribute</span></span>|<span data-ttu-id="a5e9a-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="a5e9a-109">Attribute type</span></span>|<span data-ttu-id="a5e9a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a5e9a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="a5e9a-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="a5e9a-111">Reflection</span></span>|<span data-ttu-id="a5e9a-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-112">Optional attribute.</span></span> <span data-ttu-id="a5e9a-113">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="a5e9a-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="a5e9a-114">Reflection</span></span>|<span data-ttu-id="a5e9a-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-115">Optional attribute.</span></span> <span data-ttu-id="a5e9a-116">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="a5e9a-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="a5e9a-117">Reflection</span></span>|<span data-ttu-id="a5e9a-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-118">Optional attribute.</span></span> <span data-ttu-id="a5e9a-119">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="a5e9a-120">Serializacja</span><span class="sxs-lookup"><span data-stu-id="a5e9a-120">Serialization</span></span>|<span data-ttu-id="a5e9a-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-121">Optional attribute.</span></span> <span data-ttu-id="a5e9a-122">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="a5e9a-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="a5e9a-123">Serialization</span></span>|<span data-ttu-id="a5e9a-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-124">Optional attribute.</span></span> <span data-ttu-id="a5e9a-125">Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="a5e9a-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="a5e9a-126">Serialization</span></span>|<span data-ttu-id="a5e9a-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-127">Optional attribute.</span></span> <span data-ttu-id="a5e9a-128">Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="a5e9a-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="a5e9a-129">Serialization</span></span>|<span data-ttu-id="a5e9a-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-130">Optional attribute.</span></span> <span data-ttu-id="a5e9a-131">Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="a5e9a-132">Interop</span><span class="sxs-lookup"><span data-stu-id="a5e9a-132">Interop</span></span>|<span data-ttu-id="a5e9a-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-133">Optional attribute.</span></span> <span data-ttu-id="a5e9a-134">Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="a5e9a-135">Interop</span><span class="sxs-lookup"><span data-stu-id="a5e9a-135">Interop</span></span>|<span data-ttu-id="a5e9a-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-136">Optional attribute.</span></span> <span data-ttu-id="a5e9a-137">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="a5e9a-138">Interop</span><span class="sxs-lookup"><span data-stu-id="a5e9a-138">Interop</span></span>|<span data-ttu-id="a5e9a-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-139">Optional attribute.</span></span> <span data-ttu-id="a5e9a-140">Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="a5e9a-141">Wszystkie atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5e9a-141">All attributes</span></span>  
  
|<span data-ttu-id="a5e9a-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="a5e9a-142">Value</span></span>|<span data-ttu-id="a5e9a-143">Opis</span><span class="sxs-lookup"><span data-stu-id="a5e9a-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a5e9a-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="a5e9a-144">*policy_setting*</span></span>|<span data-ttu-id="a5e9a-145">Ustawienie, które ma zostać zastosowane do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="a5e9a-146">Możliwe wartości to `All`, `Auto` `Excluded` ,,`Public` ,,`Required All`, i. `PublicAndInternal` `Required Public` `Required PublicAndInternal`</span><span class="sxs-lookup"><span data-stu-id="a5e9a-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="a5e9a-147">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a5e9a-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5e9a-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5e9a-148">Child Elements</span></span>  
 <span data-ttu-id="a5e9a-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5e9a-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5e9a-150">Parent Elements</span></span>  
  
|<span data-ttu-id="a5e9a-151">Element</span><span class="sxs-lookup"><span data-stu-id="a5e9a-151">Element</span></span>|<span data-ttu-id="a5e9a-152">Opis</span><span class="sxs-lookup"><span data-stu-id="a5e9a-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5e9a-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="a5e9a-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="a5e9a-154">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5e9a-155">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5e9a-155">Remarks</span></span>  
 <span data-ttu-id="a5e9a-156">Element `<AttributeImplies>` jest używany, jeśli jego typ zawierający jest atrybutem (czyli klasą <xref:System.Attribute?displayProperty=nameWithType>pochodną).</span><span class="sxs-lookup"><span data-stu-id="a5e9a-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="a5e9a-157">Jeśli atrybut jest stosowany do określonego elementu programu, zasady zdefiniowane przez `<AttributeImplies>` element mają zastosowanie do tego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="a5e9a-158">Atrybuty odbicia, serializacji i międzyoperacyjności są opcjonalne, chociaż co najmniej jeden z nich powinien być obecny.</span><span class="sxs-lookup"><span data-stu-id="a5e9a-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e9a-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5e9a-159">See also</span></span>

- [<span data-ttu-id="a5e9a-160">\<Typ > element</span><span class="sxs-lookup"><span data-stu-id="a5e9a-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="a5e9a-161">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a5e9a-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a5e9a-162">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a5e9a-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="a5e9a-163">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a5e9a-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
