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
ms.openlocfilehash: dd2e116c4241a44786af3a56b931b0c3c0571814
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933491"
---
# <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń
W tym temacie opisano konkretne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia, które przedstawiają etapy okresu istnienia obiektu, użycia i zniszczenia.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że właściwości zależności są rozpoznawane w perspektywie odbiorcy istniejących [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości zależności w klasach, i zapoznaj się z tematem [Omówienie właściwości zależności](dependency-properties-overview.md) . Aby postępować zgodnie z przykładami w tym temacie, należy również zapoznać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] się z tematem (zobacz [Omówienie języka XAML (WPF)](xaml-overview-wpf.md)) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i wiedzieć, jak pisać aplikacje.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń  
 Wszystkie obiekty w kodzie zarządzanym w programie Microsoft .NET Framework przechodzą przez podobny zestaw etapów życia, tworzenia, używania i niszczenia. Wiele obiektów ma również etap finalizowania cyklu życia, który występuje jako część fazy niszczenia. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obiekty, bardziej szczegółowe obiekty wizualne, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identyfikują jako elementy, również mają zestaw typowych etapów istnienia obiektu. Modele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania i aplikacji uwidaczniają te etapy jako serie zdarzeń. Istnieją cztery główne typy obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odniesieniu do zdarzeń okresu istnienia; elementy ogólnie, elementy okna, hosty nawigacji i obiekty aplikacji. Hosty systemu Windows i nawigacji znajdują się również w większej grupie obiektów wizualnych (elementów). W tym temacie opisano zdarzenia okresu istnienia, które są wspólne dla wszystkich elementów, a następnie wprowadzono bardziej szczegółowe informacje dotyczące definicji aplikacji, systemu Windows lub hostów nawigacji.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Typowe zdarzenia okresu istnienia dla elementów  
 Każdy element platformy WPF Framework (te obiekty pochodne z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>) ma trzy typowe zdarzenia dotyczące okresu istnienia: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>, i <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Zainicjowany  
 <xref:System.Windows.FrameworkElement.Initialized>jest uruchamiany jako pierwszy, a w przybliżeniu odnosi się do inicjalizacji obiektu przez wywołanie jego konstruktora. Ponieważ zdarzenie występuje w odpowiedzi na inicjalizację, masz gwarancję, że wszystkie właściwości obiektu są ustawione. (Wyjątek to użycie wyrażeń, takie jak zasoby dynamiczne lub powiązanie; będą to wyrażenia nieoceniane). W związku z wymaganiem, że wszystkie właściwości są ustawione, sekwencja <xref:System.Windows.FrameworkElement.Initialized> wywoływana przez zagnieżdżone elementy, które są zdefiniowane w znaczniku, pojawia się w kolejności najwyższego rzędu w drzewie elementów, a następnie elementy nadrzędne w kierunku katalogu głównego. Ta kolejność jest spowodowana tym, że relacje nadrzędny-podrzędny i zawierania są właściwościami, w związku z czym element nadrzędny nie może zgłosić inicjalizacji do momentu, gdy elementy podrzędne, które wypełniają właściwość, również zostaną całkowicie zainicjowane.  
  
 Gdy piszesz programy obsługi w odpowiedzi na <xref:System.Windows.FrameworkElement.Initialized> zdarzenie, należy wziąć pod uwagę, że nie ma gwarancji, że wszystkie pozostałe elementy w drzewie elementów (logiczne drzewo lub drzewo wizualne) wokół miejsca, w którym została dołączona procedura obsługi, zostały utworzone, szczególnie elementy nadrzędne. Zmienne składowe mogą mieć wartość null lub źródła danych mogą jeszcze nie zostać wypełnione przez bazowe powiązanie (nawet na poziomie wyrażenia).  
  
### <a name="loaded"></a>załadowano  
 <xref:System.Windows.FrameworkElement.Loaded>jest podnoszony dalej. <xref:System.Windows.FrameworkElement.Loaded> Zdarzenie jest wywoływane przed ostatnim renderowaniem, ale gdy system układu obliczy wszystkie wymagane wartości do renderowania. <xref:System.Windows.FrameworkElement.Loaded>polega na tym, że Drzewo logiczne, w ramach którego znajduje się element, jest kompletne i łączy się ze źródłem prezentacji, które zapewnia Właściwość HWND i powierzchnię renderowania. W <xref:System.Windows.FrameworkElement.Loaded>systemach wcześniejszych niż zostanie wystąpiło standardowe powiązanie danych (takie jak inne właściwości lub bezpośrednio zdefiniowane źródła danych). Mogły wystąpić asynchroniczne powiązania danych (zewnętrzne lub źródła dynamiczne), ale przez zdefiniowanie jego charakteru asynchronicznego nie można zagwarantować, że wystąpił.  
  
 Mechanizm, za pomocą którego <xref:System.Windows.FrameworkElement.Loaded> wywoływane jest zdarzenie, różni się <xref:System.Windows.FrameworkElement.Initialized>od. <xref:System.Windows.FrameworkElement.Initialized> Zdarzenie jest wywoływane elementu przez element, bez bezpośredniej koordynacji przez ukończone drzewo elementów. Z kolei <xref:System.Windows.FrameworkElement.Loaded> zdarzenie jest zgłaszane jako skoordynowane nakłady pracy w całym drzewie elementów (w odniesieniu do drzewa logicznego). Gdy wszystkie elementy drzewa są w stanie, w którym są uważane za załadowane, <xref:System.Windows.FrameworkElement.Loaded> zdarzenie jest najpierw wywoływane na elemencie głównym. <xref:System.Windows.FrameworkElement.Loaded> Zdarzenie jest następnie wywoływane kolejno dla każdego elementu podrzędnego.  
  
> [!NOTE]
> Takie zachowanie może być podobne do tunelowania dla zdarzenia kierowanego. Jednak żadne informacje nie są przenoszone ze zdarzenia do zdarzenia. Każdy element zawsze ma możliwość obsługi jego <xref:System.Windows.FrameworkElement.Loaded> zdarzenia i oznaczania, że dane zdarzenia jako obsłużone nie wpływają poza ten element.  
  
### <a name="unloaded"></a>Zwolniono  
 <xref:System.Windows.FrameworkElement.Unloaded>jest wysunięty jako ostatni i jest inicjowany przez źródło prezentacji lub element wizualny usuwany. Gdy <xref:System.Windows.FrameworkElement.Unloaded> jest wywoływany i obsłużony, element, który jest obiektem nadrzędnym źródła zdarzeń <xref:System.Windows.FrameworkElement.Parent%2A> (określony przez właściwość) lub dowolny element w górę w drzewach logicznych lub wizualnych, mógł już zostać nieustawiony, co oznacza, że powiązanie danych, odwołania do zasobów , a style nie mogą być ustawione na wartość normalną lub ostatnią znaną wartością czasu wykonywania.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Elementy modelu aplikacji zdarzeń okresu istnienia  
 Kompilowanie wspólnych zdarzeń okresu istnienia dla elementów to następujące elementy modelu aplikacji: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow>, i <xref:System.Windows.Controls.Frame>. Umożliwiają one rozbudowanie typowych zdarzeń okresu istnienia z dodatkowymi zdarzeniami, które są istotne dla ich określonego celu. Są one szczegółowo omówione w następujących lokalizacjach:  
  
- <xref:System.Windows.Application>: [Omówienie zarządzania aplikacjami](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [Omówienie systemu Windows WPF](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>i :<xref:System.Windows.Controls.Frame> [Przegląd nawigacji](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Następstwo wartości właściwości zależności](dependency-property-value-precedence.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
