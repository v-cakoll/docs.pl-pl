---
title: "Używanie liczników wydajności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef5a499e6d940e45e0c9aab093b0a1c00bb6cc32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-performance-counters"></a><span data-ttu-id="a58ca-102">Używanie liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="a58ca-102">Using Performance Counters</span></span>
<span data-ttu-id="a58ca-103">W tym przykładzie przedstawiono sposób uzyskiwania dostępu do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] liczniki wydajności oraz sposobu tworzenia liczników wydajności zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a58ca-103">This sample demonstrates how to access [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="a58ca-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a58ca-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a58ca-105">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a58ca-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a58ca-106">W tym przykładzie klient wywołuje metody cztery `ICalculator` usługi.</span><span class="sxs-lookup"><span data-stu-id="a58ca-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="a58ca-107">Klient w dalszym ciągu to zrobić, dopóki nie zostanie przerwane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a58ca-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="a58ca-108">Usługa pozostanie bez zmian.</span><span class="sxs-lookup"><span data-stu-id="a58ca-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="a58ca-109">Liczniki wydajności są włączone w sekcji Diagnostyka pliku Web.config dla usługi, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="a58ca-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="a58ca-110">To zadanie można również wykonać za pomocą [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a58ca-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="a58ca-111">Jeśli liczniki wydajności są włączone, cały zestaw [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liczniki wydajności są włączone dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a58ca-111">When performance counters are enabled, the entire suite of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters is enabled for the service.</span></span> <span data-ttu-id="a58ca-112">.NET Framework automatycznie przechowuje dane dotyczące wydajności na trzech poziomach: `ServiceModelService`, `ServiceModelEndpoint` i `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="a58ca-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="a58ca-113">Każda z tych poziomów ma liczniki wydajności, takich jak "Wywołania", "Wywołania na sekundę" i "Zabezpieczenia wywołania nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="a58ca-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a58ca-114">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="a58ca-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a58ca-115">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a58ca-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a58ca-116">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a58ca-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a58ca-117">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a58ca-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="a58ca-118">Aby wyświetlić dane wydajności</span><span class="sxs-lookup"><span data-stu-id="a58ca-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="a58ca-119">Uruchom narzędzie monitora wydajności, klikając **Start**, **Uruchom...** , wprowadź `perfmon` i kliknij przycisk **OK** lub z poziomu Panelu sterowania, wybierz **narzędzia administracyjne** i kliknij dwukrotnie **wydajności**.</span><span class="sxs-lookup"><span data-stu-id="a58ca-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a58ca-120">Nie można dodać liczniki, dopóki nie zostanie uruchomiony w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a58ca-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="a58ca-121">Usuń liczniki wydajności, które są wyświetlane, zaznaczając je i naciskając klawisz Delete.</span><span class="sxs-lookup"><span data-stu-id="a58ca-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="a58ca-122">Dodaj [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liczniki prawym przyciskiem myszy okienko Wykres i wybierając **Dodaj liczniki**.</span><span class="sxs-lookup"><span data-stu-id="a58ca-122">Add [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="a58ca-123">W **Dodaj liczniki** okno dialogowe, wybierz opcję **ServiceModelOperation 3.0.0.0 ServiceModelEndpoint 3.0.0.0 i ServiceModelService 3.0.0.0** w obiekcie wydajności listy rozwijanej pola listy.</span><span class="sxs-lookup"><span data-stu-id="a58ca-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="a58ca-124">Wybierz liczniki, które mają być wyświetlane na liście.</span><span class="sxs-lookup"><span data-stu-id="a58ca-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a58ca-125">Istnieją nie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liczniki wydajności dla usługi, jeśli istnieją nie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi działające na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a58ca-125">There are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters for a service if there are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="a58ca-126">Aby włączyć liczniki za pomocą edytora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a58ca-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="a58ca-127">Otwórz wystąpienie SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="a58ca-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="a58ca-128">W menu Plik kliknij polecenie **Otwórz** , a następnie kliknij przycisk **pliku konfiguracji...** .</span><span class="sxs-lookup"><span data-stu-id="a58ca-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="a58ca-129">Przejdź do folderu usługi przykładowej aplikacji, a następnie otwórz plik Web.config.</span><span class="sxs-lookup"><span data-stu-id="a58ca-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="a58ca-130">Kliknij przycisk **diagnostyki** na drzewie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a58ca-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="a58ca-131">Przełącz **licznika wydajności** w **diagnostyki** okno, aby wyświetlić "All".</span><span class="sxs-lookup"><span data-stu-id="a58ca-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="a58ca-132">Zapisz plik konfiguracji i zamknij Edytor.</span><span class="sxs-lookup"><span data-stu-id="a58ca-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a58ca-133">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a58ca-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a58ca-134">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a58ca-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a58ca-135">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a58ca-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a58ca-136">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a58ca-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="a58ca-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a58ca-137">See Also</span></span>  
 [<span data-ttu-id="a58ca-138">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="a58ca-138">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
