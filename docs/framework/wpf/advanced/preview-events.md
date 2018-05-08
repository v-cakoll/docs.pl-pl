---
title: Podgląd zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: 2d6c1ab32cb43730af2f935f4bd4405059994c12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="preview-events"></a>Podgląd zdarzeń
Podgląd zdarzeń, znany również jako tunelowania zdarzenia, są kierowane zdarzenia, gdy kierunek trasy przechodzi od katalogu głównego aplikacji na element, który wywołał zdarzenie i został zgłoszony jako źródło danych zdarzenia. Nie wszystkie scenariusze zdarzeń obsługuje ani nie wymaga podglądu zdarzeń. w tym temacie opisano sytuacje, gdy Podgląd zdarzeń istnieje, jak aplikacje i składniki powinna obsługiwać je, a przypadkach, gdy tworzenie podglądu zdarzeń w składnikach niestandardowych lub klasy jest odpowiedni.  
  
## <a name="preview-events-and-input"></a>Podgląd zdarzeń i danych wejściowych  
 Podczas obsługi podglądu zdarzeń ogólnie rzecz biorąc, należy zachować ostrożność oznaczenie zdarzeń obsługi zdarzeń danych. Obsługi zdarzeń w wersji zapoznawczej, w dowolnym elemencie inny niż element, która wywołała ona (element został zgłoszony jako źródła danych zdarzeń) skutkuje nie udostępnia możliwość obsługi zdarzenia, który pochodzi on elementu. Czasami jest to pożądany wynik, zwłaszcza w przypadku, gdy istnieje zagrożona elementów w relacje w składania formantu.  
  
 Dla zdarzenia wejściowe w szczególności Podgląd zdarzeń również udostępniać wystąpień danych zdarzeń równoważne zdarzeń propagacji. Obsługa klasy podglądu zdarzeń służy do oznaczania obsługi zdarzenia wejściowego, propagacji obsługi klasa zdarzeń wejściowych nie zostaną wywołane. Lub, jeśli wystąpienie programu obsługi podglądu zdarzeń służy do oznaczania obsługi zdarzenia, programy obsługi zdarzeń propagacji nie będzie zazwyczaj wywoływana. Programy obsługi klasy lub wystąpienia obsługi można zarejestrowany lub dołączony z opcją wywoływanej nawet wtedy, gdy zdarzenie jest oznaczony jako obsługiwany, ale ta metoda nie jest powszechnie używany.  
  
 Aby uzyskać więcej informacji na temat obsługi klasy i jego powiązań z Podglądu zdarzeń zobacz [oznaczenie kierowane zdarzenia jako Handled i obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
### <a name="working-around-event-suppression-by-controls"></a>Praca wokół pomijanie zdarzeń przez formanty  
 Jest jeden scenariusz, w którym Podgląd zdarzeń są często używane do obsługi sterowania połączone zdarzeń wejściowych. Czasami Tworzenie formantu pomija określone zdarzenie z pochodzących z ich kontroli, być może w celu zastąpienia zdefiniowane przez składnik zdarzeń, który zajmuje więcej informacji lub oznacza więcej określone zachowanie. Na przykład [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> pomija <xref:System.Windows.UIElement.MouseLeftButtonDown> i <xref:System.Windows.UIElement.MouseLeftButtonDown> propagacji zdarzenia generowane przez <xref:System.Windows.Controls.Button> lub jego elementów złożonego na rzecz przechwytywanie myszy i wywoływanie <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które zawsze zostanie wywołane przez <xref:System.Windows.Controls.Button> samej siebie. Zdarzenia i jego danych nadal wzdłuż trasy, ale ponieważ <xref:System.Windows.Controls.Button> oznacza dane zdarzenia jako <xref:System.Windows.RoutedEventArgs.Handled%2A>, tylko programy obsługi dla zdarzenia wskazaną w szczególności powinny one działać w `handledEventsToo` są wywoływane w przypadku.  Jeśli inne elementy do katalogu głównego aplikacji nadal możliwość obsługi zdarzenia pominięte kontroli, co alternatywą jest dołączyć obsługi w kodzie z `handledEventsToo` określony jako `true`. Ale często jest prostsze technika zmienić kierunek routingu obsługi odpowiadające Podgląd zdarzeń wejściowych. Na przykład jeśli formant powoduje pominięcie <xref:System.Windows.UIElement.MouseLeftButtonDown>, spróbuj dołączanie obsługi dla <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> zamiast tego. Ta metoda działa tylko dla elementu base zdarzenia wejściowe takich jak <xref:System.Windows.UIElement.MouseLeftButtonDown>. Te zdarzenia wejściowe używają par tunelu/bąbelków, wywołania obu zdarzeń i udostępnianie danych zdarzenia.  
  
 Każdy z tych metod ma efekty uboczne lub ograniczenia. Po stronie obsługi zdarzeń w wersji zapoznawczej powoduje, że w tym momencie obsługi zdarzenia może wyłączyć programy obsługi, które oczekują na zdarzenie propagacji i dlatego ograniczenia czy zazwyczaj nie jest dobrym rozwiązaniem jest oznaczenie zdarzeń obsługiwane, gdy jest on nadal na Previ Nowa część trasy. Ograniczenia `handledEventsToo` technika jest, że nie można określić `handledEventsToo` obsługi w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako atrybutu, należy zarejestrować program obsługi zdarzeń w kodzie po uzyskaniu odwołania do obiektu do elementu, gdy program obsługi ma zostać dołączony.  
  
## <a name="see-also"></a>Zobacz też  
 [Oznaczanie zdarzeń trasowanych jako obsłużonych oraz obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
