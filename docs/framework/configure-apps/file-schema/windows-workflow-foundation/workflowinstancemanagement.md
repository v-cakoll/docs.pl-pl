---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 98bc1b24da6e65a11a39d133057c1bb55b003a58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61613466"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="01578-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="01578-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="01578-102">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="01578-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="01578-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="01578-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="01578-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="01578-104">\<behaviors></span></span>  
<span data-ttu-id="01578-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="01578-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="01578-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="01578-106">\<behavior></span></span>  
<span data-ttu-id="01578-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="01578-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01578-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="01578-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01578-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="01578-109">Attributes and Elements</span></span>  
 <span data-ttu-id="01578-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="01578-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01578-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="01578-111">Attributes</span></span>  
  
|<span data-ttu-id="01578-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="01578-112">Attribute</span></span>|<span data-ttu-id="01578-113">Opis</span><span class="sxs-lookup"><span data-stu-id="01578-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01578-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="01578-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="01578-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="01578-115">Child Elements</span></span>  
 <span data-ttu-id="01578-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="01578-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01578-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="01578-117">Parent Elements</span></span>  
  
|<span data-ttu-id="01578-118">Element</span><span class="sxs-lookup"><span data-stu-id="01578-118">Element</span></span>|<span data-ttu-id="01578-119">Opis</span><span class="sxs-lookup"><span data-stu-id="01578-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01578-120">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="01578-120">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="01578-121">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="01578-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01578-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01578-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
