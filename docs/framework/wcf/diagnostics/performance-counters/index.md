---
title: Liczniki wydajności programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: d0ad7ee0bc3ea1d15197e6b8d9888d60b21a2f15
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867202"
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="8afc6-102">Liczniki wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="8afc6-102">WCF Performance Counters</span></span>
<span data-ttu-id="8afc6-103">Windows Communication Foundation (WCF) zawiera duży zestaw liczników wydajności, aby ułatwić mierzyć wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8afc6-103">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="8afc6-104">Włączanie liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="8afc6-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="8afc6-105">Liczniki wydajności dla usługi WCF można włączyć za pomocą pliku konfiguracji app.config usługi WCF w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8afc6-105">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="8afc6-106">`performanceCounters` Atrybut można ustawić tak, aby włączyć liczniki wydajności dla określonego typu.</span><span class="sxs-lookup"><span data-stu-id="8afc6-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="8afc6-107">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="8afc6-107">Valid values are</span></span>  
  
-   <span data-ttu-id="8afc6-108">Wszystko: Wszystkie liczniki kategorii (ServiceModelService i ServiceModelEndpoint ServiceModelOperation) są włączone.</span><span class="sxs-lookup"><span data-stu-id="8afc6-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
-   <span data-ttu-id="8afc6-109">ServiceOnly: Tylko ServiceModelService kategorii liczników są włączone.</span><span class="sxs-lookup"><span data-stu-id="8afc6-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="8afc6-110">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="8afc6-110">This is the default value.</span></span>  
  
-   <span data-ttu-id="8afc6-111">Wyłączony: ServiceModel \*, liczniki wydajności są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8afc6-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="8afc6-112">Jeśli chcesz włączyć liczniki wydajności dla wszystkich aplikacji WCF, ustawienia konfiguracji można umieścić w pliku Machine.config.</span><span class="sxs-lookup"><span data-stu-id="8afc6-112">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="8afc6-113">Zobacz **zwiększenie rozmiaru pamięci dla liczników wydajności** sekcji poniżej, aby uzyskać więcej informacji na temat konfigurowania wystarczającą ilość pamięci dla liczników wydajności na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8afc6-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="8afc6-114">Jeśli używasz usługi WCF punkty rozszerzeń, takich jak invokers operacji niestandardowej, powinny również wysyłać liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="8afc6-114">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="8afc6-115">Jest to spowodowane w przypadku zaimplementowania punktu rozszerzalności WCF, mogą nie są już emitowane dane licznika wydajności warstwy standardowa w domyślnej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8afc6-115">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="8afc6-116">Jeśli obsługa licznika wydajności ręczne nie jest zaimplementowane, może być niewidoczna dane licznika wydajności, których oczekujesz.</span><span class="sxs-lookup"><span data-stu-id="8afc6-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="8afc6-117">Można również włączyć liczniki wydajności w kodzie w następujący sposób,</span><span class="sxs-lookup"><span data-stu-id="8afc6-117">You can also enable performance counters in your code as follows,</span></span>  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="8afc6-118">Wyświetlanie danych wydajności</span><span class="sxs-lookup"><span data-stu-id="8afc6-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="8afc6-119">Aby wyświetlić dane przechwycone przez liczniki wydajności, można użyć Monitora wydajności (Perfmon.exe), który jest dostarczany z Windows.</span><span class="sxs-lookup"><span data-stu-id="8afc6-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="8afc6-120">Możesz uruchomić to narzędzie, przechodząc do **Start**i kliknij przycisk **Uruchom** i typ `perfmon.exe` w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="8afc6-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8afc6-121">Wystąpienia liczników wydajności mogą zostać zwolnione, zanim ostatnie komunikaty są przetwarzane przez dyspozytora punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8afc6-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="8afc6-122">Może to spowodować, że dane wydajności nie przechwycone kilka komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8afc6-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="8afc6-123">Zwiększenie rozmiaru pamięci dla liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="8afc6-123">Increasing Memory Size for Performance Counters</span></span>  
 <span data-ttu-id="8afc6-124">Usługi WCF używa oddzielnych pamięci współużytkowanej dla jego kategorii licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="8afc6-124">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="8afc6-125">Domyślnie oddzielne Pamięć współużytkowana jest równa kwartału ogólnych parametrów liczników pamięci.</span><span class="sxs-lookup"><span data-stu-id="8afc6-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="8afc6-126">Domyślny ogólnych parametrów liczników pamięci to 524,288 bajtów.</span><span class="sxs-lookup"><span data-stu-id="8afc6-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="8afc6-127">Trzy kategorie liczników wydajności programu WCF więc domyślny rozmiar około 128KB.</span><span class="sxs-lookup"><span data-stu-id="8afc6-127">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="8afc6-128">W zależności od charakterystyki środowiska uruchomieniowego aplikacji WCF na komputerze, mogą się wyczerpać pamięci licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="8afc6-128">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="8afc6-129">W takim przypadku WCF zapisuje błąd w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8afc6-129">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="8afc6-130">Zawartość błąd stwierdza, że licznika wydajności, który nie został załadowany, a wpis zawiera wyjątek "System.InvalidOperationException: za mało pamięci dla widoku pliku liczników niestandardowych."</span><span class="sxs-lookup"><span data-stu-id="8afc6-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="8afc6-131">Jeśli śledzenie jest włączone na poziomie błędu, śledzona jest również tego błędu.</span><span class="sxs-lookup"><span data-stu-id="8afc6-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="8afc6-132">Jeśli wyczerpaniu pamięci licznika wydajności w dalszym ciągu uruchamiać aplikacje programu WCF za pomocą liczników wydajności, włączone może spowodować obniżenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="8afc6-132">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="8afc6-133">Jeśli jesteś administratorem na komputerze, należy skonfigurować ją przydzielić wystarczającej ilości pamięci do obsługi maksymalną liczbę liczników wydajności, które może znajdować się w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="8afc6-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="8afc6-134">Można zmienić ilość pamięci licznika wydajności dla kategorii WCF w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="8afc6-134">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="8afc6-135">Aby to zrobić, należy dodać nową wartość DWORD o nazwie `FileMappingSize` do trzech następujących lokalizacji i ustaw ją na żądaną wartość w bajtach.</span><span class="sxs-lookup"><span data-stu-id="8afc6-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="8afc6-136">Tak, aby te zmiany są wykonywane w życie, należy ponownie uruchomić maszynę.</span><span class="sxs-lookup"><span data-stu-id="8afc6-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
-   <span data-ttu-id="8afc6-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="8afc6-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="8afc6-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="8afc6-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="8afc6-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="8afc6-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="8afc6-140">Gdy dużą liczbę obiektów (na przykład ServiceHost) będą usuwane, ale oczekujące na zebranych elementów bezużytecznych `PrivateBytes` licznika wydajności będą rejestrować się wyjątkowo dużą liczbą.</span><span class="sxs-lookup"><span data-stu-id="8afc6-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="8afc6-141">Aby rozwiązać ten problem, możesz dodać własne liczniki specyficzne dla aplikacji, lub użyj `performanceCounters` atrybutu, aby włączyć liczniki tylko poziomu usługi.</span><span class="sxs-lookup"><span data-stu-id="8afc6-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="8afc6-142">Typy liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="8afc6-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="8afc6-143">Liczniki wydajności są ograniczone do trzech różnych poziomach: usługi, punkt końcowy i operacji.</span><span class="sxs-lookup"><span data-stu-id="8afc6-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="8afc6-144">WMI umożliwia pobieranie nazwy wystąpienia licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="8afc6-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="8afc6-145">Na przykład</span><span class="sxs-lookup"><span data-stu-id="8afc6-145">For example,</span></span>  
  
-   <span data-ttu-id="8afc6-146">Nazwa wystąpienia licznika usługi można uzyskać za pomocą usługi WMI [usługi](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) właściwość "CounterInstanceName" instancji.</span><span class="sxs-lookup"><span data-stu-id="8afc6-146">Service counter instance name can be obtained through WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="8afc6-147">Nazwa wystąpienia licznika punktu końcowego można uzyskać za pomocą usługi WMI [punktu końcowego](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) właściwość "CounterInstanceName" instancji.</span><span class="sxs-lookup"><span data-stu-id="8afc6-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="8afc6-148">Nazwa wystąpienia licznika operacji można uzyskać za pomocą usługi WMI [punktu końcowego](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) metodę "GetOperationCounterInstanceName" instancji.</span><span class="sxs-lookup"><span data-stu-id="8afc6-148">Operation counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="8afc6-149">Aby uzyskać więcej informacji na temat usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="8afc6-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="8afc6-150">Liczniki wydajności usługi</span><span class="sxs-lookup"><span data-stu-id="8afc6-150">Service performance counters</span></span>  
 <span data-ttu-id="8afc6-151">Liczniki wydajności usługi zmierzyć zachowanie usługi jako całość i może służyć do diagnozowania wydajności całą usługę.</span><span class="sxs-lookup"><span data-stu-id="8afc6-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="8afc6-152">Można go znaleźć w `ServiceModelService 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="8afc6-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="8afc6-153">Wystąpienia są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="8afc6-153">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 <span data-ttu-id="8afc6-154">Licznik w zakresie usługi jest agregowana od licznika w kolekcji punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8afc6-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="8afc6-155">Liczniki wydajności do tworzenia wystąpienia usług są zwiększane, gdy zostanie utworzony nowy obiekt InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="8afc6-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="8afc6-156">Należy pamiętać o tym, czy nowy obiekt InstanceContext został utworzony, nawet gdy — Aktywacja komunikat o błędzie (z istniejącą usługę) lub podczas nawiązywania połączenia z wystąpieniem z jednej sesji, zakończyć sesję i ponownego połączenia z innej sesji.</span><span class="sxs-lookup"><span data-stu-id="8afc6-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="8afc6-157">Liczniki wydajności w punkcie końcowym</span><span class="sxs-lookup"><span data-stu-id="8afc6-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="8afc6-158">Liczniki wydajności w punkcie końcowym umożliwiają wyszukiwanie danych w czasie wykonywania odbicia, jak punkt końcowy jest akceptowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8afc6-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="8afc6-159">Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności podczas przeglądania, korzystanie z Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="8afc6-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="8afc6-160">Wystąpienia są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="8afc6-160">The instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="8afc6-161">Dane są podobne do są zbierane dla poszczególnych działań, ale tylko jest agregowana dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8afc6-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="8afc6-162">Licznik w zakresie punktu końcowego są agregowane z liczników w to kolekcja operacji.</span><span class="sxs-lookup"><span data-stu-id="8afc6-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8afc6-163">Jeśli dwa punkty końcowe mają identyczne nazwy i adresy, są mapowane do tego samego wystąpienia licznika.</span><span class="sxs-lookup"><span data-stu-id="8afc6-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="8afc6-164">Liczniki wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="8afc6-164">Operation performance counters</span></span>  
 <span data-ttu-id="8afc6-165">Liczniki wydajności operacji znajdują się w obszarze `ServiceModelOperation 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="8afc6-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="8afc6-166">Każda operacja ma poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="8afc6-166">Each operation has an individual instance.</span></span> <span data-ttu-id="8afc6-167">Oznacza to jeśli danego kontraktu operacje 10, 10 wystąpień licznika operacji skojarzonych z tej Umowy.</span><span class="sxs-lookup"><span data-stu-id="8afc6-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="8afc6-168">Wystąpienia obiektu są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="8afc6-168">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="8afc6-169">Ten licznik umożliwia pomiar sposobu używania wywołania i jak dobrze działa operacja.</span><span class="sxs-lookup"><span data-stu-id="8afc6-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="8afc6-170">Liczniki są widoczne w wielu zakresach, danych zebranych z wyższym zakresie są agregowane z danymi z niższe zakresy.</span><span class="sxs-lookup"><span data-stu-id="8afc6-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="8afc6-171">Na przykład `Calls` w punkcie końcowym reprezentuje sumę wszystkich wywołań operacji w ramach punktu końcowego; `Calls` powinna być usługa reprezentuje sumę wszystkich wywołań do wszystkich punktów końcowych w ramach usługi.</span><span class="sxs-lookup"><span data-stu-id="8afc6-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8afc6-172">Jeśli masz nazwy zduplikowanych operacji na kontrakt, tylko otrzymasz jednego wystąpienia liczników dla obu operacji.</span><span class="sxs-lookup"><span data-stu-id="8afc6-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="8afc6-173">Programowanie liczniki wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="8afc6-173">Programming the WCF Performance Counters</span></span>  
 <span data-ttu-id="8afc6-174">Kilka plików są instalowane w folderze instalacji zestawu SDK, tak aby programowy dostęp liczniki wydajności programu WCF.</span><span class="sxs-lookup"><span data-stu-id="8afc6-174">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="8afc6-175">Te pliki są wymienione w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="8afc6-175">These files are listed as follows.</span></span>  
  
-   <span data-ttu-id="8afc6-176">_ServiceModelEndpointPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="8afc6-176">_ServiceModelEndpointPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="8afc6-177">_ServiceModelOperationPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="8afc6-177">_ServiceModelOperationPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="8afc6-178">_ServiceModelServicePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="8afc6-178">_ServiceModelServicePerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="8afc6-179">_SMSvcHostPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="8afc6-179">_SMSvcHostPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="8afc6-180">_TransactionBridgePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="8afc6-180">_TransactionBridgePerfCounters.vrg</span></span>  
  
 <span data-ttu-id="8afc6-181">Aby uzyskać więcej informacji na temat sposobu programowego dostępu do liczników, zobacz [Architektura programowania licznika wydajności](https://go.microsoft.com/fwlink/?LinkId=95179).</span><span class="sxs-lookup"><span data-stu-id="8afc6-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](https://go.microsoft.com/fwlink/?LinkId=95179).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8afc6-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8afc6-182">See Also</span></span>  
 [<span data-ttu-id="8afc6-183">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="8afc6-183">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
