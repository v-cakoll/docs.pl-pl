---
title: <Event> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5d778ca30aa29ba883552f97e061fb1dde8d73e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287585"
---
# <a name="event-element-net-native"></a><span data-ttu-id="6b841-102">\<Event > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="6b841-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="6b841-103">Zastosowanie zasad odbicia środowiska uruchomieniowego do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6b841-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b841-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b841-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b841-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6b841-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6b841-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b841-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b841-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6b841-107">Attributes</span></span>  
  
|<span data-ttu-id="6b841-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6b841-108">Attribute</span></span>|<span data-ttu-id="6b841-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="6b841-109">Attribute type</span></span>|<span data-ttu-id="6b841-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6b841-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6b841-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="6b841-111">General</span></span>|<span data-ttu-id="6b841-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6b841-112">Required attribute.</span></span> <span data-ttu-id="6b841-113">Określa nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6b841-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="6b841-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="6b841-114">Reflection</span></span>|<span data-ttu-id="6b841-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6b841-115">Optional attribute.</span></span> <span data-ttu-id="6b841-116">Określa wykonanie zapytania dotyczącego informacji o wyliczanie zdarzenia, ale nie uwzględnia żadnych dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6b841-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="6b841-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="6b841-117">Reflection</span></span>|<span data-ttu-id="6b841-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6b841-118">Optional attribute.</span></span> <span data-ttu-id="6b841-119">Dostęp do środowiska uruchomieniowego formantów na zdarzenie, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="6b841-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="6b841-120">Te zasady zapewniają, że zdarzenia mogą być obsługiwane dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6b841-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6b841-121">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="6b841-121">Name attribute</span></span>  
  
|<span data-ttu-id="6b841-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="6b841-122">Value</span></span>|<span data-ttu-id="6b841-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6b841-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b841-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="6b841-124">*method_name*</span></span>|<span data-ttu-id="6b841-125">Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6b841-125">The event name.</span></span> <span data-ttu-id="6b841-126">Typ zdarzenia jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6b841-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6b841-127">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="6b841-127">All other attributes</span></span>  
  
|<span data-ttu-id="6b841-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="6b841-128">Value</span></span>|<span data-ttu-id="6b841-129">Opis</span><span class="sxs-lookup"><span data-stu-id="6b841-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b841-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6b841-130">*policy_setting*</span></span>|<span data-ttu-id="6b841-131">Ustawienia do zastosowania do tego typu zasad w wydarzeniu.</span><span class="sxs-lookup"><span data-stu-id="6b841-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="6b841-132">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="6b841-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="6b841-133">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6b841-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b841-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6b841-134">Child Elements</span></span>  
 <span data-ttu-id="6b841-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="6b841-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b841-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6b841-136">Parent Elements</span></span>  
  
|<span data-ttu-id="6b841-137">Element</span><span class="sxs-lookup"><span data-stu-id="6b841-137">Element</span></span>|<span data-ttu-id="6b841-138">Opis</span><span class="sxs-lookup"><span data-stu-id="6b841-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b841-139">\<Type></span><span class="sxs-lookup"><span data-stu-id="6b841-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="6b841-140">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6b841-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="6b841-141">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="6b841-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="6b841-142">Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6b841-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b841-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b841-143">Remarks</span></span>  
 <span data-ttu-id="6b841-144">Jeśli zasady zdarzeń nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania odpowiedniego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6b841-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b841-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b841-145">See also</span></span>
- [<span data-ttu-id="6b841-146">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6b841-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6b841-147">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6b841-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="6b841-148">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6b841-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
