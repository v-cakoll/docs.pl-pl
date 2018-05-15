---
title: '&lt;zachowania&gt; przepływu pracy'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 762fd1ff0de7980848ac3921706f406932c7f35d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="611ae-102">&lt;zachowania&gt; przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="611ae-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="611ae-103">Ten element zawiera **serviceBehaviors** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="611ae-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="611ae-104">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="611ae-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="611ae-105">Każdy element zachowanie jest identyfikowany przez jego unikatowy **nazwa** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="611ae-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="611ae-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="611ae-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="611ae-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="611ae-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="611ae-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="611ae-108">Attributes and Elements</span></span>  
 <span data-ttu-id="611ae-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="611ae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="611ae-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="611ae-110">Attributes</span></span>  
 <span data-ttu-id="611ae-111">Brak</span><span class="sxs-lookup"><span data-stu-id="611ae-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="611ae-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="611ae-112">Child Elements</span></span>  
  
|<span data-ttu-id="611ae-113">Element</span><span class="sxs-lookup"><span data-stu-id="611ae-113">Element</span></span>|<span data-ttu-id="611ae-114">Opis</span><span class="sxs-lookup"><span data-stu-id="611ae-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="611ae-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="611ae-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="611ae-116">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanych na potrzeby usługi określonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="611ae-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="611ae-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="611ae-117">Parent Elements</span></span>  
  
|<span data-ttu-id="611ae-118">Element</span><span class="sxs-lookup"><span data-stu-id="611ae-118">Element</span></span>|<span data-ttu-id="611ae-119">Opis</span><span class="sxs-lookup"><span data-stu-id="611ae-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="611ae-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="611ae-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="611ae-121">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="611ae-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="611ae-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="611ae-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="611ae-123">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="611ae-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
