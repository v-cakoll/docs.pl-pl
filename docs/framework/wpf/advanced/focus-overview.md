---
title: Przegląd Fokus
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 72b866d714e6a77020bdb74843c3aaa0ba0c3278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703429"
---
# <a name="focus-overview"></a>Przegląd Fokus
W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] istnieją dwa główne pojęcia, które odnoszą się do fokus: za pomocą klawiatury fokus i fokus logiczny.  Fokus klawiatury, który odwołuje się do elementu, który odbiera dane wejściowe z klawiatury i fokus logiczny, który odwołuje się do elementu w zakresie fokus, który ma fokus.  Te pojęcia są szczegółowo omówione w tym omówieniu.  Opis różnicy w tych pojęć jest ważna dla tworzenia złożonych aplikacji z wielu regionów, w którym można uzyskać fokus.  
  
 Główne kategorie, które uczestniczą w funkcje zarządzania są <xref:System.Windows.Input.Keyboard> klasy <xref:System.Windows.Input.FocusManager> klasy i elementu podstawowego klasy takie jak <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement>.  Aby uzyskać więcej informacji na temat podstawowych elementów, zobacz [Przegląd elementów podstawowych](base-elements-overview.md).  
  
 <xref:System.Windows.Input.Keyboard> Klasy dotyczy przede wszystkim fokus klawiatury i <xref:System.Windows.Input.FocusManager> dotyczy przede wszystkim z logiczny fokus, ale nie jest to bezwzględny różnica.  Element, który ma fokus klawiatury będą mieć również logiczny fokus, ale element, który ma fokus logiczny nie ma fokus klawiatury.  Jest to jasne w przypadku używania <xref:System.Windows.Input.Keyboard> klasy, aby ustawić element, który ma fokus klawiatury dla niego ustawia również logiczny fokus w elemencie.  

<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>Fokus klawiatury  
 Fokus klawiatury odnosi się do elementu, który jest obecnie odbieranie danych wprowadzonych z klawiatury.  Może istnieć tylko jeden element dla całego pulpitu, który ma fokus klawiatury.  W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], będzie mieć element, który ma fokus klawiatury <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> równa `true`.  Właściwość statyczna <xref:System.Windows.Input.Keyboard.FocusedElement%2A> na <xref:System.Windows.Input.Keyboard> klasy pobiera element, który aktualnie ma fokus klawiatury.  
  
 Aby element, aby uzyskać fokus klawiatury <xref:System.Windows.UIElement.Focusable%2A> i <xref:System.Windows.UIElement.IsVisible%2A> właściwości elementów podstawowych musi być równa `true`.  Niektóre klasy takie jak <xref:System.Windows.Controls.Panel> klasy bazowej, mają <xref:System.Windows.UIElement.Focusable%2A> równa `false` domyślnie; w związku z tym, należy ustawić <xref:System.Windows.UIElement.Focusable%2A> do `true` Jeśli chcesz, aby element, aby można było uzyskać fokus klawiatury.  
  
 Fokus klawiatury można uzyskać za pośrednictwem interakcji użytkownika z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], takich jak klawiszem TAB do elementu lub klikając przycisk myszy w przypadku niektórych elementów.  Fokus klawiatury można także uzyskać programistycznie przy użyciu <xref:System.Windows.Input.Keyboard.Focus%2A> metody <xref:System.Windows.Input.Keyboard> klasy.  <xref:System.Windows.Input.Keyboard.Focus%2A> Metoda podejmuje próbę przekazania fokus klawiatury określonego elementu.  Zwrócony element jest elementem, który ma fokus klawiatury, która może być element inny niż żądana, jeśli starego lub nowego skupić się Blok obiektu żądania.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Input.Keyboard.Focus%2A> metodę, aby ustawić fokus klawiatury na <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A> Właściwości klasy bazowej elementów pobiera wartość wskazującą, czy element ma fokus klawiatury.  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> Właściwości klasy bazowej elementów pobiera wartość wskazującą, czy element lub jeden z jego elementów podrzędnych visual ma fokus klawiatury.  
  
 Podczas ustawiania początkowy fokus przy uruchamianiu aplikacji, element, aby przenieść fokus, musi być w drzewie wizualnym początkowe okno, które są ładowane przez aplikację, a element musi mieć <xref:System.Windows.UIElement.Focusable%2A> i <xref:System.Windows.UIElement.IsVisible%2A> równa `true`.  Zalecane miejsce, aby ustawić początkowy fokus znajduje się <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń.  A <xref:System.Windows.Threading.Dispatcher> wywołania zwrotnego można również przez wywołanie metody <xref:System.Windows.Threading.Dispatcher.Invoke%2A> lub <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>.  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>Fokus logiczny  
 Fokus logiczny, który odwołuje się do <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> w zakresie fokus.  Zakres fokus jest element, który śledzi <xref:System.Windows.Input.FocusManager.FocusedElement%2A> w jego zakresie.  Gdy fokus klawiatury opuszcza zakresu fokus, wąsko zdefiniowany element utraci fokus klawiatury, ale zachowa fokus logiczny.  Po powrocie do zakresu fokus fokus klawiatury wąsko zdefiniowany element uzyska fokus klawiatury.  Umożliwia fokus klawiatury zmiany między wiele zakresów fokus, ale zapewnia, że element wąsko zdefiniowany w zakresie fokus powrót do zakresu fokus, przez fokus klawiatury.  
  
 Może istnieć wiele elementów, które mają logiczny fokus w aplikacji, ale może istnieć tylko jeden element, który ma logiczny fokus w zakresie określonego zespołu.  
  
 Element, który ma fokus klawiatury ma logiczny fokus dla zakresu fokus, do której należy.  
  
 Element można włączyć do danego zakresu fokus w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , ustawiając <xref:System.Windows.Input.FocusManager> dołączona właściwość <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> do `true`.  W kodzie, element można włączyć do zakresu fokus przez wywołanie metody <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.  
  
 Poniższy przykład wykonuje <xref:System.Windows.Controls.StackPanel> do zakresu fokus, ustawiając <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> dołączona właściwość.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> Zwraca wartość zakresu koncentracji uwagi dla określonego elementu.  
  
 Klasy w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , które są zakresy fokus, domyślnie są <xref:System.Windows.Window>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.ToolBar>, i <xref:System.Windows.Controls.ContextMenu>.  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> pobiera element wąsko zdefiniowany dla zakresu określonej fokus.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> Ustawia element wąsko zdefiniowany w zakresie określonym fokus.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> Zazwyczaj służy do ustawiania ukierunkowanych elementu początkowego.  
  
 Poniższy przykład ustawia wąsko zdefiniowany element w zakresie fokus i pobiera wąsko zdefiniowany element zakres fokus.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>Nawigacja przy użyciu klawiatury  
 <xref:System.Windows.Input.KeyboardNavigation> Klasy jest odpowiedzialny za Implementowanie nawigacji fokus klawiatury domyślne, po kliknięciu jednego z klawiszy nawigacyjnych.  Dostępne są następujące klawisze nawigacji: Klucze karty, SHIFT + TAB, CTRL + TAB, CTRL + SHIFT + TAB, UPARROW, Strzałka w dół, Strzałka w lewo i Strzałka w prawo.  
  
 Zachowania nawigacji kontenera nawigacji można zmienić przez ustawienie dołączonego <xref:System.Windows.Input.KeyboardNavigation> właściwości <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>, <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>, i <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>.  Te właściwości są typu <xref:System.Windows.Input.KeyboardNavigationMode> i możliwe wartości to <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, <xref:System.Windows.Input.KeyboardNavigationMode.Local>, <xref:System.Windows.Input.KeyboardNavigationMode.Contained>, <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>, <xref:System.Windows.Input.KeyboardNavigationMode.Once>, i <xref:System.Windows.Input.KeyboardNavigationMode.None>.  Wartość domyślna to <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, co oznacza, że element nie jest kontenerem nawigacji.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Menu> z liczbą <xref:System.Windows.Controls.MenuItem> obiektów.  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> Dołączonej właściwości jest równa <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> na <xref:System.Windows.Controls.Menu>.  Po zmianie fokusu przy użyciu klawisza tab w ramach <xref:System.Windows.Controls.Menu>fokus zostanie przeniesiony z każdego elementu i po ostatnim elemencie w osiągnięciu fokus powróci do pierwszego elementu.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>Nawigacja programowo koncentracji uwagi  
 Dodatkowe [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] do pracy z fokusem są <xref:System.Windows.UIElement.MoveFocus%2A> i <xref:System.Windows.UIElement.PredictFocus%2A>.  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> zmiany fokus do następnego elementu w aplikacji.  A <xref:System.Windows.Input.TraversalRequest> służy do określania kierunku.   <xref:System.Windows.Input.FocusNavigationDirection> Przekazany do <xref:System.Windows.UIElement.MoveFocus%2A> określa fokus różnych kierunkach można przenosić, taką jak <xref:System.Windows.Input.FocusNavigationDirection.First>, <xref:System.Windows.Input.FocusNavigationDirection.Last>, <xref:System.Windows.Input.FocusNavigationDirection.Up> i <xref:System.Windows.Input.FocusNavigationDirection.Down>.  
  
 W poniższym przykładzie użyto <xref:System.Windows.FrameworkElement.MoveFocus%2A> do zmieniania elementu wąsko zdefiniowany.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> Zwraca obiekt, który otrzyma fokus, gdyby fokus ma zostać zmieniony.  Obecnie tylko <xref:System.Windows.Input.FocusNavigationDirection.Up>, <xref:System.Windows.Input.FocusNavigationDirection.Down>, <xref:System.Windows.Input.FocusNavigationDirection.Left>, i <xref:System.Windows.Input.FocusNavigationDirection.Right> są obsługiwane przez <xref:System.Windows.FrameworkElement.PredictFocus%2A>.  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>Zdarzenia fokusu  
 Zdarzenia związane z fokus klawiatury są <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>, <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> i <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>, <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>.  Zdarzenia są definiowane jako dołączone zdarzenia na <xref:System.Windows.Input.Keyboard> klasy, ale są łatwiej dostępne jako równoważne zdarzeń trasowanych na klasach elementu podstawowego.  Aby uzyskać więcej informacji o zdarzeniach zobacz [Przegląd zdarzeń kierowane](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> jest wywoływane, gdy element uzyskuje fokus klawiatury.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> jest wywoływane, gdy element traci fokus klawiatury.  Jeśli <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> zdarzeń lub <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> zdarzenie jest obsługiwane i <xref:System.Windows.RoutedEventArgs.Handled%2A> jest ustawiona na `true`, a następnie fokus nie ulegnie zmianie.  
  
 Poniższy przykład dołącza <xref:System.Windows.UIElement.GotKeyboardFocus> i <xref:System.Windows.UIElement.LostKeyboardFocus> programów obsługi zdarzeń do <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Gdy <xref:System.Windows.Controls.TextBox> uzyskuje fokus klawiatury <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Controls.TextBox> jest zmieniana na <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Gdy <xref:System.Windows.Controls.TextBox> straci fokus klawiatury <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Controls.TextBox> zmieniony na biały.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Zdarzenia związane z fokus logiczny są <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus>.  Zdarzenia te są definiowane na <xref:System.Windows.Input.FocusManager> jako dołączone zdarzenia, ale <xref:System.Windows.Input.FocusManager> nie ujawnia otoki zdarzeń CLR.  <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> ułatwia udostępnianie tych zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Przegląd danych wejściowych](input-overview.md)
- [Przegląd elementów podstawowych](base-elements-overview.md)
