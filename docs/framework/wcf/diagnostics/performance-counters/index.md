---
title: "Liczniki wydajności programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
caps.latest.revision: "37"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2136b4f9ab97f7ed0e4c31e6ffc26f788546419b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="17791-102">Liczniki wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="17791-102">WCF Performance Counters</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="17791-103">zawiera duży zbiór liczników wydajności, aby ocenić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17791-103"> includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="17791-104">Włączanie liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="17791-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="17791-105">Można włączyć liczniki wydajności dla [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] za pośrednictwem pliku konfiguracyjnego app.config [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="17791-105">You can enable performance counters for a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service through the app.config configuration file of the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="17791-106">`performanceCounters` Atrybut można określać, aby włączyć liczniki wydajności dla określonego typu.</span><span class="sxs-lookup"><span data-stu-id="17791-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="17791-107">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="17791-107">Valid values are</span></span>  
  
-   <span data-ttu-id="17791-108">Wszystko: Wszystkie liczniki kategorii (ServiceModelService, ServiceModelEndpoint i ServiceModelOperation) są włączone.</span><span class="sxs-lookup"><span data-stu-id="17791-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
-   <span data-ttu-id="17791-109">ServiceOnly: Tylko ServiceModelService kategorii liczników są włączone.</span><span class="sxs-lookup"><span data-stu-id="17791-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="17791-110">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="17791-110">This is the default value.</span></span>  
  
-   <span data-ttu-id="17791-111">Wyłączone: Liczniki wydajności modelu ServiceModel * są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="17791-111">Off: ServiceModel* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="17791-112">Jeśli chcesz włączyć liczniki wydajności dla wszystkich [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikacje, ustawienia konfiguracji można umieścić w pliku Machine.config.</span><span class="sxs-lookup"><span data-stu-id="17791-112">If you want to enable performance counters for all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="17791-113">Zobacz **zwiększyć rozmiar pamięci dla liczników wydajności** sekcji poniżej, aby uzyskać więcej informacji na temat konfigurowania wystarczającą ilość pamięci dla liczników wydajności na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="17791-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="17791-114">Jeśli używasz [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] punktów rozszerzalności takich jak invokers operacja niestandardowa możesz powinny również Emituj liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="17791-114">If you use [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="17791-115">To dlatego, jeśli implementuje punkt rozszerzeń [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] może już nie Emituj danych licznika wydajności standardowe w domyślnej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="17791-115">This is because if you implement an extensibility point, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="17791-116">Jeśli nie implementuje obsługi licznika wydajności ręczne, nie zobaczysz oczekiwane dane licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="17791-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="17791-117">Można również włączyć liczniki wydajności kod w następujący sposób</span><span class="sxs-lookup"><span data-stu-id="17791-117">You can also enable performance counters in your code as follows,</span></span>  
  
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
  
## <a name="viewing-performance-data"></a><span data-ttu-id="17791-118">Wyświetlanie danych wydajności</span><span class="sxs-lookup"><span data-stu-id="17791-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="17791-119">Aby wyświetlić dane przechwycone przez liczniki wydajności, można użyć Monitora wydajności (Perfmon.exe) dołączoną do systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="17791-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="17791-120">Możesz uruchomić to narzędzie, przechodząc do **Start**i kliknij przycisk **Uruchom** i typu `perfmon.exe` w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="17791-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17791-121">Wystąpienia liczników wydajności może zostać zwolniony przed ostatnim wiadomości są przetwarzane przez Dyspozytor punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="17791-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="17791-122">Może to spowodować danych wydajności nie przechwycone kilka komunikatów.</span><span class="sxs-lookup"><span data-stu-id="17791-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="17791-123">Zwiększyć rozmiar pamięci dla liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="17791-123">Increasing Memory Size for Performance Counters</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="17791-124">używa oddzielnych Pamięć współużytkowana dla jego kategorii licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="17791-124"> uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="17791-125">Domyślnie oddzielne pamięci współużytkowanej ustawiono kwartału rozmiar pamięci liczników wydajności globalnego.</span><span class="sxs-lookup"><span data-stu-id="17791-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="17791-126">Domyślna pamięć licznika wydajności globalnego jest 524,288 bajtów.</span><span class="sxs-lookup"><span data-stu-id="17791-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="17791-127">W związku z tym trzech [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kategorii licznika wydajności ma domyślny rozmiar około 128 KB.</span><span class="sxs-lookup"><span data-stu-id="17791-127">Therefore, the three [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="17791-128">W zależności od właściwości środowisko uruchomieniowe [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikacji na maszynie pamięci liczników wydajności mogą wyczerpane.</span><span class="sxs-lookup"><span data-stu-id="17791-128">Depending upon the runtime characteristics of the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="17791-129">W takim przypadku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zapisuje komunikat o błędzie w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17791-129">When this happens, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] writes an error to the application event log.</span></span> <span data-ttu-id="17791-130">Stany zawartości błędu nie można załadować licznika wydajności, czy wyjątek zawiera wpis "System.InvalidOperationException: za mało pamięci dla widoku pliku liczników niestandardowych."</span><span class="sxs-lookup"><span data-stu-id="17791-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="17791-131">Jeśli śledzenie jest włączone na poziomie błąd, ten błąd jest również śledzone.</span><span class="sxs-lookup"><span data-stu-id="17791-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="17791-132">Jeśli wyczerpaniu pamięci liczników wydajności nadal uruchamiany z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikacji za pomocą włączone liczniki wydajności może spowodować zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="17791-132">If performance counter memory is exhausted, continuing to run your [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="17791-133">Jeśli jesteś administratorem komputera, należy skonfigurować ją przydzielić wystarczającej ilości pamięci do obsługi maksymalnie liczniki wydajności, które może występować w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="17791-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="17791-134">Możesz zmienić ilość pamięci liczników wydajności dla [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kategorii w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="17791-134">You can change the amount of performance counter memory for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] categories in the registry.</span></span> <span data-ttu-id="17791-135">Aby to zrobić, należy dodać nową wartość DWORD o nazwie `FileMappingSize` do trzech następujących lokalizacji i ustaw ją na żądaną wartość w bajtach.</span><span class="sxs-lookup"><span data-stu-id="17791-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="17791-136">Ponowny rozruch komputera, aby te zmiany są brane pod efekt.</span><span class="sxs-lookup"><span data-stu-id="17791-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
-   <span data-ttu-id="17791-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="17791-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="17791-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="17791-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="17791-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="17791-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="17791-140">Gdy dużą liczbę obiektów (na przykład ServiceHost) są usuwane, ale oczekujących na przetworzenie zbierane pamięci `PrivateBytes` licznika wydajności zarejestruje wyjątkowo dużą liczbą.</span><span class="sxs-lookup"><span data-stu-id="17791-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="17791-141">Aby rozwiązać ten problem, użytkownik może dodać własne liczniki specyficzne dla aplikacji, albo użyj `performanceCounters` atrybutu, aby włączyć liczniki tylko poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="17791-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="17791-142">Typy liczników wydajności</span><span class="sxs-lookup"><span data-stu-id="17791-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="17791-143">Liczniki wydajności są ograniczone do trzech różnych poziomów: usługi, punkt końcowy i operację.</span><span class="sxs-lookup"><span data-stu-id="17791-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="17791-144">Aby pobrać nazwę wystąpienia licznika wydajności przy użyciu usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="17791-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="17791-145">Na przykład</span><span class="sxs-lookup"><span data-stu-id="17791-145">For example,</span></span>  
  
-   <span data-ttu-id="17791-146">Nazwa wystąpienia liczników usługi można uzyskać za pomocą usługi WMI [usługi](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) właściwość "CounterInstanceName" instancji.</span><span class="sxs-lookup"><span data-stu-id="17791-146">Service counter instance name can be obtained through WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="17791-147">Nazwa wystąpienia liczników punktu końcowego można uzyskać za pomocą usługi WMI [punktu końcowego](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) właściwość "CounterInstanceName" instancji.</span><span class="sxs-lookup"><span data-stu-id="17791-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="17791-148">Nazwa wystąpienia liczników operacji można otrzymać za pośrednictwem usługi WMI [punktu końcowego](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) wystąpienia metody "GetOperationCounterInstanceName".</span><span class="sxs-lookup"><span data-stu-id="17791-148">Operation counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="17791-149">Aby uzyskać więcej informacji dotyczących usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="17791-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="17791-150">Liczniki wydajności usługi</span><span class="sxs-lookup"><span data-stu-id="17791-150">Service performance counters</span></span>  
 <span data-ttu-id="17791-151">Liczniki wydajności usługi zmierzyć zachowanie usługi jako całość i może służyć do diagnozowania wydajność całej usługi.</span><span class="sxs-lookup"><span data-stu-id="17791-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="17791-152">Można go znaleźć w `ServiceModelService 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="17791-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="17791-153">Wystąpienia są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="17791-153">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 <span data-ttu-id="17791-154">Licznik w zakresie usługi są agregowane z licznika w kolekcji punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="17791-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="17791-155">Liczniki wydajności służące do tworzenia wystąpienia usługi jest zwiększany, gdy jest tworzony nowy obiekt InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="17791-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="17791-156">Należy pamiętać, że tworzony jest nowy obiekt InstanceContext nawet po otrzymaniu wiadomości aktywowanie (z istniejącą usługę) lub gdy możesz połączyć się z wystąpieniem, z jedną sesję, zakończyć sesję i ponownego połączenia z innej sesji.</span><span class="sxs-lookup"><span data-stu-id="17791-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="17791-157">Liczniki wydajności punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="17791-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="17791-158">Liczniki wydajności punktu końcowego umożliwiają wyszukiwanie danych w czasie wykonywania odbicia, jak punkt końcowy jest akceptowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="17791-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="17791-159">Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności w przypadku wyświetlania korzystanie z Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="17791-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="17791-160">Wystąpienia są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="17791-160">The instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="17791-161">Dane są podobne do czego są zbierane dla poszczególnych działań, ale tylko jest agregowana przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="17791-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="17791-162">Licznik w zakresie punktu końcowego są agregowane z liczników w to kolekcja operacji.</span><span class="sxs-lookup"><span data-stu-id="17791-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17791-163">Jeśli dwa punkty końcowe mają identyczne nazwy i adresy, są mapowane do tego samego wystąpienia licznika.</span><span class="sxs-lookup"><span data-stu-id="17791-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="17791-164">Liczniki wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="17791-164">Operation performance counters</span></span>  
 <span data-ttu-id="17791-165">Liczniki wydajności operacji znajdują się w obszarze `ServiceModelOperation 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności.</span><span class="sxs-lookup"><span data-stu-id="17791-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="17791-166">Każda operacja wymaga poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="17791-166">Each operation has an individual instance.</span></span> <span data-ttu-id="17791-167">Oznacza to jeśli dany kontrakt operacji 10, 10 wystąpień licznika operacji są skojarzone z tej Umowy.</span><span class="sxs-lookup"><span data-stu-id="17791-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="17791-168">Wystąpienia obiektu są nazywane przy użyciu następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="17791-168">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="17791-169">Ten licznik umożliwia pomiarów sposobu używania połączenia i jak wykonywanie operacji.</span><span class="sxs-lookup"><span data-stu-id="17791-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="17791-170">Liczniki są widoczne na wiele zakresów, danych zbieranych z wyższej zakresu są agregowane z danymi z niższym zakresów.</span><span class="sxs-lookup"><span data-stu-id="17791-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="17791-171">Na przykład `Calls` w punkcie końcowym reprezentuje sumę wszystkich wywołań operacji w ramach punktu końcowego; `Calls` w punkcie usług jest sumą wszystkich połączeń do wszystkich punktów końcowych w ramach usługi.</span><span class="sxs-lookup"><span data-stu-id="17791-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17791-172">Jeśli masz nazwy zduplikowanych operacji na kontrakt tylko uzyskać jednego wystąpienia liczników dla obu operacji.</span><span class="sxs-lookup"><span data-stu-id="17791-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="17791-173">Programowanie liczniki wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="17791-173">Programming the WCF Performance Counters</span></span>  
 <span data-ttu-id="17791-174">Kilka plików są instalowane w folderze instalacyjnym zestawu SDK, dzięki czemu można uzyskać dostępu do [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] programowo liczników wydajności.</span><span class="sxs-lookup"><span data-stu-id="17791-174">Several files are installed in the SDK install folder so that you can access the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performance counters programmatically.</span></span> <span data-ttu-id="17791-175">Te pliki znajdują się w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="17791-175">These files are listed as follows.</span></span>  
  
-   <span data-ttu-id="17791-176">_ServiceModelEndpointPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="17791-176">_ServiceModelEndpointPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="17791-177">_ServiceModelOperationPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="17791-177">_ServiceModelOperationPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="17791-178">_ServiceModelServicePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="17791-178">_ServiceModelServicePerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="17791-179">_SMSvcHostPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="17791-179">_SMSvcHostPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="17791-180">_TransactionBridgePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="17791-180">_TransactionBridgePerfCounters.vrg</span></span>  
  
 <span data-ttu-id="17791-181">Aby uzyskać więcej informacji na temat sposobu programowy dostęp liczniki, zobacz [Architektura programowania licznika wydajności](http://go.microsoft.com/fwlink/?LinkId=95179).</span><span class="sxs-lookup"><span data-stu-id="17791-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](http://go.microsoft.com/fwlink/?LinkId=95179).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17791-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17791-182">See Also</span></span>  
 [<span data-ttu-id="17791-183">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="17791-183">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
