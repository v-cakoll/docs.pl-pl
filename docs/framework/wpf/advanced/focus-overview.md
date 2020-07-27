---
title: Przegląd Fokus
description: 'Dowiedz się więcej na temat dwóch głównych koncepcji w Windows Presentation Foundation, które odnoszą się do fokusu: fokus klawiatury i fokus logiczny.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 71aeb577cccd2c3b16df1c5a3cb772dd1f5479e2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165110"
---
# <a name="focus-overview"></a>Przegląd Fokus
Istnieją [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dwa główne pojęcia, które odnoszą się do fokusu: fokus klawiatury i fokus logiczny.  Fokus klawiatury odnosi się do elementu, który odbiera dane wejściowe z klawiatury i fokus logiczny odnosi się do elementu w zakresie fokusu, który ma fokus.  Te koncepcje omówiono szczegółowo w tym omówieniu.  Zrozumienie różnic w tych pojęciach jest istotne w przypadku tworzenia złożonych aplikacji, które mają wiele regionów, w których można uzyskać fokus.  
  
 Główne klasy, które uczestniczą w zarządzaniu fokusem <xref:System.Windows.Input.Keyboard> , są klasami, <xref:System.Windows.Input.FocusManager> klasami i klasami elementów podstawowych, takimi jak <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> .  Aby uzyskać więcej informacji na temat elementów podstawowych, zobacz [Omówienie elementów podstawowych](base-elements-overview.md).  
  
 <xref:System.Windows.Input.Keyboard>Klasa jest objęta głównie fokusem klawiatury i <xref:System.Windows.Input.FocusManager> dotyczy głównie fokusu logicznego, ale nie jest to bezwzględne rozróżnienie.  Element, który ma fokus klawiatury, będzie również miał fokus logiczny, ale element, który ma fokus logiczny, nie musi mieć fokus klawiatury.  Jest to oczywiste, gdy użyjesz <xref:System.Windows.Input.Keyboard> klasy, aby ustawić element, który ma fokus klawiatury, a dla niego ustawia również fokus logiczny dla elementu.  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>Fokus klawiatury  
 Fokus klawiatury odnosi się do elementu, który aktualnie otrzymuje dane wejściowe z klawiatury.  Na całym pulpicie może znajdować się tylko jeden element, który ma fokus klawiatury.  W programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element, który ma fokus klawiatury, będzie miał <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> ustawioną wartość `true` .  Właściwość statyczna <xref:System.Windows.Input.Keyboard.FocusedElement%2A> <xref:System.Windows.Input.Keyboard> klasy pobiera element, który ma obecnie fokus klawiatury.  
  
 Aby element mógł uzyskać fokus klawiatury, <xref:System.Windows.UIElement.Focusable%2A> i <xref:System.Windows.UIElement.IsVisible%2A> właściwości elementów podstawowych musi być ustawiony na `true` .  Niektóre klasy, takie jak <xref:System.Windows.Controls.Panel> Klasa bazowa, mają <xref:System.Windows.UIElement.Focusable%2A> domyślnie ustawioną wartość `false` . w związku z tym, należy ustawić <xref:System.Windows.UIElement.Focusable%2A> na, jeśli chcesz, aby `true` ten element mógł uzyskać fokus klawiatury.  
  
 Fokus klawiatury można uzyskać za pomocą interakcji użytkownika z, na przykład z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tabulacją w element lub klikając myszą na określonych elementach.  Fokus klawiatury można również uzyskać programowo przy użyciu <xref:System.Windows.Input.Keyboard.Focus%2A> metody <xref:System.Windows.Input.Keyboard> klasy.  <xref:System.Windows.Input.Keyboard.Focus%2A>Metoda próbuje nadać określony fokus klawiatury elementu.  Zwrócony element to element, który ma fokus klawiatury, który może być inny niż żądany, jeśli stary lub nowy obiekt fokusu blokuje żądanie.  
  
 W poniższym przykładzie zastosowano <xref:System.Windows.Input.Keyboard.Focus%2A> metodę, aby ustawić fokus klawiatury na <xref:System.Windows.Controls.Button> .  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>Właściwość w klasach elementu podstawowego Pobiera wartość wskazującą, czy element ma fokus klawiatury.  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>Właściwość w klasach elementu podstawowego Pobiera wartość wskazującą, czy element lub jeden z jego elementów podrzędnych wizualizacji ma fokus klawiatury.  
  
 Podczas ustawiania początkowego fokusu podczas uruchamiania aplikacji, element, który ma zostać ustawiony fokus musi znajdować się w drzewie wizualnym początkowego okna załadowanego przez aplikację, a element musi mieć <xref:System.Windows.UIElement.Focusable%2A> i mieć <xref:System.Windows.UIElement.IsVisible%2A> ustawioną wartość `true` .  Zalecane miejsce na ustawienie fokus początkowy znajduje się w programie <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń.  <xref:System.Windows.Threading.Dispatcher>Wywołanie zwrotne może być również używane przez wywołanie <xref:System.Windows.Threading.Dispatcher.Invoke%2A> lub <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> .  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>Fokus logiczny  
 Fokus logiczny odnosi się do <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> zakresu fokusu.  Zakres fokusu to element, który śledzi <xref:System.Windows.Input.FocusManager.FocusedElement%2A> zakres.  Gdy fokus klawiatury opuszcza zakres fokusu, element skoncentrowany utraci fokus klawiatury, ale będzie utrzymywać fokus logiczny.  Gdy fokus klawiatury wraca do zakresu fokusu, element Focus uzyska fokus klawiatury.  Pozwala to na zmianę fokusu klawiatury między wieloma zakresami fokusu, ale zapewnia, że element skoncentrowany w zakresie fokusu odzyskuje fokus klawiatury, gdy fokus powróci do zakresu fokusu.  
  
 Może istnieć wiele elementów mających fokus logiczny w aplikacji, ale może istnieć tylko jeden element, który ma logiczne fokus w konkretnym zakresie fokusu.  
  
 Element, który ma fokus klawiatury, ma fokus logiczny dla zakresu fokusu, do którego należy.  
  
 Element można przekształcić w zakres fokusu w programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , ustawiając <xref:System.Windows.Input.FocusManager> Właściwość dołączoną <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> do `true` .  W kodzie, element można przekształcić w zakres fokusu przez wywołanie <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> .  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.StackPanel> zakres fokusu przez ustawienie <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> dołączonej właściwości.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>Zwraca zakres fokusu dla określonego elementu.  
  
 Klasy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , w których domyślnie są zakresy koncentracji <xref:System.Windows.Window> , to,, <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ToolBar> i <xref:System.Windows.Controls.ContextMenu> .  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>Pobiera element skoncentrowany dla określonego zakresu fokusu.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>Ustawia element skoncentrowany w określonym zakresie fokusu.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>jest zazwyczaj używany do ustawiania początkowego elementu fokusowego.  
  
 Poniższy przykład ustawia element skoncentrowany w zakresie fokusu i pobiera skoncentrowany element zakresu fokusu.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>Nawigacja przy użyciu klawiatury  
 <xref:System.Windows.Input.KeyboardNavigation>Klasa jest odpowiedzialna za implementację domyślnej nawigacji fokusu klawiatury po naciśnięciu klawisza nawigacyjnego.  Klucze nawigacji to: TAB, SHIFT + TAB, CTRL + TAB, CTRL + SHIFT + TAB, strzałka, LEFTARROW i RIGHTARROW.  
  
 Zachowanie nawigacji kontenera nawigacji można zmienić, ustawiając dołączone <xref:System.Windows.Input.KeyboardNavigation> właściwości <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> , <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A> i <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> .  Te właściwości są typu, <xref:System.Windows.Input.KeyboardNavigationMode> a możliwe wartości to <xref:System.Windows.Input.KeyboardNavigationMode.Continue> ,, <xref:System.Windows.Input.KeyboardNavigationMode.Local> , <xref:System.Windows.Input.KeyboardNavigationMode.Contained> , <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Input.KeyboardNavigationMode.Once> i <xref:System.Windows.Input.KeyboardNavigationMode.None> .  Wartość domyślna to <xref:System.Windows.Input.KeyboardNavigationMode.Continue> , co oznacza, że element nie jest kontenerem nawigacyjnym.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Menu> z liczbą <xref:System.Windows.Controls.MenuItem> obiektów.  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>Dołączona właściwość jest ustawiona na <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Controls.Menu> .  Gdy fokus jest zmieniany przy użyciu klawisza Tab w <xref:System.Windows.Controls.Menu> , fokus zostanie przesunięty z każdego elementu i po osiągnięciu ostatniego elementu fokus powróci do pierwszego elementu.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>Programistyczne nawigowanie po fokusie  
 Dodatkowy interfejs API do pracy z fokusem to <xref:System.Windows.UIElement.MoveFocus%2A> i <xref:System.Windows.UIElement.PredictFocus%2A> .  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>zmienia fokus na następny element w aplikacji.  <xref:System.Windows.Input.TraversalRequest>Służy do określenia kierunku.   <xref:System.Windows.Input.FocusNavigationDirection>Przesłany do <xref:System.Windows.UIElement.MoveFocus%2A> określa różne kierunki, które można przenieść, takich jak <xref:System.Windows.Input.FocusNavigationDirection.First> , <xref:System.Windows.Input.FocusNavigationDirection.Last> , <xref:System.Windows.Input.FocusNavigationDirection.Up> i <xref:System.Windows.Input.FocusNavigationDirection.Down> .  
  
 Poniższy przykład używa <xref:System.Windows.FrameworkElement.MoveFocus%2A> do zmiany priorytetowego elementu.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>zwraca obiekt, który będzie miał fokus, jeśli fokus został zmieniony.  Obecnie tylko <xref:System.Windows.Input.FocusNavigationDirection.Up> ,, <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left> , i <xref:System.Windows.Input.FocusNavigationDirection.Right> są obsługiwane przez program <xref:System.Windows.FrameworkElement.PredictFocus%2A> .  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>Zdarzenia fokusu  
 Zdarzenia związane z fokusem klawiatury to <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> , <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> i <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> .  Zdarzenia są definiowane jako dołączone zdarzenia w <xref:System.Windows.Input.Keyboard> klasie, ale są bardziej łatwo dostępne jako równoważne zdarzenia kierowane do klas elementów podstawowych.  Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>jest uruchamiany, gdy element uzyska fokus klawiatury.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>jest uruchamiany, gdy element utraci fokus klawiatury.  Jeśli <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> zdarzenie lub <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> zdarzenie jest obsługiwane i <xref:System.Windows.RoutedEventArgs.Handled%2A> ma ustawioną wartość `true` , fokus nie ulegnie zmianie.  
  
 Poniższy przykład dołącza <xref:System.Windows.UIElement.GotKeyboardFocus> i <xref:System.Windows.UIElement.LostKeyboardFocus> obsługuje obsługę zdarzeń do <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Gdy <xref:System.Windows.Controls.TextBox> fokus klawiatury uzyska dostęp, <xref:System.Windows.Controls.Control.Background%2A> Właściwość <xref:System.Windows.Controls.TextBox> jest zmieniana na <xref:System.Windows.Media.Brushes.LightBlue%2A> .  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Po <xref:System.Windows.Controls.TextBox> utracie fokusu klawiatury <xref:System.Windows.Controls.Control.Background%2A> Właściwość <xref:System.Windows.Controls.TextBox> jest zmieniana na biały.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Zdarzenia związane z fokusem logicznym to <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus> .  Te zdarzenia są definiowane w <xref:System.Windows.Input.FocusManager> dołączonych zdarzeniach, ale <xref:System.Windows.Input.FocusManager> nie uwidaczniają otok zdarzeń CLR.  <xref:System.Windows.UIElement>i <xref:System.Windows.ContentElement> uwidocznić te zdarzenia bardziej wygodnie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Przegląd Dane wejściowe](input-overview.md)
- [Przegląd Elementy bazy](base-elements-overview.md)
