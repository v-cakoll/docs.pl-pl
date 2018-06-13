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
ms.openlocfilehash: 02a6736fe54be4683044f648e9d5ed5e8a3d95dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547537"
---
# <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń
W tym temacie opisano konkretnym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia, które wskazują etapach w okres istnienia obiektów tworzenia, użytkowania i zniszczenie.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono zrozumieć właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klas i przeczytanie [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) tematu. Aby można było wykonać przykłady w tym temacie, należy również zapoznać się [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (zobacz [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)) oraz wiedzieć, jak napisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Obiekt okresu istnienia zdarzeń  
 Wszystkie obiekty w kodzie programu Microsoft .NET Framework zarządzane przejść przez zestaw podobnych etapy cyklu życia, tworzenie, użyj i likwidacja. Wiele obiektów ma także finalizacji etap cyklu życia występujący w fazie zniszczenia. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty więcej, w szczególności visual obiekty, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identyfikuje jako elementy, ma również zbiór typowe etapy cyklu życia obiektów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modele programowania i aplikacji ujawniać te etapy jako szereg zdarzeń. Istnieją cztery główne typy obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] względem okres istnienia zdarzeń; elementów w ogólne, elementy okna nawigacji hosty i obiekty aplikacji. Hosty z systemem Windows i nawigacja są również w grupowaniu większych obiektów visual (elementy). W tym temacie opisano zdarzenia okresu istnienia, które są wspólne dla wszystkich elementów, a następnie przedstawiono bardziej szczegółowe te, które dotyczą systemu windows, hostach nawigacji lub definicji aplikacji.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Typowe zdarzenia okresu istnienia dla elementów  
 Dowolny element w poziomie struktury WPF (te obiekty z jednej <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>) ma trzy typowe zdarzenia okresu istnienia: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>, i <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Zainicjowany  
 <xref:System.Windows.FrameworkElement.Initialized> jest uruchamiany najpierw, a grubsza odpowiada inicjowania obiektu przez wywołanie jego konstruktora. Ponieważ zdarzenie w odpowiedzi na zainicjowanie, ma gwarancji, że wszystkie właściwości obiektu są ustawione. (Wyjątek jest wyrażenie zwracać dynamicznych zasobów lub powiązań; będą wyrażenia nieznanym). Zgodnie z wymaganiem, aby wszystkie właściwości są ustawione, sekwencja <xref:System.Windows.FrameworkElement.Initialized> zgłaszanych przez zagnieżdżone elementy, które są zdefiniowane w znaczniku wydaje się najpierw, występują w kolejności elementów najgłębszym w drzewie elementu element nadrzędny elementy do katalogu głównego. Porządek ten jest ponieważ relacji nadrzędny podrzędny i zawierania właściwości, i w związku z tym nadrzędny nie może zaraportować inicjowania, dopóki elementy podrzędne, które wypełnienie właściwości są również całkowicie zainicjowany.  
  
 Podczas pisania programów obsługi w odpowiedzi na <xref:System.Windows.FrameworkElement.Initialized> zdarzenia, należy rozważyć czy nie ma żadnej gwarancji, że wszystkie elementy w drzewie elementu (drzewa logicznego lub drzewa wizualnego) wokół którym jest umocowana Obsługa zostały utworzone, szczególnie elementy nadrzędne. Zmienne Członkowskie mogą mieć wartości null lub źródeł danych może nie jeszcze być wypełniony przez powiązanie podstawowej (nawet na poziomie wyrażenie).  
  
### <a name="loaded"></a>załadowano  
 <xref:System.Windows.FrameworkElement.Loaded> następnie jest uruchamiany. <xref:System.Windows.FrameworkElement.Loaded> Zdarzenie jest wywoływane przed renderowanie końcowego, ale po układu obliczoną wszystkie wartości wymagane do renderowania. <xref:System.Windows.FrameworkElement.Loaded> zakłada się, czy element zawarty w drzewie logicznym są kompletne i nawiązuje połączenie ze źródłem prezentacji, która udostępnia HWND i powierzchnię renderowania. Powiązanie standardowe danych (powiązanie do lokalnych źródeł, takich jak inne właściwości lub bezpośrednio zdefiniowanych źródeł danych) będą miały miejsce przed <xref:System.Windows.FrameworkElement.Loaded>. Powiązanie danych asynchronicznych (źródła zewnętrznego lub dynamiczny) może wystąpić, ale zgodnie z definicją natury asynchronicznego nie można zagwarantować miała miejsce.  
  
 Mechanizm, za pomocą którego <xref:System.Windows.FrameworkElement.Loaded> zdarzenia jest inna niż <xref:System.Windows.FrameworkElement.Initialized>. <xref:System.Windows.FrameworkElement.Initialized> Zdarzenie jest element podniesione przez element bez bezpośredniego koordynacji przez drzewo elementu ukończone. Z kolei <xref:System.Windows.FrameworkElement.Loaded> zdarzenie jest zgłaszane jako wspólnym wysiłku całego elementu w drzewie (w szczególności drzewa logicznego). Gdy wszystkie elementy w drzewie są w stanie, gdy są uważane za załadowane, <xref:System.Windows.FrameworkElement.Loaded> zdarzeń jest wywołany po raz pierwszy element główny. <xref:System.Windows.FrameworkElement.Loaded> Następnie zdarzenia kolejno dla każdego elementu podrzędnego.  
  
> [!NOTE]
>  To zachowanie może pozornie przypominać tunelowania dla kierowanego zdarzenia. Jednak żadne informacje nie jest przenoszona zdarzeń zdarzeń. Każdy element ma zawsze możliwość obsługi jego <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i oznaczenie dane zdarzenia, ponieważ obsługiwane nie obowiązuje, poza tego elementu.  
  
### <a name="unloaded"></a>Zwolniono  
 <xref:System.Windows.FrameworkElement.Unloaded> jest wywoływane ostatnio i jest inicjowane przez źródło prezentacji lub visual nadrzędnej, zostaną usunięte. Gdy <xref:System.Windows.FrameworkElement.Unloaded> jest uruchamiany i obsługi elementu nadrzędnego źródła zdarzeń (zgodnie z ustaleniami <xref:System.Windows.FrameworkElement.Parent%2A> właściwości) lub dowolnego danego elementu górę drzewa logicznego lub wizualnego mogła już zostać usunięta, co oznacza, że powiązania danych, odwołania do zasobów , i style nie może być ustawiony na ich normalne lub ostatniej znanej środowiska wykonawczego wartości.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Okres istnienia zdarzeń aplikacji modelu elementów  
 Opierając się na wspólnej zdarzenia okresu istnienia dla elementów są następujące elementy modelu aplikacji: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, i <xref:System.Windows.Controls.Frame>. Te rozszerzenia typowe zdarzenia okresu istnienia z dodatkowych zdarzeń, które mają zastosowanie w ich określonym przeznaczeniem. Te omówiono szczegółowo w następujących lokalizacjach:  
  
-   <xref:System.Windows.Application>: [Omówienie zarządzania aplikacji](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [WPF systemu Windows — omówienie](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, i <xref:System.Windows.Controls.Frame>: [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Następstwo wartości właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)  
 [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
