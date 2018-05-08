---
title: Odporność i wysokiej dostępności w mikrousług
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Odporność i wysokiej dostępności w mikrousług
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 1cdd938fb53e194a80f0eb3e6bc82ebed271af49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Odporność i wysokiej dostępności w mikrousług

Zajmowanie nieoczekiwanych awarii jest jednym z najtrudniejsze problemy można rozwiązać, szczególnie w rozproszonym systemie. Obejmuje wiele deweloperom pisanie kodu, obsługa wyjątków i jest to również gdzie jest zużywany czas najbardziej podczas testowania. Problem jest bardziej skomplikowane niż pisania kodu do obsługi błędów. Co się stanie, gdy maszyny, na którym jest uruchomiona mikrousługi nie powiodło się? Nie tylko muszą wykryć ten błąd mikrousługi (twarde problem samodzielnie), ale może też być konieczne coś o ponowne uruchomienie programu mikrousługi.

Mikrousługi musi być odporność na awarie i mieć możliwość ponownego uruchomienia często na innym komputerze na potrzeby dostępności. To odporności również zawiera stanu, który został zapisany w imieniu mikrousługi, gdzie mikrousługi można odzyskać tego stanu z, a także czy mikrousługi można pomyślnie uruchomić ponownie. Innymi słowy musi istnieć odporność możliwości obliczeniowych (proces ponownie można w dowolnym momencie) oraz odporność w stanie lub danych (brak utraty danych i dane pozostają spójne).

Problemy odporności są ich w innych scenariuszach, na przykład gdy wystąpią błędy podczas uaktualniania aplikacji. Mikrousługi, Praca w systemie wdrożenia musi ustalić, czy może on nadal przejście do nowszej wersji lub zamiast tego przywrócenie poprzedniej wersji, aby zachować w spójnym stanie. Pytania, takie jak czy maszyn wystarcza są dostępne do zachowania przenoszenie do przodu i jak odzyskać poprzednie wersje mikrousługi należy wziąć pod uwagę. Wymaga to mikrousługi można wyemitować informacji o kondycji, aby ogólną aplikacji i programu orchestrator mogą podjąć decyzje te.

Ponadto dotyczące odporności systemów jak oparte na chmurze musi działać. Jak wspomniano, oparte na chmurze system musi obejmować błędy i spróbuj musi automatycznie odzyskać ich. Na przykład w przypadku awarii sieci lub kontenera, klienta aplikacji lub usług klienta musi mieć strategii, aby ponowić próbę wysyłanie wiadomości lub aby ponowić próbę żądania, ponieważ w wielu przypadkach częściowe są błędy w chmurze. [Implementacja odporność aplikacji](#implementing_resilient_apps) w tym przewodniku omówiono sposób obsługi awarii częściowej. Zawiera opis technik, takich jak ponownych prób z wykładniczego wycofywania lub wzorca wyłącznika w .NET Core za pomocą biblioteki, takich jak [Polly](https://github.com/App-vNext/Polly), które oferuje wielu różnych zasad w celu obsługi tego tematu.

## <a name="health-management-and-diagnostics-in-microservices"></a>Zarządzanie Kondycja i Diagnostyka w mikrousług

Może wydawać się oczywiste i jest często pomijane, ale mikrousługi muszą zgłosić, jego kondycja i Diagnostyka. W przeciwnym razie jest niewiele wglądu z perspektywy operacji. Korelowanie zdarzeń diagnostycznych przez zestaw usług niezależnych i zajmujących maszyny zegara pochyla rozsądnie kolejność zdarzeń jest trudne. W taki sam sposób interakcji z mikrousługi za pośrednictwem protokołów ustalonym i formatów danych ma potrzeby normalizacji w sposób kondycji i zdarzeń diagnostycznych, które ostatecznie kończą w magazynie zdarzeń do badania i wyświetlania dziennika. W podejściu mikrousług jest klucz czy różnych zespołów wyrażanie zgody na format jednego rejestrowania. Musi istnieć jednolity sposób wyświetlania zdarzeń diagnostycznych w aplikacji.

### <a name="health-checks"></a>Sprawdzanie kondycji

Kondycja jest inny niż diagnostyki. Kondycja jest o mikrousługi raportowania swojego bieżącego stanu podjęcia odpowiednich działań. Dobrym przykładem jest praca z uaktualnieniu i wdrożeniu mechanizmów w celu zapewnienia dostępności. Mimo że usługa może obecnie niezdrowy z powodu awarii procesu lub ponowne uruchomienie komputera, usługi może nadal działać. Ostatnim zadaniem, które są potrzebne jest zapewnienie to pogarsza się wraz z wykonując uaktualnienie. Najlepszym rozwiązaniem jest przeprowadzenie dochodzenia lub poczekać na mikrousługi do odzyskania. Zdarzenia kondycji z mikrousługi Pomóż nam podejmowania świadomych decyzji, a w efekcie ułatwić tworzenie usług samonaprawiania.

W Implementowanie kondycji sprawdza w sekcji usług platformy ASP.NET Core tego przewodnika, możemy wyjaśniono, jak używać nowej biblioteki ASP.NET HealthChecks w sieci mikrousług, dlatego zgłaszają stanu do monitorowania usługi podjąć odpowiednie działania.

### <a name="using-diagnostics-and-logs-event-streams"></a>Za pomocą strumieni zdarzeń diagnostycznych i dzienniki

Dzienniki zawierają informacje dotyczące sposobu aplikacja lub usługa jest uruchomiona, łącznie z wyjątkami, ostrzeżenia i komunikaty informacyjne proste. Zazwyczaj każdy dziennik jest w formacie tekstowym o jeden wiersz dla każdego zdarzenia, chociaż często wyjątki Pokaż ślad stosu w wielu liniach.

W przypadku aplikacji serwerowych wbudowanymi można po prostu zapisywanie dzienników do pliku na dysku (pliku dziennika), a następnie analizować przy użyciu dowolnego narzędzia. Ponieważ wykonanie aplikacji jest ograniczony do środka serwera lub maszyny Wirtualnej, zwykle nie jest zbyt złożone, aby przeanalizować przepływu zdarzeń. Jednak w aplikacji rozproszonej, gdzie są wykonywane wiele usług w wielu węzłach w klastrze programu orchestrator, możliwość skorelować zdarzenia rozproszonej jest żądanie.

Aplikacja mikrousługi należy próbuje zapisać w strumieniu wyjściowym zdarzenia lub logfiles samodzielnie, a nawet spróbuj Zarządzanie routingiem zdarzenia, które centralne miejsce. Powinno być przezroczysty, co oznacza, że każdy proces właśnie należy zapisać jego strumienia zdarzeń do wyjścia standardowego, który poniżej zostaną zebrane przez infrastruktura środowiska uruchamiania którym jest uruchomiona. Na przykład z tych routerów strumienia zdarzeń [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), który służy do zbierania strumieni zdarzeń z wielu źródeł i publikuje ją do wyjściowego systemów. Obejmują one proste standardowego wyjścia dla środowiska programowania lub systemy chmur, takich jak [usługi Application Insights](https://azure.microsoft.com/services/application-insights/), [OMS](https://github.com/Azure/diagnostics-eventflow#oms-operations-management-suite) (dla aplikacji lokalnych) i [diagnostyki Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/azure-diagnostics). Istnieją również dobrym dziennika innych firm analizy platform i narzędzi, które można wyszukiwać alertu, raport, i dzienników monitorowania, nawet w czasie rzeczywistym, takich jak [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Zarządzanie informacjami o Kondycja i Diagnostyka orchestrators

Podczas tworzenia aplikacji opartych na mikrousługi należy uwzględniać złożoności. Oczywiście pojedynczego mikrousługi jest prosty na wypadek, ale dziesiątki lub setki typów i tysiące wystąpień mikrousług to złożony problem. Nie jest tylko tworzenie architektury mikrousługi — należy również wysokiej dostępności, adresowanie odporności, kondycja i Diagnostyka, jeśli mają być stabilny i spójny system.

![](./media/image22.png)

**Rysunek 4-22**. Platforma Mikrousługi ma zasadnicze znaczenie dla zarządzania kondycji aplikacji

Złożonych problemów wyświetlany w rysunek 4-22 są bardzo trudne do rozwiązania samodzielnie. Zespoły deweloperów skoncentrować się rozwiązywania problemów biznesowych i tworzenia niestandardowych aplikacji z podejścia mikrousługi. Nie należy skoncentrować się na temat rozwiązywania złożonych problemów z infrastrukturą; Jeśli tak, kosztów dowolnej aplikacji opartej na mikrousługi będzie ogromnych. W związku z tym istnieje zorientowane na mikrousługi platform, określany jako orchestrators lub mikrousługi klastry, które próbują rozwiązania problemów twardych tworzenia i uruchamiania usługi i wydajne użycie zasobów infrastruktury. Powoduje to zmniejszenie złożoności tworzenia aplikacji korzystających z podejścia mikrousług.

Różne orchestrators może dźwiękowej podobne, ale diagnostyki i kontroli kondycji oferowane przez każdego z nich różnią się w funkcji i stan dojrzałości czasami w zależności od platformy systemu operacyjnego, zgodnie z objaśnieniem w następnej sekcji.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Aplikacja Multi-Factor 12. XI. Dzienniki: Traktuje dzienniki jako strumieni zdarzeń**
    [*https://12factor.net/logs*](https://12factor.net/logs)

-   **Biblioteka EventFlow diagnostyczne do firmy Microsoft.** Repozytorium GitHub.

    [*https://github.com/Azure/diagnostics-eventflow*](https://github.com/Azure/diagnostics-eventflow)

-   **Co to jest Azure Diagnostics**
    [*https://docs.microsoft.com/azure/azure-diagnostics*](https://docs.microsoft.com/azure/azure-diagnostics)

-   **Łączenie komputerów z systemem Windows z usługą analizy dzienników na platformie Azure**
    [*https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents*](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents)

-   **Rejestrowanie wykonywanych średniej: Za pomocą bloku semantycznego rejestrowania aplikacji**
    [*https://msdn.microsoft.com/library/dn440729(v=pandp.60).aspx*](https://msdn.microsoft.com/library/dn440729(v=pandp.60).aspx)

-   **Splunk.** Oficjalna witryna.
    [*https://www.splunk.com/*](https://www.splunk.com/)

-   **EventSource — klasa**. Interfejs API dla zdarzenia śledzenia zdarzeń systemu Windows (ETW) [*https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource*](xref:System.Diagnostics.Tracing.EventSource)




>[!div class="step-by-step"]
[Poprzednie] (microservice-based-composite-ui-shape-layout.md) [dalej] (scalable-available-multi-container-microservice-applications.md)
