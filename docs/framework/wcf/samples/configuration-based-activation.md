---
title: Aktywacja oparta na konfiguracji
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: 3ac4edd2a51e4ed8a5c0b7e73d7d1afa31334c33
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="configuration-based-activation"></a><span data-ttu-id="cbc33-102">Aktywacja oparta na konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cbc33-102">Configuration-Based Activation</span></span>
<span data-ttu-id="cbc33-103">W tym przykładzie pokazano, jak można aktywować usługi Windows Communication Foundation (WCF) bez konieczności pliku svc.</span><span class="sxs-lookup"><span data-stu-id="cbc33-103">This sample demonstrates how to activate Windows Communication Foundation (WCF) services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cbc33-104">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cbc33-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cbc33-105">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cbc33-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cbc33-106">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="cbc33-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cbc33-107">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cbc33-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="cbc33-108">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="cbc33-108">Sample Details</span></span>  
 <span data-ttu-id="cbc33-109">W tym przykładzie klient jest klienta testowego WCF, a usługa jest obsługiwana w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="cbc33-109">In this sample, the client is the WCF test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbc33-110">Instrukcje instalacji i kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cbc33-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="cbc33-111">Aktywacja usług bez konieczności pliku svc</span><span class="sxs-lookup"><span data-stu-id="cbc33-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="cbc33-112">W [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], pliku svc nie jest wymagana do aktywacji usługi.</span><span class="sxs-lookup"><span data-stu-id="cbc33-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="cbc33-113">Przyczyną narzut na dodatkowe zarządzanie, ponieważ dodatkowy plik nie jest wymagana, aby wdrożyć i przechowywane wraz z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cbc33-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="cbc33-114">Wraz z wydaniem [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], można skonfigurować składniki aktywacji przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cbc33-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="cbc33-115"> wprowadzono nowy element konfiguracji (<xref:System.ServiceModel.Configuration.ServiceActivationElement>) w <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cbc33-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="cbc33-116"><xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Kolekcja akceptuje kolekcja usług do aktywacji, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="cbc33-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="cbc33-117">Obserwacji dokonanie jest Konfiguracja wygląda bardzo podobnie do konfigurowania plików .svc.</span><span class="sxs-lookup"><span data-stu-id="cbc33-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="cbc33-118">Atrybut dodatkowe wprowadzone jest `relativeAddress` zapewnia adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="cbc33-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="cbc33-119">Adres względny jest również ścieżki wirtualnej dla usługi.</span><span class="sxs-lookup"><span data-stu-id="cbc33-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="cbc33-120">Host pobiera plik z pliku Web.config `virtualPath` lokalizacji, jeśli występuje; w przeciwnym razie hosta wyszukuje jego rekursywnie folderu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="cbc33-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbc33-121">W tym przykładzie wymaga hosting w usługach IIS funkcji.</span><span class="sxs-lookup"><span data-stu-id="cbc33-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cbc33-122">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="cbc33-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="cbc33-123">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik Service.csproj.</span><span class="sxs-lookup"><span data-stu-id="cbc33-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="cbc33-124">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="cbc33-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="cbc33-125">Przetestuj usługę uruchamiając WCFTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="cbc33-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="cbc33-126">Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], przejdź do folderu 10.0\Common7\IDE %SystemDrive%\Program Files\Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cbc33-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="cbc33-127">Uruchom WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="cbc33-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="cbc33-128">Ustaw adres MEX usługi.</span><span class="sxs-lookup"><span data-stu-id="cbc33-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="cbc33-129">Naciśnij klawisze CTRL + SHIFT + A, aby ustawić adres usługi.</span><span class="sxs-lookup"><span data-stu-id="cbc33-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="cbc33-130">Ustaw adres http://localhost/ServiceModelSamples/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="cbc33-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="cbc33-131">Wykonaj `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="cbc33-131">Perform the `Add` operation.</span></span> <span data-ttu-id="cbc33-132">Ustaw wartość na `n1` parametru 10 i ustaw wartość na `n2` parametru do 15.</span><span class="sxs-lookup"><span data-stu-id="cbc33-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="cbc33-133">Naciśnij klawisz **wywołania**.</span><span class="sxs-lookup"><span data-stu-id="cbc33-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="cbc33-134">Oczekiwany wynik to 25.</span><span class="sxs-lookup"><span data-stu-id="cbc33-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cbc33-135">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="cbc33-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cbc33-136">Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbc33-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cbc33-137">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbc33-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="cbc33-138">Po rozwiązaniu został utworzony, uruchom pliku Setup.bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="cbc33-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="cbc33-139">Katalog ServiceModelSamples powinien zostać wyświetlony jako aplikacja IIS.</span><span class="sxs-lookup"><span data-stu-id="cbc33-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="cbc33-140">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbc33-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc33-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbc33-141">See Also</span></span>  
 [<span data-ttu-id="cbc33-142">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="cbc33-142">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
