---
title: 'Instrukcje: Tworzenie przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: 7f0bef673ff14ded13306a1fc26e09695601799d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962296"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="e4bcb-102">Instrukcje: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e4bcb-102">How to: Create a Workflow</span></span>
<span data-ttu-id="e4bcb-103">Przepływy pracy mogą być zbudowane z wbudowanych działań, a także z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e4bcb-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="e4bcb-104">Tematy w tej sekcji dotyczą tworzenia przepływu pracy, który używa zarówno wbudowanych działań, jak <xref:System.Activities.Statements.Flowchart> działania, jak i działań niestandardowych, z poprzednich [instrukcji: Utwórz temat działania](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="e4bcb-104">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="e4bcb-105">Przepływ pracy modeluje grę z liczbą odgadnąć.</span><span class="sxs-lookup"><span data-stu-id="e4bcb-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="e4bcb-106">Do ukończenia tego samouczka jest wymagany tylko jeden z tematów w tej sekcji. należy wybrać styl, który Cię interesuje, i wykonać ten krok.</span><span class="sxs-lookup"><span data-stu-id="e4bcb-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="e4bcb-107">Jednak w razie potrzeby można wykonać wszystkie tematy.</span><span class="sxs-lookup"><span data-stu-id="e4bcb-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4bcb-108">Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="e4bcb-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="e4bcb-109">Aby ukończyć ten temat, należy najpierw wykonać [następujące czynności: Utwórz działanie](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="e4bcb-109">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4bcb-110">Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="e4bcb-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4bcb-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e4bcb-111">In This Section</span></span>  
 [<span data-ttu-id="e4bcb-112">Instrukcje: Tworzenie sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e4bcb-112">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="e4bcb-113">Opisuje sposób tworzenia sekwencyjnego przepływu pracy przy użyciu <xref:System.Activities.Statements.Sequence> działania.</span><span class="sxs-lookup"><span data-stu-id="e4bcb-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="e4bcb-114">Instrukcje: Tworzenie przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="e4bcb-114">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="e4bcb-115">Opisuje sposób tworzenia przepływu pracy Flowchart przy użyciu <xref:System.Activities.Statements.Flowchart> działania.</span><span class="sxs-lookup"><span data-stu-id="e4bcb-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="e4bcb-116">Instrukcje: Tworzenie przepływu pracy automatu Stanów</span><span class="sxs-lookup"><span data-stu-id="e4bcb-116">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="e4bcb-117">Opisuje sposób tworzenia przepływu pracy automatu Stanów przy <xref:System.Activities.Statements.StateMachine> użyciu działania.</span><span class="sxs-lookup"><span data-stu-id="e4bcb-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4bcb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4bcb-118">See also</span></span>

- [<span data-ttu-id="e4bcb-119">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="e4bcb-119">Windows Workflow Foundation Programming</span></span>](programming.md)
