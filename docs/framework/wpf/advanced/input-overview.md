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
ms.openlocfilehash: 77f69fb73d40c76257accc989d4a9a57ed992cf6
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207654"
---
# <a name="input-overview"></a>Przegląd Dane wejściowe
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Podsystemu udostępnia zaawansowane [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] uzyskiwania danych wejściowych z różnych urządzeń, w tym myszy, klawiatury, touch i pióra. W tym temacie opisano usług świadczonych przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i opisano architekturę wejściowych systemów.  
  
  
<a name="input_api"></a>   
## <a name="input-api"></a>Dane wejściowe interfejsu API  
 Podstawowe dane wejściowe [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] narażenia znajduje się w klasach base element: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>, i <xref:System.Windows.FrameworkContentElement>.  Aby uzyskać więcej informacji na temat podstawowych elementów, zobacz [podstawowej Omówienie elementów](../../../../docs/framework/wpf/advanced/base-elements-overview.md).  Te klasy zawierają funkcji związanych z naciśnięć klawiszy i przycisku myszy, kółka myszy, ruchów myszy, zarządzania fokus oraz przechwytywanie myszy kilka zdarzenia wejściowe. Po umieszczeniu danych wejściowych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na podstawowe elementy, zamiast traktowanie wszystkich zdarzeń wprowadzić jako usługa, wejściowych architektura umożliwia zdarzenia wejściowe, aby ustalić źródło przez określonego obiektu w interfejsie użytkownika, a do obsługi routingu schematu zdarzeń zgodnie z którymi więcej niż jednego element ma możliwość obsługi zdarzenia wejściowe. Wiele zdarzeń wejściowych ma para zdarzeń skojarzonych z nimi.  Na przykład jest skojarzony klucz zdarzenie naciśnięcia <xref:System.Windows.Input.Keyboard.KeyDown> i <xref:System.Windows.Input.Keyboard.PreviewKeyDown> zdarzenia.  Jest to różnica w tych zdarzeń w jaki sposób są kierowane do elementu docelowego.  Podgląd zdarzeń tunelu niżej na drzewie element z elementu głównego do elementu docelowego.  Propagacji zdarzenia bąbelków się od elementu docelowego do elementu głównego.  Zdarzenia routingu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] omówiono bardziej szczegółowo w dalszej części tego przeglądu i w [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
### <a name="keyboard-and-mouse-classes"></a>Klawiatura i mysz klas  
 Oprócz danych wejściowych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na klasy podstawowej elementu <xref:System.Windows.Input.Keyboard> klasy i <xref:System.Windows.Input.Mouse> klasy zapewnić dodatkowe [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] do pracy z klawiatury i myszy.  
  
 Przykłady danych wejściowych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na <xref:System.Windows.Input.Keyboard> klasy są <xref:System.Windows.Input.Keyboard.Modifiers%2A> właściwość, która zwraca <xref:System.Windows.Input.ModifierKeys> obecnie naciśnięty i <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> metodę, która określa, czy określony klucz jest wciśnięty.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> metodę, aby określić, czy <xref:System.Windows.Input.Key> jest w stanie down.  
  
 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]  
  
 Przykłady danych wejściowych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na <xref:System.Windows.Input.Mouse> klasy są <xref:System.Windows.Input.Mouse.MiddleButton%2A>, która uzyskuje stan środkowego przycisku myszy, i <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, pobiera elementu wskaźnik myszy znajduje się obecnie nad.  
  
 Poniższy przykład określa, czy <xref:System.Windows.Input.Mouse.LeftButton%2A> w wskaźnik myszy znajduje się w <xref:System.Windows.Input.MouseButtonState.Pressed> stanu.  
  
 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]  
  
 <xref:System.Windows.Input.Mouse> i <xref:System.Windows.Input.Keyboard> klasy są opisane bardziej szczegółowo w tym omówieniu.  
  
### <a name="stylus-input"></a>Wprowadzania danych piórem  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma zintegrowanej obsłudze <xref:System.Windows.Input.Stylus>.  <xref:System.Windows.Input.Stylus> Jest piórem, wprowadzone popularnych przez [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje można traktować pióro jako myszy za pomocą myszy [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], ale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia również pióro abstrakcji urządzenia, które korzystają z modelu, które są podobne do klawiatury i myszy.  Wszystkie powiązane pióro [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] zawiera wyrazu "Pióro".  
  
 Ponieważ pióro może działać jako myszy, aplikacje, które obsługują tylko myszą można wciąż uzyskać pewnego poziomu wsparcia pióro automatycznie. Gdy pióro jest używany w taki sposób, aplikacja ma możliwość obsługi zdarzenia odpowiednie pióro i obsługuje odpowiednie zdarzenie myszy. Ponadto wyższego poziomu usług, takich jak odręczne są również dostępne za pośrednictwem abstrakcji urządzenia pióra.  Aby uzyskać więcej informacji na temat jako dane wejściowe, zobacz [wprowadzenie odręczne](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).  
  
<a name="event_routing"></a>   
## <a name="event-routing"></a>Routing zdarzeń  
 A <xref:System.Windows.FrameworkElement> może zawierać inne elementy jako elementy podrzędne w modelu zawartości, stanowiące drzewa elementów.  W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], element nadrzędny mogą uczestniczyć w danych wejściowych skierowany do jego elementy podrzędne lub innych elementów podrzędnych przez przekazywanie zdarzeń. Jest to szczególnie przydatne w przypadku tworzenia formantów poza mniejszych formanty procesu nazywanego "kontroli kompozycji" lub "składania". Aby uzyskać więcej informacji na temat element drzewa i jak element drzewa dotyczą trasy zdarzenia, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
 Zdarzenia routing jest proces przesyłania zdarzeń do wielu elementów, dzięki czemu określonego obiektu lub element marszruty możliwość oferuje znaczne odpowiedzi (za pośrednictwem obsługę) na zdarzenie, które mogą mieć zostały kwerendą źródłową inny element.  Kierowane zdarzenia, użyj jednej z trzech mechanizmów routingu: bezpośrednie, propagacji i tunelowania.  W routingu bezpośredniego elementu źródła jest jedynym elementem powiadomiony i zdarzenie nie jest kierowany do innych elementów. Jednak bezpośredniego kierowanego zdarzenia nadal ma pewne dodatkowe możliwości, które występują tylko dla kierowane zdarzenia w przeciwieństwie do standardowego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenia. Propagacji działa w górę drzewa elementu przez pierwszy powiadomienie element, który następnie powierzając jej ich konserwację zdarzenia, elementu nadrzędnego i tak dalej.  Tunelowanie rozpoczyna się od katalogu głównego drzewa elementu i działa, kończąc oryginalny element źródła.  Aby uzyskać więcej informacji na temat kierowane zdarzenia, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia wejściowe są zazwyczaj dostępne w parach, które składa się z tunelowania zdarzeń i zdarzeń propagacji.  Tunelowania zdarzenia są odróżniane ze zdarzeń propagacji z prefiksem "W wersji zapoznawczej".  Na przykład <xref:System.Windows.Input.Mouse.PreviewMouseMove> jest wersja tunelowania zdarzenie przesunięcia kursora myszy i <xref:System.Windows.Input.Mouse.MouseMove> jest propagacji wersji tego zdarzenia. To zdarzenie parowanie jest Konwencji jest zaimplementowana na poziomie elementu, który nie jest możliwość dostępu do właściwych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń systemu. Aby uzyskać więcej informacji, zobacz sekcję zdarzeń wprowadzania WPF w [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="handling_input_events"></a>   
## <a name="handling-input-events"></a>Obsługa zdarzeń wejściowych  
 Dla danych wejściowych w elemencie, program obsługi zdarzeń musi być skojarzony z danego zdarzenia.  W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest bezpośrednie: odwoływać się do nazwy zdarzenia jako atrybut elementu nasłuchiwania dla tego zdarzenia.  Następnie należy ustawić wartość atrybutu nazwę zdefiniowanego, na podstawie obiektu delegowanego obsługi zdarzeń.  Program obsługi zdarzeń musi być napisana w kodzie, takich jak C# i może być uwzględniony w pliku CodeBehind.  
  
 Zdarzenia klawiatury występują, gdy system operacyjny zgłasza klucza akcje, które są wykonywane, gdy fokus klawiatury znajduje się na element. Myszy i Pióro zdarzenia każdego można podzielić na dwie kategorie: zdarzenia, które zmienia raportu w pozycję wskaźnika względem elementu i zdarzenia, których raport zmienia się w stanie przycisków urządzenia.  
  
### <a name="keyboard-input-event-example"></a>Przykład wejściowych zdarzenia klawiatury  
 Poniższy przykład nasłuchuje naciśnięcie klawisza Strzałka w lewo.  A <xref:System.Windows.Controls.StackPanel> jest tworzony, który ma <xref:System.Windows.Controls.Button>.  Program obsługi zdarzeń do nasłuchiwania na naciśnięcie klawisza Strzałka w lewo jest dołączony do <xref:System.Windows.Controls.Button> wystąpienia.  
  
 Tworzy w pierwszej sekcji przykładu <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.Button> i dołącza program obsługi zdarzeń dla <xref:System.Windows.UIElement.KeyDown>.  
  
 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]  
  
 Druga sekcja jest zapisywane w kodzie i definiuje programu obsługi zdarzeń.  Po naciśnięciu klawisza Strzałka w lewo i <xref:System.Windows.Controls.Button> ma fokus klawiatury, uruchamia program obsługi i <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> zostanie zmieniona.  Jeśli przycisk jest naciśnięty, ale nie jest klawisz strzałki w lewo <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> zmieniony na jego kolor początkowy.  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]  
  
### <a name="mouse-input-event-example"></a>Przykład zdarzenie wejściowe myszy  
 W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> jest zmieniany, gdy wskaźnik myszy zostanie umieszczony <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.Control.Background%2A> Kolor jest przywracany, gdy mysz opuści <xref:System.Windows.Controls.Button>.  
  
 Tworzy w pierwszej sekcji przykładu <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.Button> kontroli i dołącza obsługi zdarzeń <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> zdarzenia <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]  
  
 Druga sekcja przykładzie są zapisywane w kodzie i definiuje obsługi zdarzeń.  Gdy wskaźnik myszy zostanie przesunięty <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> jest zmieniana na <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Gdy mysz opuści <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.Controls.Button> zmieniony na <xref:System.Windows.Media.Brushes.AliceBlue%2A>.  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]  
  
<a name="text_input"></a>   
## <a name="text-input"></a>Wprowadzanie tekstu  
 <xref:System.Windows.ContentElement.TextInput> Zdarzenie pozwala na wprowadzanie tekstu nasłuchiwanie w sposób niezależny od urządzenia. Klawiatura jest podstawowym elementem używanym pisma ręcznego wprowadzania, ale mowy, tekst i inne urządzenia wejściowe może generować również pola tekstowego.  
  
 Dla danych wprowadzonych z klawiatury [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] najpierw wysyła odpowiednie <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> zdarzenia. Jeśli te zdarzenia nie są obsługiwane, jak klucz tekstową zamiast (klucz kontroli takich jak strzałki kierunkowej) lub klawiszy funkcyjnych, a następnie <xref:System.Windows.ContentElement.TextInput> zdarzenia.  Nie ma zawsze proste mapowanie jeden do jednego między <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> i <xref:System.Windows.ContentElement.TextInput> zdarzeń, ponieważ wiele naciśnięcia klawiszy można wygenerować pojedynczego znaku wprowadzanie tekstu i jednym naciśnięcia klawiszy może generować wielu znaków ciągi.  Jest to szczególnie istotne dla języków, takich jak chińskich, japońskich i koreańskich, które używają [!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)] do generowania wielu znaków w ich odpowiednich małych liter.  
  
 Gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wysyła <xref:System.Windows.ContentElement.KeyUp> / <xref:System.Windows.ContentElement.KeyDown> zdarzenia <xref:System.Windows.Input.KeyEventArgs.Key%2A> ma ustawioną wartość <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> Jeśli naciśnięcia klawiszy może stać się częścią <xref:System.Windows.ContentElement.TextInput> zdarzenia (jeśli ALT + S zostanie naciśnięty, na przykład). Dzięki temu kod w <xref:System.Windows.ContentElement.KeyDown> obsługi zdarzeń, aby wyszukać <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> oraz, jeśli znaleziono, pozostaw przetwarzania dla obsługi następnie zgłoszono <xref:System.Windows.ContentElement.TextInput> zdarzeń. W tych przypadkach różne właściwości <xref:System.Windows.Input.TextCompositionEventArgs> argument może służyć do określenia oryginalnego naciśnięcia klawiszy. Podobnie jeśli [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] jest aktywny, <xref:System.Windows.Input.Key> ma wartość <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>, i <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> daje oryginalnego naciśnięcie klawisza lub naciśnięcia klawisza.  
  
 W poniższym przykładzie zdefiniowano program obsługi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń i obsługi dla <xref:System.Windows.UIElement.KeyDown> zdarzeń.  
  
 Pierwszy segment kodu lub znacznika tworzy interfejs użytkownika.  
  
 [!code-xaml[InputOvw#Input_OvwTextInputXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]  
  
 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]  
  
 Drugi segment kodu zawiera obsługi zdarzeń.  
  
 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]  
  
 Ponieważ zdarzenia wejściowe bąbelkowy zapasowej trasy zdarzenia <xref:System.Windows.Controls.StackPanel> odbiera dane wejściowe, niezależnie od tego, który element ma fokus klawiatury. <xref:System.Windows.Controls.TextBox> Formantu zostanie powiadomiony najpierw i `OnTextInputKeyDown` obsługi jest wywoływana tylko wtedy, gdy <xref:System.Windows.Controls.TextBox> nie obsłużył danych wejściowych. Jeśli <xref:System.Windows.UIElement.PreviewKeyDown> zdarzenia jest używany zamiast <xref:System.Windows.UIElement.KeyDown> zdarzenia `OnTextInputKeyDown` obsługi nazywa się najpierw.  
  
 W tym przykładzie logiki obsługi napisano dwa razy — raz dla CTRL + O, a następnie dla przycisku kliknij zdarzenie. Może to uproszczona, za pomocą poleceń, zamiast bezpośrednio obsługi zdarzenia wejściowe.  Polecenia zostały omówione w tym omówieniu, a w [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="touch_and_manipulation"></a>   
## <a name="touch-and-manipulation"></a>Manipulowanie i dotykiem  
 Nowy sprzęt i interfejsu API w systemie operacyjnym Windows 7 umożliwiają aplikacji na odbieranie danych wejściowych z wielu poprawek jednocześnie. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia aplikacjom wykrywanie i reagowanie na touch w sposób podobny do reagowania na innych danych wejściowych, takich jak mysz lub klawiatura, przez wywoływanie zdarzeń po wystąpieniu touch.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia dwa typy zdarzeń, gdy wystąpi touch: touch zdarzenia i manipulowania nimi. Zdarzenia Touch udostępniają nieprzetworzone dane dotyczące poszczególnych palca na ekran dotykowy i jego ruchu. Manipulowanie zdarzenia interpretowanie danych wejściowych jako pewne akcje. W tej sekcji omówiono obu typów zdarzeń.  
  
### <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki umożliwiające tworzenie aplikacji, która odpowiada touch.  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7.  
  
-   Urządzenie, takie jak ekran dotykowy, który obsługuje Touch z systemem Windows.  
  
### <a name="terminology"></a>Terminologia  
 Poniższe terminy są używane, gdy omówiono touch.  
  
-   **Touch** jest typem danych wejściowych użytkownika, który jest rozpoznawany przez system Windows 7. Zazwyczaj touch jest inicjowane przez umieszczenie na ekranie dotykowe palców. Należy pamiętać, że urządzeń, takich jak dotykową, który często na komputerach przenośnych nie obsługują touch, jeśli urządzenie jedynie konwertuje pozycji i przepływu jako wejście myszy palca.  
  
-   **Multitouch** jest touch, która występuje z więcej niż jeden punkt jednocześnie. Windows 7 i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje multitouch. Po każdej zmianie touch opisanej w dokumentacji dotyczącej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], pojęć dotyczą multitouch.  
  
-   A **manipulowania** występuje, gdy touch jest interpretowana jako fizyczny akcję, która jest stosowana do obiektu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], manipulowanie zdarzenia interpretowanie danych wejściowych jako manipulowania tłumaczenia, rozszerzenia lub obrotu.  
  
-   A `touch device` reprezentuje urządzenie, które tworzy dotykowym, takich jak pojedynczy palca na ekran dotykowy.  
  
### <a name="controls-that-respond-to-touch"></a>Formanty, które odpowiadają na Touch  
 Następujące formanty może być przewijane przeciągając palcem przez formant, jeśli ma ona zawartość, która jest przewijane niewidocznymi.  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.DataGrid>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
 <xref:System.Windows.Controls.ScrollViewer> Definiuje <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> dołączona właściwość, która umożliwia określenie, czy przesuwanie dotykowe jest włączona w poziomie, w pionie, zarówno lub nie. <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> Właściwość określa, jak szybko przewijania wolniej, gdy użytkownik podnosi palca z ekran dotykowy. <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> Dołączona właściwość określa stosunek przewijanie przesunięcie tłumaczenie przesunięcie manipulowanie.  
  
### <a name="touch-events"></a>Touch zdarzenia  
 Klasy podstawowe <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>, i <xref:System.Windows.ContentElement>, zdefiniuj zdarzenia, które mogą subskrybować, aplikacja będzie odpowiadać touch. Touch zdarzenia są przydatne, gdy aplikacja interpretuje touch jako manipulowanie obiektu. Na przykład aplikacja, która umożliwia użytkownikowi Rysowanie za pomocą jednego lub więcej palców czy subskrybować touch zdarzenia.  
  
 Wszystkie trzy klasy definiują następujące zdarzenia, które zachowują się podobnie, niezależnie od klasy definiującej.  
  
-   <xref:System.Windows.UIElement.TouchDown>  
  
-   <xref:System.Windows.UIElement.TouchMove>  
  
-   <xref:System.Windows.UIElement.TouchUp>  
  
-   <xref:System.Windows.UIElement.TouchEnter>  
  
-   <xref:System.Windows.UIElement.TouchLeave>  
  
-   <xref:System.Windows.UIElement.PreviewTouchDown>  
  
-   <xref:System.Windows.UIElement.PreviewTouchMove>  
  
-   <xref:System.Windows.UIElement.PreviewTouchUp>  
  
-   <xref:System.Windows.UIElement.GotTouchCapture>  
  
-   <xref:System.Windows.UIElement.LostTouchCapture>  
  
 Podobnie jak zdarzenia klawiatury i myszy zdarzenia touch są kierowane zdarzenia. Zdarzenia, które zaczynają się od `Preview` są tunelowania zdarzeń i zdarzenia, które zaczynają się od `Touch` zdarzeń propagacji. Aby uzyskać więcej informacji na temat kierowane zdarzenia, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md). Podczas obsługi tych zdarzeń, pozycja danych wejściowych, względem dowolnego elementu można uzyskać przez wywołanie metody <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> lub <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> metody.  
  
 Aby poznać interakcji między zdarzenia touch, Rozważmy scenariusz, gdy użytkownik umieszcza jeden palca w elemencie, przenosi palca w elemencie i następnie wind palca z elementu. Na poniższej ilustracji przedstawiono wykonanie propagacji zdarzenia (tunelowania zdarzeń zostały pominięte dla uproszczenia).  
  
 ![Kolejność zdarzeń touch. ] (../../../../docs/framework/wpf/advanced/media/ndp-touchevents.png "NDP_TouchEvents")  
Touch zdarzenia  
  
 Poniższa lista zawiera opis sekwencji zdarzeń na powyższej ilustracji.  
  
1.  <xref:System.Windows.UIElement.TouchEnter> Zdarzeń występuje jeden raz, gdy użytkownik umieszcza palcem w elemencie.  
  
2.  <xref:System.Windows.UIElement.TouchDown> Zdarzenie wystąpi jeden raz.  
  
3.  <xref:System.Windows.UIElement.TouchMove> Zdarzeń występuje wiele razy, gdy użytkownik przechodzi palca w elemencie.  
  
4.  <xref:System.Windows.UIElement.TouchUp> Zdarzenie wystąpi jeden raz, gdy użytkownik podnosi palca z elementu.  
  
5.  <xref:System.Windows.UIElement.TouchLeave> Zdarzenie wystąpi jeden raz.  
  
 W przypadku używania więcej niż dwoma palcami występowania zdarzeń, dla każdej linii papilarnych.  
  
### <a name="manipulation-events"></a>Manipulowanie zdarzenia  
 W przypadkach, gdy aplikacja umożliwia użytkownikowi modyfikowania obiektu <xref:System.Windows.UIElement> klasa definiuje zdarzenia manipulowanie. W przeciwieństwie do zdarzeń touch, które po prostu raport pozycja touch zdarzenia manipulowania raport interpretacji danych wejściowych. Istnieją trzy typy manipulacje, tłumaczenia, rozszerzenia i obrotu. Poniższa lista zawiera opis sposobu wywołania trzy rodzaje manipulacji.  
  
-   Umieść palcem obiektu i Przenieś palca przez ekran dotykowy do manipulowania tłumaczenia wywołania. Przenosi to zazwyczaj obiekt.  
  
-   Umieszcza dwoma palcami obiektu i Przenieś palcami razem lub je niezależnie od siebie, aby wywołać manipulowania rozszerzenia. Zmienia to zwykle rozmiar obiektu.  
  
-   Umieść dwoma palcami obiektu i obracania palcami wokół wzajemnie do wywołania manipulowania obrotu. To zwykle obraca obiekt.  
  
 Jednocześnie może występować więcej niż jeden typ manipulacji.  
  
 Gdy powoduje, że obiekty odpowiedzieć na manipulacje, może mieć obiektu ma bezwładności. Ułatwia to symulować świecie obiektów. Na przykład po naciśnięciu książkę w tabeli, jeśli wypychanych twarde wystarczająco książki będzie można przenieść po zwolnieniu go. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można symulować to zachowanie przez wywoływanie zdarzeń manipulowania po palców użytkownika zwalnia obiekt.  
  
 Aby uzyskać informacje o sposobie tworzenia aplikacji, która umożliwia użytkownikowi przenoszenie, zmienianie rozmiaru i obrót obiektu, zobacz [wskazówki: tworzenie swój pierwszy Touch aplikacji](../../../../docs/framework/wpf/advanced/walkthrough-creating-your-first-touch-application.md).  
  
 <xref:System.Windows.UIElement> Definiuje następujące zdarzenia manipulowanie.  
  
-   <xref:System.Windows.UIElement.ManipulationStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationStarted>  
  
-   <xref:System.Windows.UIElement.ManipulationDelta>  
  
-   <xref:System.Windows.UIElement.ManipulationInertiaStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationCompleted>  
  
-   <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>  
  
 Domyślnie <xref:System.Windows.UIElement> nie trafiać te zdarzenia manipulowanie. Aby odbierać zdarzenia manipulowania na <xref:System.Windows.UIElement>ustaw <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> do `true`.  
  
#### <a name="the-execution-path-of-manipulation-events"></a>Ścieżka wykonywania manipulowania zdarzeń  
 Rozważmy scenariusz, w którym użytkownik "zgłasza" obiektu. Przełączy palcem w obiekcie przenosi palca przez ekran dotykowy odległość krótki, a następnie wind palca podczas przesuwania. Wynik jest obiekt zostanie Przenieś palca użytkownika oraz przenoszenia po użytkownika wind palca w dalszym ciągu.  
  
 Na poniższej ilustracji przedstawiono ścieżka wykonywania zdarzeń manipulacji i ważnych informacji dotyczących każdego zdarzenia.  
  
 ![Kolejność zdarzeń manipulowanie. ] (../../../../docs/framework/wpf/advanced/media/ndp-manipulationevents.png "NDP_ManipulationEvents")  
Manipulowanie zdarzenia  
  
 Poniższa lista zawiera opis sekwencji zdarzeń na powyższej ilustracji.  
  
1.  <xref:System.Windows.UIElement.ManipulationStarting> Zdarzenie wystąpi, gdy użytkownik umieszcza palcem obiektu. Między innymi, to zdarzenie umożliwia ustawienie <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> właściwości. W następnych zdarzeniach pozycja operowanie będzie względem <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. W zdarzeniach w innych niż <xref:System.Windows.UIElement.ManipulationStarting>, ta właściwość jest tylko do odczytu, więc <xref:System.Windows.UIElement.ManipulationStarting> zdarzenie jest tylko wtedy, które można ustawić tej właściwości.  
  
2.  <xref:System.Windows.UIElement.ManipulationStarted> Następne wystąpienie zdarzenia. To zdarzenie raporty pochodzenia operowanie.  
  
3.  <xref:System.Windows.UIElement.ManipulationDelta> Zdarzeń występuje wiele razy, ile przenoszenia palców użytkownika na ekran dotykowy. <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> Właściwość <xref:System.Windows.Input.ManipulationDeltaEventArgs> klasy raporty, czy operowanie jest interpretowana jako ruchu, rozszerzenia lub tłumaczenia. Jest to, gdzie wykonać większość pracy manipulowania obiektu.  
  
4.  <xref:System.Windows.UIElement.ManipulationInertiaStarting> Zdarzenie wystąpi, gdy palców użytkownika traci kontaktu z obiektem. To zdarzenie umożliwia określenie prędkości manipulacji podczas bezwładności. Jest to tak obiektu może emulować różnych fizycznych spacji ani atrybutów, wybranie opcji. Na przykład, załóżmy, że aplikacja ma dwa obiekty reprezentujące elementów w świecie rzeczywistym, a drugi większych niż drugi. Możesz wprowadzić obiekt większych zwalnia szybciej niż jaśniejszy obiekt.  
  
5.  <xref:System.Windows.UIElement.ManipulationDelta> Zdarzeń występuje wiele razy, po wystąpieniu bezwładności. Należy pamiętać, że to zdarzenie występuje podczas palców użytkownika porusza się na ekran dotykowy i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] symuluje bezwładności. Innymi słowy <xref:System.Windows.UIElement.ManipulationDelta> występuje przed i po <xref:System.Windows.UIElement.ManipulationInertiaStarting> zdarzeń. <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> Raportów właściwości czy <xref:System.Windows.UIElement.ManipulationDelta> zdarzeń występuje w ciągu bezwładności, aby można było sprawdzić tej właściwości i wykonywania różnych akcji, w zależności od jego wartości.  
  
6.  <xref:System.Windows.UIElement.ManipulationCompleted> Zdarzenie występuje, gdy kończy się manipulacji i bezwładności wszystkie. Oznacza to, że po wszystkich <xref:System.Windows.UIElement.ManipulationDelta> zdarzenia występują, <xref:System.Windows.UIElement.ManipulationCompleted> wystąpienia zdarzenia, która sygnalizuje, że operowanie została zakończona.  
  
 <xref:System.Windows.UIElement> Definiuje również <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> zdarzeń. To zdarzenie występuje, gdy <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> metoda jest wywoływana <xref:System.Windows.UIElement.ManipulationDelta> zdarzeń. <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> Zdarzeń umożliwia aplikacji lub składniki w celu zapewnienia wizualne, gdy obiekt trafi granicy. Na przykład <xref:System.Windows.Window> klasy uchwytów <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> zdarzenie, aby spowodować, że okno, aby przenieść nieco po napotkaniu jego krawędzi.  
  
 Operowanie można anulować, wywołując <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> metody dla argumentów zdarzenia w każdym przypadku manipulowania, z wyjątkiem <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> zdarzeń. Podczas wywoływania <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, nie są generowane zdarzenia manipulacji i zdarzenia myszy występują dla touch. W poniższej tabeli opisano relacji między czasem operowanie zostanie anulowane i zdarzeń myszy.  
  
|Zdarzenia, które jest wywoływany Anuluj|Zdarzenia myszy występujących na dane wejściowe, który już wystąpił|  
|----------------------------------------|-----------------------------------------------------------------|  
|<xref:System.Windows.UIElement.ManipulationStarting> I <xref:System.Windows.UIElement.ManipulationStarted>|Wskaźnik myszy w dół zdarzenia.|  
|<xref:System.Windows.UIElement.ManipulationDelta>|Zdarzenia przenoszenia myszy i naciśnięcia przycisku myszy.|  
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> I <xref:System.Windows.UIElement.ManipulationCompleted>|Wskaźnik myszy w dół, przenieś wskaźnik myszy i mysz zdarzeń.|  
  
 Należy pamiętać, że jeśli wywołujesz <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> kiedy operowanie bezwładności, metoda zwraca `false` i dane wejściowe nie wygenerował zdarzeń myszy.  
  
### <a name="the-relationship-between-touch-and-manipulation-events"></a>Relacja między Touch i manipulowania zdarzenia  
 A <xref:System.Windows.UIElement> zawsze może odbierać zdarzenia touch. Gdy <xref:System.Windows.UIElement.IsManipulationEnabled%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.UIElement> może odbierać zdarzenia manipulacji i dotykiem.  Jeśli <xref:System.Windows.UIElement.TouchDown> zdarzenie nie jest obsługiwane (oznacza to, <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość jest `false`), logikę manipulowania przechwytuje touch do elementu i generuje zdarzenia manipulowanie. Jeśli <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość jest ustawiona na `true` w <xref:System.Windows.UIElement.TouchDown> zdarzenia logiki manipulowanie nie generuje manipulowania zdarzenia. Na poniższej ilustracji przedstawiono relację między touch zdarzenia i manipulowania nimi.  
  
 ![Relacja między zdarzeniami touch i manipulowania nimi](../../../../docs/framework/wpf/advanced/media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents")  
Touch i manipulowania nimi zdarzenia  
  
 Poniższa lista zawiera opis relacji między zdarzeniami touch i manipulowania nimi, które jest wyświetlane na powyższej ilustracji.  
  
-   Po pierwsze urządzenie touch generuje <xref:System.Windows.UIElement.TouchDown> zdarzenia w <xref:System.Windows.UIElement>, wywołania logiki manipulowania <xref:System.Windows.UIElement.CaptureTouch%2A> metodę, która generuje <xref:System.Windows.UIElement.GotTouchCapture> zdarzeń.  
  
-   Gdy <xref:System.Windows.UIElement.GotTouchCapture> występuje wywołania logiki manipulowania <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> metodę, która generuje <xref:System.Windows.UIElement.ManipulationStarting> zdarzeń.  
  
-   Gdy <xref:System.Windows.UIElement.TouchMove> zdarzenia występują, generuje logiki manipulowania <xref:System.Windows.UIElement.ManipulationDelta> zdarzenia występujące przed <xref:System.Windows.UIElement.ManipulationInertiaStarting> zdarzeń.  
  
-   Podczas ostatniego touch urządzenia element zgłasza <xref:System.Windows.UIElement.TouchUp> generuje logiki manipulowania zdarzenia <xref:System.Windows.UIElement.ManipulationInertiaStarting> zdarzeń.  
  
<a name="focus"></a>   
## <a name="focus"></a>Fokus  
 Istnieją dwa główne pojęcia, które odnoszą się do fokusu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: Klawiatura fokus i logiczny fokus.  
  
### <a name="keyboard-focus"></a>Fokus klawiatury  
 Fokus klawiatury odwołuje się do elementu, który otrzymuje klawiatury.  Może istnieć tylko jeden element na całej pulpitu, który ma fokus klawiatury.  W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ma element, który ma fokus klawiatury <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> ustawioną `true`.  Statycznych <xref:System.Windows.Input.Keyboard> metoda <xref:System.Windows.Input.Keyboard.FocusedElement%2A> zwraca element, który aktualnie ma fokus klawiatury.  
  
 Fokus klawiatury można uzyskać, przechodząc do elementu lub przez kliknięcie przycisku myszy w przypadku niektórych elementów, takich jak <xref:System.Windows.Controls.TextBox>.  Fokus klawiatury również można uzyskać programistycznie przy użyciu <xref:System.Windows.Input.Keyboard.Focus%2A> metoda <xref:System.Windows.Input.Keyboard> klasy.  <xref:System.Windows.Input.Keyboard.Focus%2A> podejmuje próbę przekazania fokus klawiatury określonego elementu.  Zwrócony przez element <xref:System.Windows.Input.Keyboard.Focus%2A> jest element, który aktualnie ma fokus klawiatury.  
  
 Aby element, aby uzyskać fokus klawiatury <xref:System.Windows.UIElement.Focusable%2A> właściwości i <xref:System.Windows.UIElement.IsVisible%2A> musi mieć wartość właściwości **true**.  Niektóre klasy, takich jak <xref:System.Windows.Controls.Panel>, ma <xref:System.Windows.UIElement.Focusable%2A> ustawioną `false` domyślnie; w związku z tym należy ustawić tę właściwość na `true` Jeśli chcesz, aby ten element, aby można było uzyskać fokusu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Input.Keyboard.Focus%2A> można ustawić fokus klawiatury dla <xref:System.Windows.Controls.Button>.  Zalecane miejsce, aby ustawić początkowy fokus w aplikacji znajduje się <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 Aby uzyskać więcej informacji na temat fokus klawiatury, zobacz [omówienie fokus](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
### <a name="logical-focus"></a>Logiczny fokus  
 Logiczny fokus odwołuje się do <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> w zakresie fokus.  Może istnieć wiele elementów, które ma logiczny fokus w aplikacji, ale może istnieć tylko jeden element, który ma logiczny fokus w zakresie określonego zespołu.  
  
 Zakres fokus jest elementem kontenera, który śledzi <xref:System.Windows.Input.FocusManager.FocusedElement%2A> w jego zakresie.  Gdy zakres fokus utraci fokus, ukierunkowanych elementu utraci fokus klawiatury, ale zachowa logiczny fokus.  Gdy nastąpi powrót do zakresu fokus, element ukierunkowanych uzyska fokus klawiatury.  Dzięki temu dla fokus klawiatury zostanie zmieniony między wiele zakresów fokus, ale temu, że element skupiają się w zakresie fokus nastąpi powrót, pozostanie elementem mającym fokus.  
  
 Element można zmienić zakresu fokusu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przez ustawienie <xref:System.Windows.Input.FocusManager> dołączona właściwość <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> do `true`, lub w kodzie przez ustawienie właściwości dołączonych za pomocą <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> — metoda.  
  
 Poniższy przykład powoduje, że <xref:System.Windows.Controls.StackPanel> w zakresie fokus, ustawiając <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> dołączona właściwość.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 Klasy w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , które są zakresów fokus domyślnie są <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, i <xref:System.Windows.Controls.ContextMenu>.  
  
 Element, który ma fokus klawiatury będą także mieć logiczny fokus dla zakresu fokus, do której należy; w związku z tym Ustawianie fokusu na elemencie z <xref:System.Windows.Input.Keyboard.Focus%2A> metoda <xref:System.Windows.Input.Keyboard> klasy lub klas base element podejmie próbę zapewnią fokus klawiatury element logiczny fokus.  
  
 Aby określić konkretną elementu w zakresie fokus, użyj <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Aby zmienić element ukierunkowanych zakresie fokus, użyj <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.  
  
 Aby uzyskać więcej informacji na temat logiczny fokus, zobacz [omówienie fokus](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
<a name="mouse_position"></a>   
## <a name="mouse-position"></a>Położenie myszy  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Wejściowych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] zawiera przydatne informacje dotyczące przestrzeni współrzędnych.  Na przykład koordynować `(0,0)` Współrzędna lewej górnej, ale lewej górnej które elementu w drzewie? Element, który jest elementem docelowym wejściowych? Element dołączone do procedury obsługi zdarzenia? Czy coś innego? Aby uniknąć pomyłek, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wejściowych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] wymaga określenia sieci układ odniesienia podczas pracy z współrzędne uzyskany za pomocą myszy. <xref:System.Windows.Input.Mouse.GetPosition%2A> Metoda zwraca współrzędnych wskaźnika myszy względem określonego elementu.  
  
<a name="mouse_capture"></a>   
## <a name="mouse-capture"></a>Przechwytywanie myszy  
 Myszy przytrzymaj specjalnie modalne cech, znany jako przechwytywanie myszy. Przechwytywanie myszy służy do obsługi przejściowe stanu danych wejściowych po uruchomieniu operacji przeciągania i upuszczania, dzięki czemu inne operacje na ekranie obejmujące nominalna położenia wskaźnika myszy nie zawsze występują. Podczas przeciągania użytkownik nie może kliknąć bez przerywania przeciągania i upuszczania, dzięki czemu większość wskaźników etykietka wskaźnika myszy nieodpowiednie podczas przechwytywania myszy jest trzymana przez element źródłowy przeciągania. Przedstawia system wejściowy [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] określające stanu przechwytywanie myszy, a także [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] który wymusić przechwytywanie myszy konkretnego elementu, lub Wyczyść stan przechwytywanie myszy. Aby uzyskać więcej informacji dotyczących operacji przeciągania i upuszczania, zobacz [przeciągania i upuszczania omówienie](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md).  
  
<a name="commands"></a>   
## <a name="commands"></a>Polecenia  
 Polecenia włączenia obsługi danych wejściowych na poziomie semantycznego więcej niż dane wejściowe urządzenia.  Polecenia są proste dyrektywy `Cut`, `Copy`, `Paste`, lub `Open`.  Polecenia są przydatne w przypadku scentralizowany logiki polecenia.  Tego samego polecenia mogą być używane z <xref:System.Windows.Controls.Menu>na <xref:System.Windows.Controls.ToolBar>, lub za pomocą skrótów klawiaturowych. Polecenia udostępniają mechanizm wyłączenie formantów, gdy polecenie staje się niedostępny.  
  
 <xref:System.Windows.Input.RoutedCommand> jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacja <xref:System.Windows.Input.ICommand>.  Gdy <xref:System.Windows.Input.RoutedCommand> jest wykonywane, <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> zdarzenie jest zgłaszane w elemencie docelowym polecenia, które tunelu i bąbelków za pośrednictwem elementu drzewa, takich jak innych danych wejściowych.  Jeśli element docelowy polecenia nie jest ustawiona, element z fokusem klawiatury będzie elemencie docelowym polecenia.  Logika, który wykonuje polecenie jest dołączony do <xref:System.Windows.Input.CommandBinding>.  Gdy <xref:System.Windows.Input.CommandManager.Executed> zdarzeń osiągnie <xref:System.Windows.Input.CommandBinding> dla określonego polecenia <xref:System.Windows.Input.ExecutedRoutedEventHandler> na <xref:System.Windows.Input.CommandBinding> jest wywoływana.  Ten program obsługi wykonuje akcję polecenia.  
  
 Aby uzyskać więcej informacji na wydawanie poleceń, zobacz [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia bibliotekę używanych poleceń, które składa się z <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, i <xref:System.Windows.Documents.EditingCommands>, lub można definiować własnych.  
  
 Poniższy przykład przedstawia sposób konfigurowania <xref:System.Windows.Controls.MenuItem> tak, aby po kliknięciu wywoła <xref:System.Windows.Input.ApplicationCommands.Paste%2A> na <xref:System.Windows.Controls.TextBox>, przyjmuje <xref:System.Windows.Controls.TextBox> ma fokus klawiatury.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
 Aby uzyskać więcej informacji dotyczących poleceń w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="the_input_system_and_base_elements"></a>   
## <a name="the-input-system-and-base-elements"></a>System wejściowy i elementy podstawowe  
 Dane wejściowe zdarzenia, takie jak dołączone zdarzenia zdefiniowane przez <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, i <xref:System.Windows.Input.Stylus> klasy są wywoływane przez system wejściowy i wprowadzonym w określonej pozycji w modelu obiektów oparte na trafień testowania drzewa wizualnego w czasie wykonywania.  
  
 Każdego zdarzenia który <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, i <xref:System.Windows.Input.Stylus> Definiuj dołączone zdarzenie ponownie jest również udostępniany przez klasy podstawowej elementu <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> jako nowe kierowanego zdarzenia. Element base kierowane zdarzenia są generowane przez klasy Obsługa oryginalnego dołączone zdarzenie i ponowne użycie danych zdarzenia.  
  
 Gdy zdarzenie wejściowe staje się skojarzony z elementem określonego źródła, za pośrednictwem jej implementacja zdarzenia wejściowego podstawowego elementu, można go przekierować przez pozostałej części trasy zdarzenia, który jest oparty na kombinacji obiektów drzewa logicznego i visual i będą obsługiwane przez Kod aplikacji.  Ogólnie rzecz biorąc, jest wygodniejsze do obsługi tych związanych z urządzeniami zdarzeń wejściowych przy użyciu kierowane zdarzenia na <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement>, ponieważ można bardziej intuicyjne zdarzeń Składnia programu obsługi zarówno w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i w kodzie. Można wybrać do obsługi dołączone zdarzenie, który zainicjował zamiast tego procesu, ale będą występować problemy kilka: dołączone zdarzenie może być oznaczony obsługiwane przez Obsługa klasa elementu base i należy użyć metody dostępu, a nie wartość true, zdarzenie składni w kolejności Aby dołączyć obsługi dołączone zdarzenia.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Co to jest dalej  
 Masz teraz kilka technik w celu obsługi danych wejściowych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Należy również mieć lepsze zrozumienie różnych typów zdarzeń wejściowych oraz używanych przez mechanizmy kierowanego zdarzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Dostępne są dodatkowe zasoby objaśniające [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy framework i zdarzenia routingu bardziej szczegółowo. W następujących omówieniach uzyskać więcej informacji, [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md), [omówienie fokus](../../../../docs/framework/wpf/advanced/focus-overview.md), [Omówienie elementów Base](../../../../docs/framework/wpf/advanced/base-elements-overview.md), [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md), i [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd fokusu](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [Przegląd poleceń](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Przegląd elementów podstawowych](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Właściwości](../../../../docs/framework/wpf/advanced/properties-wpf.md)
