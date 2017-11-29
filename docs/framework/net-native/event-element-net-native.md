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
ms.openlocfilehash: dabb780e24d1316a3d736f7d1f3da249704a4ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lteventgt-element-net-native"></a><span data-ttu-id="fb689-102">Element &lt;Event&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="fb689-102">&lt;Event&gt; Element (.NET Native)</span></span>
<span data-ttu-id="fb689-103">Zastosowanie zasad wykonywania odbicia do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fb689-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb689-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb689-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb689-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fb689-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fb689-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fb689-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb689-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb689-107">Attributes</span></span>  
  
|<span data-ttu-id="fb689-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fb689-108">Attribute</span></span>|<span data-ttu-id="fb689-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="fb689-109">Attribute type</span></span>|<span data-ttu-id="fb689-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fb689-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="fb689-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="fb689-111">General</span></span>|<span data-ttu-id="fb689-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fb689-112">Required attribute.</span></span> <span data-ttu-id="fb689-113">Określa nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fb689-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="fb689-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="fb689-114">Reflection</span></span>|<span data-ttu-id="fb689-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fb689-115">Optional attribute.</span></span> <span data-ttu-id="fb689-116">Określa, czy wykonywania zapytania dotyczącego informacji o wyliczaniu zdarzenia, ale nie umożliwia dostępu dynamicznej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fb689-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="fb689-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="fb689-117">Reflection</span></span>|<span data-ttu-id="fb689-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fb689-118">Optional attribute.</span></span> <span data-ttu-id="fb689-119">Formanty środowiska uruchomieniowego dostęp do zdarzeń, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="fb689-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="fb689-120">Ta zasada zapewnia, że zdarzenia można obsługiwać dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fb689-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="fb689-121">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="fb689-121">Name attribute</span></span>  
  
|<span data-ttu-id="fb689-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="fb689-122">Value</span></span>|<span data-ttu-id="fb689-123">Opis</span><span class="sxs-lookup"><span data-stu-id="fb689-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb689-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="fb689-124">*method_name*</span></span>|<span data-ttu-id="fb689-125">Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fb689-125">The event name.</span></span> <span data-ttu-id="fb689-126">Typ zdarzenia jest zdefiniowany przez nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="fb689-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="fb689-127">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb689-127">All other attributes</span></span>  
  
|<span data-ttu-id="fb689-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="fb689-128">Value</span></span>|<span data-ttu-id="fb689-129">Opis</span><span class="sxs-lookup"><span data-stu-id="fb689-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb689-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="fb689-130">*policy_setting*</span></span>|<span data-ttu-id="fb689-131">Ustawienia do zastosowania dla tego typu zasad dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fb689-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="fb689-132">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="fb689-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="fb689-133">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="fb689-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb689-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fb689-134">Child Elements</span></span>  
 <span data-ttu-id="fb689-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="fb689-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb689-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fb689-136">Parent Elements</span></span>  
  
|<span data-ttu-id="fb689-137">Element</span><span class="sxs-lookup"><span data-stu-id="fb689-137">Element</span></span>|<span data-ttu-id="fb689-138">Opis</span><span class="sxs-lookup"><span data-stu-id="fb689-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb689-139">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="fb689-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="fb689-140">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="fb689-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="fb689-141">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="fb689-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="fb689-142">Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="fb689-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb689-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb689-143">Remarks</span></span>  
 <span data-ttu-id="fb689-144">Jeśli zasady zdarzeń nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fb689-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb689-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb689-145">See Also</span></span>  
 [<span data-ttu-id="fb689-146">Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="fb689-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="fb689-147">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fb689-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="fb689-148">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fb689-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
