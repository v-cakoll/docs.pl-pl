---
title: Zarządzanie wstrzymanymi wystąpieniami
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: c23d2dfd48ecb57a3fb418734c916586178986e9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622421"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="41d9b-102">Zarządzanie wstrzymanymi wystąpieniami</span><span class="sxs-lookup"><span data-stu-id="41d9b-102">Suspended Instance Management</span></span>
<span data-ttu-id="41d9b-103">Niniejszy przykład pokazuje, jak zarządzać wystąpienia przepływu pracy, które zostało zawieszone.</span><span class="sxs-lookup"><span data-stu-id="41d9b-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="41d9b-104">Domyślna akcja dla <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> jest `AbandonAndSuspend`.</span><span class="sxs-lookup"><span data-stu-id="41d9b-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="41d9b-105">Oznacza to, że domyślnie nieobsługiwanych wyjątków zgłoszonych z wystąpienia przepływu pracy hostowane w <xref:System.ServiceModel.WorkflowServiceHost> spowoduje wystąpienie Aby zostać usunięty z pamięci (porzucone) i trwałość/utrwalona wersję wystąpienia został oznaczony jako zawieszone.</span><span class="sxs-lookup"><span data-stu-id="41d9b-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="41d9b-106">Wystąpienie Wstrzymany przepływ pracy nie będzie działać, dopóki nie zostało zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="41d9b-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="41d9b-107">Przedstawia przykładowe, jak narzędzie wiersza polecenia można zaimplementować zapytania dla wystąpień wstrzymania i udzielanie użytkownikowi opcję, aby wznowić lub zakończenie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="41d9b-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="41d9b-108">W tym przykładzie Usługa przepływu pracy celowo zgłasza wyjątek, co powoduje wstrzymane.</span><span class="sxs-lookup"><span data-stu-id="41d9b-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="41d9b-109">Narzędzie wiersza polecenia można następnie zapytania dla tego wystąpienia i następnie Wznów lub zakończyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="41d9b-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="41d9b-110">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="41d9b-110">Demonstrates</span></span>
 <span data-ttu-id="41d9b-111"><xref:System.ServiceModel.WorkflowServiceHost> za pomocą <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> i <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> w Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="41d9b-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="41d9b-112">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="41d9b-112">Discussion</span></span>
 <span data-ttu-id="41d9b-113">Narzędzie wiersza polecenia, w tym przykładzie jest specyficzne dla implementacji magazynu wystąpienia SQL, który jest dostarczany w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41d9b-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="41d9b-114">Jeśli masz niestandardową implementację magazyn wystąpienia, a następnie to narzędzie można dostosować poprzez zastąpienie `WorkflowInstanceCommand` implementacji w przykładzie z implementacji, które są specyficzne dla sklepu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="41d9b-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="41d9b-115">Podana implementacji uruchamia polecenia SQL względem magazynu wystąpienia SQL bezpośrednio po to, aby wyświetlić listę wystąpień wstrzymania i opiera się na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> dodane do <xref:System.ServiceModel.WorkflowServiceHost> w celu wznowienia lub zakończenie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="41d9b-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="41d9b-116">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="41d9b-116">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="41d9b-117">Ten przykładowy skrypt wymaga włączenia następujących składników Windows:</span><span class="sxs-lookup"><span data-stu-id="41d9b-117">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="41d9b-118">Microsoft Message Queues (MSMQ) Server</span><span class="sxs-lookup"><span data-stu-id="41d9b-118">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="41d9b-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="41d9b-119">SQL Server Express</span></span>

2. <span data-ttu-id="41d9b-120">Konfigurowanie bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="41d9b-120">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="41d9b-121">Z wiersza polecenia programu Visual Studio 2010 należy uruchomić "plik setup.cmd" z katalogu przykładowe SuspendedInstanceManagement, który wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="41d9b-121">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="41d9b-122">Tworzy bazę danych trwałości za pomocą programu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="41d9b-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="41d9b-123">Jeśli baza danych stanów trwałych już istnieje, a następnie jest porzucona i utworzona ponownie</span><span class="sxs-lookup"><span data-stu-id="41d9b-123">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="41d9b-124">Konfiguruje bazę danych do stanu trwałego.</span><span class="sxs-lookup"><span data-stu-id="41d9b-124">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="41d9b-125">Dodaje IIS APPPOOL\DefaultAppPool i NT AUTHORITY\Network Service do roli InstanceStoreUsers, która została określona podczas konfigurowania bazy danych dla trwałości.</span><span class="sxs-lookup"><span data-stu-id="41d9b-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="41d9b-126">Konfigurowanie usługi kolejki.</span><span class="sxs-lookup"><span data-stu-id="41d9b-126">Set up the service queue.</span></span>

    1. <span data-ttu-id="41d9b-127">W programie Visual Studio 2010, kliknij prawym przyciskiem myszy **SampleWorkflowApp** projektu, a następnie kliknij przycisk **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="41d9b-127">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="41d9b-128">Kompilowanie i uruchamianie SampleWorkflowApp, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="41d9b-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="41d9b-129">Spowoduje to utworzenie wymaganych kolejki.</span><span class="sxs-lookup"><span data-stu-id="41d9b-129">This will create the required queue.</span></span>

    3. <span data-ttu-id="41d9b-130">Naciśnij klawisz **Enter** przestanie SampleWorkflowApp.</span><span class="sxs-lookup"><span data-stu-id="41d9b-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="41d9b-131">Otwórz konsolę Zarządzanie komputerem, uruchamiając Compmgmt.msc z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="41d9b-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="41d9b-132">Rozwiń **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="41d9b-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="41d9b-133">Kliknij prawym przyciskiem myszy **ReceiveTx** kolejki, a następnie wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="41d9b-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="41d9b-134">Wybierz **zabezpieczeń** kartę i umożliwiają **wszyscy** musi mieć uprawnienia do **odbieranie wiadomości**, **wglądu do wiadomości**, i  **Wyślij wiadomość**.</span><span class="sxs-lookup"><span data-stu-id="41d9b-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="41d9b-135">Teraz uruchom przykład.</span><span class="sxs-lookup"><span data-stu-id="41d9b-135">Now, run the sample.</span></span>

    1. <span data-ttu-id="41d9b-136">W programie Visual Studio 2010, SampleWorkflowApp project należy ponownie uruchomić bez debugowania, naciskając klawisz **kombinację klawiszy Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="41d9b-136">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="41d9b-137">Dwa adresy punktów końcowych, które będą wypisywane w oknie konsoli: jeden dla punktu końcowego aplikacji i następnie inne z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="41d9b-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="41d9b-138">Wystąpienie przepływu pracy zostanie utworzony i śledzenia rekordów dla tego wystąpienia zostaną wyświetlone w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="41d9b-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="41d9b-139">Wystąpienie przepływu pracy spowoduje zgłoszenie wyjątku powoduje wystąpienie aby je zawieszać i zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="41d9b-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="41d9b-140">Narzędzie wiersza polecenia, następnie może służyć do podejmowania dalszych działań na dowolnym z tych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="41d9b-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="41d9b-141">Składnia służąca do argumentów wiersza polecenia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="41d9b-141">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="41d9b-142">Są obsługiwane polecenia: `Query`, `Resume`, i `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="41d9b-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="41d9b-143">Identyfikator wystąpienia przełącznika jest wymagane tylko dla `Resume` i `Terminate` operacji.</span><span class="sxs-lookup"><span data-stu-id="41d9b-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="41d9b-144">Aby oczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="41d9b-144">To cleanup (Optional)</span></span>

1. <span data-ttu-id="41d9b-145">Otwórz konsolę Zarządzanie komputerem, uruchamiając Compmgmt.msc z `vs2010` wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="41d9b-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="41d9b-146">Rozwiń **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="41d9b-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="41d9b-147">Usuń **ReceiveTx** kolejki.</span><span class="sxs-lookup"><span data-stu-id="41d9b-147">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="41d9b-148">Aby usunąć bazy danych trwałości, uruchom cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="41d9b-148">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="41d9b-149">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="41d9b-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="41d9b-150">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="41d9b-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="41d9b-151">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="41d9b-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41d9b-152">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="41d9b-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
