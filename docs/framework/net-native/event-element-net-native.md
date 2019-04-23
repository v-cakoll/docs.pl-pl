---
title: <Event> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e8ddf9ea72db63c72bfb5393709b4c20de2a14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163003"
---
# <a name="event-element-net-native"></a><span data-ttu-id="63e34-102">\<Event > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="63e34-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="63e34-103">Zastosowanie zasad odbicia środowiska uruchomieniowego do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="63e34-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63e34-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63e34-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63e34-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="63e34-105">Attributes and Elements</span></span>  
 <span data-ttu-id="63e34-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="63e34-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63e34-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="63e34-107">Attributes</span></span>  
  
|<span data-ttu-id="63e34-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="63e34-108">Attribute</span></span>|<span data-ttu-id="63e34-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="63e34-109">Attribute type</span></span>|<span data-ttu-id="63e34-110">Opis</span><span class="sxs-lookup"><span data-stu-id="63e34-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="63e34-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="63e34-111">General</span></span>|<span data-ttu-id="63e34-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="63e34-112">Required attribute.</span></span> <span data-ttu-id="63e34-113">Określa nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="63e34-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="63e34-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="63e34-114">Reflection</span></span>|<span data-ttu-id="63e34-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="63e34-115">Optional attribute.</span></span> <span data-ttu-id="63e34-116">Określa wykonanie zapytania dotyczącego informacji o wyliczanie zdarzenia, ale nie uwzględnia żadnych dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="63e34-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="63e34-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="63e34-117">Reflection</span></span>|<span data-ttu-id="63e34-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="63e34-118">Optional attribute.</span></span> <span data-ttu-id="63e34-119">Dostęp do środowiska uruchomieniowego formantów na zdarzenie, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="63e34-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="63e34-120">Te zasady zapewniają, że zdarzenia mogą być obsługiwane dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="63e34-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="63e34-121">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="63e34-121">Name attribute</span></span>  
  
|<span data-ttu-id="63e34-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="63e34-122">Value</span></span>|<span data-ttu-id="63e34-123">Opis</span><span class="sxs-lookup"><span data-stu-id="63e34-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63e34-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="63e34-124">*method_name*</span></span>|<span data-ttu-id="63e34-125">Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="63e34-125">The event name.</span></span> <span data-ttu-id="63e34-126">Typ zdarzenia jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="63e34-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="63e34-127">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="63e34-127">All other attributes</span></span>  
  
|<span data-ttu-id="63e34-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="63e34-128">Value</span></span>|<span data-ttu-id="63e34-129">Opis</span><span class="sxs-lookup"><span data-stu-id="63e34-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63e34-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="63e34-130">*policy_setting*</span></span>|<span data-ttu-id="63e34-131">Ustawienia do zastosowania do tego typu zasad w wydarzeniu.</span><span class="sxs-lookup"><span data-stu-id="63e34-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="63e34-132">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="63e34-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="63e34-133">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="63e34-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63e34-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="63e34-134">Child Elements</span></span>  
 <span data-ttu-id="63e34-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="63e34-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63e34-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="63e34-136">Parent Elements</span></span>  
  
|<span data-ttu-id="63e34-137">Element</span><span class="sxs-lookup"><span data-stu-id="63e34-137">Element</span></span>|<span data-ttu-id="63e34-138">Opis</span><span class="sxs-lookup"><span data-stu-id="63e34-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63e34-139">\<Type></span><span class="sxs-lookup"><span data-stu-id="63e34-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="63e34-140">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="63e34-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="63e34-141">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="63e34-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="63e34-142">Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="63e34-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63e34-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63e34-143">Remarks</span></span>  
 <span data-ttu-id="63e34-144">Jeśli zasady zdarzeń nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania odpowiedniego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="63e34-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e34-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63e34-145">See also</span></span>

- [<span data-ttu-id="63e34-146">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="63e34-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="63e34-147">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="63e34-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="63e34-148">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="63e34-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
