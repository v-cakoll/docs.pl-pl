---
title: "Monitorowanie zasobów domen aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 648f8b86ecf73a7da5f3f33d71fb8617bacccee1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="application-domain-resource-monitoring"></a>Monitorowanie zasobów domen aplikacji
Zasobów domen aplikacji monitorowania (ARM) umożliwia hostom monitorowanie użycia procesora CPU i pamięci według domeny aplikacji. Jest to przydatne dla hostów, takich jak ASP.NET, korzystających z wielu domen aplikacji w procesie długotrwałe. Hosta można wyładować domeny aplikacji, aplikacji, która jest negatywnego wpływu na wydajność całego procesu, ale tylko wtedy, jeśli można zidentyfikować problematyczne aplikacji. ARM zawiera informacje, które mogą służyć do celów podczas podejmowania decyzji.  
  
 Na przykład Usługa hostingu może mieć wiele aplikacji uruchomionych na serwerze programu ASP.NET. Jeśli jedną aplikację w procesie zacznie zużywa zbyt dużej ilości pamięci lub zbyt dużo czasu procesora, usługę hostingu służą ARM do identyfikacji domeny aplikacji, która powoduje problem.  
  
 ARM jest wystarczająco lekkie do użycia w aplikacjach na żywo. Można uzyskać dostępu do informacji za pomocą śledzenie zdarzeń systemu Windows (ETW) lub bezpośrednio za pośrednictwem interfejsów API zarządzanym lub macierzystym.  
  
## <a name="enabling-resource-monitoring"></a>Włączanie monitorowania zasobów  
 ARM można włączyć na cztery sposoby: poprzez dostarczanie plik konfiguracji, gdy środowisko uruchomieniowe języka wspólnego (CLR) została uruchomiona, przy użyciu niezarządzanych hosting interfejsu API, za pomocą kodu zarządzanego lub przez nasłuchiwanie zdarzeń ARM ETW.  
  
 Jak ARM jest włączona, rozpoczyna zbieranie danych we wszystkich domenach aplikacji w procesie. Jeśli domena aplikacji została utworzona przed włączeniem ARM, rozpoczyna się dane, gdy ARM jest włączone, nie, podczas tworzenia domeny aplikacji. Gdy ta funkcja jest włączona, nie można wyłączyć ARM.  
  
-   Przy uruchamianiu CLR można włączać ARM, dodając [ \<appdomainresourcemonitoring — >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) elementu do pliku konfiguracji, a ustawienie `enabled` atrybutu `true`. Wartość `false` (ustawienie domyślne) oznacza, że tylko ARM nie jest włączona przy uruchamianiu; Aktywuj ją później za pomocą jednego z innych mechanizmów aktywacji.  
  
-   Hosta można włączyć ARM przez zażądanie [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interfejs hosta. Po pomyślnym uzyskaniu ten interfejs ARM jest włączone.  
  
-   Kod zarządzany można włączyć ARM przez ustawienie statycznych (`Shared` w języku Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> właściwości `true`. Gdy ta właściwość jest ustawiona, ARM jest włączone.  
  
-   ARM można włączyć po uruchomieniu przez nasłuchiwanie zdarzeń ETW. ARM jest włączona i rozpocznie się wywoływanie zdarzeń dla wszystkich domen aplikacji, po włączeniu publicznego dostawcę `Microsoft-Windows-DotNETRuntime` za pomocą `AppDomainResourceManagementKeyword` — słowo kluczowe. Służące do skorelowania danych z domeny aplikacji i wątków, należy również włączyć `Microsoft-Windows-DotNETRuntimeRundown` dostawcy z `ThreadingKeyword` — słowo kluczowe.  
  
## <a name="using-arm"></a>Przy użyciu programu ARM  
 ARM zawiera łączny czas procesora jest używana przez domenę aplikacji i trzy rodzaje informacji na temat użycia pamięci.  
  
-   **Łączny czas procesora dla domeny aplikacji, w sekundach**: to jest obliczana przez dodawanie razy wątku podaną przez system operacyjny dla wszystkich wątków, które poświęciły czasu wykonywania w domenie aplikacji przez jego okres istnienia. Zablokowane lub uśpiony wątków nie należy używać czasu procesora. Gdy wywołuje wątku w kodzie natywnym, czas, który zużywa wątku w kodzie natywnym jest uwzględnione w liczbie domeny aplikacji, w którym wykonano wywołanie.  
  
    -   Zarządzanego interfejsu API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> właściwości.  
  
    -   Hostingu API: [ICLRAppDomainResourceMonitor::GetCurrentCpuTime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) metody.  
  
    -   Zdarzenia ETW: `ThreadCreated`, `ThreadAppDomainEnter`, i `ThreadTerminated` zdarzenia. Aby uzyskać informacje o dostawcy i słów kluczowych, zobacz "Zdarzenia monitorowania zasobów obiektu AppDomain" w [zdarzenia ETW CLR](../../../docs/framework/performance/clr-etw-events.md).  
  
-   **Łączna liczba zarządzanych przydziały domeny aplikacji przez jego okres istnienia w bajtach**: łączna alokacje nie zawsze odzwierciedlają użycie pamięci przez domenę aplikacji, ponieważ przydzielone obiekty mogą być krótkotrwały. Jednak jeśli aplikacja przydziela i zwalnia ogromnych liczby obiektów, kosztów alokacje może być istotne.  
  
    -   Zarządzanego interfejsu API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> właściwości.  
  
    -   Hostingu API: [ICLRAppDomainResourceMonitor::GetCurrentAllocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) metody.  
  
    -   Zdarzenia ETW: `AppDomainMemAllocated` zdarzenia `Allocated` pola.  
  
-   **Zarządzane pamięci w bajtach, do którego odwołuje domeny aplikacji i który udało się przetrwać ostatniego pełnego, blokowanie kolekcji**: Ta liczba jest dokładne tylko po pełnej, blokowanie kolekcji. (Jest w przeciwieństwie do kolekcji współbieżnych, które występują w tle i nie blokują aplikacji). Na przykład <xref:System.GC.Collect?displayProperty=nameWithType> przeciążenie metody powoduje, że pełne, blokowanie kolekcji.  
  
    -   Zarządzanego interfejsu API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> właściwości.  
  
    -   Hostingu API: [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metody `pAppDomainBytesSurvived` parametru.  
  
    -   Zdarzenia ETW: `AppDomainMemSurvived` zdarzenia `Survived` pola.  
  
-   **Całkowita liczba pamięci zarządzanej, w bajtach, do którego odwołuje proces i który udało się przetrwać ostatniego pełnego, blokowanie kolekcji**: survived pamięci dla poszczególnych aplikacji domen można porównać do tego numeru.  
  
    -   Zarządzanego interfejsu API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> właściwości.  
  
    -   Hostingu API: [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metody `pTotalBytesSurvived` parametru.  
  
    -   Zdarzenia ETW: `AppDomainMemSurvived` zdarzenia `ProcessSurvived` pola.  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>Określanie podczas pełnej, blokowanie kolekcji występuje  
 Aby określić, kiedy są dokładne liczniki pamięci udało przetrwać, należy poinformować, gdy tylko wystąpił kolekcji pełne, blokowania. Metodę dla tej czynności zależy od interfejsu API, użyj do sprawdzenia statystyki ARM.  
  
#### <a name="managed-api"></a>Zarządzanego interfejsu API  
 Jeśli używasz właściwości <xref:System.AppDomain> klasy, można użyć <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> metodę, aby zarejestrować powiadamiania o pełnej kolekcji. Próg, którego używasz nie jest ważna, ponieważ są oczekiwanie na zakończenia kolekcji, a nie podejście do kolekcji. Następnie można wywołać <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> metodę, która blokuje dopiero po ukończeniu pełnej kolekcji. Można utworzyć wątku, który wywołuje metodę w pętli i wykonuje wszelkie niezbędne analizy, gdy metoda zwraca.  
  
 Alternatywnie możesz wywołać <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> metody okresowo, aby zobaczyć, czy wzrosło liczba kolekcji generacji 2. W zależności od częstotliwość sondowania ta technika może nie być tak dokładne wskazanie wystąpienia pełnej kolekcji.  
  
#### <a name="hosting-api"></a>Hostingu API  
 Korzystając z niezarządzanego API hostingu, host musi przejść CLR implementacja [IHostGCManager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) interfejsu. Wywołania CLR [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metodą podczas kontynuuje wykonywanie wątków, które zostało zawieszone, gdy występuje w kolekcji. Środowisko CLR przekazuje Generowanie zakończone kolekcji jako parametr metody, dzięki czemu hosta można określić, czy kolekcja została pełnej lub częściowej. Implementacji [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metody mogą wykonywać kwerendę o udało przetrwać pamięci, aby upewnić się, że liczby elementów są pobierane, jak tylko zostaną zaktualizowane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [ICLRAppDomainResourceMonitor, interfejs](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [\<appdomainresourcemonitoring — >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
