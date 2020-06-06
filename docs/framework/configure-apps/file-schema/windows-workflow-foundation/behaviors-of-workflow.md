---
title: <behaviors>przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398876"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="df472-102">\<behaviors>przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="df472-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="df472-103">Ten element zawiera kolekcję **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="df472-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="df472-104">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="df472-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="df472-105">Każdy element zachowania jest identyfikowany przez jego unikatowy atrybut **nazwy** .</span><span class="sxs-lookup"><span data-stu-id="df472-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="df472-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="df472-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df472-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="df472-107">Attributes and Elements</span></span>  
 <span data-ttu-id="df472-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="df472-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df472-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="df472-109">Attributes</span></span>  
 <span data-ttu-id="df472-110">Brak</span><span class="sxs-lookup"><span data-stu-id="df472-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="df472-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="df472-111">Child Elements</span></span>  
  
|<span data-ttu-id="df472-112">Element</span><span class="sxs-lookup"><span data-stu-id="df472-112">Element</span></span>|<span data-ttu-id="df472-113">Opis</span><span class="sxs-lookup"><span data-stu-id="df472-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="df472-114">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanych na potrzeby usługi określonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="df472-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df472-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="df472-115">Parent Elements</span></span>  
  
|<span data-ttu-id="df472-116">Element</span><span class="sxs-lookup"><span data-stu-id="df472-116">Element</span></span>|<span data-ttu-id="df472-117">Opis</span><span class="sxs-lookup"><span data-stu-id="df472-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="df472-118">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="df472-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df472-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df472-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="df472-120">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="df472-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
