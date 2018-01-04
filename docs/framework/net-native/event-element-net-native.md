---
title: Element &lt;Event&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a37758ed497211ba0550666ec4857666041c5285
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lteventgt-element-net-native"></a><span data-ttu-id="68098-102">Element &lt;Event&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="68098-102">&lt;Event&gt; Element (.NET Native)</span></span>
<span data-ttu-id="68098-103">Zastosowanie zasad wykonywania odbicia do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="68098-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68098-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68098-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68098-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="68098-105">Attributes and Elements</span></span>  
 <span data-ttu-id="68098-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="68098-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68098-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="68098-107">Attributes</span></span>  
  
|<span data-ttu-id="68098-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="68098-108">Attribute</span></span>|<span data-ttu-id="68098-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="68098-109">Attribute type</span></span>|<span data-ttu-id="68098-110">Opis</span><span class="sxs-lookup"><span data-stu-id="68098-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="68098-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="68098-111">General</span></span>|<span data-ttu-id="68098-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="68098-112">Required attribute.</span></span> <span data-ttu-id="68098-113">Określa nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="68098-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="68098-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="68098-114">Reflection</span></span>|<span data-ttu-id="68098-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="68098-115">Optional attribute.</span></span> <span data-ttu-id="68098-116">Określa, czy wykonywania zapytania dotyczącego informacji o wyliczaniu zdarzenia, ale nie umożliwia dostępu dynamicznej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="68098-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="68098-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="68098-117">Reflection</span></span>|<span data-ttu-id="68098-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="68098-118">Optional attribute.</span></span> <span data-ttu-id="68098-119">Formanty środowiska uruchomieniowego dostęp do zdarzeń, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="68098-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="68098-120">Ta zasada zapewnia, że zdarzenia można obsługiwać dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="68098-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="68098-121">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="68098-121">Name attribute</span></span>  
  
|<span data-ttu-id="68098-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="68098-122">Value</span></span>|<span data-ttu-id="68098-123">Opis</span><span class="sxs-lookup"><span data-stu-id="68098-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68098-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="68098-124">*method_name*</span></span>|<span data-ttu-id="68098-125">Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="68098-125">The event name.</span></span> <span data-ttu-id="68098-126">Typ zdarzenia jest zdefiniowany przez nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="68098-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="68098-127">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="68098-127">All other attributes</span></span>  
  
|<span data-ttu-id="68098-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="68098-128">Value</span></span>|<span data-ttu-id="68098-129">Opis</span><span class="sxs-lookup"><span data-stu-id="68098-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68098-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="68098-130">*policy_setting*</span></span>|<span data-ttu-id="68098-131">Ustawienia do zastosowania dla tego typu zasad dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="68098-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="68098-132">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="68098-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="68098-133">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="68098-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68098-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="68098-134">Child Elements</span></span>  
 <span data-ttu-id="68098-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="68098-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68098-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="68098-136">Parent Elements</span></span>  
  
|<span data-ttu-id="68098-137">Element</span><span class="sxs-lookup"><span data-stu-id="68098-137">Element</span></span>|<span data-ttu-id="68098-138">Opis</span><span class="sxs-lookup"><span data-stu-id="68098-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68098-139">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="68098-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="68098-140">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="68098-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="68098-141">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="68098-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="68098-142">Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="68098-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68098-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68098-143">Remarks</span></span>  
 <span data-ttu-id="68098-144">Jeśli zasady zdarzeń nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="68098-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68098-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68098-145">See Also</span></span>  
 [<span data-ttu-id="68098-146">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="68098-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="68098-147">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="68098-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="68098-148">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="68098-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
