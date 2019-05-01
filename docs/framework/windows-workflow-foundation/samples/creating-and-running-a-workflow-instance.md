---
title: Tworzenie i uruchamianie wystąpienia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: f2bdfce0b311da6dd20aac5e0fe4f5fbcd14f68a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005306"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="5faca-102">Tworzenie i uruchamianie wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5faca-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="5faca-103">W tym przykładzie pokazano, jak w celu uruchomienia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5faca-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="5faca-104">Widoczny jest sposób ją wykonać synchronicznie i asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="5faca-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5faca-105">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="5faca-105">Demonstrates</span></span>  
 <span data-ttu-id="5faca-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="5faca-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5faca-107">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="5faca-107">Discussion</span></span>  
 <span data-ttu-id="5faca-108">Pierwsza część próbki używa <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="5faca-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="5faca-109">Jest to najprostszy sposób wykonania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5faca-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="5faca-110">Przepływy pracy, wykonywane przy użyciu <xref:System.Activities.WorkflowInvoker.Invoke%2A> są wykonywane synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="5faca-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="5faca-111">Druga część próbki używa <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="5faca-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="5faca-112"><xref:System.Activities.WorkflowApplication> pozwala uzyskać większą kontrolę nad każde wystąpienie, w tym możliwość interakcji z uruchomionym przepływem pracy i asynchronicznie Uruchom przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="5faca-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5faca-113">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5faca-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5faca-114">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5faca-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5faca-115">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="5faca-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5faca-116">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5faca-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="5faca-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5faca-117">See also</span></span>

- [<span data-ttu-id="5faca-118">Używanie obiektu WorkflowInvoker i WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="5faca-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
