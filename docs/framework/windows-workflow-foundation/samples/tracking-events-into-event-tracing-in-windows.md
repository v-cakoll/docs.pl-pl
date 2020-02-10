---
title: Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 2c397bcfa809a1306e9c31bf3f652b055d997f38
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094582"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="51a0d-102">Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="51a0d-102">Tracking Events into Event Tracing in Windows</span></span>

<span data-ttu-id="51a0d-103">W tym przykładzie pokazano, jak włączyć śledzenie Windows Workflow Foundation (WF) w usłudze przepływu pracy i emitować zdarzenia śledzenia w usłudze śledzenie zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="51a0d-103">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="51a0d-104">Aby emitować rekordy śledzenia przepływu pracy do funkcji ETW, przykład używa uczestnika śledzenia ETW (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span><span class="sxs-lookup"><span data-stu-id="51a0d-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>

<span data-ttu-id="51a0d-105">Przepływ pracy w przykładzie odbiera żądanie, przypisuje odwrotność danych wejściowych do zmiennej wejściowej i Zwraca odwrotność z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="51a0d-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="51a0d-106">Gdy dane wejściowe mają wartość 0, wystąpi wyjątek dzielenia przez zero, który jest nieobsługiwany, który powoduje przerwanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="51a0d-107">Po włączeniu śledzenia rekord śledzenia błędów jest emitowany do funkcji ETW, co może pomóc w późniejszym rozwiązaniu błędu.</span><span class="sxs-lookup"><span data-stu-id="51a0d-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="51a0d-108">Uczestnik śledzenia ETW jest skonfigurowany przy użyciu profilu śledzenia w celu subskrybowania śledzenia rekordów.</span><span class="sxs-lookup"><span data-stu-id="51a0d-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="51a0d-109">Profil śledzenia jest zdefiniowany w pliku Web. config i podany jako parametr konfiguracji uczestnika śledzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="51a0d-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="51a0d-110">Uczestnik śledzenia funkcji ETW jest skonfigurowany w pliku Web. config usługi przepływu pracy i jest stosowany do usługi jako zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="51a0d-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="51a0d-111">W tym przykładzie przeglądasz zdarzenia śledzenia w dzienniku zdarzeń przy użyciu Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51a0d-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>

## <a name="workflow-tracking-details"></a><span data-ttu-id="51a0d-112">Szczegóły śledzenia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="51a0d-112">Workflow Tracking Details</span></span>

<span data-ttu-id="51a0d-113">Windows Workflow Foundation udostępnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-113">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="51a0d-114">Środowisko uruchomieniowe śledzenia tworzy wystąpienie przepływu pracy do emisji zdarzeń związanych z cyklem życia przepływu pracy, zdarzeniami z działań przepływu pracy i zdarzeniami niestandardowymi.</span><span class="sxs-lookup"><span data-stu-id="51a0d-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="51a0d-115">W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.</span><span class="sxs-lookup"><span data-stu-id="51a0d-115">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="51a0d-116">Składnik</span><span class="sxs-lookup"><span data-stu-id="51a0d-116">Component</span></span>|<span data-ttu-id="51a0d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="51a0d-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="51a0d-118">Śledzenie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="51a0d-118">Tracking runtime</span></span>|<span data-ttu-id="51a0d-119">Udostępnia infrastrukturę do emisji rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="51a0d-119">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="51a0d-120">Śledzenie uczestników</span><span class="sxs-lookup"><span data-stu-id="51a0d-120">Tracking participants</span></span>|<span data-ttu-id="51a0d-121">Uzyskuje dostęp do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="51a0d-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] <span data-ttu-id="51a0d-122">dostarcza uczestnika śledzenia, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="51a0d-122">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="51a0d-123">Profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="51a0d-123">Tracking profile</span></span>|<span data-ttu-id="51a0d-124">Mechanizm filtrowania umożliwiający uczestnikom śledzenia subskrybowanie podzbioru rekordów śledzenia emitowanych z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

<span data-ttu-id="51a0d-125">W poniższej tabeli przedstawiono szczegółowe informacje o rekordach śledzenia, które są emitowane przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-125">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="51a0d-126">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="51a0d-126">Tracking record</span></span>|<span data-ttu-id="51a0d-127">Opis</span><span class="sxs-lookup"><span data-stu-id="51a0d-127">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="51a0d-128">Rekordy śledzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="51a0d-129">Opisuje cykl życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="51a0d-130">Na przykład rekord wystąpienia jest emitowany, gdy przepływ pracy zostanie uruchomiony lub zakończony.</span><span class="sxs-lookup"><span data-stu-id="51a0d-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="51a0d-131">Rekordy śledzenia stanu działania.</span><span class="sxs-lookup"><span data-stu-id="51a0d-131">Activity state tracking records.</span></span>|<span data-ttu-id="51a0d-132">Szczegóły wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="51a0d-132">Details activity execution.</span></span> <span data-ttu-id="51a0d-133">Te rekordy wskazują stan działania przepływu pracy, np. Kiedy działanie zostało zaplanowane lub gdy działanie zostało zakończone lub gdy zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="51a0d-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="51a0d-134">Rekord wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="51a0d-134">Bookmark resumption record.</span></span>|<span data-ttu-id="51a0d-135">Emitowane za każdym razem, gdy zostanie wznowiona Zakładka w wystąpieniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="51a0d-136">Niestandardowe rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="51a0d-136">Custom tracking records.</span></span>|<span data-ttu-id="51a0d-137">Autor przepływu pracy może tworzyć niestandardowe rekordy śledzenia i emitować je w ramach działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="51a0d-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="51a0d-138">Ten rekord jest emitowany, gdy działanie zaplanuje inne działanie.</span><span class="sxs-lookup"><span data-stu-id="51a0d-138">This record is emitted when an activity schedules another activity.</span></span>|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="51a0d-139">Ten rekord jest emitowany, gdy błąd jest propagowany z działania.</span><span class="sxs-lookup"><span data-stu-id="51a0d-139">This record is emitted when a fault is propagated from an activity.</span></span>|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="51a0d-140">Ten rekord jest emitowany, gdy działanie zostało anulowane przez inne działanie.</span><span class="sxs-lookup"><span data-stu-id="51a0d-140">This record is emitted when an activity is canceled by another activity.</span></span>|

<span data-ttu-id="51a0d-141">Uczestnik śledzenia subskrybuje podzestaw wyemitowanych rekordów śledzenia przy użyciu profilów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="51a0d-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="51a0d-142">Profil śledzenia zawiera kwerendy śledzenia, które umożliwiają subskrybowanie określonego typu rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="51a0d-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="51a0d-143">Profile śledzenia można określić w kodzie lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="51a0d-143">Tracking profiles can be specified in code or in configuration.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="51a0d-144">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="51a0d-144">To use this sample</span></span>

1. <span data-ttu-id="51a0d-145">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania EtwTrackingParticipantSample. sln.</span><span class="sxs-lookup"><span data-stu-id="51a0d-145">Using Visual Studio 2010, open the EtwTrackingParticipantSample.sln solution file.</span></span>

2. <span data-ttu-id="51a0d-146">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="51a0d-146">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="51a0d-147">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="51a0d-147">To run the solution, press F5.</span></span>

    <span data-ttu-id="51a0d-148">Domyślnie usługa nasłuchuje na porcie 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span><span class="sxs-lookup"><span data-stu-id="51a0d-148">By default, the service is listening on port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span></span>

4. <span data-ttu-id="51a0d-149">Korzystając z Eksploratora plików, Otwórz klienta testowego WCF.</span><span class="sxs-lookup"><span data-stu-id="51a0d-149">Using File Explorer, open the WCF test client.</span></span>

    <span data-ttu-id="51a0d-150">Klient testowy WCF (WcfTestClient. exe) znajduje się w folderze \<instalacyjnym programu Visual Studio 2010 > folderze \Common7\IDE\.</span><span class="sxs-lookup"><span data-stu-id="51a0d-150">The WCF test client (WcfTestClient.exe) is located in the \<Visual Studio 2010 installation folder>\Common7\IDE\ folder.</span></span>

    <span data-ttu-id="51a0d-151">Domyślny folder instalacji programu Visual Studio 2010 to C:\Program Files\Microsoft Visual Studio 10,0.</span><span class="sxs-lookup"><span data-stu-id="51a0d-151">The default Visual Studio 2010 installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>

5. <span data-ttu-id="51a0d-152">W kliencie testowym WCF wybierz pozycję **Dodaj usługę** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="51a0d-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>

    <span data-ttu-id="51a0d-153">Dodaj adres punktu końcowego w polu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="51a0d-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="51a0d-154">Wartość domyślna to `http://localhost:53797/SampleWorkflowService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="51a0d-154">The default is `http://localhost:53797/SampleWorkflowService.xamlx`.</span></span>

6. <span data-ttu-id="51a0d-155">Otwórz aplikację Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51a0d-155">Open the Event Viewer application.</span></span>

    <span data-ttu-id="51a0d-156">Przed wywołaniem usługi Uruchom Podgląd zdarzeń z menu **Start** , wybierz polecenie **Uruchom** i wpisz w `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="51a0d-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="51a0d-157">Upewnij się, że dziennik zdarzeń nasłuchuje zdarzeń śledzenia emitowanych z usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>

7. <span data-ttu-id="51a0d-158">W widoku drzewa Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**oraz **firmę Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="51a0d-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="51a0d-159">Kliknij prawym przyciskiem myszy pozycję **Microsoft** i wybierz pozycję **Widok** , a następnie **Pokaż dzienniki analityczne i debugowania** , aby włączyć dzienniki analityczne i debugowania.</span><span class="sxs-lookup"><span data-stu-id="51a0d-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>

    <span data-ttu-id="51a0d-160">Upewnij się, że jest zaznaczona opcja **Pokaż dzienniki analityczne i debugowania** .</span><span class="sxs-lookup"><span data-stu-id="51a0d-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

8. <span data-ttu-id="51a0d-161">W widoku drzewa w Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji-aplikacje**.</span><span class="sxs-lookup"><span data-stu-id="51a0d-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="51a0d-162">Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Włącz dziennik** , aby włączyć dziennik **analityczny** .</span><span class="sxs-lookup"><span data-stu-id="51a0d-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>

9. <span data-ttu-id="51a0d-163">Przetestuj usługę przy użyciu klienta testowego WCF przez dwukrotne kliknięcie `GetData`.</span><span class="sxs-lookup"><span data-stu-id="51a0d-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>

    <span data-ttu-id="51a0d-164">Spowoduje to otwarcie metody `GetData`.</span><span class="sxs-lookup"><span data-stu-id="51a0d-164">This opens the `GetData` method.</span></span> <span data-ttu-id="51a0d-165">Żądanie akceptuje jeden parametr i zapewnia, że wartość jest równa 0, co jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="51a0d-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>

     <span data-ttu-id="51a0d-166">Kliknij pozycję **Wywołaj**.</span><span class="sxs-lookup"><span data-stu-id="51a0d-166">Click **Invoke**.</span></span>

10. <span data-ttu-id="51a0d-167">Obserwuj zdarzenia emitowane z przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-167">Observe the events emitted from the workflow.</span></span>

    <span data-ttu-id="51a0d-168">Wróć do Podgląd zdarzeń i przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji-aplikacje**.</span><span class="sxs-lookup"><span data-stu-id="51a0d-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="51a0d-169">Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz polecenie **Odśwież**.</span><span class="sxs-lookup"><span data-stu-id="51a0d-169">Right-click **Analytic** and select **Refresh**.</span></span>

    <span data-ttu-id="51a0d-170">Zdarzenia przepływu pracy są wyświetlane w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51a0d-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="51a0d-171">Zwróć uwagę, że są wyświetlane zdarzenia wykonywania przepływu pracy, a jeden z nich jest nieobsługiwanym wyjątek, który odnosi się do błędu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="51a0d-172">Ponadto zdarzenie ostrzegawcze jest emitowane z działania przepływu pracy, co oznacza, że działanie zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="51a0d-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>

11. <span data-ttu-id="51a0d-173">Powtórz kroki 9 i 10 przy użyciu danych wejściowych innych niż 0, aby nie zgłaszać błędów.</span><span class="sxs-lookup"><span data-stu-id="51a0d-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>

<span data-ttu-id="51a0d-174">Profile śledzenia umożliwiają subskrybowanie zdarzeń, które są emitowane przez środowisko uruchomieniowe po zmianie stanu wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="51a0d-175">W zależności od wymagań dotyczących monitorowania można utworzyć profil, który jest bardzo duży, który subskrybuje niewielki zestaw zmian stanu wysokiego poziomu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="51a0d-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="51a0d-176">Z drugiej strony można utworzyć bardzo precyzyjny profil, którego dane wyjściowe są wystarczająco rozbudowane, aby odtworzyć wykonywanie później.</span><span class="sxs-lookup"><span data-stu-id="51a0d-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="51a0d-177">Przykład pokazuje zdarzenia emitowane przez środowisko uruchomieniowe przepływu pracy do funkcji ETW przy użyciu `HealthMonitoring Tracking Profile`, które emitują mały zestaw zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51a0d-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="51a0d-178">Inny profil, który emituje więcej zdarzeń śledzenia przepływu pracy, jest również dostępny w pliku Web. config o nazwie `Troubleshooting Tracking Profile`.</span><span class="sxs-lookup"><span data-stu-id="51a0d-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="51a0d-179">Po zainstalowaniu [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] w pliku Machine. config zostanie skonfigurowany profil domyślny o pustej nazwie.</span><span class="sxs-lookup"><span data-stu-id="51a0d-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="51a0d-180">Ten profil jest używany przez konfigurację zachowania śledzenia funkcji ETW, gdy nie określono nazwy profilu lub pustej nazwy profilu.</span><span class="sxs-lookup"><span data-stu-id="51a0d-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>

<span data-ttu-id="51a0d-181">Profil śledzenia monitorowania kondycji emituje rekordy wystąpień przepływu pracy i rekordy propagacji błędów aktywności.</span><span class="sxs-lookup"><span data-stu-id="51a0d-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="51a0d-182">Ten profil jest tworzony przez dodanie następującego profilu śledzenia do pliku konfiguracji Web. config.</span><span class="sxs-lookup"><span data-stu-id="51a0d-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="HealthMonitoring Tracking Profile">
      <workflow activityDefinitionId="*">
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Started"/>
              <state name="Completed"/>
              <state name="Aborted"/>
              <state name="UnhandledException"/>
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

 <span data-ttu-id="51a0d-183">Profil można zmienić, zmieniając konfigurację `EtwTrackingParticipant` w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="51a0d-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <etwTracking profileName="HealthMonitoring Tracking Profile"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

#### <a name="to-clean-up-optional"></a><span data-ttu-id="51a0d-184">Aby oczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="51a0d-184">To clean up (Optional)</span></span>

1. <span data-ttu-id="51a0d-185">Otwórz Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51a0d-185">Open Event Viewer.</span></span>

2. <span data-ttu-id="51a0d-186">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji — aplikacje**.</span><span class="sxs-lookup"><span data-stu-id="51a0d-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="51a0d-187">Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz polecenie **Wyłącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="51a0d-187">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="51a0d-188">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji — aplikacje**.</span><span class="sxs-lookup"><span data-stu-id="51a0d-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="51a0d-189">Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Wyczyść dziennik**.</span><span class="sxs-lookup"><span data-stu-id="51a0d-189">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="51a0d-190">Wybierz opcję **Wyczyść** , aby wyczyścić zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="51a0d-190">Choose the **Clear** option to clear the events.</span></span>

## <a name="known-issue"></a><span data-ttu-id="51a0d-191">Znany problem</span><span class="sxs-lookup"><span data-stu-id="51a0d-191">Known Issue</span></span>

> [!NOTE]
> <span data-ttu-id="51a0d-192">Istnieje znany problem w Podgląd zdarzeń, w którym może nie można zdekodować zdarzeń ETW.</span><span class="sxs-lookup"><span data-stu-id="51a0d-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="51a0d-193">Może pojawić się komunikat o błędzie, który wygląda podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="51a0d-193">You may see an error message that looks like the following.</span></span>
>
> <span data-ttu-id="51a0d-194">Nie można znaleźć opisu identyfikatora zdarzenia \<identyfikator > ze źródła Microsoft-Windows-Application Server-Applications.</span><span class="sxs-lookup"><span data-stu-id="51a0d-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="51a0d-195">Składnik, który wywołuje to zdarzenie, nie jest zainstalowany na komputerze lokalnym lub instalacja jest uszkodzona.</span><span class="sxs-lookup"><span data-stu-id="51a0d-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="51a0d-196">Można zainstalować lub naprawić składnik na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="51a0d-196">You can install or repair the component on the local computer.</span></span>
>
> <span data-ttu-id="51a0d-197">Jeśli ten błąd wystąpi, kliknij przycisk Odśwież w okienku Akcje.</span><span class="sxs-lookup"><span data-stu-id="51a0d-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="51a0d-198">Zdarzenie powinno teraz zostać zdekodowane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="51a0d-198">The event should now decode properly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51a0d-199">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="51a0d-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="51a0d-200">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="51a0d-200">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="51a0d-201">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51a0d-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51a0d-202">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="51a0d-202">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`

## <a name="see-also"></a><span data-ttu-id="51a0d-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51a0d-203">See also</span></span>

- <span data-ttu-id="51a0d-204">[Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="51a0d-204">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
