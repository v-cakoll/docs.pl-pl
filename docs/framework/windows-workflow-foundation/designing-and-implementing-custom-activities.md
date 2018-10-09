---
title: Projektowanie i implementowanie niestandardowych działań
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 673145c856e950c8648a87cb3dcb9665ffa51ba9
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873391"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="02f2e-102">Projektowanie i implementowanie niestandardowych działań</span><span class="sxs-lookup"><span data-stu-id="02f2e-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="02f2e-103">Niestandardowe działania w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] są tworzone przez albo montażu działania dostarczane przez system do działań złożonych lub tworząc nowe typy, które wynikają z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, lub <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="02f2e-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="02f2e-104">W tej sekcji opisano sposób tworzenia działań niestandardowych za pomocą jednej z metod.</span><span class="sxs-lookup"><span data-stu-id="02f2e-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="02f2e-105">Działania niestandardowe, które domyślnie są wyświetlane w Projektancie przepływu pracy jako prosty prostokąt o nazwie tego działania.</span><span class="sxs-lookup"><span data-stu-id="02f2e-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="02f2e-106">Zapewnienie niestandardowe wizualnej reprezentacji działania w przepływie pracy projektanta należy także utworzyć niestandardowego projektanta.</span><span class="sxs-lookup"><span data-stu-id="02f2e-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="02f2e-107">Aby uzyskać więcej informacji, zobacz [szablonów i za pomocą projektantów działań niestandardowych](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="02f2e-107">For more information, see [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="02f2e-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="02f2e-108">In This Section</span></span>  
 [<span data-ttu-id="02f2e-109">Opcje tworzenia działań</span><span class="sxs-lookup"><span data-stu-id="02f2e-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="02f2e-110">W tym artykule omówiono tworzenia style, dostępne w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02f2e-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="02f2e-111">Używanie niestandardowego działania</span><span class="sxs-lookup"><span data-stu-id="02f2e-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="02f2e-112">W tym artykule opisano sposób dodawania działań niestandardowych do projektu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="02f2e-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="02f2e-113">Tworzenie działań asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="02f2e-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="02f2e-114">Opisuje sposób tworzenie działań asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="02f2e-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="02f2e-115">Konfigurowanie walidacji działania</span><span class="sxs-lookup"><span data-stu-id="02f2e-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="02f2e-116">Opisuje sposób sprawdzania poprawności działania może służyć do identyfikowania i raportowania błędów konfiguracji działanie przed jej wykonanie.</span><span class="sxs-lookup"><span data-stu-id="02f2e-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="02f2e-117">Tworzenie działania w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="02f2e-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="02f2e-118">W tym artykule omówiono sposób tworzenia działania w czasie wykonywania za pomocą <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="02f2e-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="02f2e-119">Właściwości wykonania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="02f2e-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="02f2e-120">Opisuje sposób używania właściwości wykonania przepływu pracy, aby dodać określonej właściwości kontekstu do działania środowiska</span><span class="sxs-lookup"><span data-stu-id="02f2e-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="02f2e-121">Używanie delegatów działania</span><span class="sxs-lookup"><span data-stu-id="02f2e-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="02f2e-122">W tym artykule omówiono sposób tworzenia i używania działań, które zawierają działania delegatach.</span><span class="sxs-lookup"><span data-stu-id="02f2e-122">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="02f2e-123">Używanie rozszerzeń działania</span><span class="sxs-lookup"><span data-stu-id="02f2e-123">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="02f2e-124">Opisuje sposób tworzenia i używania rozszerzeń działania.</span><span class="sxs-lookup"><span data-stu-id="02f2e-124">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="02f2e-125">Wykorzystywanie źródeł strumieniowych danych OData z przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="02f2e-125">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="02f2e-126">W tym artykule opisano kilka metod wywoływania usługi danych WCF z przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="02f2e-126">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="02f2e-127">Wyznaczanie zakresu i widoczność definicji działania</span><span class="sxs-lookup"><span data-stu-id="02f2e-127">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="02f2e-128">W tym artykule opisano opcje i reguł określających widoczność zakresu i element członkowski danych działań.</span><span class="sxs-lookup"><span data-stu-id="02f2e-128">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
