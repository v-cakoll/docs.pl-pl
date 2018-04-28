---
title: Śledzenie zdarzeń do zdarzenia śledzenia w systemie Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1a1038f848563c106ee1cac441b8a247e161e268
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="95e36-102">Śledzenie zdarzeń do zdarzenia śledzenia w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="95e36-102">Tracking Events into Event Tracing in Windows</span></span>
<span data-ttu-id="95e36-103">W tym przykładzie pokazano, jak włączyć śledzenie usługi przepływu pracy Windows Workflow Foundation (WF), a emisją zdarzeń śledzenia w funkcji Śledzenie zdarzeń systemu Windows ().</span><span class="sxs-lookup"><span data-stu-id="95e36-103">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="95e36-104">Aby emitować śledzenia rekordów do ETW przepływu pracy, próbki używa uczestnika śledzenia zdarzeń systemu Windows (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span><span class="sxs-lookup"><span data-stu-id="95e36-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>  
  
 <span data-ttu-id="95e36-105">Przepływ pracy w próbce odbiera żądanie, przypisuje odwrotność danych wejściowych do wprowadzania zmiennej i zwraca wzajemnego wstecz do klienta.</span><span class="sxs-lookup"><span data-stu-id="95e36-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="95e36-106">Gdy dane wejściowe to 0, dzielenie przez zero wyjątek występuje nieobsługiwany który powoduje, że przepływ pracy do przerwania.</span><span class="sxs-lookup"><span data-stu-id="95e36-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="95e36-107">Z włączonym śledzeniem, błąd Śledź rekord jest emitowany do funkcji ETW, co może pomóc rozwiązać problem później.</span><span class="sxs-lookup"><span data-stu-id="95e36-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="95e36-108">Uczestnik śledzenia zdarzeń systemu Windows jest skonfigurowany przy użyciu profilu śledzenia, aby subskrybować śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="95e36-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="95e36-109">Profil śledzenia jest zdefiniowana w pliku Web.config i podać jako parametr konfiguracji do uczestnika śledzenia zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95e36-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="95e36-110">Uczestnik śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config usługi przepływu pracy i zastosowano je do usługi jako zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="95e36-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="95e36-111">W tym przykładzie można wyświetlać zdarzenia śledzenia w dzienniku zdarzeń za pomocą Podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="95e36-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>  
  
## <a name="workflow-tracking-details"></a><span data-ttu-id="95e36-112">Szczegóły śledzenia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="95e36-112">Workflow Tracking Details</span></span>  
 <span data-ttu-id="95e36-113">Windows Workflow Foundation udostępnia infrastrukturę śledzenia śledzić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-113">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="95e36-114">Środowisko uruchomieniowe śledzenia tworzy wystąpienie przepływu pracy do wysyłania zdarzeń związanych z cyklem życia przepływu pracy, zdarzenia z działań przepływu pracy i zdarzeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="95e36-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="95e36-115">W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.</span><span class="sxs-lookup"><span data-stu-id="95e36-115">The following table details the primary components of the tracking infrastructure.</span></span>  
  
|<span data-ttu-id="95e36-116">Składnik</span><span class="sxs-lookup"><span data-stu-id="95e36-116">Component</span></span>|<span data-ttu-id="95e36-117">Opis</span><span class="sxs-lookup"><span data-stu-id="95e36-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95e36-118">Śledzenie czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="95e36-118">Tracking runtime</span></span>|<span data-ttu-id="95e36-119">Zapewnia infrastrukturę do emisji rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="95e36-119">Provides the infrastructure to emit tracking records.</span></span>|  
|<span data-ttu-id="95e36-120">Uczestników śledzenia</span><span class="sxs-lookup"><span data-stu-id="95e36-120">Tracking participants</span></span>|<span data-ttu-id="95e36-121">Uzyskuje dostęp do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="95e36-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="95e36-122"> jest dostarczany z uczestnika śledzenia, który zapisuje rekordy śledzenia jako zdarzenia funkcji Śledzenie zdarzeń systemu Windows ().</span><span class="sxs-lookup"><span data-stu-id="95e36-122"> ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|  
|<span data-ttu-id="95e36-123">Profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="95e36-123">Tracking profile</span></span>|<span data-ttu-id="95e36-124">Mechanizm filtrowania, który umożliwia śledzenie uczestnika do subskrybowania dla podzestawu rekordów śledzenia wyemitowanego z wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|  
  
 <span data-ttu-id="95e36-125">W poniższej tabeli przedstawiono rekordy śledzenia emitowane środowiska uruchomieniowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-125">The following table details the tracking records that the workflow runtime emits.</span></span>  
  
|<span data-ttu-id="95e36-126">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="95e36-126">Tracking record</span></span>|<span data-ttu-id="95e36-127">Opis</span><span class="sxs-lookup"><span data-stu-id="95e36-127">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="95e36-128">Rejestruje śledzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="95e36-129">Informacje o cyklu życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="95e36-130">Na przykład wystąpienia rekord jest emitowany podczas uruchamiania przepływu pracy, lub zakończy.</span><span class="sxs-lookup"><span data-stu-id="95e36-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|  
|<span data-ttu-id="95e36-131">Rejestruje śledzenia stanu działania.</span><span class="sxs-lookup"><span data-stu-id="95e36-131">Activity state tracking records.</span></span>|<span data-ttu-id="95e36-132">Szczegóły wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="95e36-132">Details activity execution.</span></span> <span data-ttu-id="95e36-133">Te rekordy wskazują stan działania przepływu pracy, takie jak kiedy zaplanowano działania lub po ukończeniu działania lub gdy zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="95e36-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|  
|<span data-ttu-id="95e36-134">Zakładki wznowienie rekordu.</span><span class="sxs-lookup"><span data-stu-id="95e36-134">Bookmark resumption record.</span></span>|<span data-ttu-id="95e36-135">Emitowane zawsze, gdy zostanie wznowione zakładki w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|  
|<span data-ttu-id="95e36-136">Śledzenie niestandardowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="95e36-136">Custom tracking records.</span></span>|<span data-ttu-id="95e36-137">Autor przepływu pracy można utworzyć rekordy śledzenia niestandardowych i wysyłać je w ramach działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="95e36-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="95e36-138">Ten rekord jest emitowany, gdy działanie planuje innego działania.</span><span class="sxs-lookup"><span data-stu-id="95e36-138">This record is emitted when an activity schedules another activity.</span></span>|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="95e36-139">Ten rekord jest emitowany przy propagacji błąd z działania.</span><span class="sxs-lookup"><span data-stu-id="95e36-139">This record is emitted when a fault is propagated from an activity.</span></span>|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="95e36-140">Ten rekord jest emitowany, gdy działanie zostało anulowane przez innego działania.</span><span class="sxs-lookup"><span data-stu-id="95e36-140">This record is emitted when an activity is canceled by another activity.</span></span>|  
  
 <span data-ttu-id="95e36-141">Subskrybuje uczestnika śledzenia dla podzestawu rekordów emitowany śledzenia przy użyciu profilów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="95e36-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="95e36-142">Profil śledzenia zawiera śledzenia zapytań, które umożliwia subskrybowania śledzenia określonego typu rekordu.</span><span class="sxs-lookup"><span data-stu-id="95e36-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="95e36-143">Śledzenie profile można określić w kodzie, lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="95e36-143">Tracking profiles can be specified in code or in configuration.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="95e36-144">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="95e36-144">To use this sample</span></span>  
  
1.  <span data-ttu-id="95e36-145">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania EtwTrackingParticipantSample.sln.</span><span class="sxs-lookup"><span data-stu-id="95e36-145">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EtwTrackingParticipantSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="95e36-146">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="95e36-146">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="95e36-147">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="95e36-147">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="95e36-148">Domyślnie usługa nasłuchuje na porcie 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span><span class="sxs-lookup"><span data-stu-id="95e36-148">By default, the service is listening on port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span></span>  
  
4.  <span data-ttu-id="95e36-149">Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otwórz klienta testowego WCF.</span><span class="sxs-lookup"><span data-stu-id="95e36-149">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="95e36-150">Klienta testowego WCF (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji > \Common7\IDE\ folderu.</span><span class="sxs-lookup"><span data-stu-id="95e36-150">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="95e36-151">Wartość domyślna [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji to C:\Program Files\Microsoft Visual Studio 10.0.</span><span class="sxs-lookup"><span data-stu-id="95e36-151">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
5.  <span data-ttu-id="95e36-152">W kliencie testowym WCF, wybierz **Dodaj usługę** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="95e36-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="95e36-153">Dodaj adres punktu końcowego w odpowiednim polu.</span><span class="sxs-lookup"><span data-stu-id="95e36-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="95e36-154">Wartość domyślna to http://localhost:53797/SampleWorkflowService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="95e36-154">The default is http://localhost:53797/SampleWorkflowService.xamlx.</span></span>  
  
6.  <span data-ttu-id="95e36-155">Otwórz aplikację Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="95e36-155">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="95e36-156">Przed wywołaniem usługi, uruchomienie podglądu zdarzeń z **Start** menu, wybierz opcję **Uruchom** i wpisz `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="95e36-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="95e36-157">Upewnij się, że dziennik zdarzeń nasłuchuje śledzenia zdarzeń wyemitowanego z usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="95e36-158">W widoku drzewa Podgląd zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, i **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="95e36-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="95e36-159">Kliknij prawym przyciskiem myszy **Microsoft** i wybierz **widoku** , a następnie **dzienniki Pokaż analityczne i debugowania** włączyć analityczne i debugowania dzienników</span><span class="sxs-lookup"><span data-stu-id="95e36-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>  
  
     <span data-ttu-id="95e36-160">Upewnij się, że **dzienniki Pokaż analityczne i debugowania** zaznaczenia pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="95e36-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
8.  <span data-ttu-id="95e36-161">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="95e36-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="95e36-162">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik** umożliwiające **analityczne** dziennika.</span><span class="sxs-lookup"><span data-stu-id="95e36-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>  
  
9. <span data-ttu-id="95e36-163">Testowanie usługi przy użyciu klienta testowego WCF, klikając dwukrotnie `GetData`.</span><span class="sxs-lookup"><span data-stu-id="95e36-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>  
  
     <span data-ttu-id="95e36-164">Spowoduje to otwarcie `GetData` metody.</span><span class="sxs-lookup"><span data-stu-id="95e36-164">This opens the `GetData` method.</span></span> <span data-ttu-id="95e36-165">Żądanie przyjmuje jeden parametr i zapewnia, że wartość wynosi 0, co jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="95e36-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>  
  
     <span data-ttu-id="95e36-166">Kliknij przycisk **wywołania**.</span><span class="sxs-lookup"><span data-stu-id="95e36-166">Click **Invoke**.</span></span>  
  
10. <span data-ttu-id="95e36-167">Sprawdź zdarzenia wysyłanego z przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-167">Observe the events emitted from the workflow.</span></span>  
  
     <span data-ttu-id="95e36-168">Wrócić do podglądu zdarzeń, a następnie przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="95e36-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="95e36-169">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.</span><span class="sxs-lookup"><span data-stu-id="95e36-169">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="95e36-170">Przepływ pracy zdarzenia są wyświetlane w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="95e36-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="95e36-171">Zwróć uwagę, że są wyświetlane zdarzenia wykonywania przepływu pracy i że jeden z nich jest nieobsługiwany wyjątek odpowiadający błąd w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="95e36-172">Ponadto zdarzenie ostrzeżenia jest emitowany z działania przepływu pracy, co oznacza, że działanie jest zgłaszanie błędów.</span><span class="sxs-lookup"><span data-stu-id="95e36-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>  
  
11. <span data-ttu-id="95e36-173">Powtórz kroki od 9 i Update 10 z wprowadzania danych innych niż 0, dzięki czemu jest zgłaszany błąd nie.</span><span class="sxs-lookup"><span data-stu-id="95e36-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>  
  
 <span data-ttu-id="95e36-174">Profile śledzenia umożliwiają subskrybowanie zdarzeń, które są emitowane przez środowisko uruchomieniowe po zmianie stanu wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="95e36-175">W zależności od wymagań monitorowania, można utworzyć profil, który jest przybliżonego, które subskrybuje niewielki zestaw zmian stanu ogólny przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="95e36-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="95e36-176">Z drugiej strony można utworzyć profil bardzo dokładne, której wyjście jest zaawansowanych, aby odtworzyć wykonywania później.</span><span class="sxs-lookup"><span data-stu-id="95e36-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="95e36-177">W przykładzie pokazano zdarzenia wyemitowanego z środowiska uruchomieniowego przepływu pracy przy użyciu funkcji ETW `HealthMonitoring Tracking Profile`, który emituje niewielki zestaw zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="95e36-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="95e36-178">Dostępne są również innego profilu, który emituje jeden przepływ pracy zdarzenia śledzenia w pliku Web.config, o nazwie `Troubleshooting Tracking Profile`.</span><span class="sxs-lookup"><span data-stu-id="95e36-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="95e36-179">Gdy [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] jest zainstalowany, domyślny profil o pustej nazwie jest skonfigurowany w pliku Machine.config.</span><span class="sxs-lookup"><span data-stu-id="95e36-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="95e36-180">Ten profil jest używany przez ETW śledzenia konfigurację zachowania, gdy brak nazwy profilu lub profilu pusta nazwa jest określona.</span><span class="sxs-lookup"><span data-stu-id="95e36-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>  
  
 <span data-ttu-id="95e36-181">Monitorowania profilu śledzenia kondycji emituje rekordów wystąpienia przepływu pracy i działania błędów Propagacja rekordów.</span><span class="sxs-lookup"><span data-stu-id="95e36-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="95e36-182">Ten profil jest tworzony przez dodanie następującego profilu śledzenia w pliku konfiguracji Web.config.</span><span class="sxs-lookup"><span data-stu-id="95e36-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>  
  
```xml  
<<tracking>  
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
  
 <span data-ttu-id="95e36-183">Profil można zmienić, zmieniając `EtwTrackingParticipant` konfiguracji do następującego.</span><span class="sxs-lookup"><span data-stu-id="95e36-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="95e36-184">Aby wyczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="95e36-184">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="95e36-185">Otwórz Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="95e36-185">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="95e36-186">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="95e36-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="95e36-187">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączyć dziennika**.</span><span class="sxs-lookup"><span data-stu-id="95e36-187">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="95e36-188">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="95e36-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="95e36-189">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.</span><span class="sxs-lookup"><span data-stu-id="95e36-189">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="95e36-190">Wybierz **wyczyść** opcję, aby wyczyścić zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="95e36-190">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="95e36-191">Znany problem</span><span class="sxs-lookup"><span data-stu-id="95e36-191">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95e36-192">Istnieje znany problem w Podglądzie zdarzeń, jeżeli nie może zdekodować zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="95e36-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="95e36-193">Może zostać wyświetlony komunikat błędu, który wygląda następująco.</span><span class="sxs-lookup"><span data-stu-id="95e36-193">You may see an error message that looks like the following.</span></span>  
>   
>  <span data-ttu-id="95e36-194">Opisu Identyfikatora zdarzenia \<id > ze źródła nie można odnaleźć aplikacji serwera firmy Microsoft-Windows-aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95e36-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="95e36-195">Składnik, który wywołuje to zdarzenie nie jest zainstalowany na komputerze lokalnym albo instalacja jest uszkodzona.</span><span class="sxs-lookup"><span data-stu-id="95e36-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="95e36-196">Można zainstalować lub naprawić składnik na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="95e36-196">You can install or repair the component on the local computer.</span></span>  
>   
>  <span data-ttu-id="95e36-197">Jeśli wystąpi ten błąd, kliknij przycisk Odśwież w okienku Akcje.</span><span class="sxs-lookup"><span data-stu-id="95e36-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="95e36-198">Zdarzenia powinny teraz dekodowania poprawnie.</span><span class="sxs-lookup"><span data-stu-id="95e36-198">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="95e36-199">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="95e36-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="95e36-200">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="95e36-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="95e36-201">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="95e36-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95e36-202">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="95e36-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a><span data-ttu-id="95e36-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95e36-203">See Also</span></span>  
 [<span data-ttu-id="95e36-204">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="95e36-204">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
