---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398569"
---
# \<workflowUnhandledException>
<span data-ttu-id="59335-101">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="59335-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="59335-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="59335-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59335-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="59335-103">Attributes and Elements</span></span>  
 <span data-ttu-id="59335-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="59335-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59335-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="59335-105">Attributes</span></span>  
  
|<span data-ttu-id="59335-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="59335-106">Attribute</span></span>|<span data-ttu-id="59335-107">Opis</span><span class="sxs-lookup"><span data-stu-id="59335-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59335-108">action</span><span class="sxs-lookup"><span data-stu-id="59335-108">action</span></span>|<span data-ttu-id="59335-109">Ciąg, który określa akcję, która ma zostać podjęta po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="59335-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="59335-110">Ten atrybut nie ma typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="59335-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59335-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="59335-111">Child Elements</span></span>  
 <span data-ttu-id="59335-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="59335-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59335-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="59335-113">Parent Elements</span></span>  
  
|<span data-ttu-id="59335-114">Element</span><span class="sxs-lookup"><span data-stu-id="59335-114">Element</span></span>|<span data-ttu-id="59335-115">Opis</span><span class="sxs-lookup"><span data-stu-id="59335-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59335-116">\<behavior>z\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="59335-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="59335-117">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="59335-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59335-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59335-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
