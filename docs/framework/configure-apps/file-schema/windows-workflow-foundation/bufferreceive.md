---
title: '&lt;bufferReceive&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 07d5b66b14d9495808f972734cdce4476efaefde
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766839"
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="fdcdb-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="fdcdb-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="fdcdb-103">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="fdcdb-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="fdcdb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fdcdb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fdcdb-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="fdcdb-105">\<behaviors></span></span>  
<span data-ttu-id="fdcdb-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fdcdb-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fdcdb-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="fdcdb-107">\<behavior></span></span>  
<span data-ttu-id="fdcdb-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="fdcdb-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdcdb-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdcdb-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdcdb-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fdcdb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fdcdb-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fdcdb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdcdb-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fdcdb-112">Attributes</span></span>  
  
|<span data-ttu-id="fdcdb-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fdcdb-113">Attribute</span></span>|<span data-ttu-id="fdcdb-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fdcdb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fdcdb-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="fdcdb-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="fdcdb-116">Liczba całkowita określająca maksymalną liczbę oczekujących komunikatów dopuszczalną dla każdego kanału.</span><span class="sxs-lookup"><span data-stu-id="fdcdb-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="fdcdb-117">Wartość domyślna to 512.</span><span class="sxs-lookup"><span data-stu-id="fdcdb-117">The default value is 512.</span></span> <span data-ttu-id="fdcdb-118">Ta właściwość ogranicza liczbę komunikatów poza kolejnością, może zostać odebrana przez usługę przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fdcdb-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdcdb-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fdcdb-119">Child Elements</span></span>  
 <span data-ttu-id="fdcdb-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="fdcdb-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdcdb-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fdcdb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fdcdb-122">Element</span><span class="sxs-lookup"><span data-stu-id="fdcdb-122">Element</span></span>|<span data-ttu-id="fdcdb-123">Opis</span><span class="sxs-lookup"><span data-stu-id="fdcdb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdcdb-124">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fdcdb-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="fdcdb-125">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="fdcdb-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdcdb-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdcdb-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
