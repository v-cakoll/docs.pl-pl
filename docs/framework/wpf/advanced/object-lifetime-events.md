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
ms.openlocfilehash: 8ecc3f716061dfd08ac95652d1a9d8e06e26d949
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175796"
---
# <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń
W tym temacie opisano konkretne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia, które oznaczają etapów w okresie istnienia obiektu, tworzenia, użytkowania i niszczenia.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasy, a po ich przeczytaniu [Przegląd właściwości zależności](dependency-properties-overview.md) tematu. Aby można było wykonać instrukcje opisane w przykładach w tym temacie, należy również mieć świadomość [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (zobacz [Przegląd XAML (WPF)](xaml-overview-wpf.md)) i wiedzieć, jak napisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń  
 Wszystkie obiekty w kodzie programu Microsoft .NET Framework zarządzane przechodzą przez podobny zestaw etapów cyklu życia, tworzenia, używania i niszczenia. Wiele obiektów ma także etapu finalizacji wykonywanego w fazie niszczenie obiektu życia. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty więcej, w szczególności wizualizacji obiekty, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identyfikuje elementy, również mieć zestaw typowe etapy cyklu życia obiektów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modele programowania i aplikacji uwidocznić te etapy jako szereg zdarzeń. Istnieją cztery główne typy obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] względem zdarzenia okresu istnienia; elementów w ogólne, okno elementów, hosty nawigacji i obiekty aplikacji. Hosty Windows i nawigacji są również w większych grupowaniu obiekty wizualne (elementy). W tym temacie opisano zdarzenia okresu istnienia, które są wspólne dla wszystkich elementów, a następnie wprowadza bardziej precyzyjnych, które mają zastosowanie do definicji aplikacji, systemu windows lub hosty nawigacji.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Typowe zdarzenia okresu istnienia dla elementów  
 Dowolny element w poziomie struktury WPF (te obiekty pochodząca z poziomu <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>) ma trzy typowe zdarzenia okresu istnienia: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>, i <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Zainicjowany  
 <xref:System.Windows.FrameworkElement.Initialized> jest uruchamiany w pierwszy i około odnosi się do inicjowania obiektu przez wywołanie do jej konstruktora. Ponieważ zdarzenia odbywa się w odpowiedzi na zainicjowanie, ma gwarancji, że wszystkie właściwości obiektu są ustawione. (Wyjątek stanowi wyrażenie użycia takich jak dynamiczne zasobów lub powiązań, będą one nieznanym wyrażeń.) W wyniku wymogu, że wszystkie właściwości są ustawione, sekwencja <xref:System.Windows.FrameworkElement.Initialized> zgłaszanych przez elementy zagnieżdżone, które są zdefiniowane w znacznikach wydaje się występują w kolejności elementów najgłębiej zagnieżdżoną w drzewie elementów po pierwsze, następnie nadrzędne elementy kierunku głównego. Ta kolejność jest, ponieważ relacji nadrzędny podrzędny i zawierania są właściwości, a w związku z tym element nadrzędny nie może raportować inicjowania, dopóki elementy podrzędne, które wypełnienia właściwości są również całkowicie zainicjowany.  
  
 Podczas pisania procedur obsługi w odpowiedzi na <xref:System.Windows.FrameworkElement.Initialized> zdarzenia, należy rozważyć, nie ma żadnej gwarancji, że wszystkie inne elementy w drzewie elementów (drzewo logiczne lub drzewa wizualnego) wokół którego jest podłączony obsługi zostały utworzone, szczególnie elementy nadrzędne. Zmienne składowe mogą mieć wartości null lub źródła danych nie może jeszcze wypełniony przez powiązanie podstawowej (nawet na poziomie wyrażenia).  
  
### <a name="loaded"></a>załadowano  
 <xref:System.Windows.FrameworkElement.Loaded> następnie jest wywoływane. <xref:System.Windows.FrameworkElement.Loaded> Zdarzenie jest wywoływane przed ostateczne renderowanie, ale po układ obliczoną wszystkich wartości wymaganych do renderowania. <xref:System.Windows.FrameworkElement.Loaded> pociąga za sobą drzewo logiczne, że element zawarty w zostało ukończone i nawiązuje połączenie ze źródłem prezentacji, która zapewnia HWND i powierzchnię renderowania. Powiązanie danych w warstwie standardowa (powiązanie do źródeł lokalnych, takich jak inne właściwości lub bezpośrednio zdefiniowanych źródeł danych) będą miały miejsce przed <xref:System.Windows.FrameworkElement.Loaded>. Powiązanie danych asynchroniczne (źródła zewnętrznego lub dynamicznej) mogły mieć miejsce, ale zgodnie z definicją natury asynchronicznych nie może zagwarantować miały miejsce.  
  
 Mechanizm, za pomocą którego <xref:System.Windows.FrameworkElement.Loaded> zdarzenie jest zgłaszane jest inny niż <xref:System.Windows.FrameworkElement.Initialized>. <xref:System.Windows.FrameworkElement.Initialized> Zdarzenie jest element zostaje zgłoszone przez element bez bezpośredniej koordynacji przez drzewo elementu ukończone. Z kolei <xref:System.Windows.FrameworkElement.Loaded> zdarzenie jest zgłaszane jako wspólnym wysiłku całego elementu w drzewie (w szczególności drzewo logiczne). Gdy wszystkie elementy w drzewie są w stanie, gdzie są traktowane jako załadowane, <xref:System.Windows.FrameworkElement.Loaded> zdarzeń jest wywołany po raz pierwszy element główny. <xref:System.Windows.FrameworkElement.Loaded> Zdarzenie jest następnie zgłaszane kolejno dla każdego elementu podrzędnego.  
  
> [!NOTE]
>  To zachowanie pozornie może wyglądać tunelowania dla zdarzenia trasowanego. Jednak żadne informacje nie jest przenoszony zdarzeń zdarzeń. Każdy element jest zawsze ma możliwość obsługi jego <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i oznaczanie danych zdarzenia jako obsłużony, nie ma wpływu poza tego elementu.  
  
### <a name="unloaded"></a>Zwolniono  
 <xref:System.Windows.FrameworkElement.Unloaded> jest uruchamiany ostatnia i jest inicjowane przez źródło prezentacji lub nadrzędnego visual usuwany. Gdy <xref:System.Windows.FrameworkElement.Unloaded> jest wyświetlany i obsługiwane element, który z kolei jest nadrzędne źródło zdarzeń (zgodnie z ustaleniami <xref:System.Windows.FrameworkElement.Parent%2A> właściwości) lub dowolnego danego elementu do góry drzewa logicznego lub visual mogło już zostać usunięta, co oznacza, że powiązanie danych odwołania do zasobów , i nie można ustawić style ich normalne lub ostatni znany wartość w czasie wykonywania.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Elementy modelu aplikacji zdarzenia okresu istnienia  
 Opieranie się na typowych zdarzenia okresu istnienia dla elementów są następujące elementy modelu aplikacji: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, i <xref:System.Windows.Controls.Frame>. Te rozszerzenia typowych zdarzenia okresu istnienia przy użyciu dodatkowych zdarzeń, które mają zastosowanie do ich z określonym przeznaczeniem. Te są szczegółowo omówione w następujących lokalizacjach:  
  
-   <xref:System.Windows.Application>: [Zarządzanie aplikacjami — omówienie](../app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [Przegląd Windows WPF](../app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, i <xref:System.Windows.Controls.Frame>: [Nawigacja — omówienie](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Następstwo wartości właściwości zależności](dependency-property-value-precedence.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
