---
title: "Przegląd Zdarzenia trasowane"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached events [WPF]
- grouped button set [WPF]
- routed events [WPF]
- events [WPF], routed
- tunneling [WPF]
- events [WPF], attached
- routing strategies for events [WPF]
- button set [WPF], grouped
- bubbling [WPF]
ms.assetid: 1a2189ae-13b4-45b0-b12c-8de2e49c29d2
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22ce2611afa2a3b2b06b7d378479e5ffd2f744f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="routed-events-overview"></a>Przegląd Zdarzenia trasowane
W tym temacie opisano pojęcia kierowane zdarzenia w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Temat definiuje terminologii kierowane zdarzenia, w tym artykule opisano sposób kierowane zdarzenia są wysyłane za pośrednictwem drzewa elementów, zawiera podsumowanie sposobu obsługi kierowane zdarzenia oraz przedstawiono sposób tworzenia własnego niestandardowego kierowane zdarzenia.
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że masz podstawową wiedzę na temat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] i programowanie zorientowane obiektowo, a także pojęcie jak relacje między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów można conceptualized jako drzewa. Aby można było wykonać przykłady w tym temacie, należy również zapoznać się [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wiedzieć, jak napisać bardzo podstawowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji lub strony. Aby uzyskać więcej informacji, zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) i [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="routing"></a>   
## <a name="what-is-a-routed-event"></a>Co to jest kierowanego zdarzenia?  
 Należy zwrócić uwagę zdarzenia rozsyłane, albo z punktu widzenia funkcjonalności lub implementacji. Zarówno definicje są prezentowane w tym miejscu, ponieważ niektóre osoby odnaleźć co najmniej innych definicji bardziej użyteczne.  
  
 Definicja funkcjonalności: kierowanego zdarzenia jest typem zdarzenia, które może wywołać programów obsługi na wiele odbiorników w drzewie elementu, a nie tylko na obiekt, który wywołał zdarzenie.  
  
 Implementacja definicji: kierowanego zdarzenia jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenie, które nie jest obsługiwana przez wystąpienie <xref:System.Windows.RoutedEvent> klasy, a następnie są przetwarzane przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zdarzeń systemu.  
  
 Typowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji zawiera wiele elementów. Czy utworzone w kodzie zadeklarowany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], istnieje te elementy w element drzewa relacji między nimi. Trasy zdarzenia mogą być przesyłane w jednym z dwóch kierunków, w zależności od definicji zdarzenia, ale zazwyczaj trasy przechodzi od elementu źródła i następnie "propaguje" w górę w drzewie element aż osiągnie głównego drzewa elementu (zazwyczaj stronę lub okna). To pojęcie propagacji może być znane, użytkownicy mający doświadczenie z model obiektowy DHTML wcześniej.  
  
 Należy wziąć pod uwagę następujące drzewo element prosty:  
  
 [!code-xaml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Ten element drzewa tworzy postać zbliżoną do następującej:  
  
 ![Tak, nie i przyciski "Anuluj"](../../../../docs/framework/wpf/advanced/media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")  
  
 W tym drzewie uproszczony elementu źródło <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia jest jednym z <xref:System.Windows.Controls.Button> elementów i zależności <xref:System.Windows.Controls.Button> został kliknięty jest pierwszym elementem, który ma możliwość obsługi zdarzenia. Ale jeśli bez obsługi dołączony do <xref:System.Windows.Controls.Button> działa na zdarzenie, a następnie zdarzenie zostanie bąbelkowy w górę do <xref:System.Windows.Controls.Button> elementu nadrzędnego w drzewie element, który jest <xref:System.Windows.Controls.StackPanel>. Ewentualnie dymki zdarzeń do <xref:System.Windows.Controls.Border>, a następnie poza katalog główny strony drzewa elementu (tego nie pokazano).  
  
 Innymi słowy, trasy zdarzenia dla tego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie jest:  
  
 Przycisk--> Panel stosu--> obramowania-->...  
  
### <a name="top-level-scenarios-for-routed-events"></a>Najwyższego poziomu scenariusze dotyczące kierowanego zdarzenia  
 Poniżej przedstawiono krótkie podsumowanie scenariusze, które uzasadnione koncepcji kierowanego zdarzenia i do czego typowe [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń nie jest odpowiednia dla tych scenariuszy:  
  
 **Sterowanie kompozycji i hermetyzacji:** różnych formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sformatowanego modelu zawartości. Na przykład możesz umieścić obraz wewnątrz <xref:System.Windows.Controls.Button>, które skutecznie rozszerza drzewa wizualnego przycisku. Jednak dodane obrazu nie przerwać powoduje, że przycisk odpowiedzieć na zachowanie testowania trafień <xref:System.Windows.Controls.Primitives.ButtonBase.Click> jego zawartości, nawet wtedy, gdy użytkownik kliknie piksele o technicznie część obrazu.  
  
 **Program obsługi w liczbie pojedynczej załącznika punktów:** w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], konieczne będzie dołączenie tej procedury obsługi wielokrotnie do przetwarzania zdarzeń, które mogą zostać zwiększona z wielu elementów. Kierowane zdarzenia umożliwiają dołączanie programu obsługi tylko raz, jak zostało pokazano w poprzednim przykładzie, a następnie użyj programu obsługi logiki, aby określić, skąd zdarzenia pochodzą w razie potrzeby. Na przykład może to być obsługę pokazano wcześniej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-csharp[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
 [!code-vb[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]  
  
 **Obsługa klasy:** zdarzenia rozsyłane zezwolić statycznych program obsługi, który jest zdefiniowany w klasie. Ten program obsługi klasa ma możliwość obsługi zdarzenia, zanim wszystkie dołączone wystąpienia programy obsługi można.  
  
 **Odwołanie do zdarzenia bez odbicia:** pewne techniki kodu i znaczników wymagają do identyfikowania określonego zdarzenia. Tworzy kierowanego zdarzenia <xref:System.Windows.RoutedEvent> pole jako identyfikator, który udostępnia metody identyfikacji niezawodne zdarzeń, która nie wymaga statyczne lub w czasie wykonywania odbicia.  
  
### <a name="how-routed-events-are-implemented"></a>Jak kierowane zdarzenia są implementowane.  
 Kierowanego zdarzenia jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenie, które nie jest obsługiwana przez wystąpienie <xref:System.Windows.RoutedEvent> klasy i zarejestrowanego w aplecie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń systemu. <xref:System.Windows.RoutedEvent> Wystąpienia uzyskane z rejestracji jest zazwyczaj przechowywany jako `public` `static` `readonly` członek pola klasy, która rejestruje i w związku z tym "właścicielem" kierowanego zdarzenia. Połączenia o identycznej nazwie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenia (która jest czasami określane jako zdarzenie "otoki") odbywa się przez zastąpienie `add` i `remove` implementacji dla [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń. Zwykle `add` i `remove` pozostało jako niejawne domyślny, który używa składni odpowiedniego zdarzenia specyficzne dla języka Dodawanie i usuwanie programów obsługi tego zdarzenia. Mechanizm tworzenia kopii i połączenia kierowanego zdarzenia jest podobny do sposobu właściwość zależności jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwość, która nie jest obsługiwana przez <xref:System.Windows.DependencyProperty> klasy i zarejestrowanego w aplecie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości systemu.  
  
 W poniższym przykładzie przedstawiono deklaracji niestandardowych `Tap` kierowanego zdarzenia, w tym rejestracji i ujawnienia <xref:System.Windows.RoutedEvent> pole identyfikatora i `add` i `remove` implementacji dla `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń.  
  
 [!code-csharp[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
 [!code-vb[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]  
  
### <a name="routed-event-handlers-and-xaml"></a>Programy obsługi zdarzeń routingiem i języka XAML  
 Aby dodać obsługę zdarzeń przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], Nazwa zdarzenia zadeklarować jako atrybut na elemencie, który jest odbiornik zdarzeń. Wartość atrybutu jest nazwą metody obsługi zaimplementowanym musi istnieć w klasie częściowej pliku CodeBehind.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Składnia wykorzystywana do dodawania standard [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] procedury obsługi zdarzeń jest taki sam dla dodanie obsługi kierowanego zdarzenia, ponieważ są naprawdę Dodawanie obsługi do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] otoki zdarzenie, którego implementacja kierowanego zdarzenia poniżej. Aby uzyskać więcej informacji o dodawaniu obsługi zdarzeń w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="routing_strategies"></a>   
## <a name="routing-strategies"></a>Strategii routingu  
 Przesłane Użyj zdarzeń, jednego z trzech strategii routingu:  
  
-   **Propagacji:** są wywoływane programy obsługi zdarzeń w źródle zdarzeń. Do momentu osiągnięcia głównego drzewa elementu kierowanego zdarzenia kieruje do nadrzędnego kolejnych elementów. Najbardziej kierowane zdarzenia użyj propagacji strategii routingu. Propagacji kierowane zdarzenia są zazwyczaj używane do zgłaszania danych wejściowych lub stanu zmiany z różnych formantów lub inne elementy interfejsu użytkownika.  
  
-   **Bezpośrednie:** tylko samego elementu źródła jest możliwość wywołania programy obsługi zdarzeń w odpowiedzi. To jest odpowiednikiem "routingu" który [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] używa zdarzeń. Jednak w przeciwieństwie do standardowego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń, bezpośrednie kierowane zdarzenia obsługiwać klasy (Obsługa klasa znajduje się w następnej sekcji) i mogą być używane przez <xref:System.Windows.EventSetter> i <xref:System.Windows.EventTrigger>.  
  
-   **Tunelowanie:** początkowo są wywoływane programy obsługi zdarzeń w katalogu głównym drzewa elementu. Następnie kierowanego zdarzenia porusza się trasę przy użyciu elementów podrzędnych kolejnych wzdłuż trasa kierunku elementu węzła, który jest źródłem kierowanego zdarzenia (element kierowanego zdarzenia wywoływane). Tunelowania kierowane zdarzenia są często używane lub traktowane jako część składania do sterowania tak, aby zdarzenia z części złożone można celowo pominięty lub zastąpione przez zdarzenia, które są specyficzne dla pełnej kontroli. Dane wejściowe zdarzenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] często mają zaimplementowany jako para tunelowania propagacji. Zdarzenia tunelowania są czasami określane jako Podgląd zdarzeń, z powodu konwencji nazewnictwa, która jest używana dla par.  
  
<a name="why_use"></a>   
## <a name="why-use-routed-events"></a>Dlaczego zdarzenia rozsyłane użycia?  
 Jako Deweloper aplikacji zawsze zbędna, nie wiadomo lub szczególną uwagę, że zdarzenie, które są obsługi jest zaimplementowany jako kierowanego zdarzenia. Kierowane zdarzenia mają specjalnego zachowania, ale to zachowanie jest przede wszystkim niewidoczne gdzie jest wywoływane są obsługi zdarzeń dla elementu.  
  
 Gdzie kierowane zdarzenia stają się zaawansowanego jest użycie dowolnego z sugerowanych scenariuszy: Definiowanie obsługi wspólnej w typowy katalog główny składania własne kontrolki lub własne kontrolki niestandardowej klasy definiującej.  
  
 Odbiorniki kierowanego zdarzenia i źródła kierowanego zdarzenia nie trzeba udostępniać typowych zdarzeń w ich hierarchii. Wszelkie <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> może to być odbiornik zdarzeń dla dowolnego kierowanego zdarzenia. W związku z tym można użyć pełnego zestawu kierowane zdarzenia dostępne w całej pracy [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] ustawić jako koncepcyjnej "interfejs" zgodnie z którymi różnych elementów w aplikacji może wymieniać informacje o zdarzeniach. To pojęcie "interfejsu" dla kierowane zdarzenia jest szczególnie przydatny dla zdarzenia wejściowe.  
  
 Kierowane zdarzenia mogą służyć do komunikacji za pośrednictwem elementu drzewa, ponieważ dane zdarzeń dla zdarzenia jest perpetuated do każdego elementu w trasie. Jeden element można zmienić w dane zdarzenia, a zmiana będzie dostępna do następnego elementu w trasie.  
  
 Inne niż aspekt routingu, istnieją dwie inne przyczyny tego żadnej podanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia mogą zostać zaimplementowane jako kierowanego zdarzenia zamiast standardowego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń. W przypadku wdrażania własne zdarzenia, można także rozważyć tych zasad:  
  
-   Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stylami i tworzenia szablonów funkcji, takich jak <xref:System.Windows.EventSetter> i <xref:System.Windows.EventTrigger> wymagają przywoływanego zdarzenia można kierowanego zdarzenia. Jest to scenariusz identyfikator zdarzenia wymienionych poniżej.  
  
-   Kierowane zdarzenia obsługuje klasy obsługę mechanizmem zgodnie z którymi klasy można określić metody statyczne, które mają możliwość obsługi kierowane zdarzenia przed obsługi żadnych zarejestrowanych wystąpienia mogą uzyskiwać do nich dostęp. Jest to przydatne w przypadku projektu z kontroli, ponieważ klasa może wymusić zachowania sterowane zdarzeniami klasy, które nie można pominąć przypadkowo dzięki obsłudze zdarzeń w wystąpieniu.  
  
 Każdy z powyższych zagadnienia omówione w osobnej sekcji tego tematu.  
  
<a name="event_handing"></a>   
## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Dodawanie i wdrażanie programu obsługi zdarzeń dla kierowanego zdarzenia  
 Aby dodać obsługę zdarzeń w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], wystarczy dodać do elementu jako atrybut nazwy zdarzenia i ustawić wartość atrybutu z nazwą obsługi zdarzeń, który implementuje odpowiedniego obiektu delegowanego, jak w poniższym przykładzie.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 `b1SetColor`Nazwa wdrożony program obsługi, który zawiera kod, który obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń. `b1SetColor`musi mieć taką samą sygnaturę jak <xref:System.Windows.RoutedEventHandler> delegata, która jest delegata obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń. Pierwszy parametr wszystkich delegatów obsługi kierowanego zdarzenia określa element, do którego jest dodawany program obsługi zdarzeń, a drugi parametr określa dane dla zdarzenia.  
  
[!code-csharp[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]  
  
 <xref:System.Windows.RoutedEventHandler>jest delegata obsługi podstawowych kierowanego zdarzenia. Dla kierowanego zdarzenia specjalnych niektórych formantów lub scenariuszy, delegatów do użycia na potrzeby obsługi zdarzeń routingiem również może stają się coraz bardziej wyspecjalizowane, tak, aby ich może przesyłać dane zdarzeń specjalnych. Na przykład w typowym scenariuszem wejściowych, może obsługiwać <xref:System.Windows.UIElement.DragEnter> kierowanego zdarzenia. Twoje obsługi powinien implementować <xref:System.Windows.DragEventHandler> delegowanie. Za pomocą specyficzny delegata, można przetwarzać <xref:System.Windows.DragEventArgs> obsługi i odczytu <xref:System.Windows.DragEventArgs.Data%2A> właściwości, która zawiera ładunek Schowka operacji przeciągania.  
  
 Aby uzyskać kompletny przykład sposobu dodawania obsługi zdarzeń do elementu przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [obsługi zdarzenia rozsyłane](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
 Dodawanie obsługi kierowanego zdarzenia w aplikacji, która jest tworzona w kodzie jest prosta. Programy obsługi zdarzeń routingiem zawsze można dodać za pomocą metody pomocnika <xref:System.Windows.UIElement.AddHandler%2A> (która jest sama metoda, która wymaga istniejącego zapasowy `add`.) Jednak istniejące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kierowane zdarzenia mają zwykle kopii implementacje `add` i `remove` logikę, która umożliwia obsługę kierowane zdarzenia, które ma zostać dodana przez składni zdarzenia specyficzne dla języka, który jest bardziej intuicyjne składni niż metoda pomocnika. Poniżej przedstawiono przykład użycia metody pomocniczej:  
  
 [!code-csharp[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
 [!code-vb[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]  
  
 W następnym przykładzie pokazano [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] składni operatora ([!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)] ma składnię operatora nieco inny ze względu na jego obsługa usunięcia odwołania):  
  
 [!code-csharp[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
 [!code-vb[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]  
  
 Na przykład sposobu obsługi zdarzeń w kodzie zobacz [Dodaj kod przy użyciu programu obsługi zdarzeń](../../../../docs/framework/wpf/advanced/how-to-add-an-event-handler-using-code.md).  
  
 Jeśli używasz [!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)], można również użyć `Handles` — słowo kluczowe, aby dodać deklaracje obsługi w ramach obsługi. Aby uzyskać więcej informacji, zobacz [Visual Basic i obsługi zdarzeń WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="concept_handled"></a>   
### <a name="the-concept-of-handled"></a>Obsługiwane pojęcia  
 Wszystkie zdarzenia routingiem udostępnianie typowych zdarzeń danych klasy podstawowej, <xref:System.Windows.RoutedEventArgs>. <xref:System.Windows.RoutedEventArgs>definiuje <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość, która przyjmuje wartość logiczną. Celem <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwości jest włączenie obsługi zdarzeń, wszelkie wzdłuż trasy, aby oznaczyć kierowanego zdarzenia jako *obsługiwane*, ustawiając wartość <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true`. Po przetworzeniu przez program obsługi w jeden element marszruty dane zdarzenia udostępnionych ponownie został zgłoszony dla każdego odbiornika wzdłuż trasy.  
  
 Wartość <xref:System.Windows.RoutedEventArgs.Handled%2A> wpływa na sposób kierowanego zdarzenia jest zgłosił lub przetworzone podczas przekazywania dalej w tym samym trasy. Jeśli <xref:System.Windows.RoutedEventArgs.Handled%2A> jest `true` zdarzeń dane dotyczące kierowanego zdarzenia, a następnie obsługi, które nasłuchują tego kierowanego zdarzenia na inne elementy zazwyczaj są wywoływane już dla danego wystąpienia określonego zdarzenia. Dotyczy to zarówno dla programów obsługi dołączona w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i programów obsługi dodane przez składni załącznika obsługi zdarzenia specyficzne dla języka, takich jak `+=` lub `Handles`. W przypadku najbardziej typowych scenariuszy obsługi oznaczenie zdarzenia jako obsługiwany dzięki ustawieniu <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true` "przestanie" routingu dla trasy tunelowania lub propagacji trasy, a także dla dowolnego zdarzenia, który jest obsługiwany w danym punkcie trasy przez program obsługi klasy.  
  
 Istnieje jednak mechanizm "handledEventsToo", zgodnie z którymi odbiorników mogą nadal działać obsługi w odpowiedzi na zdarzenia routingiem gdzie <xref:System.Windows.RoutedEventArgs.Handled%2A> jest `true` w danych zdarzenia. Innymi słowy trasy zdarzenia nie jest rzeczywiście zatrzymane przez oznaczenie dane zdarzenia, ponieważ obsługiwane. Mechanizm handledEventsToo można używać tylko w kodzie, lub w <xref:System.Windows.EventSetter>:  
  
-   W kodzie, zamiast używać składni zdarzenia specyficzne dla języka, który działa w przypadku ogólnych [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] wywołania zdarzenia, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metody <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> do sieci programu obsługi dodawania. Określ wartość `handledEventsToo` jako `true`.  
  
-   W <xref:System.Windows.EventSetter>ustaw <xref:System.Windows.EventSetter.HandledEventsToo%2A> atrybut był `true`.  
  
 Oprócz zachowania który <xref:System.Windows.RoutedEventArgs.Handled%2A> stanu tworzy w kierowane zdarzenia, pojęcie <xref:System.Windows.RoutedEventArgs.Handled%2A> ma wpływ na sposób powinien Utwórz projekt swojej aplikacji i napisać kod obsługi zdarzenia. Można conceptualize <xref:System.Windows.RoutedEventArgs.Handled%2A> jako prosty protokół, który jest udostępniany przez kierowane zdarzenia. Dokładnie sposób użycia tego protokołu zależy od można, ale projekt koncepcyjny jak wartość <xref:System.Windows.RoutedEventArgs.Handled%2A> jest przeznaczony do użycia jest następująca:  
  
-   Jeśli kierowanego zdarzenia jest oznaczony jako obsługiwany, następnie nie musi być ponownie obsługiwane przez inne elementy wzdłuż tej trasy.  
  
-   Jeśli kierowanego zdarzenia nie jest oznaczony jako obsługiwany, a następnie inne odbiorników, która była wcześniej marszruty wybrano albo nie można zarejestrować obsługi lub obsługi, które zostały zarejestrowane wybranego nie do manipulowania danymi zdarzenia i ustawić <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true`. (Można także oczywiście jest możliwe, że bieżący odbiornika jest pierwszego punktu w trasie). Programów obsługi na bieżącym odbiornika ma teraz trzy możliwych sposobów działania:  
  
    -   Nie podejmuj żadnej akcji na wszystkich; Zdarzenie pozostaje nieobsłużony i zdarzenia kieruje do następnego odbiornika.  
  
    -   Wykonanie kodu w odpowiedzi na zdarzenie, ale należy określenie, że akcję wykonywaną nie jest istotne, aby zagwarantować oznaczenie zdarzenie, ponieważ obsługiwane. Trasy zdarzenia do następnego odbiornika.  
  
    -   Wykonanie kodu w odpowiedzi na zdarzenia. Oznaczenie zdarzeń zgodnie z obsługi zdarzeń dane przekazywane do programu obsługi, ponieważ akcję wykonywaną został uznany za istotne, aby zagwarantować oznaczanie jako obsługi. Zdarzenie nadal kieruje do następnego odbiornika, ale z <xref:System.Windows.RoutedEventArgs.Handled%2A> = `true` danych zdarzeń, dlatego tylko `handledEventsToo` odbiorników mieć możliwość dalszego wywołania obsługi.  
  
 Ten projekt koncepcyjny zostało potwierdzone przez działanie routingu wymienionych poniżej: trudniej jest (mimo że nadal możliwe w kodzie lub style) można dołączyć obsługi kierowane zdarzenia wywoływane nawet wtedy, gdy poprzednią procedurę obsługi marszruty została już ustawiona <xref:System.Windows.RoutedEventArgs.Handled%2A>do `true`.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.RoutedEventArgs.Handled%2A>klasy obsługi zdarzenia rozsyłane i zaleceń dotyczących gdy jest odpowiednie do oznaczania kierowanego zdarzenia jako <xref:System.Windows.RoutedEventArgs.Handled%2A>, zobacz [oznaczenie kierowane zdarzenia jako Handled i obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 W aplikacjach jest dość często tylko obsługi propagacji kierowanego zdarzenia na obiekt, który wywołał go i nie trzeba się troszczyć o charakterystyce routingu zdarzenia w ogóle. Jednak nadal jest dobrym rozwiązaniem jest oznaczenie kierowanego zdarzenia jako obsługiwane w przypadku danych, aby zapobiec nieprzewidziane skutki uboczne, na wypadek element, który jest dalsze w górę drzewa element ma również obsługi dołączonych do tej samej kierowanego zdarzenia.  
  
<a name="class_handlers"></a>   
## <a name="class-handlers"></a>Obsługę klas  
 Jeśli definiujesz klasy pochodnej w jakiś sposób z <xref:System.Windows.DependencyObject>, można również zdefiniować i dołączyć klasy obsługę kierowanego zdarzenia, który jest elementem członkowskim zdarzenie zadeklarowane lub dziedziczonej klasie. Klasy obsługi są wywoływane przed obsługi odbiornika wszystkie wystąpienia, które są dołączone do wystąpienia tej klasy, gdy wystąpienie elementu w jego trasy osiągnie kierowanego zdarzenia.  
  
 Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty mają związanego z używaniem klasy obsługi dla niektórych kierowane zdarzenia. Może to zapewnić na zewnątrz wygląd kierowanego zdarzenia nigdy nie jest wywoływane, ale w rzeczywistości jest on obsługiwany klasy i kierowanego zdarzenia nadal potencjalnie może być obsługiwanych przez programu obsługi wystąpienia, korzystając z określonych technik. Ponadto wielu klas podstawowych i formanty uwidacznia metody wirtualne, które mogą służyć do zastępowania klasy zachowaniu obsługi. Aby uzyskać więcej informacji, zarówno na temat sposobu obejścia Obsługa niepożądane klasy i na definiowanie własnych klasy obsługi niestandardowej klasy, zobacz [oznaczenie kierowane zdarzenia jako Handled i obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="attached_events"></a>   
## <a name="attached-events-in-wpf"></a>Dołączone zdarzenia na platformie WPF  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Języka definiuje również specjalny typ zdarzenia o nazwie *dołączone zdarzenie*. Dołączone zdarzenie umożliwia dodanie obsługi dla określonego zdarzenia do dowolnego elementu. Element obsługi zdarzenia należy zdefiniować lub nie dziedziczy dołączone zdarzenie, a obiekt potencjalnie wywołaniem zdarzenia ani wystąpienia docelowego Obsługa należy zdefiniować lub w przeciwnym razie "właścicielem" zdarzenie jako element członkowski klasy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] System wejściowy często używa dołączone zdarzenia. Jednak prawie wszystkie te dołączone zdarzenia są przekazywane za pośrednictwem podstawowych elementów. Zdarzenia wejściowe następnie widoczna jako równoważne niedołączoną kierowane zdarzenia, które są członkami klasa elementu base. Na przykład podstawowa dołączone zdarzenia <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> więcej łatwo są obsługiwane na żadnym podane <xref:System.Windows.UIElement> za pomocą <xref:System.Windows.UIElement.MouseDown> na tej <xref:System.Windows.UIElement> zamiast zajmujących składni dołączone zdarzenie albo w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kodu.  
  
 Aby uzyskać więcej informacji na temat dołączone zdarzenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [dołączony Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>   
## <a name="qualified-event-names-in-xaml"></a>Nazwy kwalifikowanej zdarzeń w języku XAML  
 Inny użycie składni podobny *typename*. *eventName* dołączony składni zdarzeń, ale nie jest mówiąc ściślej jest użycie dołączone zdarzenie po dołączeniu obsługi kierowane zdarzenia, które zostały zgłoszone przez elementy podrzędne. Programy obsługi można dołączyć do Wspólnemu elementowi nadrzędnemu, aby móc korzystać z routingu zdarzeń, mimo że Wspólnemu elementowi nadrzędnemu może nie mieć odpowiednich kierowanego zdarzenia jako element członkowski. Należy wziąć pod uwagę w tym przykładzie ponownie:  
  
 [!code-xaml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 W tym miejscu odbiornika elementu nadrzędnego, gdzie jest dodawany program obsługi jest <xref:System.Windows.Controls.StackPanel>. Jednak jest dodanie obsługi kierowanego zdarzenia, została zadeklarowana, który zostanie wygenerowany przez <xref:System.Windows.Controls.Button> klasy (<xref:System.Windows.Controls.Primitives.ButtonBase> rzeczywiście, ale można <xref:System.Windows.Controls.Button> poprzez dziedziczenie). <xref:System.Windows.Controls.Button>"właścicielem" zdarzenia, ale kierowanego zdarzenia system zezwala programy obsługi dowolnej kierowanego zdarzenia jest dołączony do żadnej <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> odbiornika wystąpienia, które w przeciwnym razie można dołączyć odbiorników dla [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] zdarzeń. Domyślnej przestrzeni nazw xmlns te nazwy atrybutu kwalifikowaną zdarzeń jest zazwyczaj domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przestrzeni nazw xmlns, ale można również określić prefiksem przestrzeni nazw dla niestandardowego kierowane zdarzenia. Aby uzyskać więcej informacji na temat xmlns, zobacz [przestrzeń nazw XAML i Namespace mapowanie WPF XAML](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="how_event_processing_works"></a>   
## <a name="wpf-input-events"></a>Zdarzenia wejściowe WPF  
 Jeden częstego stosowania kierowane zdarzenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platforma to dla zdarzenia wejściowe. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tunelowania kierowane zdarzenia nazwy są poprzedzone wyrazem "W wersji zapoznawczej" Konwencji. Zdarzenia wejściowe często mają parami, jeden propagacji zdarzeń, a druga jest tunelowania zdarzeń. Na przykład <xref:System.Windows.ContentElement.KeyDown> zdarzeń i <xref:System.Windows.ContentElement.PreviewKeyDown> zdarzeń ma taką samą sygnaturę z nią trwa propagacji zdarzenie wejściowe i ostatni trwa tunelowania wejściowego zdarzeń. Czasami zdarzenia wejściowe ma tylko propagacji wersji lub prawdopodobnie tylko bezpośrednie routingiem wersji. W dokumentacji tematy dotyczące kierowanego zdarzenia wstawienia odsyłacza kierowanego zdarzenia podobne z alternatywnych strategii routingu Jeśli istnieją takie kierowane zdarzenia i sekcje na stronach zarządzane odniesienia wyjaśnienia strategii routingu każdego kierowanego zdarzenia.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wejściowy zdarzenia, które są dostępne w pary są implementowane tak, aby jednego działania użytkownika z danych wejściowych, takich jak naciśnięcie przycisku myszy zostanie podniesiony zarówno kierowane zdarzenia pary w sekwencji. Najpierw tunelowania zdarzenie jest wywoływane i podróżuje trasę. Następnie propagacji zdarzenie jest wywoływane i podróżuje trasę. Dwa zdarzenia dosłownie współużytkują to samo wystąpienie danych zdarzeń, ponieważ <xref:System.Windows.UIElement.RaiseEvent%2A> wywołanie metody implementującej klasy, który wywołuje zdarzenie propagacji nasłuchuje dane zdarzeń z tunelowania zdarzeń i ponownie go w nowym zdarzeniem zgłoszono. Odbiorniki z obsługą tunelowania zdarzenia mają pierwsza okazja, aby oznaczyć kierowanego zdarzenia obsługiwane (obsługę klas, następnie wystąpienie obsługi). Jeśli element wzdłuż trasy tunelowania oznaczył kierowanego zdarzenia obsługiwane, dane już obsługi zdarzeń jest wysyłany na propagacji zdarzenia i typowych programów obsługi dołączonych do jego odpowiednik propagacji zdarzenia wejściowe nie zostaną wywołane. Aby na zewnątrz wygląd będzie, tak, jakby obsłużone zdarzeń propagacji nie ma jeszcze wywoływane. To zachowanie obsługa przydaje się do składania kontroli, których może zajść wszystkich testów trafień na podstawie wejściowy lub zdarzenia na podstawie fokusu wprowadzania przekazywanych przez końcowego formantu zamiast jego części złożonego. Element końcowej kontroli zbliżonej do katalogu głównego w składania i w związku z tym ma możliwość klasy obsługi zdarzeń tunelowania najpierw i być może do "replace" tego kierowanego zdarzenia ze zdarzeniem bardziej specyficzne dla formantu, jako części kodu, aby utworzyć kopię zapasową formantu Klasa.  
  
 Ilustracją przetwarzania działa jak wejściowych zdarzeń należy wziąć pod uwagę w poniższym przykładzie zdarzenie wejściowe. Na poniższej ilustracji drzewa `leaf element #2` jest elementem źródłowym `PreviewMouseDown` , a następnie `MouseDown` zdarzeń.  
  
 ![Diagram routingu zdarzeń](../../../../docs/framework/wpf/advanced/media/wcsdkcoreinputevents.png "wcsdkCoreInputEvents")  
Zdarzenie wejściowe propagacji i tunelowania  
  
 Kolejność przetwarzania zdarzeń wygląda następująco:  
  
1.  `PreviewMouseDown`(tunelowania) dla elementu głównego.  
  
2.  `PreviewMouseDown`(tunelowania) w elemencie pośredniego #1.  
  
3.  `PreviewMouseDown`(tunelowania) w źródłowym elemencie #2.  
  
4.  `MouseDown`(bąbelkowy) w źródłowym elemencie #2.  
  
5.  `MouseDown`(bąbelkowy) w elemencie pośredniego #1.  
  
6.  `MouseDown`(bąbelkowy) dla elementu głównego.  
  
 Delegata obsługi kierowanego zdarzenia zawiera odwołania do dwóch obiektów: obiekt, który wywołał zdarzenie i obiektu, gdy została wywołana przez program obsługi. Obiekt przywołane program obsługi jest obiekt zgłoszone przez `sender` parametru. Obiektu, w którym zdarzenie został wywołany po raz pierwszy został zgłoszony przez <xref:System.Windows.RoutedEventArgs.Source%2A> właściwości w danych zdarzenia. Można nadal kierowanego zdarzenia wywoływane i obsługiwane przez ten sam obiekt, w którym to przypadku `sender` i <xref:System.Windows.RoutedEventArgs.Source%2A> (jest to w przypadku kroki 3 i 4 w przypadku przetwarzania przykładową listę) są identyczne.  
  
 Z powodu tunelowania i propagacji, elementy nadrzędne odbierania zdarzeń wejściowych gdzie <xref:System.Windows.RoutedEventArgs.Source%2A> jest jednym z ich podrzędnych elementów. Jeśli ważne jest, aby dowiedzieć się, co to jest element źródła, uzyskując dostęp do można zidentyfikować elementu źródła <xref:System.Windows.RoutedEventArgs.Source%2A> właściwości.  
  
 Zwykle gdy zdarzenie wejściowe jest oznaczony <xref:System.Windows.RoutedEventArgs.Handled%2A>, dalsze nie są wywoływane programy obsługi. Zazwyczaj zdarzenia wejściowe należy oznaczyć jako obsługiwane natychmiast po wywołaniu obsługi adresów logicznych obsługę specyficzne dla aplikacji z znaczenie zdarzenia wejściowego.  
  
 Wyjątkiem od tej instrukcji ogólne informacje <xref:System.Windows.RoutedEventArgs.Handled%2A> stanu jest, że wprowadź programów obsługi zdarzeń zarejestrowane celowo zignorowanie <xref:System.Windows.RoutedEventArgs.Handled%2A> stanu danych zdarzeń nadal będzie można wywołać wzdłuż albo trasy. Aby uzyskać więcej informacji, zobacz [Podgląd zdarzeń](../../../../docs/framework/wpf/advanced/preview-events.md) lub [oznaczenie kierowane zdarzenia jako Handled i obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 Modelu danych zdarzeń udostępnionego między zdarzenia tunelowania i propagacji i sekwencyjne wywoływanie pierwszy tunelowania, następnie propagacji zdarzeń, nie jest pojęcie dotyczy ogólnie wszystkich kierowane zdarzenia. Zachowanie w szczególności jest implementowany przez jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] urządzenia wejściowe chce podnieść i połącz pary zdarzenie wejściowe. Implementowanie zdarzeń wejściowych jest zaawansowanym scenariuszu, ale można również wykonać modelu dla zdarzeń wejściowych.  
  
 Niektóre klasy wybrać dojście-do-klasy określone zdarzenia wejściowe, zwykle z celem ponowne definiowanie określonego zdarzenia wejściowe użytkownika driven oznacza w tym formancie i wywoływanie nowe zdarzenie. Aby uzyskać więcej informacji, zobacz [oznaczenie kierowane zdarzenia jako Handled i obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 Aby uzyskać więcej informacji na dane wejściowe i interakcje dane wejściowe i zdarzeń w typowych scenariuszach, zobacz [wejściowych omówienie](../../../../docs/framework/wpf/advanced/input-overview.md).  
  
<a name="events_styles"></a>   
## <a name="eventsetters-and-eventtriggers"></a>EventSetters i EventTriggers  
 Style, można dołączyć niektórych wstępnie zadeklarowany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługi przy użyciu składni w znaczniku zdarzeń <xref:System.Windows.EventSetter>. Po zastosowaniu styl przywoływanego program obsługi jest dodane do wystąpienia styl. Można zadeklarować <xref:System.Windows.EventSetter> tylko w przypadku kierowanego zdarzenia. Poniżej przedstawiono przykład. Należy pamiętać, że `b1SetColor` metoda odwołujesz znajduje się w pliku CodeBehind.  
  
 [!code-xaml[EventOvwSupport#XAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]  
  
 Zaletą uzyskane w tym miejscu jest styl może zawierać wiele innych informacji, które można zastosować do dowolnego przycisku w aplikacji oraz <xref:System.Windows.EventSetter> być częścią tego stylu wspiera ponowne użycie kodu nawet na poziomie znaczników. Ponadto <xref:System.Windows.EventSetter> abstracts nazwy metod dla programów obsługi krok dalej od ogólnych znaczników aplikacji i strony.  
  
 Inną składnię specjalne łączy kierowanego zdarzenia i animacji funkcje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest <xref:System.Windows.EventTrigger>. Jak <xref:System.Windows.EventSetter>, tylko kierowane zdarzenia mogą być używane do <xref:System.Windows.EventTrigger>. Zazwyczaj <xref:System.Windows.EventTrigger> jest zadeklarowany jako część stylu, ale <xref:System.Windows.EventTrigger> również mogą być deklarowane w przypadku elementów na poziomie strony jako część <xref:System.Windows.FrameworkElement.Triggers%2A> kolekcji, lub w <xref:System.Windows.Controls.ControlTemplate>. <xref:System.Windows.EventTrigger> Umożliwia określenie <xref:System.Windows.Media.Animation.Storyboard> czy działa, gdy kierowanego zdarzenia osiągnie element trasę deklaruje <xref:System.Windows.EventTrigger> dla tego zdarzenia. Zaletą <xref:System.Windows.EventTrigger> za pośrednictwem po prostu obsługi zdarzenia i powoduje jej uruchamiania istniejących scenorysu jest to, że <xref:System.Windows.EventTrigger> zapewnia lepszą kontrolę nad scenorysu i jego zachowania w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [wyzwalacze zdarzeń używana do sterowania scenorysu po jego uruchomieniu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
<a name="more_about"></a>   
## <a name="more-about-routed-events"></a>Więcej informacji na temat kierowane zdarzenia  
 W tym temacie omówiono przede wszystkim kierowane zdarzenia z punktu widzenia zawierająca opis podstawowych pojęć i oferty wskazówki na temat i odpowiedzieć na kierowane zdarzenia, które są już obecne w różnych podstawowych elementów i kontrolek. Jednak można utworzyć własne kierowanego zdarzenia na klasę niestandardową oraz wszystkie niezbędne wsparcie, takich jak zdarzenia specjalne danych klasy i delegaci. Właściciel kierowanego zdarzenia może być dowolną klasę, ale kierowane zdarzenia muszą być wywoływane przez i obsługiwane przez <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> klas pochodnych była użyteczna. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [utworzyć niestandardowe zdarzenia rozsyłane](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.EventManager>  
 <xref:System.Windows.RoutedEvent>  
 <xref:System.Windows.RoutedEventArgs>  
 [Oznaczanie zdarzeń trasowanych jako obsłużonych oraz obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Przegląd danych wejściowych](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Przegląd poleceń](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Drzewa w WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [Słabe wzorce zdarzeń](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)
