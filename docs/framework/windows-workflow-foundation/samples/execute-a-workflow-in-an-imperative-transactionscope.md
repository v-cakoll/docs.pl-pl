---
title: "Wykonania przepływu pracy w TransactionScope Imperatywne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 26117e7b089e85e8953912745ebc74baad8bfa29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a><span data-ttu-id="cd766-102">Wykonania przepływu pracy w TransactionScope Imperatywne</span><span class="sxs-lookup"><span data-stu-id="cd766-102">Execute a Workflow in an Imperative TransactionScope</span></span>
<span data-ttu-id="cd766-103">W tym przykładzie pokazano, jak wykonywanie przepływu pracy za pomocą <xref:System.Activities.WorkflowInvoker> w obszarze <xref:System.Transactions.Transaction> z natury kodu C#.</span><span class="sxs-lookup"><span data-stu-id="cd766-103">This sample shows how to execute a workflow using <xref:System.Activities.WorkflowInvoker> under a <xref:System.Transactions.Transaction> from imperative C# code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="cd766-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="cd766-104">Sample Details</span></span>  
 <span data-ttu-id="cd766-105">W trybie kod C# <xref:System.Transactions.TransactionScope> jest używany w celu hermetyzacji zestawu pracy, który wykonuje w tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="cd766-105">In imperative C# code, the <xref:System.Transactions.TransactionScope> is used to encapsulate a set of work that executes under the same transaction.</span></span> <span data-ttu-id="cd766-106"><xref:System.Transactions.TransactionScope> Polega na tworzeniu transakcja otoczenia i Inicjowanie <xref:System.Transactions.Transaction.Current%2A> właściwości, które następnie są dostępne dla każdej pracy wykonywanej w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="cd766-106">The <xref:System.Transactions.TransactionScope> works by creating an ambient transaction and initializing the <xref:System.Transactions.Transaction.Current%2A> property, which can then be accessed by any work being executed on that thread.</span></span>  
  
 <span data-ttu-id="cd766-107">Aby uzyskać równoważne zachowanie w przepływie pracy, środowisko uruchomieniowe ma wykonywać dodatkowe zadania inicjowania <xref:System.Transactions.Transaction.Current%2A> przed wykonaniem każde działanie, ponieważ przepływ pracy nie przechowuje koligacji wątku między działaniami.</span><span class="sxs-lookup"><span data-stu-id="cd766-107">To get equivalent behavior in workflow, the runtime has to do the extra work of initializing <xref:System.Transactions.Transaction.Current%2A> before executing each activity because a workflow does not maintain thread affinity between activities.</span></span> <span data-ttu-id="cd766-108">Z tym obsługa środowiska uruchomieniowego efekty jest to, że podczas wykonywania przepływu pracy z <xref:System.Activities.WorkflowInvoker> wewnątrz <xref:System.Transactions.TransactionScope>, wszystkie działania dotrą do uruchamiania w kontekście transakcja otoczenia utworzone przez <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="cd766-108">With this runtime support, the resulting behavior is that when executing a workflow with <xref:System.Activities.WorkflowInvoker> inside a <xref:System.Transactions.TransactionScope>, all activities are guaranteed to run under the context of the ambient transaction created by the <xref:System.Transactions.TransactionScope>.</span></span>  
  
 <span data-ttu-id="cd766-109">Przepływ pracy może mieć tylko jeden transakcja otoczenia dla każdego wystąpienia przepływu pracy; Transakcje zagnieżdżone nie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="cd766-109">A workflow can have only a single ambient transaction for each workflow instance; nested transactions are not available.</span></span> <span data-ttu-id="cd766-110">Nawet jeśli przepływ pracy zawiera <xref:System.Activities.Statements.TransactionScope> aktywności, to nie tworzy nową transakcję wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="cd766-110">Even if the workflow contains a <xref:System.Activities.Statements.TransactionScope> activity, this does not create a new inner transaction.</span></span> <span data-ttu-id="cd766-111">Zamiast tego ponownie to transakcja otoczenia, który został utworzony poza przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="cd766-111">Instead, this reuses the ambient transaction that was created outside the workflow.</span></span>  
  
 <span data-ttu-id="cd766-112">Przykład rozpoczyna nową <xref:System.Transactions.TransactionScope>, wyświetla identyfikator transakcji i rozpocznie się za pomocą przepływu pracy <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="cd766-112">The sample begins a new <xref:System.Transactions.TransactionScope>, prints the transaction ID and begins a workflow using <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="cd766-113">Przepływ pracy drukuje transakcji identyfikator ponownie, pokazujący, że jest tej samej transakcji, a następnie uruchamia <xref:System.Activities.Statements.TransactionScope>, następnie kończy.</span><span class="sxs-lookup"><span data-stu-id="cd766-113">The workflow prints the transaction ID again, showing that it is the same transaction, then runs a <xref:System.Activities.Statements.TransactionScope>, then completes.</span></span> <span data-ttu-id="cd766-114"><xref:System.Activities.WorkflowInvoker.Invoke%2A> Wywołać <xref:System.Activities.WorkflowInvoker> jest synchroniczne, więc oryginalnego wątku blokuje do momentu ukończenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cd766-114">The <xref:System.Activities.WorkflowInvoker.Invoke%2A> call on <xref:System.Activities.WorkflowInvoker> is synchronous so the original thread blocks until the workflow completes.</span></span> <span data-ttu-id="cd766-115">Po zakończeniu przepływu pracy zakończeniu transakcji, a zasoby usunięte.</span><span class="sxs-lookup"><span data-stu-id="cd766-115">Once the workflow is complete, the transaction is completed and resources disposed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cd766-116">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="cd766-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="cd766-117">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ImperativeTransactionSample.sln.</span><span class="sxs-lookup"><span data-stu-id="cd766-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ImperativeTransactionSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="cd766-118">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="cd766-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="cd766-119">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="cd766-119">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cd766-120">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cd766-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cd766-121">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cd766-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cd766-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="cd766-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cd766-123">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cd766-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`  
  
## <a name="see-also"></a><span data-ttu-id="cd766-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd766-124">See Also</span></span>
