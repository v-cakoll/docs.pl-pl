---
title: "Obiekt StateMachine scenariusz przy użyciu kombinacji schematu blokowego i pobrania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39ae1be025e3b888fff8b46ebbc45832c218dda7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a><span data-ttu-id="90220-102">Obiekt StateMachine scenariusz przy użyciu kombinacji schematu blokowego i pobrania</span><span class="sxs-lookup"><span data-stu-id="90220-102">StateMachine Scenario Using a Combination of FlowChart and Pick</span></span>
<span data-ttu-id="90220-103">W tym przykładzie pokazano, jak wdrożyć scenariusz proste stopera, przy użyciu kombinacji <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Pick> działań.</span><span class="sxs-lookup"><span data-stu-id="90220-103">This sample demonstrates how to implement a simple stopwatch scenario using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span> <span data-ttu-id="90220-104">Używa odbierania i wysyłania w działaniu wybierz do nasłuchiwania zdarzeń stopera.</span><span class="sxs-lookup"><span data-stu-id="90220-104">It uses Receive and Send within the Pick activity to listen for stopwatch events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="90220-105">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="90220-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="90220-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="90220-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="90220-107">Jeśli ten katalog nie istnieje, przejdź do (stronę pobierania), aby pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="90220-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="90220-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="90220-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a><span data-ttu-id="90220-109">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="90220-109">Sample Details</span></span>  
 <span data-ttu-id="90220-110">W poniższej tabeli wymieniono projekty w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="90220-110">The following table lists the projects in this sample.</span></span>  
  
|<span data-ttu-id="90220-111">Nazwa projektu</span><span class="sxs-lookup"><span data-stu-id="90220-111">Project Name</span></span>|<span data-ttu-id="90220-112">Opis</span><span class="sxs-lookup"><span data-stu-id="90220-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="90220-113">StopWatchService</span><span class="sxs-lookup"><span data-stu-id="90220-113">StopWatchService</span></span>|<span data-ttu-id="90220-114">Ten projekt zawiera implementację automatu stanów przykładowej stopera przy użyciu kombinacji <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Pick> działań.</span><span class="sxs-lookup"><span data-stu-id="90220-114">This project contains the implementation of a state machine for the stopwatch sample using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span><br /><br /> <span data-ttu-id="90220-115"><xref:System.Activities.Statements.Pick> Działanie ma 3 <xref:System.Activities.Statements.PickBranch> instrukcje <xref:System.Activities.Statements.Pick.Branches%2A> właściwość, która nasłuchuje `GetStart`, `GetStop` i `GetOff` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="90220-115">The <xref:System.Activities.Statements.Pick> activity has 3 <xref:System.Activities.Statements.PickBranch> statements within the <xref:System.Activities.Statements.Pick.Branches%2A> property that listen for `GetStart`, `GetStop` and `GetOff` events.</span></span> <span data-ttu-id="90220-116">Oparte na zdarzeniu przychodzących, aktywować Wyzwalacze dla jednej z gałęzi i odpowiadający mu <xref:System.Activities.Statements.PickBranch.Action%2A> zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="90220-116">Based on the incoming event, the triggers for one of the branches activate and the corresponding <xref:System.Activities.Statements.PickBranch.Action%2A> is triggered.</span></span> <span data-ttu-id="90220-117">W <xref:System.Activities.Statements.PickBranch.Action%2A> właściwości, Brak <xref:System.Activities.Statements.Switch%601> instrukcji, która ocenia, czy przejście jest uzasadnione przejścia i jeśli istnieje, `currentState` właściwości jest zaktualizowany stan przechodzenie i wysłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="90220-117">In the <xref:System.Activities.Statements.PickBranch.Action%2A> property, there is a <xref:System.Activities.Statements.Switch%601> statement that evaluates whether the transition is a legitimate transition and if it is, the `currentState` property is updated to the transitioning state and sent to the client.</span></span><br /><br /> <span data-ttu-id="90220-118"><xref:System.Activities.Statements.FlowDecision> Działania na końcu <xref:System.Activities.Statements.Flowchart> ocenia `currentState` właściwości w celu określenia, czy stan jest terminala.</span><span class="sxs-lookup"><span data-stu-id="90220-118">The <xref:System.Activities.Statements.FlowDecision> activity at the end of the <xref:System.Activities.Statements.Flowchart> evaluates the `currentState` property to determine whether the state is terminal.</span></span> <span data-ttu-id="90220-119">Jeśli tak jest, kończy się przepływu pracy; inny sposób kontroluje pętle powrót do początku <xref:System.Activities.Statements.Pick> działania, w którym przepływ pracy czeka na więcej zdarzeń stopera.</span><span class="sxs-lookup"><span data-stu-id="90220-119">If it is, the workflow ends; otherwise control loops back to the start of the <xref:System.Activities.Statements.Pick> activity where the workflow waits for more stopwatch events.</span></span>|  
|<span data-ttu-id="90220-120">StopWatchClient</span><span class="sxs-lookup"><span data-stu-id="90220-120">StopWatchClient</span></span>|<span data-ttu-id="90220-121">Jest to prosty sekwencyjny przepływ pracy aplikacja konsolowa, która wysyła różnych zdarzeń stopera przy prostego wysłać lub odebrać kombinacji działania.</span><span class="sxs-lookup"><span data-stu-id="90220-121">This is a simple sequential workflow console application that sends various stopwatch events with simple Send or Receive activity combinations.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="90220-122">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="90220-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="90220-123">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania StateMachineWithPick.sln.</span><span class="sxs-lookup"><span data-stu-id="90220-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open StateMachineWithPick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="90220-124">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="90220-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="90220-125">Uruchom StopWatchService.exe z [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] jako administrator, kliknięcie prawym przyciskiem myszy plik .exe i wybierając **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="90220-125">Start the StopWatchService.exe from [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] as an administrator by right clicking the .exe file and selecting **Run as administrator**.</span></span>  
  
    1.  <span data-ttu-id="90220-126">Przejdź do folderu StateMachineWithPick\CS\StopWatchService\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="90220-126">Navigate to the StateMachineWithPick\CS\StopWatchService\bin\Debug folder.</span></span>  
  
    2.  <span data-ttu-id="90220-127">Kliknij prawym przyciskiem myszy plik StopWatchService.exe i wybierz **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="90220-127">Right-click the StopWatchService.exe file and select **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="90220-128">Uruchom aplikację klienta StopWatchClient z poziomu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="90220-128">Start the StopWatchClient client application from within [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    1.  <span data-ttu-id="90220-129">W **Eksploratora rozwiązań**, wybierz pozycję **StopWatchClient** projekt i kliknij prawym przyciskiem myszy **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="90220-129">In **Solution Explorer**, select the **StopWatchClient** project and right-click **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="90220-130">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="90220-130">To run the solution, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="90220-131">Przejdź do okna konsoli dla StopWatchService.exe wyświetlić przejścia stanu.</span><span class="sxs-lookup"><span data-stu-id="90220-131">Switch back to the console window for the StopWatchService.exe to view the state transitions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="90220-132">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="90220-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="90220-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="90220-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="90220-134">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="90220-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="90220-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="90220-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`