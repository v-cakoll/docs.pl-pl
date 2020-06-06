---
title: <AttributeImplies>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181066"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="6a4cb-102">\<AttributeImplies>— Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6a4cb-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="6a4cb-103">Definiuje zasady dla elementów kodu, do których jest stosowany atrybut zawierający.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a4cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a4cb-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a4cb-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a4cb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6a4cb-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a4cb-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a4cb-107">Attributes</span></span>  
  
|<span data-ttu-id="6a4cb-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6a4cb-108">Attribute</span></span>|<span data-ttu-id="6a4cb-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="6a4cb-109">Attribute type</span></span>|<span data-ttu-id="6a4cb-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6a4cb-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="6a4cb-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="6a4cb-111">Reflection</span></span>|<span data-ttu-id="6a4cb-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-112">Optional attribute.</span></span> <span data-ttu-id="6a4cb-113">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6a4cb-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="6a4cb-114">Reflection</span></span>|<span data-ttu-id="6a4cb-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-115">Optional attribute.</span></span> <span data-ttu-id="6a4cb-116">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6a4cb-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="6a4cb-117">Reflection</span></span>|<span data-ttu-id="6a4cb-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-118">Optional attribute.</span></span> <span data-ttu-id="6a4cb-119">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6a4cb-120">Serializacja</span><span class="sxs-lookup"><span data-stu-id="6a4cb-120">Serialization</span></span>|<span data-ttu-id="6a4cb-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-121">Optional attribute.</span></span> <span data-ttu-id="6a4cb-122">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6a4cb-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="6a4cb-123">Serialization</span></span>|<span data-ttu-id="6a4cb-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-124">Optional attribute.</span></span> <span data-ttu-id="6a4cb-125">Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6a4cb-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="6a4cb-126">Serialization</span></span>|<span data-ttu-id="6a4cb-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-127">Optional attribute.</span></span> <span data-ttu-id="6a4cb-128">Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6a4cb-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="6a4cb-129">Serialization</span></span>|<span data-ttu-id="6a4cb-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-130">Optional attribute.</span></span> <span data-ttu-id="6a4cb-131">Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6a4cb-132">Interop</span><span class="sxs-lookup"><span data-stu-id="6a4cb-132">Interop</span></span>|<span data-ttu-id="6a4cb-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-133">Optional attribute.</span></span> <span data-ttu-id="6a4cb-134">Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6a4cb-135">Interop</span><span class="sxs-lookup"><span data-stu-id="6a4cb-135">Interop</span></span>|<span data-ttu-id="6a4cb-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-136">Optional attribute.</span></span> <span data-ttu-id="6a4cb-137">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6a4cb-138">Interop</span><span class="sxs-lookup"><span data-stu-id="6a4cb-138">Interop</span></span>|<span data-ttu-id="6a4cb-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-139">Optional attribute.</span></span> <span data-ttu-id="6a4cb-140">Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="6a4cb-141">Wszystkie atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a4cb-141">All attributes</span></span>  
  
|<span data-ttu-id="6a4cb-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="6a4cb-142">Value</span></span>|<span data-ttu-id="6a4cb-143">Opis</span><span class="sxs-lookup"><span data-stu-id="6a4cb-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6a4cb-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6a4cb-144">*policy_setting*</span></span>|<span data-ttu-id="6a4cb-145">Ustawienie, które ma zostać zastosowane do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="6a4cb-146">Możliwe wartości to `All` , `Auto` ,,,,, `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` i `Required All` .</span><span class="sxs-lookup"><span data-stu-id="6a4cb-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6a4cb-147">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6a4cb-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a4cb-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a4cb-148">Child Elements</span></span>  
 <span data-ttu-id="6a4cb-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a4cb-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a4cb-150">Parent Elements</span></span>  
  
|<span data-ttu-id="6a4cb-151">Element</span><span class="sxs-lookup"><span data-stu-id="6a4cb-151">Element</span></span>|<span data-ttu-id="6a4cb-152">Opis</span><span class="sxs-lookup"><span data-stu-id="6a4cb-152">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="6a4cb-153">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-153">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a4cb-154">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a4cb-154">Remarks</span></span>  
 <span data-ttu-id="6a4cb-155">`<AttributeImplies>`Element jest używany, jeśli jego typ zawierający jest atrybutem (czyli klasą pochodną <xref:System.Attribute?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="6a4cb-155">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="6a4cb-156">Jeśli atrybut jest stosowany do określonego elementu programu, zasady zdefiniowane przez `<AttributeImplies>` element mają zastosowanie do tego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-156">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="6a4cb-157">Atrybuty odbicia, serializacji i międzyoperacyjności są opcjonalne, chociaż co najmniej jeden z nich powinien być obecny.</span><span class="sxs-lookup"><span data-stu-id="6a4cb-157">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a4cb-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a4cb-158">See also</span></span>

- [<span data-ttu-id="6a4cb-159">\<Type>Postaci</span><span class="sxs-lookup"><span data-stu-id="6a4cb-159">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="6a4cb-160">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6a4cb-160">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6a4cb-161">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6a4cb-161">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="6a4cb-162">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6a4cb-162">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
