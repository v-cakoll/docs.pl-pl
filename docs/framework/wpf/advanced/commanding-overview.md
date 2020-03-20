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
ms.openlocfilehash: 3477e6a9eda40edeadaab9cd6d3de2f016250fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186213"
---
# <a name="commanding-overview"></a>Przegląd Polecenia
<a name="introduction"></a>Polecenie jest mechanizmem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wejściowym, w którym zapewnia obsługę danych wejściowych na poziomie bardziej semantycznym niż wejście urządzenia. Przykładami poleceń są operacje **Kopiowania,** **Wycinania**i **Wklejania** znalezione w wielu aplikacjach.  
  
 W tym przeglądzie zdefiniowano, w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jakich poleceniach znajdują się , które klasy są częścią modelu dowodzenia oraz jak używać i tworzyć polecenia w aplikacjach.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Co to są polecenia?](#commands_at_10000_feet)  
  
- [Przykład prostego polecenia w wyw.](#simple_command)  
  
- [Cztery główne pojęcia w polecaniu WPF](#Four_main_Concepts)  
  
- [Biblioteka poleceń](#Command_Library)  
  
- [Tworzenie poleceń niestandardowych](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>
## <a name="what-are-commands"></a>Co to są polecenia?  
 Polecenia mają kilka celów. Pierwszym celem jest oddzielenie semantyki i obiektu, który wywołuje polecenie od logiki, która wykonuje polecenie. Dzięki temu dla wielu i różnych źródeł do wywoływania tej samej logiki polecenia i umożliwia logiki polecenia, które mają być dostosowane do różnych obiektów docelowych. Na przykład operacje edycji **Kopiuj,** **Wytnij**i **Wklej**, które znajdują się w wielu aplikacjach, można wywołać przy użyciu różnych akcji użytkownika, jeśli są one implementowane za pomocą poleceń. Aplikacja może zezwolić użytkownikowi na wycinanie zaznaczonych obiektów lub tekstu przez kliknięcie przycisku, wybranie elementu w menu lub użycie kombinacji klawiszy, takiej jak CTRL+X. Za pomocą poleceń, można powiązać każdy typ akcji użytkownika do tej samej logiki.  
  
 Innym celem poleceń jest wskazanie, czy akcja jest dostępna. Aby kontynuować przykład wycinania obiektu lub tekstu, akcja ma sens tylko wtedy, gdy coś jest zaznaczone. Jeśli użytkownik próbuje wyciąć obiekt lub tekst bez zaznaczenia czegokolwiek, nic się nie stanie. Aby wskazać to użytkownikowi, wiele aplikacji wyłącza przyciski i elementy menu, dzięki czemu użytkownik wie, czy można wykonać akcję. Polecenie może wskazać, czy akcja jest <xref:System.Windows.Input.ICommand.CanExecute%2A> możliwa przez zaimplementowanie metody. Przycisk może subskrybować <xref:System.Windows.Input.ICommand.CanExecuteChanged> zdarzenie i <xref:System.Windows.Input.ICommand.CanExecute%2A> być `false` wyłączony, jeśli <xref:System.Windows.Input.ICommand.CanExecute%2A> `true`zwraca lub być włączone, jeśli zwraca .  
  
 Semantyka polecenia może być spójne w aplikacjach i klasach, ale logika akcji jest specyficzna dla określonego obiektu, na który działał. Kombinacja klawiszy CTRL+X wywołuje polecenie **Wytnij** w klasach tekstu, klasach obrazów i przeglądarkach sieci Web, ale rzeczywista logika wykonywania operacji **Wytnij** jest definiowana przez aplikację, która wykonuje wycięcie. A <xref:System.Windows.Input.RoutedCommand> umożliwia klientom zaimplementowanie logiki. Obiekt tekstowy może wyciąć zaznaczony tekst do schowka, podczas gdy obiekt obrazu może wyciąć zaznaczony obraz. Gdy aplikacja obsługuje <xref:System.Windows.Input.CommandManager.Executed> zdarzenie, ma dostęp do obiektu docelowego polecenia i może podjąć odpowiednie działania w zależności od typu obiektu docelowego.  
  
<a name="simple_command"></a>
## <a name="simple-command-example-in-wpf"></a>Przykład prostego polecenia w wyw.  
 Najprostszym sposobem użycia polecenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w jest użycie wstępnie <xref:System.Windows.Input.RoutedCommand> zdefiniowane z jednej z klas biblioteki poleceń; użyj formantu, który ma natywną obsługę polecenia; i użyj formantu, który ma natywną obsługę wywoływania polecenia.  Polecenie <xref:System.Windows.Input.ApplicationCommands.Paste%2A> jest jednym ze wstępnie zdefiniowanych poleceń w <xref:System.Windows.Input.ApplicationCommands> klasie.  Formant <xref:System.Windows.Controls.TextBox> ma wbudowaną logikę <xref:System.Windows.Input.ApplicationCommands.Paste%2A> do obsługi polecenia.  Klasa <xref:System.Windows.Controls.MenuItem> ma natywną obsługę wywoływania poleceń.  
  
 Poniższy przykład pokazuje, jak <xref:System.Windows.Controls.MenuItem> skonfigurować tak, że po kliknięciu będzie <xref:System.Windows.Controls.TextBox>wywołać <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie na , przy założeniu, że ma fokus klawiatury.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>
## <a name="four-main-concepts-in-wpf-commanding"></a>Cztery główne pojęcia w polecaniu WPF  
 Kierowany model polecenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można podzielić na cztery główne pojęcia: polecenie, źródło polecenia, miejsce docelowe polecenia i powiązanie polecenia:  
  
- *Polecenie* jest akcją, która ma zostać wykonana.  
  
- *Źródło polecenia* jest obiektem, który wywołuje polecenie.  
  
- Obiekt *docelowy polecenia* jest obiektem, na który jest wykonywane polecenie.  
  
- Powiązanie *polecenia* jest obiektem, który mapuje logikę polecenia do polecenia.  
  
 W poprzednim przykładzie <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie jest poleceniem, <xref:System.Windows.Controls.MenuItem> jest źródłem polecenia, <xref:System.Windows.Controls.TextBox> jest obiektem docelowym <xref:System.Windows.Controls.TextBox> polecenia, a powiązanie polecenia jest dostarczane przez formant.  Warto zauważyć, że nie zawsze jest tak, że <xref:System.Windows.Input.CommandBinding> jest dostarczany przez formant, który jest klasą docelową polecenia.  Dość często <xref:System.Windows.Input.CommandBinding> musi być utworzony przez dewelopera aplikacji lub <xref:System.Windows.Input.CommandBinding> może być dołączony do obiektu nadrzędnego obiektu docelowego polecenia.  
  
<a name="Commands"></a>
### <a name="commands"></a>Polecenia  
 Polecenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są tworzone przez <xref:System.Windows.Input.ICommand> implementowanie interfejsu.  <xref:System.Windows.Input.ICommand>udostępnia dwie metody, <xref:System.Windows.Input.ICommand.Execute%2A> <xref:System.Windows.Input.ICommand.CanExecute%2A>i , i <xref:System.Windows.Input.ICommand.CanExecuteChanged>zdarzenie, . <xref:System.Windows.Input.ICommand.Execute%2A>wykonuje akcje skojarzone z poleceniem. <xref:System.Windows.Input.ICommand.CanExecute%2A>określa, czy polecenie może wykonać na bieżącym celu polecenia. <xref:System.Windows.Input.ICommand.CanExecuteChanged>jest wywoływana, jeśli menedżer poleceń, który centralizuje operacje polecenia, wykryje zmianę w źródle poleceń, która może unieważnić polecenie, które zostało podniesione, ale nie zostało jeszcze wykonane przez powiązanie polecenia.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Implementacja <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand> klasą i jest przedmiotem tego przeglądu.  
  
 Głównymi źródłami danych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wejściowych są myszy, klawiatury, pisma odmłkowego i poleceń routed.  Bardziej zorientowane na urządzenie <xref:System.Windows.RoutedEvent> dane wejściowe używają a do powiadamiania obiektów na stronie aplikacji o wystąpieniu zdarzenia wejściowego.  A <xref:System.Windows.Input.RoutedCommand> nie jest inaczej.  I <xref:System.Windows.Input.RoutedCommand.Execute%2A> <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody <xref:System.Windows.Input.RoutedCommand> a nie zawierają logiki aplikacji dla polecenia, ale raczej podnieść kierowane zdarzenia, które tunel <xref:System.Windows.Input.CommandBinding>i bańki przez drzewo elementów, dopóki nie napotkają obiektu z .  Zawiera <xref:System.Windows.Input.CommandBinding> programy obsługi dla tych zdarzeń i jest to programy obsługi, które wykonują polecenie.  Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]na temat routingu zdarzeń w programie , zobacz [Omówienie zdarzeń trasowych](routed-events-overview.md).  
  
 Metoda <xref:System.Windows.Input.RoutedCommand.Execute%2A> na <xref:System.Windows.Input.RoutedCommand> a wywołuje <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> zdarzenia na miejsce polecenia.  Metoda <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> na <xref:System.Windows.Input.RoutedCommand> a wywołuje <xref:System.Windows.Input.CommandManager.CanExecute> <xref:System.Windows.Input.CommandManager.PreviewCanExecute> zdarzenia i na miejsce docelowe polecenia.  Te zdarzenia tunelu i bańki przez drzewo elementów, dopóki nie napotkają obiektu, który ma <xref:System.Windows.Input.CommandBinding> dla danego polecenia.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dostarcza zestaw wspólnych kierowanych poleceń rozmieszczonych <xref:System.Windows.Input.MediaCommands> <xref:System.Windows.Input.ApplicationCommands>w <xref:System.Windows.Input.NavigationCommands> <xref:System.Windows.Input.ComponentCommands>kilku <xref:System.Windows.Documents.EditingCommands>klasach: , , , i .  Te klasy składają <xref:System.Windows.Input.RoutedCommand> się tylko z obiektów, a nie logiki implementacji polecenia.  Logika implementacji jest odpowiedzialny za obiekt, na którym polecenie jest wykonywane na.  
  
<a name="Command_Sources"></a>
### <a name="command-sources"></a>Źródła poleceń  
 Źródło polecenia jest obiektem, który wywołuje polecenie.  Przykładami źródeł poleceń <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.Button>są <xref:System.Windows.Input.KeyGesture>, i .  
  
 Źródła poleceń [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w ogólnie <xref:System.Windows.Input.ICommandSource> implementują interfejs.  
  
 <xref:System.Windows.Input.ICommandSource>eksponuje trzy <xref:System.Windows.Input.ICommandSource.Command%2A>właściwości: <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, , i :  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A>jest poleceniem do wykonania, gdy wywoływane jest źródło polecenia.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>jest obiektem, na którym ma wykonać polecenie.  Warto zauważyć, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> nieruchomości <xref:System.Windows.Input.ICommandSource> na ma <xref:System.Windows.Input.ICommand> zastosowanie <xref:System.Windows.Input.RoutedCommand>tylko wtedy, gdy jest .  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona <xref:System.Windows.Input.ICommandSource> na i odpowiednie <xref:System.Windows.Input.RoutedCommand>polecenie nie jest , cel polecenia jest ignorowany. Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> nie jest ustawiona, element z fokusem klawiatury będzie celem polecenia.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>jest typem danych zdefiniowanym przez użytkownika używanym do przekazywania informacji do programów obsługi implementujących polecenie.  
  
 Klasy, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] które <xref:System.Windows.Input.ICommandSource> <xref:System.Windows.Controls.Primitives.ButtonBase>implementują są , <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>i <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>i <xref:System.Windows.Documents.Hyperlink> wywołać polecenie po ich kliknięciu, <xref:System.Windows.Input.InputBinding> a polecenie <xref:System.Windows.Input.InputGesture> wywołuje polecenie, gdy skojarzone z nim jest wykonywane.  
  
 W poniższym <xref:System.Windows.Controls.MenuItem> przykładzie pokazano, <xref:System.Windows.Controls.ContextMenu> jak używać w <xref:System.Windows.Input.ApplicationCommands.Properties%2A> a jako źródło polecenia dla polecenia.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Zazwyczaj źródło polecenia będzie nasłuchiwać <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> zdarzenia.  To zdarzenie informuje źródło polecenia, że zdolność polecenia do wykonania na bieżącym celu polecenia może ulec zmianie.  Źródło polecenia może zbadać bieżący <xref:System.Windows.Input.RoutedCommand> stan <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> za pomocą metody.  Źródło polecenia może następnie wyłączyć się, jeśli polecenie nie może wykonać.  Przykładem <xref:System.Windows.Controls.MenuItem> tego jest siwienie się, gdy polecenie nie można wykonać.  
  
 Może <xref:System.Windows.Input.InputGesture> służyć jako źródło polecenia.  Dwa rodzaje gestów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wejściowych <xref:System.Windows.Input.KeyGesture> <xref:System.Windows.Input.MouseGesture>w są i .  Skrót klawiaturowy, <xref:System.Windows.Input.KeyGesture> taki jak CTRL+C, można potraktować jako skrót klawiaturowy.  A <xref:System.Windows.Input.KeyGesture> składa się <xref:System.Windows.Input.Key> z a <xref:System.Windows.Input.ModifierKeys>i zestaw .  A <xref:System.Windows.Input.MouseGesture> składa się <xref:System.Windows.Input.MouseAction> z a i <xref:System.Windows.Input.ModifierKeys>opcjonalnego zestawu .  
  
 Aby an <xref:System.Windows.Input.InputGesture> działał jako źródło poleceń, musi być skojarzony z poleceniem. Istnieje kilka sposobów, aby to osiągnąć.  Jednym ze sposobów <xref:System.Windows.Input.InputBinding>jest użycie .  
  
 W poniższym <xref:System.Windows.Input.KeyBinding> przykładzie pokazano, <xref:System.Windows.Input.KeyGesture> jak <xref:System.Windows.Input.RoutedCommand>utworzyć między a a .  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Innym <xref:System.Windows.Input.InputGesture> sposobem skojarzenia <xref:System.Windows.Input.RoutedCommand> z a <xref:System.Windows.Input.InputGesture> jest <xref:System.Windows.Input.InputGestureCollection> dodanie <xref:System.Windows.Input.RoutedCommand>do .  
  
 W poniższym przykładzie <xref:System.Windows.Input.KeyGesture> pokazano, <xref:System.Windows.Input.InputGestureCollection> jak <xref:System.Windows.Input.RoutedCommand>dodać a do .  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>
### <a name="commandbinding"></a>CommandBinding  
 A <xref:System.Windows.Input.CommandBinding> kojarzy polecenie z programami obsługi zdarzeń, które implementują polecenie.  
  
 Klasa <xref:System.Windows.Input.CommandBinding> zawiera <xref:System.Windows.Input.CommandBinding.Command%2A> właściwość <xref:System.Windows.Input.CommandBinding.PreviewExecuted>i <xref:System.Windows.Input.CommandBinding.Executed> <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, <xref:System.Windows.Input.CommandBinding.CanExecute> , i zdarzenia.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>jest poleceniem, <xref:System.Windows.Input.CommandBinding> z które jest skojarzone.  Programy obsługi zdarzeń, które są <xref:System.Windows.Input.CommandBinding.PreviewExecuted> <xref:System.Windows.Input.CommandBinding.Executed> dołączone do i zdarzenia implementują logikę polecenia.  Programy obsługi zdarzeń dołączone <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> do <xref:System.Windows.Input.CommandBinding.CanExecute> i zdarzenia określają, czy polecenie można wykonać na bieżącym docelowym poleceniu.  
  
 W poniższym <xref:System.Windows.Input.CommandBinding> przykładzie pokazano, <xref:System.Windows.Window> jak utworzyć w katalogu głównym aplikacji.  Kojarzy <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.ApplicationCommands.Open%2A> polecenie z <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.Input.CommandBinding.CanExecute> i obsługi.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Następnie są <xref:System.Windows.Input.ExecutedRoutedEventHandler> tworzone <xref:System.Windows.Input.CanExecuteRoutedEventHandler> i a.  Otwiera, <xref:System.Windows.Input.ExecutedRoutedEventHandler> <xref:System.Windows.MessageBox> który wyświetla ciąg mówiąc, że polecenie zostało wykonane.  Ustawia <xref:System.Windows.Input.CanExecuteRoutedEventHandler> <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> właściwość `true`na .  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> jest dołączony do określonego obiektu, <xref:System.Windows.Window> takich jak katalog główny aplikacji lub formantu.  Obiekt, który <xref:System.Windows.Input.CommandBinding> jest dołączony do definiuje zakres powiązania.  Na przykład <xref:System.Windows.Input.CommandBinding> dołączony do obiektu docelowego polecenia można osiągnąć <xref:System.Windows.Input.CommandBinding.Executed> przez zdarzenie, ale nie można osiągnąć <xref:System.Windows.Input.CommandBinding> dołączonego do obiektu podrzędnego obiektu docelowego polecenia.  Jest to bezpośrednia konsekwencja <xref:System.Windows.RoutedEvent> sposobu tunele i pęcherzyki z obiektu, który podnosi zdarzenie.  
  
 W niektórych <xref:System.Windows.Input.CommandBinding> sytuacjach jest dołączony do celu polecenia, <xref:System.Windows.Controls.TextBox> takich <xref:System.Windows.Input.ApplicationCommands.Cut%2A>jak <xref:System.Windows.Input.ApplicationCommands.Copy%2A>z <xref:System.Windows.Input.ApplicationCommands.Paste%2A> klasy i , , i poleceń. Dość często jednak wygodniej jest <xref:System.Windows.Input.CommandBinding> dołączyć do obiektu docelowego polecenia, <xref:System.Windows.Window> takiego jak główny lub application, zwłaszcza jeśli to samo <xref:System.Windows.Input.CommandBinding> może być używane dla wielu obiektów docelowych polecenia.  Są to decyzje projektowe, które należy wziąć pod uwagę podczas tworzenia infrastruktury dowodzącej.  
  
<a name="Commane_Target"></a>
### <a name="command-target"></a>Cel polecenia  
 Obiekt docelowy polecenia jest elementem, na którym polecenie jest wykonywane.  W odniesieniu <xref:System.Windows.Input.RoutedCommand>do , cel polecenia jest elementem, <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.Input.CommandManager.CanExecute> w którym routing i rozpoczyna.  Jak wspomniano wcześniej, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> w <xref:System.Windows.Input.ICommandSource> nieruchomości na ma <xref:System.Windows.Input.ICommand> zastosowanie <xref:System.Windows.Input.RoutedCommand>tylko wtedy, gdy jest .  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona <xref:System.Windows.Input.ICommandSource> na i odpowiednie <xref:System.Windows.Input.RoutedCommand>polecenie nie jest , cel polecenia jest ignorowany.  
  
 Źródło polecenia może jawnie ustawić miejsce docelowe polecenia.  Jeśli obiekt docelowy polecenia nie jest zdefiniowany, element z fokusem klawiatury będzie używany jako miejsce docelowe polecenia.  Jedną z zalet korzystania z elementu z fokusem klawiatury jako miejsce docelowe polecenia jest to, że umożliwia deweloperowi aplikacji używać tego samego źródła poleceń do wywoływania polecenia na wielu obiektów docelowych bez konieczności śledzenia obiektu docelowego polecenia.  Na przykład jeśli <xref:System.Windows.Controls.MenuItem> **wywołanie wklej** polecenie w aplikacji, która ma <xref:System.Windows.Controls.TextBox> formant i <xref:System.Windows.Controls.PasswordBox> formant, miejsce docelowe może być <xref:System.Windows.Controls.TextBox> albo <xref:System.Windows.Controls.PasswordBox> w zależności od tego, który formant ma fokus klawiatury.  
  
 W poniższym przykładzie pokazano, jak jawnie ustawić miejsce docelowe polecenia w znacznikach i w kodzie za.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>
### <a name="the-commandmanager"></a>Menedżer commandmanager  
 Służy <xref:System.Windows.Input.CommandManager> szereg funkcji związanych z poleceniami.  Zawiera zestaw metod statycznych do dodawania <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.Input.CommandManager.Executed>i <xref:System.Windows.Input.CommandManager.PreviewCanExecute>usuwania , i <xref:System.Windows.Input.CommandManager.CanExecute> obsługi zdarzeń do i z określonego elementu.  Zapewnia środki do <xref:System.Windows.Input.CommandBinding> rejestracji <xref:System.Windows.Input.InputBinding> i obiektów do określonej klasy.  Zapewnia <xref:System.Windows.Input.CommandManager> również środki, za <xref:System.Windows.Input.CommandManager.RequerySuggested> pośrednictwem zdarzenia, aby powiadomić <xref:System.Windows.Input.ICommand.CanExecuteChanged> polecenie, gdy powinno podnieść zdarzenie.  
  
 Metoda <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> wymusza <xref:System.Windows.Input.CommandManager> podnieść <xref:System.Windows.Input.CommandManager.RequerySuggested> zdarzenie.  Jest to przydatne w przypadku warunków, które powinny wyłączyć/włączyć polecenie, ale nie są warunki, które <xref:System.Windows.Input.CommandManager> jest świadomy.  
  
<a name="Command_Library"></a>
## <a name="command-library"></a>Biblioteka poleceń  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera zestaw wstępnie zdefiniowanych poleceń.  Biblioteka poleceń składa się <xref:System.Windows.Input.ApplicationCommands> <xref:System.Windows.Input.NavigationCommands>z <xref:System.Windows.Input.MediaCommands> <xref:System.Windows.Documents.EditingCommands>następujących klas: , , , i <xref:System.Windows.Input.ComponentCommands>.  Klasy te zawierają polecenia, <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>takie <xref:System.Windows.Input.MediaCommands.Play%2A> <xref:System.Windows.Input.MediaCommands.Stop%2A>jak <xref:System.Windows.Input.ApplicationCommands.Cut%2A> <xref:System.Windows.Input.MediaCommands.Pause%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> i , , i .  
  
 Wiele z tych poleceń zawiera zestaw domyślnych powiązań wejściowych.  Na przykład jeśli określisz, że aplikacja obsługuje polecenie kopiowania, automatycznie otrzymasz powiązanie klawiatury "CTRL+C" Otrzymasz również powiązania dla innych urządzeń wejściowych, takich jak gesty pióra komputera typu Tablet i informacje o mowie.  
  
 Podczas odwoływania się do poleceń [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]w różnych bibliotekach poleceń przy użyciu programu zwykle można pominąć nazwę klasy biblioteki, która udostępnia właściwość polecenia statycznego. Ogólnie rzecz biorąc nazwy poleceń są jednoznaczne jako ciągi, a typy będące właścicielem istnieją w celu zapewnienia logicznego grupowania poleceń, ale nie są konieczne do rozróżniania. Na przykład można `Command="Cut"` określić, a nie `Command="ApplicationCommands.Cut"`bardziej pełne . Jest to mechanizm wygody, który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest wbudowany w procesor dla poleceń (dokładniej, jest to zachowanie konwertera <xref:System.Windows.Input.ICommand>typu , którego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor odwołuje się w czasie ładowania).  
  
<a name="creating_commands"></a>
## <a name="creating-custom-commands"></a>Tworzenie poleceń niestandardowych  
 Jeśli polecenia w klasach biblioteki poleceń nie spełniają Twoich potrzeb, możesz utworzyć własne polecenia.  Istnieją dwa sposoby tworzenia polecenia niestandardowego.  Pierwszym z nich jest uruchomienie od <xref:System.Windows.Input.ICommand> podstaw i zaimplementowanie interfejsu.  Innym sposobem, a bardziej powszechne podejście, <xref:System.Windows.Input.RoutedCommand> jest <xref:System.Windows.Input.RoutedUICommand>stworzenie lub .  
  
 Na przykład tworzenia niestandardowego <xref:System.Windows.Input.RoutedCommand>, zobacz [Tworzenie niestandardowego routedcommand sample](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Przegląd Dane wejściowe](input-overview.md)
- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
- [Implementowanie elementu ICommandSource](how-to-implement-icommandsource.md)
- [Jak: Dodawanie polecenia do menuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Tworzenie niestandardowego przykładu kierowanego](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
