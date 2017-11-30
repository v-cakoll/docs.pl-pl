---
title: "Użyj TransactedReceiveScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23117014b688f0b440da3cec8620023eaf212f71
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="use-of-transactedreceivescope"></a><span data-ttu-id="de3a6-102">Użyj TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="de3a6-102">Use of TransactedReceiveScope</span></span>
<span data-ttu-id="de3a6-103">Ten przykład przedstawia sposób uruchomienia przepływu transakcji od klienta do serwera przy użyciu <xref:System.Activities.Statements.TransactionScope> można utworzyć nowej transakcji na komputerze klienckim i <xref:System.ServiceModel.Activities.TransactedReceiveScope> do odbierania wiadomości z przesłanej transakcji i zakres okres istnienia transakcji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="de3a6-103">This sample shows how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span> <span data-ttu-id="de3a6-104">Przykład zawiera dwa projekty, które pełnienia ról klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="de3a6-104">The sample consists of two projects that fill the roles of client and server.</span></span>  
  
## <a name="client-application"></a><span data-ttu-id="de3a6-105">Aplikacja kliencka</span><span class="sxs-lookup"><span data-stu-id="de3a6-105">Client Application</span></span>  
 <span data-ttu-id="de3a6-106">Aplikacja kliencka uruchamia przepływ pracy, który wyświetla identyfikator transakcji rozproszonej, wysyła wiadomość do serwera, przepływu transakcji, otrzyma odpowiedź, ponownie wyświetla identyfikator transakcji rozproszonej i zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="de3a6-106">The client application runs a workflow that prints the distributed transaction ID, sends a message to the server, flows the transaction, receives the reply, prints the distributed transaction ID again and completes.</span></span> <span data-ttu-id="de3a6-107">Identyfikator transakcji rozproszonej to początkowo odbitek, ma pusty identyfikator GUID, ponieważ transakcja jest nadal tylko lokalnych.</span><span class="sxs-lookup"><span data-stu-id="de3a6-107">When the distributed transaction ID is initially prints, it is an empty GUID as the transaction is still only local.</span></span>  
  
## <a name="server-application"></a><span data-ttu-id="de3a6-108">Serwer aplikacji</span><span class="sxs-lookup"><span data-stu-id="de3a6-108">Server Application</span></span>  
 <span data-ttu-id="de3a6-109">Przypomina Projekt serwera, jednak przepływu pracy znajduje się w <xref:System.ServiceModel.Activities.WorkflowServiceHost> ponieważ go musi nasłuchiwać na punkt końcowy komunikat z klienta.</span><span class="sxs-lookup"><span data-stu-id="de3a6-109">The server project is similar, however, the workflow is hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> because it must listen on an endpoint for the message from the client.</span></span> <span data-ttu-id="de3a6-110">Przepływ pracy skupia się na <xref:System.ServiceModel.Activities.TransactedReceiveScope>, który odbiera przesłanej transakcji od klienta, wyświetla komunikat, który został wysłany, wyświetla identyfikator transakcji rozproszonej i wysyła odpowiedź do klienta.</span><span class="sxs-lookup"><span data-stu-id="de3a6-110">The workflow is centered on the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, which receives the flowed transaction from the client, prints the message that was sent, prints the distributed transaction ID and sends the reply to the client.</span></span> <span data-ttu-id="de3a6-111">Identyfikator transakcji rozproszonej, jest teraz niepustego identyfikatora GUID, a jeśli działanie obsługujący transakcji został dodany do treści <xref:System.ServiceModel.Activities.TransactedReceiveScope>, jego jest wykonywany w transakcji.</span><span class="sxs-lookup"><span data-stu-id="de3a6-111">The distributed transaction ID is now a non-empty GUID and if a transaction-aware activity was added to the body of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, it would execute under the flowed transaction.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="de3a6-112">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="de3a6-112">To run the sample</span></span>  
  
1.  <span data-ttu-id="de3a6-113">Otwórz rozwiązanie TransactedReceiveScope.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de3a6-113">Open the TransactedReceiveScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="de3a6-114">Skompiluj rozwiązanie, naciśnij kombinację klawiszy CTRL + SHIFT + B lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="de3a6-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="de3a6-115">Gdy kompilacja zakończyła się pomyślnie, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**.</span><span class="sxs-lookup"><span data-stu-id="de3a6-115">Once the build has succeeded, right-click the solution and select **Set Startup Projects**.</span></span> <span data-ttu-id="de3a6-116">W oknie dialogowym wybierz **wiele projektów startowych** i upewnij się, Akcja dla obu projektów jest **Start**.</span><span class="sxs-lookup"><span data-stu-id="de3a6-116">From the dialog, select **Multiple Startup Projects** and ensure the action for both projects is **Start**.</span></span>  
  
4.  <span data-ttu-id="de3a6-117">Naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu.</span><span class="sxs-lookup"><span data-stu-id="de3a6-117">Press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="de3a6-118">Alternatywnie, naciśnij klawisze CTRL + F5 lub wybierz **uruchomić bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="de3a6-118">Alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de3a6-119">Serwer musi być uruchomiona przed uruchomieniem klienta.</span><span class="sxs-lookup"><span data-stu-id="de3a6-119">The server must be running prior to starting the client.</span></span> <span data-ttu-id="de3a6-120">Dane wyjściowe z okna konsoli obsługującego usługę wskazuje, kiedy został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="de3a6-120">The output from the console window hosting the service indicates when it has started.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="de3a6-121">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="de3a6-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="de3a6-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="de3a6-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="de3a6-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="de3a6-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="de3a6-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="de3a6-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`