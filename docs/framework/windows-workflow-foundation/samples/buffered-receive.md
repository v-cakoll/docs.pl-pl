---
title: Buforowane odbieranie
ms.date: 03/30/2017
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
ms.openlocfilehash: b95577c71493275f30703b4366fab32a51097bd2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526807"
---
# <a name="buffered-receive"></a><span data-ttu-id="83324-102">Buforowane odbieranie</span><span class="sxs-lookup"><span data-stu-id="83324-102">Buffered Receive</span></span>
<span data-ttu-id="83324-103">W tym przykładzie przedstawiono sposób instalowania i konfigurowania funkcji odbierania buforowaną w Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="83324-103">This sample demonstrates how to set up and configure the buffered receive feature in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="83324-104">Buforowane odbieranie umożliwia autorowi przepływu pracy utworzyć przepływ pracy bez konieczności martwienia się o kolejności, w jakiej komunikaty są odbierane.</span><span class="sxs-lookup"><span data-stu-id="83324-104">Buffered receive allows the workflow author to create a workflow without having to worry about the order in which messages are received.</span></span> <span data-ttu-id="83324-105">Funkcja odbierania buforowanego buforuje wiadomości lokalnie i przekazuje je, gdy przepływ pracy jest gotowa do ich odebrania.</span><span class="sxs-lookup"><span data-stu-id="83324-105">The buffered receive feature buffers messages locally and delivers them when the workflow is ready to receive them.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="83324-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="83324-106">Demonstrates</span></span>  
 <span data-ttu-id="83324-107">Przetwarzanie komunikatów poza kolejnością przy użyciu buforowanego odbierać przy użyciu działań dotyczących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="83324-107">Out-of-order message processing using buffered receive with messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83324-108">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="83324-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83324-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="83324-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="83324-110">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="83324-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83324-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="83324-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a><span data-ttu-id="83324-112">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="83324-112">Discussion</span></span>  
 <span data-ttu-id="83324-113">W tym przykładzie Usługa Windows Communication Foundation (WCF) jest implementowany przy użyciu [!INCLUDE[wf1](../../../../includes/wf1-md.md)] i ma sekwencji <xref:System.ServiceModel.Activities.Receive> działań.</span><span class="sxs-lookup"><span data-stu-id="83324-113">In this sample, a Windows Communication Foundation (WCF) service is implemented using [!INCLUDE[wf1](../../../../includes/wf1-md.md)] and has a sequence of <xref:System.ServiceModel.Activities.Receive> activities.</span></span> <span data-ttu-id="83324-114">Ten przepływ pracy modeli pożyczki prosty proces zatwierdzania, gdy przepływ pracy oczekuje trzech powiadomienia dotyczące pożyczek w celu uzyskania zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="83324-114">This workflow models a simple loan approval process where the workflow expects three notifications for a loan to be approved.</span></span> <span data-ttu-id="83324-115">Aplikacja kliencka Windows Communication Foundation (WCF) wysyła trzy powiadomienia skorelowane w odwrotnej kolejności usługa oczekuje.</span><span class="sxs-lookup"><span data-stu-id="83324-115">A Windows Communication Foundation (WCF) client application sends three correlated notifications in the reverse order of what the service expects.</span></span> <span data-ttu-id="83324-116">Funkcją buforowaną odbierania jest włączony na usługę i każdy komunikat poza kolejnością jest buforowana na usługę i przetwarzane za pomocą przepływu pracy staje się gotowe do jej otrzymania.</span><span class="sxs-lookup"><span data-stu-id="83324-116">Because the buffered receive feature is turned on at the service, each out-of-order message is buffered at the service and processed as the workflow becomes ready to receive it.</span></span>  
  
 <span data-ttu-id="83324-117">Funkcja odbierania buforowanego wymaga <xref:System.ServiceModel.Activities.ReceiveContent> pomocy technicznej firmy powiązanie, w związku z tym usługa używa <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="83324-117">The buffered receive feature requires <xref:System.ServiceModel.Activities.ReceiveContent> support from the binding, therefore the service uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="83324-118">Żadna specjalna konfiguracja jest wymagana do powiązania, więc są używane wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="83324-118">No special configuration is required for the binding, so the defaults are used.</span></span>  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 <span data-ttu-id="83324-119">Usługa udostępnia również metadane dla usługi przy użyciu <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="83324-119">The service also exposes metadata for the service using <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span></span>  
  
 <span data-ttu-id="83324-120">Podobnie, punkt końcowy klienta jest konfigurowana przy użyciu <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="83324-120">Similarly, the client endpoint is configured using <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="83324-121">Kod klienta i konfiguracji jest generowany przy użyciu **Dodaj odwołanie do usługi** funkcji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83324-121">The client code and configuration is generated by using the **Add Service Reference** feature of Visual Studio.</span></span> <span data-ttu-id="83324-122">Poniższy przykład jest punktem końcowym wygenerowanego klienta, w pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="83324-122">The following example is the generated client endpoint in the App.config file.</span></span>  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 <span data-ttu-id="83324-123">Ten przykładowy skrypt wymaga włączenia następujących składników Windows:</span><span class="sxs-lookup"><span data-stu-id="83324-123">This sample requires that the following Windows components are enabled:</span></span>  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]<span data-ttu-id="83324-124"> Zgodność z narzędziami zarządzania, metabazy i zgodności konfiguracji</span><span class="sxs-lookup"><span data-stu-id="83324-124"> Management Compatibility, Metabase, and Configuration Compatibility</span></span>  
  
3.  <span data-ttu-id="83324-125">Usługi World Wide Web, funkcje tworzenia aplikacji i platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="83324-125">World Wide Web Services, Application Development Features, and ASP.NET</span></span>  
  
4.  <span data-ttu-id="83324-126">Microsoft Message kolejki serwer (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="83324-126">Microsoft Message Queues (MSMQ) Server</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="83324-127">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="83324-127">To set up, and build the sample</span></span>  
  
1.  <span data-ttu-id="83324-128">W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, Zarejestruj aplikację ASP.NET, wpisując `aspnet_regiis –I` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="83324-128">At a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by typing `aspnet_regiis –I` and press ENTER.</span></span>  
  
2.  <span data-ttu-id="83324-129">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako Administrator.</span><span class="sxs-lookup"><span data-stu-id="83324-129">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an Administrator.</span></span>  
  
3.  <span data-ttu-id="83324-130">Otwórz LoanService.sln.</span><span class="sxs-lookup"><span data-stu-id="83324-130">Open LoanService.sln.</span></span>  
  
4.  <span data-ttu-id="83324-131">Po wyświetleniu monitu, jeśli chcesz tworzyć katalogi wirtualne LoanService projektu, wybierz opcję **tak**.</span><span class="sxs-lookup"><span data-stu-id="83324-131">When asked if you would like to create the virtual directories for the LoanService project, select **Yes**.</span></span>  
  
#### <a name="to-set-up-the-service-queues"></a><span data-ttu-id="83324-132">Aby skonfigurować usługi kolejki</span><span class="sxs-lookup"><span data-stu-id="83324-132">To set up the service queues</span></span>  
  
1.  <span data-ttu-id="83324-133">Naciśnij klawisz F5, aby uruchomić aplikację LoanClient, która tworzy kolejki i aktywuje usługę zdefiniowane w Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="83324-133">Press F5 to run the LoanClient application that creates the queues and activates the service defined in Service1.xamlx.</span></span>  
  
2.  <span data-ttu-id="83324-134">Otwórz **Zarządzanie komputerem** konsoli, uruchamiając Compmgmt.msc z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="83324-134">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
3.  <span data-ttu-id="83324-135">W **Zarządzanie komputerem** konsoli, rozwiń **usługi**, **aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne** .</span><span class="sxs-lookup"><span data-stu-id="83324-135">In the **Computer Management** console, expand **Service**, **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
4.  <span data-ttu-id="83324-136">Kliknij prawym przyciskiem myszy kolejki loanservice/service1.xamlx, a następnie wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="83324-136">Right-click the loanservice/service1.xamlx queue and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="83324-137">Wybierz **zabezpieczeń** karta i Dodaj **wszyscy odbiera komunikat o**, **wglądu do wiadomości** i **wysyłania komunikatu** uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="83324-137">Select the **Security** tab, and add **Everyone Receives Message**, **Peek Message** and **Send Message** permissions.</span></span>  
  
6.  <span data-ttu-id="83324-138">Otwórz [!INCLUDE[iis60](../../../../includes/iis60-md.md)] menedżera.</span><span class="sxs-lookup"><span data-stu-id="83324-138">Open the [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.</span></span>  
  
7.  <span data-ttu-id="83324-139">Przejdź do **serwera**, **witryn**, **domyślnej witryny sieci Web**, **prywatnej**, **LoanService** i wybierz  **Opcje zaawansowane**</span><span class="sxs-lookup"><span data-stu-id="83324-139">Browse to **Server**, **Sites**, **Default Web site**, **Private**, **LoanService** and select **Advanced Options**</span></span>  
  
8.  <span data-ttu-id="83324-140">Zmiana **włączone protokoły** jako **http**, **net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="83324-140">Change the **Enabled Protocols** to be **http**, **net.msmq**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="83324-141">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="83324-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="83324-142">Przejdź do http://localhost/private/loanservice/service1.xamlx aby upewnić się, że usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="83324-142">Browse to http://localhost/private/loanservice/service1.xamlx to ensure that the service is running.</span></span>  
  
2.  <span data-ttu-id="83324-143">Naciśnij klawisz F5, aby uruchomić aplikację LoanClient.</span><span class="sxs-lookup"><span data-stu-id="83324-143">Press F5 to run the LoanClient application.</span></span> <span data-ttu-id="83324-144">Po ukończeniu przepływu pracy powinien zostać zapisany plik out.txt C:\Inbox zawierającego wynik wymianę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="83324-144">Once the workflow is complete, an out.txt file should be saved to C:\Inbox that contains the result of the message exchange.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="83324-145">Aby wyczyścić</span><span class="sxs-lookup"><span data-stu-id="83324-145">To clean up</span></span>  
  
1.  <span data-ttu-id="83324-146">Otwórz **Zarządzanie komputerem** konsoli, uruchamiając Compmgmt.msc z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="83324-146">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
2.  <span data-ttu-id="83324-147">Rozwiń **usługi** i **aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="83324-147">Expand **Service** and **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="83324-148">Usuń kolejkę loanservice/service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="83324-148">Delete the loanservice/service1.xamlx queue.</span></span>  
  
4.  <span data-ttu-id="83324-149">Usuń katalog C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="83324-149">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83324-150">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="83324-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83324-151">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="83324-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="83324-152">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="83324-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83324-153">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="83324-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
