---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397524"
---
# \<workflowInstanceManagement>
<span data-ttu-id="d4e5f-101">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="d4e5f-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="d4e5f-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4e5f-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4e5f-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4e5f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d4e5f-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4e5f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4e5f-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4e5f-105">Attributes</span></span>  
  
|<span data-ttu-id="d4e5f-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d4e5f-106">Attribute</span></span>|<span data-ttu-id="d4e5f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d4e5f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4e5f-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="d4e5f-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="d4e5f-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4e5f-109">Child Elements</span></span>  
 <span data-ttu-id="d4e5f-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="d4e5f-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4e5f-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4e5f-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d4e5f-112">Element</span><span class="sxs-lookup"><span data-stu-id="d4e5f-112">Element</span></span>|<span data-ttu-id="d4e5f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d4e5f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4e5f-114">\<behavior>z\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d4e5f-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d4e5f-115">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="d4e5f-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4e5f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4e5f-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
