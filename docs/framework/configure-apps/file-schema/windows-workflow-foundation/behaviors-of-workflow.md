---
title: <behaviors> przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: b7c5cf93a82ac88c25f9c478ad52cf41eb6f6d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129210"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="02756-102">\<zachowania > przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="02756-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="02756-103">Ten element zawiera **serviceBehaviors** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="02756-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="02756-104">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="02756-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="02756-105">Każdy element zachowanie jest określony przez jego unikatowy **nazwa** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="02756-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="02756-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="02756-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02756-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="02756-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02756-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="02756-108">Attributes and Elements</span></span>  
 <span data-ttu-id="02756-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="02756-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02756-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="02756-110">Attributes</span></span>  
 <span data-ttu-id="02756-111">Brak</span><span class="sxs-lookup"><span data-stu-id="02756-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02756-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="02756-112">Child Elements</span></span>  
  
|<span data-ttu-id="02756-113">Element</span><span class="sxs-lookup"><span data-stu-id="02756-113">Element</span></span>|<span data-ttu-id="02756-114">Opis</span><span class="sxs-lookup"><span data-stu-id="02756-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02756-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="02756-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="02756-116">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanych na potrzeby usługi określonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="02756-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02756-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="02756-117">Parent Elements</span></span>  
  
|<span data-ttu-id="02756-118">Element</span><span class="sxs-lookup"><span data-stu-id="02756-118">Element</span></span>|<span data-ttu-id="02756-119">Opis</span><span class="sxs-lookup"><span data-stu-id="02756-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02756-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="02756-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="02756-121">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="02756-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02756-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02756-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="02756-123">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="02756-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
