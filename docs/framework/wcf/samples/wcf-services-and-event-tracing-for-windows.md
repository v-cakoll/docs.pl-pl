---
title: Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: e1ee7154e2ad5b22ff0debcdd15d5809fc55df13
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044514"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="4730e-102">Usługi i śledzenie zdarzeń programu WCF dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4730e-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="4730e-103">Ten przykład pokazuje, jak używać śledzenia analitycznego w Windows Communication Foundation (WCF) do emisji zdarzeń w usłudze śledzenie zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="4730e-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="4730e-104">Ślady analityczne to zdarzenia emitowane w kluczowych punktach w stosie WCF, które umożliwiają rozwiązywanie problemów z usługami WCF w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="4730e-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="4730e-105">Śledzenie analityczne w usługach WCF to śledzenie, które można włączyć w środowisku produkcyjnym z minimalnym wpływem na wydajność.</span><span class="sxs-lookup"><span data-stu-id="4730e-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="4730e-106">Te ślady są emitowane jako zdarzenia do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="4730e-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="4730e-107">Ten przykład obejmuje podstawową usługę WCF, w której zdarzenia są emitowane z usługi do dziennika zdarzeń, które można wyświetlić przy użyciu Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4730e-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="4730e-108">Istnieje również możliwość uruchomienia dedykowanej sesji ETW, która nasłuchuje zdarzeń z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4730e-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="4730e-109">Przykład zawiera skrypt służący do tworzenia dedykowanej sesji ETW, która przechowuje zdarzenia w pliku binarnym, który można odczytać przy użyciu Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4730e-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="4730e-110">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="4730e-110">To use this sample</span></span>

1. <span data-ttu-id="4730e-111">Za pomocą programu Visual Studio 2012 Otwórz plik rozwiązania EtwAnalyticTraceSample. sln.</span><span class="sxs-lookup"><span data-stu-id="4730e-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="4730e-112">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4730e-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="4730e-113">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4730e-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="4730e-114">W przeglądarce sieci Web kliknij pozycję **Kalkulator. svc**.</span><span class="sxs-lookup"><span data-stu-id="4730e-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="4730e-115">Identyfikator URI dokumentu WSDL dla usługi powinien pojawić się w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="4730e-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="4730e-116">Skopiuj ten identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="4730e-116">Copy that URI.</span></span>

     <span data-ttu-id="4730e-117">Domyślnie usługa zaczyna nasłuchiwanie żądań na porcie 1378 `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="4730e-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="4730e-118">Uruchom klienta testowego WCF (WcfTestClient. exe).</span><span class="sxs-lookup"><span data-stu-id="4730e-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="4730e-119">Klient testowy WCF (WcfTestClient. exe) znajduje się w lokalizacji `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span><span class="sxs-lookup"><span data-stu-id="4730e-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="4730e-120">Domyślny katalog instalacji programu Visual Studio 2012 to `C:\Program Files\Microsoft Visual Studio 10.0`.</span><span class="sxs-lookup"><span data-stu-id="4730e-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="4730e-121">W ramach klienta testowego WCF Dodaj usługę, wybierając pozycję **plik**, a następnie **Dodaj usługę**.</span><span class="sxs-lookup"><span data-stu-id="4730e-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="4730e-122">Dodaj adres punktu końcowego w polu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="4730e-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="4730e-123">Wartość domyślna to `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="4730e-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="4730e-124">Otwórz aplikację Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4730e-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="4730e-125">Przed wywołaniem usługi Uruchom Podgląd zdarzeń i upewnij się, że dziennik zdarzeń nasłuchuje zdarzeń śledzenia emitowanych z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4730e-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="4730e-126">Z menu **Start** wybierz pozycję **Narzędzia administracyjne**, a następnie **Podgląd zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="4730e-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="4730e-127">Włącz dzienniki **analityczne** i **debugowania** .</span><span class="sxs-lookup"><span data-stu-id="4730e-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="4730e-128">W widoku drzewa w Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="4730e-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="4730e-129">Kliknij prawym przyciskiem myszy pozycję **serwer aplikacji — aplikacje**, wybierz polecenie **Widok**, a następnie **Pokaż dzienniki analityczne i debugowania**.</span><span class="sxs-lookup"><span data-stu-id="4730e-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="4730e-130">Upewnij się, że jest zaznaczona opcja **Pokaż dzienniki analityczne i debugowania** .</span><span class="sxs-lookup"><span data-stu-id="4730e-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="4730e-131">Włącz dziennik **analityczny** .</span><span class="sxs-lookup"><span data-stu-id="4730e-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="4730e-132">W widoku drzewa w Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="4730e-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="4730e-133">Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="4730e-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="4730e-134">Aby przetestować usługę</span><span class="sxs-lookup"><span data-stu-id="4730e-134">To test the service</span></span>

1. <span data-ttu-id="4730e-135">Wróć do klienta testowego WCF i kliknij dwukrotnie `Divide` i Zachowaj wartości domyślne, które określają mianownik równy 0.</span><span class="sxs-lookup"><span data-stu-id="4730e-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="4730e-136">Jeśli mianownik ma wartość 0, usługa zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="4730e-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="4730e-137">Obserwuj zdarzenia emitowane z usługi.</span><span class="sxs-lookup"><span data-stu-id="4730e-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="4730e-138">Przełącz się z powrotem do Podgląd zdarzeń i przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="4730e-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="4730e-139">Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz polecenie **Odśwież**.</span><span class="sxs-lookup"><span data-stu-id="4730e-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="4730e-140">Zdarzenia śledzenia analitycznego WCF są wyświetlane w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4730e-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="4730e-141">Zwróć uwagę, że ponieważ błąd został zgłoszony przez usługę, w Podglądzie zdarzeń jest wyświetlane zdarzenie śledzenia błędów.</span><span class="sxs-lookup"><span data-stu-id="4730e-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="4730e-142">Powtórz kroki 1 i 2, ale z prawidłowymi danymi wejściowymi.</span><span class="sxs-lookup"><span data-stu-id="4730e-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="4730e-143">Wartość `N2` parametru może być dowolną liczbą inną niż 0.</span><span class="sxs-lookup"><span data-stu-id="4730e-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="4730e-144">Odśwież kanał analityczny, aby wyświetlić zdarzenia WCF nie uwzględniają żadnych zdarzeń błędów.</span><span class="sxs-lookup"><span data-stu-id="4730e-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="4730e-145">Przykład demonstruje zdarzenia śledzenia analitycznego emitowane z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4730e-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="4730e-146">Aby oczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="4730e-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="4730e-147">Otwórz Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4730e-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="4730e-148">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="4730e-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="4730e-149">Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz polecenie **Wyłącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="4730e-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="4730e-150">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="4730e-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="4730e-151">Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Wyczyść dziennik**.</span><span class="sxs-lookup"><span data-stu-id="4730e-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="4730e-152">Wybierz opcję **Wyczyść** , aby wyczyścić zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4730e-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4730e-153">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4730e-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4730e-154">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="4730e-154">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4730e-155">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="4730e-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4730e-156">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4730e-156">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="4730e-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4730e-157">See also</span></span>

- [<span data-ttu-id="4730e-158">Przykłady monitorowania oprogramowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="4730e-158">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
