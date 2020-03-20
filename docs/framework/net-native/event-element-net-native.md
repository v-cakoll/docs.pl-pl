---
title: <Event>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181037"
---
# <a name="event-element-net-native"></a><span data-ttu-id="c0152-102">\<Element> zdarzenia (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="c0152-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="c0152-103">Stosuje zasady odbicia środowiska uruchomieniowego do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c0152-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0152-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0152-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0152-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c0152-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c0152-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c0152-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0152-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c0152-107">Attributes</span></span>  
  
|<span data-ttu-id="c0152-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c0152-108">Attribute</span></span>|<span data-ttu-id="c0152-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="c0152-109">Attribute type</span></span>|<span data-ttu-id="c0152-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c0152-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="c0152-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="c0152-111">General</span></span>|<span data-ttu-id="c0152-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c0152-112">Required attribute.</span></span> <span data-ttu-id="c0152-113">Określa nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c0152-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="c0152-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="c0152-114">Reflection</span></span>|<span data-ttu-id="c0152-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c0152-115">Optional attribute.</span></span> <span data-ttu-id="c0152-116">Steruje wykonywaniem zapytań o informacje o zdarzeniu lub wyliczaniu, ale nie włącza dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c0152-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="c0152-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="c0152-117">Reflection</span></span>|<span data-ttu-id="c0152-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c0152-118">Optional attribute.</span></span> <span data-ttu-id="c0152-119">Steruje dostępem środowiska wykonawczego do zdarzenia, aby włączyć programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="c0152-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="c0152-120">Ta zasada gwarantuje, że zdarzenie może być obsługiwane dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c0152-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="c0152-121">Atrybut Nazwa</span><span class="sxs-lookup"><span data-stu-id="c0152-121">Name attribute</span></span>  
  
|<span data-ttu-id="c0152-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="c0152-122">Value</span></span>|<span data-ttu-id="c0152-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c0152-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0152-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="c0152-124">*method_name*</span></span>|<span data-ttu-id="c0152-125">Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c0152-125">The event name.</span></span> <span data-ttu-id="c0152-126">Typ zdarzenia jest zdefiniowany przez [ \<](type-element-net-native.md) element nadrzędny Type>lub [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="c0152-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="c0152-127">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="c0152-127">All other attributes</span></span>  
  
|<span data-ttu-id="c0152-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="c0152-128">Value</span></span>|<span data-ttu-id="c0152-129">Opis</span><span class="sxs-lookup"><span data-stu-id="c0152-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0152-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="c0152-130">*policy_setting*</span></span>|<span data-ttu-id="c0152-131">Ustawienie, które ma zastosowanie do tego typu zasad dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c0152-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="c0152-132">Możliwe wartości `Auto` `Excluded`to `Included`, `Required`, i .</span><span class="sxs-lookup"><span data-stu-id="c0152-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="c0152-133">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="c0152-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0152-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c0152-134">Child Elements</span></span>  
 <span data-ttu-id="c0152-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="c0152-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0152-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c0152-136">Parent Elements</span></span>  
  
|<span data-ttu-id="c0152-137">Element</span><span class="sxs-lookup"><span data-stu-id="c0152-137">Element</span></span>|<span data-ttu-id="c0152-138">Opis</span><span class="sxs-lookup"><span data-stu-id="c0152-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0152-139">\<Typ></span><span class="sxs-lookup"><span data-stu-id="c0152-139">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="c0152-140">Stosuje zasady odbicia do typu i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="c0152-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="c0152-141">\<>typu></span><span class="sxs-lookup"><span data-stu-id="c0152-141">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="c0152-142">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c0152-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0152-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0152-143">Remarks</span></span>  
 <span data-ttu-id="c0152-144">Jeśli zasady zdarzenia nie jest jawnie zdefiniowane, dziedziczy zasady środowiska wykonawczego jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c0152-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0152-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0152-145">See also</span></span>

- [<span data-ttu-id="c0152-146">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="c0152-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="c0152-147">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c0152-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="c0152-148">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c0152-148">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
