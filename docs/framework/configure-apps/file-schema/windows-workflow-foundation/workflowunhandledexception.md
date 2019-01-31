---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: caf5be7aaff0df436be3a1d618a9f89bb32e6bb7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254852"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="0499e-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="0499e-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="0499e-102">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0499e-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="0499e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0499e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0499e-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="0499e-104">\<behaviors></span></span>  
<span data-ttu-id="0499e-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0499e-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="0499e-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="0499e-106">\<behavior></span></span>  
<span data-ttu-id="0499e-107">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="0499e-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0499e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="0499e-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0499e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0499e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0499e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0499e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0499e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0499e-111">Attributes</span></span>  
  
|<span data-ttu-id="0499e-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0499e-112">Attribute</span></span>|<span data-ttu-id="0499e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0499e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0499e-114">Akcja</span><span class="sxs-lookup"><span data-stu-id="0499e-114">action</span></span>|<span data-ttu-id="0499e-115">Ciąg, który określa akcję, która ma zostać podjęta po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0499e-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="0499e-116">Ten atrybut nie ma typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="0499e-116">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0499e-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0499e-117">Child Elements</span></span>  
 <span data-ttu-id="0499e-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="0499e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0499e-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0499e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0499e-120">Element</span><span class="sxs-lookup"><span data-stu-id="0499e-120">Element</span></span>|<span data-ttu-id="0499e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0499e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0499e-122">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0499e-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="0499e-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="0499e-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0499e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0499e-124">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
