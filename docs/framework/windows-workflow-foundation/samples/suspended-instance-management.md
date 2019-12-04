---
title: Zarządzanie wstrzymanymi wystąpieniami
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 3f1f4f8edcbe0e05067d3ca739ef3d5f4fe4d798
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715943"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="73fce-102">Zarządzanie wstrzymanymi wystąpieniami</span><span class="sxs-lookup"><span data-stu-id="73fce-102">Suspended Instance Management</span></span>
<span data-ttu-id="73fce-103">Ten przykład pokazuje, jak zarządzać wystąpieniami przepływów pracy, które zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="73fce-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="73fce-104">Domyślna akcja dla <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> jest `AbandonAndSuspend`.</span><span class="sxs-lookup"><span data-stu-id="73fce-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="73fce-105">Oznacza to, że domyślnie Nieobsłużone wyjątki zgłaszane z wystąpienia przepływu pracy hostowanego w <xref:System.ServiceModel.WorkflowServiceHost> spowodują, że wystąpienie zostanie usunięte z pamięci (porzucone) i trwałe/utrwalone wersje wystąpienia zostanie oznaczone jako wstrzymane.</span><span class="sxs-lookup"><span data-stu-id="73fce-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="73fce-106">Nie będzie można uruchomić wstrzymanego wystąpienia przepływu pracy, dopóki nie zostanie ono zawieszone.</span><span class="sxs-lookup"><span data-stu-id="73fce-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="73fce-107">Przykład pokazuje, jak można zaimplementować narzędzie wiersza polecenia, aby wykonać zapytanie o wstrzymane wystąpienia oraz jak dać użytkownikowi możliwość wznowienia lub zakończenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="73fce-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="73fce-108">W tym przykładzie usługa przepływu pracy celowo zgłasza wyjątek, powodując jego zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="73fce-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="73fce-109">Narzędzia wiersza polecenia można następnie użyć, aby wykonać zapytanie dotyczące wystąpienia, a następnie wznowić lub przerwać wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="73fce-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="73fce-110">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="73fce-110">Demonstrates</span></span>
 <span data-ttu-id="73fce-111"><xref:System.ServiceModel.WorkflowServiceHost> z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> i <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> w Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="73fce-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="73fce-112">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="73fce-112">Discussion</span></span>
 <span data-ttu-id="73fce-113">Narzędzie wiersza polecenia zaimplementowane w tym przykładzie jest specyficzne dla implementacji magazynu wystąpień SQL, która jest dostarczana w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73fce-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="73fce-114">Jeśli masz niestandardową implementację magazynu wystąpień, możesz dostosować to narzędzie, zastępując implementacje `WorkflowInstanceCommand` w przykładzie z implementacjami specyficznymi dla Twojego magazynu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="73fce-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="73fce-115">Podana implementacja uruchamia polecenia SQL względem magazynu wystąpień SQL bezpośrednio w celu wyświetlenia listy wstrzymanych wystąpień i opiera się na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> dodane do <xref:System.ServiceModel.WorkflowServiceHost> w celu wznowienia lub zakończenia wystąpień.</span><span class="sxs-lookup"><span data-stu-id="73fce-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="73fce-116">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="73fce-116">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="73fce-117">Ten przykład wymaga włączenia następujących składników systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="73fce-117">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="73fce-118">Serwer usługi kolejkowania komunikatów (MSMQ) firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="73fce-118">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="73fce-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="73fce-119">SQL Server Express</span></span>

2. <span data-ttu-id="73fce-120">Skonfiguruj bazę danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="73fce-120">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="73fce-121">W wierszu polecenia programu Visual Studio 2010 Uruchom polecenie "Setup. cmd" z przykładowego katalogu SuspendedInstanceManagement, który wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73fce-121">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="73fce-122">Tworzy bazę danych trwałości przy użyciu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="73fce-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="73fce-123">Jeśli baza danych trwałości już istnieje, zostanie usunięta i ponownie utworzona</span><span class="sxs-lookup"><span data-stu-id="73fce-123">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="73fce-124">Konfiguruje bazę danych do trwałości.</span><span class="sxs-lookup"><span data-stu-id="73fce-124">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="73fce-125">Dodaje usługi IIS APPPOOL\DefaultAppPool i NT AUTHORITY\Network do roli InstanceStoreUsers, która została zdefiniowana podczas konfigurowania bazy danych do trwałości.</span><span class="sxs-lookup"><span data-stu-id="73fce-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="73fce-126">Skonfiguruj kolejkę usługi.</span><span class="sxs-lookup"><span data-stu-id="73fce-126">Set up the service queue.</span></span>

    1. <span data-ttu-id="73fce-127">W programie Visual Studio 2010 kliknij prawym przyciskiem myszy projekt **SampleWorkflowApp** , a następnie kliknij pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="73fce-127">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="73fce-128">Kompiluj i uruchamiaj SampleWorkflowApp, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="73fce-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="73fce-129">Spowoduje to utworzenie wymaganej kolejki.</span><span class="sxs-lookup"><span data-stu-id="73fce-129">This will create the required queue.</span></span>

    3. <span data-ttu-id="73fce-130">Naciśnij klawisz **Enter** , aby zatrzymać SampleWorkflowApp.</span><span class="sxs-lookup"><span data-stu-id="73fce-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="73fce-131">Otwórz konsolę zarządzania komputerem, uruchamiając polecenie compmgmt. msc z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="73fce-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="73fce-132">Rozwiń węzeł **usługi i aplikacje**, kolejkowanie **komunikatów**, **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="73fce-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="73fce-133">Kliknij prawym przyciskiem myszy kolejkę **ReceiveTx** i wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="73fce-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="73fce-134">Wybierz kartę **zabezpieczenia** i zezwól **wszystkim** na posiadanie uprawnień do **odbierania wiadomości**, **wglądu wiadomości**i **wysyłania wiadomości**.</span><span class="sxs-lookup"><span data-stu-id="73fce-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="73fce-135">Teraz uruchom przykład.</span><span class="sxs-lookup"><span data-stu-id="73fce-135">Now, run the sample.</span></span>

    1. <span data-ttu-id="73fce-136">W programie Visual Studio 2010 ponownie uruchom projekt SampleWorkflowApp bez debugowania przez naciśnięcie **klawiszy CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="73fce-136">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="73fce-137">Dwa adresy punktów końcowych będą drukowane w oknie konsoli: jeden dla punktu końcowego aplikacji, a następnie inny z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="73fce-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="73fce-138">Tworzone jest wystąpienie przepływu pracy, a śledzenie rekordów dla tego wystąpienia pojawi się w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="73fce-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="73fce-139">Wystąpienie przepływu pracy spowoduje zgłoszenie wyjątku powodującego zawieszenie i przerwanie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="73fce-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="73fce-140">Narzędzia wiersza polecenia można następnie użyć do wykonania dalszych czynności na każdym z tych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="73fce-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="73fce-141">Składnia argumentów wiersza polecenia jest następująca::</span><span class="sxs-lookup"><span data-stu-id="73fce-141">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="73fce-142">Obsługiwane polecenia to: `Query`, `Resume`i `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="73fce-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="73fce-143">Przełącznik InstanceId jest wymagany tylko w przypadku operacji `Resume` i `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="73fce-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="73fce-144">Aby oczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="73fce-144">To cleanup (Optional)</span></span>

1. <span data-ttu-id="73fce-145">Otwórz konsolę zarządzania komputerem, uruchamiając polecenie compmgmt. msc z wiersza polecenia `vs2010`.</span><span class="sxs-lookup"><span data-stu-id="73fce-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="73fce-146">Rozwiń węzeł **usługi i aplikacje**, kolejkowanie **komunikatów**, **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="73fce-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="73fce-147">Usuń kolejkę **ReceiveTx** .</span><span class="sxs-lookup"><span data-stu-id="73fce-147">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="73fce-148">Aby usunąć bazę danych trwałości, uruchom polecenie Oczyść. cmd.</span><span class="sxs-lookup"><span data-stu-id="73fce-148">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73fce-149">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="73fce-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="73fce-150">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="73fce-150">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="73fce-151">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73fce-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="73fce-152">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="73fce-152">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
