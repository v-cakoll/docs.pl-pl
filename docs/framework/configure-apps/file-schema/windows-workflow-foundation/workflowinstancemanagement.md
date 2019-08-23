---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: a22c72b7a683e3ecab4344c92e7d835a184a58d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947159"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="ec792-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="ec792-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="ec792-102">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="ec792-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="ec792-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ec792-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ec792-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="ec792-104">\<behaviors></span></span>  
<span data-ttu-id="ec792-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ec792-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ec792-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="ec792-106">\<behavior></span></span>  
<span data-ttu-id="ec792-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="ec792-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec792-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec792-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec792-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ec792-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ec792-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ec792-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec792-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ec792-111">Attributes</span></span>  
  
|<span data-ttu-id="ec792-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ec792-112">Attribute</span></span>|<span data-ttu-id="ec792-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ec792-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec792-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="ec792-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="ec792-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ec792-115">Child Elements</span></span>  
 <span data-ttu-id="ec792-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="ec792-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec792-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ec792-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ec792-118">Element</span><span class="sxs-lookup"><span data-stu-id="ec792-118">Element</span></span>|<span data-ttu-id="ec792-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ec792-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec792-120">\<zachowanie > w \<usłudze serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ec792-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="ec792-121">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="ec792-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec792-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec792-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
