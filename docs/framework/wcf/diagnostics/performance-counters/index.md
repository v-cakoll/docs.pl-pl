---
title: Liczniki wydajności programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 73bb02379308fbfe507137e61ac8d84e6b9760b4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395892"
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="a4ec2-102">Liczniki wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="a4ec2-102">WCF Performance Counters</span></span>
<span data-ttu-id="a4ec2-103">Windows Communication Foundation (WCF) zawiera duży zestaw liczników wydajności, które ułatwiają pomiar wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-103">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="a4ec2-104">Włączanie liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="a4ec2-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="a4ec2-105">Liczniki wydajności dla usługi WCF można włączyć za pomocą pliku konfiguracji App. config usługi WCF w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a4ec2-105">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="a4ec2-106">Atrybut `performanceCounters` można ustawić, aby włączyć określony typ liczników wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="a4ec2-107">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="a4ec2-107">Valid values are</span></span>  
  
- <span data-ttu-id="a4ec2-108">Wszystko: wszystkie liczniki kategorii (ServiceModelService, ServiceModelEndpoint i ServiceModelOperation) są włączone.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
- <span data-ttu-id="a4ec2-109">Tylko ServiceOnly: włączone są tylko liczniki kategorii ServiceModelService.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="a4ec2-110">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-110">This is the default value.</span></span>  
  
- <span data-ttu-id="a4ec2-111">Wyłączone: ServiceModel \* liczniki wydajności są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="a4ec2-112">Jeśli chcesz włączyć liczniki wydajności dla wszystkich aplikacji WCF, możesz umieścić ustawienia konfiguracji w pliku Machine. config.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-112">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="a4ec2-113">Więcej informacji na temat konfigurowania wystarczającej ilości pamięci dla liczników wydajności na komputerze znajduje się w sekcji **zwiększanie rozmiaru pamięci dla liczników wydajności** .</span><span class="sxs-lookup"><span data-stu-id="a4ec2-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="a4ec2-114">W przypadku używania punktów rozszerzalności WCF, takich jak niestandardowe wywołania operacji, należy również emitować własne liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-114">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="a4ec2-115">Wynika to z faktu, że w przypadku zaimplementowania punktu rozszerzalności usługa WCF nie będzie już emitować standardowych danych licznika wydajności w ścieżce domyślnej.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-115">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="a4ec2-116">Jeśli nie zostanie wdrożona ręczna obsługa licznika wydajności, może nie być widoczne oczekiwane dane licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="a4ec2-117">Liczniki wydajności można również włączyć w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a4ec2-117">You can also enable performance counters in your code as follows,</span></span>  
  
```csharp
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="a4ec2-118">Wyświetlanie danych wydajności</span><span class="sxs-lookup"><span data-stu-id="a4ec2-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="a4ec2-119">Aby wyświetlić dane przechwycone przez liczniki wydajności, można użyć Monitora wydajności (Perfmon. exe), który jest dostarczany z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="a4ec2-120">Można uruchomić to narzędzie, przechodząc do **menu Start**, a następnie klikając polecenie **uruchom** i wpisz `perfmon.exe` w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4ec2-121">Wystąpienia licznika wydajności mogą zostać wydane przed przetworzeniem ostatnich komunikatów przez dyspozytora punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="a4ec2-122">Może to spowodować, że dane wydajności nie zostaną przechwycone przez kilka komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="a4ec2-123">Zwiększanie rozmiaru pamięci dla liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="a4ec2-123">Increasing Memory Size for Performance Counters</span></span>  
 <span data-ttu-id="a4ec2-124">Usługa WCF używa oddzielnej pamięci współdzielonej dla jej kategorii liczników wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-124">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="a4ec2-125">Domyślnie dla oddzielnej pamięci współdzielonej jest ustawiony kwartał rozmiaru globalnej pamięci licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="a4ec2-126">Domyślna globalna pamięć licznika wydajności to 524 288 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="a4ec2-127">W związku z tym trzy kategorie liczników wydajności programu WCF mają domyślny rozmiar około 128 KB każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-127">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="a4ec2-128">W zależności od charakterystyk środowiska uruchomieniowego aplikacji WCF na komputerze można wyczerpaniu pamięci licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-128">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="a4ec2-129">W takim przypadku usługa WCF zapisuje błąd w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-129">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="a4ec2-130">Zawartość błędów wskazuje, że licznik wydajności nie został załadowany, a wpis zawiera wyjątek "System. InvalidOperationException: niestandardowy widok pliku liczników ma za mało pamięci".</span><span class="sxs-lookup"><span data-stu-id="a4ec2-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="a4ec2-131">Jeśli śledzenie jest włączone na poziomie błędu, ten błąd jest również śledzony.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="a4ec2-132">W przypadku wyczerpania pamięci licznika wydajności kontynuowanie uruchamiania aplikacji programu WCF z włączonymi licznikami wydajności może skutkować obniżeniem wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-132">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="a4ec2-133">Jeśli jesteś administratorem maszyny, skonfiguruj ją w celu przydzielenia wystarczającej ilości pamięci, aby obsługiwać maksymalną liczbę liczników wydajności, które mogą istnieć w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="a4ec2-134">Można zmienić ilość pamięci licznika wydajności dla kategorii WCF w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-134">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="a4ec2-135">Aby to zrobić, należy dodać nową wartość DWORD o nazwie `FileMappingSize` do trzech następujących lokalizacji i ustawić ją na żądaną wartość w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="a4ec2-136">Uruchom ponownie maszynę, aby zmiany zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
- <span data-ttu-id="a4ec2-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0 \ wydajność</span><span class="sxs-lookup"><span data-stu-id="a4ec2-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="a4ec2-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0 \ wydajność</span><span class="sxs-lookup"><span data-stu-id="a4ec2-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="a4ec2-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0 \ wydajność</span><span class="sxs-lookup"><span data-stu-id="a4ec2-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="a4ec2-140">W przypadku usunięcia dużej liczby obiektów (na przykład ServiceHost), ale oczekujących na odtworzenie elementów bezużytecznych, licznik wydajności `PrivateBytes` będzie rejestrował nietypowo dużą liczbę.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="a4ec2-141">Aby rozwiązać ten problem, można dodać własne liczniki specyficzne dla aplikacji lub użyć atrybutu `performanceCounters` w celu włączenia tylko liczników poziomu usługi.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="a4ec2-142">Typy liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="a4ec2-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="a4ec2-143">Liczniki wydajności są objęte zakresem trzech różnych poziomów: usługi, punktu końcowego i operacji.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="a4ec2-144">Za pomocą usługi WMI można pobrać nazwę wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="a4ec2-145">Na przykład</span><span class="sxs-lookup"><span data-stu-id="a4ec2-145">For example,</span></span>  
  
- <span data-ttu-id="a4ec2-146">Nazwę wystąpienia licznika usługi można uzyskać za pomocą właściwości "CounterInstanceName" wystąpienia [usługi](../wmi/service.md) WMI.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-146">Service counter instance name can be obtained through WMI [Service](../wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="a4ec2-147">Nazwę wystąpienia licznika punktu końcowego można uzyskać za pomocą właściwości "CounterInstanceName" wystąpienia [punktu końcowego](../wmi/endpoint.md) usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="a4ec2-148">Nazwę wystąpienia licznika operacji można uzyskać za pomocą metody "GetOperationCounterInstanceName" wystąpienia [punktu końcowego](../wmi/endpoint.md) usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-148">Operation counter instance name can be obtained through WMI [Endpoint](../wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="a4ec2-149">Aby uzyskać więcej informacji na temat usługi WMI, zobacz [używanie Instrumentacja zarządzania Windows do diagnostyki](../wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="a4ec2-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="a4ec2-150">Liczniki wydajności usługi</span><span class="sxs-lookup"><span data-stu-id="a4ec2-150">Service performance counters</span></span>  
 <span data-ttu-id="a4ec2-151">Liczniki wydajności usługi mierzą zachowanie usługi jako całość i mogą służyć do diagnozowania wydajności całej usługi.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="a4ec2-152">Można je znaleźć w obiekcie wydajności `ServiceModelService 4.0.0.0` podczas wyświetlania z monitorem wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="a4ec2-153">Wystąpienia są nazwane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="a4ec2-153">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
 <span data-ttu-id="a4ec2-154">Licznik w zakresie usługi jest agregowany z licznika w kolekcji punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="a4ec2-155">Liczniki wydajności dla tworzenia wystąpień usług są zwiększane, gdy tworzony jest nowy obiekt InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="a4ec2-156">Należy pamiętać, że tworzony jest nowy element InstanceContext, nawet jeśli otrzymujesz komunikat Nieaktywowany (z istniejącą usługą) lub po nawiązaniu połączenia z wystąpieniem z jednej sesji, zakończyć sesję, a następnie ponownie nawiązać połączenie z innej sesji.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="a4ec2-157">Liczniki wydajności punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="a4ec2-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="a4ec2-158">Liczniki wydajności punktu końcowego umożliwiają przeglądanie danych odzwierciedlających, w jaki sposób punkt końcowy akceptuje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="a4ec2-159">Można je znaleźć w obiekcie wydajności `ServiceModelEndpoint 4.0.0.0` podczas wyświetlania przy użyciu Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="a4ec2-160">Wystąpienia są nazwane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="a4ec2-160">The instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`
  
 <span data-ttu-id="a4ec2-161">Dane są podobne do tego, co jest zbierane dla poszczególnych operacji, ale są agregowane w całym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="a4ec2-162">Licznik w zakresie punktu końcowego jest agregowany z liczników w kolekcji operacji.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4ec2-163">Jeśli dwa punkty końcowe mają identyczne nazwy i adresy kontraktu, są mapowane na to samo wystąpienie licznika.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="a4ec2-164">Liczniki wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="a4ec2-164">Operation performance counters</span></span>  
 <span data-ttu-id="a4ec2-165">Liczniki wydajności operacji są dostępne pod obiektem wydajności `ServiceModelOperation 4.0.0.0` podczas wyświetlania z monitorem wydajności.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="a4ec2-166">Każda operacja ma pojedyncze wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-166">Each operation has an individual instance.</span></span> <span data-ttu-id="a4ec2-167">Oznacza to, że jeśli dany kontrakt zawiera 10 operacji, do tego kontraktu są skojarzone 10 wystąpień liczników operacji.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="a4ec2-168">Wystąpienia obiektów są nazwane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="a4ec2-168">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="a4ec2-169">Ten licznik umożliwia pomiar sposobu użycia wywołania oraz sposobu wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="a4ec2-170">Gdy liczniki są widoczne w wielu zakresach, dane zbierane z wyższego zakresu są agregowane przy użyciu danych z niższych zakresów.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="a4ec2-171">Na przykład `Calls` w punkcie końcowym reprezentuje sumę wszystkich wywołań operacji w punkcie końcowym; `Calls` w ramach usługi reprezentuje sumę wszystkich wywołań wszystkich punktów końcowych w ramach usługi.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4ec2-172">Jeśli na kontrakcie istnieją zduplikowane nazwy operacji, tylko jeden z nich jest odbierany dla obu operacji.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="a4ec2-173">Programowanie liczników wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="a4ec2-173">Programming the WCF Performance Counters</span></span>  

<span data-ttu-id="a4ec2-174">Kilka plików jest zainstalowanych w folderze instalacyjnym zestawu SDK, dzięki czemu można programowo uzyskać dostęp do liczników wydajności programu WCF.</span><span class="sxs-lookup"><span data-stu-id="a4ec2-174">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="a4ec2-175">Te pliki są wymienione w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a4ec2-175">These files are listed as follows:</span></span>
  
- <span data-ttu-id="a4ec2-176">*@no__t -1ServiceModelEndpointPerfCounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="a4ec2-176">*\_ServiceModelEndpointPerfCounters.vrg*</span></span>
- <span data-ttu-id="a4ec2-177">*@no__t -1ServiceModelOperationPerfCounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="a4ec2-177">*\_ServiceModelOperationPerfCounters.vrg*</span></span>
- <span data-ttu-id="a4ec2-178">*@no__t -1ServiceModelServicePerfCounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="a4ec2-178">*\_ServiceModelServicePerfCounters.vrg*</span></span>  
- <span data-ttu-id="a4ec2-179">*@no__t -1SMSvcHostPerfCounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="a4ec2-179">*\_SMSvcHostPerfCounters.vrg*</span></span>
- <span data-ttu-id="a4ec2-180">*@no__t -1TransactionBridgePerfCounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="a4ec2-180">*\_TransactionBridgePerfCounters.vrg*</span></span>
  
<span data-ttu-id="a4ec2-181">Aby uzyskać więcej informacji na temat programistycznego uzyskiwania dostępu do liczników, zobacz [Architektura programowania liczników wydajności](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a4ec2-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a4ec2-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4ec2-182">See also</span></span>

- [<span data-ttu-id="a4ec2-183">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="a4ec2-183">Administration and Diagnostics</span></span>](../index.md)
