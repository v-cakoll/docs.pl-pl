---
title: Przegląd Polecenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interfaces [WPF], ICommandSource
- command library [WPF]
- commands [WPF], definition of
- CommandBindings [WPF]
- ICommandSource interfaces [WPF]
- commanding [WPF]
- CommandManager [WPF]
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
ms.openlocfilehash: 192fe629493947ffe4e0aa8ade417b7701ff95b4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004596"
---
# <a name="commanding-overview"></a>Przegląd Polecenia
<a name="introduction"></a>Polecenie jest mechanizmem wprowadzania w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], który zapewnia obsługę danych wejściowych na wyższym poziomie semantycznym niż dane wejściowe urządzenia. Przykładami poleceń są operacje **kopiowania**, **wycinania**i **wklejania** w wielu aplikacjach.  
  
 To omówienie definiuje, jakie polecenia znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które klasy są częścią modelu poleceń i jak używać poleceń i tworzyć polecenia w aplikacjach.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Co to są polecenia?](#commands_at_10000_feet)  
  
- [Proste przykładowe polecenie w WPF](#simple_command)  
  
- [Cztery główne koncepcje w przypadku poleceń WPF](#Four_main_Concepts)  
  
- [Biblioteka poleceń](#Command_Library)  
  
- [Tworzenie poleceń niestandardowych](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Co to są polecenia?  
 Polecenia mają kilka zastosowań. Pierwszy cel polega na rozdzieleniu semantyki i obiektu, który wywołuje polecenie z logiki, która wykonuje polecenie. Pozwala to na wiele i różne źródła do wywołania tej samej logiki poleceń i umożliwia dostosowanie logiki poleceń dla różnych elementów docelowych. Na przykład operacje edycji **Kopiowanie**, **wycinanie**i **wklejanie**, które znajdują się w wielu aplikacjach, mogą być wywoływane przy użyciu różnych akcji użytkownika, jeśli są implementowane za pomocą poleceń. Aplikacja może zezwolić użytkownikowi na wycinanie wybranych obiektów lub tekstu przez kliknięcie przycisku, wybranie elementu w menu lub użycie kombinacji klawiszy, takiej jak CTRL + X. Za pomocą poleceń można powiązać poszczególne typy akcji użytkownika z tą samą logiką.  
  
 Innym celem poleceń jest wskazanie, czy akcja jest dostępna. Aby kontynuować przykład wycinania obiektu lub tekstu, akcja ma sens tylko wtedy, gdy coś jest zaznaczone. Jeśli użytkownik próbuje wyciąć obiekt lub tekst bez żadnych wybranych elementów, nic się nie stało. Aby wskazać to użytkownikowi, wiele aplikacji wyłącza przyciski i elementy menu, dzięki czemu użytkownik wie, czy można wykonać akcję. Polecenie może wskazywać, czy możliwe jest wykonanie akcji przez implementację metody <xref:System.Windows.Input.ICommand.CanExecute%2A>. Przycisk może subskrybować zdarzenie <xref:System.Windows.Input.ICommand.CanExecuteChanged> i być wyłączone, jeśli <xref:System.Windows.Input.ICommand.CanExecute%2A> zwróci `false` lub włączyć, jeśli <xref:System.Windows.Input.ICommand.CanExecute%2A> zwróci wartość `true`.  
  
 Semantyka polecenia może być spójna w aplikacjach i klasach, ale logika akcji jest specyficzna dla konkretnego obiektu. Kombinacja klawiszy CTRL + X wywołuje polecenie **Wytnij** w klasach tekstowych, klasach obrazów i przeglądarkach sieci Web, ale rzeczywista logika wykonywania operacji **wycinania** jest definiowana przez aplikację wykonującą wycinanie. @No__t-0 umożliwia klientom implementację logiki. Obiekt tekstowy może wyciąć zaznaczony tekst do schowka, podczas gdy obiekt obrazu może wyciąć wybrany obraz. Gdy aplikacja obsługuje zdarzenie <xref:System.Windows.Input.CommandManager.Executed>, ma dostęp do obiektu docelowego polecenia i może podejmować odpowiednie działania w zależności od typu elementu docelowego.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>Proste przykładowe polecenie w WPF  
 Najprostszym sposobem użycia polecenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest użycie wstępnie zdefiniowanego <xref:System.Windows.Input.RoutedCommand> z jednej z klas biblioteki poleceń; Użyj kontrolki z natywną obsługą obsługi polecenia; i użyj formantu, który ma natywną obsługę wywoływania polecenia.  @No__t-0 polecenie jest jednym ze wstępnie zdefiniowanych poleceń w klasie <xref:System.Windows.Input.ApplicationCommands>.  Kontrolka <xref:System.Windows.Controls.TextBox> ma wbudowaną logikę do obsługi polecenia <xref:System.Windows.Input.ApplicationCommands.Paste%2A>.  Natomiast Klasa <xref:System.Windows.Controls.MenuItem> ma natywną obsługę wywoływania poleceń.  
  
 Poniższy przykład pokazuje, jak skonfigurować <xref:System.Windows.Controls.MenuItem>, aby po jego kliknięciu wywoła polecenie <xref:System.Windows.Input.ApplicationCommands.Paste%2A> na <xref:System.Windows.Controls.TextBox>, przy założeniu, że <xref:System.Windows.Controls.TextBox> ma fokus klawiatury.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>Cztery główne koncepcje w przypadku poleceń WPF  
 Model polecenia kierowany w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może być podzielony na cztery główne koncepcje: polecenie, źródło polecenia, obiekt docelowy polecenia i powiązanie poleceń:  
  
- *Polecenie* jest akcją do wykonania.  
  
- *Źródło polecenia* jest obiektem, który wywołuje polecenie.  
  
- *Element docelowy polecenia* jest obiektem, na którym jest wykonywane polecenie.  
  
- *Powiązanie polecenia* to obiekt, który mapuje logikę poleceń na polecenie.  
  
 W poprzednim przykładzie polecenie <xref:System.Windows.Input.ApplicationCommands.Paste%2A> jest poleceniem, <xref:System.Windows.Controls.MenuItem> jest źródłem polecenia, <xref:System.Windows.Controls.TextBox> jest elementem docelowym polecenia i powiązanie polecenia jest dostarczane przez kontrolkę <xref:System.Windows.Controls.TextBox>.  Należy zauważyć, że nie zawsze jest to przypadek, że <xref:System.Windows.Input.CommandBinding> jest dostarczana przez formant, który jest klasą docelową polecenia.  Bardzo często <xref:System.Windows.Input.CommandBinding> musi zostać utworzony przez dewelopera aplikacji lub <xref:System.Windows.Input.CommandBinding> może być dołączany do obiektu nadrzędnego polecenia.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Polecenia  
 Polecenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są tworzone przez implementację interfejsu <xref:System.Windows.Input.ICommand>.  <xref:System.Windows.Input.ICommand> uwidacznia dwie metody, <xref:System.Windows.Input.ICommand.Execute%2A>, i <xref:System.Windows.Input.ICommand.CanExecute%2A> oraz zdarzenie <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A> wykonuje akcje, które są skojarzone z poleceniem. <xref:System.Windows.Input.ICommand.CanExecute%2A> Określa, czy polecenie można wykonać na bieżącym obiekcie docelowym polecenia. <xref:System.Windows.Input.ICommand.CanExecuteChanged> jest zgłaszany, jeśli Menedżer poleceń, który scentralizowany operacje polecenia wykrywa zmianę w źródle polecenia, która może unieważnić polecenie, które zostało podniesione, ale nie zostało jeszcze wykonane przez powiązanie polecenia.  Implementacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommand> jest klasą <xref:System.Windows.Input.RoutedCommand> i jest fokusem tego omówienia.  
  
 Główne źródła danych wejściowych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to mysz, klawiatura, atrament i rozesłane polecenia.  Dodatkowe dane wejściowe zorientowane na urządzenia używają <xref:System.Windows.RoutedEvent> do powiadamiania obiektów na stronie aplikacji o wystąpieniu zdarzenia wejściowego.  @No__t-0 nie jest inny.  Metody <xref:System.Windows.Input.RoutedCommand.Execute%2A> i <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> <xref:System.Windows.Input.RoutedCommand> nie zawierają logiki aplikacji dla polecenia, ale raczej zgłaszają zdarzenia kierowane, które tuneluje i bąbelki przez drzewo elementów do momentu wystąpienia obiektu z <xref:System.Windows.Input.CommandBinding>.  @No__t-0 zawiera programy obsługi dla tych zdarzeń i jest obsługą, która wykonuje polecenie.  Aby uzyskać więcej informacji na temat routingu zdarzeń w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
 Metoda <xref:System.Windows.Input.RoutedCommand.Execute%2A> na <xref:System.Windows.Input.RoutedCommand> wywołuje <xref:System.Windows.Input.CommandManager.PreviewExecuted> i zdarzenia <xref:System.Windows.Input.CommandManager.Executed> w obiekcie docelowym polecenia.  Metoda <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> na <xref:System.Windows.Input.RoutedCommand> wywołuje zdarzenia <xref:System.Windows.Input.CommandManager.CanExecute> i <xref:System.Windows.Input.CommandManager.PreviewCanExecute> w obiekcie docelowym polecenia.  Te zdarzenia są tunele i bąbelki przez drzewo elementów do momentu napotkania obiektu, który ma <xref:System.Windows.Input.CommandBinding> dla danego polecenia.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dostarcza zestaw typowych poleceń kierowanych w ramach kilku klas: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands> i <xref:System.Windows.Documents.EditingCommands>.  Te klasy składają się tylko z obiektów <xref:System.Windows.Input.RoutedCommand>, a nie logiki implementacji polecenia.  Logika implementacji jest odpowiedzialna za obiekt, na którym polecenie jest wykonywane.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Źródła poleceń  
 Źródło polecenia jest obiektem, który wywołuje polecenie.  Przykłady źródeł poleceń to <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button> i <xref:System.Windows.Input.KeyGesture>.  
  
 Źródła poleceń w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zazwyczaj implementują interfejs <xref:System.Windows.Input.ICommandSource>.  
  
 <xref:System.Windows.Input.ICommandSource> uwidacznia trzy właściwości: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> i <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A> to polecenie, które ma zostać wykonane w przypadku wywołania źródła poleceń.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> to obiekt, na którym ma zostać wykonane polecenie.  Warto zauważyć, że w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Właściwość <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> w <xref:System.Windows.Input.ICommandSource> ma zastosowanie tylko wtedy, gdy <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand>.  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona dla <xref:System.Windows.Input.ICommandSource>, a odpowiednie polecenie nie jest <xref:System.Windows.Input.RoutedCommand>, obiekt docelowy polecenia jest ignorowany. Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> nie jest ustawiona, element z fokusem klawiatury będzie elementem docelowym polecenia.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> jest typem danych zdefiniowanym przez użytkownika, który służy do przekazywania informacji do programów obsługi implementujących polecenie.  
  
 Klasy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementujące <xref:System.Windows.Input.ICommandSource> są <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink> i <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem> i <xref:System.Windows.Documents.Hyperlink> Wywołaj polecenie po kliknięciu, a <xref:System.Windows.Input.InputBinding> wywołuje polecenie, gdy zostanie wykonane <xref:System.Windows.Input.InputGesture>.  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.MenuItem> w <xref:System.Windows.Controls.ContextMenu> jako źródło polecenia dla polecenia <xref:System.Windows.Input.ApplicationCommands.Properties%2A>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Zazwyczaj źródło polecenia będzie nasłuchiwać zdarzenia <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged>.  To zdarzenie informuje źródło polecenia, że możliwość wykonania polecenia w bieżącym obiekcie docelowym polecenia mogła ulec zmianie.  Źródło polecenia może badać bieżący stan <xref:System.Windows.Input.RoutedCommand> przy użyciu metody <xref:System.Windows.Input.RoutedCommand.CanExecute%2A>.  Źródło polecenia może następnie wyłączyć, jeśli polecenie nie może zostać wykonane.  Przykładem jest szare <xref:System.Windows.Controls.MenuItem>, gdy polecenie nie może zostać wykonane.  
  
 @No__t-0 może służyć jako źródło polecenia.  Dwa typy gestów wejścia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to <xref:System.Windows.Input.KeyGesture> i <xref:System.Windows.Input.MouseGesture>.  Możesz traktować <xref:System.Windows.Input.KeyGesture> jako skrót klawiaturowy, taki jak CTRL + C.  @No__t-0 składa się z <xref:System.Windows.Input.Key> i zestawu <xref:System.Windows.Input.ModifierKeys>.  @No__t-0 składa się z <xref:System.Windows.Input.MouseAction> i opcjonalnego zestawu <xref:System.Windows.Input.ModifierKeys>.  
  
 Aby <xref:System.Windows.Input.InputGesture> działał jako źródło polecenia, musi być skojarzona z poleceniem. Istnieje kilka sposobów, aby to zrobić.  Jednym ze sposobów jest użycie <xref:System.Windows.Input.InputBinding>.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Input.KeyBinding> między <xref:System.Windows.Input.KeyGesture> i <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Innym sposobem kojarzenia <xref:System.Windows.Input.InputGesture> z <xref:System.Windows.Input.RoutedCommand> jest dodanie <xref:System.Windows.Input.InputGesture> do <xref:System.Windows.Input.InputGestureCollection> na <xref:System.Windows.Input.RoutedCommand>.  
  
 Poniższy przykład pokazuje, jak dodać <xref:System.Windows.Input.KeyGesture> do <xref:System.Windows.Input.InputGestureCollection> <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 @No__t-0 kojarzy polecenie z obsługą zdarzeń implementującą polecenie.  
  
 Klasa <xref:System.Windows.Input.CommandBinding> zawiera właściwość <xref:System.Windows.Input.CommandBinding.Command%2A>, <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> i <xref:System.Windows.Input.CommandBinding.CanExecute> zdarzeń.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> to polecenie, z którym jest skojarzony <xref:System.Windows.Input.CommandBinding>.  Programy obsługi zdarzeń dołączone do zdarzeń <xref:System.Windows.Input.CommandBinding.PreviewExecuted> i <xref:System.Windows.Input.CommandBinding.Executed> implementują logikę poleceń.  Programy obsługi zdarzeń dołączone do zdarzeń <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> i <xref:System.Windows.Input.CommandBinding.CanExecute> określają, czy polecenie można wykonać na bieżącym obiekcie docelowym polecenia.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Input.CommandBinding> w głównym <xref:System.Windows.Window> aplikacji.  @No__t-0 kojarzy polecenie <xref:System.Windows.Input.ApplicationCommands.Open%2A> z obsługą <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandBinding.CanExecute>.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Następnie zostanie utworzona <xref:System.Windows.Input.ExecutedRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler>.  @No__t-0 otwiera <xref:System.Windows.MessageBox>, który wyświetla ciąg informujący, że polecenie zostało wykonane.  @No__t-0 ustawia właściwość <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> na `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 @No__t-0 jest dołączany do określonego obiektu, takiego jak główny <xref:System.Windows.Window> aplikacji lub kontrolki.  Obiekt, do którego jest dołączany <xref:System.Windows.Input.CommandBinding> definiuje zakres powiązania.  Na przykład wartość <xref:System.Windows.Input.CommandBinding> dołączona do elementu nadrzędnego polecenia Target może być osiągnięta przez zdarzenie <xref:System.Windows.Input.CommandBinding.Executed>, ale nie można osiągnąć <xref:System.Windows.Input.CommandBinding> dołączonego do elementu podrzędnego elementu docelowego polecenia.  Jest to bezpośrednia konsekwencja dla sposobu, w jaki tunele i bąbelki <xref:System.Windows.RoutedEvent> z obiektu, który wywołuje zdarzenie.  
  
 W niektórych sytuacjach <xref:System.Windows.Input.CommandBinding> jest dołączona do samego obiektu docelowego polecenia, na przykład z klasą <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A> i <xref:System.Windows.Input.ApplicationCommands.Paste%2A> poleceniami. Dość często zdarza się, aby dołączać <xref:System.Windows.Input.CommandBinding> do elementu nadrzędnego polecenia, takich jak główna <xref:System.Windows.Window> lub obiekt aplikacji, zwłaszcza jeśli ten sam <xref:System.Windows.Input.CommandBinding> może być używany dla wielu celów polecenia.  Są to decyzje projektowe, które należy wziąć pod uwagę podczas tworzenia infrastruktury poleceń.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Element docelowy polecenia  
 Obiekt docelowy polecenia jest elementem, w którym polecenie jest wykonywane.  W odniesieniu do <xref:System.Windows.Input.RoutedCommand>, obiekt docelowy polecenia jest elementem, w którym rozpoczyna się Routing <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandManager.CanExecute>.  Jak wspomniano wcześniej, w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Właściwość <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> w <xref:System.Windows.Input.ICommandSource> ma zastosowanie tylko wtedy, gdy <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand>.  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona dla <xref:System.Windows.Input.ICommandSource>, a odpowiednie polecenie nie jest <xref:System.Windows.Input.RoutedCommand>, obiekt docelowy polecenia jest ignorowany.  
  
 Źródło polecenia może jawnie ustawić element docelowy polecenia.  Jeśli obiekt docelowy polecenia nie jest zdefiniowany, element z fokusem klawiatury będzie używany jako obiekt docelowy polecenia.  Jedną z korzyści wynikających z używania elementu z fokusem klawiatury jako obiektu docelowego polecenia jest umożliwienie deweloperowi aplikacji używania tego samego źródła poleceń do wywołania polecenia na wielu celach, bez konieczności śledzenia obiektu docelowego polecenia.  Na przykład jeśli <xref:System.Windows.Controls.MenuItem> wywoła polecenie **wklejenia** w aplikacji, która ma kontrolkę <xref:System.Windows.Controls.TextBox> i formant <xref:System.Windows.Controls.PasswordBox>, obiektem docelowym może być <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.PasswordBox> w zależności od tego, który formant ma fokus klawiatury.  
  
 Poniższy przykład pokazuje, jak jawnie ustawić obiekt docelowy polecenia w znacznikach i w kodzie.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>Polecenie CommandManager  
 @No__t-0 pełni wiele funkcji związanych z poleceniem.  Zawiera zestaw metod statycznych do dodawania i usuwania <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute> i <xref:System.Windows.Input.CommandManager.CanExecute> obsługi zdarzeń do i z określonego elementu.  Zapewnia to możliwość rejestrowania obiektów <xref:System.Windows.Input.CommandBinding> i <xref:System.Windows.Input.InputBinding> na określonej klasie.  @No__t-0 udostępnia również za pośrednictwem zdarzenia <xref:System.Windows.Input.CommandManager.RequerySuggested>, aby powiadomić polecenie o zdarzeniu <xref:System.Windows.Input.ICommand.CanExecuteChanged>.  
  
 Metoda <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> wymusza <xref:System.Windows.Input.CommandManager> w celu wywołania zdarzenia <xref:System.Windows.Input.CommandManager.RequerySuggested>.  Jest to przydatne w przypadku warunków, które powinny wyłączać/włączać polecenie, ale nie są to warunki, dla których <xref:System.Windows.Input.CommandManager>.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Biblioteka poleceń  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera zestaw wstępnie zdefiniowanych poleceń.  Biblioteka poleceń składa się z następujących klas: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands> i <xref:System.Windows.Input.ComponentCommands>.  Klasy te udostępniają polecenia, takie jak <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> i <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A> i <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Wiele z tych poleceń zawiera zestaw domyślnych powiązań wejściowych.  Na przykład jeśli określisz, że aplikacja obsługuje polecenie copy, automatycznie otrzymujesz powiązanie klawiatury "CTRL + C", uzyskasz także powiązania z innymi urządzeniami wejściowymi, takimi jak gesty pióra komputera typu tablet i informacje o mowy.  
  
 Podczas odwoływania się do poleceń w różnych bibliotekach poleceń przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] można zwykle pominąć nazwę klasy klasy biblioteki, która uwidacznia właściwość polecenia statycznego. Ogólnie rzecz biorąc, nazwy poleceń są niejednoznaczne jako ciągi i istnieją typy posiadające do zapewnienia logicznego grupowania poleceń, ale nie są niezbędne do uściślania. Na przykład można określić `Command="Cut"`, a nie więcej pełnych `Command="ApplicationCommands.Cut"`. Jest to wygodny mechanizm, który jest wbudowany w procesor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla poleceń (dokładniej, jest to zachowanie konwertera typów w <xref:System.Windows.Input.ICommand>, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odwołania procesora w czasie ładowania).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Tworzenie poleceń niestandardowych  
 Jeśli polecenia z klas biblioteki poleceń nie spełniają Twoich potrzeb, możesz utworzyć własne polecenia.  Istnieją dwa sposoby tworzenia polecenia niestandardowego.  Pierwszy jest początek od podstaw i implementuje interfejs <xref:System.Windows.Input.ICommand>.  Innym sposobem i bardziej typowym podejściem jest utworzenie <xref:System.Windows.Input.RoutedCommand> lub <xref:System.Windows.Input.RoutedUICommand>.  
  
 Przykład tworzenia niestandardowego <xref:System.Windows.Input.RoutedCommand> można znaleźć w temacie [Tworzenie niestandardowego przykładu RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Przegląd danych wejściowych](input-overview.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Implementowanie elementu ICommandSource](how-to-implement-icommandsource.md)
- [Instrukcje: Dodawanie polecenia do elementu MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Tworzenie niestandardowego przykładu RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
