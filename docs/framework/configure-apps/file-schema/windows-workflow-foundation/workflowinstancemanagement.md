---
title: '&lt;workflowInstanceManagement&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: ba3d9415efc21012b470fd2e9a7f426ca8f3aad1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662065"
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="ea124-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="ea124-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="ea124-103">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="ea124-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="ea124-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ea124-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ea124-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ea124-105">\<behaviors></span></span>  
<span data-ttu-id="ea124-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ea124-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ea124-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ea124-107">\<behavior></span></span>  
<span data-ttu-id="ea124-108">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="ea124-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea124-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea124-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea124-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ea124-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ea124-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ea124-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea124-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ea124-112">Attributes</span></span>  
  
|<span data-ttu-id="ea124-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ea124-113">Attribute</span></span>|<span data-ttu-id="ea124-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ea124-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea124-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="ea124-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="ea124-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ea124-116">Child Elements</span></span>  
 <span data-ttu-id="ea124-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="ea124-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea124-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ea124-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ea124-119">Element</span><span class="sxs-lookup"><span data-stu-id="ea124-119">Element</span></span>|<span data-ttu-id="ea124-120">Opis</span><span class="sxs-lookup"><span data-stu-id="ea124-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea124-121">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ea124-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="ea124-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="ea124-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea124-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea124-123">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
