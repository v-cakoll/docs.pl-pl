---
title: Odporność i wysoka dostępność w ramach mikrousług
description: Mikrousługi muszą być zaprojektowane tak, aby wytrzymywały przejściowe awarie sieci i zależności, które muszą być odporne na uzyskanie wysokiej dostępności.
ms.date: 09/20/2018
ms.openlocfilehash: 28f8b124cd59b2c3d621267cb437872af42c9ea8
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988924"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Odporność i wysoka dostępność w ramach mikrousług

Radzenie sobie z nieoczekiwanymi awariami jest jednym z najtrudniejszych problemów do rozwiązania, zwłaszcza w systemie rozproszonym. Wiele kodu, który piszą deweloperzy obejmuje obsługę wyjątków i jest to również, gdzie najwięcej czasu spędza się w testowaniu. Problem jest bardziej zaangażowany niż pisanie kodu do obsługi błędów. Co się stanie, gdy komputer, na którym jest uruchomiona mikrousługa, nie powiedzie się? Nie tylko trzeba wykryć ten błąd mikrousługi (problem twardy na własną), ale także trzeba coś, aby ponownie uruchomić mikrousługi.

Mikrousługi musi być odporne na awarie i mieć możliwość ponownego uruchamiania często na innym komputerze w celu zapewnienia dostępności. Ta odporność również sprowadza się do stanu, który został zapisany w imieniu mikrousługi, gdzie mikrousługi można odzyskać ten stan z i czy mikrousługi można uruchomić pomyślnie. Innymi słowy musi być odporność w możliwości obliczeniowych (proces można ponownie uruchomić w dowolnym momencie), a także odporność w stanie lub danych (brak utraty danych, a dane pozostają spójne).

Problemy z odpornością są potęgowane podczas innych scenariuszy, takich jak gdy występują błędy podczas uaktualniania aplikacji. Mikrousługi, pracy z systemem wdrażania, musi określić, czy można kontynuować przejście do przodu do nowszej wersji lub zamiast tego wycofać do poprzedniej wersji, aby zachować spójny stan. Pytania, takie jak czy dostępnych jest wystarczająca liczba komputerów, aby kontynuować postęp do przodu i jak odzyskać poprzednie wersje mikrousługi, należy wziąć pod uwagę. Wymaga to mikrousługi do emitowania informacji o kondycji, dzięki czemu ogólna aplikacja i koordynator może podejmować te decyzje.

Ponadto odporność jest związana z zachowaniem systemów opartych na chmurze. Jak wspomniano, system oparty na chmurze musi uwzględniać błędy i musi próbować automatycznie odzyskać od nich. Na przykład w przypadku awarii sieci lub kontenera aplikacje klienckie lub usługi klienckie muszą mieć strategię ponowiania prób wysyłania wiadomości lub ponawiania prób żądania, ponieważ w wielu przypadkach błędy w chmurze są częściowe. Sekcja [Implementowanie aplikacji odpornych](../implement-resilient-applications/index.md) w tym przewodniku dotyczy sposobu obsługi częściowego błędu. Opisano w nim techniki, takie jak ponownych prób z wykładniczym wycofywania lub wzorca wyłącznika w .NET Core przy użyciu bibliotek, takich jak [Polly](https://github.com/App-vNext/Polly), który oferuje wiele różnych zasad do obsługi tego tematu.

## <a name="health-management-and-diagnostics-in-microservices"></a>Zarządzanie zdrowiem i diagnostyka w mikrousługach

Może się wydawać oczywiste i często pomijane, ale mikrousługi musi zgłosić jego kondycji i diagnostyki. W przeciwnym razie istnieje mały wgląd z punktu widzenia operacji. Korelowanie zdarzeń diagnostycznych w ramach zestawu niezależnych usług i radzenie sobie z przekrzywieniami zegara maszynowego w celu uzyskania sensu kolejności zdarzeń jest wyzwaniem. W ten sam sposób, w jaki wchodzisz w interakcję z mikrousługą za pomocą uzgodnionych protokołów i formatów danych, istnieje potrzeba standaryzacji w sposobie rejestrowania zdarzeń kondycji i diagnostyki, które ostatecznie kończą się w magazynie zdarzeń do wykonywania zapytań i wyświetlania. W podejściu mikrousług jest kluczem, że różne zespoły zgadzają się na pojedynczy format rejestrowania. Musi istnieć spójne podejście do wyświetlania zdarzeń diagnostycznych w aplikacji.

### <a name="health-checks"></a>Kontrole kondycji

Zdrowie różni się od diagnostyki. Kondycja jest o mikrousługi raportowania jego bieżącego stanu do podjęcia odpowiednich działań. Dobrym przykładem jest praca z mechanizmami uaktualniania i wdrażania w celu utrzymania dostępności. Chociaż usługa może być obecnie w złej kondycji z powodu awarii procesu lub ponownego uruchomienia komputera, usługa może nadal działać. Ostatnią rzeczą, której potrzebujesz, jest, aby to pogorszyć, wykonując uaktualnienie. Najlepszym rozwiązaniem jest najpierw wykonać badanie lub dać czas na odzyskanie mikrousługi. Zdarzenia dotyczące kondycji z mikrousługi pomagają nam podejmować świadome decyzje, a w efekcie pomagają tworzyć usługi samoleczenia.

W [implementacji kontroli kondycji w ASP.NET podstawowych usług](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) w tym przewodniku wyjaśniamy, jak używać nowej biblioteki ASP.NET HealthChecks w mikrousługach, aby mogli zgłaszać swój stan do usługi monitorowania w celu podjęcia odpowiednich działań.

Masz również możliwość korzystania z doskonałej biblioteki open-source o nazwie Beat Pulse, dostępnej na [GitHub](https://github.com/Xabaril/BeatPulse) i jako [pakiet NuGet](https://www.nuget.org/packages/BeatPulse/). Ta biblioteka wykonuje również kontrole kondycji, z niespodzianką, obsługuje dwa rodzaje kontroli:

- **Żywotność:** Sprawdza, czy mikrousługa jest żywa, to znaczy, jeśli jest w stanie zaakceptować żądania i odpowiedzieć.
- **Gotowość:** Sprawdza, czy zależności mikrousługi (baza danych, usługi kolejki, itp.) są gotowe, więc mikrousługi można zrobić to, co ma zrobić.

### <a name="using-diagnostics-and-logs-event-streams"></a>Korzystanie z diagnostyki i dzienników strumieni zdarzeń

Dzienniki zawierają informacje o tym, jak aplikacja lub usługa jest uruchomiona, w tym wyjątki, ostrzeżenia i proste komunikaty informacyjne. Zazwyczaj każdy dziennik jest w formacie tekstowym z jednego wiersza na zdarzenie, chociaż wyjątki również często pokazują ślad stosu w wielu wierszach.

W monolitycznych aplikacjach serwerowych można po prostu zapisywać dzienniki do pliku na dysku (plik dziennika), a następnie analizować je za pomocą dowolnego narzędzia. Ponieważ wykonanie aplikacji jest ograniczone do serwera stałego lub maszyny Wirtualnej, zazwyczaj nie jest zbyt skomplikowane, aby analizować przepływ zdarzeń. Jednak w rozproszonej aplikacji, gdzie wiele usług są wykonywane w wielu węzłach w klastrze orchestrator, jest w stanie skorelować rozproszone zdarzenia jest wyzwaniem.

Aplikacja oparta na mikrousługach nie należy próbować przechowywać strumienia wyjściowego zdarzeń lub plików dziennika przez siebie, a nawet nie próbować zarządzać routingu zdarzeń do centralnego miejsca. Powinien być przezroczysty, co oznacza, że każdy proces powinien po prostu zapisać swój strumień zdarzeń do standardowego wyjścia, które poniżej będą zbierane przez infrastrukturę środowiska wykonywania, w którym jest uruchomiona. Przykładem tych routerów strumienia zdarzeń jest [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), który zbiera strumienie zdarzeń z wielu źródeł i publikuje je w systemach wyjściowych. Mogą one obejmować proste standardowe dane wyjściowe dla środowiska programistycznego lub systemów chmurowych, takich jak [Azure Monitor](https://azure.microsoft.com/services/monitor//) i [Diagnostyka Azure.](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostics-extension-overview) Istnieją również dobre platformy analizy dzienników innych firm i narzędzia, które mogą wyszukiwać, alarmować, raportować i monitorować dzienniki, nawet w czasie rzeczywistym, takie jak [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Koordynatorzy zarządzający informacjami o kondycji i diagnostyce

Podczas tworzenia aplikacji opartej na mikrousługach, należy radzić sobie ze złożonością. Oczywiście pojedyncza mikrousługa jest prosta do rozwiązania, ale dziesiątki lub setki typów i tysiące wystąpień mikrousług jest złożonym problemem. Nie chodzi tylko o tworzenie architektury mikrousług — potrzebujesz również wysokiej dostępności, adresowalności, odporności, kondycji i diagnostyki, jeśli zamierzasz mieć stabilny i spójny system.

![Diagram klastrów dostarczających platformę pomocy technicznej dla mikrousług.](./media/resilient-high-availability-microservices/microservice-platform.png)

**Rysunek 4-22**. Platforma mikrousług ma podstawowe znaczenie dla zarządzania kondycją aplikacji

Złożone problemy pokazane na rysunku 4-22 są bardzo trudne do rozwiązania samodzielnie. Zespoły programistyczne powinny skupić się na rozwiązywaniu problemów biznesowych i tworzeniu aplikacji niestandardowych za pomocą metod opartych na mikrousługach. Nie powinny one koncentrować się na rozwiązywaniu złożonych problemów infrastrukturalnych; jeśli tak, koszt dowolnej aplikacji opartej na mikrousługach będzie ogromny. W związku z tym istnieją platformy zorientowane na mikrousługi, określane jako orchestrators lub klastrów mikrousług, które próbują rozwiązać trudne problemy tworzenia i uruchamiania usługi i efektywnego korzystania z zasobów infrastruktury. Zmniejsza to złożoność tworzenia aplikacji, które używają podejścia mikrousług.

Różne orchestrators może brzmieć podobnie, ale diagnostyki i kontroli kondycji oferowanych przez każdego z nich różnią się funkcje i stan dojrzałości, czasami w zależności od platformy systemu operacyjnego, jak wyjaśniono w następnej sekcji.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Aplikacja Dwunastocewnikowa. Dzienniki: Traktuj dzienniki jako strumienie zdarzeń** \
  <https://12factor.net/logs>

- **Biblioteka przepływów zdarzeń diagnostycznych firmy Microsoft** Repozytorium GitHub. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Co to jest diagnostyka platformy Azure** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Łączenie komputerów z systemem Windows z usługą Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Rejestrowanie, co masz na myśli: korzystanie z bloku aplikacji rejestrowania semantycznego** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk (Splunk)** Oficjalna strona. \
  <https://www.splunk.com/>

- **Klasa EventSource** Interfejs API śledzenia zdarzeń dla systemu Windows (ETW) \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Poprzedni](microservice-based-composite-ui-shape-layout.md)
>[następny](scalable-available-multi-container-microservice-applications.md)
