---
title: Tworzenie i uruchamianie wystąpienia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 571d41194ebc98be81646fb5bfdab060225015ca
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097857"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="7b33c-102">Tworzenie i uruchamianie wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7b33c-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="7b33c-103">W tym przykładzie pokazano, jak w celu uruchomienia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b33c-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="7b33c-104">Widoczny jest sposób ją wykonać synchronicznie i asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="7b33c-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7b33c-105">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="7b33c-105">Demonstrates</span></span>  
 <span data-ttu-id="7b33c-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="7b33c-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7b33c-107">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="7b33c-107">Discussion</span></span>  
 <span data-ttu-id="7b33c-108">Pierwsza część próbki używa <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b33c-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="7b33c-109">Jest to najprostszy sposób wykonania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b33c-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="7b33c-110">Przepływy pracy, wykonywane przy użyciu <xref:System.Activities.WorkflowInvoker.Invoke%2A> są wykonywane synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="7b33c-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="7b33c-111">Druga część próbki używa <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="7b33c-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="7b33c-112"><xref:System.Activities.WorkflowApplication> pozwala uzyskać większą kontrolę nad każde wystąpienie, w tym możliwość interakcji z uruchomionym przepływem pracy i asynchronicznie Uruchom przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="7b33c-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b33c-113">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7b33c-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b33c-114">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7b33c-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b33c-115">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="7b33c-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b33c-116">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7b33c-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="7b33c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b33c-117">See Also</span></span>  
 [<span data-ttu-id="7b33c-118">Używanie obiektu WorkflowInvoker i WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="7b33c-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
