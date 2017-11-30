---
title: '&lt;workflowUnhandledException&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b3e9450721de526aa489500f152a277acc52178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="782f0-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="782f0-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="782f0-103">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="782f0-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="782f0-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="782f0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="782f0-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="782f0-105">\<behaviors></span></span>  
<span data-ttu-id="782f0-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="782f0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="782f0-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="782f0-107">\<behavior></span></span>  
<span data-ttu-id="782f0-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="782f0-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="782f0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="782f0-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="782f0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="782f0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="782f0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="782f0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="782f0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="782f0-112">Attributes</span></span>  
  
|<span data-ttu-id="782f0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="782f0-113">Attribute</span></span>|<span data-ttu-id="782f0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="782f0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="782f0-115">Akcja</span><span class="sxs-lookup"><span data-stu-id="782f0-115">action</span></span>|<span data-ttu-id="782f0-116">Ciąg, który określa akcję, która ma zostać podjęta po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="782f0-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="782f0-117">Ten atrybut nie ma typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="782f0-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="782f0-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="782f0-118">Child Elements</span></span>  
 <span data-ttu-id="782f0-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="782f0-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="782f0-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="782f0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="782f0-121">Element</span><span class="sxs-lookup"><span data-stu-id="782f0-121">Element</span></span>|<span data-ttu-id="782f0-122">Opis</span><span class="sxs-lookup"><span data-stu-id="782f0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="782f0-123">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="782f0-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="782f0-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="782f0-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="782f0-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="782f0-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
