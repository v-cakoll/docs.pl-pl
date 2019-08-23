---
title: <behaviors>przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 7dd3b0b20c9d7accd80a85b3693e67ffc9b729e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945995"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="79de3-102">\<> zachowań przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="79de3-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="79de3-103">Ten element zawiera kolekcję serviceBehaviors.</span><span class="sxs-lookup"><span data-stu-id="79de3-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="79de3-104">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="79de3-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="79de3-105">Każdy element zachowania jest identyfikowany przez jego unikatowy atrybut **nazwy** .</span><span class="sxs-lookup"><span data-stu-id="79de3-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="79de3-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79de3-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79de3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="79de3-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79de3-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="79de3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="79de3-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="79de3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79de3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="79de3-110">Attributes</span></span>  
 <span data-ttu-id="79de3-111">Brak</span><span class="sxs-lookup"><span data-stu-id="79de3-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79de3-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="79de3-112">Child Elements</span></span>  
  
|<span data-ttu-id="79de3-113">Element</span><span class="sxs-lookup"><span data-stu-id="79de3-113">Element</span></span>|<span data-ttu-id="79de3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="79de3-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79de3-115">\<> serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="79de3-115">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="79de3-116">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanych na potrzeby usługi określonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="79de3-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79de3-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="79de3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="79de3-118">Element</span><span class="sxs-lookup"><span data-stu-id="79de3-118">Element</span></span>|<span data-ttu-id="79de3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="79de3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79de3-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="79de3-120">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="79de3-121">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="79de3-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79de3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79de3-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="79de3-123">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="79de3-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
