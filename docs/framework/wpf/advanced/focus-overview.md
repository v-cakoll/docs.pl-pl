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
ms.openlocfilehash: 620839a0060469604d0affa6637c3cafac0f62c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548113"
---
# <a name="focus-overview"></a>Przegląd Fokus
W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] istnieją dwa główne pojęcia, które odnoszą się do fokus: Klawiatura fokus i logiczny fokus.  Fokus klawiatury odwołuje się do elementu, który odbiera klawiatury i logiczny fokus odwołuje się do elementu w zakresie fokus, który ma fokus.  Pojęcia te omówiono szczegółowo w tym omówieniu.  Opis różnicy w tych pojęć jest ważne w przypadku tworzenia złożonych aplikacji z wielu regionach, gdzie można uzyskać fokusu.  
  
 Główne kategorie, które uczestniczą w funkcje zarządzania są <xref:System.Windows.Input.Keyboard> klasy <xref:System.Windows.Input.FocusManager> klasy, a base element klas, takich jak <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement>.  Aby uzyskać więcej informacji na temat podstawowych elementów, zobacz [podstawowej Omówienie elementów](../../../../docs/framework/wpf/advanced/base-elements-overview.md).  
  
 <xref:System.Windows.Input.Keyboard> Klasy dotyczy głównie fokus klawiatury i <xref:System.Windows.Input.FocusManager> dotyczy przede wszystkim z logiczny fokus, ale nie jest bezwzględna różnicy.  Element, który ma fokus klawiatury będą także mieć logiczny fokus, ale element, który ma logiczny fokus nie ma fokus klawiatury.  To jest widoczny, gdy używasz <xref:System.Windows.Input.Keyboard> klasy można ustawić elementu, który ma fokus klawiatury dla niego ustawia również logiczny fokus w elemencie.  
  

  
<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>Fokus klawiatury  
 Fokus klawiatury odwołuje się do elementu, który jest obecnie odbieranie danych wprowadzonych z klawiatury.  Może istnieć tylko jeden element na całej pulpitu, który ma fokus klawiatury.  W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ma element, który ma fokus klawiatury <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> ustawioną `true`.  Właściwość statyczna <xref:System.Windows.Input.Keyboard.FocusedElement%2A> na <xref:System.Windows.Input.Keyboard> klasy pobiera element, który aktualnie ma fokus klawiatury.  
  
 Aby element, aby uzyskać fokus klawiatury <xref:System.Windows.UIElement.Focusable%2A> i <xref:System.Windows.UIElement.IsVisible%2A> musi mieć wartość właściwości podstawowych elementów `true`.  Niektóre klasy, takich jak <xref:System.Windows.Controls.Panel> klasy podstawowej, mieć <xref:System.Windows.UIElement.Focusable%2A> ustawioną `false` domyślnie; w związku z tym należy ustawić <xref:System.Windows.UIElement.Focusable%2A> do `true` Jeśli chcesz, aby element, aby można było uzyskać fokus klawiatury.  
  
 Fokus klawiatury można uzyskać za pośrednictwem interakcji użytkowników z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], na przykład klawisza TAB do elementu lub kliknięcie przycisku myszy w przypadku niektórych elementów.  Fokus klawiatury również można uzyskać programistycznie przy użyciu <xref:System.Windows.Input.Keyboard.Focus%2A> metoda <xref:System.Windows.Input.Keyboard> klasy.  <xref:System.Windows.Input.Keyboard.Focus%2A> Metody podejmuje próbę przekazania fokus klawiatury określonego elementu.  Zwrócony element to element, który ma fokus klawiatury, która może być elementu innego niż wymagane, jeśli albo starego lub nowego skupić się Blok obiektu żądania.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Input.Keyboard.Focus%2A> metodę, aby ustawić fokus klawiatury na <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A> Właściwości klasy podstawowej elementu pobiera wartość wskazującą, czy element ma fokus klawiatury.  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> Właściwości klasy podstawowej elementu pobiera wartość wskazującą, czy element lub jeden z jego elementów podrzędnych visual ma fokus klawiatury.  
  
 Podczas ustawiania początkowy fokus przy uruchamianiu aplikacji, element, aby ustawić fokusu musi być w drzewie wizualnym okna początkowego załadowanych przez aplikację, i musi mieć element <xref:System.Windows.UIElement.Focusable%2A> i <xref:System.Windows.UIElement.IsVisible%2A> ustawioną `true`.  Zalecane miejsce, aby ustawić początkowy fokus znajduje się <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń.  A <xref:System.Windows.Threading.Dispatcher> wywołania zwrotnego może być również wykorzystywane przez wywołanie <xref:System.Windows.Threading.Dispatcher.Invoke%2A> lub <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>.  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>Logiczny fokus  
 Logiczny fokus odwołuje się do <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> w zakresie fokus.  Zakres fokus jest element, który śledzi <xref:System.Windows.Input.FocusManager.FocusedElement%2A> w jego zakresie.  Gdy zakres fokus utraci fokus klawiatury, ukierunkowanych elementu utraci fokus klawiatury, ale zachowa logiczny fokus.  Po powrocie do zakresu fokus klawiatury ukierunkowanych element uzyska fokus klawiatury.  Dzięki temu dla fokus klawiatury zostanie zmieniony między wiele zakresów fokus, ale gwarantuje, że element skupiają się w zakresie fokus odzyskał fokus klawiatury, gdy nastąpi powrót do zakresu fokus.  
  
 Może istnieć wiele elementów, które ma logiczny fokus w aplikacji, ale może istnieć tylko jeden element, który ma logiczny fokus w zakresie określonego zespołu.  
  
 Element, który ma fokus klawiatury ma logiczny fokus, dla której należy zakres fokus.  
  
 Element można zmienić zakresu fokusu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przez ustawienie <xref:System.Windows.Input.FocusManager> dołączona właściwość <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> do `true`.  W kodzie, element można włączyć w zakresie fokus przez wywołanie metody <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.  
  
 Poniższy przykład powoduje, że <xref:System.Windows.Controls.StackPanel> w zakresie fokus, ustawiając <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> dołączona właściwość.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> zwraca zakres fokus dla określonego elementu.  
  
 Klasy w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , które są zakresów fokus domyślnie są <xref:System.Windows.Window>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.ToolBar>, i <xref:System.Windows.Controls.ContextMenu>.  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> pobiera element ukierunkowanych fokus określonego zakresu.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> Ustawia element skupiają się w zakresie określonym fokus.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> zwykle służy do ustawiania początkowej elementem mającym fokus.  
  
 Ustawia element skupiają się na zakres fokus, pobiera ukierunkowanych element zakresu fokusu w następującym przykładzie.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>Nawigacji klawiatury  
 <xref:System.Windows.Input.KeyboardNavigation> Klasy jest odpowiedzialny za Implementowanie nawigacji fokus klawiatury domyślne, gdy jeden z kluczy nawigacji zostanie naciśnięty.  Klawisze nawigacji są: klucze kartę, SHIFT + TAB klawiszy CTRL + TAB, CTRL + SHIFT + TAB, UPARROW, DOWNARROW, Strzałka w lewo i Strzałka w prawo.  
  
 Zachowanie nawigacji kontenera nawigacji można zmienić ustawienie dołączonego <xref:System.Windows.Input.KeyboardNavigation> właściwości <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>, <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>, i <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>.  Te właściwości są typu <xref:System.Windows.Input.KeyboardNavigationMode> i możliwe wartości to <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, <xref:System.Windows.Input.KeyboardNavigationMode.Local>, <xref:System.Windows.Input.KeyboardNavigationMode.Contained>, <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>, <xref:System.Windows.Input.KeyboardNavigationMode.Once>, i <xref:System.Windows.Input.KeyboardNavigationMode.None>.  Wartość domyślna to <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, co oznacza, że element nie jest kontenerem nawigacji.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Menu> o liczbie <xref:System.Windows.Controls.MenuItem> obiektów.  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> Ustawiono dołączona właściwość <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> na <xref:System.Windows.Controls.Menu>.  Gdy fokus zostanie zmieniona, za pomocą klawisza tab w <xref:System.Windows.Controls.Menu>, fokus zostanie przeniesiony z każdego elementu i po ostatnim elemencie osiągnięciu fokus zwraca pierwszy element.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>Nawigowanie po fokus programowo  
 Dodatkowe [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] do pracy z fokusem są <xref:System.Windows.UIElement.MoveFocus%2A> i <xref:System.Windows.UIElement.PredictFocus%2A>.  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> zmiany fokus do następnego elementu w aplikacji.  A <xref:System.Windows.Input.TraversalRequest> służy do określania kierunku.   <xref:System.Windows.Input.FocusNavigationDirection> Przekazany do <xref:System.Windows.UIElement.MoveFocus%2A> określa fokus różnych kierunkach można przenosić, takich jak <xref:System.Windows.Input.FocusNavigationDirection.First>, <xref:System.Windows.Input.FocusNavigationDirection.Last>, <xref:System.Windows.Input.FocusNavigationDirection.Up> i <xref:System.Windows.Input.FocusNavigationDirection.Down>.  
  
 W poniższym przykładzie użyto <xref:System.Windows.FrameworkElement.MoveFocus%2A> zmienić elementem mającym fokus.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> Zwraca obiekt, który będzie fokusu gdyby można zmienić fokus.  Obecnie tylko <xref:System.Windows.Input.FocusNavigationDirection.Up>, <xref:System.Windows.Input.FocusNavigationDirection.Down>, <xref:System.Windows.Input.FocusNavigationDirection.Left>, i <xref:System.Windows.Input.FocusNavigationDirection.Right> są obsługiwane przez <xref:System.Windows.FrameworkElement.PredictFocus%2A>.  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>Zdarzeń fokusu  
 Zdarzenia związane z fokus klawiatury są <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>, <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> i <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>, <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>.  Zdarzenia są zdefiniowane jako dołączone zdarzenia na <xref:System.Windows.Input.Keyboard> klasy, ale są bardziej łatwo dostępne jako równoważne kierowane zdarzenia na base element klasy.  Aby uzyskać więcej informacji o zdarzeniach, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> jest wywoływane, gdy element uzyskuje fokus klawiatury.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> jest wywoływane, gdy element traci fokus klawiatury.  Jeśli <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> zdarzenia lub <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> zdarzenie jest obsługiwane i <xref:System.Windows.RoutedEventArgs.Handled%2A> ma ustawioną wartość `true`, a następnie fokus nie spowoduje zmiany.  
  
 Poniższy przykład dołącza <xref:System.Windows.UIElement.GotKeyboardFocus> i <xref:System.Windows.UIElement.LostKeyboardFocus> procedury obsługi zdarzeń do <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Gdy <xref:System.Windows.Controls.TextBox> uzyskuje fokus klawiatury <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Controls.TextBox> jest zmieniana na <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Gdy <xref:System.Windows.Controls.TextBox> utraci fokus klawiatury <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Controls.TextBox> zmieniony na biały.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Zdarzenia związane z logiczny fokus są <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus>.  Te zdarzenia są zdefiniowane w <xref:System.Windows.Input.FocusManager> jako dołączone zdarzenia, ale <xref:System.Windows.Input.FocusManager> nie ujawnia otoki zdarzenia CLR.  <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> ułatwia udostępnianie tych zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Input.FocusManager>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.ContentElement>  
 [Przegląd danych wejściowych](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Przegląd elementów podstawowych](../../../../docs/framework/wpf/advanced/base-elements-overview.md)
