---
title: "Projektowanie i implementowanie niestandardowych działań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9243761803bc8b68ce37b3d3ad310e8bb7f93d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="3b0ae-102">Projektowanie i implementowanie niestandardowych działań</span><span class="sxs-lookup"><span data-stu-id="3b0ae-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="3b0ae-103">Niestandardowe działania w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] są tworzone przez albo montaż działania dostarczane przez system do działań złożonych lub tworząc nowe typy, które pochodzą z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, lub <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="3b0ae-104">W tej sekcji opisano sposób tworzenia działań niestandardowych z jednej z metod.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3b0ae-105">Działania niestandardowe, które domyślnie są wyświetlane w Projektancie przepływów pracy jako prosty prostokąt o nazwie działania.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="3b0ae-106">Zapewnienie niestandardowych wizualną reprezentację działanie w przepływie pracy projektanta należy również utworzyć designer niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="3b0ae-107">[Przy użyciu projektantów działań niestandardowych i szablonów](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="3b0ae-107"> [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b0ae-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3b0ae-108">In This Section</span></span>  
 [<span data-ttu-id="3b0ae-109">Opcje tworzenia działania</span><span class="sxs-lookup"><span data-stu-id="3b0ae-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="3b0ae-110">W tym artykule omówiono tworzenia style dostępne w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b0ae-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="3b0ae-111">Przy użyciu działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="3b0ae-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="3b0ae-112">Opisuje sposób dodawania działań niestandardowych do projektu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="3b0ae-113">Tworzenie działań asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="3b0ae-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="3b0ae-114">Opisuje sposób tworzenia działań asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="3b0ae-115">Konfigurowanie sprawdzania poprawności działania</span><span class="sxs-lookup"><span data-stu-id="3b0ae-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="3b0ae-116">Opisuje sposób sprawdzania poprawności działania może służyć do identyfikowania i raportowania błędów konfiguracji działania przed jego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="3b0ae-117">Tworzenie działania w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="3b0ae-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="3b0ae-118">W tym artykule omówiono sposób tworzenia działań w czasie wykonywania za pomocą <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="3b0ae-119">Właściwości wykonania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3b0ae-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="3b0ae-120">Opisuje, jak dodać właściwości specyficzne dla kontekstu środowiska działania za pomocą właściwości wykonania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3b0ae-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="3b0ae-121">Używanie delegatów działania</span><span class="sxs-lookup"><span data-stu-id="3b0ae-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="3b0ae-122">Zawiera omówienie sposobu tworzenia i używania działań, które zawierają działanie delegatów.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-122">Discusses how to author and use activities that contain activity delegates.</span></span>  
  
 [<span data-ttu-id="3b0ae-123">Lokalizacja działania</span><span class="sxs-lookup"><span data-stu-id="3b0ae-123">Activity Localization</span></span>](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 <span data-ttu-id="3b0ae-124">Informacje dotyczące używania lokalizacji zasobów ciągu w działaniach.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-124">Describes how to use localization of string resources in activities.</span></span>  
  
 [<span data-ttu-id="3b0ae-125">Przy użyciu rozszerzeń działania</span><span class="sxs-lookup"><span data-stu-id="3b0ae-125">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="3b0ae-126">Zawiera opis sposobu tworzenia i używania działania rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-126">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="3b0ae-127">Wykorzystywanie OData źródeł danych z przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3b0ae-127">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="3b0ae-128">W tym artykule opisano kilka metod wywoływania usługi danych WCF z przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-128">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="3b0ae-129">Określanie zakresu definicji działania i widoczność</span><span class="sxs-lookup"><span data-stu-id="3b0ae-129">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="3b0ae-130">Opisuje opcje i reguł określających widoczność zakresu i element członkowski danych działań.</span><span class="sxs-lookup"><span data-stu-id="3b0ae-130">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
