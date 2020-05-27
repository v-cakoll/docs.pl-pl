---
title: Azure Monitor
description: Korzystanie z Azure Monitor w celu uzyskania wglądu w system działa.
ms.date: 05/13/2020
ms.openlocfilehash: e3ff673c63ecbc380cb8b74ae54065a091882d7b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614269"
---
# <a name="azure-monitor"></a>Azure Monitor

Żaden inny dostawca chmury nie jest gotowy do monitorowania aplikacji w chmurze, który znajduje się na platformie Azure. Azure Monitor to nazwa parasola kolekcji narzędzi zaprojektowanych w celu zapewnienia wglądu w stan systemu, szczegółowych informacji o wszelkich problemach i optymalizacji aplikacji.

![Azure Monitor, kolekcja służąca do uzyskiwania wglądu w sposób działania aplikacji natywnej w chmurze. ](./media/azure-monitor.png)
 **Rysunek 7-12**. Azure Monitor, kolekcja służąca do uzyskiwania wglądu w sposób działania aplikacji natywnej w chmurze.

## <a name="gathering-logs-and-metrics"></a>Zbieranie dzienników i metryk

Pierwszym krokiem w dowolnym rozwiązaniu monitorowania jest gromadzenie możliwie największej ilości danych. Im więcej danych, które można zebrać, tym dokładniejsze informacje, które można uzyskać. Systemy Instrumentacji są tradycyjnie trudne. Simple Network Management Protocol (SNMP) był standardowym protokołem do zbierania informacji na poziomie komputera, ale wymagało dużej wiedzy i konfiguracji. Na szczęście większość tej pracy twardej została wyeliminowana, ponieważ najczęstsze metryki są zbierane automatycznie przez Azure Monitor.

Metryki i zdarzenia na poziomie aplikacji nie są możliwe do automatycznego przystąpienia, ponieważ są specyficzne dla wdrażanej aplikacji. Aby zebrać te metryki, [dostępne są zestawy SDK i interfejsy API](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) służące do bezpośredniego zgłaszania takich informacji, na przykład gdy klient zarejestruje lub ukończy zamówienie. Wyjątki mogą być również przechwytywane i raportowane z powrotem do Azure Monitor za pośrednictwem Application Insights. Zestawy SDK obsługują większość języków znalezionych w natywnych aplikacjach w chmurze, takich jak go, Python, JavaScript i .NET.

Ostatecznym celem zebrania informacji o stanie aplikacji jest upewnienie się, że użytkownicy końcowi mają dobre doświadczenie. Jaki lepszy sposób, aby stwierdzić, czy użytkownicy napotykają problemy niż [w przypadku testów sieci Web](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)? Te testy mogą być proste jako polecenie ping dla witryny internetowej z lokalizacji na całym świecie lub w przypadku, gdy agenci są zalogować się do lokacji i symulują akcje użytkownika.

## <a name="reporting-data"></a>Dane raportowania

Gromadzone dane mogą być przetwarzane, podsumowywane i kreślone na wykresach, co umożliwia użytkownikom natychmiastowe wyświetlanie w przypadku wystąpienia problemów. Te wykresy można zbierać do pulpitów nawigacyjnych lub do skoroszytów, a raport wielostronicowy umożliwiający wyświetlenie historii niektórych aspektów systemu.

Nie będzie można ukończyć nowoczesnej aplikacji bez konieczności sztucznej analizy ani uczenia maszynowego. W tym celu dane [mogą być przesyłane](https://www.youtube.com/watch?v=Cuza-I1g9tw) do różnych narzędzi uczenia maszynowego na platformie Azure, aby umożliwić wyodrębnienie trendów i informacji, które w przeciwnym razie byłyby ukryte.

Application Insights zapewnia zaawansowany język zapytań o nazwie Kusto, który może służyć do znajdowania rekordów, podsumowywania ich, a nawet wykresów wykresu. Na przykład to zapytanie zlokalizuje wszystkie rekordy w miesiącu z listopada 2007, pogrupuj je według stanu i Wykreśl 10 pierwszych jako wykres kołowy.

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

![Wynik Application Insights ](./media/azure-monitor.png)
 **rysunku 7-13**. Wynik zapytania Application Insights.

Istnieje [plac zabaw do eksperymentowania z](https://dataexplorer.azure.com/clusters/help/databases/Samples) zapytaniami Kusto, które są fantastycznie miejsce na godzinę lub dwa. Odczytywanie [przykładowych zapytań](https://docs.microsoft.com/azure/kusto/query/samples) może być również instrukcją.

## <a name="dashboards"></a>Pulpity nawigacyjne

Istnieje kilka różnych technologii pulpitu nawigacyjnego, które mogą być używane do prezentowania informacji z Azure Monitor. Prawdopodobnie najprostszym sposobem jest tylko uruchomienie zapytań w Application Insights i [wykreślenie danych na wykresie](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards).

![Przykład Application Insights wykresów osadzonych na głównym rysunku pulpitu nawigacyjnego platformy Azure ](./media/azure-monitor.png)
 **7-14**. Przykład Application Insights wykresów osadzonych na głównym pulpicie nawigacyjnym platformy Azure.

Te wykresy można następnie osadzić w Azure Portal w odpowiedni sposób przy użyciu funkcji pulpitu nawigacyjnego. Dla użytkowników mających dokładniejsze wymagania, takie jak możliwość przechodzenia do kilku warstw danych, Azure Monitor dane są dostępne do [Power BI](https://powerbi.microsoft.com/). Power BI to wiodąca w branży Klasa korporacyjna, Narzędzie analizy biznesowej, które umożliwia agregowanie danych z wielu różnych źródeł danych.

![Przykład Power BI pulpitu nawigacyjnego ](./media/azure-monitor.png)
 **7-15**. Przykład Power BI pulpitu nawigacyjnego.

## <a name="alerts"></a>Alerty

Czasami posiadanie pulpitów nawigacyjnych danych jest niewystarczające. Jeśli nikt nie będzie w stanie obejrzeć pulpitów nawigacyjnych, może to potrwać kilka godzin, zanim problem zostanie rozwiązany, a nawet wykryty. W tym celu Azure Monitor również zawiera pierwsze rozwiązanie do tworzenia [alertów](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview). Alerty mogą być wyzwalane przez szeroki zakres warunków, w tym:

- Wartości metryk
- Zapytania przeszukiwania dzienników
- Zdarzenia dziennika aktywności
- Kondycja podstawowej platformy Azure
- Testy dostępności witryny sieci Web

Po wyzwoleniu alerty mogą wykonywać wiele różnych zadań. Po stronie prostej alerty mogą po prostu wysłać powiadomienie e-mail do listy adresowej lub wiadomości tekstowej do osoby. Bardziej powiązane alerty mogą wyzwolić przepływ pracy w narzędziu, takim jak usługi PagerDuty, który ma świadomość, kto jest w wywołaniu dla określonej aplikacji. Alerty mogą wyzwalać akcje w [Microsoft Flow](https://flow.microsoft.com/) odblokowywanie w bliskich nieograniczonych możliwościach dla przepływów pracy.

W miarę identyfikowania typowych przyczyn alertów można rozszerzyć alerty z szczegółowymi przyczynami alertów i czynnościami, które należy podjąć w celu ich rozwiązania. Wysoce dojrzałe wdrożenia aplikacji natywnych w chmurze mogą zrezygnować z wykonywania zadań samonaprawiania, które wykonują działania, takie jak usuwanie węzłów zakończonych niepowodzeniem z zestawu skalowania lub wyzwalanie działania skalowania automatycznego. Na koniec nie jest już konieczne wznawianie pracy w ramach usługi –: 00, aby rozwiązać problem związany z witryną na żywo, ponieważ system będzie mógł dopasować się do co najmniej Limp, dopóki ktoś się nie dotrze do następnego dnia.

Azure Monitor automatycznie wykorzystuje Uczenie maszynowe do zrozumienia normalnych parametrów operacyjnych wdrożonych aplikacji. Dzięki temu można wykryć usługi, które działają poza ich normalnymi parametrami. Na przykład typowy ruch w dniu tygodnia w witrynie może wynosić 10 000 żądań na minutę. A następnie w danym tygodniu nagle liczba żądań trafi o wysoce nietypowe żądania 20 000 na minutę. [Inteligentne wykrywanie](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) będzie zauważyć takie odróżnienie od normy i wyzwolenie alertu. W tym samym czasie analiza trendu jest na tyle inteligentna, aby uniknąć zapłonu fałszywych wartości dodatnich, gdy oczekiwane jest obciążenie ruchem.

## <a name="references"></a>Dokumentacja

- [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Poprzedni](monitoring-azure-kubernetes.md) 
> [Dalej](identity.md)
