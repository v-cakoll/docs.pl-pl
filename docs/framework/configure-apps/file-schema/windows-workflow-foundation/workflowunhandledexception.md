---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: cfe3350ac42d1e0e837b79f25753f62dc2051dd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096254"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="92f38-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="92f38-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="92f38-102">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="92f38-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="92f38-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="92f38-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="92f38-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="92f38-104">\<behaviors></span></span>  
<span data-ttu-id="92f38-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="92f38-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="92f38-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="92f38-106">\<behavior></span></span>  
<span data-ttu-id="92f38-107">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="92f38-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f38-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="92f38-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92f38-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="92f38-109">Attributes and Elements</span></span>  
 <span data-ttu-id="92f38-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="92f38-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92f38-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="92f38-111">Attributes</span></span>  
  
|<span data-ttu-id="92f38-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="92f38-112">Attribute</span></span>|<span data-ttu-id="92f38-113">Opis</span><span class="sxs-lookup"><span data-stu-id="92f38-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92f38-114">Akcja</span><span class="sxs-lookup"><span data-stu-id="92f38-114">action</span></span>|<span data-ttu-id="92f38-115">Ciąg, który określa akcję, która ma zostać podjęta po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="92f38-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="92f38-116">Ten atrybut jest typu</span><span class="sxs-lookup"><span data-stu-id="92f38-116">This attribute is of type</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>|  
  
### <a name="child-elements"></a><span data-ttu-id="92f38-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="92f38-117">Child Elements</span></span>  
 <span data-ttu-id="92f38-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="92f38-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92f38-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92f38-119">Parent Elements</span></span>  
  
|<span data-ttu-id="92f38-120">Element</span><span class="sxs-lookup"><span data-stu-id="92f38-120">Element</span></span>|<span data-ttu-id="92f38-121">Opis</span><span class="sxs-lookup"><span data-stu-id="92f38-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92f38-122">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="92f38-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="92f38-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="92f38-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92f38-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92f38-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
