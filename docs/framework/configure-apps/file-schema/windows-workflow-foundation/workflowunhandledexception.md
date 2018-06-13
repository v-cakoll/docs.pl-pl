---
title: '&lt;workflowUnhandledException&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: d9db6ecc2e95e0d1ec5738f1d2f4a09a89c57f21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755139"
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="71a2a-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="71a2a-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="71a2a-103">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="71a2a-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="71a2a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="71a2a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="71a2a-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="71a2a-105">\<behaviors></span></span>  
<span data-ttu-id="71a2a-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="71a2a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="71a2a-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="71a2a-107">\<behavior></span></span>  
<span data-ttu-id="71a2a-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="71a2a-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71a2a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="71a2a-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71a2a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="71a2a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="71a2a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="71a2a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71a2a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="71a2a-112">Attributes</span></span>  
  
|<span data-ttu-id="71a2a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="71a2a-113">Attribute</span></span>|<span data-ttu-id="71a2a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="71a2a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71a2a-115">Akcja</span><span class="sxs-lookup"><span data-stu-id="71a2a-115">action</span></span>|<span data-ttu-id="71a2a-116">Ciąg, który określa akcję, która ma zostać podjęta po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="71a2a-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="71a2a-117">Ten atrybut nie ma typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="71a2a-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71a2a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="71a2a-118">Child Elements</span></span>  
 <span data-ttu-id="71a2a-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="71a2a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71a2a-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="71a2a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="71a2a-121">Element</span><span class="sxs-lookup"><span data-stu-id="71a2a-121">Element</span></span>|<span data-ttu-id="71a2a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="71a2a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71a2a-123">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="71a2a-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="71a2a-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="71a2a-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71a2a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71a2a-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
