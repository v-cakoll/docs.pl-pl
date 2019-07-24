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
ms.openlocfilehash: 24fa283ec0c1fef2023845df0a05c3f1ebf5df06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400753"
---
# <a name="routed-events-overview"></a>Przegląd Zdarzenia trasowane

W tym temacie opisano koncepcję zdarzeń kierowanych [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]w programie. Temat definiuje terminologię dotyczącą zdarzeń kierowanych, opis sposobu, w jaki zdarzenia kierowane są kierowane przez drzewo elementów, podsumowują sposób obsługi zdarzeń kierowanych i wprowadzają sposób tworzenia własnych niestandardowych zdarzeń routingu.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Wymagania wstępne

W tym temacie założono, że masz podstawową wiedzę na temat środowiska uruchomieniowego języka wspólnego (CLR) i programowania zorientowanego obiektowo, a także koncepcji, w jaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sposób relacje między elementami mogą być koncepcyjne jako drzewo. Aby postępować zgodnie z przykładami w tym temacie, należy również zrozumieć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wiedzieć, jak pisać bardzo podstawowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje lub strony. Aby uzyskać więcej informacji, [zobacz Przewodnik: Moja pierwsza aplikacja](../getting-started/walkthrough-my-first-wpf-desktop-application.md) klasyczna WPF i [Omówienie języka XAML (WPF)](xaml-overview-wpf.md).

<a name="routing"></a>

## <a name="what-is-a-routed-event"></a>Co to jest zdarzenie trasowane?

Zdarzenia kierowane można traktować z perspektywy funkcjonalnej lub implementacji. Obie definicje są prezentowane w tym miejscu, ponieważ niektóre osoby mogą łatwiej znaleźć jedną lub drugą definicję.

Definicja funkcjonalności: Zdarzenie trasowane to typ zdarzenia, które umożliwia wywoływanie programów obsługi dla wielu odbiorników w drzewie elementów, a nie tylko na obiekt, który spowodował zdarzenie.

Definicja implementacji: Zdarzenie trasowane to zdarzenie CLR, które jest obsługiwane przez wystąpienie <xref:System.Windows.RoutedEvent> klasy i przetwarzane [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przez system zdarzeń.

Typowa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja zawiera wiele elementów. Niezależnie od tego, czy utworzono w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kodzie, czy zadeklarowano w, te elementy istnieją w relacji drzewa elementów ze sobą. Trasa zdarzenia może poruszać się w jednym z dwóch kierunków, w zależności od definicji zdarzenia, ale ogólnie trasa jest przenoszona z elementu źródłowego, a następnie "bąbelki" w górę za pośrednictwem drzewa elementów do momentu osiągnięcia elementu głównego drzewa elementów (zazwyczaj strony lub okna). Ta koncepcja propagacji może być znana użytkownikowi, jeśli wcześniej pracujesz z modelem obiektów DHTML.

Rozważmy następujące proste drzewo elementów:

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

To drzewo elementów generuje coś podobne do następujących:

![Przyciski tak, nie i Anuluj](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")

W tym uproszczonym drzewie elementów źródło <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia jest jednym <xref:System.Windows.Controls.Button> z elementów, a w zależności od tego <xref:System.Windows.Controls.Button> , który został kliknięty jest pierwszym elementem, który ma możliwość obsługi zdarzenia. Ale jeśli nie dołączono obsługi do <xref:System.Windows.Controls.Button> działań na zdarzeniu, zdarzenie spowoduje przechodzenie w górę <xref:System.Windows.Controls.Button> do elementu nadrzędnego w <xref:System.Windows.Controls.StackPanel>drzewie elementów, który jest. Potencjalnie może to być bąbelki <xref:System.Windows.Controls.Border>zdarzeń do, a następnie poza katalogiem głównym strony drzewa elementów (niepokazywany).

Innymi słowy, trasa zdarzenia dla tego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia to:

Button--> StackPanel--> Border-->...

### <a name="top-level-scenarios-for-routed-events"></a>Scenariusze najwyższego poziomu dla zdarzeń kierowanych

Poniżej przedstawiono krótkie podsumowanie scenariuszy, które podlegają koncepcji kierowanego zdarzenia i dlaczego typowe zdarzenie CLR nie było wystarczające dla następujących scenariuszy:

**Układ i hermetyzacja formantu:** Różne kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w programie mają bogaty model zawartości. Na przykład można umieścić obraz wewnątrz <xref:System.Windows.Controls.Button>obiektu, który skutecznie rozszerza drzewo wizualne przycisku. Jednak dodany obraz nie może przerwać działania testowania trafień, które powoduje, że przycisk reaguje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> na jego zawartość, nawet jeśli użytkownik kliknie piksele, które są technicznie częścią obrazu.

**Punkty załącznika procedury obsługi pojedynczej:** W [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]programie konieczne jest dołączenie tego samego programu obsługi wiele razy, aby przetwarzać zdarzenia, które mogą być wywoływane z wielu elementów. Zdarzenia kierowane umożliwiają dołączenie tego programu obsługi tylko raz, jak pokazano w poprzednim przykładzie, i użycie logiki obsługi do określenia, w razie potrzeby zdarzenia, z którego pochodzi. Na przykład może to być procedura obsługi poprzednio pokazanego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:

[!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
[!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]

**Obsługa klasy:** Zdarzenia kierowane umożliwiają obsługę statyczną, która jest definiowana przez klasę. Ta procedura obsługi klas umożliwia obsługę zdarzenia przed dowolnymi dołączonymi procedurami obsługi wystąpień.

**Odwoływanie się do zdarzenia bez odbicia:** Niektóre techniki kodu i znaczników wymagają sposobu identyfikacji konkretnego zdarzenia. Zdarzenie trasowane tworzy <xref:System.Windows.RoutedEvent> pole jako identyfikator, który zapewnia niezawodną technikę identyfikacji zdarzeń, która nie wymaga odbicia statycznego ani w czasie wykonywania.

### <a name="how-routed-events-are-implemented"></a>Jak są implementowane zdarzenia kierowane

Zdarzenie trasowane to zdarzenie CLR, które jest obsługiwane przez wystąpienie <xref:System.Windows.RoutedEvent> klasy i zarejestrowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w systemie zdarzeń. Wystąpienie uzyskane z rejestracji jest zwykle `static` zachowywane `readonly` `public` jako element członkowski pola klasy, która rejestruje i w tym samym "właścicielem" zdarzenia kierowanego. <xref:System.Windows.RoutedEvent> Połączenie z identycznie nazwanym zdarzeniem środowiska CLR (które jest czasami określane jako zdarzenie otoki) jest realizowane przez zastąpienie `add` implementacji i `remove` dla zdarzenia CLR. `add` Zwykle i `remove` są pozostawiane jako niejawne domyślne, które wykorzystują odpowiednią składnię zdarzenia specyficzną dla języka do dodawania i usuwania programów obsługi tego zdarzenia. Mechanizm tworzenia kopii zapasowych i łączenia zdarzeń jest koncepcyjnie podobny do tego, w jaki sposób właściwość zależności jest właściwością CLR, <xref:System.Windows.DependencyProperty> która jest obsługiwana przez klasę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i zarejestrowana w systemie właściwości.

W poniższym przykładzie `Tap` pokazano deklarację dla niestandardowego zdarzenia trasowanego, w tym rejestracji i ekspozycji <xref:System.Windows.RoutedEvent> pola identyfikatora oraz `add` implementacji i `remove` dla `Tap` zdarzenia CLR.

[!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
[!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]

### <a name="routed-event-handlers-and-xaml"></a>Procedury obsługi zdarzeń kierowanych i XAML

Aby dodać procedurę obsługi dla zdarzenia przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy zadeklarować nazwę zdarzenia jako atrybut w elemencie, który jest odbiornikiem zdarzeń. Wartość atrybutu jest nazwą zaimplementowanej metody obsługi, która musi istnieć w klasie częściowej pliku związanego z kodem.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Składnia służąca do dodawania standardowych programów obsługi zdarzeń CLR jest taka sama w przypadku dodawania obsługi zdarzeń kierowanych, ponieważ w rzeczywistości dodajesz programy obsługi do otoki zdarzeń CLR, która ma zaimplementowaną implementację zdarzenia. Aby uzyskać więcej informacji na temat dodawania obsługi zdarzeń [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]w programie, zobacz [XAML — Omówienie (WPF)](xaml-overview-wpf.md).

<a name="routing_strategies"></a>

## <a name="routing-strategies"></a>Strategie routingu

Zdarzenia kierowane korzystają z jednej z trzech strategii routingu:

- **Propagacja** Procedury obsługi zdarzeń w źródle zdarzeń są wywoływane. Rozesłane zdarzenie następnie kieruje do kolejnych elementów nadrzędnych do momentu osiągnięcia katalogu głównego drzewa elementów. Większość przesłanych zdarzeń korzysta z strategii routingu propagacji. Propagacja zdarzeń kierowanych jest zwykle używana do raportowania zmian wprowadzonych lub stanu z różnych kontrolek lub innych elementów interfejsu użytkownika.

- **Bezpośrednie** Tylko element źródłowy ma możliwość wywołania programów obsługi w odpowiedzi. Jest to analogiczne do "routingu" używanego [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dla zdarzeń. Jednak, w przeciwieństwie do standardowego zdarzenia CLR, obsługiwane są zdarzenia kierowane do obsługi klas (obsługa klasy została omówiona w nadchodzącej sekcji) i może <xref:System.Windows.EventSetter> być <xref:System.Windows.EventTrigger>używane przez i.

- **Tunelowania** Początkowo procedury obsługi zdarzeń w katalogu głównym drzewa elementów są wywoływane. Rozesłane zdarzenie następnie kieruje trasę przez kolejne elementy podrzędne wzdłuż trasy do elementu węzła, który jest kierowanym źródłem zdarzeń (element, który zgłosił zdarzenie kierowane). Tunelowanie zdarzeń kierowanych jest często używane lub obsługiwane jako część składu kontrolki, tak że zdarzenia z części złożonych można celowo pominąć lub zastąpić zdarzeniami, które są specyficzne dla całej kontroli. Zdarzenia wejściowe podane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] często są implementowane jako para tunelowania/propagacji. Zdarzenia tunelowania są również czasami określane jako zdarzenia w wersji zapoznawczej ze względu na konwencję nazewnictwa, która jest używana dla par.

<a name="why_use"></a>

## <a name="why-use-routed-events"></a>Dlaczego warto używać zdarzeń kierowanych?

Jako deweloper aplikacji nie zawsze musisz znać lub zadbać o to, aby obsługiwane zdarzenie zostało zaimplementowane jako zdarzenie trasowane. Zdarzenia kierowane mają specjalne zachowanie, ale takie zachowanie jest w dużym stopniu niewidoczne, jeśli są obsługiwane zdarzenia dotyczące elementu, w którym jest wywoływany.

W przypadku, gdy zdarzenia kierowane stają się rozbudowane, można użyć dowolnego z sugerowanych scenariuszy: definiowania wspólnych programów obsługi w wspólnym katalogu głównym, tworzenia własnej kontrolki lub definiowania własnej niestandardowej klasy kontrolek.

Rozesłane detektory zdarzeń i źródła zdarzeń kierowane nie muszą udostępniać typowego zdarzenia w swojej hierarchii. Każdy <xref:System.Windows.UIElement> lub<xref:System.Windows.ContentElement> może być odbiornikiem zdarzeń dla dowolnego zdarzenia kierowanego. Z tego względu można użyć pełnego zestawu zdarzeń kierowanych dostępnych w ramach działającego zestawu interfejsów API jako koncepcyjnego "interfejsu", za pomocą którego różne elementy w aplikacji mogą wymieniać informacje o zdarzeniach. Pojęcie "Interface" dla zdarzeń kierowanych jest szczególnie stosowane w przypadku zdarzeń wejściowych.

Zdarzenia trasowane mogą być również używane do komunikowania się w drzewie elementów, ponieważ dane zdarzenia dla zdarzenia są perpetuated do każdego elementu w marszrucie. Jeden element może zmienić coś w danych zdarzenia, a ta zmiana byłaby dostępna dla następnego elementu w marszrucie.

Poza aspektem routingu istnieją dwie inne przyczyny, w których każde określone [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenie może zostać zaimplementowane jako zdarzenie trasowane zamiast standardowego zdarzenia CLR. W przypadku wdrażania własnych zdarzeń można także wziąć pod uwagę następujące zasady:

- Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje stylów i tworzenia szablonów, takie <xref:System.Windows.EventSetter> jak <xref:System.Windows.EventTrigger> i wymagają zdarzenia przywoływanego, są zdarzeniem kierowanym. Jest to opisany wcześniej scenariusz identyfikatora zdarzenia.

- Zdarzenia kierowane obsługują mechanizm obsługi klasy, dzięki czemu Klasa może określać metody statyczne, które mają możliwość obsługi zdarzeń kierowanych, zanim wszystkie zarejestrowane programy obsługi wystąpień będą mogły uzyskać do nich dostęp. Jest to bardzo przydatne w projekcie kontroli, ponieważ Klasa może wymuszać zachowania klas sterowane zdarzeniami, których nie można przypadkowo pominąć przez obsługę zdarzenia w wystąpieniu.

Każdy z powyższych zagadnień został omówiony w oddzielnej sekcji tego tematu.

<a name="event_handing"></a>

## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Dodawanie i implementowanie obsługi zdarzeń dla zdarzenia kierowanego

Aby dodać procedurę obsługi zdarzeń w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programie, wystarczy dodać nazwę zdarzenia do elementu jako atrybut i ustawić wartość atrybutu jako nazwę programu obsługi zdarzeń implementującego odpowiedni delegat, jak w poniższym przykładzie.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

`b1SetColor`jest nazwą zaimplementowanej procedury obsługi, która zawiera kod, który obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie. `b1SetColor`musi mieć taką samą sygnaturę jak <xref:System.Windows.RoutedEventHandler> delegat, który jest delegatem obsługi zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dla zdarzenia. Pierwszy parametr wszystkich rozesłanych delegatów obsługi zdarzeń określa element, do którego zostanie dodana procedura obsługi zdarzeń, a drugi parametr określa dane dla zdarzenia.

[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]

<xref:System.Windows.RoutedEventHandler>jest obiektem delegowanym obsługi zdarzeń z obsługą podstawową. W przypadku zdarzeń kierowanych, które są wyspecjalizowane dla pewnych kontrolek lub scenariuszy, Delegaty do użycia w przypadku obsługi zdarzeń kierowanych mogą być bardziej wyspecjalizowane, aby mogły przesyłać wyspecjalizowane dane zdarzeń. Na przykład w typowym scenariuszu danych wejściowych może dojść do <xref:System.Windows.UIElement.DragEnter> obsłużenia zdarzenia kierowanego. Program obsługi powinien zaimplementować <xref:System.Windows.DragEventHandler> delegata. Korzystając z najbardziej określonego delegata, można przetwarzać <xref:System.Windows.DragEventArgs> w programie obsługi i <xref:System.Windows.DragEventArgs.Data%2A> odczytywać właściwość, która zawiera ładunek schowka operacji przeciągania.

Aby zapoznać się z kompletnym przykładem dodawania obsługi zdarzeń do elementu przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz temat [Obsługa zdarzenia kierowanego](how-to-handle-a-routed-event.md).

Dodawanie programu obsługi dla zdarzenia kierowanego w aplikacji, która jest tworzona w kodzie, jest proste. Procedury obsługi zdarzeń kierowanych mogą być zawsze dodawane za pomocą metody <xref:System.Windows.UIElement.AddHandler%2A> pomocnika (która jest taka sama jak metoda, dla `add`której jest używane istniejące wywołania zapasowe). Jednak istniejące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia kierowane zwykle mają `add` implementacje i `remove` logikę, które umożliwiają obsługę zdarzeń kierowanych, które mogą być dodawane przez składnię zdarzenia specyficzną dla języka, która jest bardziej intuicyjna składnia niż metoda pomocnika. Poniżej przedstawiono przykładowe użycie metody pomocnika:

[!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
[!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]

W następnym przykładzie pokazano składnię C# operatora (Visual Basic ma nieco inną składnię operatora ze względu na sposób obsługi dereferencji):

[!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
[!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]

Aby zapoznać się z przykładem dodawania obsługi zdarzeń w kodzie, zobacz [Dodawanie programu obsługi zdarzeń przy użyciu kodu](how-to-add-an-event-handler-using-code.md).

Jeśli używasz Visual Basic, możesz również użyć `Handles` słowa kluczowego, aby dodać procedury obsługi jako część deklaracji obsługi. Aby uzyskać więcej informacji, zobacz [Visual Basic i obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).

<a name="concept_handled"></a>

### <a name="the-concept-of-handled"></a>Koncepcja obsłużonych

Wszystkie zdarzenia trasowane mają wspólną klasę <xref:System.Windows.RoutedEventArgs>bazową danych zdarzenia. <xref:System.Windows.RoutedEventArgs><xref:System.Windows.RoutedEventArgs.Handled%2A> definiuje właściwość, która przyjmuje wartość logiczną. Celem <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwości jest włączenie dowolnego programu obsługi zdarzeń wzdłuż trasy, aby oznaczyć zdarzenia kierowane jako *Obsłużone*, <xref:System.Windows.RoutedEventArgs.Handled%2A> ustawiając wartość na. `true` Po przetworzeniu przez program obsługi w jednym elemencie wzdłuż trasy dane zdarzenia udostępnione są ponownie raportowane dla każdego odbiornika wzdłuż trasy.

Wartość <xref:System.Windows.RoutedEventArgs.Handled%2A> wpływa na to, w jaki sposób zdarzenie kierowane jest raportowane lub przetwarzane w miarę dalszej podróży na trasie. Jeśli <xref:System.Windows.RoutedEventArgs.Handled%2A> znajduje `true` się w danych zdarzenia dla zdarzenia kierowanego, programy obsługi, które nasłuchują zdarzenia kierowanego na inne elementy, nie są już wywoływane dla danego wystąpienia zdarzenia. Jest to prawdziwe zarówno w przypadku programów obsługi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , jak i dla programów obsługi dodanych przez składnię załączników specyficznych dla języka, takich jak `+=` lub `Handles`. W przypadku większości typowych scenariuszy obsługi Oznaczanie zdarzenia jako obsługiwanego przez <xref:System.Windows.RoutedEventArgs.Handled%2A> ustawienie `true` spowoduje "Zatrzymaj" Routing dla trasy tunelowania lub trasy propagacji, a także dla każdego zdarzenia, które jest obsługiwane w punkcie w trasie przez procedurę obsługi klasy.

Istnieje jednak mechanizm "handledEventsToo", w którym detektory mogą nadal uruchamiać programy obsługi w odpowiedzi na zdarzenia kierowane, <xref:System.Windows.RoutedEventArgs.Handled%2A> gdzie `true` znajduje się w danych zdarzenia. Innymi słowy, trasa zdarzenia nie jest naprawdę zatrzymana przez oznaczenie danych zdarzenia jako obsłużonych. Mechanizm handledEventsToo można używać tylko w kodzie lub w <xref:System.Windows.EventSetter>:

- W kodzie, zamiast używać składni zdarzeń specyficznych dla języka, która działa dla ogólnych zdarzeń CLR, wywołaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metodę <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> , aby dodać program obsługi. Określ wartość `handledEventsToo` jako `true`.

- W, należy <xref:System.Windows.EventSetter.HandledEventsToo%2A> ustawić atrybut na `true`. <xref:System.Windows.EventSetter>

Oprócz zachowania wytwarzanego przez ten <xref:System.Windows.RoutedEventArgs.Handled%2A> stan w zdarzeniach kierowanych <xref:System.Windows.RoutedEventArgs.Handled%2A> pojęcie ma wpływ na sposób projektowania aplikacji i zapisywanie kodu programu obsługi zdarzeń. Możesz konceptualizacji <xref:System.Windows.RoutedEventArgs.Handled%2A> jako prosty protokół, który jest udostępniany przez zdarzenia kierowane. Dokładnie, jak korzystać z tego protokołu, ale projekt koncepcyjny, dla którego ma być używana wartość <xref:System.Windows.RoutedEventArgs.Handled%2A> , jest następujący:

- Jeśli zdarzenie trasowane jest oznaczone jako obsługiwane, nie trzeba go obsługiwać ponownie przy użyciu innych elementów i trasy.

- Jeśli zdarzenie trasowane nie jest oznaczone jako obsługiwane, inne detektory, które wcześniej znajdowały się na trasie, nie zarejestrowali procedury obsługi lub zarejestrowano programy obsługi, które wybrały niemanipulowanie danymi zdarzenia i <xref:System.Windows.RoutedEventArgs.Handled%2A> ustawioną na `true`. (Lub jest oczywiście możliwe, że bieżący odbiornik jest punktem początkowym trasy). Programy obsługi dla bieżącego odbiornika mają teraz trzy możliwe kursy:

  - Nie podejmuj żadnych działań w ogóle; zdarzenie pozostaje nieobsłużone i trasy zdarzeń do następnego odbiornika.

  - Wykonaj kod w odpowiedzi na zdarzenie, ale Określ, że podjęta akcja nie była wystarczająco istotna, aby zagwarantować oznaczenie zdarzenia jako obsłużonego. Trasy zdarzeń do następnego odbiornika.

  - Wykonaj kod w odpowiedzi na zdarzenie. Oznacz zdarzenie jako obsłużone w danych zdarzenia przekazaniu do procedury obsługi, ponieważ podjęta akcja została uznana za wystarczającą do oznaczania jako przewidzianą. Zdarzenie nadal <xref:System.Windows.RoutedEventArgs.Handled%2A> kieruje do następnego odbiornika, ale z = `true` danymi zdarzeń, dlatego tylko `handledEventsToo` detektory mają możliwość wywołania dalszych programów obsługi.

Ten projekt koncepcyjny został wzmocniony przez zachowanie routingu wymienione wcześniej: jest trudniejsze (chociaż nadal możliwe w kodzie lub w stylu) do dołączania obsługi zdarzeń kierowanych, które są wywoływane nawet wtedy, gdy wcześniej została ustawiona <xref:System.Windows.RoutedEventArgs.Handled%2A>Poprzedniaproceduraobsługitrasydo `true`programu.

Aby uzyskać więcej informacji <xref:System.Windows.RoutedEventArgs.Handled%2A>na temat obsługi zdarzeń kierowanych i zaleceń dotyczących tego, kiedy jest to odpowiednie do oznaczenia zdarzenia kierowanego jako <xref:System.Windows.RoutedEventArgs.Handled%2A>, zobacz [oznaczanie zdarzeń kierowanych jako obsłużone i obsługa klas](marking-routed-events-as-handled-and-class-handling.md).

W aplikacjach bardzo często wystarczy obsłużyć zdarzenie propagacji kierowane na obiekt, który go wywołał, i nie powinno być objęte charakterystyką routingu zdarzenia. Jednak nadal dobrym sposobem jest oznaczenie zdarzenia kierowanego jako obsługiwanego w danych zdarzenia, aby zapobiec nieoczekiwanym efektom ubocznym tylko w przypadku, gdy element, który jest w dalszym ciągu drzew elementu, również ma dołączony program obsługi dla tego samego zdarzenia kierowanego.

<a name="class_handlers"></a>

## <a name="class-handlers"></a>Procedury obsługi klas

W przypadku definiowania klasy, która dziedziczy w jakiś sposób z <xref:System.Windows.DependencyObject>, można również zdefiniować i dołączyć procedurę obsługi klasy dla zdarzenia trasowanego, które jest zadeklarowanym lub dziedziczonym członkiem zdarzenia klasy. Procedury obsługi klas są wywoływane przed dowolnymi uchwytami detektora wystąpienia, które są dołączone do wystąpienia tej klasy, za każdym razem, gdy zdarzenie trasowane osiągnie wystąpienie elementu w swojej trasie.

Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki mają nieodłączną obsługę klas dla pewnych zdarzeń kierowanych. Może to dać na zewnątrz wrażenie, że zdarzenie kierowane nie zostało kiedykolwiek zgłoszone, ale w rzeczywistości jest obsługiwane klasy, a zdarzenie kierowane może być nadal obsługiwane przez programy obsługi wystąpień, jeśli używasz niektórych technik. Ponadto wiele klas podstawowych i kontrolek uwidaczniają metody wirtualne, których można użyć do przesłonięcia zachowania obsługi klasy. Aby uzyskać więcej informacji na temat sposobu obejścia nieżądanej obsługi klas i zdefiniowania obsługi własnej klasy w klasie niestandardowej, zobacz [oznaczanie zdarzeń kierowanych jako obsłużone i obsługa klas](marking-routed-events-as-handled-and-class-handling.md).

<a name="attached_events"></a>

## <a name="attached-events-in-wpf"></a>Zdarzenia dołączone w WPF

Język definiuje również specjalny typ zdarzenia o nazwie *dołączone zdarzenie.* [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dołączone zdarzenie umożliwia dodanie procedury obsługi dla danego zdarzenia do dowolnego elementu. Element obsługujący zdarzenie nie wymaga zdefiniowania lub dziedziczenia dołączonego zdarzenia, a obiekt, który nie może podnieść zdarzenia, ani docelowego wystąpienia obsługi musi definiować lub w inny sposób "własne" jako element członkowski klasy.

System [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wejściowy używa załączonych zdarzeń w szerokim stopniu. Jednak niemal wszystkie te dołączone zdarzenia są przekazywane przez elementy podstawowe. Zdarzenia wejściowe są wyświetlane jako równoważne niedołączone zdarzenia kierowane, które są elementami członkowskimi klasy elementu podstawowego. Na przykład <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> , bazowe dołączone zdarzenie może być łatwiej obsługiwane na <xref:System.Windows.UIElement> dowolnym z nich przy użyciu <xref:System.Windows.UIElement.MouseDown> , <xref:System.Windows.UIElement> a nie na podstawie dołączonej składni zdarzenia w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kodzie.

Aby uzyskać więcej informacji o załączonych zdarzeniach w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz Omówienie załączonych [zdarzeń](attached-events-overview.md).

<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>

## <a name="qualified-event-names-in-xaml"></a>Kwalifikowane nazwy zdarzeń w języku XAML

Inne użycie składni podobne do elementu *TypeName*. *EventName* — połączona składnia zdarzenia, ale nie jest ściśle mówiąca o załączonym wykorzystaniu zdarzenia, jeśli dołączysz obsługę zdarzeń kierowanych, które są wywoływane przez elementy podrzędne. Aby skorzystać z routingu zdarzeń, należy dołączyć programy obsługi do wspólnego elementu nadrzędnego, nawet jeśli wspólny element nadrzędny może nie mieć odpowiedniego zdarzenia kierowanego jako element członkowski. Ponownie Rozważ następujący przykład:

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

W tym miejscu znajduje się odbiornik elementu nadrzędnego, w którym dodano <xref:System.Windows.Controls.StackPanel>procedurę obsługi. Jednak dodaje procedurę obsługi dla zdarzenia trasowanego, które zostało zadeklarowane i zostanie wywołane przez <xref:System.Windows.Controls.Button> klasę (<xref:System.Windows.Controls.Primitives.ButtonBase> w rzeczywistości, ale dostępna do <xref:System.Windows.Controls.Button> dziedziczenia). <xref:System.Windows.Controls.Button>"jest to zdarzenie, ale system zdarzeń kierowanych umożliwia obsługę dowolnego zdarzenia kierowanego do dołączenia do dowolnego <xref:System.Windows.UIElement> odbiornika lub <xref:System.Windows.ContentElement> detektora, który może w inny sposób dołączyć detektory dla zdarzenia środowiska uruchomieniowego języka wspólnego (CLR). Domyślną przestrzenią nazw xmlns dla tych kwalifikowanych nazw atrybutów zdarzeń jest zazwyczaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] domyślna przestrzeń nazw xmlns, ale można także określić prefiksy przestrzenie nazw dla niestandardowych zdarzeń kierowanych. Aby uzyskać więcej informacji na temat xmlns, zobacz [przestrzenie nazw XAML i mapowanie przestrzeni nazw dla języka XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

<a name="how_event_processing_works"></a>

## <a name="wpf-input-events"></a>Zdarzenia wejściowe WPF

Jednym z częstych zastosowań zdarzeń kierowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w ramach platformy jest dla zdarzeń wejściowych. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]systemie nazwy tunelowanych zdarzeń są poprzedzone prefiksem "wersja zapoznawcza" według Konwencji. Zdarzenia wejściowe często pojawiają się w parach, a jedno jest zdarzeniem propagacji i drugim zdarzeniem tunelowania. Na przykład <xref:System.Windows.ContentElement.KeyDown> zdarzenie <xref:System.Windows.ContentElement.PreviewKeyDown> i zdarzenie mają taki sam podpis, z dawnym zdarzeniem wsadowym propagacji, a drugie to zdarzenie wejściowe tunelowania. Czasami zdarzenia wejściowe mają tylko wersję propagacji lub być może tylko bezpośrednio kierowanej wersji. W dokumentacji zdarzenia kierowane zawierają odsyłacze podobne do zdarzeń kierowanych, które mają Alternatywne strategie routingu, jeśli istnieją takie zdarzenia, a sekcje na zarządzanych stronach referencyjnych wyjaśniają strategię routingu każdego zdarzenia kierowanego.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zdarzenia wejściowe, które znajdują się w parach, są implementowane, dzięki czemu pojedyncze działanie użytkownika z danych wejściowych, takich jak naciśnięcie przycisku myszy, spowoduje wygenerowanie obydwu zdarzeń kierowanych przez parę w sekwencji. Po pierwsze zdarzenie tunelowania jest zgłaszane i podróżuje swoją trasę. Następnie zdarzenia propagacji są wywoływane i podróżują swoją trasę. Dwa zdarzenia dosłownie współużytkują to samo wystąpienie danych zdarzenia, ponieważ <xref:System.Windows.UIElement.RaiseEvent%2A> wywołanie metody w klasie implementującej, która wywołuje zdarzenie propagacji, nasłuchuje danych zdarzenia ze zdarzenia tunelowania i ponownie używa go w nowym zdarzeniu podniesione. Odbiorniki z obsługą zdarzenia tunelowania mają pierwszą okazję do oznaczenia rozesłanego zdarzenia obsłużonego (najpierw obsługi klas, a następnie obsługi wystąpień). Jeśli element wzdłuż trasy tunelowania oznaczył zdarzenie kierowane jako obsłużone, dane zdarzenia, które są już obsługiwane, są wysyłane dla zdarzenia propagacji, a typowe programy obsługi dołączone do równoważnych propagacji zdarzeń wejściowych nie będą wywoływane. Na zewnątrz wygląd będzie wyglądać tak, jakby obsłużone zdarzenie propagacji nie zostało jeszcze zgłoszone. Takie zachowanie obsługi jest przydatne w przypadku składania formantów, w którym można chcieć, aby wszystkie zdarzenia wejściowe na podstawie testów trafień lub zdarzenia wejściowe oparte na koncentracji były zgłaszane przez ostateczną kontrolkę, a nie jej części złożone. Końcowy element kontrolny jest bliższy katalogowi głównemu w składowej i dlatego ma możliwość, aby najpierw obsługiwać zdarzenie tunelowania, a nawet "zastępować", które skierowało zdarzenie z dokładniejszym zdarzeniem kontroli, jako część kodu, który wykonuje kopię zapasową formantu określonej.

Jako ilustracja przedstawiająca sposób działania przetwarzania zdarzeń wejściowych należy wziąć pod uwagę Poniższy przykład zdarzenia wejściowego. Na poniższej ilustracji `leaf element #2` przedstawiono źródło `PreviewMouseDown` obu a i then `MouseDown` zdarzenia:

![Diagram routingu zdarzeń](./media/routed-events-overview/input-event-routing.png)

Kolejność przetwarzania zdarzeń jest następująca:

1. `PreviewMouseDown`(tunel) w elemencie głównym.

2. `PreviewMouseDown`(tunel) dla pośredniego elementu #1.

3. `PreviewMouseDown`(tunel) w elemencie źródłowym #2.

4. `MouseDown`(bąbelkowy) dla elementu źródłowego #2.

5. `MouseDown`(bąbelkowy) dla pośredniego elementu #1.

6. `MouseDown`(bąbelkowy) na elemencie głównym.

Delegat procedury obsługi zdarzeń kierowanych zawiera odwołania do dwóch obiektów: obiektu, który spowodował zdarzenie i obiekt, w którym została wywołana procedura obsługi. Obiekt, do którego została wywołana procedura obsługi, jest obiektem zgłoszonym przez `sender` parametr. Obiekt, w którym zdarzenie zostało po raz pierwszy zgłoszone przez <xref:System.Windows.RoutedEventArgs.Source%2A> właściwość w danych zdarzenia. Zdarzenie trasowane może nadal być wywoływane i obsługiwane przez ten sam obiekt, w którym to przypadku `sender` i <xref:System.Windows.RoutedEventArgs.Source%2A> są identyczne (w tym przypadku kroki 3 i 4 znajdują się na liście przykładowych przetwarzania zdarzeń).

Z powodu tunelowania i propagacji elementy nadrzędne odbierają zdarzenia wejściowe, <xref:System.Windows.RoutedEventArgs.Source%2A> gdzie jest jednym z ich elementów podrzędnych. Gdy ważne jest, aby wiedzieć, co to jest element źródłowy, można zidentyfikować element źródłowy, uzyskując dostęp <xref:System.Windows.RoutedEventArgs.Source%2A> do właściwości.

Zwykle po oznaczeniu <xref:System.Windows.RoutedEventArgs.Handled%2A>zdarzenia wejściowego nie są wywoływane dalsze procedury obsługi. Zazwyczaj należy oznaczyć zdarzenia wejściowe jako obsługiwane, gdy tylko zostanie wywołana procedura obsługi, która odnosi się do obsługi logicznej specyficznej dla aplikacji o znaczeniu zdarzenia wejściowego.

Wyjątkiem od tej ogólnej instrukcji dotyczącej <xref:System.Windows.RoutedEventArgs.Handled%2A> stanu jest to, że programy obsługi zdarzeń wejściowych, które są zarejestrowane w <xref:System.Windows.RoutedEventArgs.Handled%2A> celu zamierzonego ignorowania stanu danych zdarzenia, nadal będą wywoływane wraz z trasą. Aby uzyskać więcej informacji, zobacz temat [Podgląd zdarzeń](preview-events.md) lub [oznaczanie zdarzeń kierowanych jako obsłużone i obsługa klas](marking-routed-events-as-handled-and-class-handling.md).

Współużytkowany model danych zdarzeń między tunelowaniem i propagacją zdarzeń oraz sekwencyjne wywoływanie operacji pierwszego tunelowania, a następnie Propagacja zdarzeń, nie jest koncepcją, która jest ogólnie prawdziwa dla wszystkich zdarzeń kierowanych. Takie zachowanie jest implementowane w sposób [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , w jaki urządzenia wejściowe decydują się na podnoszenie i połączenie par zdarzeń wejściowych. Implementowanie własnych zdarzeń wejściowych jest zaawansowanym scenariuszem, ale można również wybrać ten model dla własnych zdarzeń wejściowych.

Niektóre klasy decydują o obsłudze klas przez niektóre zdarzenia wejściowe, zwykle z zamiarem ponownego zdefiniowania określonego przez użytkownika zdarzenia wejściowego w ramach tej kontrolki i podniesienia nowego zdarzenia. Aby uzyskać więcej informacji, zobacz [oznaczanie zdarzeń kierowanych jako obsłużone i obsługa klas](marking-routed-events-as-handled-and-class-handling.md).

Aby uzyskać więcej informacji na temat danych wejściowych i sposobu współdziałania danych wejściowych i zdarzeń w typowych scenariuszach aplikacji, zobacz [Omówienie danych wejściowych](input-overview.md).

<a name="events_styles"></a>

## <a name="eventsetters-and-eventtriggers"></a>EventSetters i eventtriggers

W obszarze Style można uwzględnić niepewną zadeklarowaną [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składnię obsługi zdarzeń w znaczniku przy <xref:System.Windows.EventSetter>użyciu. Po zastosowaniu stylu do wystąpienia z stylem zostanie dodany przywoływany program obsługi. Można zadeklarować <xref:System.Windows.EventSetter> tylko dla zdarzenia kierowanego. Oto przykład. Należy zauważyć, `b1SetColor` że metoda, do której się odwołuje się, znajduje się w pliku związanym z kodem.

[!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]

Zaletą tej metody jest to, że styl może zawierać bardzo duże rozliczenie innych informacji, które mogą <xref:System.Windows.EventSetter> być stosowane do dowolnego przycisku w aplikacji, a ich częścią tego stylu jest promowanie ponownego użycia kodu nawet na poziomie znaczników. Ponadto bardziej <xref:System.Windows.EventSetter> abstrakcyjne nazwy metod dla programów obsługi jeden krok poza ogólną aplikacją i znacznikiem strony.

Kolejną wyspecjalizowaną składnią, która łączy kierowane zdarzenia i funkcje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji programu <xref:System.Windows.EventTrigger>, jest. Podobnie jak <xref:System.Windows.EventSetter>w przypadku, tylko zdarzenia trasowane mogą być używane <xref:System.Windows.EventTrigger>dla. Zwykle jest zadeklarowany jako część stylu, <xref:System.Windows.EventTrigger> ale można go również zadeklarować w <xref:System.Windows.FrameworkElement.Triggers%2A> elementach na poziomie strony jako część kolekcji lub w <xref:System.Windows.Controls.ControlTemplate>. <xref:System.Windows.EventTrigger> Umożliwia określenie, które jest uruchamiane za każdym razem, gdy zdarzenie kierowane osiągnie element w <xref:System.Windows.EventTrigger> swojej trasie, który deklaruje dla tego zdarzenia. <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.EventTrigger> Zaletą <xref:System.Windows.EventTrigger> po prostu obsłudze zdarzenia i spowodowanym rozpoczęciem istniejącego scenorysu jest to <xref:System.Windows.EventTrigger> , że zapewnia lepszą kontrolę nad scenorysem i jego zachowaniem w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Używanie wyzwalaczy zdarzeń do kontrolowania scenorysu po jego uruchomieniu](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

<a name="more_about"></a>

## <a name="more-about-routed-events"></a>Więcej informacji na temat zdarzeń kierowanych

W tym temacie opisano głównie zdarzenia kierowane z perspektywy opisującej podstawowe koncepcje i oferujące wskazówki dotyczące sposobu reagowania na zdarzenia kierowane, które znajdują się już w różnych elementach podstawowych i formantach. Można jednak utworzyć własne wydarzenie kierowane w klasie niestandardowej wraz ze wszystkimi niezbędnymi, takimi jak klasy danych zdarzeń i delegatów. Właścicielem zdarzenia kierowanego może być dowolna klasa, ale zdarzenia kierowane muszą być zgłaszane przez i obsługiwane <xref:System.Windows.UIElement> przez <xref:System.Windows.ContentElement> lub klasy pochodne, aby były użyteczne. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [Tworzenie niestandardowego zdarzenia kierowanego](how-to-create-a-custom-routed-event.md).

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
