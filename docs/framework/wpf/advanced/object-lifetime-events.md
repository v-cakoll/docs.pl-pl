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
ms.openlocfilehash: c0858a0194bc0e9efa60a42d4029bdba9f4f3fef
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458576"
---
# <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń
W tym temacie opisano konkretne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia, które przedstawiają etapy okresu istnienia obiektu, użycia i zniszczenia.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że właściwości zależności są rozpoznawane w perspektywie odbiorcy istniejących właściwości zależności w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasach, i zapoznaj się z tematem [Omówienie właściwości zależności](dependency-properties-overview.md) . Aby postępować zgodnie z przykładami w tym temacie, należy również zrozumieć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (zobacz [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md)) i wiedzieć, jak pisać aplikacje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń  
 Wszystkie obiekty w kodzie zarządzanym w programie Microsoft .NET Framework przechodzą przez podobny zestaw etapów życia, tworzenia, używania i niszczenia. Wiele obiektów ma również etap finalizowania cyklu życia, który występuje jako część fazy niszczenia. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów, bardziej szczegółowe obiekty wizualne, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identyfikować jako elementy, również mają zestaw typowych etapów istnienia obiektu. Modele programowania i aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uwidaczniają te etapy jako serie zdarzeń. Istnieją cztery główne typy obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w odniesieniu do zdarzeń okresu istnienia. elementy ogólnie, elementy okna, hosty nawigacji i obiekty aplikacji. Hosty systemu Windows i nawigacji znajdują się również w większej grupie obiektów wizualnych (elementów). W tym temacie opisano zdarzenia okresu istnienia, które są wspólne dla wszystkich elementów, a następnie wprowadzono bardziej szczegółowe informacje dotyczące definicji aplikacji, systemu Windows lub hostów nawigacji.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Typowe zdarzenia okresu istnienia dla elementów  
 Każdy element poziomu platformy WPF (te obiekty pochodzące z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>) ma trzy typowe zdarzenia dotyczące okresu istnienia: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>i <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Zainicjowany  
 <xref:System.Windows.FrameworkElement.Initialized> jest najpierw wywoływany, a w przybliżeniu odnosi się do inicjalizacji obiektu przez wywołanie jego konstruktora. Ponieważ zdarzenie występuje w odpowiedzi na inicjalizację, masz gwarancję, że wszystkie właściwości obiektu są ustawione. (Wyjątek to użycie wyrażeń, takie jak zasoby dynamiczne lub powiązanie; będą to wyrażenia nieoceniane). W związku z wymaganiem, że wszystkie właściwości są ustawione, sekwencja <xref:System.Windows.FrameworkElement.Initialized>, które są wywoływane przez zagnieżdżone elementy, które są zdefiniowane w znaczniku, pojawia się w kolejności największych elementów w drzewie elementów, a następnie elementów nadrzędnych do katalogu głównego. Ta kolejność jest spowodowana tym, że relacje nadrzędny-podrzędny i zawierania są właściwościami, w związku z czym element nadrzędny nie może zgłosić inicjalizacji do momentu, gdy elementy podrzędne, które wypełniają właściwość, również zostaną całkowicie zainicjowane.  
  
 Podczas pisania programów obsługi w odpowiedzi na zdarzenie <xref:System.Windows.FrameworkElement.Initialized>, należy wziąć pod uwagę, że nie ma gwarancji, że wszystkie pozostałe elementy w drzewie elementów (logiczne drzewo lub drzewo wizualne) wokół miejsca, w którym została dołączona procedura obsługi, zostały utworzone, szczególnie elementy nadrzędne części. Zmienne składowe mogą mieć wartość null lub źródła danych mogą jeszcze nie zostać wypełnione przez bazowe powiązanie (nawet na poziomie wyrażenia).  
  
### <a name="loaded"></a>załadowano  
 <xref:System.Windows.FrameworkElement.Loaded> zostanie zgłoszone dalej. Zdarzenie <xref:System.Windows.FrameworkElement.Loaded> jest wywoływane przed ostatnim renderowaniem, ale po obliczeniu przez system układu wszystkich wymaganych wartości renderowania. <xref:System.Windows.FrameworkElement.Loaded> wiąże się z tym, że Drzewo logiczne, w ramach którego znajduje się element, jest kompletne i łączy się ze źródłem prezentacji, które zapewnia Właściwość HWND i powierzchnię renderowania. Przed <xref:System.Windows.FrameworkElement.Loaded>em zostaną nawiązane standardowe powiązanie danych (takie jak inne właściwości lub bezpośrednio zdefiniowane źródła danych). Mogły wystąpić asynchroniczne powiązania danych (zewnętrzne lub źródła dynamiczne), ale przez zdefiniowanie jego charakteru asynchronicznego nie można zagwarantować, że wystąpił.  
  
 Mechanizm, za pomocą którego wywoływane jest zdarzenie <xref:System.Windows.FrameworkElement.Loaded>, różni się od <xref:System.Windows.FrameworkElement.Initialized>. Zdarzenie <xref:System.Windows.FrameworkElement.Initialized> jest wywoływane elementu przez element, bez bezpośredniej koordynacji przez ukończone drzewo elementów. Z kolei zdarzenie <xref:System.Windows.FrameworkElement.Loaded> jest zgłaszane jako skoordynowane nakłady pracy w całym drzewie elementów (w odniesieniu do drzewa logicznego). Gdy wszystkie elementy drzewa znajdują się w stanie, w którym są uważane za załadowane, zdarzenie <xref:System.Windows.FrameworkElement.Loaded> jest najpierw wywoływane na elemencie głównym. Zdarzenie <xref:System.Windows.FrameworkElement.Loaded> jest następnie wywoływane kolejno dla każdego elementu podrzędnego.  
  
> [!NOTE]
> Takie zachowanie może być podobne do tunelowania dla zdarzenia kierowanego. Jednak żadne informacje nie są przenoszone ze zdarzenia do zdarzenia. Każdy element zawsze ma możliwość obsługi swojego zdarzenia <xref:System.Windows.FrameworkElement.Loaded> i oznaczania, że dane zdarzenia jako obsłużone nie wpływają poza ten element.  
  
### <a name="unloaded"></a>Zwolniono  
 <xref:System.Windows.FrameworkElement.Unloaded> jest wysunięty jako ostatni i jest inicjowany przez źródło prezentacji lub usuwanie elementu nadrzędnego elementu wizualnego. Po podniesieniu i obsłudze <xref:System.Windows.FrameworkElement.Unloaded> element, który jest elementem nadrzędnym źródła zdarzeń (określony przez właściwość <xref:System.Windows.FrameworkElement.Parent%2A>) lub dowolny element w górę w drzewach logicznych lub wizualnych, mógł już zostać nieustawiony, co oznacza powiązanie danych, odwołania do zasobów i style nie może być ustawiona na ich normalną lub ostatnią znaną wartość czasu wykonywania.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Elementy modelu aplikacji zdarzeń okresu istnienia  
 Kompilowanie wspólnych zdarzeń okresu istnienia dla elementów to następujące elementy modelu aplikacji: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>i <xref:System.Windows.Controls.Frame>. Umożliwiają one rozbudowanie typowych zdarzeń okresu istnienia z dodatkowymi zdarzeniami, które są istotne dla ich określonego celu. Są one szczegółowo omówione w następujących lokalizacjach:  
  
- <xref:System.Windows.Application>: [Omówienie zarządzania aplikacjami](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [Omówienie systemu Windows WPF](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>i <xref:System.Windows.Controls.Frame>: [Przegląd nawigacji](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Następstwo wartości właściwości zależności](dependency-property-value-precedence.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
