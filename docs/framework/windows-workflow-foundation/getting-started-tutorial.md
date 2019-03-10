---
title: Wprowadzenie do Tutorial2
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: 33d89b92dc17bc26391047b78c619aac01ea21da
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724703"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="dcfe5-102">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="dcfe5-102">Getting Started Tutorial</span></span>
<span data-ttu-id="dcfe5-103">Ta sekcja zawiera zestaw tematów wskazówki, które służą jako wprowadzenie do programowania aplikacji Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="dcfe5-103">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="dcfe5-104">Zgodnie z instrukcjami opisanymi w tych tematach, utworzysz aplikację, która jest liczba gra odgadnięcia.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-104">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="dcfe5-105">Pierwszy temat, samouczek poprowadzi Cię przez kroki, aby utworzyć niestandardowe działania wymagane dla przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-105">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="dcfe5-106">W drugiej części tematu te działania są łączone wraz z działań wbudowanych przepływu pracy do przepływu pracy schematu blokowego.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-106">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="dcfe5-107">W trzecim temacie aplikacji hosta jest skonfigurowany do uruchamiania przepływu pracy, a w ostatnim temacie wprowadzono trwałości.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-107">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="dcfe5-108">Każdy krok w ramach tego procesu zależy od poprzednie kroki, tak więc zaleca się zakończyć je w kolejności.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-108">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dcfe5-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dcfe5-109">In This Section</span></span>  
 [<span data-ttu-id="dcfe5-110">Instrukcje: Utwórz działanie</span><span class="sxs-lookup"><span data-stu-id="dcfe5-110">How to: Create an Activity</span></span>](how-to-create-an-activity.md)  
 <span data-ttu-id="dcfe5-111">W tym artykule opisano sposób tworzenia działań niestandardowych, która pochodzi od klasy <xref:System.Activities.NativeActivity%601>oraz sposobu tworzenia tego działania wraz z wbudowanego działania do działania złożonego za pomocą projektanta działań.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-111">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="dcfe5-112">Instrukcje: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dcfe5-112">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)  
 <span data-ttu-id="dcfe5-113">Opisuje sposób tworzenia schematu blokowego sekwencyjnie i przepływów pracy automatu stanów przy użyciu działań wbudowanych i niestandardowych działań z poprzedniego samouczka.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-113">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="dcfe5-114">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dcfe5-114">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)  
 <span data-ttu-id="dcfe5-115">Opisuje sposób wywołania przepływu pracy w środowisku hosta, przekazywanie danych do i z przepływu pracy oraz wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-115">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="dcfe5-116">Instrukcje: Tworzenie i uruchamianie długotrwałego uruchamiania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dcfe5-116">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="dcfe5-117">W tym artykule opisano sposób dodawania trwałości do poziomu aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-117">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="dcfe5-118">Instrukcje: Tworzenie niestandardowego uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="dcfe5-118">How to: Create a Custom Tracking Participant</span></span>](how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="dcfe5-119">W tym artykule opisano sposób tworzenia niestandardowego uczestnika śledzenia i profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-119">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="dcfe5-120">Instrukcje: Hostowanie wielu wersji przepływu pracy Side-by-Side</span><span class="sxs-lookup"><span data-stu-id="dcfe5-120">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="dcfe5-121">Opisuje sposób używania `WorkflowIdentity` do hostowania wielu wersji przepływu pracy side-by-side.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-121">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="dcfe5-122">Instrukcje: Aktualizowanie definicji działającego wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dcfe5-122">How to: Update the Definition of a Running Workflow Instance</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="dcfe5-123">Opisuje sposób używania aktualizacji dynamicznej, aby zmodyfikować uruchomionego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-123">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcfe5-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcfe5-124">See also</span></span>
- [<span data-ttu-id="dcfe5-125">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="dcfe5-125">Windows Workflow Foundation Programming</span></span>](programming.md)
