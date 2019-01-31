---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: baa1ccbe0accd2db701fac9ef53cdc6357713c5d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257424"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="ff7f7-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="ff7f7-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="ff7f7-102">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="ff7f7-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="ff7f7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ff7f7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ff7f7-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ff7f7-104">\<behaviors></span></span>  
<span data-ttu-id="ff7f7-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ff7f7-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ff7f7-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ff7f7-106">\<behavior></span></span>  
<span data-ttu-id="ff7f7-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="ff7f7-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff7f7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff7f7-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff7f7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ff7f7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ff7f7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ff7f7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff7f7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ff7f7-111">Attributes</span></span>  
  
|<span data-ttu-id="ff7f7-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ff7f7-112">Attribute</span></span>|<span data-ttu-id="ff7f7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ff7f7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff7f7-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="ff7f7-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="ff7f7-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ff7f7-115">Child Elements</span></span>  
 <span data-ttu-id="ff7f7-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="ff7f7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff7f7-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ff7f7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ff7f7-118">Element</span><span class="sxs-lookup"><span data-stu-id="ff7f7-118">Element</span></span>|<span data-ttu-id="ff7f7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ff7f7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff7f7-120">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ff7f7-120">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="ff7f7-121">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="ff7f7-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff7f7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff7f7-122">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
