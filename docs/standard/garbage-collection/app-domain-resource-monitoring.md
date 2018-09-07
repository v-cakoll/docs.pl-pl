---
title: Monitorowanie zasobów domen aplikacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50d601d711579bce2e2651a1efc65d824a50d47a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44082101"
---
# <a name="application-domain-resource-monitoring"></a>Monitorowanie zasobów domen aplikacji
(ARM) do monitorowania zasobów domen aplikacji włącza hosty do monitorowania wykorzystania procesora CPU i pamięci przez domenę aplikacji. Jest to przydatne w przypadku hostów takich jak ASP.NET, korzystających z wielu domen aplikacji w procesie długotrwałych. Host może zwolnienie domeny aplikacji w aplikacji, która jest negatywnego wpływu na wydajność całego procesu, ale tylko wtedy, gdy go zidentyfikować problematyczne aplikacji. ARM zawiera informacje, które mogą służyć do celów w podejmowaniu decyzji.  
  
 Na przykład Usługa hostingu może mieć wiele aplikacji uruchomionych na serwerze programu ASP.NET. Po rozpoczęciu zużywa zbyt dużej ilości pamięci lub zbyt dużo czasu procesora przez jedną aplikację w procesie usługi hostingowej służy ARM do identyfikowania domeny aplikacji, który jest przyczyną problemu.  
  
 ARM jest wystarczająco uproszczone do użycia w aplikacji na żywo. Za dostęp do informacji za pomocą śledzenia zdarzeń dla Windows (ETW) lub bezpośrednio w ramach zarządzanych lub natywnych interfejsów API.  
  
## <a name="enabling-resource-monitoring"></a>Włączanie monitorowania zasobu  
 ARM można włączyć na cztery sposoby: poprzez dostarczenie pliku konfiguracji, gdy środowisko uruchomieniowe języka wspólnego (CLR) została uruchomiona, przy użyciu niezarządzanych hostowanie interfejsu API przy użyciu kodu zarządzanego lub przez nasłuchiwanie zdarzeń ARM ETW.  
  
 Zaraz po włączeniu ARM rozpoczyna zbieranie danych na wszystkie domeny aplikacji, w tym procesie. Jeśli domena aplikacji zostało utworzone przed włączeniem ARM, skumulowane dane rozpoczyna się po włączeniu ARM nie, podczas tworzenia domeny aplikacji. Gdy jest włączone, nie można wyłączyć ARM.  
  
-   ARM można włączyć podczas uruchamiania środowiska CLR, dodając [ \<appdomainresourcemonitoring — >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) element do pliku konfiguracji, a ustawienie `enabled` atrybutu `true`. Wartość `false` (ustawienie domyślne) oznacza jedynie, że ARM nie jest włączone przy uruchamianiu; aktywować go później przy użyciu jednego z innych mechanizmów aktywacji.  
  
-   Hosta można włączyć ARM, żądając [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interfejs hosta. Po pomyślnym uzyskaniu ten interfejs jest włączone ARM.  
  
-   Kod zarządzany, można włączyć ARM przez ustawienie statycznego (`Shared` w języku Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> właściwość `true`. Jak najszybciej zostaje ustalona ARM jest włączona.  
  
-   Aby włączyć ARM po uruchomieniu, nasłuchiwać zdarzeń ETW. ARM jest włączona i rozpoczyna się wywoływanie zdarzeń, dla wszystkich domen aplikacji, po włączeniu publicznego dostawcę `Microsoft-Windows-DotNETRuntime` przy użyciu `AppDomainResourceManagementKeyword` — słowo kluczowe. Korelowanie danych z domenami aplikacji i wątków, należy również włączyć `Microsoft-Windows-DotNETRuntimeRundown` dostawcy o `ThreadingKeyword` — słowo kluczowe.  
  
## <a name="using-arm"></a>Za pomocą ARM  
 ARM zapewnia całkowitego czasu procesora, używanego przez domenę aplikacji i trzy rodzaje informacji na temat użycia pamięci.  
  
-   **Łączny czas procesora dla domeny aplikacji, w ciągu kilku sekund**: to jest obliczany przez zsumowanie razy wątku zgłoszony przez system operacyjny dla wszystkich wątków, w których czas wykonywania w domenie aplikacji, jego okres istnienia. Zablokowane lub uśpionych wątków nie należy używać czasu procesora. Gdy wątek wywołuje kod natywny, czas, jaki wątek zużywa w kodzie natywnym znajduje się w liczbę elementów w domenie aplikacji, w którym wykonano wywołanie.  
  
    -   Zarządzany interfejs API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> właściwości.  
  
    -   Hostowanie interfejsu API: [iclrappdomainresourcemonitor::getcurrentcputime —](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) metody.  
  
    -   Zdarzenia ETW: `ThreadCreated`, `ThreadAppDomainEnter`, i `ThreadTerminated` zdarzenia. Dla informacji o dostawcy i słów kluczowych, zobacz "Zdarzenia monitorowania zasobów obiektu AppDomain" w [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md).  
  
-   **Łączna liczba zarządzanych alokacji dokonanych przez domenę aplikacji, jego okres istnienia w bajtach**: całkowitą alokacji nie zawsze odzwierciedla użycia pamięci przez domenę aplikacji, ponieważ przydzielone obiekty mogą być krótkotrwałe. Jednak jeśli aplikacja przydziela i zwalnia ogromną liczbę obiektów, koszt alokacje może być istotne.  
  
    -   Zarządzany interfejs API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> właściwości.  
  
    -   Hostowanie interfejsu API: [iclrappdomainresourcemonitor::getcurrentallocated —](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) metody.  
  
    -   Zdarzenia ETW: `AppDomainMemAllocated` zdarzenia `Allocated` pola.  
  
-   **Zarządzane pamięci w bajtach, która odwołuje się do domeny aplikacji i które przetrwały najnowszych pełnej, blokowanie pamięci**: Ta liczba jest dokładne dopiero po pełnej, blokowanie pamięci. (To w przeciwieństwie do kolekcji współbieżnych, które występują w tle i nie zablokują aplikacji). Na przykład <xref:System.GC.Collect?displayProperty=nameWithType> przeciążenie metody powoduje, że pełne, blokowanie pamięci.  
  
    -   Zarządzany interfejs API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> właściwości.  
  
    -   Hostowanie interfejsu API: [iclrappdomainresourcemonitor::getcurrentsurvived —](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metody `pAppDomainBytesSurvived` parametru.  
  
    -   Zdarzenia ETW: `AppDomainMemSurvived` zdarzenia `Survived` pola.  
  
-   **Łączna liczba zarządzanej pamięci w bajtach, który odwołuje się do niej proces i które przetrwały najnowszych pełnej, blokowanie pamięci**: pamięci przetrwałych dla poszczególnych aplikacji domen można porównać do tej liczby.  
  
    -   Zarządzany interfejs API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> właściwości.  
  
    -   Hostowanie interfejsu API: [iclrappdomainresourcemonitor::getcurrentsurvived —](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metody `pTotalBytesSurvived` parametru.  
  
    -   Zdarzenia ETW: `AppDomainMemSurvived` zdarzenia `ProcessSurvived` pola.  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>Określanie podczas pełnego, blokowanie pamięci występuje  
 Aby określić, kiedy są dokładne liczniki pamięci przetrwałych, musisz wiedzieć, kiedy tylko wystąpił pełną kolekcję blokowania. Metoda w ten sposób zależy od interfejsu API umożliwia zbadanie statystyki ARM.  
  
#### <a name="managed-api"></a>Zarządzany interfejs API  
 Jeśli używasz właściwości <xref:System.AppDomain> klasy, można użyć <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> metodę, aby zarejestrować powiadamiania o pełnej kolekcji. Próg, którego używasz nie jest istotna, ponieważ oczekiwania na ukończenie kolekcji, a nie podejście kolekcji. Następnie możesz wywołać <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> metody, która blokuje, dopóki nie zakończy się zebranie pełnych. Można utworzyć wątku, który wywołuje metodę w pętli i wykonuje wszystkie niezbędne analizy, zawsze wtedy, gdy metoda ta zwraca.  
  
 Ewentualnie możesz wywołać <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> metoda okresowo, aby zobaczyć, jeśli został zwiększony liczba kolekcji generacji 2. W zależności od częstotliwości sondowania ta technika może nie być tak dokładne wskazanie wystąpienia zebranie pełnych.  
  
#### <a name="hosting-api"></a>Hostowanie interfejsu API  
 Jeśli korzystasz z niezarządzanego API hostingu, hosta musi pomyślnie przejść CLR implementację [ihostgcmanager —](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) interfejsu. CLR wywołuje [ihostgcmanager::suspensionending —](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metody, gdy kontynuuje wykonywanie wątków, które zostało zawieszone, gdy występuje w kolekcji. Środowisko CLR przekazuje Generowanie ukończone kolekcji jako parametru metody, tak przyjmującym można określić, czy kolekcja została pełnej lub częściowej. Implementacja [ihostgcmanager::suspensionending —](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metoda wysłać zapytanie dotyczące pamięci przetrwałych, aby upewnić się, że liczby są pobierane, tak szybko, jak są one aktualizowane.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
- [ICLRAppDomainResourceMonitor, interfejs](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
- [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
