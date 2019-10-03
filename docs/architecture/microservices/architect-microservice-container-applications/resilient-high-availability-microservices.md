---
title: Odporność i wysoka dostępność w mikrousługach
description: Mikrousługi muszą zostać zaprojektowane w celu wyizolowania przejściowych błędów sieci i zależności, które muszą być odporne na uzyskanie wysokiej dostępności.
ms.date: 09/20/2018
ms.openlocfilehash: 6c110b0fe7a80842f12779494e5b0bdd29c5fb64
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834352"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Odporność i wysoka dostępność w mikrousługach

Postępowanie z nieoczekiwanymi awariami jest jednym z najtrudniejszych problemów, które należy rozwiązać, szczególnie w systemie rozproszonym. Większość kodu, który deweloperzy piszą, obejmuje obsługę wyjątków, a także to, w jaki sposób jest to najbardziej czasochłonne w testowaniu. Ten problem jest większy niż podczas pisania kodu do obsługi błędów. Co się stanie, gdy maszyna, na której działa mikrousługa, nie powiedzie się? Nie tylko należy wykryć ten błąd mikrousługi (na swoim własnym problemie), ale konieczne jest również ponowne uruchomienie mikrousługi.

Mikrousługa musi być odporna na awarie i być w stanie uruchamiać się często na innym komputerze w celu zapewnienia dostępności. Ta odporność jest również dostępna w odniesieniu do stanu, który został zapisany w imieniu mikrousługi, w którym mikrousługa może odzyskać ten stan, a także czy mikrousługa może zostać pomyślnie ponownie uruchomiona. Innymi słowy, musi być odporności w możliwości obliczeniowej (proces można uruchomić ponownie w dowolnym momencie), a także odporności w stanie lub danych (bez utraty danych, a dane pozostają spójne).

Problemy związane z odpornością są złożone w innych scenariuszach, na przykład w przypadku wystąpienia awarii podczas uaktualniania aplikacji. Mikrousługa, praca z systemem wdrażania, musi ustalić, czy może kontynuować przejście do nowszej wersji, czy też przywrócić poprzednią wersję, aby zachować spójny stan. Pytania, takie jak informacje o dostępności wystarczającej liczby maszyn do przechodzenia do przodu i sposobu odzyskania wcześniejszych wersji mikrousług. Wymaga to mikrousługi do emitowania informacji o kondycji, tak aby ogólna aplikacja i program Orchestrator mogły podejmować te decyzje.

Ponadto odporność jest związana z sposobem, w jaki działają systemy oparte na chmurze. Jak wspomniano, system oparty na chmurze musi obejmować błędy i musi próbować automatycznie odzyskać z nich. Na przykład w przypadku awarii sieci lub kontenera aplikacje klienckie lub usługi klienta muszą mieć strategię, aby ponowić próbę wysłania wiadomości lub ponowić żądanie, ponieważ w wielu przypadkach błędy w chmurze są częściowe. Sekcja [implementowanie odpornych aplikacji](../implement-resilient-applications/index.md) w tym przewodniku dotyczy sposobu obsługi awarii częściowej. Opisano w nim techniki, takie jak ponawianie prób z wykładniczą wycofywania lub wzorzec wyłącznika w środowisku .NET Core za pomocą bibliotek, takich jak [Polly](https://github.com/App-vNext/Polly), które oferują wiele różnych zasad do obsługi tego tematu.

## <a name="health-management-and-diagnostics-in-microservices"></a>Zarządzanie kondycją i Diagnostyka w mikrousługach

Może wydawać się oczywiste i często pojawia się, ale mikrousługa musi zgłosić swoją kondycję i diagnostykę. W przeciwnym razie można uzyskać niewiele informacji o perspektywie operacji. Skorelowanie zdarzeń diagnostycznych w ramach zestawu niezależnych usług i rozwiązywanie problemów z zegarem maszynowym sprawia, że kolejność zdarzeń jest trudne. W taki sam sposób, w jaki współdziałasz z mikrousługą przez uzgodnione protokoły i formaty danych, istnieje potrzeba standaryzacji w sposobie rejestrowania kondycji i zdarzeń diagnostycznych, które ostatecznie kończą się w magazynie zdarzeń na potrzeby wykonywania zapytań i wyświetlania. W podejściu mikrousług jest kluczem, że różne zespoły zgadzają się w jednym formacie rejestrowania. Musi być spójne podejście do wyświetlania zdarzeń diagnostycznych w aplikacji.

### <a name="health-checks"></a>Kontrole kondycji

Kondycja różni się od diagnostyki. Kondycja polega na tym, że usługa mikrousług zgłasza bieżący stan, aby podjąć odpowiednie działania. Dobrym przykładem jest praca z mechanizmami uaktualniania i wdrażania w celu zapewnienia dostępności. Mimo że usługa może być w złej kondycji ze względu na awarię procesu lub ponowny rozruch komputera, usługa może nadal działać. Ostatnim wymaganiem jest to, że jest to gorsze dzięki przeprowadzeniu uaktualnienia. Najlepszym rozwiązaniem jest wykonanie badania w pierwszej kolejności lub poczekanie na odzyskanie mikrousługi. Zdarzenia dotyczące kondycji z mikrousługi pomagają nam podejmować świadome decyzje i, w efekcie, ułatwiają tworzenie samonaprawczych usług.

W sekcji [implementujące testy kondycji w usługach ASP.NET Core Services](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) w tym przewodniku wyjaśniono, jak używać nowej biblioteki ASP.NET HealthChecks w mikrousługach, dzięki czemu mogą oni zgłosić swój stan do usługi monitorowania w celu podjęcia odpowiednich działań.

Istnieje również możliwość użycia doskonałej biblioteki typu open source o nazwie puls pulsu, dostępnej w witrynie [GitHub](https://github.com/Xabaril/BeatPulse) i jako [pakietu NuGet](https://www.nuget.org/packages/BeatPulse/). Ta biblioteka przeprowadza również kontrole kondycji z symbolem, który obsługuje dwa typy kontroli:

- Wartość **dynamiczna**: sprawdza, czy usługa jest aktywna, czyli jeśli jest w stanie akceptować żądania i odpowiadać na nie. 
- **Gotowość**: sprawdza, czy zależności mikrousług (baza danych, usługi kolejek itp.) są gotowe, więc mikrousługa może wykonać to działanie. 

### <a name="using-diagnostics-and-logs-event-streams"></a>Używanie diagnostyki i dzienników strumieni zdarzeń

Dzienniki zawierają informacje dotyczące sposobu działania aplikacji lub usługi, w tym wyjątków, ostrzeżeń i prostych komunikatów informacyjnych. Zwykle każdy dziennik jest w formacie tekstowym z jedną linią dla każdego zdarzenia, chociaż wyjątki często zawierają również ślad stosu w wielu wierszach.

W monolitycznych aplikacjach opartych na serwerach można po prostu napisać dzienniki do pliku na dysku (pliku dziennika), a następnie przeanalizować je za pomocą dowolnego narzędzia. Ponieważ wykonanie aplikacji jest ograniczone do stałego serwera lub maszyny wirtualnej, zazwyczaj nie jest zbyt skomplikowane, aby analizować przepływ zdarzeń. Jednak w aplikacji rozproszonej, w której wiele usług jest wykonywanych w wielu węzłach w klastrze programu Orchestrator, możliwość skorelowania zdarzeń rozproszonych jest wyzwaniem.

Aplikacja oparta na mikrousługach nie powinna próbować przechowywać strumienia wyjściowego zdarzeń lub plików dziennika przez siebie, a nawet nie próbuje zarządzać kierowaniem zdarzeń do centralnej lokalizacji. Powinien być przezroczysty, co oznacza, że każdy proces powinien po prostu napisać strumień zdarzeń do standardowego wyjścia, który poniżej zostanie zebrany przez infrastrukturę środowiska wykonawczego, w której jest uruchomiona. Przykładem tych routerów strumienia zdarzeń jest [Microsoft. Diagnostic. użyciu struktury eventflow](https://github.com/Azure/diagnostics-eventflow), który zbiera strumienie zdarzeń z wielu źródeł i publikuje je w systemach wyjściowych. Mogą one obejmować proste wyjście standardowe dla środowiska programistycznego lub systemów chmurowych, takich jak [Azure monitor](https://azure.microsoft.com/services/monitor//) i [Diagnostyka Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostics-extension-overview). Istnieją również dobre platformy i narzędzia do analizy dzienników innych firm, które umożliwiają wyszukiwanie, generowanie alertów, raportowanie i monitorowanie dzienników nawet w czasie rzeczywistym, takich jak [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Usługi Orchestrator zarządzające kondycją i informacjami diagnostycznymi

Podczas tworzenia aplikacji opartej na mikrousługach należy zająć się złożonością. Oczywiście jedną mikrousługą jest prosta do rozpatrzenia, ale dziesiątki lub setki typów i tysięcy wystąpień mikrousług są skomplikowanym problemem. Nie dotyczy to jedynie kompilowania architektury mikrousług — potrzebna jest również wysoka dostępność, możliwość obsługi, odporność, kondycja i diagnostyka, jeśli zamierzasz mieć stabilny i spójny system.

![Diagram klastrów dostarczających platformę obsługi dla mikrousług.](./media/resilient-high-availability-microservices/microservice-platform.png)

**Rysunek 4-22**. Platforma mikrousług ma podstawowe znaczenie dla zarządzania kondycją aplikacji

Złożone problemy pokazane na rysunku 4-22 są bardzo trudne do rozwiązania przez siebie. Zespoły programistyczne powinny skupić się na rozwiązywaniu problemów z firmą i tworzeniu niestandardowych aplikacji przy użyciu metod opartych na mikrousługach. Nie powinny skupić się na rozwiązywaniu złożonych problemów z infrastrukturą; w takim przypadku koszt dowolnej aplikacji opartej na mikrousługach będzie ogromny. Z tego względu istnieją platformy oparte na mikrousługach, określane jako koordynator lub klastry mikrousług, które próbują rozwiązać twarde problemy związane z tworzeniem i uruchamianiem usługi oraz wydajnie korzystać z zasobów infrastruktury. Zmniejsza to złożoność kompilowania aplikacji, które korzystają z podejścia mikrousług.

Różne koordynatorzy mogą dźwiękować podobnie, ale testy diagnostyczne i kondycji oferowane przez poszczególne z nich różnią się w zależności od platformy systemu operacyjnego, jak wyjaśniono w następnej sekcji.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **12-składnikowa aplikacja. XI. Dzienniki: Traktuj dzienniki jako strumienie zdarzeń** \
  <https://12factor.net/logs>

- **Biblioteka diagnostyki użyciu struktury eventflow firmy Microsoft** Repozytorium GitHub. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Co to jest Diagnostyka Azure** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Łączenie komputerów z systemem Windows z usługą Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Rejestrowanie informacji o znaczeniu: przy użyciu bloku aplikacji do rejestrowania semantyki** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk** Oficjalna lokacja. \
  <https://www.splunk.com/>

- **EventSource — Klasa** Interfejs API śledzenia zdarzeń dla systemu Windows (ETW) \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Poprzedni](microservice-based-composite-ui-shape-layout.md)
>[dalej](scalable-available-multi-container-microservice-applications.md)
