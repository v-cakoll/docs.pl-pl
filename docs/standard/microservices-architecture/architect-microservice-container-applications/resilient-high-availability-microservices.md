---
title: Odporność i wysoka dostępność w ramach mikrousług
description: Mikrousługi mają być tak zaprojektowana, radzić sobie ze przejściowe problemy z siecią i błędów zależności, które muszą być odporne na błędy w celu uzyskania wysokiej dostępności.
ms.date: 09/20/2018
ms.openlocfilehash: bb1bef0c9cc08e43aed80a29effe89587fb296f6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639936"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Odporność i wysoka dostępność w ramach mikrousług

Zajmowanie się nieoczekiwanych awarii jest jednym z najtrudniejszych problemów do rozwiązania, szczególnie w rozproszonym systemie. Obejmuje większość kodu, który napisać deweloperów, obsługa wyjątków i jest to również gdzie najlepiej jest zużywany czas podczas testowania. Problem polega na bardziej skomplikowane niż pisanie kodu w celu obsługi błędów. Co się stanie, gdy maszyna, na którym jest uruchomione mikrousługa nie powiedzie się? Nie tylko potrzebne wykryć ten błąd mikrousługi (twardego problem samodzielnie), ale należy również coś o ponowne uruchomienie usługi mikrousług.

Mikrousługi wymaga, aby była odporna na awarie i mieć możliwość ponownego uruchomienia często na innej maszynie dostępności. Odporność to również sprowadza się do stanu, który został zapisany w imieniu mikrousług, gdzie mikrousługi można odzyskać tego stanu z, a także czy mikrousługi można pomyślnie uruchomić ponownie. Innymi słowy musi istnieć odporności w możliwości obliczeniowych (ten proces może ponownie w dowolnym momencie) oraz odporności w stanie lub dane (bez utraty danych i dane pozostają spójne).

Problemy odporność jest rozliczana w innych scenariuszach, takich jak kiedy występują błędy podczas uaktualniania aplikacji. Mikrousłudze oraz pracy z systemem wdrażania musi ustalić, czy może on nadal przejść od razu do nowszej wersji lub zamiast niego wrócić do poprzedniej wersji do utrzymania spójnego stanu. Pytania, takie jak czy maszyn wystarcza są dostępne do zachowania przenoszenie do przodu i sposób odzyskać poprzednie wersje mikrousługi należy wziąć pod uwagę. Wymaga to mikrousług emitowanie informacji o kondycji, aby cała aplikacja i orchestrator można podejmowanie tych decyzji.

Ponadto dotyczące odporności systemów jak oparte na chmurze musi zachowywać się. Jak wspomniano wcześniej, oparte na chmurze system musi wykorzystywać błędów i będą musieli spróbować automatycznie odzyskiwać po nich sprawność. Na przykład w przypadku awarii sieci lub kontenera, aplikacje klienckie lub usług klienta musi mieć strategii, aby ponowić próbę wysyłanie wiadomości lub aby ponowić próbę żądania, ponieważ w wielu przypadkach są częściowej awarii w chmurze. [Implementowanie aplikacji odpornych na błędy](../implement-resilient-applications/index.md) sekcji, w tym przewodniku omówiono sposób obsługi częściowych niepowodzeń. Opisano w nim technik, takich jak ponawiają próby z wykorzystaniem wykładniczego wycofywania lub wzorzec wyłącznika w programie .NET Core przy użyciu bibliotek, takich jak [Polly](https://github.com/App-vNext/Polly), które oferuje szerokiej gamy zasad w celu obsługi tego tematu.

## <a name="health-management-and-diagnostics-in-microservices"></a>Zarządzanie stanem zdrowia i diagnostyki w mikrousługach

Może wydawać się oczywiste, jest często pomijane, ale mikrousługi należy zgłosić, jego kondycja i Diagnostyka. W przeciwnym razie jest mały wgląd z perspektywy operacji. Korelowanie zdarzeń diagnostycznych na zestaw niezależnych usług i korzystające z niesymetryczności zegara komputera rozsądnie kolejność zdarzeń jest trudne. W ten sam sposób, że możesz korzystać z mikrousług za pośrednictwem protokołów uzgodnionego i formatów danych istnieje potrzeba normalizacji w sposób kondycji i zdarzenia diagnostyczne, które ostatecznie znajdą się w magazynie zdarzeń do wykonywania zapytań i wyświetlania dziennika. W podejściu z mikrousług go ma klucza różne zespoły dojdą do Porozumienia w postaci pojedynczego logowania. Musi istnieć spójnego podejścia do wyświetlania zdarzeń diagnostycznych w aplikacji.

### <a name="health-checks"></a>Kontrole kondycji

Kondycja różni się od diagnostyki. Kondycja jest o mikrousługach raportowania swojego bieżącego stanu, aby podjąć odpowiednie działania. Dobrym przykładem jest praca z mechanizmów uaktualnieniu i wdrożeniu w celu zapewnienia dostępności. Mimo, że usługa może obecnie będącą w złej kondycji ze względu na awarię procesu lub ponowne uruchomienie komputera, usługi może nadal działać. Ostatnią czynnością, jaką potrzebne jest zapewnienie to niższa, wykonując uaktualnienie. Najlepszym rozwiązaniem jest w celu badania lub poczekaj na mikrousługach odzyskać. Zdarzenia dotyczące kondycji z mikrousługi pomagają nam podejmowanie świadomych decyzji, a w efekcie pomagają stworzyć samonaprawiania usług.

W [Implementowanie kondycji sprawdza, czy w programie ASP.NET Core services](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) sekcji tego przewodnika firma Microsoft wyjaśniają jak używać nowej biblioteki ASP.NET HealthChecks w mikrousługi, więc zgłaszają stanu do monitorowania usługi i podejmij odpowiednie Akcje.

Istnieje również możliwość korzystania z doskonałą biblioteki typu open source o nazwie zapewniała Pulse, dostępne na [GitHub](https://github.com/Xabaril/BeatPulse) i [pakietu NuGet](https://www.nuget.org/packages/BeatPulse/). Ta biblioteka jest również kontrole kondycji, za pomocą akcentem, obsługiwane są dwa typy kontroli:

- **Żywotności**: Sprawdza, czy mikrousługach podtrzymania połączenia, oznacza to, jeśli będzie to możliwe do akceptowania żądań i odpowiedzi. 
- **Gotowość**: Sprawdza, czy mikrousług zależności (bazy danych, usługi kolejki, itp.) czy samodzielnie wszystko będzie gotowe, więc mikrousługi można zrobić, co ma odbywać się zrobić. 

### <a name="using-diagnostics-and-logs-event-streams"></a>Za pomocą strumieni zdarzeń diagnostycznych i dzienniki

Dzienniki zawierają informacje dotyczące sposobu aplikacja lub usługa jest uruchomiona, łącznie z wyjątkami, ostrzeżenia i komunikaty informacyjne proste. Zazwyczaj każdy dziennik jest w formacie tekstowym o jeden wiersz dla każdego zdarzenia, chociaż wyjątki często Pokaż ślad stosu w wielu wierszach.

W monolitycznych aplikacji serwerowych można po prostu zapisują dzienniki w pliku na dysku (plik dziennika), a następnie analizować za pomocą dowolnego narzędzia. Ponieważ wykonanie aplikacji jest ograniczony do stałej server lub maszyny Wirtualnej, zazwyczaj nie jest zbyt złożona, aby analizować przepływu zdarzeń. Jednak w których wielu usług są wykonywane na wielu węzłach w klastrze usługi orchestrator aplikacji rozproszonej, móc skorelować zdarzenia rozproszonej jest trudne.

Aplikacją opartą na mikrousługach powinna nie próbuje zapisać w strumieniu wyjściowym zdarzeń lub logfiles samodzielnie, a nawet spróbuj do zarządzania routingiem zdarzeń w centralnym miejscu. Powinny być przezroczyste, co oznacza, że każdy proces powinien zapisać jej strumienia zdarzeń do wyjścia standardowego, które mają być zbierane przez infrastrukturę środowiska wykonywania gdzie działa pod. Na przykład te routery strumienia zdarzeń [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), który służy do zbierania strumieni zdarzeń z wielu źródeł i publikuje go w danych wyjściowych systemy. Obejmują one proste standardowe dane wyjściowe w środowisku deweloperskim lub systemów w chmurze, takich jak [usługi Azure Monitor](https://azure.microsoft.com/services/monitor//) i [diagnostyki Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostics-extension-overview). Dostępne są także dobry dziennika firm analizy platform i narzędzi, które można wyszukiwać, alertów i raportów, i dzienniki monitora, nawet w czasie rzeczywistym, takich jak [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Zarządzanie informacjami o Kondycja i Diagnostyka koordynatorów

Podczas tworzenia aplikacji opartych na mikrousługach, należy radzenia sobie z złożoności. Oczywiście pojedynczych mikrousług jest prosty do czynienia z dziesiątek, jak i setek typów oraz tysięcy wystąpień mikrousług jest jednak złożony problem. Nie jest niemal tworzenia architektury mikrousług, należy również wysoką dostępność, adresowanie, odporności, kondycja i Diagnostyka, jeśli użytkownik zamierza umieścić stabilne i spójny system.

![Koordynatorów, podaj to platforma pomocy technicznej do uruchamiania mikrousługi.](./media/image22.png)

**Rysunek 4-22**. To platforma Mikrousług ma zasadnicze znaczenie dla zarządzania stanem aplikacji

Złożone problemy, które przedstawiono w rysunek 4-22 są bardzo trudne rozwiązać samodzielnie. Zespoły deweloperów należy skoncentrować się na rozwiązywaniu problemów biznesowych i tworzących niestandardowe aplikacje za pomocą metod opartych na mikrousługach. Nie należy skoncentrować się na temat rozwiązywania złożonych problemów z infrastrukturą; Jeżeli tak, opłata aplikacji opartych na mikrousługach wyniesie duży. W związku z tym czy platformy opartej na mikrousługach, nazywane koordynatorów lub klastrów mikrousług, w których podejmowana jest próba rozwiązywaniu trudnych problemów, kompilowania i uruchamiania usługi i efektywne używanie zasobów infrastruktury. Pozwala to zmniejszyć złożoność tworzenia aplikacji korzystających z podejścia mikrousług.

Różne koordynatorów może brzmią podobnie, ale dane diagnostyczne i kontrole kondycji oferowanych przez każdą z nich różnią się w funkcjach i stan dojrzałości czasami w zależności od platformy systemu operacyjnego, zgodnie z opisem w następnej sekcji.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **12 Factor aplikacji. XI. Dzienniki: Traktuj dzienniki jako strumieni zdarzeń** \
  <https://12factor.net/logs>

- **Biblioteka programu Microsoft diagnostycznych użyciu struktury EventFlow** repozytorium GitHub. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Co to jest Azure Diagnostics** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Łączenie komputerów Windows do usługi Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Rejestrowanie tym, co oznacza: Za pomocą blok semantycznego rejestrowania aplikacji** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk** oficjalna witryna. \
  <https://www.splunk.com/>

- **EventSource — klasa** interfejsu API dla zdarzenia śledzenia dla Windows (ETW) \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Poprzednie](microservice-based-composite-ui-shape-layout.md)
>[dalej](scalable-available-multi-container-microservice-applications.md)
