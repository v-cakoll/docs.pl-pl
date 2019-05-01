---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 360d26fda964fa33640e833ad22dab7e06e153f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790263"
---
# <a name="bufferreceive"></a><span data-ttu-id="81605-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="81605-101">\<bufferReceive></span></span>
<span data-ttu-id="81605-102">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="81605-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="81605-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="81605-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="81605-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="81605-104">\<behaviors></span></span>  
<span data-ttu-id="81605-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="81605-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="81605-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="81605-106">\<behavior></span></span>  
<span data-ttu-id="81605-107">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="81605-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81605-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="81605-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81605-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="81605-109">Attributes and Elements</span></span>  
 <span data-ttu-id="81605-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="81605-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81605-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="81605-111">Attributes</span></span>  
  
|<span data-ttu-id="81605-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="81605-112">Attribute</span></span>|<span data-ttu-id="81605-113">Opis</span><span class="sxs-lookup"><span data-stu-id="81605-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81605-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="81605-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="81605-115">Liczba całkowita określająca maksymalną liczbę oczekujących komunikatów dopuszczalną dla każdego kanału.</span><span class="sxs-lookup"><span data-stu-id="81605-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="81605-116">Wartość domyślna to 512.</span><span class="sxs-lookup"><span data-stu-id="81605-116">The default value is 512.</span></span> <span data-ttu-id="81605-117">Ta właściwość ogranicza liczbę komunikatów poza kolejnością, może zostać odebrana przez usługę przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81605-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81605-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="81605-118">Child Elements</span></span>  
 <span data-ttu-id="81605-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="81605-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81605-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="81605-120">Parent Elements</span></span>  
  
|<span data-ttu-id="81605-121">Element</span><span class="sxs-lookup"><span data-stu-id="81605-121">Element</span></span>|<span data-ttu-id="81605-122">Opis</span><span class="sxs-lookup"><span data-stu-id="81605-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81605-123">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="81605-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="81605-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="81605-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81605-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81605-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
