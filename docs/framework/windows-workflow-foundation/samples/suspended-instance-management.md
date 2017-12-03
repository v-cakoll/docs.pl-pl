---
title: "Zarządzanie wystąpieniami wstrzymane"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24c94f93524f6b31b622c527da068379ce7e724d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="suspended-instance-management"></a><span data-ttu-id="9b75f-102">Zarządzanie wystąpieniami wstrzymane</span><span class="sxs-lookup"><span data-stu-id="9b75f-102">Suspended Instance Management</span></span>
<span data-ttu-id="9b75f-103">W tym przykładzie pokazano, jak zarządzać wystąpienia przepływu pracy, które zostało zawieszone.</span><span class="sxs-lookup"><span data-stu-id="9b75f-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="9b75f-104">Domyślnym działaniem <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> jest `AbandonAndSuspend`.</span><span class="sxs-lookup"><span data-stu-id="9b75f-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="9b75f-105">Oznacza to, że domyślnie nieobsługiwane wyjątki rzucane z wystąpieniem przepływu pracy hostowanych w <xref:System.ServiceModel.WorkflowServiceHost> spowoduje wystąpienie można usunąć z pamięci (porzucone) i wersji niezawodny/utrwalony wystąpienia może być oznaczony jako zawieszone.</span><span class="sxs-lookup"><span data-stu-id="9b75f-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="9b75f-106">Nie będzie można uruchamiać, dopóki zostanie Anulowano wystąpienie Wstrzymany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="9b75f-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>  
  
 <span data-ttu-id="9b75f-107">W przykładowych pokazano, jak narzędzie wiersza polecenia można zaimplementować zapytania dla wystąpień wstrzymania i sposobu przesyłania opcję, aby wznowić, lub przerywania wystąpienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9b75f-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="9b75f-108">W tym przykładzie usługi przepływu pracy celowo zgłasza wyjątek, co powoduje stanie zawieszone.</span><span class="sxs-lookup"><span data-stu-id="9b75f-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="9b75f-109">Narzędzie wiersza polecenia mogą następnie służyć do zapytania dla tego wystąpienia, a następnie Wznów lub przerywania wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="9b75f-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9b75f-110">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="9b75f-110">Demonstrates</span></span>  
 <span data-ttu-id="9b75f-111"><xref:System.ServiceModel.WorkflowServiceHost>z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> i <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> w [!INCLUDE[wf](../../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b75f-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9b75f-112">Omówienie</span><span class="sxs-lookup"><span data-stu-id="9b75f-112">Discussion</span></span>  
 <span data-ttu-id="9b75f-113">Narzędzie wiersza polecenia zaimplementowana w tym przykładzie jest specyficzna dla Implementacja magazynu wystąpienia SQL, który jest dostarczany w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b75f-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="9b75f-114">Jeśli masz niestandardowej implementacji w magazynie wystąpień, a następnie tego narzędzia można dostosować poprzez zastąpienie `WorkflowInstanceCommand` implementacji w przykładzie z implementacji, które są specyficzne dla sklepu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9b75f-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>  
  
 <span data-ttu-id="9b75f-115">Podana implementacji jest uruchamiana poleceń SQL dla magazynu wystąpienia SQL bezpośrednio, aby wyświetlić listę wystąpień zawieszone, i opiera się na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> dodane do <xref:System.ServiceModel.WorkflowServiceHost> Aby wznowić, lub przerwanie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9b75f-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9b75f-116">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="9b75f-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9b75f-117">W tym przykładzie wymaga włączenia następujące składniki systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="9b75f-117">This sample requires that the following Windows components are enabled:</span></span>  
  
    1.  <span data-ttu-id="9b75f-118">Wiadomości firmy Microsoft (MSMQ) kolejek serwera</span><span class="sxs-lookup"><span data-stu-id="9b75f-118">Microsoft Message Queues (MSMQ) Server</span></span>  
  
    2.  <span data-ttu-id="9b75f-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="9b75f-119">SQL Server Express</span></span>  
  
2.  <span data-ttu-id="9b75f-120">Konfigurowanie bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9b75f-120">Set up the SQL Server database.</span></span>  
  
    1.  <span data-ttu-id="9b75f-121">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia, uruchom "setup.cmd" w katalogu próbki SuspendedInstanceManagement, który wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9b75f-121">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>  
  
        1.  <span data-ttu-id="9b75f-122">Tworzy bazę danych trwałości przy użyciu programu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="9b75f-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="9b75f-123">Jeśli trwałości bazy danych już istnieje, a następnie jest porzucona i utworzona ponownie</span><span class="sxs-lookup"><span data-stu-id="9b75f-123">If the persistence database already exists, then it is dropped and re-created</span></span>  
  
        2.  <span data-ttu-id="9b75f-124">Konfiguruje bazę danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="9b75f-124">Sets up the database for persistence.</span></span>  
  
        3.  <span data-ttu-id="9b75f-125">Dodaje IIS APPPOOL\DefaultAppPool i NT AUTHORITY\Network Service do roli InstanceStoreUsers, która została określona podczas konfigurowania bazy danych dla trwałości.</span><span class="sxs-lookup"><span data-stu-id="9b75f-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>  
  
3.  <span data-ttu-id="9b75f-126">Konfigurowanie usługi kolejki.</span><span class="sxs-lookup"><span data-stu-id="9b75f-126">Set up the service queue.</span></span>  
  
    1.  <span data-ttu-id="9b75f-127">W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], kliknij prawym przyciskiem myszy **SampleWorkflowApp** projekt i kliknij przycisk **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="9b75f-127">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>  
  
    2.  <span data-ttu-id="9b75f-128">Kompilowanie i uruchamianie SampleWorkflowApp naciskając **F5**.</span><span class="sxs-lookup"><span data-stu-id="9b75f-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="9b75f-129">Spowoduje to utworzenie wymagane kolejki.</span><span class="sxs-lookup"><span data-stu-id="9b75f-129">This will create the required queue.</span></span>  
  
    3.  <span data-ttu-id="9b75f-130">Naciśnij klawisz **Enter** przestanie SampleWorkflowApp.</span><span class="sxs-lookup"><span data-stu-id="9b75f-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>  
  
    4.  <span data-ttu-id="9b75f-131">Otwórz konsolę Zarządzanie komputerem, uruchamiając Compmgmt.msc z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b75f-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>  
  
    5.  <span data-ttu-id="9b75f-132">Rozwiń węzeł **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="9b75f-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    6.  <span data-ttu-id="9b75f-133">Kliknij prawym przyciskiem myszy **ReceiveTx** kolejki, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9b75f-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>  
  
    7.  <span data-ttu-id="9b75f-134">Wybierz **zabezpieczeń** karcie i umożliwić **wszyscy** uprawnień do **odbieranie wiadomości**, **wglądu do wiadomości**, i  **Wyślij wiadomość**.</span><span class="sxs-lookup"><span data-stu-id="9b75f-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>  
  
4.  <span data-ttu-id="9b75f-135">Teraz uruchom próbkę.</span><span class="sxs-lookup"><span data-stu-id="9b75f-135">Now, run the sample.</span></span>  
  
    1.  <span data-ttu-id="9b75f-136">W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], uruchom ponownie projekt SampleWorkflowApp bez debugowania, naciskając klawisz **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="9b75f-136">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="9b75f-137">Dwa adresy punktów końcowych będą wypisywane w oknie konsoli: jeden dla punktu końcowego aplikacji, a następnie inne z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="9b75f-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="9b75f-138">Wystąpienie przepływu pracy jest tworzona i śledzenie rekordów dla tego wystąpienia zostaną wyświetlone w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="9b75f-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="9b75f-139">Wystąpienie przepływu pracy spowoduje zgłoszenie wyjątku powoduje wystąpienie można je zawieszać i zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="9b75f-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>  
  
    2.  <span data-ttu-id="9b75f-140">Narzędzie wiersza polecenia można następnie wykonywanie dodatkowych działań na żadnym z tych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="9b75f-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="9b75f-141">Składnia dla argumentów wiersza polecenia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="9b75f-141">The syntax for command line arguments is as follows::</span></span>  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         <span data-ttu-id="9b75f-142">Są obsługiwane polecenia: `Query`, `Resume`, i `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="9b75f-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="9b75f-143">Przełącznik identyfikator wystąpienia jest wymagana tylko dla `Resume` i `Terminate` operacji.</span><span class="sxs-lookup"><span data-stu-id="9b75f-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="9b75f-144">Do oczyszczania (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="9b75f-144">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="9b75f-145">Otwórz konsolę Zarządzanie komputerem, uruchamiając Compmgmt.msc z `vs2010` wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b75f-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>  
  
2.  <span data-ttu-id="9b75f-146">Rozwiń węzeł **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="9b75f-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="9b75f-147">Usuń **ReceiveTx** kolejki.</span><span class="sxs-lookup"><span data-stu-id="9b75f-147">Delete the **ReceiveTx** queue.</span></span>  
  
4.  <span data-ttu-id="9b75f-148">Aby usunąć bazę danych trwałości, uruchom cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="9b75f-148">To remove the persistence database, run cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b75f-149">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9b75f-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9b75f-150">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9b75f-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9b75f-151">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="9b75f-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9b75f-152">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9b75f-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
