---
title: Używanie liczników wydajności
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 8784b4a481b8313d370aad1d8f265dcb44ab3ed6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="using-performance-counters"></a><span data-ttu-id="ffab0-102">Używanie liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="ffab0-102">Using Performance Counters</span></span>
<span data-ttu-id="ffab0-103">W tym przykładzie przedstawiono sposób dostępu do liczników wydajności systemu Windows Communication Foundation (WCF) oraz sposobu tworzenia liczników wydajności zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ffab0-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="ffab0-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ffab0-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffab0-105">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ffab0-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ffab0-106">W tym przykładzie klient wywołuje metody cztery `ICalculator` usługi.</span><span class="sxs-lookup"><span data-stu-id="ffab0-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="ffab0-107">Klient w dalszym ciągu to zrobić, dopóki nie zostanie przerwane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ffab0-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="ffab0-108">Usługa pozostanie bez zmian.</span><span class="sxs-lookup"><span data-stu-id="ffab0-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="ffab0-109">Liczniki wydajności są włączone w sekcji Diagnostyka pliku Web.config dla usługi, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="ffab0-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ffab0-110">To zadanie można również wykonać za pomocą [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ffab0-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="ffab0-111">Jeśli liczniki wydajności są włączone, cały zestaw liczników wydajności usługi WCF jest włączone dla usługi.</span><span class="sxs-lookup"><span data-stu-id="ffab0-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="ffab0-112">.NET Framework automatycznie przechowuje dane dotyczące wydajności na trzech poziomach: `ServiceModelService`, `ServiceModelEndpoint` i `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="ffab0-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="ffab0-113">Każda z tych poziomów ma liczniki wydajności, takich jak "Wywołania", "Wywołania na sekundę" i "Zabezpieczenia wywołania nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="ffab0-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ffab0-114">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="ffab0-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ffab0-115">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ffab0-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ffab0-116">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ffab0-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ffab0-117">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ffab0-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="ffab0-118">Aby wyświetlić dane wydajności</span><span class="sxs-lookup"><span data-stu-id="ffab0-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="ffab0-119">Uruchom narzędzie monitora wydajności, klikając **Start**, **Uruchom...** , wprowadź `perfmon` i kliknij przycisk **OK** lub z poziomu Panelu sterowania, wybierz **narzędzia administracyjne** i kliknij dwukrotnie **wydajności**.</span><span class="sxs-lookup"><span data-stu-id="ffab0-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffab0-120">Nie można dodać liczniki, dopóki nie zostanie uruchomiony w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ffab0-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="ffab0-121">Usuń liczniki wydajności, które są wyświetlane, zaznaczając je i naciskając klawisz Delete.</span><span class="sxs-lookup"><span data-stu-id="ffab0-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="ffab0-122">Dodaj liczniki WCF prawym przyciskiem myszy okienko Wykres i wybierając **Dodaj liczniki**.</span><span class="sxs-lookup"><span data-stu-id="ffab0-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="ffab0-123">W **Dodaj liczniki** okno dialogowe, wybierz opcję **ServiceModelOperation 3.0.0.0 ServiceModelEndpoint 3.0.0.0 i ServiceModelService 3.0.0.0** w obiekcie wydajności listy rozwijanej pola listy.</span><span class="sxs-lookup"><span data-stu-id="ffab0-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="ffab0-124">Wybierz liczniki, które mają być wyświetlane na liście.</span><span class="sxs-lookup"><span data-stu-id="ffab0-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffab0-125">Nie ma żadnych liczniki wydajności programu WCF dla usługi, jeśli nie są żadne usługi WCF uruchomionej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ffab0-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="ffab0-126">Aby włączyć liczniki za pomocą edytora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ffab0-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="ffab0-127">Otwórz wystąpienie SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="ffab0-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="ffab0-128">W menu Plik kliknij polecenie **Otwórz** , a następnie kliknij przycisk **pliku konfiguracji...** .</span><span class="sxs-lookup"><span data-stu-id="ffab0-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="ffab0-129">Przejdź do folderu usługi przykładowej aplikacji, a następnie otwórz plik Web.config.</span><span class="sxs-lookup"><span data-stu-id="ffab0-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="ffab0-130">Kliknij przycisk **diagnostyki** na drzewie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ffab0-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="ffab0-131">Przełącz **licznika wydajności** w **diagnostyki** okno, aby wyświetlić "All".</span><span class="sxs-lookup"><span data-stu-id="ffab0-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="ffab0-132">Zapisz plik konfiguracji i zamknij Edytor.</span><span class="sxs-lookup"><span data-stu-id="ffab0-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffab0-133">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ffab0-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ffab0-134">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ffab0-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ffab0-135">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ffab0-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ffab0-136">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ffab0-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="ffab0-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ffab0-137">See Also</span></span>  
 [<span data-ttu-id="ffab0-138">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="ffab0-138">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
