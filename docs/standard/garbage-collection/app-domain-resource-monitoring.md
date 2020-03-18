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
ms.openlocfilehash: 54e300bef1818fd08f27d7920eec68ee1f2c45bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141380"
---
# <a name="application-domain-resource-monitoring"></a>Monitorowanie zasobów domen aplikacji

Monitorowanie zasobów domeny aplikacji (ARM) umożliwia hostom monitorowanie użycia procesora CPU i pamięci według domeny aplikacji. Jest to przydatne w przypadku hostów, takich jak ASP.NET, które używają wielu domen aplikacji w długotrwałym procesie. Host może zwolnić domeny aplikacji aplikacji, która ma negatywny wpływ na wydajność całego procesu, ale tylko wtedy, gdy można zidentyfikować problematyczną aplikację. ARM dostarcza informacji, które mogą być wykorzystane do pomocy w podejmowaniu takich decyzji.

Na przykład usługa hostingowa może mieć wiele aplikacji uruchomionych na serwerze ASP.NET. Jeśli jedna aplikacja w procesie zaczyna zużywać zbyt dużo pamięci lub zbyt dużo czasu procesora, usługa hostingowa może użyć ARM do zidentyfikowania domeny aplikacji, która jest przyczyną problemu.

ARM jest wystarczająco lekki, aby można go było używać w zastosowaniach na żywo. Dostęp do informacji można uzyskać za pomocą śledzenia zdarzeń dla systemu Windows (ETW) lub bezpośrednio za pośrednictwem zarządzanych lub macierzystych interfejsów API.

## <a name="enabling-resource-monitoring"></a>Włączanie monitorowania zasobów

ARM można włączyć na cztery sposoby: po podaniu pliku konfiguracyjnego po uruchomieniu wspólnego języka (CLR), przy użyciu interfejsu API hostingu niezarządzanego, przy użyciu kodu zarządzanego lub nasłuchując zdarzeń ARM ETW.

Po włączeniu funkcji ARM rozpoczyna zbieranie danych we wszystkich domenach aplikacji w procesie. Jeśli domena aplikacji została utworzona przed włączeniu arm, dane skumulowane uruchamia się, gdy ARM jest włączona, a nie po utworzeniu domeny aplikacji. Po włączeniu arm nie można wyłączyć.

- Funkcję ARM podczas uruchamiania systemu CLR można włączyć, dodając element [ \<>appDomainResourceMonitoring](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) do pliku konfiguracyjnego i ustawiając atrybut na `enabled` `true`. Wartość `false` (domyślna) oznacza tylko, że ARM nie jest włączona podczas uruchamiania; można aktywować go później za pomocą jednego z innych mechanizmów aktywacji.

- Host może włączyć ARM, żądając interfejsu hostingu [ICLRAppDomainResourceMonitor.](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) Po pomyślnym uzyskaniu tego interfejsu, ARM jest włączona.

- Kod zarządzany może włączyć ARM,`Shared` ustawiając <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> właściwość `true`static (w języku Visual Basic) na . Jak tylko właściwość jest ustawiona, ARM jest włączona.

- Po uruchomieniu można włączyć funkcję ARM, słuchając zdarzeń ETW. ARM jest włączona i rozpoczyna podnoszenie zdarzeń dla wszystkich `Microsoft-Windows-DotNETRuntime` domen `AppDomainResourceManagementKeyword` aplikacji po włączeniu dostawcy publicznego przy użyciu słowa kluczowego. Aby skorelować dane z domenami aplikacji i `Microsoft-Windows-DotNETRuntimeRundown` wątkami, należy również włączyć dostawcę za pomocą słowa kluczowego. `ThreadingKeyword`

## <a name="using-arm"></a>Korzystanie z ARM

ARM zapewnia całkowity czas procesora, który jest używany przez domenę aplikacji i trzy rodzaje informacji o użyciu pamięci.

- **Całkowity czas procesora dla domeny aplikacji, w sekundach**: Jest on obliczany przez sumowanie czasów wątków zgłoszonych przez system operacyjny dla wszystkich wątków, które spędziły czas wykonywania w domenie aplikacji w okresie jej istnienia. Zablokowane lub uśpione wątki nie używają czasu procesora. Gdy wątek wywołuje do kodu macierzystego, czas, który wątek spędza w kodzie macierzystym jest uwzględniony w liczbie dla domeny aplikacji, w której zostało wykonane wywołanie.

  - Zarządzany interfejs <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> API: właściwość.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentCpuTime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) metody.

  - Zdarzenia `ThreadCreated`ETW: `ThreadAppDomainEnter`, `ThreadTerminated` i wydarzenia. Aby uzyskać informacje o dostawcach i słowach kluczowych, zobacz "Zdarzenia monitorowania zasobów appdomain" w [zdarzeniach CLR ETW](../../../docs/framework/performance/clr-etw-events.md).

- **Całkowita liczba zarządzanych alokacji dokonanych przez domenę aplikacji w okresie jej istnienia, w bajtach**: Całkowita alokacja nie zawsze odzwierciedla użycie pamięci przez domenę aplikacji, ponieważ przydzielone obiekty mogą być krótkotrwałe. Jeśli jednak aplikacja przydziela i zwalnia ogromną liczbę obiektów, koszt alokacji może być znaczny.

  - Zarządzany interfejs <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> API: właściwość.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentAllocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) metody.

  - Zdarzenia ETW: `AppDomainMemAllocated` `Allocated` zdarzenie, pole.

- **Pamięć zarządzana, w bajtach, do której odwołuje się domena aplikacji i która przetrwała najnowszą pełną, blokującą kolekcję**: Ten numer jest dokładny dopiero po pełnej, blokującej kolekcji. (Jest to w przeciwieństwie do równoczesnych kolekcji, które występują w tle i nie blokują aplikacji.) Na przykład <xref:System.GC.Collect?displayProperty=nameWithType> przeciążenie metody powoduje pełne, blokowanie kolekcji.

  - Zarządzany interfejs <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> API: właściwość.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metoda, `pAppDomainBytesSurvived` parametr.

  - Zdarzenia ETW: `AppDomainMemSurvived` `Survived` zdarzenie, pole.

- **Całkowita pamięć zarządzana, w bajtach, do której odwołuje się proces i która przetrwała najnowszą pełną, blokującą kolekcję**: Przetrwała pamięć dla poszczególnych domen aplikacji można porównać z tą liczbą.

  - Zarządzany interfejs <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> API: właściwość.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metoda, `pTotalBytesSurvived` parametr.

  - Zdarzenia ETW: `AppDomainMemSurvived` `ProcessSurvived` zdarzenie, pole.

### <a name="determining-when-a-full-blocking-collection-occurs"></a>Określanie, kiedy występuje pełna, blokująca kolekcja

Aby określić, kiedy liczba pamięci przetrwała są dokładne, musisz wiedzieć, kiedy pełne, blokowanie kolekcji właśnie wystąpił. Metoda tego zależy od interfejsu API, którego używasz do badania statystyk ARM.

#### <a name="managed-api"></a>Zarządzany interfejs API

Jeśli używasz właściwości <xref:System.AppDomain> klasy, można użyć <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> metody, aby zarejestrować się do powiadamiania o pełnych kolekcji. Próg, którego używasz nie jest ważne, ponieważ oczekujesz na zakończenie kolekcji, a nie podejście kolekcji. Następnie można wywołać <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> metodę, która blokuje, dopóki pełna kolekcja nie zostanie ukończona. Można utworzyć wątek, który wywołuje metodę w pętli i wykonuje wszelkie niezbędne analizy, gdy zwraca metodę.

Alternatywnie można wywołać <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> metodę okresowo, aby sprawdzić, czy liczba kolekcji generacji 2 wzrosła. W zależności od częstotliwości sondowania ta technika może nie zapewniać jako dokładne wskazanie wystąpienia pełnej kolekcji.

#### <a name="hosting-api"></a>Hosting API

Jeśli używasz interfejsu API hostingu niezarządzanego, host musi przekazać CLR implementację interfejsu [IHostGCManager.](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) CLR wywołuje [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metody, gdy wznawia wykonywanie wątków, które zostały zawieszone podczas wystąpienia kolekcji. CLR przekazuje generacji ukończonej kolekcji jako parametr metody, dzięki czemu host może określić, czy kolekcja była pełna lub częściowa. Implementacja [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metoda może kwerendy dla pamięci przetrwała, aby upewnić się, że liczby są pobierane, jak tylko są aktualizowane.

## <a name="see-also"></a>Zobacz też

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [ICLRAppDomainResourceMonitor — Interfejs](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [\<>monitorowania zasobów domeny aplikacjiDomainResource](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Zdarzenia ETW CLR](../../../docs/framework/performance/clr-etw-events.md)
