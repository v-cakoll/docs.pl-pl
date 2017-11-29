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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 623ff924e171282c399bddcdc212a0606a3416d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="65c52-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="65c52-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="65c52-103">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="65c52-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="65c52-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="65c52-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="65c52-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="65c52-105">\<behaviors></span></span>  
<span data-ttu-id="65c52-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="65c52-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="65c52-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="65c52-107">\<behavior></span></span>  
<span data-ttu-id="65c52-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="65c52-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c52-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="65c52-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65c52-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="65c52-110">Attributes and Elements</span></span>  
 <span data-ttu-id="65c52-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="65c52-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65c52-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="65c52-112">Attributes</span></span>  
  
|<span data-ttu-id="65c52-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="65c52-113">Attribute</span></span>|<span data-ttu-id="65c52-114">Opis</span><span class="sxs-lookup"><span data-stu-id="65c52-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65c52-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="65c52-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="65c52-116">Liczba całkowita określająca maksymalną liczbę oczekujących komunikatów dopuszczalną dla każdego kanału.</span><span class="sxs-lookup"><span data-stu-id="65c52-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="65c52-117">Wartość domyślna to 512.</span><span class="sxs-lookup"><span data-stu-id="65c52-117">The default value is 512.</span></span> <span data-ttu-id="65c52-118">Ta właściwość ogranicza liczbę komunikatów poza kolejnością, może zostać odebrana przez usługę przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="65c52-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65c52-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="65c52-119">Child Elements</span></span>  
 <span data-ttu-id="65c52-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="65c52-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65c52-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="65c52-121">Parent Elements</span></span>  
  
|<span data-ttu-id="65c52-122">Element</span><span class="sxs-lookup"><span data-stu-id="65c52-122">Element</span></span>|<span data-ttu-id="65c52-123">Opis</span><span class="sxs-lookup"><span data-stu-id="65c52-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65c52-124">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="65c52-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="65c52-125">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="65c52-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65c52-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65c52-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
