---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: a87966f643fe46d0ef69f843dc306151ca7c18bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400597"
---
# <a name="behaviors"></a><span data-ttu-id="97c95-101">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="97c95-101">\<behaviors></span></span>
<span data-ttu-id="97c95-102">Ten element definiuje dwie kolekcje podrzędne o `endpointBehaviors` nazwach i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="97c95-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="97c95-103">Każda kolekcja definiuje elementy zachowań używane odpowiednio przez punkty końcowe i usługi.</span><span class="sxs-lookup"><span data-stu-id="97c95-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="97c95-104">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="97c95-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="97c95-105">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="97c95-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="97c95-106">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="97c95-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
<span data-ttu-id="97c95-107">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="97c95-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="97c95-108">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="97c95-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="97c95-109">&nbsp;&nbsp;&nbsp;&nbsp; **\<> zachowań**</span><span class="sxs-lookup"><span data-stu-id="97c95-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c95-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="97c95-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97c95-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="97c95-111">Attributes and Elements</span></span>  
 <span data-ttu-id="97c95-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="97c95-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97c95-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="97c95-113">Attributes</span></span>  
 <span data-ttu-id="97c95-114">Brak</span><span class="sxs-lookup"><span data-stu-id="97c95-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="97c95-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="97c95-115">Child Elements</span></span>  
  
|<span data-ttu-id="97c95-116">Element</span><span class="sxs-lookup"><span data-stu-id="97c95-116">Element</span></span>|<span data-ttu-id="97c95-117">Opis</span><span class="sxs-lookup"><span data-stu-id="97c95-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97c95-118">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="97c95-118">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="97c95-119">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowane dla określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="97c95-119">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="97c95-120">\<> serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="97c95-120">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="97c95-121">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanego dla określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="97c95-121">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97c95-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="97c95-122">Parent Elements</span></span>  
  
|<span data-ttu-id="97c95-123">Element</span><span class="sxs-lookup"><span data-stu-id="97c95-123">Element</span></span>|<span data-ttu-id="97c95-124">Opis</span><span class="sxs-lookup"><span data-stu-id="97c95-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97c95-125">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="97c95-125">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="97c95-126">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="97c95-126">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97c95-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97c95-127">Remarks</span></span>  
 <span data-ttu-id="97c95-128">Możesz użyć elementu, `<remove>` aby usunąć określone zachowanie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="97c95-128">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="97c95-129">W tym celu wystarczy podać nazwę zachowania do usunięcia w `name` atrybucie `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="97c95-129">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="97c95-130">Można również użyć elementu, `<clear>` aby upewnić się, że kolekcja zachowań zaczyna się pusta przez wyczyszczenie całej zawartości kolekcji.</span><span class="sxs-lookup"><span data-stu-id="97c95-130">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c95-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97c95-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="97c95-132">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="97c95-132">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="97c95-133">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="97c95-133">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="97c95-134">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="97c95-134">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="97c95-135">Określanie zachowania środowiska uruchomieniowego usługi</span><span class="sxs-lookup"><span data-stu-id="97c95-135">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="97c95-136">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="97c95-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
