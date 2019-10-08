---
title: Przegląd Dane wejściowe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [WPF]
- input [WPF], overview
- keyboard focus [WPF]
- keyboard input [WPF]
- touch events [WPF]
- event routing [WPF]
- touch input [WPF]
- manipulation [WPF]
- logical focus [WPF]
- stylus input [WPF]
- text input [WPF]
- input events [WPF], handling
- WPF [WPF], input overview
- manipulation events [WPF]
- mouse input [WPF]
- mouse capture [WPF]
- focus [WPF]
- mouse position [WPF]
ms.assetid: ee5258b7-6567-415a-9b1c-c0cbe46e79ef
ms.openlocfilehash: a90c74542c1a6604ed27d37f882385b67402dd92
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005027"
---
# <a name="input-overview"></a>Przegląd Dane wejściowe
<a name="introduction"></a>Podsystem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia zaawansowany interfejs API umożliwiający uzyskiwanie danych z różnych urządzeń, w tym myszy, klawiatury, dotyku i pióra. W tym temacie opisano usługi udostępniane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i wyjaśniono architekturę systemów wejściowych.

<a name="input_api"></a>
## <a name="input-api"></a>Wejściowy interfejs API
 Podstawowe dane wejściowe interfejsu API wejścia znajdują się w klasach elementu podstawowego: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement> i <xref:System.Windows.FrameworkContentElement>.  Aby uzyskać więcej informacji na temat elementów podstawowych, zobacz [Omówienie elementów podstawowych](base-elements-overview.md).  Klasy te zapewniają funkcjonalność dla zdarzeń wejściowych związanych z naciśnięciami klawiszy, przyciskami myszy, kółkiem myszy, przenoszeniem myszy, zarządzaniem fokusem i przechwytywaniem myszy, co pozwala na kilka nazw. Umieszczając wejściowy interfejs API na elementach podstawowych, zamiast traktować wszystkie zdarzenia wejściowe jako usługę, architektura wejścia umożliwia źródło zdarzeń wejściowych przez określony obiekt w interfejsie użytkownika, a także obsługę schematu routingu zdarzeń, w przypadku których więcej niż jeden element ma OPP ortunity, aby obsłużyć zdarzenie wejściowe. Wiele zdarzeń wejściowych ma parę zdarzeń skojarzonych z nimi.  Na przykład zdarzenie Key w dół jest skojarzone ze zdarzeniami <xref:System.Windows.Input.Keyboard.KeyDown> i <xref:System.Windows.Input.Keyboard.PreviewKeyDown>.  Różnica w tych zdarzeniach jest w sposób, w jaki są kierowane do elementu docelowego.  Wyświetl podgląd zdarzeń w dół drzewo elementów od elementu głównego do elementu docelowego.  Propagacja zdarzeń z elementu docelowego do elementu głównego.  Routing zdarzeń w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] został szczegółowo omówiony w dalszej części tego omówienia oraz w [przeglądzie zdarzeń kierowanych](routed-events-overview.md).

### <a name="keyboard-and-mouse-classes"></a>Klasy klawiatury i myszy
 Oprócz wejściowych interfejsów API w klasach elementów podstawowych Klasa <xref:System.Windows.Input.Keyboard> i klasy <xref:System.Windows.Input.Mouse> oferują dodatkowe interfejsy API do pracy z klawiaturą i myszą.

 Przykładami wejściowego interfejsu API w klasie <xref:System.Windows.Input.Keyboard> są Właściwość <xref:System.Windows.Input.Keyboard.Modifiers%2A>, która zwraca <xref:System.Windows.Input.ModifierKeys> aktualnie naciśnięte i metodę <xref:System.Windows.Input.Keyboard.IsKeyDown%2A>, która określa, czy zostanie naciśnięty określony klucz.

 W poniższym przykładzie zastosowano metodę <xref:System.Windows.Input.Keyboard.GetKeyStates%2A>, aby określić, czy <xref:System.Windows.Input.Key> jest w stanie down.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 Przykłady wejściowych interfejsów API w klasie <xref:System.Windows.Input.Mouse> są <xref:System.Windows.Input.Mouse.MiddleButton%2A>, które uzyskują stan środkowego przycisku myszy, i <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, który pobiera element, który jest obecnie dostępny.

 Poniższy przykład określa, czy <xref:System.Windows.Input.Mouse.LeftButton%2A> na myszy jest w stanie <xref:System.Windows.Input.MouseButtonState.Pressed>.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 Klasy <xref:System.Windows.Input.Mouse> i <xref:System.Windows.Input.Keyboard> zostały omówione bardziej szczegółowo w tym omówieniu.

### <a name="stylus-input"></a>Wprowadzanie piórem
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma zintegrowane wsparcie dla <xref:System.Windows.Input.Stylus>.  @No__t-0 to dane wejściowe piórem, które są popularne przez komputer typu Tablet.  aplikacje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mogą traktować pióro jako mysz przy użyciu interfejsu API myszy, ale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uwidacznia także abstrakcję urządzenia pióra, która używa modelu podobnego do klawiatury i myszy.  Wszystkie interfejsy API związane z piórem zawierają słowo "Pisak".

 Ponieważ pióro może działać jako mysz, aplikacje obsługujące tylko wprowadzanie za pomocą myszy mogą w dalszym ciągu uzyskać obsługę pióra. Gdy pióro jest używane w taki sposób, aplikacja uzyskuje możliwość obsługi odpowiedniego zdarzenia pióra, a następnie obsługuje odpowiednie zdarzenie myszy. Ponadto usługi wyższego poziomu, takie jak dane wejściowe pisma odręcznego, są również dostępne za pomocą abstrakcji urządzenia pióra.  Aby uzyskać więcej informacji na temat pisma odręcznego, zobacz [wprowadzenie with Ink](getting-started-with-ink.md).

<a name="event_routing"></a>
## <a name="event-routing"></a>Routing zdarzeń
 @No__t-0 może zawierać inne elementy jako elementy podrzędne w modelu zawartości, tworząc drzewo elementów.  W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element nadrzędny może uczestniczyć w danych wejściowych skierowanych do elementów podrzędnych lub innych elementów podrzędnych przez skierowanie zdarzeń. Jest to szczególnie przydatne w przypadku kompilowania kontrolek z mniejszych kontrolek, procesów znanych jako "skład kontrolny" lub "złożenie". Aby uzyskać więcej informacji na temat drzew elementów i sposobu, w jaki drzewa elementów odnoszą się do tras zdarzeń, zobacz [drzewa w WPF](trees-in-wpf.md).

 Routing zdarzeń to proces przekazywania zdarzeń do wielu elementów, dzięki czemu określony obiekt lub element na trasie może zaoferować znaczną odpowiedź (za pomocą obsługi) do zdarzenia, które mogło zostać spowodowane przez inny element.  Zdarzenia kierowane korzystają z jednego z trzech mechanizmów routingu: bezpośrednie, propagacja i tunelowanie.  W przypadku routingu bezpośredniego element źródłowy jest jedynym powiadamianym elementem, a zdarzenie nie jest kierowane do żadnych innych elementów. Jednak bezpośrednie kierowanie Zdarzenia nadal oferuje pewne dodatkowe możliwości, które są dostępne tylko dla zdarzeń kierowanych, zamiast standardowych zdarzeń CLR. Propagacja działa w drzewie elementów przez pierwsze powiadomienie elementu, który podaje zdarzenie, następnie element nadrzędny i tak dalej.  Tunelowanie rozpoczyna się w katalogu głównym drzewa elementów i działa, kończąc na oryginalnym elemencie source.  Aby uzyskać więcej informacji na temat zdarzeń kierowanych, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).

 zdarzenia wejściowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zwykle są parami, które składają się z zdarzenia tunelowania i zdarzenia propagacji.  Zdarzenia tunelowania różnią się od propagacji zdarzeń z prefiksem "wersja zapoznawcza".  Na przykład, <xref:System.Windows.Input.Mouse.PreviewMouseMove> to wersja tunelowania zdarzenia przenoszenia myszy i <xref:System.Windows.Input.Mouse.MouseMove> jest wersją propagacji tego zdarzenia. To parowanie zdarzeń jest konwencją, która jest implementowana na poziomie elementu i nie jest nieodłączną możliwością systemu zdarzeń [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aby uzyskać szczegółowe informacje, zobacz sekcję zdarzenia wejściowe WPF w temacie [zdarzenia kierowane — Omówienie](routed-events-overview.md).

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Obsługa zdarzeń wejściowych
 Aby można było odbierać dane wejściowe dla elementu, program obsługi zdarzeń musi być skojarzony z tym konkretnym zdarzeniem.  W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest to proste: odwołanie się do nazwy zdarzenia jako atrybutu elementu, który będzie nasłuchiwać tego zdarzenia.  Następnie należy ustawić wartość atrybutu na nazwę zdefiniowanego programu obsługi zdarzeń na podstawie delegata.  Procedura obsługi zdarzeń musi być zapisywana w kodzie, C# takim jak i może być uwzględniona w pliku związanym z kodem.

 Zdarzenia klawiatury pojawiają się, gdy system operacyjny zgłasza kluczowe akcje, które występują, gdy fokus klawiatury znajduje się na elemencie. Zdarzenia myszy i pióra dzielą się na dwie kategorie: zdarzenia, które raportują zmiany w pozycji wskaźnika względem elementu, i zdarzenia, które raportują zmiany w stanie przycisków urządzeń.

### <a name="keyboard-input-event-example"></a>Przykład zdarzenia wejściowego klawiatury
 Poniższy przykład nasłuchuje naciśnięcie klawisza Strzałka w lewo.  Jest tworzony <xref:System.Windows.Controls.StackPanel>, który ma <xref:System.Windows.Controls.Button>.  Procedura obsługi zdarzeń do nasłuchiwania dla klawisza Strzałka w lewo jest dołączona do wystąpienia <xref:System.Windows.Controls.Button>.

 Pierwsza sekcja przykładu tworzy <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.Button> i dołącza procedurę obsługi zdarzeń dla <xref:System.Windows.UIElement.KeyDown>.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 Druga sekcja jest zapisywana w kodzie i definiuje procedurę obsługi zdarzeń.  Po naciśnięciu klawisza Strzałka w lewo, gdy <xref:System.Windows.Controls.Button> ma fokus klawiatury, program obsługi działa i kolor <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> zostanie zmieniony.  Jeśli klawisz jest wciśnięty, ale nie jest to klawisz Strzałka w lewo, kolor <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> zostanie zmieniony z powrotem do jego koloru początkowego.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Przykład zdarzenia wejściowego myszy
 W poniższym przykładzie kolor <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> jest zmieniany, gdy wskaźnik myszy zostanie przesunięty do <xref:System.Windows.Controls.Button>.  Kolor <xref:System.Windows.Controls.Control.Background%2A> jest przywracany, gdy mysz opuszcza <xref:System.Windows.Controls.Button>.

 Pierwsza sekcja przykładu tworzy <xref:System.Windows.Controls.StackPanel> i kontrolki <xref:System.Windows.Controls.Button> i dołącza obsługę zdarzeń dla zdarzeń <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> do <xref:System.Windows.Controls.Button>.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 Druga sekcja przykładu jest zapisywana w kodzie i definiuje procedury obsługi zdarzeń.  Gdy mysz przejdzie do <xref:System.Windows.Controls.Button>, kolor <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> zostanie zmieniony na <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Gdy mysz opuszcza <xref:System.Windows.Controls.Button>, kolor <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> zostanie zmieniony z powrotem na <xref:System.Windows.Media.Brushes.AliceBlue%2A>.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Wprowadzanie tekstu
 Zdarzenie <xref:System.Windows.ContentElement.TextInput> umożliwia nasłuchiwanie danych tekstowych w sposób niezależny od urządzenia. Klawiatura jest podstawowym środkiem wprowadzania tekstu, ale mowy, pismem ręcznym i innymi urządzeniami wejściowymi może również generować dane wejściowe tekstu.

 W przypadku wprowadzania z klawiatury [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] najpierw wysyła odpowiednie zdarzenia <xref:System.Windows.ContentElement.KeyDown> @ no__t-2 @ no__t-3. Jeśli te zdarzenia nie są obsługiwane, a klucz to tekst (a nie klawisz kontrolny, taki jak strzałki kierunkowe lub klawisze funkcyjne), zostanie zgłoszone zdarzenie <xref:System.Windows.ContentElement.TextInput>.  Nie zawsze jest proste mapowanie jeden do jednego między <xref:System.Windows.ContentElement.KeyDown> @ no__t-1 @ no__t-2 i <xref:System.Windows.ContentElement.TextInput> zdarzenia, ponieważ wiele naciśnięć klawiszy może generować pojedynczy znak wprowadzania tekstu, a pojedyncze naciśnięcia klawiszy mogą generować ciągi z wieloma znakami.  Jest to szczególnie prawdziwe w przypadku języków takich jak chiński, japoński i koreański, które używają edytorów Input Method Editors (IME) do generowania tysięcy możliwych znaków w odpowiadających im alfabetach.

 Gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wysyła zdarzenie <xref:System.Windows.ContentElement.KeyUp> @ no__t-2 @ no__t-3, <xref:System.Windows.Input.KeyEventArgs.Key%2A> jest ustawione na <xref:System.Windows.Input.Key.System?displayProperty=nameWithType>, jeśli naciśnięcia klawiszy mogą stać się częścią zdarzenia <xref:System.Windows.ContentElement.TextInput> (na przykład naciśnięcie klawisza ALT + S). Umożliwia to kod w programie obsługi zdarzeń <xref:System.Windows.ContentElement.KeyDown> w celu sprawdzenia, czy <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> i, w przypadku znalezienia, opuszcza przetwarzanie do obsługi zdarzenia <xref:System.Windows.ContentElement.TextInput>. W takich przypadkach różne właściwości argumentu <xref:System.Windows.Input.TextCompositionEventArgs> mogą służyć do określenia oryginalnych naciśnięć klawiszy. Analogicznie, jeśli edytor IME jest aktywny, <xref:System.Windows.Input.Key> ma wartość <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType> i <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> podaje oryginalne naciśnięcie klawiszy lub naciśnięcia klawiszy.

 W poniższym przykładzie zdefiniowano procedurę obsługi dla zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click> i programu obsługi dla zdarzenia <xref:System.Windows.UIElement.KeyDown>.

 Pierwszy segment kodu lub znaczników tworzy interfejs użytkownika.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 Drugi segment kodu zawiera programy obsługi zdarzeń.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Ponieważ zdarzenia wejściowe są bąbelkowe w górę trasy zdarzeń, <xref:System.Windows.Controls.StackPanel> otrzymuje dane wejściowe, niezależnie od tego, który element ma fokus klawiatury. Kontrolka <xref:System.Windows.Controls.TextBox> jest powiadamiana jako pierwsza, a procedura obsługi `OnTextInputKeyDown` jest wywoływana tylko wtedy, gdy <xref:System.Windows.Controls.TextBox> nie obsłużył danych wejściowych. Jeśli jest używane zdarzenie <xref:System.Windows.UIElement.PreviewKeyDown> zamiast zdarzenia <xref:System.Windows.UIElement.KeyDown>, program obsługi `OnTextInputKeyDown` jest wywoływany jako pierwszy.

 W tym przykładzie logika obsługi jest zapisywana dwa razy — jeden raz dla klawiszy CTRL + O i ponownie dla zdarzenia kliknięcia przycisku. Można to uprościć przy użyciu poleceń, zamiast bezpośrednio obsługiwać zdarzenia wejściowe.  Polecenia zostały omówione w tym przeglądzie i w [omówieniu poleceń](commanding-overview.md).

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Dotyk i manipulowanie
 Nowy sprzęt i interfejs API w systemie operacyjnym Windows 7 zapewniają aplikacjom możliwość otrzymywania danych wejściowych z wielu jednocześnie. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwia aplikacjom wykrywanie i reagowanie na dotknięcie w sposób podobny do odpowiedzi na inne dane wejściowe, takie jak mysz lub klawiatura, przez podnoszenie poziomu zdarzeń, gdy nastąpi dotknięcie.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uwidacznia dwa typy zdarzeń, gdy nastąpi dotknięcie: zdarzenia dotknięcia i zdarzenia manipulowania. Zdarzenia dotknięcia zapewniają pierwotne dane dotyczące każdego palca na ekranie dotykowym i jego ruchu. Zdarzenia manipulowania interpretują dane wejściowe jako określone akcje. W tej sekcji omówiono oba typy zdarzeń.

### <a name="prerequisites"></a>Wymagania wstępne
 Do tworzenia aplikacji, która reaguje na dotyk, potrzebne są następujące składniki.

- Program Visual Studio 2010.

- System Windows 7.

- Urządzenie, takie jak ekran dotykowy, obsługujące funkcję Touch systemu Windows.

### <a name="terminology"></a>Terminologia
 Poniższe terminy są używane podczas omawiania dotyku.

- **Dotyk** jest typem danych wprowadzonych przez użytkownika, które są rozpoznawane przez system Windows 7. Zwykle dotyk jest inicjowany przez umieszczenie palców na ekranie dotykowym. Należy zauważyć, że urządzenia takie jak płytka dotykowa, która jest często spotykana na komputerach przenośnych, nie obsługują dotyku, jeśli urządzenie tylko przekonwertuje pozycję i przemieszczenie palca jako dane wejściowe myszy.

- **Wielodotyku** jest dotknięciem, który występuje z więcej niż jednego punktu jednocześnie. Systemy Windows 7 i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługują wielodotyku. Za każdym razem, gdy program Touch zostanie omówiony w dokumentacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], pojęcia dotyczą wielodotyku.

- **Manipulowanie** występuje, gdy dotyk jest interpretowany jako fizyczna akcja zastosowana do obiektu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia manipulowania interpretują dane wejściowe jako operacje tłumaczenia, rozwinięcia lub obrotu.

- @No__t-0 reprezentuje urządzenie generujące dane wejściowe dotyku, takie jak pojedynczy Finger na ekranie dotykowym.

### <a name="controls-that-respond-to-touch"></a>Kontrolki, które reagują na dotyk
 Następujące kontrolki można przewijać, przeciągając palecę w kontrolce, jeśli ma ona zawartość, która jest przewijana z widoku.

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.ContextMenu>

- <xref:System.Windows.Controls.DataGrid>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListView>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.TextBox>

- <xref:System.Windows.Controls.ToolBar>

- <xref:System.Windows.Controls.TreeView>

 @No__t-0 definiuje dołączoną Właściwość <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType>, która pozwala określić, czy panoramowanie dotykowe jest włączone w poziomie, w pionie, czy nie. Właściwość <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> Określa, jak szybko przewijanie jest spowalniane, gdy użytkownik wydźwiga palca z ekranu dotykowego. Dołączona właściwość <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> określa stosunek przesunięcia przewijania do translacji przesunięcia manipulacji.

### <a name="touch-events"></a>Zdarzenia dotknięcia
 Klasy podstawowe, <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D> i <xref:System.Windows.ContentElement>, definiują zdarzenia, które można subskrybować, aby Twoja aplikacja odpowiadała na dotknięcie. Zdarzenia touch są przydatne, gdy aplikacja interpretuje dotyk jako coś innego niż manipulowanie obiektem. Na przykład aplikacja, która umożliwia użytkownikowi rysowanie przy użyciu co najmniej jednego palca, subskrybuje zdarzenia dotknięcia.

 Wszystkie trzy klasy definiują następujące zdarzenia, które zachowują się podobnie niezależnie od klasy definiującej.

- <xref:System.Windows.UIElement.TouchDown>

- <xref:System.Windows.UIElement.TouchMove>

- <xref:System.Windows.UIElement.TouchUp>

- <xref:System.Windows.UIElement.TouchEnter>

- <xref:System.Windows.UIElement.TouchLeave>

- <xref:System.Windows.UIElement.PreviewTouchDown>

- <xref:System.Windows.UIElement.PreviewTouchMove>

- <xref:System.Windows.UIElement.PreviewTouchUp>

- <xref:System.Windows.UIElement.GotTouchCapture>

- <xref:System.Windows.UIElement.LostTouchCapture>

 Podobnie jak zdarzenia klawiatury i myszy, zdarzenia touch są zdarzeniami kierowanymi. Zdarzenia, które zaczynają się od `Preview` są zdarzeniami tunelowania, a zdarzenia, które zaczynają się od `Touch` są zdarzeniami propagacji. Aby uzyskać więcej informacji na temat zdarzeń kierowanych, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md). Podczas obsługi tych zdarzeń można pobrać pozycję danych wejściowych względem dowolnego elementu, wywołując metodę <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> lub <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A>.

 Aby zrozumieć interakcję między zdarzeniami dotyku, Rozważmy scenariusz, w którym użytkownik umieszcza jeden palec w elemencie, przenosi palec w elemencie, a następnie dźwig palcem z elementu. Na poniższej ilustracji przedstawiono wykonywanie zdarzeń propagacji (zdarzenia tunelowania są pomijane dla uproszczenia).

 ![Sekwencja zdarzeń dotykowych.](./media/ndp-touchevents.png "NDP_TouchEvents") Zdarzenia dotknięcia

 Poniższa lista zawiera opis sekwencji zdarzeń na powyższej ilustracji.

1. Zdarzenie <xref:System.Windows.UIElement.TouchEnter> występuje jeden raz, gdy użytkownik umieści palca w elemencie.

2. Zdarzenie <xref:System.Windows.UIElement.TouchDown> występuje jeden raz.

3. Zdarzenie <xref:System.Windows.UIElement.TouchMove> występuje wiele razy, gdy użytkownik przenosi palec w obrębie elementu.

4. Zdarzenie <xref:System.Windows.UIElement.TouchUp> występuje jednorazowo, gdy użytkownik wychodzi z elementu.

5. Zdarzenie <xref:System.Windows.UIElement.TouchLeave> występuje jeden raz.

 Gdy używane są więcej niż dwa palców, zdarzenia są wykonywane dla każdego palca.

### <a name="manipulation-events"></a>Zdarzenia manipulowania
 W przypadku, gdy aplikacja umożliwia użytkownikowi manipulowanie obiektem, Klasa <xref:System.Windows.UIElement> definiuje zdarzenia manipulowania. W przeciwieństwie do zdarzeń dotykowych, które po prostu raportują pozycję Touch, zdarzenia manipulowania raportują, jak można interpretować dane wejściowe. Istnieją trzy typy manipulowania, tłumaczenia, rozwijania i obrotu. Na poniższej liście opisano, jak wywołać trzy typy manipulacji.

- Umieść palec na obiekcie i Przenieś palec na ekranie dotykowym, aby wywołać manipulowanie tłumaczeniami. Zwykle jest to przeniesienie obiektu.

- Umieść dwa Palcy na obiekcie i przesuń je bliżej siebie lub obok siebie, aby wywołać manipulowanie ekspansją. Zwykle zmieniany jest rozmiar obiektu.

- Umieść dwa Palcy w obiekcie i Obróć palcami wokół siebie, aby wywołać manipulowanie rotacją. Zwykle powoduje to obrócenie obiektu.

 Jednocześnie może wystąpić więcej niż jeden typ manipulowania.

 Gdy obiekty reagują na manipulacje, można mieć, że obiekt wydaje się być bezwładnością. Może to sprawiać, że obiekty są symulowane na świecie fizycznym. Na przykład w przypadku wypychania książki w ramach tabeli, jeśli wypchnięcie jest wystarczające, książka będzie nadal przenoszona po jej udostępnieniu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwia symulowanie tego zachowania przez podnoszenie poziomu zdarzeń manipulowania po zwolnieniu obiektu przez użytkownika.

 Aby uzyskać informacje o sposobie tworzenia aplikacji, która umożliwia użytkownikowi przenoszenie, zmienianie rozmiaru i obracanie obiektu, zobacz [Przewodnik: Tworzenie pierwszej aplikacji dotykowej](walkthrough-creating-your-first-touch-application.md).

 @No__t-0 definiuje następujące zdarzenia manipulowania.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Domyślnie <xref:System.Windows.UIElement> nie otrzymuje tych zdarzeń manipulowania. Aby otrzymywać zdarzenia manipulowania na <xref:System.Windows.UIElement>, ustaw <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> na `true`.

#### <a name="the-execution-path-of-manipulation-events"></a>Ścieżka wykonywania zdarzeń manipulowania
 Rozważmy scenariusz, w którym użytkownik "zgłosi" obiekt. Użytkownik umieszcza palca na obiekcie, przesuwa palec na ekranie dotykowym o krótkiej odległości, a następnie dźwiga podczas przesuwania. Wynikiem tego jest to, że obiekt zostanie przesunięty pod palcem użytkownika i będzie kontynuował pracę po wyjściu palca przez użytkownika.

 Na poniższej ilustracji przedstawiono ścieżkę wykonywania zdarzeń manipulacji i ważne informacje dotyczące poszczególnych zdarzeń.

 ![Sekwencja zdarzeń manipulowania.](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") Zdarzenia manipulowania

 Poniższa lista zawiera opis sekwencji zdarzeń na powyższej ilustracji.

1. Zdarzenie <xref:System.Windows.UIElement.ManipulationStarting> występuje, gdy użytkownik umieści palca w obiekcie. To zdarzenie jest między innymi ustawieniem właściwości <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. W kolejnych zdarzeniach pozycja manipulowania będzie odnosząca się do <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. W przypadku zdarzeń innych niż <xref:System.Windows.UIElement.ManipulationStarting> ta właściwość jest tylko do odczytu, więc zdarzenie <xref:System.Windows.UIElement.ManipulationStarting> jest jedynym czasem, w którym można ustawić tę właściwość.

2. Zdarzenie <xref:System.Windows.UIElement.ManipulationStarted> występuje dalej. To zdarzenie służy do zgłaszania pochodzenia manipulowania.

3. Zdarzenie <xref:System.Windows.UIElement.ManipulationDelta> występuje wiele razy, gdy użytkownik przechodzi na ekran dotykowy. Właściwość <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> klasy <xref:System.Windows.Input.ManipulationDeltaEventArgs> zgłasza, czy manipulowanie jest interpretowane jako przesunięcia, rozwinięcia czy tłumaczenie. Jest to miejsce, w którym wykonuje się większość pracy manipulowania obiektem.

4. Zdarzenie <xref:System.Windows.UIElement.ManipulationInertiaStarting> występuje, gdy palce utraci kontakt z obiektem. To zdarzenie umożliwia określenie opóźnienia manipulacji podczas bezwładności. Jest tak dlatego, że obiekt może emulować różne fizyczne miejsca lub atrybuty w przypadku wybrania opcji. Załóżmy na przykład, że aplikacja ma dwa obiekty reprezentujące elementy w świecie fizycznym, a jeden z nich jest grubszy niż drugi. Można sprawić, aby większy obiekt spowalniania szybciej niż jaśniejszy obiekt.

5. Zdarzenie <xref:System.Windows.UIElement.ManipulationDelta> występuje wiele razy, gdy nastąpi przełożenia bezwładności. Należy zauważyć, że to zdarzenie występuje, gdy użytkownik przechodzi przez palców na ekranie dotykowym i gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] symuluje bezwładności. Innymi słowy, <xref:System.Windows.UIElement.ManipulationDelta> występuje przed i po zdarzeniu <xref:System.Windows.UIElement.ManipulationInertiaStarting>. Właściwość <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> Określa, czy zdarzenie <xref:System.Windows.UIElement.ManipulationDelta> występuje w czasie bezwładności, więc można sprawdzić tę właściwość i wykonać różne akcje, w zależności od jej wartości.

6. Zdarzenie <xref:System.Windows.UIElement.ManipulationCompleted> występuje podczas manipulowania i dowolnych punktów końcowych. Oznacza to, że po wystąpieniu wszystkich <xref:System.Windows.UIElement.ManipulationDelta> zdarzenie <xref:System.Windows.UIElement.ManipulationCompleted> będzie miało na celu sygnalizowanie zakończenia manipulowania.

 @No__t-0 definiuje również zdarzenie <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>. To zdarzenie występuje, gdy metoda <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> jest wywoływana w zdarzeniu <xref:System.Windows.UIElement.ManipulationDelta>. Zdarzenie <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> umożliwia aplikacjom i składnikom dostarczanie wizualnych informacji zwrotnych, gdy obiekt osiągnie granicę. Na przykład Klasa <xref:System.Windows.Window> obsługuje zdarzenie <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>, aby spowodować nieco przechodzenie okna po napotkaniu jego krawędzi.

 Manipulację można anulować, wywołując metodę <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> w argumentach zdarzeń w każdym zdarzeniu manipulacji z wyjątkiem zdarzenia <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>. Gdy wywołasz <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, zdarzenia manipulowania nie są już wywoływane i pojawiają się zdarzenia myszy dla dotyku. W poniższej tabeli opisano relację między czasem anulowania manipulowania a zdarzeniami myszy, które wystąpiły.

|Zdarzenie, które Anuluj jest wywoływane w|Zdarzenia myszy występujące dla danych wejściowych, które już wystąpiły|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> i <xref:System.Windows.UIElement.ManipulationStarted>|Zdarzenia myszy.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Zdarzenia myszy i przenoszenia kursora myszy.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> i <xref:System.Windows.UIElement.ManipulationCompleted>|Mysz w dół, ruch przychodzący i wskaźnik myszy.|

 Należy pamiętać, że w przypadku wywołania <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, gdy manipulacja jest w trybie bezwładności, metoda zwraca `false`, a dane wejściowe nie powodują zdarzeń myszy.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Relacja między zdarzeniami dotykowymi i manipulowania
 @No__t-0 zawsze może odbierać zdarzenia dotknięcia. Gdy właściwość <xref:System.Windows.UIElement.IsManipulationEnabled%2A> jest ustawiona na wartość `true`, <xref:System.Windows.UIElement> może odbierać zarówno zdarzenia dotykowe, jak i manipulowania.  Jeśli zdarzenie <xref:System.Windows.UIElement.TouchDown> nie jest obsługiwane (oznacza to, że właściwość <xref:System.Windows.RoutedEventArgs.Handled%2A> jest `false`), logika manipulowania przechwytuje element i generuje zdarzenia manipulowania. Jeśli właściwość <xref:System.Windows.RoutedEventArgs.Handled%2A> jest ustawiona na wartość `true` w zdarzeniu <xref:System.Windows.UIElement.TouchDown>, logika manipulowania nie generuje zdarzeń manipulowania. Na poniższej ilustracji przedstawiono relacje między zdarzeniami Touch i zdarzeniami manipulowania.

 ![Relacja między zdarzeniami dotykowymi i manipulacji](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") zdarzenia dotykowe i manipulowania

 Poniższa lista zawiera opis relacji między zdarzeniami dotyku i manipulowania, które są wyświetlane na powyższej ilustracji.

- Gdy pierwsze urządzenie dotykowe generuje zdarzenie <xref:System.Windows.UIElement.TouchDown> na <xref:System.Windows.UIElement>, logika manipulowania wywołuje metodę <xref:System.Windows.UIElement.CaptureTouch%2A>, która generuje zdarzenie <xref:System.Windows.UIElement.GotTouchCapture>.

- Gdy występuje <xref:System.Windows.UIElement.GotTouchCapture>, logika operia wywołuje metodę <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType>, która generuje zdarzenie <xref:System.Windows.UIElement.ManipulationStarting>.

- Gdy wystąpią zdarzenia <xref:System.Windows.UIElement.TouchMove>, logika manipulowania generuje zdarzenia <xref:System.Windows.UIElement.ManipulationDelta>, które wystąpiły przed zdarzeniem <xref:System.Windows.UIElement.ManipulationInertiaStarting>.

- Gdy ostatnie urządzenie dotykowe w elemencie zgłasza zdarzenie <xref:System.Windows.UIElement.TouchUp>, logika manipulowania generuje zdarzenie <xref:System.Windows.UIElement.ManipulationInertiaStarting>.

<a name="focus"></a>
## <a name="focus"></a>Fokus
 Istnieją dwa główne pojęcia, które odnoszą się do koncentracji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: fokus klawiatury i fokus logiczny.

### <a name="keyboard-focus"></a>Fokus klawiatury
 Fokus klawiatury odnosi się do elementu, który otrzymuje dane wejściowe z klawiatury.  Na całym pulpicie może znajdować się tylko jeden element, który ma fokus klawiatury.  W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element, który ma fokus klawiatury, będzie miał ustawioną <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> wartość `true`.  Metoda static <xref:System.Windows.Input.Keyboard> <xref:System.Windows.Input.Keyboard.FocusedElement%2A> zwraca element, który aktualnie ma fokus klawiatury.

 Fokus klawiatury można uzyskać, naciskając klawisz Tab do elementu lub klikając myszą na określonych elementach, takich jak <xref:System.Windows.Controls.TextBox>.  Fokus klawiatury można również uzyskać programowo przy użyciu metody <xref:System.Windows.Input.Keyboard.Focus%2A> w klasie <xref:System.Windows.Input.Keyboard>.  <xref:System.Windows.Input.Keyboard.Focus%2A> próbuje nadać określony fokus klawiatury elementu.  Element zwrócony przez <xref:System.Windows.Input.Keyboard.Focus%2A> to element, który aktualnie ma fokus klawiatury.

 Aby element mógł uzyskać fokus klawiatury, właściwość <xref:System.Windows.UIElement.Focusable%2A> i właściwości <xref:System.Windows.UIElement.IsVisible%2A> muszą mieć wartość **true**.  Niektóre klasy, takie jak <xref:System.Windows.Controls.Panel>, mają domyślnie <xref:System.Windows.UIElement.Focusable%2A> ustawione na `false`; w związku z tym może być konieczne ustawienie tej właściwości na `true`, jeśli chcesz, aby ten element mógł uzyskać fokus.

 Poniższy przykład używa <xref:System.Windows.Input.Keyboard.Focus%2A>, aby ustawić fokus klawiatury na <xref:System.Windows.Controls.Button>.  Zalecane miejsce, aby ustawić początkowy fokus w aplikacji, znajduje się w obsłudze zdarzeń <xref:System.Windows.FrameworkElement.Loaded>.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Aby uzyskać więcej informacji na temat naciskania klawiatury, zobacz temat [Omówienie fokusu](focus-overview.md).

### <a name="logical-focus"></a>Fokus logiczny
 Fokus logiczny odnosi się do <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> w zakresie fokusu.  Może istnieć wiele elementów mających fokus logiczny w aplikacji, ale może istnieć tylko jeden element, który ma logiczne fokus w konkretnym zakresie fokusu.

 Zakres fokusu to element kontenera, który śledzi <xref:System.Windows.Input.FocusManager.FocusedElement%2A> w zakresie.  Gdy fokus opuszcza zakres fokusu, element skoncentrowany utraci fokus klawiatury, ale będzie utrzymywać fokus logiczny.  Gdy fokus powróci do zakresu fokusu, element skoncentrowany uzyska fokus klawiatury.  Pozwala to na zmianę fokusu klawiatury między wieloma zakresami fokusu, ale nie ma pewności, że element skoncentrowany w zakresie fokusu pozostaje elementem skoncentrowanym, gdy fokus jest zwracany.

 Element może zostać włączony do zakresu fokusu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przez ustawienie właściwości dołączonej <xref:System.Windows.Input.FocusManager> <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> do `true` lub w kodzie przez ustawienie właściwości dołączonej przy użyciu metody <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.

 W poniższym przykładzie <xref:System.Windows.Controls.StackPanel> do zakresu fokusu przez ustawienie dołączonej właściwości <xref:System.Windows.Input.FocusManager.IsFocusScope%2A>.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 Klasy w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które domyślnie są zakresy koncentracji, są <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar> i <xref:System.Windows.Controls.ContextMenu>.

 Element, który ma fokus klawiatury, będzie również miał fokus logiczny dla zakresu fokusu, do którego należy. w związku z tym ustawienie fokusu na elemencie z metodą <xref:System.Windows.Input.Keyboard.Focus%2A> w klasie <xref:System.Windows.Input.Keyboard> lub klasy elementu podstawowego podejmie próbę nawiązania fokusu na klawiaturze i logicznej ostrości.

 Aby określić element skoncentrowany w zakresie fokusu, użyj <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Aby zmienić element skoncentrowany dla zakresu fokusu, użyj <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.

 Aby uzyskać więcej informacji o koncentracji logicznej, zobacz temat [Omówienie fokusu](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Położenie myszy
 Interfejs API wejścia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia przydatne informacje w odniesieniu do przestrzeni współrzędnych.  Na przykład, koordynuj `(0,0)` to współrzędna górnej krawędzi, ale w lewym górnym rogu elementu drzewa? Element, który jest obiektem docelowym wprowadzania? Do którego elementu została dołączona procedura obsługi zdarzeń? Lub coś innego? Aby uniknąć nieporozumień, interfejs API wprowadzania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wymaga określenia ramki odwołania podczas pracy ze współrzędnymi uzyskanymi za pomocą myszy. Metoda <xref:System.Windows.Input.Mouse.GetPosition%2A> zwraca współrzędną wskaźnika myszy względem określonego elementu.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Przechwytywanie myszy
 Urządzenia myszy mają specjalne cechy modalne znane jako przechwycenie myszy. Przechwytywanie myszy służy do zachowywania stanu przejściowego danych wejściowych podczas uruchamiania operacji przeciągania i upuszczania, dzięki czemu inne operacje obejmujące nominalną pozycję na ekranie wskaźnika myszy nie muszą być wykonywane. Podczas przeciągania użytkownik nie może kliknąć bez przerywania przeciągania i upuszczania, co sprawia, że większość mouseoverych wskaźników jest nieodpowiedni, podczas gdy przechwytywanie myszy jest przechowywane przez punkt przeciągania. System wejściowy udostępnia interfejsy API, które mogą określać stan przechwytywania myszy, a także interfejsy API, które mogą wymusić przechwycenie myszy do określonego elementu lub wyczyścić stan przechwycenia myszy. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania, zobacz temat [Przeciąganie i upuszczanie — Omówienie](drag-and-drop-overview.md).

<a name="commands"></a>
## <a name="commands"></a>Polecenia
 Polecenia umożliwiają obsługę danych wejściowych na wyższym poziomie semantycznym niż dane wejściowe urządzenia.  Polecenia są prostymi dyrektywami, takimi jak `Cut`, `Copy`, `Paste` lub `Open`.  Polecenia są przydatne do scentralizowania logiki poleceń.  Do tego samego polecenia można uzyskać dostęp z <xref:System.Windows.Controls.Menu>, na <xref:System.Windows.Controls.ToolBar> lub za pomocą skrótu klawiaturowego. Polecenia udostępniają również mechanizm wyłączania formantów, gdy polecenie staną się niedostępne.

 <xref:System.Windows.Input.RoutedCommand> to implementacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommand>.  Po wykonaniu <xref:System.Windows.Input.RoutedCommand> zdarzenie <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> są wywoływane w celu wykonania polecenia, który tuneluje i bąbelki przez drzewo elementów, jak inne dane wejściowe.  Jeśli obiekt docelowy polecenia nie jest ustawiony, element z fokusem klawiatury będzie elementem docelowym polecenia.  Logika, która wykonuje polecenie, jest dołączona do <xref:System.Windows.Input.CommandBinding>.  Gdy zdarzenie <xref:System.Windows.Input.CommandManager.Executed> osiągnie <xref:System.Windows.Input.CommandBinding> dla tego konkretnego polecenia, zostanie wywołane <xref:System.Windows.Input.ExecutedRoutedEventHandler> na <xref:System.Windows.Input.CommandBinding>.  Ta procedura obsługi wykonuje akcję polecenia.

 Aby uzyskać więcej informacji na temat poleceń, zobacz [Omówienie poleceń](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia bibliotekę wspólnych poleceń, która składa się z <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands> i <xref:System.Windows.Documents.EditingCommands> lub można zdefiniować własne.

 Poniższy przykład pokazuje, jak skonfigurować <xref:System.Windows.Controls.MenuItem>, aby po jego kliknięciu wywoła polecenie <xref:System.Windows.Input.ApplicationCommands.Paste%2A> na <xref:System.Windows.Controls.TextBox>, przy założeniu, że <xref:System.Windows.Controls.TextBox> ma fokus klawiatury.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 Aby uzyskać więcej informacji na temat poleceń w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Omówienie poleceń](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>System wejściowy i elementy podstawowe
 Zdarzenia wejściowe, takie jak dołączone zdarzenia zdefiniowane przez <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard> i <xref:System.Windows.Input.Stylus> klasy są wywoływane przez system wejściowy i wstrzykiwane do określonej pozycji w modelu obiektów na podstawie trafień podczas testowania drzewa wizualnego w czasie wykonywania.

 Wszystkie zdarzenia, które <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard> i <xref:System.Windows.Input.Stylus> definiują jako dołączone zdarzenie, są również ponownie uwidaczniane przez klasy elementów podstawowych <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> jako nowe zdarzenie kierowane. Zdarzenia przesyłane do elementu podstawowego są generowane przez klasy obsługujące pierwotne dołączone zdarzenie i ponownie korzystające z danych zdarzenia.

 Gdy zdarzenie wejściowe stanie się skojarzone z konkretnym elementem źródłowym za pośrednictwem implementacji zdarzenia wejściowego elementu podstawowego, może być kierowane przez resztę trasy zdarzenia na podstawie kombinacji obiektów drzewa logicznego i wizualnego i być obsługiwane przez kod aplikacji.  Ogólnie rzecz biorąc, łatwiej jest obsługiwać te zdarzenia wejściowe powiązane z urządzeniem przy użyciu zdarzeń kierowanych na <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement>, ponieważ można użyć bardziej intuicyjnej składni procedury obsługi zdarzeń zarówno w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak i w kodzie. Można wybrać obsługę dołączonego zdarzenia, które zainicjowało proces, ale może wystąpić kilka problemów: dołączone zdarzenie może być oznaczone jako obsługiwane przez obsługę klasy elementu podstawowego i należy użyć metod dostępu zamiast prawdziwej składni zdarzeń w kolejności Aby dołączyć procedury obsługi dla dołączonych zdarzeń.

<a name="whats_next"></a>
## <a name="whats-next"></a>Co dalej
 Teraz masz kilka technik obsługi danych wejściowych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Należy również mieć ulepszone zrozumienie różnych typów zdarzeń wejściowych i mechanizmów zdarzeń kierowanych używanych przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Dostępne są dodatkowe zasoby, które bardziej szczegółowo opisują elementy struktury [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i routing zdarzeń. Zapoznaj się z poniższymi omówieniami, aby uzyskać więcej informacji, [Omówienie poleceń](commanding-overview.md), [Przegląd koncentracji](focus-overview.md), [Przegląd elementów podstawowych](base-elements-overview.md), [drzewa w WPF](trees-in-wpf.md)i [Informacje o rutowanych zdarzeniach](routed-events-overview.md).

## <a name="see-also"></a>Zobacz także

- [Przegląd fokusu](focus-overview.md)
- [Przegląd poleceń](commanding-overview.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Przegląd elementów podstawowych](base-elements-overview.md)
- [Właściwości](properties-wpf.md)
