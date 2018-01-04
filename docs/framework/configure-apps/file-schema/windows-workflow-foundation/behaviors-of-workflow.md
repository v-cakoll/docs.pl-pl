---
title: "&lt;zachowania&gt; przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c1bf4beb244b72d2fe3d82d749ff6ae6723baf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="1d57f-102">&lt;zachowania&gt; przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1d57f-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="1d57f-103">Ten element zawiera **serviceBehaviors** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1d57f-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="1d57f-104">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1d57f-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="1d57f-105">Każdy element zachowanie jest identyfikowany przez jego unikatowy **nazwa** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1d57f-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="1d57f-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1d57f-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d57f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d57f-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d57f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d57f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1d57f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d57f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d57f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d57f-110">Attributes</span></span>  
 <span data-ttu-id="1d57f-111">Brak</span><span class="sxs-lookup"><span data-stu-id="1d57f-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d57f-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d57f-112">Child Elements</span></span>  
  
|<span data-ttu-id="1d57f-113">Element</span><span class="sxs-lookup"><span data-stu-id="1d57f-113">Element</span></span>|<span data-ttu-id="1d57f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1d57f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d57f-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1d57f-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="1d57f-116">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanych na potrzeby usługi określonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1d57f-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d57f-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d57f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1d57f-118">Element</span><span class="sxs-lookup"><span data-stu-id="1d57f-118">Element</span></span>|<span data-ttu-id="1d57f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1d57f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d57f-120">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1d57f-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="1d57f-121">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1d57f-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d57f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d57f-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="1d57f-123">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="1d57f-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
