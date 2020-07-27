---
title: Przegląd Polecenia
description: Informacje o poleceniach, mechanizmie wejścia w Windows Presentation Foundation, który zapewnia obsługę danych wejściowych na wyższym poziomie semantycznym niż dane wejściowe urządzenia.
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
ms.openlocfilehash: 4f7d12fbf0de9b1546f15061ab7eb1318378bbbb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168117"
---
# <a name="commanding-overview"></a>Przegląd Polecenia
<a name="introduction"></a>Polecenie jest mechanizmem wprowadzania, w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] którym zapewnia obsługę wejścia na wyższym poziomie semantycznym niż dane wejściowe urządzenia. Przykładami poleceń są operacje **kopiowania**, **wycinania**i **wklejania** w wielu aplikacjach.  
  
 To omówienie określa, jakie polecenia znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , które klasy są częścią modelu poleceń i jak używać poleceń i tworzyć je w aplikacjach.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Co to są polecenia?](#commands_at_10000_feet)  
  
- [Proste przykładowe polecenie w WPF](#simple_command)  
  
- [Cztery główne koncepcje w przypadku poleceń WPF](#Four_main_Concepts)  
  
- [Biblioteka poleceń](#Command_Library)  
  
- [Tworzenie poleceń niestandardowych](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>
## <a name="what-are-commands"></a>Co to są polecenia?  
 Polecenia mają kilka zastosowań. Pierwszy cel polega na rozdzieleniu semantyki i obiektu, który wywołuje polecenie z logiki, która wykonuje polecenie. Pozwala to na wiele i różne źródła do wywołania tej samej logiki poleceń i umożliwia dostosowanie logiki poleceń dla różnych elementów docelowych. Na przykład operacje edycji **Kopiowanie**, **wycinanie**i **wklejanie**, które znajdują się w wielu aplikacjach, mogą być wywoływane przy użyciu różnych akcji użytkownika, jeśli są implementowane za pomocą poleceń. Aplikacja może zezwolić użytkownikowi na wycinanie wybranych obiektów lub tekstu przez kliknięcie przycisku, wybranie elementu w menu lub użycie kombinacji klawiszy, takiej jak CTRL + X. Za pomocą poleceń można powiązać poszczególne typy akcji użytkownika z tą samą logiką.  
  
 Innym celem poleceń jest wskazanie, czy akcja jest dostępna. Aby kontynuować przykład wycinania obiektu lub tekstu, akcja ma sens tylko wtedy, gdy coś jest zaznaczone. Jeśli użytkownik próbuje wyciąć obiekt lub tekst bez żadnych wybranych elementów, nic się nie stało. Aby wskazać to użytkownikowi, wiele aplikacji wyłącza przyciski i elementy menu, dzięki czemu użytkownik wie, czy można wykonać akcję. Polecenie może wskazywać, czy możliwe jest wykonanie akcji przez implementację <xref:System.Windows.Input.ICommand.CanExecute%2A> metody. Przycisk może subskrybować <xref:System.Windows.Input.ICommand.CanExecuteChanged> zdarzenie i zostać wyłączony, jeśli <xref:System.Windows.Input.ICommand.CanExecute%2A> zwraca `false` lub zostanie włączony, jeśli <xref:System.Windows.Input.ICommand.CanExecute%2A> zwraca wartość `true` .  
  
 Semantyka polecenia może być spójna w aplikacjach i klasach, ale logika akcji jest specyficzna dla konkretnego obiektu. Kombinacja klawiszy CTRL + X wywołuje polecenie **Wytnij** w klasach tekstowych, klasach obrazów i przeglądarkach sieci Web, ale rzeczywista logika wykonywania operacji **wycinania** jest definiowana przez aplikację wykonującą wycinanie. A <xref:System.Windows.Input.RoutedCommand> umożliwia klientom implementację logiki. Obiekt tekstowy może wyciąć zaznaczony tekst do schowka, podczas gdy obiekt obrazu może wyciąć wybrany obraz. Gdy aplikacja obsługuje <xref:System.Windows.Input.CommandManager.Executed> zdarzenie, ma dostęp do obiektu docelowego polecenia i może podejmować odpowiednie działania w zależności od typu elementu docelowego.  
  
<a name="simple_command"></a>
## <a name="simple-command-example-in-wpf"></a>Proste przykładowe polecenie w WPF  
 Najprostszym sposobem użycia polecenia w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest użycie wstępnie zdefiniowanego <xref:System.Windows.Input.RoutedCommand> z jednej z klas bibliotek poleceń; Użyj formantu, który ma natywną obsługę obsługi polecenia; i użyj formantu, który ma natywną obsługę wywoływania polecenia.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A>Polecenie jest jednym ze wstępnie zdefiniowanych poleceń w <xref:System.Windows.Input.ApplicationCommands> klasie.  <xref:System.Windows.Controls.TextBox>Formant ma wbudowaną logikę do obsługi <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenia.  I <xref:System.Windows.Controls.MenuItem> Klasa ma natywną obsługę Wywoływanie poleceń.  
  
 Poniższy przykład pokazuje, jak skonfigurować program, <xref:System.Windows.Controls.MenuItem> Aby po jego kliknięciu wywoła <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie na <xref:System.Windows.Controls.TextBox> , przy założeniu, że <xref:System.Windows.Controls.TextBox> ma fokus klawiatury.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>
## <a name="four-main-concepts-in-wpf-commanding"></a>Cztery główne koncepcje w przypadku poleceń WPF  
 Model polecenia kierowany w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można podzielić na cztery główne pojęcia: polecenie, źródło polecenia, obiekt docelowy polecenia i powiązanie poleceń:  
  
- *Polecenie* jest akcją do wykonania.  
  
- *Źródło polecenia* jest obiektem, który wywołuje polecenie.  
  
- *Element docelowy polecenia* jest obiektem, na którym jest wykonywane polecenie.  
  
- *Powiązanie polecenia* to obiekt, który mapuje logikę poleceń na polecenie.  
  
 W poprzednim przykładzie <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie jest poleceniem, <xref:System.Windows.Controls.MenuItem> jest źródłem polecenia, <xref:System.Windows.Controls.TextBox> jest elementem docelowym polecenia i powiązanie polecenia jest dostarczane przez <xref:System.Windows.Controls.TextBox> formant.  Należy zauważyć, że nie zawsze jest to przypadek, który <xref:System.Windows.Input.CommandBinding> jest dostarczany przez formant, który jest klasą docelową polecenia.  Bardzo często <xref:System.Windows.Input.CommandBinding> musi być utworzony przez dewelopera aplikacji lub <xref:System.Windows.Input.CommandBinding> może być dołączony do obiektu nadrzędnego polecenia.  
  
<a name="Commands"></a>
### <a name="commands"></a>Polecenia  
 Polecenia w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są tworzone przez implementację <xref:System.Windows.Input.ICommand> interfejsu.  <xref:System.Windows.Input.ICommand>uwidacznia dwie metody, <xref:System.Windows.Input.ICommand.Execute%2A> , i <xref:System.Windows.Input.ICommand.CanExecute%2A> i zdarzenie <xref:System.Windows.Input.ICommand.CanExecuteChanged> . <xref:System.Windows.Input.ICommand.Execute%2A>wykonuje akcje, które są skojarzone z poleceniem. <xref:System.Windows.Input.ICommand.CanExecute%2A>Określa, czy polecenie można wykonać na bieżącym obiekcie docelowym polecenia. <xref:System.Windows.Input.ICommand.CanExecuteChanged>jest zgłaszany, jeśli Menedżer poleceń, który służy do scentralizowania operacji wykonywania poleceń, wykrywa zmiany w źródle poleceń, które mogą unieważnić polecenie, które zostało podniesione, ale nie zostało jeszcze wykonane przez powiązanie polecenia.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Implementacja <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand> klasą i jest fokusem tego omówienia.  
  
 Główne źródła danych wejściowych w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to mysz, klawiatura, atrament i rozesłane polecenia.  Dodatkowe dane wejściowe zorientowane na urządzenia używają <xref:System.Windows.RoutedEvent> do powiadamiania obiektów na stronie aplikacji o wystąpieniu zdarzenia wejściowego.  A <xref:System.Windows.Input.RoutedCommand> nie różni się.  <xref:System.Windows.Input.RoutedCommand.Execute%2A>Metody i nie <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> <xref:System.Windows.Input.RoutedCommand> zawierają logiki aplikacji dla polecenia, ale raczej zgłaszają zdarzenia kierowane, które tuneluje i bąbelki przez drzewo elementów do momentu wystąpienia obiektu z <xref:System.Windows.Input.CommandBinding> .  <xref:System.Windows.Input.CommandBinding>Zawiera programy obsługi tych zdarzeń i jest obsługą, która wykonuje polecenie.  Aby uzyskać więcej informacji na temat routingu zdarzeń w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A>Metoda <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.CommandManager.PreviewExecuted> obiektu wywołuje i <xref:System.Windows.Input.CommandManager.Executed> zdarzenia w celu polecenia.  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A>Metoda na <xref:System.Windows.Input.RoutedCommand> wywołuje <xref:System.Windows.Input.CommandManager.CanExecute> <xref:System.Windows.Input.CommandManager.PreviewCanExecute> zdarzenia i w obiekcie docelowym polecenia.  Te zdarzenia są tunele i bąbelki przez drzewo elementów, dopóki nie napotkają obiektu <xref:System.Windows.Input.CommandBinding> , który ma dla danego polecenia.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dostarcza zestaw typowych poleceń kierowanych w ramach kilku klas:,,, <xref:System.Windows.Input.MediaCommands> <xref:System.Windows.Input.ApplicationCommands> <xref:System.Windows.Input.NavigationCommands> <xref:System.Windows.Input.ComponentCommands> i <xref:System.Windows.Documents.EditingCommands> .  Te klasy składają się tylko z <xref:System.Windows.Input.RoutedCommand> obiektów, a nie logiki implementacji polecenia.  Logika implementacji jest odpowiedzialna za obiekt, na którym polecenie jest wykonywane.  
  
<a name="Command_Sources"></a>
### <a name="command-sources"></a>Źródła poleceń  
 Źródło polecenia jest obiektem, który wywołuje polecenie.  Przykłady źródeł poleceń to <xref:System.Windows.Controls.MenuItem> , <xref:System.Windows.Controls.Button> , i <xref:System.Windows.Input.KeyGesture> .  
  
 Źródła poleceń [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ogólnie implementują <xref:System.Windows.Input.ICommandSource> interfejs.  
  
 <xref:System.Windows.Input.ICommandSource>uwidacznia trzy właściwości: <xref:System.Windows.Input.ICommandSource.Command%2A> , <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> i <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> :  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A>jest poleceniem do wykonania, gdy zostanie wywołane źródło polecenia.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>jest obiektem, na którym ma zostać wykonane polecenie.  Warto zauważyć, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Właściwość on <xref:System.Windows.Input.ICommandSource> jest stosowana tylko wtedy, gdy <xref:System.Windows.Input.ICommand> jest to <xref:System.Windows.Input.RoutedCommand> .  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona dla <xref:System.Windows.Input.ICommandSource> i odpowiednie polecenie nie jest <xref:System.Windows.Input.RoutedCommand> , obiekt docelowy polecenia jest ignorowany. Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> nie jest ustawiona, element z fokusem klawiatury będzie elementem docelowym polecenia.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>jest typem danych zdefiniowanym przez użytkownika, który służy do przekazywania informacji do programów obsługi implementujących polecenie.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Klasy, które implementują <xref:System.Windows.Input.ICommandSource> to,, <xref:System.Windows.Controls.Primitives.ButtonBase> <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Documents.Hyperlink> , i <xref:System.Windows.Input.InputBinding> .  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem> i <xref:System.Windows.Documents.Hyperlink> Wywołaj polecenie po kliknięciu i <xref:System.Windows.Input.InputBinding> wywołuje polecenie, gdy <xref:System.Windows.Input.InputGesture> jest wykonywane skojarzone z nim.  
  
 W poniższym przykładzie pokazano, jak używać <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ContextMenu> jako źródła poleceń polecenia <xref:System.Windows.Input.ApplicationCommands.Properties%2A> .  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Zazwyczaj źródło polecenia będzie nasłuchiwać <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> zdarzenia.  To zdarzenie informuje źródło polecenia, że możliwość wykonania polecenia w bieżącym obiekcie docelowym polecenia mogła ulec zmianie.  Źródło polecenia może wysyłać zapytania do bieżącego stanu przy <xref:System.Windows.Input.RoutedCommand> użyciu <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody.  Źródło polecenia może następnie wyłączyć, jeśli polecenie nie może zostać wykonane.  Przykładem jest <xref:System.Windows.Controls.MenuItem> szare wyjście, gdy polecenie nie może zostać wykonane.  
  
 <xref:System.Windows.Input.InputGesture>Może służyć jako źródło polecenia.  Dwa typy gestów wejścia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to <xref:System.Windows.Input.KeyGesture> i <xref:System.Windows.Input.MouseGesture> .  Można traktować <xref:System.Windows.Input.KeyGesture> jako skrót klawiaturowy, taki jak Ctrl + C.  A <xref:System.Windows.Input.KeyGesture> składa się z <xref:System.Windows.Input.Key> i zestawu <xref:System.Windows.Input.ModifierKeys> .  A <xref:System.Windows.Input.MouseGesture> składa się z <xref:System.Windows.Input.MouseAction> i opcjonalnego zestawu <xref:System.Windows.Input.ModifierKeys> .  
  
 <xref:System.Windows.Input.InputGesture>Aby obiekt działał jako źródło polecenia, musi być skojarzony z poleceniem. Istnieje kilka sposobów, aby to zrobić.  Jednym ze sposobów jest użycie <xref:System.Windows.Input.InputBinding> .  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Input.KeyBinding> między <xref:System.Windows.Input.KeyGesture> a i <xref:System.Windows.Input.RoutedCommand> .  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Innym sposobem skojarzenia elementu <xref:System.Windows.Input.InputGesture> a <xref:System.Windows.Input.RoutedCommand> jest dodanie <xref:System.Windows.Input.InputGesture> do elementu <xref:System.Windows.Input.InputGestureCollection> w <xref:System.Windows.Input.RoutedCommand> .  
  
 Poniższy przykład pokazuje, jak dodać a <xref:System.Windows.Input.KeyGesture> do <xref:System.Windows.Input.InputGestureCollection> <xref:System.Windows.Input.RoutedCommand> .  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>
### <a name="commandbinding"></a>CommandBinding  
 A <xref:System.Windows.Input.CommandBinding> kojarzy polecenie z obsługą zdarzeń implementującą polecenie.  
  
 <xref:System.Windows.Input.CommandBinding>Klasa zawiera <xref:System.Windows.Input.CommandBinding.Command%2A> Właściwość, i,, <xref:System.Windows.Input.CommandBinding.PreviewExecuted> <xref:System.Windows.Input.CommandBinding.Executed> <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> i <xref:System.Windows.Input.CommandBinding.CanExecute> zdarzenia.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>jest poleceniem, <xref:System.Windows.Input.CommandBinding> z którym jest skojarzony.  Programy obsługi zdarzeń dołączone do <xref:System.Windows.Input.CommandBinding.PreviewExecuted> <xref:System.Windows.Input.CommandBinding.Executed> zdarzeń i implementują logikę poleceń.  Programy obsługi zdarzeń dołączone do <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> <xref:System.Windows.Input.CommandBinding.CanExecute> zdarzeń i określają, czy polecenie można wykonać na bieżącym obiekcie docelowym polecenia.  
  
 Poniższy przykład pokazuje, jak utworzyć element <xref:System.Windows.Input.CommandBinding> w katalogu głównym <xref:System.Windows.Window> aplikacji.  <xref:System.Windows.Input.CommandBinding>Kojarzy <xref:System.Windows.Input.ApplicationCommands.Open%2A> polecenie z <xref:System.Windows.Input.CommandManager.Executed> programami i <xref:System.Windows.Input.CommandBinding.CanExecute> .  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Następnie <xref:System.Windows.Input.ExecutedRoutedEventHandler> <xref:System.Windows.Input.CanExecuteRoutedEventHandler> tworzone są i.  <xref:System.Windows.Input.ExecutedRoutedEventHandler>Otwiera a zostanie <xref:System.Windows.MessageBox> wyświetlony ciąg informujący, że polecenie zostało wykonane.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler>Ustawia <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> Właściwość na `true` .  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> jest dołączony do określonego obiektu, takiego jak katalog główny <xref:System.Windows.Window> aplikacji lub formantu.  Obiekt, do którego <xref:System.Windows.Input.CommandBinding> jest dołączony, definiuje zakres powiązania.  Na przykład, <xref:System.Windows.Input.CommandBinding> dołączone do elementu nadrzędnego elementu docelowego polecenia można osiągnąć przez <xref:System.Windows.Input.CommandBinding.Executed> zdarzenie, ale <xref:System.Windows.Input.CommandBinding> nie można osiągnąć dołączonego elementu podrzędnego obiektu docelowego polecenia.  Jest to bezpośrednia konsekwencja sposobu, w jaki <xref:System.Windows.RoutedEvent> tunele i bąbelki z obiektu, który wywołuje zdarzenie.  
  
 W niektórych sytuacjach <xref:System.Windows.Input.CommandBinding> jest dołączony do samego obiektu docelowego polecenia, na przykład z <xref:System.Windows.Controls.TextBox> klasą i <xref:System.Windows.Input.ApplicationCommands.Cut%2A> <xref:System.Windows.Input.ApplicationCommands.Copy%2A> <xref:System.Windows.Input.ApplicationCommands.Paste%2A> poleceniami, i. Dość często zdarza się, aby dołączyć <xref:System.Windows.Input.CommandBinding> do elementu nadrzędnego polecenia, takiego jak główny <xref:System.Windows.Window> lub obiekt aplikacji, zwłaszcza jeśli <xref:System.Windows.Input.CommandBinding> można użyć tego samego polecenia dla wielu obiektów docelowych poleceń.  Są to decyzje projektowe, które należy wziąć pod uwagę podczas tworzenia infrastruktury poleceń.  
  
<a name="Commane_Target"></a>
### <a name="command-target"></a>Element docelowy polecenia  
 Obiekt docelowy polecenia jest elementem, w którym polecenie jest wykonywane.  W odniesieniu do <xref:System.Windows.Input.RoutedCommand> , obiekt docelowy polecenia jest elementem, w którym Routing <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandManager.CanExecute> rozpoczyna się.  Jak wspomniano wcześniej, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] we <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Właściwości on <xref:System.Windows.Input.ICommandSource> ma zastosowanie tylko wtedy, gdy <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand> .  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona dla <xref:System.Windows.Input.ICommandSource> i odpowiednie polecenie nie jest <xref:System.Windows.Input.RoutedCommand> , obiekt docelowy polecenia jest ignorowany.  
  
 Źródło polecenia może jawnie ustawić element docelowy polecenia.  Jeśli obiekt docelowy polecenia nie jest zdefiniowany, element z fokusem klawiatury będzie używany jako obiekt docelowy polecenia.  Jedną z korzyści wynikających z używania elementu z fokusem klawiatury jako obiektu docelowego polecenia jest umożliwienie deweloperowi aplikacji używania tego samego źródła poleceń do wywołania polecenia na wielu celach, bez konieczności śledzenia obiektu docelowego polecenia.  Na przykład jeśli <xref:System.Windows.Controls.MenuItem> wywołuje polecenie **wklejenia** w aplikacji, która ma <xref:System.Windows.Controls.TextBox> kontrolkę i <xref:System.Windows.Controls.PasswordBox> kontrolkę, obiektem docelowym może być albo w <xref:System.Windows.Controls.TextBox> zależności od tego, <xref:System.Windows.Controls.PasswordBox> który formant ma fokus klawiatury.  
  
 Poniższy przykład pokazuje, jak jawnie ustawić obiekt docelowy polecenia w znacznikach i w kodzie.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>
### <a name="the-commandmanager"></a>Polecenie CommandManager  
 Wykonuje <xref:System.Windows.Input.CommandManager> wiele funkcji związanych z poleceniem.  Zawiera zestaw metod statycznych do dodawania i usuwania <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.Input.CommandManager.PreviewCanExecute> <xref:System.Windows.Input.CommandManager.CanExecute> programów obsługi zdarzeń oraz do i z określonego elementu.  Umożliwia ona rejestrowanie <xref:System.Windows.Input.CommandBinding> i <xref:System.Windows.Input.InputBinding> obiekty w określonej klasie.  <xref:System.Windows.Input.CommandManager>Udostępnia również środki, <xref:System.Windows.Input.CommandManager.RequerySuggested> aby powiadomić polecenie o zdarzeniu <xref:System.Windows.Input.ICommand.CanExecuteChanged> .  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A>Metoda wymusza wygenerowanie <xref:System.Windows.Input.CommandManager> <xref:System.Windows.Input.CommandManager.RequerySuggested> zdarzenia.  Jest to przydatne w przypadku warunków, które powinny wyłączać/włączać polecenie, ale nie są to warunki, o których należy <xref:System.Windows.Input.CommandManager> wiedzieć.  
  
<a name="Command_Library"></a>
## <a name="command-library"></a>Biblioteka poleceń  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia zestaw wstępnie zdefiniowanych poleceń.  Biblioteka poleceń składa się z następujących klas: <xref:System.Windows.Input.ApplicationCommands> , <xref:System.Windows.Input.NavigationCommands> , <xref:System.Windows.Input.MediaCommands> , <xref:System.Windows.Documents.EditingCommands> i <xref:System.Windows.Input.ComponentCommands> .  Klasy te udostępniają polecenia, takie jak <xref:System.Windows.Input.ApplicationCommands.Cut%2A> , <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> i <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A> ,, <xref:System.Windows.Input.MediaCommands.Play%2A> <xref:System.Windows.Input.MediaCommands.Stop%2A> i <xref:System.Windows.Input.MediaCommands.Pause%2A> .  
  
 Wiele z tych poleceń zawiera zestaw domyślnych powiązań wejściowych.  Na przykład jeśli określisz, że aplikacja obsługuje polecenie copy, automatycznie otrzymujesz powiązanie klawiatury "CTRL + C", uzyskasz także powiązania z innymi urządzeniami wejściowymi, takimi jak gesty pióra komputera typu tablet i informacje o mowy.  
  
 Podczas odwoływania się do poleceń w różnych bibliotekach poleceń przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , można zwykle pominąć nazwę klasy klasy biblioteki, która uwidacznia właściwość polecenia statycznego. Ogólnie rzecz biorąc, nazwy poleceń są niejednoznaczne jako ciągi i istnieją typy posiadające do zapewnienia logicznego grupowania poleceń, ale nie są niezbędne do uściślania. Na przykład można określić, `Command="Cut"` a nie pełne `Command="ApplicationCommands.Cut"` . Jest to wygodny mechanizm, który jest wbudowany w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor dla poleceń (dokładniej, jest to zachowanie konwertera typów, które jest używane <xref:System.Windows.Input.ICommand> przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor w czasie ładowania).  
  
<a name="creating_commands"></a>
## <a name="creating-custom-commands"></a>Tworzenie poleceń niestandardowych  
 Jeśli polecenia z klas biblioteki poleceń nie spełniają Twoich potrzeb, możesz utworzyć własne polecenia.  Istnieją dwa sposoby tworzenia polecenia niestandardowego.  Pierwszy z nich zaczyna się od podstaw i implementuje <xref:System.Windows.Input.ICommand> interfejs.  Innym sposobem i bardziej typowym podejściem jest utworzenie <xref:System.Windows.Input.RoutedCommand> lub <xref:System.Windows.Input.RoutedUICommand> .  
  
 Aby zapoznać się z przykładem tworzenia niestandardowego <xref:System.Windows.Input.RoutedCommand> , zobacz [Tworzenie niestandardowego przykładu RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Przegląd Dane wejściowe](input-overview.md)
- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
- [Implementowanie elementu ICommandSource](how-to-implement-icommandsource.md)
- [Instrukcje: Dodawanie polecenia do elementu MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Tworzenie niestandardowego przykładu RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
