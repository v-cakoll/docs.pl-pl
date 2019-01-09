---
title: '&lt;Zachowania&gt;'
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 4396aefd982dd29c6a9c9f2be9f2af43d00671b2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150100"
---
# <a name="ltbehaviorsgt"></a><span data-ttu-id="99e4e-102">&lt;Zachowania&gt;</span><span class="sxs-lookup"><span data-stu-id="99e4e-102">&lt;behaviors&gt;</span></span>
<span data-ttu-id="99e4e-103">Ten element definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="99e4e-103">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="99e4e-104">Każdej kolekcji definiuje zachowanie elementy używane przez punkty końcowe i usługi, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="99e4e-104">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="99e4e-105">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="99e4e-105">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="99e4e-106">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="99e4e-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="99e4e-107">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="99e4e-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="99e4e-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="99e4e-108">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99e4e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="99e4e-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99e4e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="99e4e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="99e4e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="99e4e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99e4e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="99e4e-112">Attributes</span></span>  
 <span data-ttu-id="99e4e-113">Brak</span><span class="sxs-lookup"><span data-stu-id="99e4e-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99e4e-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="99e4e-114">Child Elements</span></span>  
  
|<span data-ttu-id="99e4e-115">Element</span><span class="sxs-lookup"><span data-stu-id="99e4e-115">Element</span></span>|<span data-ttu-id="99e4e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="99e4e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99e4e-117">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="99e4e-117">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="99e4e-118">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowane dla określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="99e4e-118">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="99e4e-119">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="99e4e-119">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="99e4e-120">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanego dla określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="99e4e-120">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99e4e-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="99e4e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="99e4e-122">Element</span><span class="sxs-lookup"><span data-stu-id="99e4e-122">Element</span></span>|<span data-ttu-id="99e4e-123">Opis</span><span class="sxs-lookup"><span data-stu-id="99e4e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99e4e-124">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="99e4e-124">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="99e4e-125">Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="99e4e-125">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99e4e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99e4e-126">Remarks</span></span>  
 <span data-ttu-id="99e4e-127">Możesz użyć `<remove>` elementu do usunięcia określone zachowanie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="99e4e-127">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="99e4e-128">Aby to zrobić, po prostu podać nazwę zachowania do usunięcia w `name` atrybutu `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="99e4e-128">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="99e4e-129">Można również użyć `<clear>` elementu, aby upewnić się, czy zbieranie zachowanie rozpoczyna się puste, czyszcząc się całą zawartość kolekcji.</span><span class="sxs-lookup"><span data-stu-id="99e4e-129">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99e4e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99e4e-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="99e4e-131">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="99e4e-131">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 [<span data-ttu-id="99e4e-132">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="99e4e-132">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="99e4e-133">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="99e4e-133">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="99e4e-134">Określanie zachowania środowiska uruchomieniowego usługi</span><span class="sxs-lookup"><span data-stu-id="99e4e-134">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)  
 [<span data-ttu-id="99e4e-135">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="99e4e-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
