---
title: Azure Monitor
description: Za pomocą usługi Azure Monitor, aby uzyskać wgląd w systemie jest uruchomiony.
ms.date: 02/05/2020
ms.openlocfilehash: 4e5ddba6c1c13dc65662a7748d4ae3a58a6a6f68
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805629"
---
# <a name="azure-monitor"></a>Azure Monitor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Żaden inny dostawca chmury nie ma tak dojrzałego rozwiązania do monitorowania aplikacji w chmurze, jak to znalezione na platformie Azure. Usługa Azure Monitor to nazwa parasola dla kolekcji narzędzi zaprojektowanych w celu zapewnienia wglądu w stan systemu, wgląd w wszelkie problemy i optymalizację aplikacji.

![Usługa Azure Monitor— kolekcja narzędzi zapewniająca wgląd w działanie aplikacji natywnej dla chmury. ](./media/azure-monitor.png)
 **Rysunek 7-12**. Usługa Azure Monitor— kolekcja narzędzi zapewniająca wgląd w działanie aplikacji natywnej dla chmury.

## <a name="gathering-logs-and-metrics"></a>Zbieranie dzienników i danych

Pierwszym krokiem w każdym rozwiązaniu monitorowania jest zebranie jak największej ilości danych. Im więcej danych można zebrać, tym głębsze informacje, które można uzyskać. Systemy oprzyrządowania tradycyjnie były trudne. Simple Network Management Protocol (SNMP) był złotym standardowym protokołem do zbierania informacji na poziomie maszyny, ale wymagał dużej wiedzy i konfiguracji. Na szczęście wiele z tej ciężkiej pracy zostało wyeliminowane, ponieważ najczęściej spotykane metryki są zbierane automatycznie przez usługę Azure Monitor.

Metryki i zdarzenia poziomu aplikacji nie są możliwe do in instrumentów automatycznie, ponieważ są one specyficzne dla aplikacji wdrażane. Aby zebrać te metryki, istnieją [szesnaszki SDK i interfejsy API dostępne](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) do bezpośredniego zgłaszania takich informacji, takich jak gdy klient rejestruje się lub kończy zamówienie. Wyjątki można również przechwytywane i zgłaszane z powrotem do usługi Azure Monitor za pośrednictwem usługi Application Insights. Pakiety SDK obsługują większość wszystkich języków znalezionych w aplikacjach natywnych w chmurze, w tym w językach Go, Python, JavaScript i .NET.

Ostatecznym celem zbierania informacji o stanie aplikacji jest zapewnienie, że użytkownicy końcowi mają dobre doświadczenia. Czy jest lepszy sposób, aby stwierdzić, czy użytkownicy doświadczają problemów niż robi [poza w testów internetowych?](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability) Testy te mogą być tak proste, jak pingowanie witryny z lokalizacji na całym świecie lub tak zaangażowane, jak posiadanie agentów zalogować się do witryny i symulować działania użytkownika.

## <a name="reporting-data"></a>Dane raportowania

Po zebraniu danych można nimi manipulować, podsumowywać i wykreślać na wykresach, co pozwala użytkownikom natychmiast zobaczyć, kiedy występują problemy. Wykresy te można gromadzić na pulpitach nawigacyjnych lub w skoroszytach , wielostronicowym raporcie zaprojektowanym w celu opowiedzenia o jakimś aspekcie systemu.

Żadna nowoczesna aplikacja nie byłaby kompletna bez sztucznej inteligencji lub uczenia maszynowego. W tym celu dane [mogą być przekazywane](https://www.youtube.com/watch?v=Cuza-I1g9tw) do różnych narzędzi uczenia maszynowego na platformie Azure, aby umożliwić wyodrębnianie trendów i informacji, które w przeciwnym razie byłyby ukryte.

Usługa Application Insights udostępnia zaawansowany język zapytań o nazwie Kusto, który może służyć do znajdowania rekordów, ich podsumowywania, a nawet drukowania wykresów. Na przykład ta kwerenda zlokalizuje wszystkie rekordy w listopadzie 2007 r., pogrupuje je według stanu i wykreśli pierwszą dziesiątkę jako wykres kołowy.

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

![Wynik kwerendy aplikacji](./media/azure-monitor.png)
Insights**Rysunek 7-13**. Wynik kwerendy usługi Application Insights.

Jest plac zabaw do eksperymentowania z zapytaniami [Kusto,](https://dataexplorer.azure.com/clusters/help/databases/Samples) który jest fantastycznym miejscem do spędzenia godziny lub dwóch. Czytanie [przykładowych zapytań](https://docs.microsoft.com/azure/kusto/query/samples) może być również pouczające.

## <a name="dashboards"></a>Pulpity nawigacyjne

Istnieje kilka różnych technologii pulpitu nawigacyjnego, które mogą służyć do powierzchni informacji z usługi Azure Monitor. Być może najprostszym jest po prostu uruchomić kwerendy w usłudze Application Insights i [wykreślić dane na wykresie](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards).

![Przykład wykresów usługi Application Insights osadzonych](./media/azure-monitor.png)
na głównym pulpicie nawigacyjnym platformy Azure**rysunek 7-14**. Przykład wykresów usługi Application Insights osadzonych w głównym pulpicie nawigacyjnym platformy Azure.

Te wykresy można następnie osadzone w witrynie Azure portal właściwego za pomocą funkcji pulpitu nawigacyjnego. Dla użytkowników z bardziej rygorystycznymi wymaganiami, takimi jak możliwość przechodzenia do szczegółów w kilku warstwach danych, dane usługi Azure Monitor są dostępne dla [usługi Power BI.](https://powerbi.microsoft.com/) Usługa Power BI to wiodące w branży narzędzie do analizy biznesowej klasy korporacyjnej, które może agregować dane z wielu różnych źródeł danych.

![Przykładowy pulpit](./media/azure-monitor.png)
nawigacyjny usługi Power BI**Rysunek 7-15**. Przykładowy pulpit nawigacyjny usługi Power BI.

## <a name="alerts"></a>Alerty

Czasami posiadanie pulpitów nawigacyjnych danych jest niewystarczające. Jeśli nikt nie budzi się, aby oglądać pulpity nawigacyjne, może to być jeszcze wiele godzin przed zażenią problem, a nawet wykryte. W tym celu usługa Azure Monitor zapewnia również najwyższej klasy [rozwiązanie do ostrzegania.](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview) Alerty mogą być wyzwalane przez szeroki zakres warunków, w tym:

- Wartości metryk
- Zapytania przeszukiwania dzienników
- Zdarzenia dziennika aktywności
- Kondycja podstawowej platformy Azure
- Testy dostępności witryny sieci Web

Po wyzwoleniu alerty mogą wykonywać wiele różnych zadań. Po prostu alerty mogą po prostu wysłać powiadomienie e-mail na listę mailingową lub wiadomość tekstową do danej osoby. Bardziej zaangażowane alerty mogą wyzwolić przepływ pracy w narzędziu, takim jak PagerDuty, który jest świadomy tego, kto jest na wezwanie dla określonej aplikacji. Alerty mogą wyzwalać akcje w [usłudze Microsoft Flow,](https://flow.microsoft.com/) odblokowując niemal nieograniczone możliwości przepływów pracy.

Ponieważ typowe przyczyny alertów są identyfikowane, alerty można zwiększyć o szczegóły dotyczące typowych przyczyn alertów i kroków, które należy podjąć, aby je rozwiązać. Wysoce dojrzałe wdrożenia aplikacji natywnych dla chmury mogą zdecydować się na rozpoczęcie zadań samonaprawiających się, które wykonują akcje, takie jak usuwanie węzłów, które nie działają, z zestawu skalowania lub wyzwalanie działania skalowania automatycznego. Ostatecznie może nie być już konieczne, aby obudzić się na dyżurze personelu w 2AM, aby rozwiązać problem na żywo miejscu, jak system będzie w stanie dostosować się do kompensacji lub przynajmniej wiotki, aż ktoś przybywa do pracy następnego dnia rano.

Usługa Azure Monitor automatycznie wykorzystuje uczenie maszynowe do zrozumienia normalnych parametrów operacyjnych wdrożonych aplikacji. Dzięki temu można wykryć usługi, które działają poza ich normalnych parametrów. Na przykład typowy ruch w dni powszednie w witrynie może wynosić 10 000 żądań na minutę. A potem, w danym tygodniu, nagle liczba żądań trafia bardzo nietypowe 20 000 żądań na minutę. [Inteligentne wykrywanie](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) zauważy to odchylenie od normy i wyzwoli alert. W tym samym czasie analiza trendu jest wystarczająco inteligentny, aby uniknąć wypalania fałszywych alarmów, gdy oczekuje się obciążenia ruchu.

## <a name="references"></a>Dokumentacja

- [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Poprzedni](monitoring-azure-kubernetes.md)
>[następny](identity.md)
