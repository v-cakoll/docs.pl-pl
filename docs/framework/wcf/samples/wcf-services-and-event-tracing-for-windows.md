---
title: "Usługi i śledzenie zdarzeń programu WCF dla systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb8924cc04442e3b9eda5e251e6dcdc57f5660c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="754ec-102">Usługi i śledzenie zdarzeń programu WCF dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="754ec-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="754ec-103">W tym przykładzie przedstawiono sposób użycia śledzenie analityczne w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] do wysyłania zdarzeń w zdarzenia śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="754ec-103">This sample demonstrates how to use the analytic tracing in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="754ec-104">Śledzenie analityczne są zdarzenia wysyłanego w punktach klucza [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu, który umożliwia rozwiązywanie problemów z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="754ec-104">The analytic traces are events emitted at key points in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stack that allow troubleshooting of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services in production environment.</span></span>  
  
 <span data-ttu-id="754ec-105">Śledzenie analityczne w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi śledzenia, który może być włączony w środowisku produkcyjnym z minimalnym wpływem na wydajność.</span><span class="sxs-lookup"><span data-stu-id="754ec-105">Analytic trace in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="754ec-106">Te operacje śledzenia są emitowane jako zdarzenia do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="754ec-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="754ec-107">Ten przykład zawiera podstawowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w zdarzenia, które są emitowane przez usługę w dzienniku zdarzeń, które można wyświetlić za pomocą Podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="754ec-107">This sample includes a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="754ec-108">Istnieje również możliwość rozpocząć sesję ETW dedykowanych nasłuchuje zdarzeń z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="754ec-108">It is also possible to start a dedicated ETW session that listens for events from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="754ec-109">Przykład obejmuje skrypt służący do tworzenia dedykowanych sesji funkcji ETW, która zapisuje zdarzenia w pliku binarnego, który może zostać odczytany za pomocą Podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="754ec-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="754ec-110">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="754ec-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="754ec-111">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="754ec-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="754ec-112">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="754ec-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="754ec-113">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="754ec-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="754ec-114">W przeglądarce sieci Web, kliknij przycisk **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="754ec-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="754ec-115">Identyfikator URI dokumentu WSDL dla usługi powinien zostać wyświetlony w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="754ec-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="754ec-116">Skopiuj ten identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="754ec-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="754ec-117">Domyślnie usługa rozpoczyna nasłuchiwanie na porcie 1378 (http://localhost:1378/Calculator.svc) żądań.</span><span class="sxs-lookup"><span data-stu-id="754ec-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="754ec-118">Uruchom [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta testowego (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="754ec-118">Run the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="754ec-119">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Klienta testowego (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] zainstalować Dir > \Common7\IDE\ WcfTestClient.exe (domyślny [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir instalacji to C:\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="754ec-119">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="754ec-120">W ramach [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Klient testowy, Dodaj usługę, wybierając **pliku**, a następnie **Dodaj usługę**.</span><span class="sxs-lookup"><span data-stu-id="754ec-120">Within the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="754ec-121">Dodaj adres punktu końcowego w odpowiednim polu.</span><span class="sxs-lookup"><span data-stu-id="754ec-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="754ec-122">Wartość domyślna to http://localhost:1378/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="754ec-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="754ec-123">Otwórz aplikację Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="754ec-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="754ec-124">Przed wywołaniem usługi, Uruchom Podgląd zdarzeń i upewnij się, nasłuchują dziennika zdarzeń dla zdarzenia śledzenia wyemitowanego z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="754ec-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
7.  <span data-ttu-id="754ec-125">Z **Start** menu, wybierz opcję **narzędzia administracyjne**, a następnie **Podgląd zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="754ec-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="754ec-126">Włącz **analityczne** i **debugowania** dzienniki.</span><span class="sxs-lookup"><span data-stu-id="754ec-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="754ec-127">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="754ec-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="754ec-128">Kliknij prawym przyciskiem myszy **aplikacji serwerowych aplikacji**, wybierz pozycję **widoku**, a następnie **dzienniki Pokaż analityczne i debugowania**.</span><span class="sxs-lookup"><span data-stu-id="754ec-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="754ec-129">Upewnij się, że **dzienniki Pokaż analityczne i debugowania** zaznaczenia pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="754ec-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="754ec-130">Włącz **analityczne** dziennika.</span><span class="sxs-lookup"><span data-stu-id="754ec-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="754ec-131">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="754ec-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="754ec-132">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="754ec-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="754ec-133">Aby przetestować usługę</span><span class="sxs-lookup"><span data-stu-id="754ec-133">To test the service</span></span>  
  
1.  <span data-ttu-id="754ec-134">Przywraca [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przetestować klienta, a następnie kliknij dwukrotnie ikonę `Divide` i Zachowaj wartości domyślne, które określają denominator 0.</span><span class="sxs-lookup"><span data-stu-id="754ec-134">Switch back to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="754ec-135">Jeżeli dzielnik wynosi 0, usługa zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="754ec-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="754ec-136">Sprawdź zdarzenia wysyłanego z usługi.</span><span class="sxs-lookup"><span data-stu-id="754ec-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="754ec-137">Wrócić do podglądu zdarzeń, a następnie przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="754ec-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="754ec-138">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.</span><span class="sxs-lookup"><span data-stu-id="754ec-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="754ec-139">Zdarzenia śledzenia analitycznego WCF są wyświetlane w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="754ec-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="754ec-140">Zauważ, że ponieważ błąd został zgłoszony przez usługę zdarzenie śledzenia błędu jest wyświetlana w zdarzeniu podglądu.</span><span class="sxs-lookup"><span data-stu-id="754ec-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="754ec-141">Powtórz kroki 1 i 2, ale z prawidłowe wartości wejściowe.</span><span class="sxs-lookup"><span data-stu-id="754ec-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="754ec-142">Wartość `N2` parametr może być dowolna liczba innych niż 0.</span><span class="sxs-lookup"><span data-stu-id="754ec-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="754ec-143">Odśwież analityczne kanału, aby wyświetlić usługi WCF zdarzeń nie ma zdarzenia błędów.</span><span class="sxs-lookup"><span data-stu-id="754ec-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="754ec-144">W przykładzie pokazano zdarzenia śledzenia analitycznego wyemitowanego z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="754ec-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="754ec-145">Do oczyszczania (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="754ec-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="754ec-146">Otwórz Podgląd zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="754ec-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="754ec-147">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="754ec-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="754ec-148">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączyć dziennika**.</span><span class="sxs-lookup"><span data-stu-id="754ec-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="754ec-149">Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**.</span><span class="sxs-lookup"><span data-stu-id="754ec-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="754ec-150">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.</span><span class="sxs-lookup"><span data-stu-id="754ec-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="754ec-151">Wybierz **wyczyść** opcję, aby wyczyścić zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="754ec-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="754ec-152">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="754ec-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="754ec-153">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="754ec-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="754ec-154">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="754ec-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="754ec-155">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="754ec-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="754ec-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="754ec-156">See Also</span></span>  
 [<span data-ttu-id="754ec-157">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="754ec-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
