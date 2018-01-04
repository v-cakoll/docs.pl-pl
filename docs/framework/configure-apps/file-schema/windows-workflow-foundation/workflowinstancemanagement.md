---
title: '&lt;workflowInstanceManagement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3be696133bff5c1fc8858ab31093866ed05c98a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="1d57b-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="1d57b-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="1d57b-103">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="1d57b-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="1d57b-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1d57b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d57b-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="1d57b-105">\<behaviors></span></span>  
<span data-ttu-id="1d57b-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1d57b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1d57b-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="1d57b-107">\<behavior></span></span>  
<span data-ttu-id="1d57b-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="1d57b-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d57b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d57b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d57b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d57b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1d57b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d57b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d57b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d57b-112">Attributes</span></span>  
  
|<span data-ttu-id="1d57b-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1d57b-113">Attribute</span></span>|<span data-ttu-id="1d57b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1d57b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d57b-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="1d57b-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="1d57b-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d57b-116">Child Elements</span></span>  
 <span data-ttu-id="1d57b-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="1d57b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d57b-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d57b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1d57b-119">Element</span><span class="sxs-lookup"><span data-stu-id="1d57b-119">Element</span></span>|<span data-ttu-id="1d57b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1d57b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d57b-121">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1d57b-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="1d57b-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="1d57b-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d57b-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d57b-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
