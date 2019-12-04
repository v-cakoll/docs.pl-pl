---
title: Tworzenie i uruchamianie wystąpienia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d895cfa9e924ecf4d1571cf67f1c1e7069e25da5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715200"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="51915-102">Tworzenie i uruchamianie wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="51915-102">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="51915-103">Ten przykład pokazuje, jak uruchomić wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51915-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="51915-104">Pokazuje, jak wykonać ją synchronicznie i asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="51915-104">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="51915-105">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="51915-105">Demonstrates</span></span>

<span data-ttu-id="51915-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="51915-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="51915-107">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="51915-107">Discussion</span></span>

<span data-ttu-id="51915-108">Pierwsza część przykładu używa <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="51915-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="51915-109">Jest to najbardziej podstawowy sposób wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51915-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="51915-110">Przepływy pracy wykonywane z <xref:System.Activities.WorkflowInvoker.Invoke%2A> są wykonywane synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="51915-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="51915-111">Druga część przykładu używa klasy <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="51915-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="51915-112"><xref:System.Activities.WorkflowApplication> umożliwia większą kontrolę nad każdym wystąpieniem, w tym możliwość współdziałania z uruchomionym przepływem pracy oraz do asynchronicznego uruchamiania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51915-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51915-113">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="51915-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="51915-114">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="51915-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="51915-115">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51915-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51915-116">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="51915-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="51915-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51915-117">See also</span></span>

- [<span data-ttu-id="51915-118">Używanie obiektu WorkflowInvoker i WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="51915-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
