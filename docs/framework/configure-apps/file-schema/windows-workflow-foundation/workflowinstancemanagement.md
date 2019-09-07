---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397524"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="55e02-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="55e02-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="55e02-102">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="55e02-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="55e02-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="55e02-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="55e02-104">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="55e02-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="55e02-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="55e02-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="55e02-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="55e02-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="55e02-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="55e02-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="55e02-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceManagement >**</span><span class="sxs-lookup"><span data-stu-id="55e02-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e02-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="55e02-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55e02-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="55e02-110">Attributes and Elements</span></span>  
 <span data-ttu-id="55e02-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="55e02-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55e02-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="55e02-112">Attributes</span></span>  
  
|<span data-ttu-id="55e02-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="55e02-113">Attribute</span></span>|<span data-ttu-id="55e02-114">Opis</span><span class="sxs-lookup"><span data-stu-id="55e02-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55e02-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="55e02-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="55e02-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="55e02-116">Child Elements</span></span>  
 <span data-ttu-id="55e02-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="55e02-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55e02-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="55e02-118">Parent Elements</span></span>  
  
|<span data-ttu-id="55e02-119">Element</span><span class="sxs-lookup"><span data-stu-id="55e02-119">Element</span></span>|<span data-ttu-id="55e02-120">Opis</span><span class="sxs-lookup"><span data-stu-id="55e02-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55e02-121">\<zachowanie > w \<usłudze serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="55e02-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="55e02-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="55e02-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55e02-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55e02-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
