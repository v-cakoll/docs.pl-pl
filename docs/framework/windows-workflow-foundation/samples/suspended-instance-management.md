---
title: Zarządzanie wstrzymanymi wystąpieniami
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 784ec3cdda8eedb188c3c776ed412ea40baf37ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182788"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="6777e-102">Zarządzanie wstrzymanymi wystąpieniami</span><span class="sxs-lookup"><span data-stu-id="6777e-102">Suspended Instance Management</span></span>
<span data-ttu-id="6777e-103">W tym przykładzie pokazano, jak zarządzać wystąpień przepływu pracy, które zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="6777e-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="6777e-104">Domyślną <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> akcją `AbandonAndSuspend`jest .</span><span class="sxs-lookup"><span data-stu-id="6777e-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="6777e-105">Oznacza to, że domyślnie nieobsługiwane wyjątki generowane <xref:System.ServiceModel.WorkflowServiceHost> z wystąpienia przepływu pracy hostowane w spowoduje wystąpienie, które mają być usuwane z pamięci (porzucone) i trwałe/utrwalone wersji wystąpienia, które mają być oznaczone jako zawieszone.</span><span class="sxs-lookup"><span data-stu-id="6777e-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="6777e-106">Wystąpienie zawieszonego przepływu pracy nie będzie można uruchomić, dopóki nie zostanie wstrzymane.</span><span class="sxs-lookup"><span data-stu-id="6777e-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="6777e-107">Przykład pokazuje, jak narzędzie wiersza polecenia można zaimplementować do wykonywania zapytań o zawieszone wystąpienia i jak dać użytkownikowi możliwość wznowienia lub zakończenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6777e-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="6777e-108">W tym przykładzie usługa przepływu pracy celowo zgłasza wyjątek, powodując, że zostanie zawieszony.</span><span class="sxs-lookup"><span data-stu-id="6777e-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="6777e-109">Narzędzie wiersza polecenia może następnie służyć do wykonywania kwerend dla wystąpienia, a następnie wznawiania lub zakończenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6777e-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6777e-110">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="6777e-110">Demonstrates</span></span>
 <span data-ttu-id="6777e-111"><xref:System.ServiceModel.WorkflowServiceHost>z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> i w Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="6777e-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="6777e-112">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="6777e-112">Discussion</span></span>
 <span data-ttu-id="6777e-113">Narzędzie wiersza polecenia zaimplementowane w tym przykładzie jest [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]specyficzne dla implementacji magazynu wystąpień SQL, która jest dostarczana w programie .</span><span class="sxs-lookup"><span data-stu-id="6777e-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="6777e-114">Jeśli masz niestandardową implementację magazynu wystąpień, możesz dostosować `WorkflowInstanceCommand` to narzędzie, zastępując implementacje w przykładzie implementacjami specyficznymi dla magazynu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="6777e-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="6777e-115">Podana implementacja uruchamia polecenia SQL względem magazynu wystąpień SQL bezpośrednio do <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> listy zawieszonych wystąpień i opiera się na dodane <xref:System.ServiceModel.WorkflowServiceHost> do w celu wznowienia lub zakończenia wystąpień.</span><span class="sxs-lookup"><span data-stu-id="6777e-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6777e-116">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="6777e-116">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6777e-117">W tym przykładzie wymaga włączenia następujących składników systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="6777e-117">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="6777e-118">Serwer kolejek komunikatów firmy Microsoft (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="6777e-118">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="6777e-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="6777e-119">SQL Server Express</span></span>

2. <span data-ttu-id="6777e-120">Konfigurowanie bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6777e-120">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="6777e-121">Z wiersza polecenia programu Visual Studio 2010 uruchom polecenie "setup.cmd" z przykładowego katalogu SuspendedInstanceManagement, który wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6777e-121">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="6777e-122">Tworzy bazę danych trwałości przy użyciu programu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="6777e-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="6777e-123">Jeśli baza danych trwałości już istnieje, zostanie ona porzucona i ponownie utworzona</span><span class="sxs-lookup"><span data-stu-id="6777e-123">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="6777e-124">Konfiguruje bazę danych dla trwałości.</span><span class="sxs-lookup"><span data-stu-id="6777e-124">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="6777e-125">Dodaje usługi IIS APPPOOL\DefaultAppPool i NT AUTHORITY\Network Service do roli InstanceStoreUsers, która została zdefiniowana podczas konfigurowania bazy danych pod kątem trwałości.</span><span class="sxs-lookup"><span data-stu-id="6777e-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="6777e-126">Skonfiguruj kolejkę usługi.</span><span class="sxs-lookup"><span data-stu-id="6777e-126">Set up the service queue.</span></span>

    1. <span data-ttu-id="6777e-127">W programie Visual Studio 2010 kliknij prawym przyciskiem myszy projekt **SampleWorkflowApp** i kliknij polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="6777e-127">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="6777e-128">Skompiluj i uruchom SampleWorkflowApp, naciskając **klawisz F5**.</span><span class="sxs-lookup"><span data-stu-id="6777e-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="6777e-129">Spowoduje to utworzenie wymaganej kolejki.</span><span class="sxs-lookup"><span data-stu-id="6777e-129">This will create the required queue.</span></span>

    3. <span data-ttu-id="6777e-130">Naciśnij **klawisz Enter,** aby zatrzymać plik SampleWorkflowApp.</span><span class="sxs-lookup"><span data-stu-id="6777e-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="6777e-131">Otwórz konsolę Zarządzanie komputerem, uruchamiając plik Compmgmt.msc w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6777e-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="6777e-132">Rozwiń **węzeł Usługi i aplikacje**, **Kolejkowanie wiadomości,** **Kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="6777e-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="6777e-133">Kliknij prawym przyciskiem myszy kolejkę **ReceiveTx** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6777e-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="6777e-134">Wybierz kartę **Zabezpieczenia** i **zezwalaj wszystkim** na uprawnienia do **odbierania wiadomości,** **wglądu**do wiadomości i **wysyłania wiadomości**.</span><span class="sxs-lookup"><span data-stu-id="6777e-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="6777e-135">Teraz uruchom próbkę.</span><span class="sxs-lookup"><span data-stu-id="6777e-135">Now, run the sample.</span></span>

    1. <span data-ttu-id="6777e-136">W programie Visual Studio 2010 uruchom ponownie projekt SampleWorkflowApp bez debugowania, naciskając **klawisze Ctrl+F5**.</span><span class="sxs-lookup"><span data-stu-id="6777e-136">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="6777e-137">W oknie konsoli zostaną wydrukowane dwa adresy punktów końcowych: jeden dla <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>punktu końcowego aplikacji, a drugi z pliku .</span><span class="sxs-lookup"><span data-stu-id="6777e-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="6777e-138">Następnie zostanie utworzone wystąpienie przepływu pracy, a rekordy śledzenia dla tego wystąpienia pojawią się w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="6777e-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="6777e-139">Wystąpienie przepływu pracy zda wyjątek powodujący zawieszenie i przerwanie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6777e-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="6777e-140">Narzędzie wiersza polecenia może następnie służyć do podejmowania dalszych działań na każdym z tych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="6777e-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="6777e-141">Składnia argumentów wiersza polecenia jest następująca::</span><span class="sxs-lookup"><span data-stu-id="6777e-141">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="6777e-142">Obsługiwane polecenia to: `Query`, `Resume`, `Terminate`i .</span><span class="sxs-lookup"><span data-stu-id="6777e-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="6777e-143">Przełącznik InstanceId jest wymagany `Resume` tylko `Terminate` dla i operacji.</span><span class="sxs-lookup"><span data-stu-id="6777e-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="6777e-144">Aby wyczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="6777e-144">To cleanup (Optional)</span></span>

1. <span data-ttu-id="6777e-145">Otwórz konsolę Zarządzanie komputerem, uruchamiając plik `vs2010` Compmgmt.msc w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6777e-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="6777e-146">Rozwiń **węzeł Usługi i aplikacje**, **Kolejkowanie wiadomości,** **Kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="6777e-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="6777e-147">Usuń kolejkę **ReceiveTx.**</span><span class="sxs-lookup"><span data-stu-id="6777e-147">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="6777e-148">Aby usunąć bazę danych trwałości, uruchom cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="6777e-148">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6777e-149">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6777e-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6777e-150">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="6777e-150">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6777e-151">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="6777e-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6777e-152">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6777e-152">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
