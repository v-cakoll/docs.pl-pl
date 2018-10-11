---
title: Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 6684f6415fa6ee82a59fc9b54911b5c65d6dadb2
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086586"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="2ea44-102">Usługi i śledzenie zdarzeń programu WCF dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ea44-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="2ea44-103">Ten przykład pokazuje sposób użycia śledzenia danych analitycznych w Windows Communication Foundation (WCF) aby emitować zdarzenia w śledzenie zdarzeń dla Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="2ea44-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="2ea44-104">Śledzenie analityczne są zdarzenia emitowane w kluczowych punktach w stosie usługi WCF, które umożliwiają rozwiązywanie problemów z usług WCF w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2ea44-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="2ea44-105">Śledzenie jest śledzenia analitycznego w usługach WCF, która może zostać włączona w środowisku produkcyjnym przy minimalnym wpływie na wydajność.</span><span class="sxs-lookup"><span data-stu-id="2ea44-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="2ea44-106">Ślady te są emitowane jako zdarzenia do sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="2ea44-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="2ea44-107">W tym przykładzie zawiera podstawowe usługi WCF, w której zdarzenia są emitowane z usługi w dzienniku zdarzeń, które można przeglądać za pomocą Podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2ea44-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="2ea44-108">Jest również możliwe do uruchomienia w dedykowanym sesji ETW, który nasłuchuje zdarzeń z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="2ea44-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="2ea44-109">Przykład obejmuje skrypt służący do tworzenia dedykowanych sesja funkcji ETW, który przechowuje zdarzenia w pliku binarnym, który może zostać odczytany za pomocą Podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2ea44-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="2ea44-110">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="2ea44-110">To use this sample</span></span>

1.  <span data-ttu-id="2ea44-111">Za pomocą programu Visual Studio 2012, otwórz plik rozwiązania EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="2ea44-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2.  <span data-ttu-id="2ea44-112">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="2ea44-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="2ea44-113">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="2ea44-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="2ea44-114">W przeglądarce internetowej kliknij **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="2ea44-115">Identyfikator URI dokumentu WSDL usługi powinna zostać wyświetlona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="2ea44-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="2ea44-116">Skopiuj ten identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="2ea44-116">Copy that URI.</span></span>

     <span data-ttu-id="2ea44-117">Domyślnie usługa rozpoczyna nasłuchiwanie żądań na porcie 1378 (http://localhost:1378/Calculator.svc).</span><span class="sxs-lookup"><span data-stu-id="2ea44-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>

4.  <span data-ttu-id="2ea44-118">Uruchom klienta testowego WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="2ea44-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="2ea44-119">Testowy klient WCF (WcfTestClient.exe) znajduje się w \<Visual Studio 2012 zainstalować Dir > \Common7\IDE\ WcfTestClient.exe (katalog domyślny program Visual Studio 2012 to C:\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="2ea44-119">The WCF test client (WcfTestClient.exe) is located in the \<Visual Studio 2012 Install Dir>\Common7\IDE\ WcfTestClient.exe (default Visual Studio 2012 install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>

5.  <span data-ttu-id="2ea44-120">W kliencie testowym WCF, należy dodać usługę, wybierając **pliku**, a następnie **Dodaj usługę**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-120">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="2ea44-121">W polu wejściowym, należy dodać adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2ea44-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="2ea44-122">Wartość domyślna to `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="2ea44-122">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6.  <span data-ttu-id="2ea44-123">Otwórz aplikację Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2ea44-123">Open the Event Viewer application.</span></span>

     <span data-ttu-id="2ea44-124">Przed wywołaniem usługi, Uruchom Podgląd zdarzeń i upewnij się, że w dzienniku zdarzeń nasłuchuje śledzenia zdarzeń wysyłanego z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="2ea44-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7.  <span data-ttu-id="2ea44-125">Z **Start** menu, wybierz opcję **narzędzia administracyjne**, a następnie **Podgląd zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="2ea44-126">Włącz **analityczne** i **debugowania** dzienniki.</span><span class="sxs-lookup"><span data-stu-id="2ea44-126">Enable the **Analytic** and **Debug** logs.</span></span>

8.  <span data-ttu-id="2ea44-127">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="2ea44-128">Kliknij prawym przyciskiem myszy **aplikacje serwera aplikacji**, wybierz opcję **widoku**, a następnie **Pokaż analityczne i debugowania dzienniki**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="2ea44-129">Upewnij się, że **Pokaż analityczne i debugowania dzienniki** opcja jest zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="2ea44-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="2ea44-130">Włącz **analityczne** dziennika.</span><span class="sxs-lookup"><span data-stu-id="2ea44-130">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="2ea44-131">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="2ea44-132">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-132">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="2ea44-133">Aby przetestować usługę</span><span class="sxs-lookup"><span data-stu-id="2ea44-133">To test the service</span></span>

1.  <span data-ttu-id="2ea44-134">Przejdź z powrotem do klienta testowego WCF, a następnie kliknij dwukrotnie ikonę `Divide` i Zachowaj wartości domyślne, które określają mianownik 0.</span><span class="sxs-lookup"><span data-stu-id="2ea44-134">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="2ea44-135">Jeżeli mianownik wynosi 0, usługa zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="2ea44-135">If the denominator is 0, then the service throws a fault.</span></span>

2.  <span data-ttu-id="2ea44-136">Sprawdź zdarzenia wysyłanego z usługi.</span><span class="sxs-lookup"><span data-stu-id="2ea44-136">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="2ea44-137">Przejdź z powrotem do programu Podgląd zdarzeń i przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="2ea44-138">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-138">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="2ea44-139">Zdarzenia śledzenia analitycznego WCF są wyświetlane w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2ea44-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="2ea44-140">Zauważ, że ponieważ błąd został zgłoszony przez usługę, którą zdarzenie śledzenia błędu jest wyświetlana w zdarzeniu podglądu.</span><span class="sxs-lookup"><span data-stu-id="2ea44-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3.  <span data-ttu-id="2ea44-141">Powtórz kroki 1 i 2, ale z prawidłowych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="2ea44-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="2ea44-142">Wartość `N2` parametr może być dowolna liczba innych niż 0.</span><span class="sxs-lookup"><span data-stu-id="2ea44-142">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="2ea44-143">Odśwież kanał analityczne, aby wyświetlić WCF zdarzeń nie ma żadnych zdarzeń błędu.</span><span class="sxs-lookup"><span data-stu-id="2ea44-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="2ea44-144">W przykładzie pokazano zdarzenia śledzenia analitycznego wysyłanego z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="2ea44-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="2ea44-145">Aby oczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="2ea44-145">To cleanup (Optional)</span></span>

1.  <span data-ttu-id="2ea44-146">Otwórz Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2ea44-146">Open Event Viewer.</span></span>

2.  <span data-ttu-id="2ea44-147">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="2ea44-148">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączanie dziennika**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-148">Right-click **Analytic** and select **Disable Log**.</span></span>

3.  <span data-ttu-id="2ea44-149">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="2ea44-150">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.</span><span class="sxs-lookup"><span data-stu-id="2ea44-150">Right-click **Analytic** and select **Clear Log**.</span></span>

4.  <span data-ttu-id="2ea44-151">Wybierz **wyczyść** możliwość wyczyszczenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2ea44-151">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="2ea44-152">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2ea44-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2ea44-153">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2ea44-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2ea44-154">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2ea44-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2ea44-155">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2ea44-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="2ea44-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ea44-156">See Also</span></span>  
 [<span data-ttu-id="2ea44-157">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="2ea44-157">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
