---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 8fcb5ac0c552d1ac2e849c95a5c0757d0c142f3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926396"
---
# <a name="behaviors"></a><span data-ttu-id="d157b-101">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="d157b-101">\<behaviors></span></span>
<span data-ttu-id="d157b-102">Ten element definiuje dwie kolekcje podrzędne o `endpointBehaviors` nazwach i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="d157b-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="d157b-103">Każda kolekcja definiuje elementy zachowań używane odpowiednio przez punkty końcowe i usługi.</span><span class="sxs-lookup"><span data-stu-id="d157b-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="d157b-104">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d157b-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="d157b-105">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="d157b-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d157b-106">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d157b-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="d157b-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d157b-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d157b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d157b-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d157b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d157b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d157b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d157b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d157b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d157b-111">Attributes</span></span>  
 <span data-ttu-id="d157b-112">Brak</span><span class="sxs-lookup"><span data-stu-id="d157b-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d157b-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d157b-113">Child Elements</span></span>  
  
|<span data-ttu-id="d157b-114">Element</span><span class="sxs-lookup"><span data-stu-id="d157b-114">Element</span></span>|<span data-ttu-id="d157b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d157b-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d157b-116">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d157b-116">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="d157b-117">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowane dla określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d157b-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="d157b-118">\<> serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="d157b-118">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="d157b-119">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanego dla określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="d157b-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d157b-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d157b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d157b-121">Element</span><span class="sxs-lookup"><span data-stu-id="d157b-121">Element</span></span>|<span data-ttu-id="d157b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d157b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d157b-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d157b-123">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="d157b-124">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d157b-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d157b-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d157b-125">Remarks</span></span>  
 <span data-ttu-id="d157b-126">Możesz użyć elementu, `<remove>` aby usunąć określone zachowanie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d157b-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="d157b-127">W tym celu wystarczy podać nazwę zachowania do usunięcia w `name` atrybucie `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d157b-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="d157b-128">Można również użyć elementu, `<clear>` aby upewnić się, że kolekcja zachowań zaczyna się pusta przez wyczyszczenie całej zawartości kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d157b-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d157b-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d157b-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="d157b-130">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="d157b-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="d157b-131">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="d157b-131">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="d157b-132">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="d157b-132">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="d157b-133">Określanie zachowania środowiska uruchomieniowego usługi</span><span class="sxs-lookup"><span data-stu-id="d157b-133">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="d157b-134">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d157b-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
