---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: c46d1fb9eb853e57c7ad1b97eb9a22556cdfb7d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913098"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="432b4-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="432b4-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="432b4-102">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="432b4-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="432b4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="432b4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="432b4-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="432b4-104">\<behaviors></span></span>  
<span data-ttu-id="432b4-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="432b4-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="432b4-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="432b4-106">\<behavior></span></span>  
<span data-ttu-id="432b4-107">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="432b4-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="432b4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="432b4-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="432b4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="432b4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="432b4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="432b4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="432b4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="432b4-111">Attributes</span></span>  
  
|<span data-ttu-id="432b4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="432b4-112">Attribute</span></span>|<span data-ttu-id="432b4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="432b4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="432b4-114">Akcja</span><span class="sxs-lookup"><span data-stu-id="432b4-114">action</span></span>|<span data-ttu-id="432b4-115">Ciąg, który określa akcję, która ma zostać podjęta po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="432b4-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="432b4-116">Ten atrybut nie ma typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="432b4-116">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="432b4-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="432b4-117">Child Elements</span></span>  
 <span data-ttu-id="432b4-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="432b4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="432b4-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="432b4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="432b4-120">Element</span><span class="sxs-lookup"><span data-stu-id="432b4-120">Element</span></span>|<span data-ttu-id="432b4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="432b4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="432b4-122">\<zachowanie > w \<usłudze serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="432b4-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="432b4-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="432b4-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="432b4-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="432b4-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
