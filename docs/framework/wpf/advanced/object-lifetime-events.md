---
title: Obiekt okresu istnienia zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- events [WPF], ContentRendered
- events [WPF], Deactivated
- events [WPF], Unloaded
- Activated events [WPF]
- events [WPF], Loaded
- Application objects [WPF], lifetime events
- events [WPF], Activated
- ContentRendered events [WPF]
- Deactivated events [WPF]
- events [WPF], Initialized
- events [WPF], Closing
- Unloaded events [WPF]
- exit events [WPF]
- objects' lifetime events [WPF]
- Loaded events [WPF]
- Closing events [WPF]
- events [WPF], Closed
- Initialized events [WPF]
- Closed events [WPF]
- startup events [WPF]
- lifetime events of objects [WPF]
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
ms.openlocfilehash: 3b761674bd2464ee87e07d9299c805431f8fdeb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141110"
---
# <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń
W tym temacie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] opisano określone zdarzenia, które oznaczają etapy w okresie istnienia obiektu tworzenia, używania i niszczenia.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że rozumiesz właściwości zależności z perspektywy konsumenta istniejących właściwości zależności w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasach i przeczytałeś temat [Omówienie właściwości zależności.](dependency-properties-overview.md) Aby postępować zgodnie z przykładami w tym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] temacie, należy również zrozumieć (zobacz [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)) i wiedzieć, jak pisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje.  
  
<a name="intro"></a>
## <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń  
 Wszystkie obiekty w kodzie zarządzanym programu Microsoft .NET Framework przechodzą przez podobny zestaw etapów życia, tworzenia, używania i niszczenia. Wiele obiektów ma również etap finalizacji życia, który występuje w ramach fazy zniszczenia. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obiekty, a dokładniej obiekty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wizualne, które identyfikuje się jako elementy, mają również zestaw wspólnych etapów życia obiektu. Modele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania i aplikacji uwidaczniają te etapy jako serię zdarzeń. Istnieją cztery główne typy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów w odniesieniu do zdarzeń lifetime; elementy, elementy okna, hosty nawigacji i obiekty aplikacji. Windows i hosty nawigacji są również w ramach większej grupy obiektów wizualnych (elementów). W tym temacie opisano zdarzenia okresu istnienia, które są wspólne dla wszystkich elementów, a następnie wprowadzono bardziej szczegółowe te, które mają zastosowanie do definicji aplikacji, okien lub hostów nawigacji.  
  
<a name="common_events"></a>
## <a name="common-lifetime-events-for-elements"></a>Typowe zdarzenia dotyczące okresu istnienia dla elementów  
 Każdy element na poziomie struktury WPF (te <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>obiekty pochodzące z <xref:System.Windows.FrameworkElement.Initialized>jednego <xref:System.Windows.FrameworkElement.Loaded>lub <xref:System.Windows.FrameworkElement.Unloaded>) ma trzy typowe zdarzenia istnienia: , , i .  
  
### <a name="initialized"></a>Zainicjowany  
 <xref:System.Windows.FrameworkElement.Initialized>jest wywoływana pierwszy i z grubsza odpowiada inicjowania obiektu przez wywołanie jego konstruktora. Ponieważ zdarzenie dzieje się w odpowiedzi na inicjalizacji, masz gwarancję, że wszystkie właściwości obiektu są ustawione. (Wyjątkiem są użycia wyrażenia, takie jak zasoby dynamiczne lub powiązanie; będą to wyrażenia nieoceniowe). W wyniku wymogu, że wszystkie właściwości są <xref:System.Windows.FrameworkElement.Initialized> ustawione, sekwencja wywoływane przez elementy zagnieżdżone, które są zdefiniowane w znacznikach wydaje się występować w kolejności najgłębszych elementów w drzewie elementu, a następnie elementy nadrzędne w kierunku katalogu głównego. Ta kolejność jest, ponieważ relacje nadrzędny podrzędny i hermetyzacji są właściwości, a zatem element nadrzędny nie może zgłosić inicjowania, dopóki elementy podrzędne, które wypełniają właściwość są również całkowicie zainicjowane.  
  
 Podczas pisania programów obsługi w <xref:System.Windows.FrameworkElement.Initialized> odpowiedzi na zdarzenie, należy wziąć pod uwagę, że nie ma żadnej gwarancji, że wszystkie inne elementy w drzewie elementów (drzewa logicznego lub drzewa wizualnego) wokół, gdzie program obsługi jest dołączony zostały utworzone, szczególnie elementy nadrzędne. Zmienne członkowskie mogą mieć wartość null lub źródła danych mogą jeszcze nie zostać wypełnione przez podstawowe powiązanie (nawet na poziomie wyrażenia).  
  
### <a name="loaded"></a>załadowano  
 <xref:System.Windows.FrameworkElement.Loaded>jest podniesiona w następnej kolejności. Zdarzenie <xref:System.Windows.FrameworkElement.Loaded> jest wywoływane przed ostatecznym renderowaniem, ale po obliczeniu przez system układu wszystkich wartości niezbędnych do renderowania. <xref:System.Windows.FrameworkElement.Loaded>oznacza, że drzewo logiczne, w którego znajduje się element, jest kompletne i łączy się ze źródłem prezentacji, które zapewnia HWND i powierzchnię renderowania. Standardowe powiązanie danych (powiązanie ze źródłami lokalnymi, takimi jak inne właściwości lub <xref:System.Windows.FrameworkElement.Loaded>bezpośrednio zdefiniowane źródła danych) miało miejsce przed programem . Mogło wystąpić powiązanie danych asynchronicznych (źródeł zewnętrznych lub dynamicznych), ale z definicji jego asynchronicznie nie można zagwarantować wystąpienia.  
  
 Mechanizm, za <xref:System.Windows.FrameworkElement.Loaded> pomocą którego zdarzenie <xref:System.Windows.FrameworkElement.Initialized>jest wywoływane, jest inny niż . Zdarzenie <xref:System.Windows.FrameworkElement.Initialized> jest wywoływane element po elemencie, bez bezpośredniej koordynacji przez ukończone drzewo elementów. Z drugiej <xref:System.Windows.FrameworkElement.Loaded> strony zdarzenie jest wywoływane jako skoordynowany wysiłek w całym drzewie elementów (w szczególności drzewa logicznego). Gdy wszystkie elementy w drzewie są w stanie, <xref:System.Windows.FrameworkElement.Loaded> w którym są one uważane za załadowany, zdarzenie jest najpierw wywoływane na element główny. Zdarzenie <xref:System.Windows.FrameworkElement.Loaded> jest następnie wywoływane kolejno na każdy element podrzędny.  
  
> [!NOTE]
> To zachowanie może powierzchownie przypominać tunelowanie dla kierowanego zdarzenia. Jednak żadne informacje nie są przenoszone z zdarzenia na zdarzenie. Każdy element zawsze ma możliwość <xref:System.Windows.FrameworkElement.Loaded> obsługi jego zdarzenia i oznaczanie danych zdarzenia jako obsługiwane nie ma wpływu poza tym elementem.  
  
### <a name="unloaded"></a>Zwolniono  
 <xref:System.Windows.FrameworkElement.Unloaded>jest wywoływana jako ostatnia i jest inicjowana przez źródło prezentacji lub wizualny element nadrzędny, który jest usuwany. Gdy <xref:System.Windows.FrameworkElement.Unloaded> jest wywoływana i obsługiwane, element, który jest <xref:System.Windows.FrameworkElement.Parent%2A> elementem nadrzędnym źródła zdarzeń (określone przez właściwość) lub dowolnego elementu w górę w drzewach logicznych lub wizualnych może już zostały unset, co oznacza, że powiązanie danych, odwołania do zasobów i style nie mogą być ustawione na ich normalną lub ostatnio znaną wartość w czasie wykonywania.  
  
<a name="application_model_elements"></a>
## <a name="lifetime-events-application-model-elements"></a>Elementy modelu aplikacji zdarzeń okresu istnienia  
 Opierając się na typowych zdarzeniach okresu istnienia <xref:System.Windows.Application> <xref:System.Windows.Window>dla <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow>elementów są następujące elementy modelu aplikacji: , , , i <xref:System.Windows.Controls.Frame>. Rozszerzają one typowe zdarzenia życia o dodatkowe zdarzenia, które są istotne dla ich określonego celu. Są one szczegółowo omówione w następujących lokalizacjach:  
  
- <xref:System.Windows.Application>: [Omówienie zarządzania aplikacjami](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [Przegląd systemu Windows WPF](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>i : [Przegląd nawigacji](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Następstwo zależności wartości właściwości](dependency-property-value-precedence.md)
- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
