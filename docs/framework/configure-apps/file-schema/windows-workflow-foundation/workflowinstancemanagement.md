---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 98bc1b24da6e65a11a39d133057c1bb55b003a58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191617"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="cb2b3-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="cb2b3-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="cb2b3-102">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="cb2b3-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="cb2b3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cb2b3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="cb2b3-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="cb2b3-104">\<behaviors></span></span>  
<span data-ttu-id="cb2b3-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cb2b3-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="cb2b3-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cb2b3-106">\<behavior></span></span>  
<span data-ttu-id="cb2b3-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="cb2b3-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb2b3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb2b3-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb2b3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cb2b3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cb2b3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cb2b3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb2b3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cb2b3-111">Attributes</span></span>  
  
|<span data-ttu-id="cb2b3-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cb2b3-112">Attribute</span></span>|<span data-ttu-id="cb2b3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cb2b3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb2b3-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="cb2b3-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="cb2b3-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cb2b3-115">Child Elements</span></span>  
 <span data-ttu-id="cb2b3-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="cb2b3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb2b3-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cb2b3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cb2b3-118">Element</span><span class="sxs-lookup"><span data-stu-id="cb2b3-118">Element</span></span>|<span data-ttu-id="cb2b3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="cb2b3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb2b3-120">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cb2b3-120">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="cb2b3-121">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="cb2b3-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb2b3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb2b3-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
