---
title: Przegląd Zdarzenia trasowane
ms.date: 03/30/2017
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
ms.openlocfilehash: a6baf073e25635f0a6dd666d681d8bc641128ea0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982374"
---
# <a name="routed-events-overview"></a>Przegląd Zdarzenia trasowane
W tym temacie opisano pojęcia zdarzenia trasowane w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Temat definiuje zdarzenia trasowane terminologii, w tym artykule opisano sposób zdarzenia trasowane są przesyłane za pośrednictwem drzewa elementów, podsumowano, jak obsługiwać zdarzenia trasowane i wyjaśniono, jak tworzyć własne niestandardowe zdarzenia trasowane.
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że masz podstawową wiedzę na temat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] i programowanie zorientowane obiektowo, a także pojęcia jak relacje między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy mogą być conceptualized jako drzewa. Aby można było wykonać instrukcje opisane w przykładach w tym temacie, należy również mieć świadomość [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wiedzieć, jak napisać wykraczającego poza podstawowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji lub stron. Aby uzyskać więcej informacji, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) i [Przegląd XAML (WPF)](xaml-overview-wpf.md).  
  
<a name="routing"></a>   
## <a name="what-is-a-routed-event"></a>Co to jest zdarzenie trasowane?  
 Można to porównać zdarzenia trasowanego, albo z punktu widzenia funkcjonalności lub implementacji. Zarówno definicje są prezentowane w tym miejscu, ponieważ niektórzy znaleźć co najmniej innych definicji bardziej użyteczne.  
  
 Definicja funkcjonalności: Zdarzenia trasowanego jest typem zdarzenia, które można wywołać procedury obsługi na wiele odbiorników w drzewie elementu, a nie tylko na obiekt, który spowodował zdarzenie.  
  
 Definicja wdrożenia: To zdarzenie trasowane [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń, która jest wspierana przez wystąpienie <xref:System.Windows.RoutedEvent> klasy i są przez nią przetwarzane [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] system zdarzeń.  
  
 Typowa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja zawiera wiele elementów. Czy utworzonych w kodzie zadeklarowanych w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], te elementy znajdują się w elemencie drzewa relacji między sobą. Trasy zdarzenia mogą być przesyłane w jednym z dwóch kierunkach w zależności od definicji zdarzenia, ale zazwyczaj trasy przybliżone ilości tych danych z elementu źródłowego, a następnie "propaguje" w górę za pośrednictwem drzewa elementów aż do napotkania głównego drzewa elementu (zazwyczaj strony lub okno). To pojęcie propagacji musi być znane, użytkownicy mający doświadczenie z model obiektowy DHTML wcześniej.  
  
 Należy wziąć pod uwagę następujące drzewo prosty element:  
  
 [!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Ten element drzewa daje podobny do poniższego:  
  
 ![Tak, nie i przyciski "Anuluj"](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")  
  
 W tym drzewie uproszczone element źródła <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia jest jednym z <xref:System.Windows.Controls.Button> elementy i zależności <xref:System.Windows.Controls.Button> został kliknięty jest pierwszym elementem, który ma możliwość obsługi zdarzenia. Jednak jeśli żadna procedura obsługi nie jest dołączony do <xref:System.Windows.Controls.Button> działa na zdarzenie, a następnie zdarzenia będą pojawiać się do góry do <xref:System.Windows.Controls.Button> nadrzędnego w drzewie elementów, czyli <xref:System.Windows.Controls.StackPanel>. Ewentualnie bąbelków zdarzeń do <xref:System.Windows.Controls.Border>, a następnie poza do strony katalogu głównego drzewa elementów (niewyświetlany).  
  
 Innymi słowy, trasy zdarzenia dla tego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia:  
  
 Przycisk--> StackPanel--> obramowania-->...  
  
### <a name="top-level-scenarios-for-routed-events"></a>Scenariusze najwyższego poziomu dla zdarzenia trasowane  
 Poniżej przedstawiono krótkie podsumowanie scenariuszy, które uzasadnione pojęcia zdarzenia trasowanego i dlaczego jest to typowa [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń nie jest odpowiednia dla tych scenariuszy:  
  
 **Kompozycji formantu i hermetyzacji:** Różne formanty w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sformatowanego modelu zawartości. Na przykład możesz umieścić obraz wewnątrz <xref:System.Windows.Controls.Button>, która rozszerza skutecznie drzewo wizualne przycisku. Jednak dodano obrazu nie mogą przerwać działania zachowanie testowania trafień, który powoduje, że przycisk odpowiedzieć na <xref:System.Windows.Controls.Primitives.ButtonBase.Click> jego zawartości, nawet wtedy, gdy użytkownik kliknie piksele, które są pod względem technicznym część obrazu.  
  
 **Obsługi w liczbie pojedynczej punktami załącznika:** W [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], trzeba dołączyć wiele razy tę samą procedurę obsługi do przetwarzania zdarzeń, które może zostać wywołane z wieloma elementami. Zdarzenia trasowane umożliwiają dołączanie programu obsługi tylko raz, ponieważ został wyświetlony w poprzednim przykładzie, a następnie użyć logiki obsługi do określenia, zdarzenie pochodzenia w razie potrzeby. Na przykład może to być Obsługa pokazanych wcześniej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
 [!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]  
  
 **Obsługa klasy:** Kierowane zezwolenia zdarzeń statycznych program obsługi, który jest zdefiniowany w klasie. Ten program obsługi klasa ma możliwość obsługi zdarzenia przed obsługi wszelkich dołączonych wystąpienia.  
  
 **Odwołanie do zdarzenia bez odbicia:** Pewne techniki kodu i znaczników wymagają określenia sposobu identyfikowania określonego zdarzenia. Tworzy zdarzenie trasowane <xref:System.Windows.RoutedEvent> pola jako identyfikator, który zapewnia technika identyfikacji niezawodne zdarzeń, która nie wymaga statyczne lub w czasie wykonywania odbicia.  
  
### <a name="how-routed-events-are-implemented"></a>W jaki sposób są implementowane zdarzenia trasowane  
 To zdarzenie trasowane [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń, która jest wspierana przez wystąpienie <xref:System.Windows.RoutedEvent> klasy i zarejestrowanego w aplecie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system zdarzeń. <xref:System.Windows.RoutedEvent> Wystąpienia uzyskany z rejestracji są zwykle zachowywane jako `public` `static` `readonly` pole składowej klasy, która rejestruje i dlatego jego "właścicielem" zdarzenia trasowanego. Połączenie o identycznej nazwie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń (co jest czasami określane jako zdarzenie "otoki") odbywa się przez zastąpienie `add` i `remove` niedotyczące [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń. Zazwyczaj `add` i `remove` są pozostawiane jako niejawnego domyślnego, w której używana jest składnia odpowiedniego zdarzenia specyficzne dla języka umożliwiającą Dodawanie i usuwanie programów obsługi zdarzenia. Mechanizm tworzenia kopii i połączenia zdarzenia trasowanego jest podobna do jak właściwość zależności jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwość, która jest wspierana przez <xref:System.Windows.DependencyProperty> klasy i zarejestrowanego w aplecie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości systemu.  
  
 W poniższym przykładzie pokazano deklarację dla niestandardowego `Tap` zdarzenie trasowane, łącznie z rejestracji i ujawniania <xref:System.Windows.RoutedEvent> pole identyfikatora i `add` i `remove` niedotyczące `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń.  
  
 [!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
 [!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]  
  
### <a name="routed-event-handlers-and-xaml"></a>Programy obsługi zdarzeń trasowanych i XAML  
 Aby dodać program obsługi zdarzeń za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], został zadeklarowany Nazwa zdarzenia jako atrybut na element, który jest odbiornik zdarzeń. Wartość atrybutu jest nazwa metody obsługi zaimplementowano musi istnieć w klasie częściowej pliku CodeBehind.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Składni dodawania standard [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] procedury obsługi zdarzeń jest taka sama dla Dodawanie obsługi zdarzeń trasowanych, ponieważ są naprawdę Dodawanie programów obsługi do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] otoki zdarzeń, który zawiera implementację zdarzenia trasowanego poniżej. Aby uzyskać więcej informacji o dodawaniu programów obsługi zdarzeń w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [Przegląd XAML (WPF)](xaml-overview-wpf.md).  
  
<a name="routing_strategies"></a>   
## <a name="routing-strategies"></a>Strategie routingu  
 Kierowane Użyj zdarzeń, jednego z trzech strategie routingu:  
  
- **Bubbling:** Są wywoływane programy obsługi zdarzeń w źródle zdarzenia. Aż do osiągnięcia element główny drzewa zdarzenia trasowanego kieruje do elementów nadrzędnych kolejnych. Większość zdarzeń trasowanych używają propagacji strategii routingu. Propagacja zdarzeń trasowanych są zazwyczaj używane do zgłaszania zmian danych wejściowych lub stanu z różnych kontrolkę lub inne elementy interfejsu użytkownika.  
  
- **Bezpośrednie:** Element źródłowy, sama jest możliwość wywołania procedur obsługi w odpowiedzi. To jest odpowiednikiem "routing" który [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] używa zdarzeń. Jednak w przeciwieństwie do standardowego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń, bezpośrednie obsługiwać zdarzenia trasowane, klasa (Obsługa klasy jest opisana w następnej sekcji) i mogą być używane przez <xref:System.Windows.EventSetter> i <xref:System.Windows.EventTrigger>.  
  
- **Tunelowanie:** Początkowo są wywoływane programy obsługi zdarzeń na element główny drzewa. Zdarzenia trasowanego następnie przybliżone ilości tych danych trasę przez elementy podrzędne kolejnych wzdłuż trasy, elementu węzła, który jest źródłem zdarzeń trasowanych (element, który spowodował zdarzenie trasowane). Zdarzenia trasowane tunelowania są często używane lub obsługiwane jako część składania kontrolki, w taki sposób, że zdarzenia z części złożonego mogą być celowo pominięty lub zastąpione przez zdarzenia, które są specyficzne dla pełną kontrolę. Dane wejściowe zdarzenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] często jest opracowywane zaimplementowane jako para tunelowania Propagacja. Tunelowania zdarzenia są czasami określane jako zdarzenia (wersja zapoznawcza), ze względu na Konwencję nazewnictwa, która jest używana dla par.  
  
<a name="why_use"></a>   
## <a name="why-use-routed-events"></a>Dlaczego zdarzenia trasowanego użycia?  
 Jako Deweloper aplikacji nie zawsze należy znać lub się, że zdarzenia, które obsługujesz jest implementowana jako zdarzenie trasowane. Zdarzenia trasowane mają specjalne zachowanie, ale to zachowanie jest w dużej mierze niewidoczne, jeśli gdzie jest wywoływane są obsługi zdarzeń dla elementu.  
  
 Gdy zdarzenia trasowane stają się zaawansowane jest, jeśli używasz jednego z sugerowanych scenariuszy: Definiowanie często używanych procedur obsługi w typowy katalog główny składania własny formant lub Definiowanie klasy formantu niestandardowego.  
  
 Detektory zdarzenia trasowanego i źródła zdarzeń trasowanych nie muszą udostępniać typowe zdarzenia w jego hierarchii. Wszelkie <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> może to być odbiornik zdarzeń dla dowolnego zdarzenia trasowane. W związku z tym, można użyć pełnego zestawu zdarzenia trasowane, które są dostępne w całej pracy [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] ustawiona jako koncepcyjny "interfejs" zgodnie z którą różnych elementów w aplikacji mogą wymieniać informacje o zdarzeniu. To pojęcie "interfejsu" dla zdarzenia trasowane jest szczególnie przydatny dla zdarzenia wejściowe.  
  
 Zdarzenia trasowane można również komunikować się za pośrednictwem drzewa elementów, ponieważ dane zdarzeń dla zdarzenia jest perpetuated do każdego elementu w trasie. Jeden element można zmienić element dane zdarzenia, a ta zmiana będzie dostępny do następnego elementu w trasie.  
  
 Inne niż aspekt routingu, istnieją dwie inne przyczyny tego dowolnej podanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń można zaimplementować jako zdarzenia trasowanego zamiast standardowego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń. W przypadku wdrażania własnych zdarzeń można też rozważyć następujące zasady:  
  
- Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Tworzenie szablonów i stylów funkcje, takie jak <xref:System.Windows.EventSetter> i <xref:System.Windows.EventTrigger> odwołania zdarzeń do zdarzenia trasowanego wymagają. Jest scenariusz identyfikator zdarzenia wspomnianych wcześniej.  
  
- Zdarzenia trasowane obsługuje klasy obsługi mechanizmu, według której klasy można określić metody statyczne, które mają możliwość obsługi zdarzenia trasowane, zanim wszystkie procedury obsługi zarejestrowane wystąpienia można uzyskiwać do nich dostęp. Może to być przydatne w przypadku projektowania formantu, dlatego klasy mogą zostać wymuszone zachowania klasy oparte na zdarzeniach, których nie można pominąć przypadkowo dzięki obsłudze zdarzeń w wystąpieniu.  
  
 W osobnej sekcji w tym temacie omówiono każdego z powyższych zagadnienia.  
  
<a name="event_handing"></a>   
## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Dodawanie i wdrażanie program obsługi zdarzeń dla zdarzenia trasowanego  
 Aby dodać program obsługi zdarzeń w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], po prostu Dodaj nazwę zdarzenia do elementu jako atrybut i ustawić wartość atrybutu jako nazwę programu obsługi zdarzeń, która implementuje delegata odpowiednie, jak w poniższym przykładzie.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 `b1SetColor` jest nazwą zaimplementowano program obsługi, który zawiera kod, który obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń. `b1SetColor` musi mieć taką samą sygnaturę jak <xref:System.Windows.RoutedEventHandler> delegata, która jest delegata obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń. Pierwszy parametr wszystkich delegatów obsługi zdarzeń trasowanych określa element, do której jest dodawany program obsługi zdarzeń, a drugi parametr określa dane dla zdarzenia.  
  
[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]  
  
 <xref:System.Windows.RoutedEventHandler> jest delegata obsługi zdarzeń trasowanych w wersji basic. Zdarzenia trasowane, które są wyspecjalizowane w przypadku niektórych kontrolek lub scenariuszy delegatów dla procedur obsługi zdarzeń trasowanych również może stać się bardziej wyspecjalizowane, tak, aby ich mogą przesyłać dane zdarzenia wyspecjalizowanych. Na przykład w typowym scenariuszu danych wejściowych może obsługiwać <xref:System.Windows.UIElement.DragEnter> zdarzenia trasowanego. Należy zaimplementować programu obsługi <xref:System.Windows.DragEventHandler> delegować. Za pomocą delegowanego bardziej konkretny od pozostałych, może przetwarzać <xref:System.Windows.DragEventArgs> obsługi i odczytu <xref:System.Windows.DragEventArgs.Data%2A> właściwości, która zawiera ładunek Schowka operacji przeciągania.  
  
 Pełny przykład sposobu dodawania programu obsługi zdarzeń do elementu za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [obsłużyć zdarzenie kierowane](how-to-handle-a-routed-event.md).  
  
 Dodawanie obsługi dla zdarzenia trasowanego w aplikację, która jest tworzona w kodzie jest bardzo proste. Zawsze można dodać procedury obsługi zdarzeń trasowanych za pośrednictwem metody pomocnika <xref:System.Windows.UIElement.AddHandler%2A> (czyli tej samej metody, wywołuje istniejących zapasowy `add`.) Jednak istniejące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia trasowane reguły mają kopii implementacje `add` i `remove` Logic Apps, dzięki czemu programy obsługi dla zdarzenia trasowane, które mają zostać dodane przez składnię zdarzeń specyficznych dla języka, co jest bardziej intuicyjne działanie składnia niż metoda pomocnika. Poniżej przedstawiono przykład użycia metody pomocniczej:  
  
 [!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
 [!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]  
  
 W następnym przykładzie pokazano C# składni operatora (Visual Basic ma składni operatora nieco inny ze względu na jego obsługę wyłuskanie):  
  
 [!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
 [!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]  
  
 Na przykład sposobu dodawania programu obsługi zdarzeń w kodzie zobacz [Dodaj kod za pomocą procedury obsługi zdarzeń](how-to-add-an-event-handler-using-code.md).  
  
 Jeśli używasz języka Visual Basic umożliwia także `Handles` — słowo kluczowe do dodania obsługi jako część deklaracji programu obsługi. Aby uzyskać więcej informacji, zobacz [Visual Basic i obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="concept_handled"></a>   
### <a name="the-concept-of-handled"></a>Obsługiwane koncepcji  
 Wszystkie zdarzenia trasowane udostępnić typowych zdarzeń danych klasę bazową, <xref:System.Windows.RoutedEventArgs>. <xref:System.Windows.RoutedEventArgs> definiuje <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość, która przyjmuje wartość logiczną. Celem <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość jest włączenie dowolnego programu obsługi zdarzeń wzdłuż trasy, oznaczanie zdarzenia trasowanego jako *obsługiwane*, ustawiając wartość <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true`. Po przetworzeniu przez program obsługi w jeden element wzdłuż trasy dane zdarzenia udostępnionych jest ponownie zgłaszany w przypadku każdego odbiornika wzdłuż trasy.  
  
 Wartość <xref:System.Windows.RoutedEventArgs.Handled%2A> ma wpływ na sposób zdarzenia trasowanego jest zgłaszane lub przetworzone podczas przekazywania dalej w tym samym trasy. Jeśli <xref:System.Windows.RoutedEventArgs.Handled%2A> jest `true` w zdarzeniu dane dla zdarzenia trasowanego, a następnie programów obsługi, które nasłuchują tego zdarzenia trasowanego na inne elementy zazwyczaj są nie jest już wywoływane dla tego wystąpienia określonego zdarzenia. Dotyczy to zarówno dla programów obsługi dołączona w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i obsługi dodane przez składnie załącznika procedury obsługi zdarzeń specyficznych dla języka, takich jak `+=` lub `Handles`. W przypadku najbardziej typowych scenariuszy obsługi oznaczanie zdarzenia jako obsłużony, ustawiając <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true` będzie "Zatrzymaj" routingu dla trasy tunelowania lub propagacji trasy, a także dla dowolnego zdarzenia, które odbywa się w punkcie trasy przez program obsługi klasy.  
  
 Istnieje jednak mechanizm "handledEventsToo", według której odbiorników nadal można uruchomić procedury obsługi w odpowiedzi na zdarzenia trasowane gdzie <xref:System.Windows.RoutedEventArgs.Handled%2A> jest `true` danych zdarzenia. Innymi słowy trasy zdarzeń nie jest naprawdę wyłączana jako obsłużony, oznaczając dane zdarzenia. Mechanizm handledEventsToo można używać tylko w kodzie lub w <xref:System.Windows.EventSetter>:  
  
- W kodzie, a nie za pomocą składni zdarzenia specyficzne dla języka, który działa ogólne [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] wywoływać zdarzenia, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metoda <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> do dodawania programu obsługi. Określ wartość `handledEventsToo` jako `true`.  
  
- W <xref:System.Windows.EventSetter>ustaw <xref:System.Windows.EventSetter.HandledEventsToo%2A> atrybut był `true`.  
  
 Oprócz zachowania, <xref:System.Windows.RoutedEventArgs.Handled%2A> stanu tworzy w zdarzenia trasowane koncepcji <xref:System.Windows.RoutedEventArgs.Handled%2A> ma wpływ na sposób należy zaprojektować aplikację i napisać kod procedury obsługi zdarzeń. Można wyobrażenie <xref:System.Windows.RoutedEventArgs.Handled%2A> jako prosty protokół, który jest udostępniany przez zdarzenia trasowane. Dokładnie jak używać tego protokołu zależy od należy jednak projektowe dotyczące wartości <xref:System.Windows.RoutedEventArgs.Handled%2A> jest przeznaczony do użycia jest następująca:  
  
- Jeśli zdarzenia trasowanego jest oznaczony jako obsłużony, następnie go nie trzeba ponownie obsłużenia przez inne elementy wzdłuż tej trasy.  
  
- Jeśli zdarzenia trasowanego nie jest oznaczony jako obsłużony, a następnie innych nasłuchujących, która była wcześniej wzdłuż trasy wybrał opcję nie, aby zarejestrować program obsługi lub obsługi, które zostały zarejestrowane wybierz opcję nie, aby wykonywać operacje na danych zdarzenia i ustawić <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true`. (Można także oczywiście jest to możliwe, że bieżący odbiornika jest pierwszym punktem w trasie). Programy obsługi odbiornik bieżącego mają teraz trzy możliwe kursów akcji:  
  
    - Nie podejmuj żadnych działań w ogóle; Zdarzenie pozostaje nieobsłużony i zdarzenia kieruje połączenia z odbiornikiem dalej.  
  
    - Wykonanie kodu w odpowiedzi na zdarzenie, ale wprowadzać określenie, że akcję podejmowaną nie jest istotne, aby gwarantowało to oznaczenie zdarzenia jako obsługiwane. Trasy zdarzeń do następnego odbiornika.  
  
    - Wykonanie kodu w odpowiedzi na zdarzenie. Znacznik zdarzenia jako obsługiwane w przypadku danych przekazanych do programu obsługi, ponieważ akcję podejmowaną został uznany za istotne, aby gwarantowało oznaczanie jako obsługiwane. Zdarzenie nadal kieruje połączenia z odbiornikiem dalej, ale z <xref:System.Windows.RoutedEventArgs.Handled%2A> = `true` w danych zdarzeń, dlatego tylko `handledEventsToo` odbiorników mieć możliwość dalszego wywoływanie programów obsługi.  
  
 Ten projekt koncepcyjny wspiera zachowania routingu, o których wspomniano wcześniej: trudniej jest (chociaż jest to możliwe, w kodzie lub style) można dołączyć programy obsługi dla zdarzenia trasowane, które są wywoływane, nawet jeśli poprzednie obsługi wzdłuż trasy już ustawił <xref:System.Windows.RoutedEventArgs.Handled%2A>do `true`.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.RoutedEventArgs.Handled%2A>, obsługę klasy dla zdarzenia trasowanego i zalecenia dotyczące znajduje się w odpowiednich do oznaczania zdarzenia trasowanego jako <xref:System.Windows.RoutedEventArgs.Handled%2A>, zobacz [oznaczanie zdarzeń trasowanych jako Handled oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md).  
  
 W przypadku aplikacji jest dość często po prostu obsługi propagacji zdarzenia trasowanego w obiekcie, który spowodował jego i nie są związani z właściwości routingu zdarzeń na wszystkich. Jednak nadal jest dobrym rozwiązaniem, aby oznaczyć zdarzenia trasowanego jako obsługiwane w przypadku danych, aby zapobiec nieprzewidziane efekty uboczne, na wypadek element, który jest dalsze w górę drzewa elementów ma również dołączony do tego samego zdarzenia trasowane program obsługi.  
  
<a name="class_handlers"></a>   
## <a name="class-handlers"></a>Funkcje obsługi klas  
 Jeśli definiujesz klasy pochodnej w jakiś sposób z <xref:System.Windows.DependencyObject>, można również zdefiniować i dołączyć program obsługi klasy dla zdarzenia trasowanego, który jest elementem członkowskim zdarzenie zadeklarowane lub dziedziczone klasy. Klasa procedury obsługi są wywoływane przed obsługi odbiornika wszystkie wystąpienia, które są dołączone do wystąpienia tej klasy, zawsze wtedy, gdy zdarzenie trasowane osiągnie wystąpienie elementu w jego trasę.  
  
 Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty mają nieprzerwaną pracę obsługę klasy dla określonych zdarzeń trasowanych. To może nadać wygląd na zewnątrz zdarzenia trasowanego nigdy nie jest inicjowane, ale w rzeczywistości jest klasa obsługiwane i zdarzenia trasowanego nadal potencjalnie może zostać obsłużony przez inne programy obsługi wystąpienia, jeśli używasz niektórych technik. Ponadto wiele klas podstawowych i formanty ujawniać metod wirtualnych, które mogą służyć do zastępowania obsługę zachowanie klasy. Aby uzyskać więcej informacji, zarówno na sposób obejścia niepożądane klasy obsługi i definiowanie własnych klasy obsługi niestandardowej klasy, zobacz [oznaczanie zdarzeń trasowanych jako Handled oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="attached_events"></a>   
## <a name="attached-events-in-wpf"></a>Zdarzenia dołączone w WPF  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Język również definiuje specjalny rodzaj zdarzeń o nazwie *dołączone zdarzenie*. Dołączone zdarzenie umożliwia dodawanie obsługi dla określonego zdarzenia do dowolnego elementu. Element obsługi zdarzenia należy zdefiniować lub nie dziedziczą dołączone zdarzenie, a obiekt potencjalnie podnoszonego zdarzenia ani wystąpienia docelowego obsługi, należy zdefiniować lub w przeciwnym razie "własnością" tego zdarzenia jako członek klasy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] System wejściowy często używa dołączone zdarzenia. Jednak prawie wszystkich tych dołączone zdarzenia są przekazywane za pośrednictwem podstawowych elementów. Zdarzenia wejściowe są następnie wyświetlane jako odpowiednik niedołączonych kierowane zdarzenia, które należą do klasy bazowej elementów. Na przykład podstawowa dołączone zdarzenie <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> więcej łatwo są obsługiwane w przypadku dowolnego danego <xref:System.Windows.UIElement> przy użyciu <xref:System.Windows.UIElement.MouseDown> na tym <xref:System.Windows.UIElement> zamiast rozwiązywania problemów związanych ze składnią dołączone zdarzenie albo w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kodu.  
  
 Aby uzyskać więcej informacji na temat zdarzenia dołączone w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Przegląd zdarzeń dołączonych](attached-events-overview.md).  
  
<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>   
## <a name="qualified-event-names-in-xaml"></a>Nazwy kwalifikowane zdarzeń w XAML  
 Inny użycie składni, które przypomina *typename*. *eventName* dołączony składni zdarzenia, ale nie jest ściśle rzecz ujmując użycia dołączone zdarzenie jest po dołączeniu programy obsługi dla zdarzenia trasowane, które są wywoływane przez elementy podrzędne. Programy obsługi możesz dołączyć do wspólnego elementu nadrzędnego z zalet routingu zdarzeń, nawet jeśli nadrzędnego wspólnego może nie mieć odpowiednich zdarzenia trasowanego jako członka. Rozważmy następujący przykład ponownie:  
  
 [!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 W tym miejscu jest odbiornika elementu nadrzędnego, gdzie jest dodawany program obsługi <xref:System.Windows.Controls.StackPanel>. Jednak jest dodanie obsługi dla zdarzenia trasowanego został zadeklarowany, który zostanie wygenerowany przez <xref:System.Windows.Controls.Button> klasy (<xref:System.Windows.Controls.Primitives.ButtonBase> faktycznie, ale można <xref:System.Windows.Controls.Button> poprzez dziedziczenie). <xref:System.Windows.Controls.Button> jego "właścicielem" zdarzenia, ale obsługi zdarzenia trasowanego system zezwala dla dowolnego zdarzenia trasowane do podłączenia do dowolnego <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> odbiornika wystąpienia, które w przeciwnym razie można dołączyć detektory [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] zdarzeń. Domyślny obszar nazw xmlns te nazwy atrybutu kwalifikowaną zdarzeń zwykle jest ustawieniem domyślnym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przestrzeni nazw xmlns, ale można również określić prefiksem obszary nazw dla zdarzenia trasowanego niestandardowe. Aby uzyskać więcej informacji na temat xmlns zobacz [przestrzeni nazw XAML i Namespace mapowania dla WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="how_event_processing_works"></a>   
## <a name="wpf-input-events"></a>Zdarzenia wejściowe WPF  
 Jednej aplikacji często zdarzeń trasowanych w ramach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platformy dotyczy zdarzeń wejściowych. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tunelowanie kierowane nazwy są poprzedzone wyrazem "Podgląd" zgodnie z Konwencją zdarzenia. Zdarzenia wejściowe często jest opracowywane w parach, za pomocą jednego Propagacja zdarzeń i inne są tunelowania zdarzeń. Na przykład <xref:System.Windows.ContentElement.KeyDown> zdarzeń i <xref:System.Windows.ContentElement.PreviewKeyDown> zdarzenia mają taki sam podpis, z nią jest propagacja zdarzeń wejściowych oraz ostatni trwa tunelowania wejściowych zdarzeń. Czasami zdarzenia wejściowe mieć tylko propagacji wersji lub prawdopodobnie tylko bezpośredniego trasowane wersji. W dokumentacji programu tematy zdarzenia trasowanego uzyskane podobnych zdarzeń trasowanych z alternatywnych strategii routingu, jeśli istnieją takie zdarzenia trasowane i sekcji na stronie zarządzana dokumentacja dotycząca wyjaśnienia strategii routingu dla zdarzeń trasowanych.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia wejściowe, które są dostępne w pary są wdrażane tak, aby akcja pojedynczego użytkownika z danych wejściowych, takich jak naciśnięcie przycisku myszy zgłosi zarówno zdarzenia trasowane pary w sekwencji. Najpierw tunelowania zdarzenie jest zgłaszane i przybliżone ilości tych danych trasę. Następnie propagacji zdarzenie jest wywoływane i przybliżone ilości tych danych trasę. Dwa zdarzenia dosłownie udostępniać tego samego wystąpienie danych zdarzeń, ponieważ <xref:System.Windows.UIElement.RaiseEvent%2A> wywołania metody w klasie wykonawczych, która wywołuje zdarzenia propagacji nasłuchuje dane zdarzenia z tunelowania zdarzenia i są ponownie używane nowe zdarzenie zostaje zgłoszone. Odbiorniki z obsługą tunelowania zdarzenia mają pierwsza okazja, aby oznaczyć zdarzenia trasowanego obsługiwane (funkcje obsługi klas po pierwsze, następnie wystąpienia obsługi). Jeśli element wzdłuż trasy tunelowania oznaczone zdarzenia trasowanego jako obsłużony, dane już obsługi zdarzeń jest wysyłany na zdarzenia propagacji, a typowy obsługi dołączony dla równoważnego Propagacja zdarzeń wejściowych nie zostaną wywołane. Na zewnątrz wygląd będzie tak, jakby obsługiwanego propagacji zdarzenie nie ma jeszcze zgłaszane. To zachowanie obsługi przydaje się do składania kontroli, których możesz chcieć wszystkich testowania trafienia na podstawie zdarzeń wejściowych lub skoncentrować się na podstawie zdarzeń wejściowych przekazywanych przez kontroli nad końcowego, a nie jej części złożonego. Elementu formantu końcowego zbliżonej do katalogu głównego w składania i dlatego ma okazję do klasy obsługi zdarzeń tunelowania najpierw, a być może do "replace" tego zdarzenia trasowanego ze zdarzeniem bardziej specyficznych dla formantu, jako część kodu, który tworzy kopie kontrolki Klasa.  
  
 Ilustracją jak danych wejściowych do przetwarzania zdarzeń, działa należy wziąć pod uwagę następujące przykładowe dane wejściowe zdarzenia. Na poniższej ilustracji drzewa `leaf element #2` jest źródłem zarówno `PreviewMouseDown` i następnie `MouseDown` zdarzeń.  
  
 ![Diagram routingu zdarzeń](./media/wcsdkcoreinputevents.png "wcsdkCoreInputEvents")  
Dane wejściowe zdarzenia Propagacja i tunelowanie  
  
 Kolejność przetwarzania zdarzeń jest następująca:  
  
1. `PreviewMouseDown` (tunelowania) na element główny.  
  
2. `PreviewMouseDown` (tunelowania) w elemencie pośrednich #1.  
  
3. `PreviewMouseDown` (tunelowania) w elemencie źródła #2.  
  
4. `MouseDown` (bąbelkowy) w elemencie źródła #2.  
  
5. `MouseDown` (bąbelkowy) w elemencie pośrednich #1.  
  
6. `MouseDown` (bąbelkowy) na element główny.  
  
 Procedury obsługi delegata zdarzenia trasowanego udostępniający odwołania do dwóch obiektów: obiektu, który podniósł zdarzenie i obiekt, w której został wywołany program obsługi. Obiekt, w której został wywołany program obsługi jest obiektem, który został zgłoszony przez `sender` parametru. Obiekt, w którym zdarzenie został wywołany po raz pierwszy, jest zgłaszany przez <xref:System.Windows.RoutedEventArgs.Source%2A> właściwości danych zdarzenia. Zdarzenia trasowanego nadal można podniesione i obsługiwane przez ten sam obiekt, w którym to przypadku `sender` i <xref:System.Windows.RoutedEventArgs.Source%2A> są identyczne (jest to w przypadku kroki 3 i 4 w zdarzeniu przetwarzania listy przykład).  
  
 Ze względu na tunelowania i propagacja, elementy nadrzędne odbierania zdarzeń wejściowych gdzie <xref:System.Windows.RoutedEventArgs.Source%2A> jest jednym z jego podrzędnych elementów. Gdy jest to ważne, aby dowiedzieć się, co to jest element źródła, można zidentyfikować element źródła, uzyskując dostęp do <xref:System.Windows.RoutedEventArgs.Source%2A> właściwości.  
  
 Zazwyczaj gdy dane wejściowe zdarzenia jest oznaczony <xref:System.Windows.RoutedEventArgs.Handled%2A>, dodatkowo nie są wywoływane programy obsługi. Zazwyczaj zdarzenia wejściowe należy oznaczyć jako obsłużony, tak szybko, jak program obsługi zostanie wywołana, odnoszący się do obsługi usługi specyficzne dla aplikacji logicznej znaczenie dane wejściowe zdarzenia.  
  
 Wyjątek niniejszych ogólne dotyczące <xref:System.Windows.RoutedEventArgs.Handled%2A> stan to, że dane wejściowe procedury obsługi zdarzeń, które są zarejestrowane w celu ignorowania celowo <xref:System.Windows.RoutedEventArgs.Handled%2A> stanu danych zdarzeń nadal będzie można wywołać wzdłuż albo trasy. Aby uzyskać więcej informacji, zobacz [Podgląd zdarzeń](preview-events.md) lub [oznaczanie zdarzeń trasowanych jako Handled oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md).  
  
 Model danych udostępnionych zdarzeń między tunelowania i Propagacja zdarzeń i sekwencyjny wywoływanie pierwszy tunelowania, następnie Propagacja zdarzeń, nie jest pojęcia, które jest zazwyczaj spełniony dla wszystkich zdarzeń trasowanych. Zachowanie w szczególności jest implementowany przez jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] urządzenia wejściowe możliwość pozyskiwania i połączyć pary dane wejściowe zdarzenia. Implementowanie zdarzenia wejściowe to zaawansowany scenariusz, ale można również wykonać modelu dla danych wejściowych zdarzeń.  
  
 Niektóre klasy zdecydować się na dojście-do-klasy niektórych zdarzeń wejściowych, zwykle z zamiarem, definiują na nowo określonego zdarzenia wejściowe oparte na użytkownika oznacza w obrębie tej kontrolki i wywoływanie nowe zdarzenie. Aby uzyskać więcej informacji, zobacz [oznaczanie zdarzeń trasowanych jako Handled oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md).  
  
 Aby uzyskać więcej informacji na temat danych wejściowych i sposób interakcji dane wejściowe i zdarzenia w typowych scenariuszy aplikacji, zobacz [przegląd danych wejściowych](input-overview.md).  
  
<a name="events_styles"></a>   
## <a name="eventsetters-and-eventtriggers"></a>EventSetters i EventTriggers  
 Style, może zawierać niektóre wstępnie zadeklarować [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługi składni języka znaczników przy użyciu zdarzeń <xref:System.Windows.EventSetter>. Stosowania stylu odwołania program obsługi jest dodawany do wystąpienia ze stylem. Można zadeklarować <xref:System.Windows.EventSetter> tylko dla zdarzenia trasowanego. Oto przykład. Należy pamiętać, że `b1SetColor` metoda z odwołaniem w tym miejscu znajduje się w pliku związanym z kodem.  
  
 [!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]  
  
 Zaletą uzyskane w tym miejscu jest styl mogących zawierać wiele innych informacji, które można zastosować do dowolnego przycisku w aplikacji i równoważy <xref:System.Windows.EventSetter> część stylu promuje ponowne wykorzystanie kodu, nawet na poziomie znaczników. Ponadto <xref:System.Windows.EventSetter> przenosi nazwy metod dla programów obsługi krok dalej od ogólnego znaczników aplikacji i strony.  
  
 Inny wyspecjalizowane składnia, która łączy routingiem zdarzeń i animacji funkcje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest <xref:System.Windows.EventTrigger>. Podobnie jak w przypadku <xref:System.Windows.EventSetter>, mogą być używane tylko zdarzenia trasowane do <xref:System.Windows.EventTrigger>. Zazwyczaj <xref:System.Windows.EventTrigger> jest zadeklarowany jako część stylu, ale <xref:System.Windows.EventTrigger> mogą być także zadeklarowane na poziomie strony elementów w ramach <xref:System.Windows.FrameworkElement.Triggers%2A> kolekcji lub w <xref:System.Windows.Controls.ControlTemplate>. <xref:System.Windows.EventTrigger> Pozwala na określenie <xref:System.Windows.Media.Animation.Storyboard> czy działa w każdym przypadku, gdy zdarzenie trasowane osiągnie elementu w jego trasę deklaruje <xref:System.Windows.EventTrigger> dla tego zdarzenia. Zaletą <xref:System.Windows.EventTrigger> na tylko obsługi zdarzenia i powodują, że jej uruchamiania istniejących scenorys jest to, że <xref:System.Windows.EventTrigger> zapewnia lepszą kontrolę nad scenorysu i jego zachowanie w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [użyć wyzwalaczy zdarzeń, aby kontrolować Scenorys po uruchomieniu](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
<a name="more_about"></a>   
## <a name="more-about-routed-events"></a>Więcej informacji na temat zdarzenia trasowane  
 W tym temacie omówiono przede wszystkim zdarzeń trasowanych z punktu widzenia zawierająca opis podstawowych pojęć i podzielimy się wskazówkami na temat i odpowiedzieć na zdarzenia trasowane, które są już obecne w różnych elementów podstawowych i kontrolek. Jednak można utworzyć własne zdarzenia trasowanego na klasę niestandardową oraz niezbędne wsparcie, takie jak klas danych zdarzeń wyspecjalizowanych i delegatów. Właściciel zdarzenia trasowanego może być dowolną klasę, ale zdarzenia trasowane musi być wywołane przez i obsługiwane przez <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> klasy pochodne była użyteczna. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [Utwórz niestandardowe zdarzenie kierowane](how-to-create-a-custom-routed-event.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.EventManager>
- <xref:System.Windows.RoutedEvent>
- <xref:System.Windows.RoutedEventArgs>
- [Oznaczanie zdarzeń trasowanych jako obsłużonych oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md)
- [Przegląd danych wejściowych](input-overview.md)
- [Przegląd poleceń](commanding-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Drzewa w WPF](trees-in-wpf.md)
- [Słabe wzorce zdarzeń](weak-event-patterns.md)
