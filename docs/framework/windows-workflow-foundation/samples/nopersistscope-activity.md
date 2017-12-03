---
title: "Działanie NoPersistScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a1f2703f79e68ec0dae00cf1dd81972d0f0ad889
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="nopersistscope-activity"></a><span data-ttu-id="e3857-102">Działanie NoPersistScope</span><span class="sxs-lookup"><span data-stu-id="e3857-102">NoPersistScope Activity</span></span>
<span data-ttu-id="e3857-103">W tym przykładzie pokazano, jak do manipulowania nie można serializować i możliwe do rozporządzania stanu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="e3857-103">This sample shows how to manipulate a non-serializable and disposable state within a workflow.</span></span> <span data-ttu-id="e3857-104">Jest ważne, przepływy pracy nie należy próbować zachować nie można serializować stanu, a także jest ważna w przypadku obiekty możliwe do rozporządzania na oczyszczenie po są one używane w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="e3857-104">It is important that workflows do not attempt to persist non-serializable state and it is also important for disposable objects to be cleaned up after they are used in workflow.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e3857-105">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="e3857-105">Demonstrates</span></span>  
 <span data-ttu-id="e3857-106">`NoPersistScope`Niestandardowe działania i projektanta.</span><span class="sxs-lookup"><span data-stu-id="e3857-106">`NoPersistScope` custom activity and designer.</span></span>  
  
## <a name="using-the-nopersistzone-activity"></a><span data-ttu-id="e3857-107">Za pomocą działania NoPersistZone</span><span class="sxs-lookup"><span data-stu-id="e3857-107">Using the NoPersistZone activity</span></span>  
 <span data-ttu-id="e3857-108">Po uruchomieniu przykładowego przepływu pracy działania niestandardowego o nazwie `CreateTextWriter` tworzy obiekt typu <xref:System.IO.TextWriter> i zapisuje je w zmiennej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e3857-108">When the sample workflow runs, a custom activity called `CreateTextWriter` creates an object of type <xref:System.IO.TextWriter> and saves it into a workflow variable.</span></span> <span data-ttu-id="e3857-109"><xref:System.IO.TextWriter>jest <xref:System.IDisposable> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3857-109"><xref:System.IO.TextWriter> is an <xref:System.IDisposable> object.</span></span> <span data-ttu-id="e3857-110">To <xref:System.IO.TextWriter>, która jest skonfigurowana do zapisu w pliku o nazwie "out.txt" w katalogu, w której jest uruchamiana próbki, jest używany przez <xref:System.Activities.Statements.WriteLine> działania echa dowolny tekst, wpisz w konsoli.</span><span class="sxs-lookup"><span data-stu-id="e3857-110">This <xref:System.IO.TextWriter>, which is configured to write to a file named ‘out.txt’ in the directory in which the sample runs, is used by a <xref:System.Activities.Statements.WriteLine> activity as it echoes any text you type in at the console.</span></span>  
  
 <span data-ttu-id="e3857-111">Logika echo jest uruchamiany w ramach `NoPersistScope` działania (dla kodu jest również częścią tego przykładu), co zapobiega przepływu pracy są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="e3857-111">The echo logic runs within a `NoPersistScope` activity (the code for which is also part of this sample), which prevents the workflow from being persisted.</span></span> <span data-ttu-id="e3857-112">W przypadku wpisania w `unload` za pomocą konsoli hosta próby potrzebna na utrwalenie wystąpienia przepływu pracy, ale ponieważ przepływ pracy pozostaje w ramach limitu czasu tej operacji `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="e3857-112">If you type in `unload` at the console, the host attempts to persist the workflow instance but this operation times out because the workflow remains within a `NoPersistScope`.</span></span> <span data-ttu-id="e3857-113">Przepływ pracy używa również niestandardowego działania o nazwie `Dispose` można zlikwidować <xref:System.IO.TextWriter> obiekt po zakończeniu przepływu pracy przy jej użyciu.</span><span class="sxs-lookup"><span data-stu-id="e3857-113">The workflow also utilizes a custom activity called `Dispose` to dispose the <xref:System.IO.TextWriter> object when the workflow is finished using it.</span></span> <span data-ttu-id="e3857-114">`Dispose` Działanie znajduje się w obrębie <xref:System.Activities.Statements.TryCatch.Finally%2A> zablokować z <xref:System.Activities.Statements.TryCatch> działania, w którym <xref:System.IO.TextWriter> zmienna została zadeklarowana, aby upewnić się, że działa nawet wtedy, gdy wystąpią Wystąpił wyjątek podczas wykonywania bloku Try.</span><span class="sxs-lookup"><span data-stu-id="e3857-114">The `Dispose` activity is placed within the <xref:System.Activities.Statements.TryCatch.Finally%2A> block of the <xref:System.Activities.Statements.TryCatch> activity in which the <xref:System.IO.TextWriter> variable is declared, to ensure that it runs even if an exception should occur during execution of the Try block.</span></span>  
  
 <span data-ttu-id="e3857-115">Można wpisać w `exit` aby zakończyć wystąpienia przepływu pracy i zamknąć program.</span><span class="sxs-lookup"><span data-stu-id="e3857-115">You can type in `exit` to complete the workflow instance and exit the program.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="e3857-116">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="e3857-116">To run the sample</span></span>  
  
1.  <span data-ttu-id="e3857-117">Otwórz rozwiązanie NoPersistZone.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3857-117">Open the NoPersistZone.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="e3857-118">Skompiluj rozwiązanie, naciśnij kombinację klawiszy CTRL + SHIFT + B lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="e3857-118">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="e3857-119">Gdy kompilacja zakończyła się pomyślnie, naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu można również nacisnąć klawisze CTRL + F5 lub wybierz **uruchomić bez debugowania** z **Debugowania** menu, aby uruchomić bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="e3857-119">Once the build has succeeded, press F5 or select **Start Debugging** from the **Debug** menu alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="e3857-120">Do oczyszczania (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e3857-120">To cleanup (optional)</span></span>  
  
1.  <span data-ttu-id="e3857-121">Aby usunąć magazyn wystąpienia SQL, uruchom Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="e3857-121">To remove the SQL Instance Store, run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3857-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e3857-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3857-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e3857-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e3857-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e3857-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3857-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e3857-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`