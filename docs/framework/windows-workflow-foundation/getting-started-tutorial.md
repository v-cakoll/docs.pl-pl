---
title: Wprowadzenie do Tutorial2
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: 99daa524f041ffcd096195fc79527557b8f2697d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591990"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="89a58-102">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="89a58-102">Getting Started Tutorial</span></span>
<span data-ttu-id="89a58-103">Ta sekcja zawiera zestaw tematów wskazówki, które służą jako wprowadzenie do programowania aplikacji Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="89a58-103">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="89a58-104">Zgodnie z instrukcjami opisanymi w tych tematach, utworzysz aplikację, która jest liczba gra odgadnięcia.</span><span class="sxs-lookup"><span data-stu-id="89a58-104">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="89a58-105">Pierwszy temat, samouczek poprowadzi Cię przez kroki, aby utworzyć niestandardowe działania wymagane dla przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="89a58-105">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="89a58-106">W drugiej części tematu te działania są łączone wraz z działań wbudowanych przepływu pracy do przepływu pracy schematu blokowego.</span><span class="sxs-lookup"><span data-stu-id="89a58-106">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="89a58-107">W trzecim temacie aplikacji hosta jest skonfigurowany do uruchamiania przepływu pracy, a w ostatnim temacie wprowadzono trwałości.</span><span class="sxs-lookup"><span data-stu-id="89a58-107">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="89a58-108">Każdy krok w ramach tego procesu zależy od poprzednie kroki, tak więc zaleca się zakończyć je w kolejności.</span><span class="sxs-lookup"><span data-stu-id="89a58-108">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89a58-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="89a58-109">In This Section</span></span>  
 [<span data-ttu-id="89a58-110">Instrukcje: Utwórz działanie</span><span class="sxs-lookup"><span data-stu-id="89a58-110">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 <span data-ttu-id="89a58-111">W tym artykule opisano sposób tworzenia działań niestandardowych, która pochodzi od klasy <xref:System.Activities.NativeActivity%601>oraz sposobu tworzenia tego działania wraz z wbudowanego działania do działania złożonego za pomocą projektanta działań.</span><span class="sxs-lookup"><span data-stu-id="89a58-111">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="89a58-112">Instrukcje: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="89a58-112">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 <span data-ttu-id="89a58-113">Opisuje sposób tworzenia schematu blokowego sekwencyjnie i przepływów pracy automatu stanów przy użyciu działań wbudowanych i niestandardowych działań z poprzedniego samouczka.</span><span class="sxs-lookup"><span data-stu-id="89a58-113">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="89a58-114">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="89a58-114">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)  
 <span data-ttu-id="89a58-115">Opisuje sposób wywołania przepływu pracy w środowisku hosta, przekazywanie danych do i z przepływu pracy oraz wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="89a58-115">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="89a58-116">Instrukcje: Tworzenie i uruchamianie długotrwałego uruchamiania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="89a58-116">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="89a58-117">W tym artykule opisano sposób dodawania trwałości do poziomu aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="89a58-117">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="89a58-118">Instrukcje: Tworzenie niestandardowego uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="89a58-118">How to: Create a Custom Tracking Participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="89a58-119">W tym artykule opisano sposób tworzenia niestandardowego uczestnika śledzenia i profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="89a58-119">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="89a58-120">Instrukcje: Hostowanie wielu wersji przepływu pracy Side-by-Side</span><span class="sxs-lookup"><span data-stu-id="89a58-120">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="89a58-121">Opisuje sposób używania `WorkflowIdentity` do hostowania wielu wersji przepływu pracy side-by-side.</span><span class="sxs-lookup"><span data-stu-id="89a58-121">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="89a58-122">Instrukcje: Aktualizowanie definicji działającego wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="89a58-122">How to: Update the Definition of a Running Workflow Instance</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="89a58-123">Opisuje sposób używania aktualizacji dynamicznej, aby zmodyfikować uruchomionego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="89a58-123">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a58-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89a58-124">See also</span></span>
- [<span data-ttu-id="89a58-125">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="89a58-125">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
