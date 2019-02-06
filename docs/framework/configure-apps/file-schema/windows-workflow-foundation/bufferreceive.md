---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 1e095e3da11277c6b7b3c24e98a769500e1a0c0b
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759538"
---
# <a name="bufferreceive"></a><span data-ttu-id="6a832-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="6a832-101">\<bufferReceive></span></span>
<span data-ttu-id="6a832-102">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="6a832-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="6a832-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6a832-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6a832-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="6a832-104">\<behaviors></span></span>  
<span data-ttu-id="6a832-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6a832-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="6a832-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="6a832-106">\<behavior></span></span>  
<span data-ttu-id="6a832-107">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="6a832-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a832-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a832-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a832-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a832-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6a832-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a832-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a832-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a832-111">Attributes</span></span>  
  
|<span data-ttu-id="6a832-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6a832-112">Attribute</span></span>|<span data-ttu-id="6a832-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6a832-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a832-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="6a832-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="6a832-115">Liczba całkowita określająca maksymalną liczbę oczekujących komunikatów dopuszczalną dla każdego kanału.</span><span class="sxs-lookup"><span data-stu-id="6a832-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="6a832-116">Wartość domyślna to 512.</span><span class="sxs-lookup"><span data-stu-id="6a832-116">The default value is 512.</span></span> <span data-ttu-id="6a832-117">Ta właściwość ogranicza liczbę komunikatów poza kolejnością, może zostać odebrana przez usługę przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6a832-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a832-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a832-118">Child Elements</span></span>  
 <span data-ttu-id="6a832-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a832-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a832-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a832-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6a832-121">Element</span><span class="sxs-lookup"><span data-stu-id="6a832-121">Element</span></span>|<span data-ttu-id="6a832-122">Opis</span><span class="sxs-lookup"><span data-stu-id="6a832-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a832-123">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6a832-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="6a832-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="6a832-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a832-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a832-125">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
