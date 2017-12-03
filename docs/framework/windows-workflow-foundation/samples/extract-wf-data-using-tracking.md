---
title: "Wyodrębnianie danych WF przy użyciu śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 988dbef057b5980ac3f23b88c39669706d44557e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="extract-wf-data-using-tracking"></a><span data-ttu-id="b1565-102">Wyodrębnianie danych WF przy użyciu śledzenia</span><span class="sxs-lookup"><span data-stu-id="b1565-102">Extract WF Data using Tracking</span></span>
<span data-ttu-id="b1565-103">W tym przykładzie przedstawiono sposób użycia śledzenia można wyodrębnić zmienne przepływu pracy i argumenty z działań przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b1565-103">This sample demonstrates how to use workflow tracking to extract workflow variables and arguments from activities.</span></span> <span data-ttu-id="b1565-104">Przedstawia on także dodawanie adnotacji do śledzenia rekordów i wyodrębniania danych ładunku w rekordach śledzenia niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="b1565-104">It also shows the addition of annotations to tracking records and the extraction of data payload within custom tracking records.</span></span> <span data-ttu-id="b1565-105">W przykładzie użyto uczestnika śledzenia zdarzeń śledzenia dla systemu Windows (ETW) do wyodrębniania danych z przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b1565-105">The sample uses the Event Tracing for Windows (ETW) tracking participant to extract data from the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="b1565-106">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="b1565-106">Sample Details</span></span>  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="b1565-107">Umożliwia śledzenie wgląd we wykonywania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b1565-107"> provides tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="b1565-108">Środowisko uruchomieniowe śledzenia emituje przepływu pracy śledzenia rekordów podczas wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b1565-108">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="b1565-109">Wraz z przepływu pracy śledzenia rekordy można wyodrębnić danych w wystąpieniu przepływu pracy z przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b1565-109">Along with the workflow tracking records, data within the workflow instance can be extracted from the workflow.</span></span> <span data-ttu-id="b1565-110">Poniżej przedstawiono szczegóły typów danych, który może zostać wyodrębniony z śledzenie rekordów:</span><span class="sxs-lookup"><span data-stu-id="b1565-110">The following list details the types of data that can be extracted from tracking records:</span></span>  
  
1.  <span data-ttu-id="b1565-111">Zmienne przepływu pracy w ramach działania i śledzenie rekordów podczas wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="b1565-111">Workflow variables within an activity and tracking records during activity execution.</span></span>  
  
     <span data-ttu-id="b1565-112">Aby wyodrębnić zmienne przepływu pracy, zmienne, które mają zostać wyodrębnione są określone w profilu.</span><span class="sxs-lookup"><span data-stu-id="b1565-112">To extract workflow variables, the variables to be extracted are specified in a profile.</span></span> <span data-ttu-id="b1565-113">Zmienne, które mają zostać wyodrębnione można określić tylko w przypadku `ActivityStateQueries`.</span><span class="sxs-lookup"><span data-stu-id="b1565-113">Variables to be extracted can only be specified with `ActivityStateQueries`.</span></span> <span data-ttu-id="b1565-114">Poniższy przykład kodu pokazuje profil śledzenia używany do wyodrębnienia zmiennej przepływu pracy z działania.</span><span class="sxs-lookup"><span data-stu-id="b1565-114">The following code example demonstrates a tracking profile used to extract the workflow variable from an activity.</span></span>  
  
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
  
2.  <span data-ttu-id="b1565-115">Argumentów działania i stan działania śledzenia rekordów.</span><span class="sxs-lookup"><span data-stu-id="b1565-115">Activity arguments and activity state tracking records.</span></span>  
  
     <span data-ttu-id="b1565-116">Argumenty zdefiniować dane sposób przepływów do lub z działania.</span><span class="sxs-lookup"><span data-stu-id="b1565-116">Arguments define the way data flows in or out of an activity.</span></span> <span data-ttu-id="b1565-117">Argumenty do wyodrębnienia są określane za pomocą <xref:System.Activities.Tracking.ActivityStateQuery>. Poniższy przykładowy kod jest profilu śledzenia, która wyodrębnia `Value` argumentu.</span><span class="sxs-lookup"><span data-stu-id="b1565-117">Arguments to be extracted are specified using an <xref:System.Activities.Tracking.ActivityStateQuery>.The following code example is a tracking profile that extracts the `Value` argument.</span></span>  
  
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
  
3.  <span data-ttu-id="b1565-118">Adnotacje są pary klucz wartość, które mogą zostać dodane do dowolnego rekordu śledzenia emitowanego.</span><span class="sxs-lookup"><span data-stu-id="b1565-118">Annotations are key/value pairs that can be added to any tracking record that is emitted.</span></span>  
  
     <span data-ttu-id="b1565-119">Adnotacje służyć jako mechanizmu tagowania śledzenia rekordów.</span><span class="sxs-lookup"><span data-stu-id="b1565-119">Annotations serve as a tagging mechanism for tracking records.</span></span> <span data-ttu-id="b1565-120">Adnotacje są dodawane do śledzenia rekordów za pomocą profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b1565-120">Annotations are added to tracking records through a tracking profile.</span></span> <span data-ttu-id="b1565-121">Można dodać adnotacje do dowolnego typu zapytania śledzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b1565-121">Annotations can be added to any type of a workflow tracking query.</span></span> <span data-ttu-id="b1565-122">Poniższy przykładowy kod jest profil śledzenia, który pokazuje, jak można dodać adnotacji do rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b1565-122">The following code example is a tracking profile that shows how an annotation can be added to a tracking record.</span></span>  
  
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
  
4.  <span data-ttu-id="b1565-123">Śledzenie niestandardowych rekordów są emitowane z działań użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b1565-123">Custom tracking records are emitted from user-defined activities.</span></span>  
  
     <span data-ttu-id="b1565-124">Niestandardowe śledzenie rekordów może przenosić dane ładunku zdefiniowane w obrębie tego działania.</span><span class="sxs-lookup"><span data-stu-id="b1565-124">Custom tracking records can carry payload data defined within this activity.</span></span> <span data-ttu-id="b1565-125">Subskrypcja dla śledzenia niestandardowych rekordów w profilu śledzenia umożliwia wyodrębnianie ładunku w rekordzie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b1565-125">Subscribing for custom tracking records in a tracking profile allows the extraction of the payload within the tracking record.</span></span> <span data-ttu-id="b1565-126">Rejestruje śledzenia niestandardowych można wyodrębnić z niestandardowego <xref:System.Activities.Tracking.TrackingQuery>.</span><span class="sxs-lookup"><span data-stu-id="b1565-126">The custom tracking records can be extracted with custom a <xref:System.Activities.Tracking.TrackingQuery>.</span></span> <span data-ttu-id="b1565-127">Poniższy przykładowy kod jest profilu śledzenia, która wyodrębnia rekord śledzenia niestandardowych wraz z jego ładunku.</span><span class="sxs-lookup"><span data-stu-id="b1565-127">The following code example is a tracking profile that extracts a custom tracking record along with its payload.</span></span>  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 <span data-ttu-id="b1565-128">W przykładzie pokazano wyodrębniania zmiennych, argumenty, niestandardowych rekordów i dodawanie adnotacji przy użyciu profilu określony w pliku Web.config. Włączono śledzenie na przykład usługi przepływu pracy, dodając `<etwTracking>` element zachowania.</span><span class="sxs-lookup"><span data-stu-id="b1565-128">The sample demonstrates the extraction of a variables, arguments, custom records and adding annotations using a profile specified in a Web.config. Tracking is enabled on the sample workflow service by adding an `<etwTracking>` behavior element.</span></span> <span data-ttu-id="b1565-129">Poniższy kod umożliwia przykład śledzenie `ExtractWorkflowVariables` profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b1565-129">The following code example enables tracking for the `ExtractWorkflowVariables` tracking profile.</span></span>  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b1565-130">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="b1565-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="b1565-131">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="b1565-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b1565-132">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b1565-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b1565-133">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="b1565-133">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="b1565-134">Oknie przeglądarki zostanie otwarty i zawiera katalog zawierający informacje o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1565-134">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="b1565-135">W przeglądarce kliknij przycisk StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="b1565-135">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="b1565-136">W przeglądarce pojawi się stronie StockPriceService zawiera Usługa lokalna adres WSDL.</span><span class="sxs-lookup"><span data-stu-id="b1565-136">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="b1565-137">Skopiuj ten adres.</span><span class="sxs-lookup"><span data-stu-id="b1565-137">Copy this address.</span></span>  
  
     <span data-ttu-id="b1565-138">W poniższym przykładzie przedstawiono adres WSDL Usługa lokalna.</span><span class="sxs-lookup"><span data-stu-id="b1565-138">The following example shows a local service WSDL address.</span></span> `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  <span data-ttu-id="b1565-139">Przed wywołaniem usługi, należy uruchomić Podgląd zdarzeń i upewnij się, że dziennik zdarzeń nasłuchuje śledzenia zdarzeń wyemitowanego z usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b1565-139">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="b1565-140">Z **Start** menu, wybierz opcję **narzędzia administracyjne** , a następnie **Podgląd zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="b1565-140">From the **Start** menu, select **Administrative Tools** and then **Event Viewer**.</span></span>  
  
8.  <span data-ttu-id="b1565-141">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, i **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="b1565-141">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="b1565-142">Kliknij prawym przyciskiem myszy **Microsoft** i wybierz **widoku** , a następnie **dzienniki Pokaż analityczne i debugowania**.</span><span class="sxs-lookup"><span data-stu-id="b1565-142">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="b1565-143">Upewnij się, że **dzienniki Pokaż analityczne i debugowania** zaznaczenia pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="b1565-143">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="b1565-144">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="b1565-144">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b1565-145">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="b1565-145">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="b1565-146">Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otwórz klienta testowego WCF.</span><span class="sxs-lookup"><span data-stu-id="b1565-146">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="b1565-147">Klienta testowego WCF (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji > \Common7\IDE\ folderu.</span><span class="sxs-lookup"><span data-stu-id="b1565-147">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="b1565-148">Wartość domyślna [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji to C:\Program Files\Microsoft Visual Studio 10.0.</span><span class="sxs-lookup"><span data-stu-id="b1565-148">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
11. <span data-ttu-id="b1565-149">W kliencie testowym WCF, wybierz **Dodaj usługę** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="b1565-149">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="b1565-150">Dodaj usługę lokalny adres WSDL, które wcześniej zostały skopiowane w odpowiednim polu.</span><span class="sxs-lookup"><span data-stu-id="b1565-150">Add the local service WSDL address you copied earlier in the input box.</span></span>  
  
12. <span data-ttu-id="b1565-151">W kliencie testowym WCF, kliknij dwukrotnie `GetStockPrice`.</span><span class="sxs-lookup"><span data-stu-id="b1565-151">In WCF test client, double-click `GetStockPrice`.</span></span>  
  
     <span data-ttu-id="b1565-152">Spowoduje to otwarcie `GetStockPrice` metody.</span><span class="sxs-lookup"><span data-stu-id="b1565-152">This opens the `GetStockPrice` method.</span></span> <span data-ttu-id="b1565-153">Żądanie przyjmuje jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="b1565-153">The request accepts one parameter.</span></span> <span data-ttu-id="b1565-154">Użyj wartości **Contoso**.</span><span class="sxs-lookup"><span data-stu-id="b1565-154">Use the value **Contoso**.</span></span>  
  
13. <span data-ttu-id="b1565-155">Kliknij przycisk **wywołania**.</span><span class="sxs-lookup"><span data-stu-id="b1565-155">Click **Invoke**.</span></span>  
  
14. <span data-ttu-id="b1565-156">Wrócić do podglądu zdarzeń, a następnie przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="b1565-156">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b1565-157">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.</span><span class="sxs-lookup"><span data-stu-id="b1565-157">Right-click **Analytic** and select **Refresh**.</span></span> <span data-ttu-id="b1565-158">Identyfikator zakresu 100 – 199 zdarzeń są zdarzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b1565-158">The workflow events are in the event ID ranges 100-199.</span></span>  
  
     <span data-ttu-id="b1565-159">Zdarzenia zawierają adnotacje, zmienne, argumentów i śledzenia niestandardowych rekordów, które mogą być wyświetlane w zdarzeniu podglądu.</span><span class="sxs-lookup"><span data-stu-id="b1565-159">The events contain the annotations, variables, arguments and custom tracking records that can be viewed in the event viewer.</span></span>  
  
## <a name="cleaning-up-in-the-event-viewer"></a><span data-ttu-id="b1565-160">Czyszczenie zdarzeń podglądu</span><span class="sxs-lookup"><span data-stu-id="b1565-160">Cleaning up in the Event Viewer</span></span>  
 <span data-ttu-id="b1565-161">Kanał danych analitycznych w dzienniku zdarzeń mogą zostać wyczyszczone zdarzeń podglądu w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b1565-161">The analytic channel in the event log can be cleaned up in the Event Viewer by doing the following.</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="b1565-162">Aby wyczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b1565-162">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="b1565-163">Otwórz Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b1565-163">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="b1565-164">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="b1565-164">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b1565-165">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączyć dziennika**.</span><span class="sxs-lookup"><span data-stu-id="b1565-165">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="b1565-166">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="b1565-166">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b1565-167">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.</span><span class="sxs-lookup"><span data-stu-id="b1565-167">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
     <span data-ttu-id="b1565-168">Wybierz **wyczyść** opcję, aby wyczyścić zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b1565-168">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="b1565-169">Znany problem</span><span class="sxs-lookup"><span data-stu-id="b1565-169">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1565-170">Istnieje znany problem w Podglądzie zdarzeń, jeżeli nie może zdekodować zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="b1565-170">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="b1565-171">Może zostać wyświetlony komunikat błędu, który wygląda następująco.</span><span class="sxs-lookup"><span data-stu-id="b1565-171">You may see an error message that looks like the following.</span></span>  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  <span data-ttu-id="b1565-172">Jeśli wystąpi ten błąd, kliknij przycisk **Odśwież** w okienku Akcje.</span><span class="sxs-lookup"><span data-stu-id="b1565-172">If you encounter this error, click **Refresh** in the actions pane.</span></span> <span data-ttu-id="b1565-173">Zdarzenia powinny teraz dekodowania poprawnie.</span><span class="sxs-lookup"><span data-stu-id="b1565-173">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b1565-174">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b1565-174">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b1565-175">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b1565-175">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b1565-176">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b1565-176">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1565-177">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b1565-177">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a><span data-ttu-id="b1565-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1565-178">See Also</span></span>  
 [<span data-ttu-id="b1565-179">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="b1565-179">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
