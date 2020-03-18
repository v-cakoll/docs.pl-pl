---
title: Odporność i wysoka dostępność w ramach mikrousług
description: Mikrousługi muszą być zaprojektowane tak, aby wytrzymać przejściowe błędy sieci i zależności, które muszą być odporne na osiągnięcie wysokiej dostępności.
ms.date: 09/20/2018
ms.openlocfilehash: 1c0f75a8c68d1f84ba24c550e854edc5372cf7f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73094213"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Odporność i wysoka dostępność w ramach mikrousług

Radzenie sobie z nieoczekiwanymi awariami jest jednym z najtrudniejszych problemów do rozwiązania, zwłaszcza w systemie rozproszonym. Wiele kodu, który deweloperzy zapisu obejmuje obsługę wyjątków i jest to również, gdzie najwięcej czasu spędza się w testowaniu. Problem jest bardziej zaangażowany niż pisanie kodu do obsługi błędów. Co się stanie, gdy komputer, na którym działa mikrousługi, nie powiedzie się? Nie tylko trzeba wykryć ten błąd mikrousługi (twardy problem na własną rękę), ale także coś, aby ponownie uruchomić mikrousługę.

Mikrousługi musi być odporne na awarie i być w stanie często ponownie uruchomić na innym komputerze w celu zapewnienia dostępności. Ta odporność również sprowadza się do stanu, który został zapisany w imieniu mikrousługi, gdzie mikrousługi można odzyskać ten stan z i czy mikrousługi można pomyślnie ponownie uruchomić. Innymi słowy, musi istnieć odporność w możliwości obliczeniowej (proces można ponownie uruchomić w dowolnym momencie), a także odporność w stanie lub danych (brak utraty danych, a dane pozostają spójne).

Problemy z odpornością są potęgowane podczas innych scenariuszy, takich jak gdy wystąpią błędy podczas uaktualniania aplikacji. Mikrousługi, pracy z systemem wdrażania, musi określić, czy można kontynuować przejście do nowszej wersji lub zamiast tego przywrócić do poprzedniej wersji, aby zachować stan spójny. Pytania, takie jak czy wystarczająca liczba maszyn są dostępne do dalszego przechodzenia do przodu i jak odzyskać poprzednie wersje mikrousługi muszą być brane pod uwagę. Wymaga to mikrousługi do emitowania informacji o kondycji, dzięki czemu ogólna aplikacja i koordynator może podejmować te decyzje.

Ponadto odporność jest związana z tym, jak muszą zachowywać się systemy oparte na chmurze. Jak wspomniano, system oparty na chmurze musi obejmować awarie i musi próbować automatycznie odzyskać od nich. Na przykład w przypadku awarii sieci lub kontenera aplikacje klienckie lub usługi klienta muszą mieć strategię ponawiania próby wysyłania wiadomości lub ponawiania ponawiania żądań, ponieważ w wielu przypadkach błędy w chmurze są częściowe. [Implementowanie aplikacji odpornych w](../implement-resilient-applications/index.md) tym przewodniku dotyczy sposobu obsługi częściowego błędu. Opisano w nim techniki, takie jak ponownych prób z wykładniczym wycofywaniem lub wzorzec wyłącznika w .NET Core przy użyciu bibliotek, takich jak [Polly](https://github.com/App-vNext/Polly), który oferuje wiele różnych zasad do obsługi tego tematu.

## <a name="health-management-and-diagnostics-in-microservices"></a>Zarządzanie kondycją i diagnostyka w mikrousługach

Może się wydawać oczywiste i często pomijane, ale mikrousługi musi zgłosić jego kondycji i diagnostyki. W przeciwnym razie nie ma wglądu z punktu widzenia operacji. Korelowanie zdarzeń diagnostycznych w zestawie niezależnych usług i radzenie sobie z pochyleniami zegara maszynowego, aby zrozumieć kolejność zdarzeń, jest wyzwaniem. W ten sam sposób, że interakcji z mikrousług za uzgodnione protokoły i formaty danych, istnieje potrzeba standaryzacji w jaki sposób rejestrowania kondycji i diagnostycznych zdarzeń, które ostatecznie kończy się w magazynie zdarzeń do wykonywania zapytań i wyświetlania. W podejściu mikrousług jest kluczem, że różne zespoły zgadzają się na jeden format rejestrowania. Musi istnieć spójne podejście do wyświetlania zdarzeń diagnostycznych w aplikacji.

### <a name="health-checks"></a>Kontrole kondycji

Zdrowie różni się od diagnostyki. Kondycja dotyczy mikrousługi raportowania jego bieżącego stanu do podjęcia odpowiednich działań. Dobrym przykładem jest praca z mechanizmami uaktualniania i wdrażania w celu utrzymania dostępności. Mimo że usługa może być obecnie w złej kondycji z powodu awarii procesu lub ponownego uruchomienia komputera, usługa może nadal działać. Ostatnią rzeczą, której potrzebujesz, jest pogorszyć to, wykonując uaktualnienie. Najlepszym rozwiązaniem jest najpierw przeprowadzenie badania lub zezwolenie na odzyskanie mikrousługi. Zdarzenia zdrowotne z mikrousługi pomagają nam podejmować świadome decyzje i w efekcie pomagać w tworzeniu usług samonaprawiających się.

W [implementowaniu kontroli kondycji w sekcji ASP.NET usług podstawowych](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) w tym przewodniku wyjaśniono, jak używać nowej biblioteki HealthChecks ASP.NET w mikrousługach, aby mogli zgłaszać swój stan do usługi monitorowania w celu podjęcia odpowiednich działań.

Masz również możliwość korzystania z doskonałej biblioteki open-source o nazwie Beat Pulse, dostępnej w [githubie](https://github.com/Xabaril/BeatPulse) i jako [pakiet NuGet.](https://www.nuget.org/packages/BeatPulse/) Ta biblioteka wykonuje również kontrole kondycji, z niespodzianką, obsługuje dwa rodzaje kontroli:

- **Żywotność:** Sprawdza, czy mikrousługi jest aktywne, oznacza to, że jest w stanie akceptować żądania i odpowiadać.
- **Gotowość:** Sprawdza, czy zależności mikrousługi (baza danych, usługi kolejki itp.) są gotowe, więc mikrousługa może wykonywać to, co ma robić.

### <a name="using-diagnostics-and-logs-event-streams"></a>Korzystanie ze strumieni zdarzeń diagnostyki i dzienników

Dzienniki zawierają informacje o sposobie działania aplikacji lub usługi, w tym wyjątki, ostrzeżenia i proste komunikaty informacyjne. Zazwyczaj każdy dziennik jest w formacie tekstowym z jednym wierszem na zdarzenie, chociaż wyjątki często pokazują śledzenia stosu w wielu wierszach.

W monolitycznych aplikacjach opartych na serwerze można po prostu zapisywać dzienniki do pliku na dysku (plik dziennika), a następnie analizować je za pomocą dowolnego narzędzia. Ponieważ wykonywanie aplikacji jest ograniczona do stałego serwera lub maszyny Wirtualnej, zazwyczaj nie jest zbyt skomplikowane, aby analizować przepływ zdarzeń. Jednak w aplikacji rozproszonej, gdzie wiele usług są wykonywane w wielu węzłach w klastrze koordynatora, jest w stanie skorelować zdarzenia rozproszone jest wyzwaniem.

Aplikacja oparta na mikrousługach nie należy próbować przechowywać strumienia danych wyjściowych zdarzeń lub plików dziennika przez siebie, a nawet próbować zarządzać routingiem zdarzeń do centralnego miejsca. Powinien być przezroczysty, co oznacza, że każdy proces powinien po prostu napisać strumień zdarzeń do standardowego danych wyjściowych, które pod nim będą zbierane przez infrastrukturę środowiska wykonywania, w której jest uruchomiona. Przykładem tych routerów strumienia zdarzeń jest [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), który zbiera strumienie zdarzeń z wielu źródeł i publikuje je w systemach wyjściowych. Mogą one obejmować proste standardowe dane wyjściowe dla środowiska programistycznego lub systemów w chmurze, takich jak [Azure Monitor](https://azure.microsoft.com/services/monitor//) i [Diagnostyka platformy Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostics-extension-overview). Istnieją również dobre platformy analizy dzienników innych firm i narzędzia, które mogą wyszukiwać, ostrzegać, raportować i monitorować dzienniki, nawet w czasie rzeczywistym, takie jak [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orkiestratorzy zarządzający informacjami o stanie zdrowia i diagnostyce

Podczas tworzenia aplikacji opartej na mikrousługach należy radzić sobie ze złożonością. Oczywiście pojedyncza mikrousługa jest prosta do czynienia z, ale dziesiątki lub setki typów i tysiące wystąpień mikrousług jest złożonym problemem. Nie chodzi tylko o tworzenie architektury mikrousług — potrzebujesz również wysokiej dostępności, adresowalności, odporności, kondycji i diagnostyki, jeśli zamierzasz mieć stabilny i spoistowy system.

![Diagram klastrów dostarczających platformę pomocy technicznej dla mikrousług.](./media/resilient-high-availability-microservices/microservice-platform.png)

**Rysunek 4-22**. Platforma mikrousług ma podstawowe znaczenie dla zarządzania kondycją aplikacji

Złożone problemy przedstawione na rysunku 4-22 są bardzo trudne do rozwiązania samodzielnie. Zespoły programistyczne powinny koncentrować się na rozwiązywaniu problemów biznesowych i tworzeniu aplikacji niestandardowych za pomocą metod opartych na mikrousługach. Nie powinny one koncentrować się na rozwiązywaniu złożonych problemów infrastrukturalnych; jeśli tak, koszt dowolnej aplikacji opartej na mikrousługach będzie ogromny. W związku z tym istnieją platformy zorientowane na mikrousługi, określane jako koordynatorów lub klastrów mikrousług, które próbują rozwiązać trudne problemy tworzenia i uruchamiania usługi i efektywnego korzystania z zasobów infrastruktury. Zmniejsza to złożoność tworzenia aplikacji, które używają podejścia mikrousług.

Różne koordynatorów może brzmieć podobnie, ale diagnostyki i kontroli kondycji oferowanych przez każdego z nich różnią się w funkcji i stanu dojrzałości, czasami w zależności od platformy systemu operacyjnego, jak wyjaśniono w następnej sekcji.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Aplikacja dwunastoczynnikowa XI. Dzienniki: Traktuj dzienniki jako strumienie zdarzeń** \
  <https://12factor.net/logs>

- **Biblioteka przepływu zdarzeń diagnostycznych firmy Microsoft** Reppo Usługi GitHub. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Co to jest diagnostyka platformy Azure** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Łączenie komputerów z systemem Windows z usługą Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Rejestrowanie tego, co masz na myśli: Korzystanie z bloku aplikacji rejestrowania semantycznego** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk (Splunk)** Oficjalna strona internetowa. \
  <https://www.splunk.com/>

- **Klasa źródła zdarzeń** Interfejs API dla śledzenia zdarzeń dla systemu Windows (ETW) \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Poprzedni](microservice-based-composite-ui-shape-layout.md)
>[następny](scalable-available-multi-container-microservice-applications.md)
