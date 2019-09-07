---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398569"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="fb3a7-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="fb3a7-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="fb3a7-102">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb3a7-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="fb3a7-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb3a7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fb3a7-104">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fb3a7-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="fb3a7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fb3a7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="fb3a7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fb3a7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="fb3a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fb3a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="fb3a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowUnhandledException >**</span><span class="sxs-lookup"><span data-stu-id="fb3a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb3a7-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb3a7-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb3a7-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fb3a7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fb3a7-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fb3a7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb3a7-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb3a7-112">Attributes</span></span>  
  
|<span data-ttu-id="fb3a7-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fb3a7-113">Attribute</span></span>|<span data-ttu-id="fb3a7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fb3a7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb3a7-115">Akcja</span><span class="sxs-lookup"><span data-stu-id="fb3a7-115">action</span></span>|<span data-ttu-id="fb3a7-116">Ciąg, który określa akcję, która ma zostać podjęta po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="fb3a7-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="fb3a7-117">Ten atrybut nie ma typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="fb3a7-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb3a7-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fb3a7-118">Child Elements</span></span>  
 <span data-ttu-id="fb3a7-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="fb3a7-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb3a7-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fb3a7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fb3a7-121">Element</span><span class="sxs-lookup"><span data-stu-id="fb3a7-121">Element</span></span>|<span data-ttu-id="fb3a7-122">Opis</span><span class="sxs-lookup"><span data-stu-id="fb3a7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb3a7-123">\<zachowanie > w \<usłudze serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fb3a7-123">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="fb3a7-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="fb3a7-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb3a7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb3a7-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
