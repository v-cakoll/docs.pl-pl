---
title: Buforowane odbierania
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9cd4dfcbfc9d417766615c624905f8bce2c10e54
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="buffered-receive"></a><span data-ttu-id="61943-102">Buforowane odbierania</span><span class="sxs-lookup"><span data-stu-id="61943-102">Buffered Receive</span></span>
<span data-ttu-id="61943-103">W tym przykładzie pokazano, jak instalowanie i konfigurowanie funkcję odbierania buforowane w [!INCLUDE[wf](../../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61943-103">This sample demonstrates how to set up and configure the buffered receive feature in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span> <span data-ttu-id="61943-104">Buforowane odbierania umożliwia autorowi przepływu pracy utworzyć przepływ pracy bez konieczności martwić o kolejność, w którym są odbierane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="61943-104">Buffered receive allows the workflow author to create a workflow without having to worry about the order in which messages are received.</span></span> <span data-ttu-id="61943-105">Funkcja odbierania buforowanego buforuje wiadomości lokalnie i dostarcza je, gdy przepływ pracy jest gotowa do ich odebrania.</span><span class="sxs-lookup"><span data-stu-id="61943-105">The buffered receive feature buffers messages locally and delivers them when the workflow is ready to receive them.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="61943-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="61943-106">Demonstrates</span></span>  
 <span data-ttu-id="61943-107">Przetwarzanie komunikatów poza kolejnością. przy użyciu buforowanych odbierać z działań dotyczących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="61943-107">Out-of-order message processing using buffered receive with messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="61943-108">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="61943-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="61943-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="61943-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="61943-110">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="61943-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="61943-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="61943-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a><span data-ttu-id="61943-112">Omówienie</span><span class="sxs-lookup"><span data-stu-id="61943-112">Discussion</span></span>  
 <span data-ttu-id="61943-113">W tym przykładzie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługa jest wdrażana przy użyciu [!INCLUDE[wf1](../../../../includes/wf1-md.md)] i ma sekwencji <xref:System.ServiceModel.Activities.Receive> działań.</span><span class="sxs-lookup"><span data-stu-id="61943-113">In this sample, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is implemented using [!INCLUDE[wf1](../../../../includes/wf1-md.md)] and has a sequence of <xref:System.ServiceModel.Activities.Receive> activities.</span></span> <span data-ttu-id="61943-114">Ten przepływ pracy modele pożyczki prosty proces zatwierdzania, gdy przepływ pracy oczekuje trzy powiadomienia pożyczki zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="61943-114">This workflow models a simple loan approval process where the workflow expects three notifications for a loan to be approved.</span></span> <span data-ttu-id="61943-115">A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacja kliencka wysyła trzy skorelowane powiadomienia w odwrotnej kolejności oczekuje usługi.</span><span class="sxs-lookup"><span data-stu-id="61943-115">A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application sends three correlated notifications in the reverse order of what the service expects.</span></span> <span data-ttu-id="61943-116">Ponieważ funkcja buforowanego receive jest włączona w usłudze, każdy komunikat poza kolejnością jest buforowana w usłudze i przetwarzania przepływu pracy będzie gotowa do odbioru go.</span><span class="sxs-lookup"><span data-stu-id="61943-116">Because the buffered receive feature is turned on at the service, each out-of-order message is buffered at the service and processed as the workflow becomes ready to receive it.</span></span>  
  
 <span data-ttu-id="61943-117">Funkcja odbierania buforowanego wymaga <xref:System.ServiceModel.Activities.ReceiveContent> wsparciu powiązanie, w związku z tym usługa używa <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="61943-117">The buffered receive feature requires <xref:System.ServiceModel.Activities.ReceiveContent> support from the binding, therefore the service uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="61943-118">Konfiguracja nie specjalne jest wymagane dla tego powiązania, dlatego są używane wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="61943-118">No special configuration is required for the binding, so the defaults are used.</span></span>  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 <span data-ttu-id="61943-119">Usługa udostępnia również metadanych dla usługi przy użyciu <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="61943-119">The service also exposes metadata for the service using <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span></span>  
  
 <span data-ttu-id="61943-120">Podobnie, klient punkt końcowy skonfigurowany przy użyciu <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="61943-120">Similarly, the client endpoint is configured using <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="61943-121">Kod klienta i konfiguracji jest generowany przy użyciu **Dodaj odwołanie do usługi** funkcji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="61943-121">The client code and configuration is generated by using the **Add Service Reference** feature of Visual Studio.</span></span> <span data-ttu-id="61943-122">Poniższy przykład jest punkt końcowy wygenerowanego klienta w pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="61943-122">The following example is the generated client endpoint in the App.config file.</span></span>  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 <span data-ttu-id="61943-123">W tym przykładzie wymaga włączenia następujące składniki systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="61943-123">This sample requires that the following Windows components are enabled:</span></span>  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]<span data-ttu-id="61943-124"> Zgodność z narzędziami zarządzania metabazy i zgodności konfiguracji</span><span class="sxs-lookup"><span data-stu-id="61943-124"> Management Compatibility, Metabase, and Configuration Compatibility</span></span>  
  
3.  <span data-ttu-id="61943-125">Usługi sieci World Wide Web, funkcje tworzenia aplikacji i programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="61943-125">World Wide Web Services, Application Development Features, and ASP.NET</span></span>  
  
4.  <span data-ttu-id="61943-126">Wiadomości firmy Microsoft (MSMQ) kolejek serwera</span><span class="sxs-lookup"><span data-stu-id="61943-126">Microsoft Message Queues (MSMQ) Server</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="61943-127">Do ustawiania i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="61943-127">To set up, and build the sample</span></span>  
  
1.  <span data-ttu-id="61943-128">W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, zarejestrować platformę ASP.NET, wpisując `aspnet_regiis –I` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="61943-128">At a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by typing `aspnet_regiis –I` and press ENTER.</span></span>  
  
2.  <span data-ttu-id="61943-129">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako Administrator.</span><span class="sxs-lookup"><span data-stu-id="61943-129">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an Administrator.</span></span>  
  
3.  <span data-ttu-id="61943-130">Otwórz LoanService.sln.</span><span class="sxs-lookup"><span data-stu-id="61943-130">Open LoanService.sln.</span></span>  
  
4.  <span data-ttu-id="61943-131">Po otrzymaniu monitu, jeśli chcesz utworzyć wirtualne katalogi dla projektu LoanService, wybierz **tak**.</span><span class="sxs-lookup"><span data-stu-id="61943-131">When asked if you would like to create the virtual directories for the LoanService project, select **Yes**.</span></span>  
  
#### <a name="to-set-up-the-service-queues"></a><span data-ttu-id="61943-132">Aby skonfigurować usługi kolejki</span><span class="sxs-lookup"><span data-stu-id="61943-132">To set up the service queues</span></span>  
  
1.  <span data-ttu-id="61943-133">Naciśnij klawisz F5, aby uruchomić aplikację LoanClient, która tworzy kolejek i aktywuje usługę zdefiniowane w Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="61943-133">Press F5 to run the LoanClient application that creates the queues and activates the service defined in Service1.xamlx.</span></span>  
  
2.  <span data-ttu-id="61943-134">Otwórz **Zarządzanie komputerem** konsoli, uruchamiając Compmgmt.msc z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61943-134">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
3.  <span data-ttu-id="61943-135">W **Zarządzanie komputerem** rozwiń **usługi**, **aplikacji**, **usługi kolejkowania komunikatów**, **kolejki prywatne** .</span><span class="sxs-lookup"><span data-stu-id="61943-135">In the **Computer Management** console, expand **Service**, **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
4.  <span data-ttu-id="61943-136">Kliknij prawym przyciskiem myszy kolejki loanservice/service1.xamlx i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="61943-136">Right-click the loanservice/service1.xamlx queue and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="61943-137">Wybierz **zabezpieczeń** karta i Dodaj **komunikat odbiera wszyscy**, **wglądu do wiadomości** i **wysyłania komunikatu** uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="61943-137">Select the **Security** tab, and add **Everyone Receives Message**, **Peek Message** and **Send Message** permissions.</span></span>  
  
6.  <span data-ttu-id="61943-138">Otwórz [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.</span><span class="sxs-lookup"><span data-stu-id="61943-138">Open the [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.</span></span>  
  
7.  <span data-ttu-id="61943-139">Przejdź do **serwera**, **witryny**, **domyślnej witryny sieci Web**, **prywatnej**, **LoanService** i wybierz  **Opcje zaawansowane**</span><span class="sxs-lookup"><span data-stu-id="61943-139">Browse to **Server**, **Sites**, **Default Web site**, **Private**, **LoanService** and select **Advanced Options**</span></span>  
  
8.  <span data-ttu-id="61943-140">Zmień **włączone protokoły** jako **http**, **net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="61943-140">Change the **Enabled Protocols** to be **http**, **net.msmq**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="61943-141">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="61943-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="61943-142">Przejdź do http://localhost/private/loanservice/service1.xamlx aby upewnić się, że usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="61943-142">Browse to http://localhost/private/loanservice/service1.xamlx to ensure that the service is running.</span></span>  
  
2.  <span data-ttu-id="61943-143">Naciśnij klawisz F5, aby uruchomić aplikację LoanClient.</span><span class="sxs-lookup"><span data-stu-id="61943-143">Press F5 to run the LoanClient application.</span></span> <span data-ttu-id="61943-144">Po zakończeniu przepływu pracy należy można zapisać pliku out.txt C:\Inbox zawierający wynik wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="61943-144">Once the workflow is complete, an out.txt file should be saved to C:\Inbox that contains the result of the message exchange.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="61943-145">Aby wyczyścić</span><span class="sxs-lookup"><span data-stu-id="61943-145">To clean up</span></span>  
  
1.  <span data-ttu-id="61943-146">Otwórz **Zarządzanie komputerem** konsoli, uruchamiając Compmgmt.msc z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61943-146">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
2.  <span data-ttu-id="61943-147">Rozwiń węzeł **usługi** i **aplikacji**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="61943-147">Expand **Service** and **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="61943-148">Usuwanie kolejki loanservice/service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="61943-148">Delete the loanservice/service1.xamlx queue.</span></span>  
  
4.  <span data-ttu-id="61943-149">Usuń katalog C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="61943-149">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="61943-150">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="61943-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="61943-151">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="61943-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="61943-152">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="61943-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="61943-153">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="61943-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
