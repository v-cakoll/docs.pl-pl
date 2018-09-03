---
title: 'Porady: Tworzenie przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: adaa322d4129f56abcad4fd848204ee373e907bd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43462301"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="d83a2-102">Porady: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d83a2-102">How to: Create a Workflow</span></span>
<span data-ttu-id="d83a2-103">Przepływy pracy można skonstruować z wbudowanych działań, a także z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d83a2-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="d83a2-104">Ten temat w tym kroku sekcji proces tworzenia przepływu pracy, który używa zarówno wbudowanych działań, takich jak <xref:System.Activities.Statements.Flowchart> działanie i działań niestandardowych z poprzedniego [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="d83a2-104">This topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="d83a2-105">Przepływ pracy modeli gra odgadnięcia liczb.</span><span class="sxs-lookup"><span data-stu-id="d83a2-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="d83a2-106">Tylko jeden tematy w tej sekcji jest wymagany do ukończenia tego samouczka; należy wybrać styl, który Cię interesuje i wykonaj ten krok.</span><span class="sxs-lookup"><span data-stu-id="d83a2-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="d83a2-107">Jednak użytkownik może przejść wszystkie tematy w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="d83a2-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d83a2-108">Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach.</span><span class="sxs-lookup"><span data-stu-id="d83a2-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="d83a2-109">Aby ukończyć ten temat, najpierw musisz zakończyć [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="d83a2-109">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d83a2-110">Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="d83a2-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d83a2-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d83a2-111">In This Section</span></span>  
 [<span data-ttu-id="d83a2-112">Instrukcje: Tworzenie sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d83a2-112">How to: Create a Sequential Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="d83a2-113">Opisuje sposób tworzenia sekwencyjnego przepływu pracy przy użyciu <xref:System.Activities.Statements.Sequence> działania.</span><span class="sxs-lookup"><span data-stu-id="d83a2-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="d83a2-114">Instrukcje: Tworzenie przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="d83a2-114">How to: Create a Flowchart Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="d83a2-115">W tym artykule opisano sposób tworzenia przepływu pracy schematu blokowego przy użyciu <xref:System.Activities.Statements.Flowchart> działania.</span><span class="sxs-lookup"><span data-stu-id="d83a2-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="d83a2-116">Instrukcje: Tworzenie przepływu pracy automatu stanów</span><span class="sxs-lookup"><span data-stu-id="d83a2-116">How to: Create a State Machine Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="d83a2-117">Opisuje, jak utworzyć stanu komputera przepływu pracy przy użyciu <xref:System.Activities.Statements.StateMachine> działania.</span><span class="sxs-lookup"><span data-stu-id="d83a2-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83a2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d83a2-118">See Also</span></span>  
 [<span data-ttu-id="d83a2-119">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="d83a2-119">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
