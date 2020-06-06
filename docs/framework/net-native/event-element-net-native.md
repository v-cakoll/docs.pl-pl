---
title: <Event>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181037"
---
# <a name="event-element-net-native"></a><span data-ttu-id="e441f-102">\<Event>— Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e441f-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="e441f-103">Stosuje zasady odbicia środowiska uruchomieniowego do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e441f-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e441f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e441f-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e441f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e441f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e441f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e441f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e441f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e441f-107">Attributes</span></span>  
  
|<span data-ttu-id="e441f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e441f-108">Attribute</span></span>|<span data-ttu-id="e441f-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="e441f-109">Attribute type</span></span>|<span data-ttu-id="e441f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="e441f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e441f-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="e441f-111">General</span></span>|<span data-ttu-id="e441f-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="e441f-112">Required attribute.</span></span> <span data-ttu-id="e441f-113">Określa nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e441f-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="e441f-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="e441f-114">Reflection</span></span>|<span data-ttu-id="e441f-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e441f-115">Optional attribute.</span></span> <span data-ttu-id="e441f-116">Kontroluje wykonywanie zapytań dotyczących informacji na temat lub wyliczanie zdarzenia, ale nie umożliwia dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e441f-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="e441f-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="e441f-117">Reflection</span></span>|<span data-ttu-id="e441f-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e441f-118">Optional attribute.</span></span> <span data-ttu-id="e441f-119">Kontroluje dostęp środowiska uruchomieniowego do zdarzenia w celu włączenia programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="e441f-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="e441f-120">Te zasady zapewniają, że zdarzenie może być obsługiwane dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e441f-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e441f-121">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="e441f-121">Name attribute</span></span>  
  
|<span data-ttu-id="e441f-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="e441f-122">Value</span></span>|<span data-ttu-id="e441f-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e441f-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e441f-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="e441f-124">*method_name*</span></span>|<span data-ttu-id="e441f-125">Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e441f-125">The event name.</span></span> <span data-ttu-id="e441f-126">Typ zdarzenia jest definiowany przez [\<Type>](type-element-net-native.md) element nadrzędny lub [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="e441f-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e441f-127">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="e441f-127">All other attributes</span></span>  
  
|<span data-ttu-id="e441f-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="e441f-128">Value</span></span>|<span data-ttu-id="e441f-129">Opis</span><span class="sxs-lookup"><span data-stu-id="e441f-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e441f-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e441f-130">*policy_setting*</span></span>|<span data-ttu-id="e441f-131">Ustawienie, które ma zostać zastosowane do tego typu zasad dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e441f-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="e441f-132">Możliwe wartości to `Auto` , `Excluded` , `Included` , i `Required` .</span><span class="sxs-lookup"><span data-stu-id="e441f-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="e441f-133">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e441f-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e441f-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e441f-134">Child Elements</span></span>  
 <span data-ttu-id="e441f-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="e441f-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e441f-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e441f-136">Parent Elements</span></span>  
  
|<span data-ttu-id="e441f-137">Element</span><span class="sxs-lookup"><span data-stu-id="e441f-137">Element</span></span>|<span data-ttu-id="e441f-138">Opis</span><span class="sxs-lookup"><span data-stu-id="e441f-138">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="e441f-139">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="e441f-139">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="e441f-140">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="e441f-140">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e441f-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e441f-141">Remarks</span></span>  
 <span data-ttu-id="e441f-142">Jeśli zasady zdarzenia nie są jawnie zdefiniowane, dziedziczy zasad środowiska uruchomieniowego jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="e441f-142">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e441f-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e441f-143">See also</span></span>

- [<span data-ttu-id="e441f-144">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="e441f-144">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e441f-145">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e441f-145">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="e441f-146">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e441f-146">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
