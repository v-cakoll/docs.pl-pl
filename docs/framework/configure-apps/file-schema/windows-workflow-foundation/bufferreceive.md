---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398836"
---
# \<bufferReceive>
<span data-ttu-id="aa2ad-101">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="aa2ad-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="aa2ad-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa2ad-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa2ad-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aa2ad-103">Attributes and Elements</span></span>  
 <span data-ttu-id="aa2ad-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aa2ad-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa2ad-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aa2ad-105">Attributes</span></span>  
  
|<span data-ttu-id="aa2ad-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aa2ad-106">Attribute</span></span>|<span data-ttu-id="aa2ad-107">Opis</span><span class="sxs-lookup"><span data-stu-id="aa2ad-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa2ad-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="aa2ad-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="aa2ad-109">Liczba całkowita określająca maksymalną liczbę oczekujących komunikatów dopuszczalną dla każdego kanału.</span><span class="sxs-lookup"><span data-stu-id="aa2ad-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="aa2ad-110">Wartość domyślna to 512.</span><span class="sxs-lookup"><span data-stu-id="aa2ad-110">The default value is 512.</span></span> <span data-ttu-id="aa2ad-111">Ta właściwość ogranicza liczbę komunikatów poza kolejnością, może zostać odebrana przez usługę przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="aa2ad-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa2ad-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aa2ad-112">Child Elements</span></span>  
 <span data-ttu-id="aa2ad-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="aa2ad-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa2ad-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aa2ad-114">Parent Elements</span></span>  
  
|<span data-ttu-id="aa2ad-115">Element</span><span class="sxs-lookup"><span data-stu-id="aa2ad-115">Element</span></span>|<span data-ttu-id="aa2ad-116">Opis</span><span class="sxs-lookup"><span data-stu-id="aa2ad-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa2ad-117">\<behavior>z\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="aa2ad-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="aa2ad-118">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="aa2ad-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa2ad-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa2ad-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
