---
title: 'Instrukcje: Tworzenie przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: aaaac74d26421f96a3170b3e5a788145f8ea09fc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704950"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="6d9a9-102">Instrukcje: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6d9a9-102">How to: Create a Workflow</span></span>
<span data-ttu-id="6d9a9-103">Przepływy pracy można skonstruować z wbudowanych działań, a także z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6d9a9-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="6d9a9-104">Tematy w tej części kroku proces tworzenia przepływu pracy, który używa zarówno wbudowanych działań, takich jak <xref:System.Activities.Statements.Flowchart> działanie i działań niestandardowych z poprzedniego [jak: Utwórz działanie](how-to-create-an-activity.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="6d9a9-104">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="6d9a9-105">Przepływ pracy modeli gra odgadnięcia liczb.</span><span class="sxs-lookup"><span data-stu-id="6d9a9-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="6d9a9-106">Tylko jeden tematy w tej sekcji jest wymagany do ukończenia tego samouczka; należy wybrać styl, który Cię interesuje i wykonaj ten krok.</span><span class="sxs-lookup"><span data-stu-id="6d9a9-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="6d9a9-107">Jednak użytkownik może przejść wszystkie tematy w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="6d9a9-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d9a9-108">Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach.</span><span class="sxs-lookup"><span data-stu-id="6d9a9-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="6d9a9-109">Aby ukończyć ten temat, najpierw musisz zakończyć [jak: Utwórz działanie](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="6d9a9-109">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d9a9-110">Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="6d9a9-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d9a9-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6d9a9-111">In This Section</span></span>  
 [<span data-ttu-id="6d9a9-112">Instrukcje: Tworzenie sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6d9a9-112">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="6d9a9-113">Opisuje sposób tworzenia sekwencyjnego przepływu pracy przy użyciu <xref:System.Activities.Statements.Sequence> działania.</span><span class="sxs-lookup"><span data-stu-id="6d9a9-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="6d9a9-114">Instrukcje: Tworzenie przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="6d9a9-114">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="6d9a9-115">W tym artykule opisano sposób tworzenia przepływu pracy schematu blokowego przy użyciu <xref:System.Activities.Statements.Flowchart> działania.</span><span class="sxs-lookup"><span data-stu-id="6d9a9-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="6d9a9-116">Instrukcje: Tworzenie przepływu pracy automatu stanów</span><span class="sxs-lookup"><span data-stu-id="6d9a9-116">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="6d9a9-117">Opisuje, jak utworzyć stanu komputera przepływu pracy przy użyciu <xref:System.Activities.Statements.StateMachine> działania.</span><span class="sxs-lookup"><span data-stu-id="6d9a9-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d9a9-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d9a9-118">See also</span></span>
- [<span data-ttu-id="6d9a9-119">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="6d9a9-119">Windows Workflow Foundation Programming</span></span>](programming.md)
