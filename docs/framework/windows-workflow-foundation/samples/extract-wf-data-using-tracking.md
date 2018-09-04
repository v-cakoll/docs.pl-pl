---
title: Wyodrębnianie danych WF przy użyciu śledzenia
ms.date: 03/30/2017
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
ms.openlocfilehash: ef8118df2c5834e32c40760ef31f75660893d89b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501586"
---
# <a name="extract-wf-data-using-tracking"></a><span data-ttu-id="091e6-102">Wyodrębnianie danych WF przy użyciu śledzenia</span><span class="sxs-lookup"><span data-stu-id="091e6-102">Extract WF Data using Tracking</span></span>
<span data-ttu-id="091e6-103">Ten przykład pokazuje sposób użycia śledzenia można wyodrębnić zmienne przepływu pracy i argumenty z działań przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="091e6-103">This sample demonstrates how to use workflow tracking to extract workflow variables and arguments from activities.</span></span> <span data-ttu-id="091e6-104">Pokazuje także dodawanie adnotacji do śledzenia rekordów i wyodrębnianie ładunku danych w ramach śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="091e6-104">It also shows the addition of annotations to tracking records and the extraction of data payload within custom tracking records.</span></span> <span data-ttu-id="091e6-105">W przykładzie użyto uczestnika śledzenia Śledzenie zdarzeń dla Windows (ETW), aby wyodrębnić dane z przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="091e6-105">The sample uses the Event Tracing for Windows (ETW) tracking participant to extract data from the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="091e6-106">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="091e6-106">Sample Details</span></span>  
 <span data-ttu-id="091e6-107">Windows Workflow Foundation (WF) umożliwia śledzenie, aby uzyskać wgląd w wykonywania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="091e6-107">Windows Workflow Foundation (WF) provides tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="091e6-108">Środowisko uruchomieniowe śledzenia emituje przepływu pracy śledzenia rekordów podczas wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="091e6-108">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="091e6-109">Wraz z rekordów śledzenia przepływu pracy dane w ramach wystąpienie przepływu pracy można wyodrębnić z przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="091e6-109">Along with the workflow tracking records, data within the workflow instance can be extracted from the workflow.</span></span> <span data-ttu-id="091e6-110">Poniżej przedstawiono szczegółową listę typów danych, które można wyodrębnić z rekordy śledzenia:</span><span class="sxs-lookup"><span data-stu-id="091e6-110">The following list details the types of data that can be extracted from tracking records:</span></span>  
  
1.  <span data-ttu-id="091e6-111">Zmienne przepływu pracy w ramach działania i rekordy śledzenia podczas wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="091e6-111">Workflow variables within an activity and tracking records during activity execution.</span></span>  
  
     <span data-ttu-id="091e6-112">Aby wyodrębnić zmienne przepływu pracy, zmienne, które ma zostać wyodrębniony są określone w profilu.</span><span class="sxs-lookup"><span data-stu-id="091e6-112">To extract workflow variables, the variables to be extracted are specified in a profile.</span></span> <span data-ttu-id="091e6-113">Zmienne, które ma zostać wyodrębniony można określić tylko z `ActivityStateQueries`.</span><span class="sxs-lookup"><span data-stu-id="091e6-113">Variables to be extracted can only be specified with `ActivityStateQueries`.</span></span> <span data-ttu-id="091e6-114">Poniższy przykład kodu pokazuje profil śledzenia służą do wyodrębniania zmiennej przepływu pracy na podstawie działania.</span><span class="sxs-lookup"><span data-stu-id="091e6-114">The following code example demonstrates a tracking profile used to extract the workflow variable from an activity.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  <span data-ttu-id="091e6-115">Argumenty aktywności i stanu działania śledzenia rekordów.</span><span class="sxs-lookup"><span data-stu-id="091e6-115">Activity arguments and activity state tracking records.</span></span>  
  
     <span data-ttu-id="091e6-116">Argumenty do definiowania danych sposób przepływów w lub poza nią działania.</span><span class="sxs-lookup"><span data-stu-id="091e6-116">Arguments define the way data flows in or out of an activity.</span></span> <span data-ttu-id="091e6-117">Argumenty, które można wyodrębnić są określane za pomocą <xref:System.Activities.Tracking.ActivityStateQuery>. Poniższy przykład kodu jest profilu śledzenia, która wyodrębnia `Value` argumentu.</span><span class="sxs-lookup"><span data-stu-id="091e6-117">Arguments to be extracted are specified using an <xref:System.Activities.Tracking.ActivityStateQuery>.The following code example is a tracking profile that extracts the `Value` argument.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  <span data-ttu-id="091e6-118">Adnotacje są pary klucz/wartość, które można dodać do dowolnego rekordu śledzenia, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="091e6-118">Annotations are key/value pairs that can be added to any tracking record that is emitted.</span></span>  
  
     <span data-ttu-id="091e6-119">Adnotacje służyć jako znakowania mechanizm śledzenia rekordów.</span><span class="sxs-lookup"><span data-stu-id="091e6-119">Annotations serve as a tagging mechanism for tracking records.</span></span> <span data-ttu-id="091e6-120">Adnotacje są dodawane do śledzenia rekordów za pomocą profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="091e6-120">Annotations are added to tracking records through a tracking profile.</span></span> <span data-ttu-id="091e6-121">Adnotacje można dodać do dowolnego typu zapytania śledzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="091e6-121">Annotations can be added to any type of a workflow tracking query.</span></span> <span data-ttu-id="091e6-122">Poniższy przykład kodu jest profilu śledzenia, który pokazuje, jak można dodać adnotacji z rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="091e6-122">The following code example is a tracking profile that shows how an annotation can be added to a tracking record.</span></span>  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  <span data-ttu-id="091e6-123">Niestandardowe rekordy śledzenia są emitowane z działań użytkownika.</span><span class="sxs-lookup"><span data-stu-id="091e6-123">Custom tracking records are emitted from user-defined activities.</span></span>  
  
     <span data-ttu-id="091e6-124">Niestandardowe rekordy śledzenia może przenosić dane ładunku zdefiniowany w ramach tego działania.</span><span class="sxs-lookup"><span data-stu-id="091e6-124">Custom tracking records can carry payload data defined within this activity.</span></span> <span data-ttu-id="091e6-125">Subskrybowania śledzenia niestandardowe rekordów w profilu śledzenia umożliwia wyodrębnianie ładunku w rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="091e6-125">Subscribing for custom tracking records in a tracking profile allows the extraction of the payload within the tracking record.</span></span> <span data-ttu-id="091e6-126">Można wyodrębnić śledzenia niestandardowe rekordów za pomocą niestandardowego <xref:System.Activities.Tracking.TrackingQuery>.</span><span class="sxs-lookup"><span data-stu-id="091e6-126">The custom tracking records can be extracted with custom a <xref:System.Activities.Tracking.TrackingQuery>.</span></span> <span data-ttu-id="091e6-127">Poniższy przykład kodu jest profilu śledzenia, która wyodrębnia rekord śledzenia niestandardowego, wraz z jego ładunku.</span><span class="sxs-lookup"><span data-stu-id="091e6-127">The following code example is a tracking profile that extracts a custom tracking record along with its payload.</span></span>  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 <span data-ttu-id="091e6-128">W przykładzie pokazano wyodrębniania zmienne, argumenty, niestandardowych rekordów i dodawanie adnotacji, przy użyciu profilu określony w pliku Web.config. Śledzenia jest włączona na przykład usługi przepływu pracy, dodając `<etwTracking>` element zachowania.</span><span class="sxs-lookup"><span data-stu-id="091e6-128">The sample demonstrates the extraction of a variables, arguments, custom records and adding annotations using a profile specified in a Web.config. Tracking is enabled on the sample workflow service by adding an `<etwTracking>` behavior element.</span></span> <span data-ttu-id="091e6-129">Poniższy kod przykładowy umożliwia śledzenie `ExtractWorkflowVariables` profil śledzenia.</span><span class="sxs-lookup"><span data-stu-id="091e6-129">The following code example enables tracking for the `ExtractWorkflowVariables` tracking profile.</span></span>  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="091e6-130">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="091e6-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="091e6-131">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="091e6-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="091e6-132">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="091e6-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="091e6-133">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="091e6-133">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="091e6-134">Okno przeglądarki otwiera i pokazuje katalog zawierający informacje o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="091e6-134">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="091e6-135">W przeglądarce kliknij przycisk StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="091e6-135">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="091e6-136">W przeglądarce pojawi się stronie StockPriceService zawiera usługę lokalnego adresu WSDL.</span><span class="sxs-lookup"><span data-stu-id="091e6-136">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="091e6-137">Skopiuj ten adres.</span><span class="sxs-lookup"><span data-stu-id="091e6-137">Copy this address.</span></span>  
  
     <span data-ttu-id="091e6-138">Poniższy przykład pokazuje adresu lokalnej usługi WSDL.</span><span class="sxs-lookup"><span data-stu-id="091e6-138">The following example shows a local service WSDL address.</span></span> `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  <span data-ttu-id="091e6-139">Przed wywołaniem usługi, Uruchom Podgląd zdarzeń i upewnij się, czy w dzienniku zdarzeń nasłuchuje dla śledzenia zdarzeń wysyłanego z usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="091e6-139">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="091e6-140">Z **Start** menu, wybierz opcję **narzędzia administracyjne** i następnie **Podgląd zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="091e6-140">From the **Start** menu, select **Administrative Tools** and then **Event Viewer**.</span></span>  
  
8.  <span data-ttu-id="091e6-141">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, i **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="091e6-141">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="091e6-142">Kliknij prawym przyciskiem myszy **Microsoft** i wybierz **widoku** i następnie **Pokaż analityczne i debugowania dzienniki**.</span><span class="sxs-lookup"><span data-stu-id="091e6-142">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="091e6-143">Upewnij się, że **Pokaż analityczne i debugowania dzienniki** opcja jest zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="091e6-143">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="091e6-144">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="091e6-144">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="091e6-145">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="091e6-145">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="091e6-146">Za pomocą [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otwórz klienta testowego WCF.</span><span class="sxs-lookup"><span data-stu-id="091e6-146">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="091e6-147">Testowy klient WCF (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji > \Common7\IDE\ folderu.</span><span class="sxs-lookup"><span data-stu-id="091e6-147">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="091e6-148">Wartość domyślna [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji to C:\Program Files\Microsoft Visual Studio 10.0.</span><span class="sxs-lookup"><span data-stu-id="091e6-148">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
11. <span data-ttu-id="091e6-149">W kliencie testowym WCF, wybierz **Dodaj usługę** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="091e6-149">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="091e6-150">Dodaj usługę lokalnego adresu WSDL, który został wcześniej skopiowany w polu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="091e6-150">Add the local service WSDL address you copied earlier in the input box.</span></span>  
  
12. <span data-ttu-id="091e6-151">W kliencie testowym WCF, kliknij dwukrotnie `GetStockPrice`.</span><span class="sxs-lookup"><span data-stu-id="091e6-151">In WCF test client, double-click `GetStockPrice`.</span></span>  
  
     <span data-ttu-id="091e6-152">Spowoduje to otwarcie `GetStockPrice` metody.</span><span class="sxs-lookup"><span data-stu-id="091e6-152">This opens the `GetStockPrice` method.</span></span> <span data-ttu-id="091e6-153">Żądanie przyjmuje jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="091e6-153">The request accepts one parameter.</span></span> <span data-ttu-id="091e6-154">Użyj wartości **Contoso**.</span><span class="sxs-lookup"><span data-stu-id="091e6-154">Use the value **Contoso**.</span></span>  
  
13. <span data-ttu-id="091e6-155">Kliknij przycisk **wywołania**.</span><span class="sxs-lookup"><span data-stu-id="091e6-155">Click **Invoke**.</span></span>  
  
14. <span data-ttu-id="091e6-156">Przejdź z powrotem do programu Podgląd zdarzeń i przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="091e6-156">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="091e6-157">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.</span><span class="sxs-lookup"><span data-stu-id="091e6-157">Right-click **Analytic** and select **Refresh**.</span></span> <span data-ttu-id="091e6-158">Zdarzenia przepływu pracy w zdarzeniu są zakresy identyfikatorów 100 199.</span><span class="sxs-lookup"><span data-stu-id="091e6-158">The workflow events are in the event ID ranges 100-199.</span></span>  
  
     <span data-ttu-id="091e6-159">Zdarzenia zawierać adnotacji, zmienne, argumenty i śledzenia niestandardowe rekordów, które mogą być wyświetlane w zdarzeniu podglądu.</span><span class="sxs-lookup"><span data-stu-id="091e6-159">The events contain the annotations, variables, arguments and custom tracking records that can be viewed in the event viewer.</span></span>  
  
## <a name="cleaning-up-in-the-event-viewer"></a><span data-ttu-id="091e6-160">Czyszczenie w zdarzeniu podglądu</span><span class="sxs-lookup"><span data-stu-id="091e6-160">Cleaning up in the Event Viewer</span></span>  
 <span data-ttu-id="091e6-161">Kanał analityczne w dzienniku zdarzeń mogą zostać wyczyszczone w zdarzeniu podglądu, wykonując następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="091e6-161">The analytic channel in the event log can be cleaned up in the Event Viewer by doing the following.</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="091e6-162">Aby wyczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="091e6-162">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="091e6-163">Otwórz Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="091e6-163">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="091e6-164">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="091e6-164">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="091e6-165">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączanie dziennika**.</span><span class="sxs-lookup"><span data-stu-id="091e6-165">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="091e6-166">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="091e6-166">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="091e6-167">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.</span><span class="sxs-lookup"><span data-stu-id="091e6-167">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
     <span data-ttu-id="091e6-168">Wybierz **wyczyść** możliwość wyczyszczenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="091e6-168">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="091e6-169">Znany problem</span><span class="sxs-lookup"><span data-stu-id="091e6-169">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="091e6-170">Istnieje znany problem w Podglądzie zdarzeń, gdzie może nie zdekodować zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="091e6-170">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="091e6-171">Zobaczysz komunikat o błędzie, który wygląda podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="091e6-171">You may see an error message that looks like the following.</span></span>  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  <span data-ttu-id="091e6-172">Jeśli wystąpi ten błąd, kliknij przycisk **Odśwież** w okienku Akcje.</span><span class="sxs-lookup"><span data-stu-id="091e6-172">If you encounter this error, click **Refresh** in the actions pane.</span></span> <span data-ttu-id="091e6-173">Zdarzenia powinny teraz poprawnie dekodowane.</span><span class="sxs-lookup"><span data-stu-id="091e6-173">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="091e6-174">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="091e6-174">The samples may already be installed on your computer.</span></span> <span data-ttu-id="091e6-175">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="091e6-175">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="091e6-176">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="091e6-176">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="091e6-177">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="091e6-177">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a><span data-ttu-id="091e6-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="091e6-178">See Also</span></span>  
 [<span data-ttu-id="091e6-179">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="091e6-179">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
