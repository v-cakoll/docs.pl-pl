---
title: '&lt;bufferReceive&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b5b6176e7c5b982bc9f41b13c669af104bf784f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="996f5-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="996f5-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="996f5-103">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="996f5-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="996f5-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="996f5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="996f5-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="996f5-105">\<behaviors></span></span>  
<span data-ttu-id="996f5-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="996f5-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="996f5-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="996f5-107">\<behavior></span></span>  
<span data-ttu-id="996f5-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="996f5-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996f5-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="996f5-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="996f5-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="996f5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="996f5-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="996f5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="996f5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="996f5-112">Attributes</span></span>  
  
|<span data-ttu-id="996f5-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="996f5-113">Attribute</span></span>|<span data-ttu-id="996f5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="996f5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="996f5-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="996f5-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="996f5-116">Liczba całkowita określająca maksymalną liczbę oczekujących komunikatów dopuszczalną dla każdego kanału.</span><span class="sxs-lookup"><span data-stu-id="996f5-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="996f5-117">Wartość domyślna to 512.</span><span class="sxs-lookup"><span data-stu-id="996f5-117">The default value is 512.</span></span> <span data-ttu-id="996f5-118">Ta właściwość ogranicza liczbę komunikatów poza kolejnością, może zostać odebrana przez usługę przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="996f5-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="996f5-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="996f5-119">Child Elements</span></span>  
 <span data-ttu-id="996f5-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="996f5-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="996f5-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="996f5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="996f5-122">Element</span><span class="sxs-lookup"><span data-stu-id="996f5-122">Element</span></span>|<span data-ttu-id="996f5-123">Opis</span><span class="sxs-lookup"><span data-stu-id="996f5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="996f5-124">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="996f5-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="996f5-125">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="996f5-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="996f5-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="996f5-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
