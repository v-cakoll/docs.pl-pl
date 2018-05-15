---
title: Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ea917ee87b598fc3ad01df70d9aedfadfd1396a4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="b9c07-102">Usługi i śledzenie zdarzeń programu WCF dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9c07-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="b9c07-103">W tym przykładzie przedstawiono sposób użycia śledzenie analityczne w systemie Windows Communication Foundation (WCF) do wysyłania zdarzeń w zdarzenia śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="b9c07-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="b9c07-104">Śledzenie analityczne są zdarzenia emitowane na klucz wskazuje na stosie WCF, umożliwiających rozwiązywanie problemów z usług WCF w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="b9c07-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>  
  
 <span data-ttu-id="b9c07-105">Śledzenia analitycznego w usługach WCF jest śledzenie, które mogą być włączone w środowisku produkcyjnym z minimalnym wpływem na wydajność.</span><span class="sxs-lookup"><span data-stu-id="b9c07-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="b9c07-106">Te operacje śledzenia są emitowane jako zdarzenia do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="b9c07-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="b9c07-107">Ten przykład zawiera podstawowe usługi WCF, w której zdarzenia są emitowane przez usługę w dzienniku zdarzeń, które można wyświetlić za pomocą Podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b9c07-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="b9c07-108">Istnieje również możliwość rozpocząć sesję ETW dedykowanych nasłuchuje zdarzeń z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b9c07-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="b9c07-109">Przykład obejmuje skrypt służący do tworzenia dedykowanych sesji funkcji ETW, która zapisuje zdarzenia w pliku binarnego, który może zostać odczytany za pomocą Podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b9c07-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b9c07-110">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="b9c07-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="b9c07-111">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="b9c07-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b9c07-112">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b9c07-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b9c07-113">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="b9c07-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="b9c07-114">W przeglądarce sieci Web, kliknij przycisk **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="b9c07-115">Identyfikator URI dokumentu WSDL dla usługi powinien zostać wyświetlony w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="b9c07-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="b9c07-116">Skopiuj ten identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="b9c07-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="b9c07-117">Domyślnie usługa rozpoczyna nasłuchiwanie na porcie 1378 żądań (http://localhost:1378/Calculator.svc).</span><span class="sxs-lookup"><span data-stu-id="b9c07-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="b9c07-118">Uruchomić klienta testowego WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="b9c07-118">Run the WCF test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="b9c07-119">Klienta testowego WCF (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] zainstalować Dir > \Common7\IDE\ WcfTestClient.exe (domyślny [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir instalacji to C:\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="b9c07-119">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="b9c07-120">W kliencie testowym WCF, Dodaj usługę, wybierając **pliku**, a następnie **Dodaj usługę**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-120">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="b9c07-121">Dodaj adres punktu końcowego w odpowiednim polu.</span><span class="sxs-lookup"><span data-stu-id="b9c07-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="b9c07-122">Wartość domyślna to http://localhost:1378/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="b9c07-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="b9c07-123">Otwórz aplikację Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b9c07-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="b9c07-124">Przed wywołaniem usługi, należy uruchomić Podgląd zdarzeń i upewnij się, czy dziennik zdarzeń nasłuchuje śledzenia zdarzeń wysyłanego z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b9c07-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>  
  
7.  <span data-ttu-id="b9c07-125">Z **Start** menu, wybierz opcję **narzędzia administracyjne**, a następnie **Podgląd zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="b9c07-126">Włącz **analityczne** i **debugowania** dzienniki.</span><span class="sxs-lookup"><span data-stu-id="b9c07-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="b9c07-127">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="b9c07-128">Kliknij prawym przyciskiem myszy **aplikacji serwerowych aplikacji**, wybierz pozycję **widoku**, a następnie **dzienniki Pokaż analityczne i debugowania**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="b9c07-129">Upewnij się, że **dzienniki Pokaż analityczne i debugowania** zaznaczenia pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="b9c07-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="b9c07-130">Włącz **analityczne** dziennika.</span><span class="sxs-lookup"><span data-stu-id="b9c07-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="b9c07-131">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="b9c07-132">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="b9c07-133">Aby przetestować usługę</span><span class="sxs-lookup"><span data-stu-id="b9c07-133">To test the service</span></span>  
  
1.  <span data-ttu-id="b9c07-134">Przełącza z powrotem do klienta testowego WCF, a następnie kliknij dwukrotnie ikonę `Divide` i Zachowaj wartości domyślne, które określają denominator 0.</span><span class="sxs-lookup"><span data-stu-id="b9c07-134">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="b9c07-135">Jeżeli dzielnik wynosi 0, usługa zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="b9c07-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="b9c07-136">Sprawdź zdarzenia wysyłanego z usługi.</span><span class="sxs-lookup"><span data-stu-id="b9c07-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="b9c07-137">Wrócić do podglądu zdarzeń, a następnie przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="b9c07-138">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="b9c07-139">Zdarzenia śledzenia analitycznego WCF są wyświetlane w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b9c07-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="b9c07-140">Zauważ, że ponieważ błąd został zgłoszony przez usługę zdarzenie śledzenia błędu jest wyświetlana w zdarzeniu podglądu.</span><span class="sxs-lookup"><span data-stu-id="b9c07-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="b9c07-141">Powtórz kroki 1 i 2, ale z prawidłowe wartości wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b9c07-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="b9c07-142">Wartość `N2` parametr może być dowolna liczba innych niż 0.</span><span class="sxs-lookup"><span data-stu-id="b9c07-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="b9c07-143">Odśwież analityczne kanału, aby wyświetlić usługi WCF zdarzeń nie ma zdarzenia błędów.</span><span class="sxs-lookup"><span data-stu-id="b9c07-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="b9c07-144">W przykładzie pokazano zdarzenia śledzenia analitycznego wyemitowanego z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="b9c07-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="b9c07-145">Do oczyszczania (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b9c07-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="b9c07-146">Otwórz Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b9c07-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="b9c07-147">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="b9c07-148">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączyć dziennika**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="b9c07-149">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="b9c07-150">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.</span><span class="sxs-lookup"><span data-stu-id="b9c07-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="b9c07-151">Wybierz **wyczyść** opcję, aby wyczyścić zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b9c07-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9c07-152">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b9c07-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b9c07-153">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b9c07-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b9c07-154">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b9c07-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b9c07-155">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9c07-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="b9c07-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9c07-156">See Also</span></span>  
 [<span data-ttu-id="b9c07-157">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="b9c07-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
