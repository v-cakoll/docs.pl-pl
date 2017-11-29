---
title: "Wprowadzenie tutorial2 —"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9947833a11fa0b7227a11e65f3b42a91d8fe91d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="aee6d-102">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="aee6d-102">Getting Started Tutorial</span></span>
<span data-ttu-id="aee6d-103">Ta sekcja zawiera zestaw tematów wskazówki, które służą jako wprowadzenie do programowania w języku [!INCLUDE[wf](../../../includes/wf-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aee6d-103">This section contains a set of walkthrough topics that introduce you to programming [!INCLUDE[wf](../../../includes/wf-md.md)] applications.</span></span> <span data-ttu-id="aee6d-104">Zgodnie z instrukcjami opisanymi w tych tematach, zostanie utworzona aplikacja, która jest numer gry guessing.</span><span class="sxs-lookup"><span data-stu-id="aee6d-104">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="aee6d-105">Pierwszym temacie samouczka poprowadzi Cię przez kroki tworzenia działań niestandardowych wymagane dla przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="aee6d-105">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="aee6d-106">W drugim temacie te działania są łączone wraz z działań wbudowanych przepływów pracy w przepływie pracy schemat blokowy.</span><span class="sxs-lookup"><span data-stu-id="aee6d-106">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="aee6d-107">W trzecim temacie aplikacja hosta jest skonfigurowana do uruchamiania przepływu pracy, a w ostatnim temacie wprowadzono trwałości.</span><span class="sxs-lookup"><span data-stu-id="aee6d-107">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="aee6d-108">Każdy krok w procesie zależy od poprzednie kroki, tak więc zaleca się zakończyć je w kolejności.</span><span class="sxs-lookup"><span data-stu-id="aee6d-108">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aee6d-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="aee6d-109">In This Section</span></span>  
 [<span data-ttu-id="aee6d-110">Porady: tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="aee6d-110">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 <span data-ttu-id="aee6d-111">Opisuje sposób tworzenia działań niestandardowych, która jest pochodną <xref:System.Activities.NativeActivity%601>oraz sposobu tworzenia tego działania wraz z wbudowanych działanie do działania złożonego przy użyciu narzędzia Projektant działań.</span><span class="sxs-lookup"><span data-stu-id="aee6d-111">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="aee6d-112">Porady: tworzenie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="aee6d-112">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 <span data-ttu-id="aee6d-113">Opisuje sposób tworzenia schematu blokowego sekwencyjnych i przepływów pracy maszyny stanu przy użyciu działań wbudowanych i niestandardowych działań z poprzednim samouczka.</span><span class="sxs-lookup"><span data-stu-id="aee6d-113">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="aee6d-114">Porady: uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="aee6d-114">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)  
 <span data-ttu-id="aee6d-115">W tym artykule opisano, jak wywołać przepływu pracy w środowisku hosta, przekazywanie danych do i z przepływu pracy i sposób wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="aee6d-115">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="aee6d-116">Porady: tworzenie i uruchamianie długi uruchamiania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="aee6d-116">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="aee6d-117">Opisuje sposób dodawania trwałości aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="aee6d-117">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="aee6d-118">Porady: Tworzenie niestandardowych śledzenia uczestnika</span><span class="sxs-lookup"><span data-stu-id="aee6d-118">How to: Create a Custom Tracking Participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="aee6d-119">Opisuje sposób tworzenia niestandardowych śledzenia uczestnika i profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="aee6d-119">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="aee6d-120">Porady: hostowanie wielu wersji przepływu pracy Side-by-Side</span><span class="sxs-lookup"><span data-stu-id="aee6d-120">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="aee6d-121">Informacje dotyczące używania `WorkflowIdentity` do obsługi wielu wersji przepływu pracy side-by-side.</span><span class="sxs-lookup"><span data-stu-id="aee6d-121">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="aee6d-122">Porady: aktualizowanie definicji działania wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="aee6d-122">How to: Update the Definition of a Running Workflow Instance</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="aee6d-123">Informacje dotyczące używania aktualizacji dynamicznej można zmodyfikować uruchomionych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="aee6d-123">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee6d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aee6d-124">See Also</span></span>  
 [<span data-ttu-id="aee6d-125">Windows Workflow Foundation programowania</span><span class="sxs-lookup"><span data-stu-id="aee6d-125">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
