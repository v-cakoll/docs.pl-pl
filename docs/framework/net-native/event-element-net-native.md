---
title: Element <Event> (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 6966caede63faafa718b760be879f6bc6cbd3ab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128491"
---
# <a name="event-element-net-native"></a><span data-ttu-id="a3932-102">\<> zdarzeń (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="a3932-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="a3932-103">Stosuje zasady odbicia środowiska uruchomieniowego do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3932-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3932-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3932-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3932-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a3932-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a3932-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a3932-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3932-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a3932-107">Attributes</span></span>  
  
|<span data-ttu-id="a3932-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a3932-108">Attribute</span></span>|<span data-ttu-id="a3932-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="a3932-109">Attribute type</span></span>|<span data-ttu-id="a3932-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a3932-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="a3932-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="a3932-111">General</span></span>|<span data-ttu-id="a3932-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a3932-112">Required attribute.</span></span> <span data-ttu-id="a3932-113">Określa nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3932-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="a3932-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="a3932-114">Reflection</span></span>|<span data-ttu-id="a3932-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a3932-115">Optional attribute.</span></span> <span data-ttu-id="a3932-116">Kontroluje wykonywanie zapytań dotyczących informacji na temat lub wyliczanie zdarzenia, ale nie umożliwia dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a3932-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="a3932-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="a3932-117">Reflection</span></span>|<span data-ttu-id="a3932-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a3932-118">Optional attribute.</span></span> <span data-ttu-id="a3932-119">Kontroluje dostęp środowiska uruchomieniowego do zdarzenia w celu włączenia programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="a3932-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="a3932-120">Te zasady zapewniają, że zdarzenie może być obsługiwane dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a3932-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="a3932-121">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="a3932-121">Name attribute</span></span>  
  
|<span data-ttu-id="a3932-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="a3932-122">Value</span></span>|<span data-ttu-id="a3932-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a3932-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a3932-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="a3932-124">*method_name*</span></span>|<span data-ttu-id="a3932-125">Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3932-125">The event name.</span></span> <span data-ttu-id="a3932-126">Typ zdarzenia jest definiowany przez [typ\<nadrzędnego >](type-element-net-native.md) lub [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="a3932-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="a3932-127">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="a3932-127">All other attributes</span></span>  
  
|<span data-ttu-id="a3932-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="a3932-128">Value</span></span>|<span data-ttu-id="a3932-129">Opis</span><span class="sxs-lookup"><span data-stu-id="a3932-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a3932-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="a3932-130">*policy_setting*</span></span>|<span data-ttu-id="a3932-131">Ustawienie, które ma zostać zastosowane do tego typu zasad dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3932-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="a3932-132">Możliwe wartości to `Auto`, `Excluded`, `Included`i `Required`.</span><span class="sxs-lookup"><span data-stu-id="a3932-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="a3932-133">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a3932-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3932-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a3932-134">Child Elements</span></span>  
 <span data-ttu-id="a3932-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="a3932-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3932-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a3932-136">Parent Elements</span></span>  
  
|<span data-ttu-id="a3932-137">Element</span><span class="sxs-lookup"><span data-stu-id="a3932-137">Element</span></span>|<span data-ttu-id="a3932-138">Opis</span><span class="sxs-lookup"><span data-stu-id="a3932-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3932-139">Typ\<</span><span class="sxs-lookup"><span data-stu-id="a3932-139">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="a3932-140">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="a3932-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="a3932-141">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="a3932-141">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="a3932-142">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="a3932-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3932-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3932-143">Remarks</span></span>  
 <span data-ttu-id="a3932-144">Jeśli zasady zdarzenia nie są jawnie zdefiniowane, dziedziczy zasad środowiska uruchomieniowego jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a3932-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3932-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3932-145">See also</span></span>

- [<span data-ttu-id="a3932-146">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a3932-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a3932-147">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a3932-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="a3932-148">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a3932-148">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
