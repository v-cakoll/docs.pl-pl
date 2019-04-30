---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 108c349a44ed3ac902652f86241c1e96a622549b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701232"
---
# <a name="behaviors"></a><span data-ttu-id="abf3c-101">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="abf3c-101">\<behaviors></span></span>
<span data-ttu-id="abf3c-102">Ten element definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="abf3c-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="abf3c-103">Każdej kolekcji definiuje zachowanie elementy używane przez punkty końcowe i usługi, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="abf3c-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="abf3c-104">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="abf3c-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="abf3c-105">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="abf3c-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="abf3c-106">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="abf3c-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="abf3c-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="abf3c-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf3c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="abf3c-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abf3c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="abf3c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="abf3c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="abf3c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abf3c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="abf3c-111">Attributes</span></span>  
 <span data-ttu-id="abf3c-112">Brak</span><span class="sxs-lookup"><span data-stu-id="abf3c-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="abf3c-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="abf3c-113">Child Elements</span></span>  
  
|<span data-ttu-id="abf3c-114">Element</span><span class="sxs-lookup"><span data-stu-id="abf3c-114">Element</span></span>|<span data-ttu-id="abf3c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="abf3c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abf3c-116">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="abf3c-116">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="abf3c-117">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowane dla określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="abf3c-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="abf3c-118">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="abf3c-118">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="abf3c-119">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanego dla określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3c-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="abf3c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="abf3c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="abf3c-121">Element</span><span class="sxs-lookup"><span data-stu-id="abf3c-121">Element</span></span>|<span data-ttu-id="abf3c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="abf3c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abf3c-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="abf3c-123">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="abf3c-124">Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="abf3c-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abf3c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abf3c-125">Remarks</span></span>  
 <span data-ttu-id="abf3c-126">Możesz użyć `<remove>` elementu do usunięcia określone zachowanie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="abf3c-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="abf3c-127">Aby to zrobić, po prostu podać nazwę zachowania do usunięcia w `name` atrybutu `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="abf3c-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="abf3c-128">Można również użyć `<clear>` elementu, aby upewnić się, czy zbieranie zachowanie rozpoczyna się puste, czyszcząc się całą zawartość kolekcji.</span><span class="sxs-lookup"><span data-stu-id="abf3c-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf3c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abf3c-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="abf3c-130">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="abf3c-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="abf3c-131">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="abf3c-131">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="abf3c-132">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="abf3c-132">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="abf3c-133">Określanie zachowania środowiska uruchomieniowego usługi</span><span class="sxs-lookup"><span data-stu-id="abf3c-133">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="abf3c-134">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="abf3c-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
