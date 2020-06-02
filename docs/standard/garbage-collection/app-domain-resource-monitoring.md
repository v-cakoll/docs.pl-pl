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
ms.openlocfilehash: 12dfdd3ac6d75a3e2a33f93d8847c963ded912e8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286096"
---
# <a name="application-domain-resource-monitoring"></a>Monitorowanie zasobów domen aplikacji

Monitorowanie zasobów domeny aplikacji (ARM) umożliwia hostom monitorowanie użycia procesora i pamięci przez domenę aplikacji. Jest to przydatne w przypadku hostów, takich jak ASP.NET, które używają wielu domen aplikacji w długotrwałym procesie. Host może zwolnić domenę aplikacji, która ma negatywny wpływ na wydajność całego procesu, ale tylko wtedy, gdy może identyfikować problematyczną aplikację. ARM zawiera informacje, które mogą pomóc w podejmowaniu takich decyzji.

Na przykład usługa hostingu może mieć wiele aplikacji uruchomionych na serwerze ASP.NET. Jeśli jedna aplikacja w procesie zacznie zużywać zbyt dużo pamięci lub zbyt dużo czasu procesora, usługa hostingu może użyć ARM do zidentyfikowania domeny aplikacji, która powoduje problem.

ARM jest wystarczająco lekki, aby można go było używać w aplikacjach na żywo. Dostęp do tych informacji można uzyskać przy użyciu funkcji śledzenia zdarzeń systemu Windows (ETW) lub bezpośrednio za pośrednictwem interfejsów API zarządzanych lub natywnych.

## <a name="enabling-resource-monitoring"></a>Włączanie monitorowania zasobów

ARM można włączyć na cztery sposoby: dostarczając plik konfiguracyjny podczas uruchamiania środowiska uruchomieniowego języka wspólnego (CLR), używając niezarządzanego interfejsu API hostingu przy użyciu kodu zarządzanego lub przez nasłuchiwanie zdarzeń ETW usługi ARM.

Zaraz po włączeniu ARM rozpocznie się zbieranie danych we wszystkich domenach aplikacji w procesie. Jeśli domena aplikacji została utworzona przed włączeniem ARM, dane zbiorcze są uruchamiane po włączeniu ARM, a nie podczas tworzenia domeny aplikacji. Po włączeniu nie można wyłączyć ARM.

- Możesz włączyć ARM przy uruchamianiu CLR przez dodanie [\<appDomainResourceMonitoring>](../../framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) elementu do pliku konfiguracji i ustawienie `enabled` atrybutu na `true` . Wartość `false` (domyślna) oznacza tylko to, że ARM nie jest włączona przy uruchamianiu. można ją później aktywować przy użyciu jednego z innych mechanizmów aktywacji.

- Host może włączyć ARM, żądając interfejsu hostingu [ICLRAppDomainResourceMonitor](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) . Po pomyślnym uzyskaniu tego interfejsu ARM jest włączona.

- Kod zarządzany może włączyć ARM przez ustawienie właściwości static ( `Shared` in Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> na `true` . Gdy tylko właściwość jest ustawiona, ARM jest włączona.

- Możesz włączyć ARM po uruchomieniu, nasłuchuje zdarzeń ETW. Funkcja ARM jest włączona i rozpoczyna wywoływanie zdarzeń dla wszystkich domen aplikacji po włączeniu dostawcy publicznego `Microsoft-Windows-DotNETRuntime` za pomocą `AppDomainResourceManagementKeyword` słowa kluczowego. Aby skorelować dane z domenami i wątkami aplikacji, należy również włączyć `Microsoft-Windows-DotNETRuntimeRundown` dostawcę za pomocą `ThreadingKeyword` słowa kluczowego.

## <a name="using-arm"></a>Korzystanie z usługi ARM

ARM udostępnia łączny czas procesora używany przez domenę aplikacji oraz trzy rodzaje informacji o użyciu pamięci.

- **Łączny czas procesora dla domeny aplikacji (w sekundach**): jest to obliczone przez dodanie czasów wątków zgłoszonych przez system operacyjny dla wszystkich wątków, które wykorzystały czas wykonywania w domenie aplikacji w okresie istnienia. Wątki zablokowane lub uśpione nie używają czasu procesora. Gdy wątek wywołuje kod natywny, czas spędzony przez wątek w kodzie natywnym jest uwzględniany w liczbie dla domeny aplikacji, w której wykonano wywołanie.

  - Zarządzany interfejs API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> Właściwość.

  - Hostowanie interfejsu API: [ICLRAppDomainResourceMonitor:: GetCurrentCpuTime —](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) .

  - Zdarzenia ETW: `ThreadCreated` , `ThreadAppDomainEnter` i `ThreadTerminated` . Aby uzyskać informacje o dostawcach i słowach kluczowych, zobacz "zdarzenia monitorowania zasobów domeny aplikacji" w [zdarzeniach ETW CLR](../../framework/performance/clr-etw-events.md).

- **Łączna liczba zarządzanych alokacji wykonanych przez domenę aplikacji w okresie istnienia (w bajtach**): całkowita liczba alokacji nie zawsze odzwierciedla użycie pamięci przez domenę aplikacji, ponieważ przydzielone obiekty mogą być krótkotrwałe. Jeśli jednak aplikacja przydzieli i zwolni ogromną liczbę obiektów, koszt alokacji może być znaczny.

  - Zarządzany interfejs API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> Właściwość.

  - Hostowanie interfejsu API: [ICLRAppDomainResourceMonitor:: GetCurrentAllocated —](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) .

  - Zdarzenia ETW: `AppDomainMemAllocated` zdarzenie, `Allocated` pole.

- **Pamięć zarządzana, w bajtach, do której odwołuje się domena aplikacji i która przeżyły ostatnią pełną, blokującą kolekcję**: Ta liczba jest dokładna tylko wtedy, gdy pełna, blokująca kolekcja. (W przeciwieństwie do współbieżnych kolekcji, które występują w tle i nie blokują aplikacji). Na przykład <xref:System.GC.Collect?displayProperty=nameWithType> Przeciążenie metody powoduje pełna, blokująca kolekcja.

  - Zarządzany interfejs API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> Właściwość.

  - Hosting API: [ICLRAppDomainResourceMonitor:: GetCurrentSurvived —](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) Metoda, `pAppDomainBytesSurvived` parametr.

  - Zdarzenia ETW: `AppDomainMemSurvived` zdarzenie, `Survived` pole.

- **Całkowita pamięć zarządzana, w bajtach, do której odwołuje się proces i która przeżyły najnowszą pełną, blokującą kolekcję: pamięć przepełniona**dla poszczególnych domen aplikacji może być porównana z tą liczbą.

  - Zarządzany interfejs API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> Właściwość.

  - Hosting API: [ICLRAppDomainResourceMonitor:: GetCurrentSurvived —](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) Metoda, `pTotalBytesSurvived` parametr.

  - Zdarzenia ETW: `AppDomainMemSurvived` zdarzenie, `ProcessSurvived` pole.

### <a name="determining-when-a-full-blocking-collection-occurs"></a>Ustalanie, kiedy występuje pełna, blokująca kolekcja

Aby określić, kiedy liczby przepełnionych pamięci są dokładne, musisz wiedzieć, kiedy wystąpiła pełna, blokująca kolekcja. Ta metoda jest zależna od interfejsu API, który jest używany do badania statystyk ARM.

#### <a name="managed-api"></a>Zarządzany interfejs API

Jeśli używasz właściwości <xref:System.AppDomain> klasy, możesz użyć <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> metody do zarejestrowania się w celu powiadomienia o pełnych kolekcjach. Używany próg nie jest istotny, ponieważ oczekujesz na ukończenie kolekcji, a nie podejścia do kolekcji. Następnie można wywołać <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> metodę, która blokuje do momentu ukończenia pełnej kolekcji. Można utworzyć wątek, który wywołuje metodę w pętli i wykonuje wszelką konieczną analizę za każdym razem, gdy metoda zwraca.

Alternatywnie można wywołać <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> metodę okresowo, aby sprawdzić, czy liczba kolekcji generacji 2 została zwiększona. W zależności od częstotliwości sondowania ta technika może nie zapewniać dokładnego wskazania wystąpienia pełnej kolekcji.

#### <a name="hosting-api"></a>Hostowanie interfejsu API

W przypadku korzystania z niezarządzanego interfejsu API hostingu host musi przekazać CLR implementację interfejsu [IHostGCManager](../../framework/unmanaged-api/hosting/ihostgcmanager-interface.md) . Środowisko CLR wywołuje metodę [IHostGCManager:: SuspensionEnding —](../../framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) , gdy wznawia wykonywanie wątków, które zostały zawieszone, gdy występuje kolekcja. Środowisko CLR przekazuje generowanie zakończonej kolekcji jako parametr metody, dlatego host może określić, czy kolekcja jest pełna czy częściowa. Implementacja metody [IHostGCManager:: SuspensionEnding —](../../framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) może wysyłać zapytania o pamięć przeżyły, aby upewnić się, że liczniki są pobierane zaraz po ich aktualizacji.

## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [ICLRAppDomainResourceMonitor — Interfejs](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [\<appDomainResourceMonitoring>](../../framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Zdarzenia ETW CLR](../../framework/performance/clr-etw-events.md)
