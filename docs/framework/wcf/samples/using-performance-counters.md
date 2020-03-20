---
title: Używanie liczników wydajności
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143580"
---
# <a name="using-performance-counters"></a><span data-ttu-id="869da-102">Używanie liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="869da-102">Using Performance Counters</span></span>
<span data-ttu-id="869da-103">W tym przykładzie pokazano, jak uzyskać dostęp do liczników wydajności programu Windows Communication Foundation (WCF) i jak tworzyć liczniki wydajności zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="869da-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="869da-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="869da-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="869da-105">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="869da-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="869da-106">W tym przykładzie klient wywołuje cztery `ICalculator` metody usługi.</span><span class="sxs-lookup"><span data-stu-id="869da-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="869da-107">Klient kontynuuje to, dopóki nie zostanie przerwany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="869da-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="869da-108">Usługa pozostaje niezmieniona.</span><span class="sxs-lookup"><span data-stu-id="869da-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="869da-109">Liczniki wydajności są włączone w sekcji diagnostyki pliku Web.config dla usługi, jak pokazano w poniższej przykładowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="869da-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="869da-110">To zadanie można również wykonać za pomocą [narzędzia Edytor konfiguracji (SvcConfigEditor.exe).](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)</span><span class="sxs-lookup"><span data-stu-id="869da-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="869da-111">Gdy liczniki wydajności są włączone, cały zestaw liczników wydajności WCF jest włączona dla usługi.</span><span class="sxs-lookup"><span data-stu-id="869da-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="869da-112">Program .NET Framework automatycznie przechowuje dane `ServiceModelService`o `ServiceModelEndpoint` `ServiceModelOperation`wydajności na trzech poziomach: , i .</span><span class="sxs-lookup"><span data-stu-id="869da-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="869da-113">Każdy z tych poziomów ma liczniki wydajności, takie jak "Połączenia", "Połączenia na sekundę" i "Połączenia zabezpieczeń nie autoryzowane".</span><span class="sxs-lookup"><span data-stu-id="869da-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="869da-114">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="869da-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="869da-115">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="869da-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="869da-116">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="869da-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="869da-117">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="869da-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="869da-118">Aby wyświetlić dane dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="869da-118">To view performance data</span></span>  
  
1. <span data-ttu-id="869da-119">Uruchom narzędzie Monitor wydajności, **Start**klikając przycisk Start `perfmon` , **Uruchom...**, wprowadź i kliknij przycisk **OK** lub w Panelu sterowania, wybierz pozycję **Narzędzia administracyjne** i kliknij dwukrotnie pozycję **Wydajność**.</span><span class="sxs-lookup"><span data-stu-id="869da-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="869da-120">Nie można dodać liczników, dopóki przykładowy kod nie jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="869da-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="869da-121">Usuń liczniki wydajności, które są wymienione, zaznaczając je i naciskając klawisz Delete.</span><span class="sxs-lookup"><span data-stu-id="869da-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="869da-122">Dodaj liczniki WCF, klikając prawym przyciskiem myszy okienko wykresu i wybierając pozycję **Dodaj liczniki**.</span><span class="sxs-lookup"><span data-stu-id="869da-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="869da-123">W oknie dialogowym **Dodawanie liczników** wybierz pozycję **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 lub ServiceModelService 3.0.0.0** w polu listy rozwijanej obiektu Wydajność.</span><span class="sxs-lookup"><span data-stu-id="869da-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="869da-124">Wybierz liczniki, które chcesz wyświetlić z listy.</span><span class="sxs-lookup"><span data-stu-id="869da-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="869da-125">Nie ma żadnych liczników wydajności WCF dla usługi, jeśli na komputerze nie ma żadnych usług WCF.</span><span class="sxs-lookup"><span data-stu-id="869da-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="869da-126">Aby włączyć liczniki za pomocą Edytora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="869da-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="869da-127">Otwórz wystąpienie pliku SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="869da-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="869da-128">W menu Plik kliknij polecenie **Otwórz,** a następnie kliknij polecenie **Plik konfiguracyjny...**.</span><span class="sxs-lookup"><span data-stu-id="869da-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="869da-129">Przejdź do przykładowego folderu usługi aplikacji i otwórz plik Web.config.</span><span class="sxs-lookup"><span data-stu-id="869da-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="869da-130">Kliknij **pozycję Diagnostyka** w drzewie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="869da-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="869da-131">Przełącz **licznik wydajności** w oknie **Diagnostyka,** aby wyświetlić "Wszystko".</span><span class="sxs-lookup"><span data-stu-id="869da-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="869da-132">Zapisz plik konfiguracyjny i zamknij edytor.</span><span class="sxs-lookup"><span data-stu-id="869da-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="869da-133">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="869da-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="869da-134">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="869da-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="869da-135">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="869da-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="869da-136">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="869da-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="869da-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="869da-137">See also</span></span>

- <span data-ttu-id="869da-138">[Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="869da-138">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
