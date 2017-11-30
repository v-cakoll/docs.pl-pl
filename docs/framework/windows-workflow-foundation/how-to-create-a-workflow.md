---
title: "Porady: tworzenie przepływów pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
caps.latest.revision: "34"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f16df123837b2233efd156bf35975e3adbe7279
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="8f24a-102">Porady: tworzenie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="8f24a-102">How to: Create a Workflow</span></span>
<span data-ttu-id="8f24a-103">Przepływy pracy można skonstruować z działań wbudowanych oraz z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="8f24a-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="8f24a-104">Ten tematy w tym kroku sekcji przez proces tworzenia przepływu pracy, który używa zarówno wbudowane działania, takie jak <xref:System.Activities.Statements.Flowchart> działania i działań niestandardowych z poprzedniej [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="8f24a-104">This topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="8f24a-105">Przepływ pracy modele numer guessing gier.</span><span class="sxs-lookup"><span data-stu-id="8f24a-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="8f24a-106">Tylko jeden tematy w tej sekcji jest wymagany do ukończenia samouczka; należy wybierz odpowiedni styl interesującego i wykonać ten krok.</span><span class="sxs-lookup"><span data-stu-id="8f24a-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="8f24a-107">Jednak użytkownik może zakończyć się we wszystkich tematach w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="8f24a-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f24a-108">Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="8f24a-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="8f24a-109">Aby ukończyć w tym temacie, najpierw musisz zakończyć [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="8f24a-109">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f24a-110">Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="8f24a-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f24a-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8f24a-111">In This Section</span></span>  
 [<span data-ttu-id="8f24a-112">Porady: tworzenie sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8f24a-112">How to: Create a Sequential Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="8f24a-113">Opisuje sposób tworzenia sekwencyjnego przepływu pracy przy użyciu <xref:System.Activities.Statements.Sequence> działania.</span><span class="sxs-lookup"><span data-stu-id="8f24a-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="8f24a-114">Porady: tworzenie przepływów pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="8f24a-114">How to: Create a Flowchart Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="8f24a-115">Opisuje sposób tworzenia przepływu pracy schemat blokowy przy użyciu <xref:System.Activities.Statements.Flowchart> działania.</span><span class="sxs-lookup"><span data-stu-id="8f24a-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="8f24a-116">Porady: Tworzenie przepływu pracy automatu stanów</span><span class="sxs-lookup"><span data-stu-id="8f24a-116">How to: Create a State Machine Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="8f24a-117">Opisuje sposób tworzenia stanu komputera przepływu pracy używającego <xref:System.Activities.Statements.StateMachine> działania.</span><span class="sxs-lookup"><span data-stu-id="8f24a-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f24a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f24a-118">See Also</span></span>  
 [<span data-ttu-id="8f24a-119">Windows Workflow Foundation programowania</span><span class="sxs-lookup"><span data-stu-id="8f24a-119">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
