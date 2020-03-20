---
title: <AttributeImplies>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181066"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="b613c-102">\<Atrybut implikuje element> (natywny.NET)</span><span class="sxs-lookup"><span data-stu-id="b613c-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="b613c-103">Definiuje zasady dla elementów kodu, do których jest stosowany atrybut zawierający.</span><span class="sxs-lookup"><span data-stu-id="b613c-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b613c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b613c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b613c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b613c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b613c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b613c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b613c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b613c-107">Attributes</span></span>  
  
|<span data-ttu-id="b613c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b613c-108">Attribute</span></span>|<span data-ttu-id="b613c-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="b613c-109">Attribute type</span></span>|<span data-ttu-id="b613c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b613c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="b613c-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="b613c-111">Reflection</span></span>|<span data-ttu-id="b613c-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-112">Optional attribute.</span></span> <span data-ttu-id="b613c-113">Steruje dostępem środowiska wykonawczego do konstruktorów, aby włączyć aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="b613c-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="b613c-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="b613c-114">Reflection</span></span>|<span data-ttu-id="b613c-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-115">Optional attribute.</span></span> <span data-ttu-id="b613c-116">Steruje wykonywaniem zapytań o informacje o elementach programu, ale nie włącza dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b613c-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="b613c-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="b613c-117">Reflection</span></span>|<span data-ttu-id="b613c-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-118">Optional attribute.</span></span> <span data-ttu-id="b613c-119">Steruje dostępem środowiska uruchomieniowego do wszystkich elementów członkowskich typu, w tym konstruktorów, metod, pól, właściwości i zdarzeń, aby włączyć programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="b613c-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="b613c-120">Serializacja</span><span class="sxs-lookup"><span data-stu-id="b613c-120">Serialization</span></span>|<span data-ttu-id="b613c-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-121">Optional attribute.</span></span> <span data-ttu-id="b613c-122">Steruje dostępem środowiska wykonawczego do konstruktorów, pól i właściwości, aby umożliwić serializowanie i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON firmy Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="b613c-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="b613c-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="b613c-123">Serialization</span></span>|<span data-ttu-id="b613c-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-124">Optional attribute.</span></span> <span data-ttu-id="b613c-125">Steruje zasadami serializacji, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> która używa klasy.</span><span class="sxs-lookup"><span data-stu-id="b613c-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="b613c-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="b613c-126">Serialization</span></span>|<span data-ttu-id="b613c-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-127">Optional attribute.</span></span> <span data-ttu-id="b613c-128">Steruje zasadami serializacji JSON, która używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="b613c-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="b613c-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="b613c-129">Serialization</span></span>|<span data-ttu-id="b613c-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-130">Optional attribute.</span></span> <span data-ttu-id="b613c-131">Steruje zasadami serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> tej klasy.</span><span class="sxs-lookup"><span data-stu-id="b613c-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="b613c-132">Interop</span><span class="sxs-lookup"><span data-stu-id="b613c-132">Interop</span></span>|<span data-ttu-id="b613c-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-133">Optional attribute.</span></span> <span data-ttu-id="b613c-134">Steruje zasadami organizowania typów odwołań do środowiska wykonawczego systemu Windows i środowiska COM.</span><span class="sxs-lookup"><span data-stu-id="b613c-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="b613c-135">Interop</span><span class="sxs-lookup"><span data-stu-id="b613c-135">Interop</span></span>|<span data-ttu-id="b613c-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-136">Optional attribute.</span></span> <span data-ttu-id="b613c-137">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="b613c-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="b613c-138">Interop</span><span class="sxs-lookup"><span data-stu-id="b613c-138">Interop</span></span>|<span data-ttu-id="b613c-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b613c-139">Optional attribute.</span></span> <span data-ttu-id="b613c-140">Steruje zasadami organizowania typów wartości do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="b613c-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="b613c-141">Wszystkie atrybuty</span><span class="sxs-lookup"><span data-stu-id="b613c-141">All attributes</span></span>  
  
|<span data-ttu-id="b613c-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="b613c-142">Value</span></span>|<span data-ttu-id="b613c-143">Opis</span><span class="sxs-lookup"><span data-stu-id="b613c-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b613c-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="b613c-144">*policy_setting*</span></span>|<span data-ttu-id="b613c-145">Ustawienie, które ma zastosowanie do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="b613c-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="b613c-146">Możliwe wartości `All` `Auto`to `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , i .</span><span class="sxs-lookup"><span data-stu-id="b613c-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="b613c-147">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b613c-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b613c-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b613c-148">Child Elements</span></span>  
 <span data-ttu-id="b613c-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="b613c-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b613c-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b613c-150">Parent Elements</span></span>  
  
|<span data-ttu-id="b613c-151">Element</span><span class="sxs-lookup"><span data-stu-id="b613c-151">Element</span></span>|<span data-ttu-id="b613c-152">Opis</span><span class="sxs-lookup"><span data-stu-id="b613c-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b613c-153">\<Typ></span><span class="sxs-lookup"><span data-stu-id="b613c-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="b613c-154">Stosuje zasady odbicia do typu i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="b613c-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b613c-155">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b613c-155">Remarks</span></span>  
 <span data-ttu-id="b613c-156">Element `<AttributeImplies>` jest używany, jeśli jego typ zawierający jest atrybutem (czyli klasą pochodną <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="b613c-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="b613c-157">Jeśli atrybut jest stosowany do określonego elementu programu, zasady `<AttributeImplies>` zdefiniowane przez element stosuje się do tego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="b613c-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="b613c-158">Atrybuty odbicia, serializacji i międzyoperacyjne są opcjonalne, chociaż co najmniej jeden powinien być obecny.</span><span class="sxs-lookup"><span data-stu-id="b613c-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b613c-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b613c-159">See also</span></span>

- [<span data-ttu-id="b613c-160">\<Wpisz element></span><span class="sxs-lookup"><span data-stu-id="b613c-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="b613c-161">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="b613c-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b613c-162">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b613c-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="b613c-163">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b613c-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
