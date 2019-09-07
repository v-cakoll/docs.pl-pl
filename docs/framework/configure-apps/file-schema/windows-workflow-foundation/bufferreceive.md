---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398836"
---
# <a name="bufferreceive"></a><span data-ttu-id="6754e-101">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="6754e-101">\<bufferReceive></span></span>
<span data-ttu-id="6754e-102">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="6754e-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="6754e-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6754e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6754e-104">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6754e-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="6754e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6754e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="6754e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6754e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="6754e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6754e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="6754e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bufferReceive >**</span><span class="sxs-lookup"><span data-stu-id="6754e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6754e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="6754e-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6754e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6754e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6754e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6754e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6754e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6754e-112">Attributes</span></span>  
  
|<span data-ttu-id="6754e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6754e-113">Attribute</span></span>|<span data-ttu-id="6754e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6754e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6754e-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="6754e-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="6754e-116">Liczba całkowita określająca maksymalną liczbę oczekujących komunikatów dopuszczalną dla każdego kanału.</span><span class="sxs-lookup"><span data-stu-id="6754e-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="6754e-117">Wartość domyślna to 512.</span><span class="sxs-lookup"><span data-stu-id="6754e-117">The default value is 512.</span></span> <span data-ttu-id="6754e-118">Ta właściwość ogranicza liczbę komunikatów poza kolejnością, może zostać odebrana przez usługę przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6754e-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6754e-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6754e-119">Child Elements</span></span>  
 <span data-ttu-id="6754e-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="6754e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6754e-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6754e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6754e-122">Element</span><span class="sxs-lookup"><span data-stu-id="6754e-122">Element</span></span>|<span data-ttu-id="6754e-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6754e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6754e-124">\<zachowanie > w \<usłudze serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6754e-124">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="6754e-125">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="6754e-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6754e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6754e-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
