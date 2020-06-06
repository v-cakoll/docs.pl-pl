---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: bcdd26f038b343040d81b0add83bf166a5e3151f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139687"
---
# \<behaviors>
<span data-ttu-id="0d66e-101">Ten element definiuje dwie kolekcje podrzędne o nazwach `endpointBehaviors` i `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="0d66e-101">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="0d66e-102">Każda kolekcja definiuje elementy zachowań używane odpowiednio przez punkty końcowe i usługi.</span><span class="sxs-lookup"><span data-stu-id="0d66e-102">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="0d66e-103">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0d66e-103">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="0d66e-104">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="0d66e-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0d66e-105">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0d66e-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="0d66e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d66e-106">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d66e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0d66e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0d66e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0d66e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d66e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0d66e-109">Attributes</span></span>  
 <span data-ttu-id="0d66e-110">Brak</span><span class="sxs-lookup"><span data-stu-id="0d66e-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0d66e-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0d66e-111">Child Elements</span></span>  
  
|<span data-ttu-id="0d66e-112">Element</span><span class="sxs-lookup"><span data-stu-id="0d66e-112">Element</span></span>|<span data-ttu-id="0d66e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0d66e-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="0d66e-114">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowane dla określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0d66e-114">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="0d66e-115">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanego dla określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="0d66e-115">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d66e-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0d66e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0d66e-117">Element</span><span class="sxs-lookup"><span data-stu-id="0d66e-117">Element</span></span>|<span data-ttu-id="0d66e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="0d66e-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="0d66e-119">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0d66e-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d66e-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d66e-120">Remarks</span></span>  
 <span data-ttu-id="0d66e-121">Możesz użyć elementu, `<remove>` Aby usunąć określone zachowanie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0d66e-121">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="0d66e-122">W tym celu wystarczy podać nazwę zachowania do usunięcia w `name` atrybucie `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0d66e-122">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="0d66e-123">Można również użyć elementu, `<clear>` Aby upewnić się, że kolekcja zachowań zaczyna się pusta przez wyczyszczenie całej zawartości kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0d66e-123">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d66e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d66e-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="0d66e-125">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="0d66e-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="0d66e-126">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="0d66e-126">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="0d66e-127">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="0d66e-127">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="0d66e-128">Określanie zachowania środowiska uruchomieniowego usługi</span><span class="sxs-lookup"><span data-stu-id="0d66e-128">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="0d66e-129">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0d66e-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
