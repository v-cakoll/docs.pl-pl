---
title: Wycofanie transakcji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aaebbb7fa2e6e0420243c32cb70c64092ea86fa7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-rollback"></a><span data-ttu-id="2307c-102">Wycofanie transakcji</span><span class="sxs-lookup"><span data-stu-id="2307c-102">Transaction Rollback</span></span>
<span data-ttu-id="2307c-103">W tym przykładzie przedstawiono sposób tworzenia niestandardowego <xref:System.Activities.NativeActivity> dostępu do otoczenia <xref:System.Activities.RuntimeTransactionHandle> uzyskać transakcja otoczenia i jawnie wycofać go.</span><span class="sxs-lookup"><span data-stu-id="2307c-103">This sample shows how to create a custom <xref:System.Activities.NativeActivity> that accesses the ambient <xref:System.Activities.RuntimeTransactionHandle> to get the ambient transaction and explicitly roll it back.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="2307c-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="2307c-104">Sample Details</span></span>  
 <span data-ttu-id="2307c-105">W przepływie pracy, transakcja jest automatycznie zakończona podczas peryferyjnych <xref:System.Activities.Statements.TransactionScope> lub <xref:System.ServiceModel.Activities.TransactedReceiveScope> zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="2307c-105">In workflow, a transaction is automatically completed when the outermost <xref:System.Activities.Statements.TransactionScope> or <xref:System.ServiceModel.Activities.TransactedReceiveScope> completes.</span></span>  <span data-ttu-id="2307c-106">Transakcja przedstawia niejawnie po nieobsługiwany wyjątek propaguje granicy zakresu.</span><span class="sxs-lookup"><span data-stu-id="2307c-106">A transaction implicitly rolls back when an unhandled exception propagates across the scope boundary.</span></span> <span data-ttu-id="2307c-107">Jednak może być czas, kiedy warto jawnie wycofać transakcji bez konieczności Zgłoś wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2307c-107">However, there may be times when it makes sense to explicitly roll back a transaction without having to throw an exception.</span></span> <span data-ttu-id="2307c-108">W takim przypadku można działania niestandardowe wycofywania jak w tym przykładzie jawnie przerwać transakcję otoczenia i podaj z powodu wyjątku opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="2307c-108">In this case, you can use the custom rollback activity like the one in this sample to explicitly abort the ambient transaction and provide an optional exception reason.</span></span>  
  
 <span data-ttu-id="2307c-109">`RollbackActivity` Jest <xref:System.Activities.NativeActivity> ponieważ wymaga dostępu do właściwości wykonywania, aby pobrać otoczenia <xref:System.Activities.RuntimeTransactionHandle>.</span><span class="sxs-lookup"><span data-stu-id="2307c-109">The `RollbackActivity` is a <xref:System.Activities.NativeActivity> as it requires access to the execution properties to get the ambient <xref:System.Activities.RuntimeTransactionHandle>.</span></span> <span data-ttu-id="2307c-110">W `Execute` metody, uzyskuje <xref:System.Activities.RuntimeTransactionHandle> i sprawdza, czy jest `null`, co oznacza, że działanie zostało użyte bez transakcja otoczenia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2307c-110">In the `Execute` method, it obtains the <xref:System.Activities.RuntimeTransactionHandle> and checks whether it is `null`, which indicates that the activity was used without an ambient run-time transaction.</span></span> <span data-ttu-id="2307c-111">Następnie uzyskuje transakcji, ponownie sprawdzanie czy `null` jest obecny.</span><span class="sxs-lookup"><span data-stu-id="2307c-111">It then obtains the transaction, again checking whether `null` is present.</span></span> <span data-ttu-id="2307c-112">Istnieje możliwość ma otoczenia <xref:System.Activities.RuntimeTransactionHandle> bez kiedykolwiek inicjowanie transakcja czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2307c-112">It is possible to have an ambient <xref:System.Activities.RuntimeTransactionHandle> without ever initializing a run-time transaction.</span></span> <span data-ttu-id="2307c-113">Na koniec przerywa transakcję wywołując <xref:System.Transactions.Transaction.Rollback%2A> i określenia wyjątku dostarczone przez użytkownika lub wyjątek ogólny, stwierdzający, że działanie wycofana transakcji.</span><span class="sxs-lookup"><span data-stu-id="2307c-113">Finally it aborts the transaction by calling <xref:System.Transactions.Transaction.Rollback%2A> and specifying either a user-provided exception or a generic exception that states that the activity rolled back the transaction.</span></span>  
  
 <span data-ttu-id="2307c-114">Pokaz przepływ pracy składa się z <xref:System.Activities.Statements.TransactionScope> którego treści Wyświetla stan transakcji przed i po `RollbackActivity` wykonuje.</span><span class="sxs-lookup"><span data-stu-id="2307c-114">The demonstration workflow consists of a <xref:System.Activities.Statements.TransactionScope> whose body prints the transaction status before and after the `RollbackActivity` executes.</span></span> <span data-ttu-id="2307c-115">Należy pamiętać, że mimo że transakcja została wycofana, <xref:System.Activities.Statements.TransactionScope> wykonuje się i nie przerwać przepływu pracy do chwili zakończenia treści.</span><span class="sxs-lookup"><span data-stu-id="2307c-115">Note that even though the transaction has been rolled back, the <xref:System.Activities.Statements.TransactionScope> executes to completion and does not abort the workflow until the body completes.</span></span> <span data-ttu-id="2307c-116">Przepływ pracy zostało przerwane, ponieważ <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> wartością domyślną właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="2307c-116">The workflow is aborted because the <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> property defaults to `true`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2307c-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="2307c-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="2307c-118">Załadowanie rozwiązania TransactionRollback.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2307c-118">Load the TransactionRollback.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="2307c-119">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2307c-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="2307c-120">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="2307c-120">Press CTRL+F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2307c-121">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2307c-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2307c-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2307c-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2307c-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="2307c-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2307c-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2307c-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a><span data-ttu-id="2307c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2307c-125">See Also</span></span>  
 [<span data-ttu-id="2307c-126">Transakcje</span><span class="sxs-lookup"><span data-stu-id="2307c-126">Transactions</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
