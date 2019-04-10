---
title: Podgląd zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: 75165df94aa8b508ef85cf970933efb98b9d62ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211400"
---
# <a name="preview-events"></a>Podgląd zdarzeń
Podgląd zdarzeń, tzw. tunelowanie zdarzeń, są zdarzenia trasowane, gdzie kierunek trasy, przybliżone ilości tych danych z katalogu głównego aplikacji do elementu, który spowodował zdarzenie i jest zgłaszana jako źródło danych zdarzenia. Nie wszystkie scenariusze zdarzenie obsługi lub wymagania Podgląd zdarzeń; w tym temacie opisano sytuacje, gdzie Podgląd zdarzeń istnieją, jak aplikacje lub składniki powinny obsługiwać je i przypadkach, gdy tworzenie zdarzenia (wersja zapoznawcza) w niestandardowych składnikami lub klasami jest odpowiednie.  
  
## <a name="preview-events-and-input"></a>Podgląd zdarzeń i danych wejściowych  
 Podczas obsługi zdarzenia ogólnie rzecz biorąc, należy zachować ostrożność w wersji zapoznawczej oznaczanie zdarzenia obsługiwane w przypadku danych. Obsługa zdarzeń (wersja zapoznawcza), w dowolnym elemencie innych niż element, który spowodował jego (elementu, który jest zgłaszany jako źródła danych zdarzeń) efektem nie udostępnia możliwość obsługi zdarzeń, który pochodzi element. Czasami jest to oczekiwany wynik, zwłaszcza, jeśli elementy w danym znajdują się w relacji składania kontrolki.  
  
 Dla zdarzenia wejściowe ściślej mówiąc, Podgląd zdarzeń także udostępniać wystąpień danych zdarzeń równoważne zdarzenia propagacji. Klasy obsługi zdarzenia (wersja zapoznawcza) służy do oznaczania dane wejściowe zdarzenia obsłużony, propagacji obsługi klasy dane wejściowe zdarzenia nie zostaną wywołane. Lub, jeśli używasz wystąpienia obsługi zdarzenia (wersja zapoznawcza) do oznaczenia zdarzeń obsługiwane programy obsługi dla zdarzenia propagacji nie zostaną zazwyczaj wywołane. Funkcje obsługi klas lub wystąpień obsługi można zarejestrowany lub dołączone z opcją do wywołania nawet wtedy, gdy zdarzenie jest oznaczony jako obsługiwany, ale ta technika nie jest używana najczęściej.  
  
 Aby uzyskać więcej informacji na temat obsługi klasy oraz jej Podgląd zdarzeń zobacz [oznaczanie zdarzeń trasowanych jako Handled oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md).  
  
### <a name="working-around-event-suppression-by-controls"></a>Praca wokół pomijanie zdarzenia kontrolki  
 Jeden scenariusz, w którym zdarzenia (wersja zapoznawcza) są często używane dotyczy złożone kontroli obsługi zdarzenia wejściowe. Czasami Tworzenie formantu pomija określone zdarzenie z pochodzących z ich kontroli, być może w celu zastąpienia zdefiniowane przez składnik zdarzeń, który niesie ze sobą informacji zaświadczenie lub aprobatę dokładniejsze zachowanie. Na przykład [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> pomija <xref:System.Windows.UIElement.MouseLeftButtonDown> i <xref:System.Windows.UIElement.MouseRightButtonDown> Propagacja zdarzeń wywołanych przez <xref:System.Windows.Controls.Button> lub jej elementów złożonego na rzecz przechwytywanie myszy i wywoływanie <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń, który zawsze jest wywoływany przez <xref:System.Windows.Controls.Button> sam. Zdarzenia i jego danych nadal będzie wzdłuż trasy, ale ponieważ <xref:System.Windows.Controls.Button> oznacza dane zdarzenia jako <xref:System.Windows.RoutedEventArgs.Handled%2A>, tylko programy obsługi dla zdarzenia, które wyraźnie wskazane, powinny one działać w `handledEventsToo` przypadków są wywoływane.  Jeśli inne elementy do katalogu głównego aplikacji nadal możliwość obsługi zdarzenia pominięte przez formant, zamiast jednego jest dołączenie obsługi w kodzie za pomocą `handledEventsToo` określony jako `true`. Jednak często łatwiejsze techniką jest zmiana routingu kierunku obsługi odpowiadające dane wejściowe zdarzenia (wersja zapoznawcza). Na przykład jeśli formant pomija <xref:System.Windows.UIElement.MouseLeftButtonDown>, spróbować dołączania obsługi dla <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> zamiast tego. Ta technika działa tylko w przypadku elementu base zdarzenia wejściowe takich jak <xref:System.Windows.UIElement.MouseLeftButtonDown>. Te zdarzenia wejściowe używania pary tunelu/bąbelków, wywołania obu zdarzeń i udostępniać dane zdarzenia.  
  
 Każda z tych metod ma efekty uboczne lub ograniczenia. Po stronie obsługi zdarzenia (wersja zapoznawcza) powoduje, że w tym momencie obsługi zdarzenia może wyłączyć programy obsługi, które oczekują, aby obsłużyć zdarzenie propagacji i dlatego nie ograniczenia, zazwyczaj nie jest dobry pomysł, aby oznaczyć zdarzeń obsługiwane, gdy jest nadal na Previ Nowa część trasy. Ograniczenia `handledEventsToo` techniką jest, że nie można określić `handledEventsToo` obsługi w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako atrybutu, należy zarejestrować program obsługi zdarzeń w kodzie po uzyskaniu odwołania do obiektu do elementu, gdzie program obsługi ma zostać dołączony.  
  
## <a name="see-also"></a>Zobacz także

- [Oznaczanie zdarzenia trasowanego jako obsłużonego oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md)
- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
