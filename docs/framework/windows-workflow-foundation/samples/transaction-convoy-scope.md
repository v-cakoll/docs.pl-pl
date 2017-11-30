---
title: "Zakres który transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b5fc8834fb72163a615633d81232e25768683278
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-convoy-scope"></a><span data-ttu-id="2e888-102">Zakres który transakcji</span><span class="sxs-lookup"><span data-stu-id="2e888-102">Transaction Convoy Scope</span></span>
<span data-ttu-id="2e888-103">Ten przykład przedstawia sposób tworzenia równoległych który wiadomości wzorzec działania w połączeniu z <xref:System.ServiceModel.Activities.TransactedReceiveScope> do modelowania protokołu, na której liczba operacji może się zdarzyć w dowolnej kolejności, wszystkie w tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="2e888-103">This sample demonstrates how to create a Parallel Convoy messaging activity pattern in conjunction with a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to model a protocol where a number of operations can happen in any order all under the same transaction.</span></span> <span data-ttu-id="2e888-104">W tym przykładzie również pokazano, jak <xref:System.ServiceModel.Activities.TransactedReceiveScope> automatycznie tworzy nową transakcję, gdy jeden jest nie umieszczane na serwerze, więc klienta nie powoduje użycie wszystkich transakcji.</span><span class="sxs-lookup"><span data-stu-id="2e888-104">This sample also demonstrates how a <xref:System.ServiceModel.Activities.TransactedReceiveScope> automatically creates a new transaction when one is not flowed to the server, so the client does not make use of any transactions.</span></span>  
  
 <span data-ttu-id="2e888-105">Przykład zawiera dwa projekty przepływu pracy, które reprezentują klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="2e888-105">The sample consists of two workflow projects that represent the client and server.</span></span> <span data-ttu-id="2e888-106">Projekt klienta uruchamia przepływ pracy, który rozpoczyna się od wysyłania komunikatu do ładowania początkowego serwera przepływu pracy, które inicjuje korelację i uruchamia transakcyjne zakresu w pozostałej części działania obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2e888-106">The client project runs a workflow that begins by sending a message to bootstrap the server workflow, which initializes a correlation and starts a transactional scope for the remainder of the messaging activities.</span></span> <span data-ttu-id="2e888-107">Klient <xref:System.Activities.Statements.Sequence> działania zawiera wstępne <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> pary, a następnie <xref:System.Activities.Statements.Parallel> działania o trzy gałęzie.</span><span class="sxs-lookup"><span data-stu-id="2e888-107">The client <xref:System.Activities.Statements.Sequence> activity contains an initial <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> pair and then a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="2e888-108">Każda gałąź wysyła komunikat jednokierunkowy do serwera.</span><span class="sxs-lookup"><span data-stu-id="2e888-108">Each branch sends a one-way message to the server.</span></span> <span data-ttu-id="2e888-109"><xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Właściwość <xref:System.Activities.Statements.Parallel> działanie ma ustawioną wartość `false` tak, aby wykonać wszystkie trzy gałęzie.</span><span class="sxs-lookup"><span data-stu-id="2e888-109">The <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> property of the <xref:System.Activities.Statements.Parallel> activity is set to `false` so that all three branches complete.</span></span>  
  
 <span data-ttu-id="2e888-110">Przepływ pracy serwera jest podobny do przepływu pracy klienta, z wyjątkiem działania obsługi komunikatów są ukierunkowane na komunikację po stronie serwera i są zawarte w <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania, aby wszystkie pracy wykonywanej wykonuje w tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="2e888-110">The server workflow is similar to the client workflow except the messaging activities are oriented towards the server side of the communication and they are contained within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity so that all work done executes under the same transaction.</span></span> <span data-ttu-id="2e888-111">Po odebraniu pierwszego komunikatu na serwerze transakcji jest tworzony i staje się w zakresie otaczającym <xref:System.ServiceModel.Activities.TransactedReceiveScope> body, tak aby wszystkie działania w tym zakresie mogą uzyskiwać dostęp do transakcji.</span><span class="sxs-lookup"><span data-stu-id="2e888-111">When the first message is received on the server, a transaction is created and is made ambient for the scope of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> body so that any activity within this scope can access the transaction.</span></span> <span data-ttu-id="2e888-112">Dzięki temu wszystkie odbiera wykonywanie równoległe.</span><span class="sxs-lookup"><span data-stu-id="2e888-112">After this, all receives execute in parallel.</span></span> <span data-ttu-id="2e888-113">Odbiera wszystkie musi wykonać tylko raz w sposób opisany w stan ukończenia działania równoległe.</span><span class="sxs-lookup"><span data-stu-id="2e888-113">All receives must execute exactly once as described by the completion condition on the parallel activity.</span></span> <span data-ttu-id="2e888-114">Istnieje punkt niejawne trwałości na końcu <xref:System.ServiceModel.Activities.TransactedReceiveScope> treści i operacji trwałości również jest wykonywane w ramach tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="2e888-114">An implicit persistence point exists at the end of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> body and the persistence operation is also executed under the same transaction.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2e888-115">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="2e888-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="2e888-116">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ParallelConvoySample.sln.</span><span class="sxs-lookup"><span data-stu-id="2e888-116">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ParallelConvoySample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2e888-117">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="2e888-117">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2e888-118">Upewnij się, że oba projekty są ustawione na uruchomienie.</span><span class="sxs-lookup"><span data-stu-id="2e888-118">Ensure both projects are set to start.</span></span>  
  
    1.  <span data-ttu-id="2e888-119">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**.</span><span class="sxs-lookup"><span data-stu-id="2e888-119">In **Solution Explorer**, right-click the solution and select **Set Startup Projects**.</span></span>  
  
    2.  <span data-ttu-id="2e888-120">Wybierz **wiele projektów startowych** i upewnij się, ustawiono akcję dla obu projektów **Start**.</span><span class="sxs-lookup"><span data-stu-id="2e888-120">Select **Multiple Startup Projects** and ensure the action for both projects is set to **Start**.</span></span>  
  
4.  <span data-ttu-id="2e888-121">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="2e888-121">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="2e888-122">Serwer wydruku `Server is running`, co oznacza serwera jest gotowy.</span><span class="sxs-lookup"><span data-stu-id="2e888-122">The server prints `Server is running`, which indicates the server is ready.</span></span>  
  
     <span data-ttu-id="2e888-123">Naciśnij dowolny klawisz, w oknie konsoli klienta do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="2e888-123">Press any key in the client console window to start the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e888-124">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2e888-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e888-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2e888-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2e888-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="2e888-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e888-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2e888-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`  
  
## <a name="see-also"></a><span data-ttu-id="2e888-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e888-128">See Also</span></span>
