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
ms.openlocfilehash: 6aae66de973c357b4b87578221a169bf750739fb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599016"
---
# <a name="input-overview"></a>Przegląd Dane wejściowe
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Podsystemu zapewnia zaawansowany [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] w celu uzyskania danych wejściowych z różnych urządzeń, m.in. myszy, klawiatury, touch i Pióro. W tym temacie opisano usługi świadczone przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i opisano architekturę systemów danych wejściowych.

<a name="input_api"></a>
## <a name="input-api"></a>Dane wejściowe interfejsu API
 Podstawowe dane wejściowe [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] narażenia znajduje się w klasach elementu base: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>, i <xref:System.Windows.FrameworkContentElement>.  Aby uzyskać więcej informacji na temat podstawowych elementów, zobacz [Przegląd elementów podstawowych](base-elements-overview.md).  Te klasy oferują funkcje dla danych wejściowych zdarzenia związane z naciśnięć klawiszy, przyciski myszy, kółka myszy ruchów myszy, funkcje zarządzania i przechwytywanie myszy w kilka. Umieszczając dane wejściowe [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] podstawowych elementów, zamiast traktując wszystkie zdarzenia wejściowe jako usługa, architektura wejścia umożliwia zdarzenia wejściowe ustalić źródło według określonego obiektu w interfejsie użytkownika i obsługuje schematu routingu zdarzeń, według których więcej niż jednego element ma możliwość obsługi dane wejściowe zdarzenia. Wiele zdarzeń wejściowych miała parę zdarzeń powiązanych z nimi.  Na przykład klucz szczegółów zdarzeń jest skojarzony z <xref:System.Windows.Input.Keyboard.KeyDown> i <xref:System.Windows.Input.Keyboard.PreviewKeyDown> zdarzenia.  Różnica w ramach tych zdarzeń jest w jaki sposób są kierowane do elementu docelowego.  Tunel zdarzenia (wersja zapoznawcza), dół drzewa elementów w elemencie głównym do elementu docelowego.  Propagacja zdarzeń będą się pojawiać się z elementu docelowego elementu głównego.  Zdarzenia, routing w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest omówiona bardziej szczegółowo w dalszej części tego omówienia i w [Przegląd zdarzeń kierowane](routed-events-overview.md).

### <a name="keyboard-and-mouse-classes"></a>Klawiatura i mysz klas
 Oprócz danych wejściowych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] w klasach elementu podstawowego, <xref:System.Windows.Input.Keyboard> klasy i <xref:System.Windows.Input.Mouse> klasy zapewniają dodatkowe [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] do pracy z klawiatury i myszy.

 Przykładowe dane wejściowe [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na <xref:System.Windows.Input.Keyboard> klasy są <xref:System.Windows.Input.Keyboard.Modifiers%2A> właściwość, która zwraca <xref:System.Windows.Input.ModifierKeys> obecnie naciśnięciu i <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> metody, która określa, czy określony klucz naciśnięciu.

 W poniższym przykładzie użyto <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> metodę, aby określić, czy <xref:System.Windows.Input.Key> znajduje się w stanie down.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 Przykładowe dane wejściowe [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na <xref:System.Windows.Input.Mouse> klasy są <xref:System.Windows.Input.Mouse.MiddleButton%2A>, która uzyskuje stan środkowego przycisku myszy, i <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, która pobiera element wskaźnik myszy jest obecnie nad.

 Poniższy przykład określa czy <xref:System.Windows.Input.Mouse.LeftButton%2A> w wskaźnik myszy znajduje się w <xref:System.Windows.Input.MouseButtonState.Pressed> stanu.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 <xref:System.Windows.Input.Mouse> i <xref:System.Windows.Input.Keyboard> klasy są opisane bardziej szczegółowo zawarte w tym omówieniu.

### <a name="stylus-input"></a>Wejście pióra
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] została zintegrowana obsługa <xref:System.Windows.Input.Stylus>.  <xref:System.Windows.Input.Stylus> Wejście pióra, takich jak strzelanki przez [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje można traktować pióro jako myszy przy użyciu myszy [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], ale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia również pióro abstrakcję urządzenia, które korzystają z modelu, podobnie jak klawiatury i myszy.  Wszystkie powiązane pióro [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] zawierają wyraz "Pióro".

 Ponieważ pióro może działać jako mysz, aplikacje, które obsługują jedynie wprowadzanie za pomocą myszy można nadal uzyskać pewien poziom pomocy technicznej pióro automatycznie. Gdy pióro jest używany w taki sposób, aplikacja ma możliwość obsługi zdarzenia odpowiednie pióra i następnie obsługuje odpowiednie zdarzenie myszy. Ponadto usługi wyższego poziomu, takie jak odręczne są również dostępne za pomocą pióra abstrakcję urządzenia.  Aby uzyskać więcej informacji na temat pisma odręcznego jako dane wejściowe, zobacz [wprowadzenie do użycia atramentu](getting-started-with-ink.md).

<a name="event_routing"></a>
## <a name="event-routing"></a>Routing zdarzeń
 A <xref:System.Windows.FrameworkElement> mogą zawierać inne elementy jako elementy podrzędne w modelu zawartości, tworzących drzewa elementów.  W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], element nadrzędny mogą uczestniczyć w danych wejściowych, zaleci jego elementów podrzędnych lub inne elementy podrzędne przekazywanie zdarzeń. Jest to szczególnie przydatne do tworzenia kontrolek z mniejszych formantów, proces ten jest znany jako "kompozycji formantu" lub "składania." Aby uzyskać więcej informacji na temat element drzewa i jak element drzewa odnoszą się do tras zdarzeń, zobacz [drzewa w WPF](trees-in-wpf.md).

 Routing zdarzeń to proces przesyłania dalej zdarzeń do wielu elementów, tak, aby wybrać konkretny obiekt lub element wzdłuż trasy oferowanie znaczących odpowiedzi (za pośrednictwem obsługę) do zdarzenia, które może być źródłem przez inny element.  Zdarzenia trasowane, użyj jednej z trzech mechanizmów routingu: bezpośredni, Propagacja i tunelowanie.  W routingu bezpośredniego element źródłowy jest jedynym elementem, o której powiadamiany i zdarzenie nie jest kierowany do innych elementów. Jednak bezpośredniego zdarzenie trasowane nadal oferuje pewne dodatkowe możliwości, które istnieją tylko dla zdarzenia trasowane, w przeciwieństwie do standardowego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenia. Propagacja polega na górę drzewa elementów pierwszego powiadamiania elementu, który jest źródłem zdarzeń, następnie element nadrzędny i tak dalej.  Tunelowanie rozpoczyna się od katalogu głównego drzewa elementów i działa w dół, kończąc oryginalny element źródła.  Aby uzyskać więcej informacji na temat zdarzenia trasowane, zobacz [Przegląd zdarzeń kierowane](routed-events-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia wejściowe są ogólnie dostępne w pary, które składa się z tunelowania zdarzeń i zdarzenia propagacji.  Zdarzenia tunelowania różnią się od Propagacja zdarzeń z prefiksem "Preview".  Na przykład <xref:System.Windows.Input.Mouse.PreviewMouseMove> jest wersja tunelowania zdarzenie przesunięcia kursora myszy i <xref:System.Windows.Input.Mouse.MouseMove> propagacji wersja tego zdarzenia. Parowanie to zdarzenie jest z Konwencją, która jest zaimplementowana na poziomie elementu, a nie nieprzerwaną pracę możliwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system zdarzeń. Aby uzyskać szczegółowe informacje, zobacz sekcję zdarzeń wejściowych WPF w [Przegląd zdarzeń kierowane](routed-events-overview.md).

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Obsługa zdarzeń wejściowych
 Dla danych wejściowych w elemencie, program obsługi zdarzeń musi być skojarzona z danego zdarzenia.  W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest bezpośrednie: odwoływać się do nazwy zdarzenia jako atrybutu elementu, który będzie nasłuchiwać dla tego zdarzenia.  Następnie należy ustawić wartość atrybutu nazwę programu obsługi zdarzeń, który zdefiniujesz, na podstawie obiektu delegowanego.  Program obsługi zdarzeń musi być napisana w kodzie, takim jak C# i mogą być zawarte w pliku związanym z kodem.

 Zdarzenia klawiatury występują, gdy system operacyjny zgłasza kluczowych działań, które wystąpiły w trakcie fokus klawiatury jest ustawiony na element. Mysz i Pióro zdarzenia każdego można podzielić na dwie kategorie: zdarzenia, które w raporcie zmienia się w pozycję wskaźnika względem elementu i zdarzenia, które raportu zmieni się w stanie przyciski urządzenia.

### <a name="keyboard-input-event-example"></a>Przykładowe dane wejściowe zdarzenia klawiatury
 Poniższy przykład nasłuchuje na naciśnięcie klawisza Strzałka w lewo.  A <xref:System.Windows.Controls.StackPanel> utworzono, która ma <xref:System.Windows.Controls.Button>.  Program obsługi zdarzeń do nasłuchiwania na naciśnięcie klawisza Strzałka w lewo jest dołączony do <xref:System.Windows.Controls.Button> wystąpienia.

 Pierwsza sekcja przykład tworzy <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.Button> i dołącza program obsługi zdarzeń dla <xref:System.Windows.UIElement.KeyDown>.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 Druga sekcja są zapisywane w kodzie, a także określa procedurę obsługi zdarzeń.  Kiedy wciśnięto klawisz Strzałka w lewo i <xref:System.Windows.Controls.Button> ma fokus klawiatury, uruchamia program obsługi i <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> zostanie zmieniony.  Jeśli zostanie naciśnięty, ale nie jest klawisz Strzałka w lewo <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> zmieniony na jej kolor początkowy.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Przykładowe dane wejściowe zdarzenia myszy
 W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> jest zmieniany, gdy wskaźnik myszy zostanie <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.Control.Background%2A> Kolorów jest przywracany po opuszczeniu przez wskaźnik myszy <xref:System.Windows.Controls.Button>.

 Pierwsza sekcja przykład tworzy <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.Button> kontroli i dołącza obsługę zdarzeń dla <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> zdarzenia <xref:System.Windows.Controls.Button>.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 Druga sekcja przykładu są zapisywane w kodzie i definiuje procedury obsługi zdarzeń.  Gdy wskaźnik myszy zostanie przesunięty <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> jest zmieniana na <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Gdy wskaźnik myszy opuszcza <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> zmieniony na <xref:System.Windows.Media.Brushes.AliceBlue%2A>.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Wprowadzanie tekstu
 <xref:System.Windows.ContentElement.TextInput> Zdarzenie pozwala wykrywać wprowadzanie tekstu w sposób niezależny od urządzenia. Klawiatury jest podstawowym elementem używanym pisma ręcznego wprowadzania, ale mowy, tekst i inne urządzenia wejściowego może generować również tekstowego.

 Dla danych wprowadzonych z klawiatury [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] najpierw wysyła odpowiednie <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> zdarzenia. Jeśli te zdarzenia nie są obsługiwane, a klucz jest tekstowych zamiast (klawisz control takich jak strzałki kierunkowej) lub klawiszy funkcyjnych, a następnie <xref:System.Windows.ContentElement.TextInput> zdarzenie jest wywoływane.  Nie ma zawsze prostego mapowanie jeden do jednego między <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> i <xref:System.Windows.ContentElement.TextInput> zdarzenia, ponieważ wiele naciśnięć klawiszy można wygenerować pojedynczy znak wprowadzania tekstu i pojedynczego naciśnięcia klawiszy może generować wielu znaków ciągi.  Jest to szczególnie istotne dla języków, takich jak chiński i japoński, koreański, które używają [!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)] do generowania tysiące możliwe znaki w alfabety odpowiednie.

 Gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wysyła <xref:System.Windows.ContentElement.KeyUp> / <xref:System.Windows.ContentElement.KeyDown> zdarzenia <xref:System.Windows.Input.KeyEventArgs.Key%2A> jest ustawiona na <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> Jeśli naciśnięcia klawiszy może stać się częścią <xref:System.Windows.ContentElement.TextInput> zdarzenia (jeśli ALT + S jest wciśnięty, na przykład). Dzięki temu kod w <xref:System.Windows.ContentElement.KeyDown> programu obsługi zdarzeń, aby wyszukać <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> i, jeśli znaleziono, pozostaw przetwarzania program obsługi zostaje zgłoszone później <xref:System.Windows.ContentElement.TextInput> zdarzeń. W tych przypadkach różne właściwości <xref:System.Windows.Input.TextCompositionEventArgs> można użyć argumentu, aby określić, oryginalnym naciśnięć klawiszy. Podobnie jeśli [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] jest aktywny, <xref:System.Windows.Input.Key> ma wartość <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>, i <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> zapewnia, oryginalnym naciśnięcia klawisza lub naciśnięć klawiszy.

 W poniższym przykładzie zdefiniowano program obsługi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń i obsługi dla <xref:System.Windows.UIElement.KeyDown> zdarzeń.

 Pierwszy segment kodu lub języka znaczników jest tworzony interfejs użytkownika.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 Drugi segment kodu zawiera procedury obsługi zdarzeń.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Ponieważ zdarzenia wejściowe przetwarzany trasy zdarzeń <xref:System.Windows.Controls.StackPanel> odbiera dane wejściowe, niezależnie od tego, który element ma fokus klawiatury. <xref:System.Windows.Controls.TextBox> Kontroli jest powiadamiany najpierw i `OnTextInputKeyDown` program obsługi jest wywoływany tylko wtedy, gdy <xref:System.Windows.Controls.TextBox> nie obsłużyła danych wejściowych. Jeśli <xref:System.Windows.UIElement.PreviewKeyDown> zdarzeń jest używany zamiast <xref:System.Windows.UIElement.KeyDown> zdarzenia `OnTextInputKeyDown` program obsługi jest wywoływany jako pierwszy.

 W tym przykładzie logika obsługi są zapisywane dwa razy — raz dla CTRL + O, a następnie dla przycisku kliknij zdarzenie. Może to uproszczona, za pomocą poleceń, a nie bezpośrednio obsługi zdarzenia wejściowe.  Polecenia zostały omówione w tym omówieniu, a w [polecenia Przegląd](commanding-overview.md).

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Dotyk i manipulowania
 Nowego sprzętu i interfejsu API w systemu operacyjnego Windows 7 należy udostępnić aplikacjom możliwość odbierania danych z wielu poprawek jednocześnie. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia aplikacjom wykrywanie oraz reagowanie na dotyk w sposób podobny do reagowania na inne dane wejściowe, takie jak myszy lub klawiatury, przez wywoływanie zdarzeń, gdy wystąpi touch.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia dwa typy zdarzeń, gdy wystąpi touch: touch zdarzenia i manipulowania. Zdarzenia Touch udostępniają dane pierwotne dotyczące każdego palcem na ekranie dotykowym i jego ruchu. Zdarzenia manipulowania interpretowania danych wejściowych jako pewne akcje. Oba rodzaje zdarzeń zostały omówione w tej sekcji.

### <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki do tworzenia aplikacji, która reaguje na dotyk są wymagane.

- Visual Studio 2010.

- Windows 7.

- Urządzenie, na przykład ekranu dotykowego, który obsługuje Windows Touch.

### <a name="terminology"></a>Terminologia
 Poniższe terminy są używane, gdy omówiono touch.

- **Touch** jest typem danych wejściowych użytkownika, który jest rozpoznawany przez Windows 7. Zazwyczaj touch jest inicjowane przez umieszczenie palców na ekranie dotykowej. Należy pamiętać, że urządzeń, takich jak dotykowej, który często na komputerach przenośnych obsługuje touch, gdy urządzenie jedynie konwertuje pozycję i przepływu jako wejście myszy finger.

- **Multitouch** jest touch, która występuje z więcej niż jeden punkt jednocześnie. Windows 7 i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje multitouch. Zawsze, gdy touch opisanej w dokumentacji dotyczącej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], stosowania pojęć do multitouch.

- A **manipulowania** występuje, gdy touch jest interpretowany jako fizycznych akcji, która jest stosowana do obiektu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], manipulowania zdarzenia interpretowanie danych wejściowych jako manipulowania tłumaczenia, rozszerzenia lub obrotu.

- A `touch device` reprezentuje urządzenie, które generuje dotykowym, takich jak pojedynczy palcem na ekranie dotykowym.

### <a name="controls-that-respond-to-touch"></a>Formanty, które odpowiadają Touch
 Może być przewijane następujące kontrolki, przeciągając palcem na formant ma zawartość, która jest przewijane poza widokiem.

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.ContextMenu>

- <xref:System.Windows.Controls.DataGrid>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListView>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.TextBox>

- <xref:System.Windows.Controls.ToolBar>

- <xref:System.Windows.Controls.TreeView>

 <xref:System.Windows.Controls.ScrollViewer> Definiuje <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> dołączona właściwość, która pozwala na określenie, czy przesuwanie dotykowe jest włączony w pionie, w poziomie, obie lub nie. <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> Właściwość określa, jak szybko przewijania spowalnia po użytkownik wind palcem z ekran dotykowy. <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> Dołączoną właściwość określa współczynnik przewijanie przesunięcie do translacji przesunięcie manipulacji.

### <a name="touch-events"></a>Zdarzenia dotykowe
 Klasy bazowe <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>, i <xref:System.Windows.ContentElement>, definiowanie zdarzeń, które możesz zasubskrybować aplikacja będzie reagować na touch. Zdarzenia dotykowe są przydatne, gdy aplikacja interpretuje touch jako coś innego niż manipulowanie obiektu. Na przykład aplikację, która umożliwia użytkownikowi Rysowanie za pomocą co najmniej jeden palców może subskrybować zdarzenia dotykowe.

 Wszystkie trzy klasy definiują następujące zdarzenia, które działają w podobny sposób, niezależnie od tego, definiowanie klas.

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

 Podobnie jak w przypadku zdarzeń klawiatury oraz myszy zdarzenia dotykowe są zdarzenia trasowane. Zdarzenia, które zaczynają się od `Preview` są tunelowanie zdarzeń i zdarzeń, które zaczynają się od `Touch` są zdarzenia propagacji. Aby uzyskać więcej informacji na temat zdarzenia trasowane, zobacz [Przegląd zdarzeń kierowane](routed-events-overview.md). Podczas obsługi tych zdarzeń, pozycja danych wejściowych, względem dowolnego elementu można uzyskać przez wywołanie metody <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> lub <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> metody.

 Aby zrozumieć interakcję między zdarzenia dotykowe, Rozważmy scenariusz, w którym użytkownik umieszcza jednym palcem w elemencie, przenosi palca w elemencie i następnie wind palcem z elementu. Poniższa ilustracja przedstawia wykonywania Propagacja zdarzeń (tunelowania zdarzenia są pomijane dla uproszczenia).

 ![Kolejność zdarzeń touch. ](./media/ndp-touchevents.png "NDP_TouchEvents") zdarzenia dotykowe

 Poniższa lista zawiera opis sekwencji zdarzeń na poprzedniej ilustracji.

1. <xref:System.Windows.UIElement.TouchEnter> Jeden raz po użytkownik umieszcza palcem w elemencie wystąpi zdarzenie.

2. <xref:System.Windows.UIElement.TouchDown> Zdarzenie wystąpi jeden raz.

3. <xref:System.Windows.UIElement.TouchMove> Zdarzeń powtarza się wielokrotnie, gdy użytkownik przesuwa palca w elemencie.

4. <xref:System.Windows.UIElement.TouchUp> Zdarzenie wystąpi jeden raz po użytkownik wind palcem z elementu.

5. <xref:System.Windows.UIElement.TouchLeave> Zdarzenie wystąpi jeden raz.

 W przypadku używania więcej niż dwóch palców wystąpienia zdarzenia, dla każdej linii papilarnych.

### <a name="manipulation-events"></a>Zdarzenia manipulowania
 W przypadkach, gdy aplikacja umożliwia użytkownikowi manipulowania obiektu <xref:System.Windows.UIElement> klasa definiuje do manipulowania zdarzenia. W przeciwieństwie do zdarzeń touch, które po prostu Zgłoś pozycja touch zdarzenia manipulowania raportu, jak interpretować dane wejściowe. Istnieją trzy typy manipulacje, tłumaczenia, rozszerzenia oraz obrotu. Na poniższej liście opisano, jak wywołać trzy rodzaje manipulacji.

- Umieść palcem na obiekcie i finger poruszają się ekran dotykowy do wywołania manipulowania tłumaczenia. Przenosi to zazwyczaj obiekt.

- Umieścić dwóch palców dla obiektu, a następnie przenieść palców, razem lub oddalone od siebie, aby wywołać manipulowania rozszerzenia. To zazwyczaj zmienia rozmiar obiektu.

- Umieść dwóch palców dla obiektu i Obróć palców wokół sobą w celu wywołania manipulowania obrotu. Obraca to zazwyczaj obiekt.

 Jednocześnie może występować więcej niż jeden typ manipulacji.

 Po powoduje, że obiekty odpowiedzieć na manipulacje, będziesz mieć obiekt ma bezwładności. Dzięki temu może być obiektów symulacji świata fizycznego. Na przykład podczas wypychania książki w tabeli, jeśli wypchniesz twardych wystarczająco książki będzie przenoszone po jego zwolnieniu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia symulowanie to zachowanie, tworząc do manipulowania zdarzenia po palców użytkownika zwalnia obiekt.

 Aby uzyskać informacje o sposobie tworzenia aplikacji, która umożliwia użytkownikowi przenoszenie, zmienianie rozmiaru i obracanie obiektu, zobacz [instruktażu: Tworzenie pierwszej aplikacji dotykowej](walkthrough-creating-your-first-touch-application.md).

 <xref:System.Windows.UIElement> Definiuje następujące zdarzenia manipulowania.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Domyślnie <xref:System.Windows.UIElement> nie otrzymuje tych do manipulowania zdarzenia. Aby odbierać zdarzenia manipulowania na <xref:System.Windows.UIElement>ustaw <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> do `true`.

#### <a name="the-execution-path-of-manipulation-events"></a>Ścieżki wykonywania do manipulowania zdarzenia
 Rozważmy scenariusz, w którym użytkownik "zgłasza" obiekt. Użytkownik umieszcza palcem w obiekcie, porusza się palcem na ekran dotykowy na krótką odległość, a następnie wind palca podczas przesuwania. Z tego powodu jest obiekt będzie Przenieś finger użytkownika oraz przenieść po użytkownik wind palcem w dalszym ciągu.

 Poniższa ilustracja przedstawia ścieżki wykonywania do manipulowania zdarzenia i ważnych informacji dotyczących każdego zdarzenia.

 ![Sekwencja do manipulowania zdarzenia. ](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") do manipulowania zdarzenia

 Poniższa lista zawiera opis sekwencji zdarzeń na poprzedniej ilustracji.

1. <xref:System.Windows.UIElement.ManipulationStarting> Zdarzenie występuje, gdy użytkownik umieści palcem na obiekcie. Między innymi, to zdarzenie pozwala na ustawienie <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> właściwości. W ramach kolejnych zdarzeń będzie pozycja operowanie atrybutami względem <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. W zdarzeniach innych niż <xref:System.Windows.UIElement.ManipulationStarting>, ta właściwość jest tylko do odczytu, więc <xref:System.Windows.UIElement.ManipulationStarting> zdarzenie jest jedyną sytuacją, którego można ustawić tej właściwości.

2. <xref:System.Windows.UIElement.ManipulationStarted> Następne wystąpienie zdarzenia. To zdarzenie raporty pochodzenia operowanie atrybutami.

3. <xref:System.Windows.UIElement.ManipulationDelta> Zdarzenie występuje wiele razy, ile przenoszenie palców użytkowników na ekranie dotykowym. <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> Właściwość <xref:System.Windows.Input.ManipulationDeltaEventArgs> klasa raportuje, czy operowanie jest interpretowany jako przepływu, rozszerzenia lub tłumaczenia. Jest to, gdzie wykonać większość zadań wykonywania operacji na obiekcie.

4. <xref:System.Windows.UIElement.ManipulationInertiaStarting> Zdarzenie występuje, gdy palców użytkownika utracą połączenie z obiektem. To zdarzenie umożliwia określenie spowolnieniu manipulacje podczas bezwładności. Jest to więc obiektu może emulować różnych fizycznego miejsca do magazynowania lub atrybutów, jeśli wybierzesz. Na przykład załóżmy, że Twoja aplikacja ma dwa obiekty, które reprezentują elementy w świecie fizycznym, a jedna jest większe niż ten drugi. Można wprowadzić obiekt większych zwalnianie szybciej niż jaśniejsze obiektu.

5. <xref:System.Windows.UIElement.ManipulationDelta> Zdarzeń powtarza się wielokrotnie, ponieważ występuje bezwładności. Należy pamiętać, że to zdarzenie występuje podczas palców użytkownika poruszają się ekran dotykowy i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] symuluje bezwładności. Innymi słowy <xref:System.Windows.UIElement.ManipulationDelta> występuje przed i po nim <xref:System.Windows.UIElement.ManipulationInertiaStarting> zdarzeń. <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> Raportów właściwości czy <xref:System.Windows.UIElement.ManipulationDelta> zdarzenie występuje w ciągu bezwładności, aby można było sprawdzić właściwości i wykonywania różnych akcji, w zależności od jego wartość.

6. <xref:System.Windows.UIElement.ManipulationCompleted> Wystąpi zdarzenie zakończenia manipulacji i bezwładności wszystkie. Oznacza to, że po wszystkich <xref:System.Windows.UIElement.ManipulationDelta> wystąpieniu zdarzenia, <xref:System.Windows.UIElement.ManipulationCompleted> wystąpi zdarzenie do sygnalizowania, że operowanie została zakończona.

 <xref:System.Windows.UIElement> Definiuje również <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> zdarzeń. To zdarzenie występuje, gdy <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> metoda jest wywoływana w <xref:System.Windows.UIElement.ManipulationDelta> zdarzeń. <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> Zdarzeń umożliwia aplikacji lub składników przekazać wizualną opinię, gdy obiekt osiągnie granicę. Na przykład <xref:System.Windows.Window> klasy obsługuje <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> zdarzenie, aby spowodować, że okno nieco przenieść po napotkaniu jego krawędzi.

 Operowanie można anulować, wywołując <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> metody argumenty zdarzeń w każdym przypadku manipulowania, z wyjątkiem <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> zdarzeń. Gdy wywołujesz <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>zdarzenia myszy zachodzą na dotyk i manipulowania zdarzenia nie są wywoływane. W poniższej tabeli opisano relację między podczas modyfikowania zostanie anulowane i zdarzenia myszy, które wystąpiły.

|Zdarzenie, które anulowanie jest wywoływana w|Zdarzenia myszy, które wystąpiły dla danych wejściowych, które już wystąpiły|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> i <xref:System.Windows.UIElement.ManipulationStarted>|Wskaźnik myszy w dół do zdarzenia.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Naciśnięcia przycisku myszy i myszy przesuń zdarzenia.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> i <xref:System.Windows.UIElement.ManipulationCompleted>|Naciśnięcia myszą i myszy zdarzenia przycisku myszy.|

 Należy pamiętać, że jeśli wywołasz <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> podczas modyfikowania znajduje się w bezwładności, metoda zwraca `false` i dane wejściowe nie zgłaszać zdarzenia myszy.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Relacja między Dotyk i manipulowania zdarzenia
 A <xref:System.Windows.UIElement> zawsze może odbierać zdarzenia touch. Gdy <xref:System.Windows.UIElement.IsManipulationEnabled%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.UIElement> może odbierać zdarzenia dotykowe i manipulowania.  Jeśli <xref:System.Windows.UIElement.TouchDown> zdarzenie nie jest obsługiwane (czyli <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość jest `false`), logiki manipulowania przechwytuje touch do elementu i generuje zdarzenia manipulowania. Jeśli <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość jest ustawiona na `true` w <xref:System.Windows.UIElement.TouchDown> zdarzenia logiki manipulacji nie generuje do manipulowania zdarzenia. Poniższa ilustracja przedstawia relację między zdarzenia dotykowe i manipulowania.

 ![Relacja między zdarzeniami Dotyk i manipulowania](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") Dotyk i manipulowania zdarzenia

 Na poniższej liście opisano relację między Dotyk i manipulowania zdarzenia, które jest wyświetlany na poprzedniej ilustracji.

- Podczas pierwszego urządzenia dotykowe generuje <xref:System.Windows.UIElement.TouchDown> zdarzenie na <xref:System.Windows.UIElement>, wywołania logiki manipulowania <xref:System.Windows.UIElement.CaptureTouch%2A> metody, która generuje <xref:System.Windows.UIElement.GotTouchCapture> zdarzeń.

- Gdy <xref:System.Windows.UIElement.GotTouchCapture> występuje wywołania logiki manipulowania <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> metody, która generuje <xref:System.Windows.UIElement.ManipulationStarting> zdarzeń.

- Gdy <xref:System.Windows.UIElement.TouchMove> wystąpieniu zdarzenia, generuje logiki manipulowania <xref:System.Windows.UIElement.ManipulationDelta> wydarzenia, występujących przed <xref:System.Windows.UIElement.ManipulationInertiaStarting> zdarzeń.

- Podczas ostatniego touch urządzenia element zgłasza <xref:System.Windows.UIElement.TouchUp> generuje logiki manipulowania zdarzenia <xref:System.Windows.UIElement.ManipulationInertiaStarting> zdarzeń.

<a name="focus"></a>
## <a name="focus"></a>fokus
 Istnieją dwa główne pojęcia, które odnoszą się skoncentrować się [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: za pomocą klawiatury fokus i fokus logiczny.

### <a name="keyboard-focus"></a>Fokus klawiatury
 Fokus klawiatury odnosi się do elementu, który odbiera dane wejściowe z klawiatury.  Może istnieć tylko jeden element dla całego pulpitu, który ma fokus klawiatury.  W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], będzie mieć element, który ma fokus klawiatury <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> równa `true`.  Statyczne <xref:System.Windows.Input.Keyboard> metoda <xref:System.Windows.Input.Keyboard.FocusedElement%2A> zwraca element, który aktualnie ma fokus klawiatury.

 Fokus klawiatury można uzyskać, przechodząc do elementu, lub przez kliknięcie przycisku myszy w przypadku niektórych elementów, takich jak <xref:System.Windows.Controls.TextBox>.  Fokus klawiatury można także uzyskać programistycznie przy użyciu <xref:System.Windows.Input.Keyboard.Focus%2A> metody <xref:System.Windows.Input.Keyboard> klasy.  <xref:System.Windows.Input.Keyboard.Focus%2A> próbuje zapewniają fokus klawiatury określonego elementu.  Zwrócony przez element <xref:System.Windows.Input.Keyboard.Focus%2A> jest elementem, który aktualnie ma fokus klawiatury.

 Aby element uzyskać fokus klawiatury <xref:System.Windows.UIElement.Focusable%2A> właściwości i <xref:System.Windows.UIElement.IsVisible%2A> właściwości musi być równa **true**.  Niektóre klasy takie jak <xref:System.Windows.Controls.Panel>, mają <xref:System.Windows.UIElement.Focusable%2A> równa `false` domyślnie; w związku z tym, należy ustawić tę właściwość na `true` Jeśli chcesz, aby ten element, aby można było uzyskać fokus.

 W poniższym przykładzie użyto <xref:System.Windows.Input.Keyboard.Focus%2A> ustawić fokus klawiatury na <xref:System.Windows.Controls.Button>.  Zalecane miejscem, aby ustawić początkowy fokus w aplikacji jest <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Aby uzyskać więcej informacji na temat fokus klawiatury, zobacz [Przegląd fokus](focus-overview.md).

### <a name="logical-focus"></a>Fokus logiczny
 Fokus logiczny, który odwołuje się do <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> w zakresie fokus.  Może istnieć wiele elementów, które mają logiczny fokus w aplikacji, ale może istnieć tylko jeden element, który ma logiczny fokus w zakresie określonego zespołu.

 Zakres fokus jest element kontenera, który śledzi <xref:System.Windows.Input.FocusManager.FocusedElement%2A> w jego zakresie.  Gdy zakres fokus utraci fokus, wąsko zdefiniowany element utraci fokus klawiatury, ale zachowa fokus logiczny.  Po powrocie do zakresu fokus fokus wąsko zdefiniowany element uzyska fokus klawiatury.  Umożliwia fokus klawiatury zmiany między wiele zakresów fokus, ale uzyskanie, że element wąsko zdefiniowany w zakresie fokus powrót, pozostanie wąsko zdefiniowany element.

 Element można włączyć do danego zakresu fokus w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , ustawiając <xref:System.Windows.Input.FocusManager> dołączona właściwość <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> do `true`, lub w kodzie przez ustawienie właściwości dołączonych przy użyciu <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> metody.

 Poniższy przykład wykonuje <xref:System.Windows.Controls.StackPanel> do zakresu fokus, ustawiając <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> dołączona właściwość.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 Klasy w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , które są zakresy fokus, domyślnie są <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, i <xref:System.Windows.Controls.ContextMenu>.

 Element, który ma fokus klawiatury będą mieć również fokus logiczny dla zakresu fokus, której należy. w związku z tym, ustawienie fokusu na element z <xref:System.Windows.Input.Keyboard.Focus%2A> metody <xref:System.Windows.Input.Keyboard> klasy lub klas elementu podstawowego podejmie próbę zapewniają fokus klawiatury elementem i logiczny fokus.

 Aby określić konkretną elementu w zakresie fokus, użyj <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Aby zmienić element wąsko zdefiniowany dla zakresu fokus, użyj <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.

 Aby uzyskać więcej informacji na temat fokus logiczny zobacz [Przegląd fokus](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Położenie myszy
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Wejściowych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] zawiera informacje pomocne w odniesieniu do przestrzeni współrzędnych.  Na przykład, koordynować `(0,0)` Współrzędna lewej górnej, ale w lewym górnym rogu elementu, który w drzewie? Element, który jest elementem docelowym danych wejściowych? Element dołączone do procedury obsługi zdarzenia? Albo coś innego? Aby uniknąć pomyłek, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wejściowych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] wymaga określenia z układem odniesienia podczas pracy z współrzędne uzyskanej za pomocą myszy. <xref:System.Windows.Input.Mouse.GetPosition%2A> Metoda zwraca współrzędne wskaźnika myszy względem określonego elementu.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Przechwytywanie myszy
 Myszy przytrzymaj specjalnie modalne cech, znane jako przechwytywanie myszy. Przechwytywanie myszy jest używany do obsługi przejściowym stanu danych wejściowych, po rozpoczęciu operacji przeciągania i upuszczania, aby inne operacje na ekranie obejmujące nominalna pozycji wskaźnika myszy nie zawsze występują. Podczas przeciągania użytkownik nie może kliknąć bez przerywania przeciągania i upuszczania, co sprawia, że większość podpowiedzi mouseover niewłaściwe podczas przechwytywania myszy jest utrzymywane przez element źródłowy przeciągania. Udostępnia system wejściowy [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , można określić stanu przechwytywanie myszy, jak i [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , wymusić przechwytywanie myszy określony element lub Wyczyść stan przechwytywanie myszy. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania, zobacz [przeciągania i upuszczania Przegląd](drag-and-drop-overview.md).

<a name="commands"></a>
## <a name="commands"></a>Polecenia
 Polecenia włączenia obsługi danych wejściowych na poziomie semantycznego więcej niż dane wejściowe z urządzenia.  Polecenia są proste dyrektywy `Cut`, `Copy`, `Paste`, lub `Open`.  Polecenia są przydatne w przypadku Centralizowanie logikę polecenia.  To polecenie może być uzyskiwany z <xref:System.Windows.Controls.Menu>na <xref:System.Windows.Controls.ToolBar>, lub za pomocą skrótów klawiaturowych. Polecenia udostępniają mechanizm wyłączenie formantów, gdy polecenie staje się niedostępny.

 <xref:System.Windows.Input.RoutedCommand> jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji <xref:System.Windows.Input.ICommand>.  Gdy <xref:System.Windows.Input.RoutedCommand> jest wykonywane, <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> zdarzenie jest zgłaszane w elemencie docelowym polecenia, który tunel i bąbelkowych za pośrednictwem drzewa elementów, takich jak inne dane wejściowe.  Jeśli nie ustawiono elementu docelowego polecenia, element z fokusem klawiatury będą elemencie docelowym polecenia.  Logiki, która wykonuje polecenie jest dołączony do <xref:System.Windows.Input.CommandBinding>.  Gdy <xref:System.Windows.Input.CommandManager.Executed> zdarzeń osiągnie <xref:System.Windows.Input.CommandBinding> dla określonego polecenia <xref:System.Windows.Input.ExecutedRoutedEventHandler> na <xref:System.Windows.Input.CommandBinding> jest wywoływana.  Ten program obsługi wykonuje akcję polecenia.

 Aby uzyskać więcej informacji na temat polecenia, zobacz [polecenia Przegląd](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera bibliotekę typowych poleceń, które składa się z <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, i <xref:System.Windows.Documents.EditingCommands>, lub Definiowanie swoich własnych.

 Poniższy przykład pokazuje, jak skonfigurować <xref:System.Windows.Controls.MenuItem> tak, aby po kliknięciu wywoła <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie <xref:System.Windows.Controls.TextBox>, przyjmuje <xref:System.Windows.Controls.TextBox> ma fokus klawiatury.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 Aby uzyskać więcej informacji na temat poleceń w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [polecenia Przegląd](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>System wejściowy i elementy bazy
 Dane wejściowe zdarzenia, takie jak dołączone zdarzenia, zdefiniowany przez <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, i <xref:System.Windows.Input.Stylus> klasy są wygenerowane przez system wejściowy i wprowadzonym w określonej pozycji w modelu obiektów, oparte na trafień testowania drzewa wizualnego w czasie wykonywania.

 Każda z tych zdarzeń, <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, i <xref:System.Windows.Input.Stylus> zdefiniować jako dołączone zdarzenie jest również ponownie narażona jest klasy bazowej elementów <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> jako nowe zdarzenia trasowanego. Zdarzenia elementu podstawowego kierowane są generowane przez klasy obsługi oryginalnego dołączone zdarzenie i ponowne użycie danych zdarzenia.

 Gdy dane wejściowe zdarzenia staje się skojarzone z elementem określonego źródła, za pomocą implementacji elementu podstawowego dane wejściowe zdarzenia, można go przekierować przez resztę trasy zdarzeń, która jest oparta na kombinacji obiektów drzewo logiczne i visual i być obsługiwane przez Kod aplikacji.  Ogólnie rzecz biorąc, jest bardziej wygodne do obsługi tych urządzeń zdarzeń związanych z danych wejściowych za pomocą zdarzeń trasowanych na <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement>, ponieważ umożliwia bardziej intuicyjne zdarzeń Składnia programu obsługi zarówno w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i w kodzie. Możesz wybrać do obsługi zdarzeń dołączonych, która zainicjowała zamiast tego procesu, ale będzie twarzy kilka problemów: dołączone zdarzenie może być oznaczony obsługiwane przez obsługę klasy elementu podstawowego, a następnie należy użyć metody dostępu, a nie wartość true, zdarzenie składni w kolejności Aby dołączyć programy obsługi dla zdarzenia dołączone.

<a name="whats_next"></a>
## <a name="whats-next"></a>Jaka jest przyszłość
 Masz teraz kilka technik do obsługi danych wejściowych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Należy przygotować także lepsze zrozumienie różnych typów zdarzeń wejściowych i mechanizmy zdarzenia trasowanego posługują się [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Dodatkowe zasoby są dostępne objaśniające [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów framework i routingu zdarzeń, bardziej szczegółowo. Omówienia następujących zagadnień, aby uzyskać więcej informacji, zobacz [polecenia Przegląd](commanding-overview.md), [Przegląd fokus](focus-overview.md), [Przegląd elementy bazy](base-elements-overview.md), [drzewa w WPF](trees-in-wpf.md), i [kierowane Przegląd zdarzeń](routed-events-overview.md).

## <a name="see-also"></a>Zobacz także

- [Przegląd fokusu](focus-overview.md)
- [Przegląd poleceń](commanding-overview.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Przegląd elementów podstawowych](base-elements-overview.md)
- [Właściwości](properties-wpf.md)
