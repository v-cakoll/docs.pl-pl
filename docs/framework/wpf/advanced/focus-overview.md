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
ms.openlocfilehash: de788ec3f0628ff2f7c422c76c73ff7985424113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186665"
---
# <a name="focus-overview"></a>Przegląd Fokus
Istnieją [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dwa główne pojęcia, które odnoszą się do ostrości: fokus klawiatury i logiczne fokus.  Fokus klawiatury odnosi się do elementu, który odbiera dane wejściowe klawiatury i fokus logiczny odnosi się do elementu w zakresie fokusu, który ma fokus.  Pojęcia te zostały szczegółowo omówione w tym przeglądzie.  Zrozumienie różnicy w tych pojęciach jest ważne dla tworzenia złożonych aplikacji, które mają wiele regionów, w których można uzyskać fokus.  
  
 Główne klasy, które uczestniczą w <xref:System.Windows.Input.Keyboard> zarządzaniu <xref:System.Windows.Input.FocusManager> fokusem to klasa, <xref:System.Windows.UIElement> klasa <xref:System.Windows.ContentElement>i klasy elementów podstawowych, takie jak i .  Aby uzyskać więcej informacji na temat elementów podstawowych, zobacz [Omówienie elementów bazowych](base-elements-overview.md).  
  
 Klasa <xref:System.Windows.Input.Keyboard> dotyczy przede wszystkim ostrości klawiatury i <xref:System.Windows.Input.FocusManager> dotyczy to przede wszystkim logicznego skupienia, ale nie jest to absolutne rozróżnienie.  Element, który ma fokus klawiatury będzie również logiczne fokus, ale element, który ma fokus logiczny nie musi mieć fokus klawiatury.  Jest to widoczne, <xref:System.Windows.Input.Keyboard> gdy używasz klasy, aby ustawić element, który ma fokus klawiatury, ponieważ ustawia również logiczne fokus na elemencie.  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>Ostrość klawiatury  
 Fokus klawiatury odnosi się do elementu, który jest obecnie odbieranie danych wejściowych klawiatury.  Może istnieć tylko jeden element na całym pulpicie, który ma fokus klawiatury.  W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], element, który ma <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> fokus klawiatury będzie ustawiony na `true`.  Właściwość <xref:System.Windows.Input.Keyboard.FocusedElement%2A> statyczna <xref:System.Windows.Input.Keyboard> w klasie pobiera element, który obecnie ma fokus klawiatury.  
  
 Aby element uzyskał fokus <xref:System.Windows.UIElement.Focusable%2A> klawiatury, <xref:System.Windows.UIElement.IsVisible%2A> i właściwości elementów podstawowych `true`musi być ustawiona na .  Niektóre klasy, takie <xref:System.Windows.Controls.Panel> jak klasa <xref:System.Windows.UIElement.Focusable%2A> podstawowa, zostały ustawione `false` domyślnie; w związku z <xref:System.Windows.UIElement.Focusable%2A> tym `true` należy ustawić, jeśli chcesz, aby taki element mógł uzyskać fokus klawiatury.  
  
 Fokus klawiatury można uzyskać [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]poprzez interakcję użytkownika z , takich jak tabulacji do elementu lub klikając myszką na niektórych elementów.  Fokus klawiatury można również uzyskać <xref:System.Windows.Input.Keyboard.Focus%2A> programowo <xref:System.Windows.Input.Keyboard> przy użyciu metody na klasie.  Metoda <xref:System.Windows.Input.Keyboard.Focus%2A> próbuje nadać określony element fokus klawiatury.  Zwrócony element jest elementem, który ma fokus klawiatury, który może być inny element niż wymagane, jeśli stary lub nowy obiekt fokus zablokować żądanie.  
  
 W poniższym przykładzie użyto metody <xref:System.Windows.Input.Keyboard.Focus%2A> <xref:System.Windows.Controls.Button>ustawiania fokusu klawiatury na pliku .  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 Właściwość <xref:System.Windows.UIElement.IsKeyboardFocused%2A> na klasy elementów podstawowych pobiera wartość wskazującą, czy element ma fokus klawiatury.  Właściwość <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> na klasy elementów podstawowych pobiera wartość wskazującą, czy element lub którykolwiek z jego wizualnych elementów podrzędnych ma fokus klawiatury.  
  
 Podczas ustawiania początkowego fokusu podczas uruchamiania aplikacji element, który ma odbierać fokus, <xref:System.Windows.UIElement.IsVisible%2A> musi `true`znajdować się w drzewie wizualnym początkowego okna załadowanego przez aplikację, a element musi mieć <xref:System.Windows.UIElement.Focusable%2A> i ustawić na .  Zalecane miejsce, aby ustawić początkowy <xref:System.Windows.FrameworkElement.Loaded> fokus znajduje się w programie obsługi zdarzeń.  Wywołania zwrotnego <xref:System.Windows.Threading.Dispatcher> można również <xref:System.Windows.Threading.Dispatcher.Invoke%2A> <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>użyć przez wywołanie lub .  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>Logiczne skupienie  
 Fokus logiczny <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> odnosi się do zakresu ostrości.  Zakres fokusu jest elementem, który śledzi <xref:System.Windows.Input.FocusManager.FocusedElement%2A> w jego zakresie.  Gdy fokus klawiatury pozostawia zakres ostrości, element fokusu straci fokus klawiatury, ale zachowa fokus logiczny.  Gdy fokus klawiatury powróci do zakresu fokusu, element fokus uzyskiwać fokus klawiatury.  Dzięki temu fokus klawiatury można zmienić między wieloma zakresami fokusu, ale zapewnia, że element skupiona w zakresie fokusu odzyskuje fokus klawiatury, gdy fokus powróci do zakresu fokusu.  
  
 Może istnieć wiele elementów, które mają fokus logiczny w aplikacji, ale może istnieć tylko jeden element, który ma logiczne fokus w określonym zakresie fokusu.  
  
 Element, który ma fokus klawiatury ma fokus logiczny dla zakresu fokusu, do którego należy.  
  
 Element można przekształcić w zakres [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fokusu, ustawiając dołączoną <xref:System.Windows.Input.FocusManager> właściwość <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> na `true`.  W kodzie element można przekształcić w zakres <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>ostrości, wywołując .  
  
 Poniższy przykład <xref:System.Windows.Controls.StackPanel> sprawia, że w <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> zakresie fokusu przez ustawienie dołączonej właściwości.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>zwraca zakres fokusu dla określonego elementu.  
  
 Klasy, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w których domyślnie <xref:System.Windows.Window>są <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ToolBar>zakresami <xref:System.Windows.Controls.ContextMenu>fokusu to , , i .  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>pobiera element koncentruje się dla określonego zakresu fokusu.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>ustawia element skupiona w określonym zakresie fokusu.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>jest zwykle używany do ustawiania początkowego elementu skupiona.  
  
 W poniższym przykładzie ustawia element koncentruje się na zakresie fokusu i pobiera element koncentruje zakresu fokusu.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>Nawigacja przy użyciu klawiatury  
 Klasa <xref:System.Windows.Input.KeyboardNavigation> jest odpowiedzialna za implementowanie domyślnej nawigacji fokus klawiatury po naciśnięciu jednego z klawiszy nawigacyjnych.  Klawisze nawigacyjne to: TAB, SHIFT+TAB, CTRL+TAB, CTRL+SHIFT+TAB, UPARROW, DOWNARROW, LEFTARROW i RIGHTARROW.  
  
 Zachowanie nawigacji kontenera nawigacji można zmienić, <xref:System.Windows.Input.KeyboardNavigation> ustawiając <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>dołączone <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>właściwości , i .  Te właściwości są <xref:System.Windows.Input.KeyboardNavigationMode> typu i możliwe <xref:System.Windows.Input.KeyboardNavigationMode.Continue> <xref:System.Windows.Input.KeyboardNavigationMode.Local>wartości <xref:System.Windows.Input.KeyboardNavigationMode.Contained> <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>są <xref:System.Windows.Input.KeyboardNavigationMode.Once>, <xref:System.Windows.Input.KeyboardNavigationMode.None>, , , i .  Wartością domyślną jest <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, co oznacza, że element nie jest kontenerem nawigacji.  
  
 Poniższy przykład <xref:System.Windows.Controls.Menu> tworzy z <xref:System.Windows.Controls.MenuItem> wieloma obiektami.  Załączona <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> właściwość <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> jest <xref:System.Windows.Controls.Menu>ustawiona na .  Po zmianie fokusu za <xref:System.Windows.Controls.Menu>pomocą klawisza tabu w obrębie , fokus zostanie przesunięty z każdego elementu, a po osiągnięciu ostatniego elementu fokus powróci do pierwszego elementu.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>Programowa nawigacja w centrum uwagi  
 Dodatkowy interfejs API do <xref:System.Windows.UIElement.MoveFocus%2A> <xref:System.Windows.UIElement.PredictFocus%2A>pracy z fokusem są i .  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>zmienia fokus do następnego elementu w aplikacji.  A <xref:System.Windows.Input.TraversalRequest> służy do określania kierunku.   Przekazywane <xref:System.Windows.Input.FocusNavigationDirection> do <xref:System.Windows.UIElement.MoveFocus%2A> określa różne kierunki fokus <xref:System.Windows.Input.FocusNavigationDirection.First>może <xref:System.Windows.Input.FocusNavigationDirection.Last> <xref:System.Windows.Input.FocusNavigationDirection.Up> być <xref:System.Windows.Input.FocusNavigationDirection.Down>przeniesiony, takich jak , i .  
  
 Poniższy przykład <xref:System.Windows.FrameworkElement.MoveFocus%2A> służy do zmiany elementu skupiona.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>zwraca obiekt, który otrzymałby fokus, jeśli fokus miałby zostać zmieniony.  Obecnie <xref:System.Windows.Input.FocusNavigationDirection.Up>tylko , <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left>, <xref:System.Windows.Input.FocusNavigationDirection.Right> i są <xref:System.Windows.FrameworkElement.PredictFocus%2A>obsługiwane przez .  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>Wydarzenia fokusu  
 Zdarzenia związane z fokusem klawiatury <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>to <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> , i <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>, <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>.  Zdarzenia są definiowane jako dołączone <xref:System.Windows.Input.Keyboard> zdarzenia w klasie, ale są łatwiej dostępne jako równoważne kierowane zdarzenia w klasach podstawowych elementów.  Aby uzyskać więcej informacji o zdarzeniach, zobacz [Omówienie trasowych zdarzeń](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>jest wywoływana, gdy element uzyskuje fokus klawiatury.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>jest wywoływana, gdy element traci fokus klawiatury.  Jeśli <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> zdarzenie lub <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> zdarzenie jest <xref:System.Windows.RoutedEventArgs.Handled%2A> obsługiwane i `true`jest ustawione na , a następnie fokus nie ulegnie zmianie.  
  
 Poniższy przykład <xref:System.Windows.UIElement.GotKeyboardFocus> dołącza <xref:System.Windows.UIElement.LostKeyboardFocus> i programy <xref:System.Windows.Controls.TextBox>obsługi zdarzeń do .  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Gdy <xref:System.Windows.Controls.TextBox> uzyskuje fokus <xref:System.Windows.Controls.Control.Background%2A> klawiatury, <xref:System.Windows.Controls.TextBox> właściwość <xref:System.Windows.Media.Brushes.LightBlue%2A>jest zmieniana na .  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Gdy <xref:System.Windows.Controls.TextBox> traci fokus <xref:System.Windows.Controls.Control.Background%2A> klawiatury, <xref:System.Windows.Controls.TextBox> właściwość jest zmieniana z powrotem na biały.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Zdarzenia związane z logicznym fokusem są <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus>.  Te zdarzenia są <xref:System.Windows.Input.FocusManager> zdefiniowane jako dołączone <xref:System.Windows.Input.FocusManager> zdarzenia, ale nie udostępnia otoki zdarzeń CLR.  <xref:System.Windows.UIElement>i <xref:System.Windows.ContentElement> ujawnić te zdarzenia wygodniej.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Przegląd Dane wejściowe](input-overview.md)
- [Przegląd Elementy bazy](base-elements-overview.md)
