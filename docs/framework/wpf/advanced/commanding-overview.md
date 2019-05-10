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
ms.openlocfilehash: 835b06c6107cd44d49c83cfe34102b0c2d2a4bb9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627396"
---
# <a name="commanding-overview"></a>Przegląd Polecenia
<a name="introduction"></a> Polecenia jest mechanizm danych wejściowych w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępniającej dane wejściowe Obsługa na poziomie semantycznego więcej niż dane wejściowe z urządzenia. Przykłady poleceń **kopiowania**, **Wytnij**, i **Wklej** odnaleźć operacji na wielu aplikacji.  
  
 W tym omówieniu definiuje, jakie polecenia znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], klas, które są częścią modelu sterująca i sposobie używania i tworzenia poleceń w aplikacjach.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Co to są polecenia?](#commands_at_10000_feet)  
  
- [Przykład prostego polecenia na platformie WPF](#simple_command)  
  
- [Cztery główne pojęcia dotyczące polecenia WPF](#Four_main_Concepts)  
  
- [Biblioteka poleceń](#Command_Library)  
  
- [Tworzenie niestandardowych poleceń](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Co to są polecenia?  
 Polecenia mają wiele celów. Pierwszy ma na celu oddzielenia semantyka i obiekt, który wywołuje polecenie od logiki, która wykonuje polecenie. Dzięki temu wielu i różnych źródeł, aby wywołać tę samą logikę polecenia, a umożliwia logikę polecenia i być dostosowane do różnych celów. Na przykład operacje edycji **kopiowania**, **Wytnij**, i **Wklej**, które znajdują się w wielu aplikacjach, może być wywoływany przy użyciu różnych działań użytkownika, jeśli są one zaimplementowane przy użyciu poleceń. Aplikacja może zezwolić użytkownikowi na Wytnij zaznaczonych obiektów lub tekstu, klikając przycisk, wybierając element menu lub za pomocą kombinacji klawiszy, takie jak CTRL + X. Za pomocą poleceń, można powiązać tę samą logikę każdego typu akcji przez użytkownika.  
  
 Inny poleceń ma na celu wskazania, czy akcja jest dostępna. Aby kontynuować przykład wycinania obiektu lub tekstu, akcja tylko sens, gdy coś jest zaznaczone. Jeśli użytkownik próbuje wycinania obiektu lub tekstu bez żadnych wybrane, nic się stanie. Wiele aplikacji jest wskaż, to dla użytkownika, Wyłącz elementy menu i przycisków tak, aby użytkownik wie, czy jest możliwe do wykonania akcji. Polecenia można wskazać, czy akcja jest możliwe dzięki wdrożeniu <xref:System.Windows.Input.ICommand.CanExecute%2A> metody. Może być subskrybowana przez przycisk <xref:System.Windows.Input.ICommand.CanExecuteChanged> zdarzeń i go wyłączyć, jeżeli <xref:System.Windows.Input.ICommand.CanExecute%2A> zwraca `false` lub włączona, jeśli <xref:System.Windows.Input.ICommand.CanExecute%2A> zwraca `true`.  
  
 Semantykę polecenie może być zgodne, obejmujących wiele aplikacji i klasy, ale logikę działania jest specyficzny dla określonego obiektu podjęte. Kombinacja klawiszy CTRL + X wywołuje **Wytnij** w tekst klasy, klasy obrazu i przeglądarki sieci Web, ale logikę wykonywania polecenie **Wytnij** operacji jest zdefiniowany przez aplikację, która wykonuje Wytnij. A <xref:System.Windows.Input.RoutedCommand> umożliwia klientom implementują logikę. Obiekt tekstowy może Wytnij zaznaczonego tekstu do Schowka, podczas gdy obiekt obrazu mogą być obcięte wybranego obrazu. Gdy aplikacja zajmuje się <xref:System.Windows.Input.CommandManager.Executed> zdarzeń, ma dostęp do elementu docelowego polecenia i mogą podjąć odpowiednie działania w zależności od typu elementu docelowego.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>Przykład prostego polecenia na platformie WPF  
 Najprostszym sposobem użycia polecenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma użyć wstępnie zdefiniowanej <xref:System.Windows.Input.RoutedCommand> z jednej z klas biblioteki polecenia; używać formant, który zapewnia natywną obsługę obsługi polecenia; i formant, który zapewnia natywną obsługę wywoływania polecenia.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> Polecenie jest jedno z poleceń wstępnie zdefiniowanych w <xref:System.Windows.Input.ApplicationCommands> klasy.  <xref:System.Windows.Controls.TextBox> Kontroli ma wbudowane logikę obsługi <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenia.  I <xref:System.Windows.Controls.MenuItem> klasy zapewnia natywną obsługę wywoływania poleceń.  
  
 Poniższy przykład pokazuje, jak skonfigurować <xref:System.Windows.Controls.MenuItem> tak, aby po kliknięciu wywoła <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie <xref:System.Windows.Controls.TextBox>, przyjmuje <xref:System.Windows.Controls.TextBox> ma fokus klawiatury.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>Cztery główne pojęcia dotyczące polecenia WPF  
 Model trasowane polecenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może zostać podzielony na cztery główne pojęcia: polecenie, źródło polecenia, element docelowy polecenia i powiązanie polecenia:  
  
- *Polecenia* jest akcja do wykonania.  
  
- *Źródło polecenia* jest obiekt, który wywołuje polecenie.  
  
- *Elemencie docelowym polecenia* to polecenie jest wykonywane na obiekt.  
  
- *Polecenia powiązania* jest obiekt, który mapuje polecenia logikę do polecenia.  
  
 W poprzednim przykładzie <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenia jest poleceniem, <xref:System.Windows.Controls.MenuItem> jest źródłem polecenia <xref:System.Windows.Controls.TextBox> jest miejscem docelowym polecenia i powiązanie polecenia jest dostarczana przez <xref:System.Windows.Controls.TextBox> kontroli.  Warto zauważyć, że nie zawsze jest przypadek, <xref:System.Windows.Input.CommandBinding> jest dostarczana przez formant który jest Klasa docelowa polecenia.  Bardzo często <xref:System.Windows.Input.CommandBinding> musi zostać utworzona przez dewelopera aplikacji lub <xref:System.Windows.Input.CommandBinding> może zostać dołączony do elementu nadrzędnego w elemencie docelowym polecenia.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Polecenia  
 Polecenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są tworzone przez zaimplementowanie <xref:System.Windows.Input.ICommand> interfejsu.  <xref:System.Windows.Input.ICommand> udostępnia dwie metody <xref:System.Windows.Input.ICommand.Execute%2A>, i <xref:System.Windows.Input.ICommand.CanExecute%2A>, a zdarzenia, <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A> wykonuje akcje, które są skojarzone z poleceniem. <xref:System.Windows.Input.ICommand.CanExecute%2A> Określa, czy polecenie może być wykonane na aktualnym elemencie docelowym polecenia. <xref:System.Windows.Input.ICommand.CanExecuteChanged> jest wywoływane, gdy Menedżer poleceń, który umożliwia scentralizowanie sterująca operacje wykryje zmianę w źródle polecenia, które może unieważnić polecenie, które zostały zgłoszone, ale nie zostały jeszcze wykonane przez powiązanie polecenia.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Implementacji <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand> klasy i skupia się z omówieniem tego zagadnienia.  
  
 Główne źródła danych wejściowych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] myszy, klawiatury, pisma odręcznego i trasowane poleceń.  Użyj danych wejściowych więcej zorientowane na urządzenia <xref:System.Windows.RoutedEvent> do powiadamiania obiekty na stronie aplikacji, które wystąpiło zdarzenie wejściowe.  Element <xref:System.Windows.Input.RoutedCommand> nie różni się.  <xref:System.Windows.Input.RoutedCommand.Execute%2A> i <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody <xref:System.Windows.Input.RoutedCommand> nie zawiera logiki aplikacji w poleceniu, ale zamiast zgłaszać zdarzenia trasowane tunelowane i będą się pojawiać za pośrednictwem drzewa elementów do momentu oni natrafić, za pomocą obiektu <xref:System.Windows.Input.CommandBinding>.  <xref:System.Windows.Input.CommandBinding> Zawiera programy obsługi dla tych zdarzeń i obsługi, które wykonuje polecenie.  Aby uzyskać więcej informacji na temat routingu w zdarzeń [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Przegląd zdarzeń kierowane](routed-events-overview.md).  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A> Metody <xref:System.Windows.Input.RoutedCommand> zgłasza <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> zdarzeń w elemencie docelowym polecenia.  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> Metody <xref:System.Windows.Input.RoutedCommand> zgłasza <xref:System.Windows.Input.CommandManager.CanExecute> i <xref:System.Windows.Input.CommandManager.PreviewCanExecute> zdarzeń w elemencie docelowym polecenia.  Te zdarzenia tunel i bąbelkowych za pośrednictwem drzewa elementów do czasu napotkania obiektu, który ma <xref:System.Windows.Input.CommandBinding> na tym konkretnym poleceniem.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dostarcza zestaw typowych poleceń trasowane rozkładają się na kilka klas: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands>, i <xref:System.Windows.Documents.EditingCommands>.  W ramach tych zajęć składają się tylko z <xref:System.Windows.Input.RoutedCommand> obiektów i nie logika wykonania polecenia.  Logika implementacji odpowiada obiektu, na którym polecenie jest wykonywane na.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Polecenie źródeł  
 Źródło polecenia jest obiekt, który wywołuje polecenie.  Polecenie źródeł należą do nich <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button>, i <xref:System.Windows.Input.KeyGesture>.  
  
 Polecenie źródeł w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji ogólnie <xref:System.Windows.Input.ICommandSource> interfejsu.  
  
 <xref:System.Windows.Input.ICommandSource> udostępnia trzy właściwości: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, i <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A> to polecenie do wykonania, gdy źródło polecenia zostanie wywołana.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest to obiekt, w którym można wykonać polecenia.  Warto zauważyć, że w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> właściwość <xref:System.Windows.Input.ICommandSource> dotyczy tylko kiedy <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand>.  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona na <xref:System.Windows.Input.ICommandSource> i odpowiednie polecenie nie jest <xref:System.Windows.Input.RoutedCommand>, jest ignorowana w elemencie docelowym polecenia. Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> nie jest ustawiony, element z fokusem klawiatury będą w elemencie docelowym polecenia.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> Typ danych zdefiniowany przez użytkownika używany do przekazywania informacji do obsługi implementuje polecenie.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Klas, które implementują <xref:System.Windows.Input.ICommandSource> są <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>, i <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, i <xref:System.Windows.Documents.Hyperlink> Wywołaj polecenie, po ich kliknięciu i moduł <xref:System.Windows.Input.InputBinding> wywołuje polecenie po <xref:System.Windows.Input.InputGesture> skojarzone z jest wykonywane.  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.MenuItem> w <xref:System.Windows.Controls.ContextMenu> jako źródło polecenia <xref:System.Windows.Input.ApplicationCommands.Properties%2A> polecenia.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Zazwyczaj będzie nasłuchiwać źródło polecenia <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> zdarzeń.  To zdarzenie informuje źródła polecenia, które mogły ulec zmianie możliwości polecenia do wykonania w bieżącym elemencie docelowym polecenia.  Źródło polecenia mogą wysyłać zapytania o bieżącym stanie <xref:System.Windows.Input.RoutedCommand> przy użyciu <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody.  Źródło polecenia można następnie sam się wyłączy Jeśli nie można wykonać polecenia.  Na przykład <xref:System.Windows.Controls.MenuItem> graying sam się, gdy nie można wykonać polecenia.  
  
 <xref:System.Windows.Input.InputGesture> Mogą być używane jako źródło polecenia.  Dwa typy wejściowe gestów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są <xref:System.Windows.Input.KeyGesture> i <xref:System.Windows.Input.MouseGesture>.  Można potraktować <xref:System.Windows.Input.KeyGesture> skrótu klawiaturowego, takie jak CTRL + C.  A <xref:System.Windows.Input.KeyGesture> składa się z <xref:System.Windows.Input.Key> oraz zestaw <xref:System.Windows.Input.ModifierKeys>.  A <xref:System.Windows.Input.MouseGesture> składa się z <xref:System.Windows.Input.MouseAction> i opcjonalny zestaw <xref:System.Windows.Input.ModifierKeys>.  
  
 Aby <xref:System.Windows.Input.InputGesture> do działania jako źródło polecenia, muszą być skojarzone z poleceniem. Istnieje kilka sposobów, w tym celu.  Jednym ze sposobów jest użycie <xref:System.Windows.Input.InputBinding>.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Input.KeyBinding> między <xref:System.Windows.Input.KeyGesture> i <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Innym sposobem, aby skojarzyć <xref:System.Windows.Input.InputGesture> do <xref:System.Windows.Input.RoutedCommand> jest dodanie <xref:System.Windows.Input.InputGesture> do <xref:System.Windows.Input.InputGestureCollection> na <xref:System.Windows.Input.RoutedCommand>.  
  
 Poniższy przykład pokazuje, jak dodać <xref:System.Windows.Input.KeyGesture> do <xref:System.Windows.Input.InputGestureCollection> z <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 A <xref:System.Windows.Input.CommandBinding> kojarzy polecenie z programami obsługi zdarzeń, które implementują polecenia.  
  
 <xref:System.Windows.Input.CommandBinding> Klasa zawiera <xref:System.Windows.Input.CommandBinding.Command%2A> właściwości i <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, i <xref:System.Windows.Input.CommandBinding.CanExecute> zdarzenia.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> jest poleceniem, który <xref:System.Windows.Input.CommandBinding> jest skojarzona z.  Programy obsługi zdarzeń, które są dołączone do <xref:System.Windows.Input.CommandBinding.PreviewExecuted> i <xref:System.Windows.Input.CommandBinding.Executed> zdarzenia implementują logikę polecenia.  Programy obsługi zdarzeń dołączonych do <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> i <xref:System.Windows.Input.CommandBinding.CanExecute> zdarzenia decydują, jeśli polecenie można wykonać na aktualnym elemencie docelowym polecenia.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Input.CommandBinding> w katalogu głównym <xref:System.Windows.Window> aplikacji.  <xref:System.Windows.Input.CommandBinding> Kojarzy <xref:System.Windows.Input.ApplicationCommands.Open%2A> polecenia <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandBinding.CanExecute> programów obsługi.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Następnie <xref:System.Windows.Input.ExecutedRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> są tworzone.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Otwiera <xref:System.Windows.MessageBox> wyświetlającą ciąg informujący o tym polecenia została wykonana.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Ustawia <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> właściwość `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> jest dołączona do określonego obiektu, takie jak katalog główny <xref:System.Windows.Window> aplikacja lub formant.  Obiekt, <xref:System.Windows.Input.CommandBinding> jest dołączony do definiuje zakres wiązania.  Na przykład <xref:System.Windows.Input.CommandBinding> dołączony do elementu nadrzędnego polecenie docelowy jest osiągalna <xref:System.Windows.Input.CommandBinding.Executed> zdarzeń, ale <xref:System.Windows.Input.CommandBinding> dołączony do obiektu podrzędnego, polecenia docelowy jest nieosiągalny.  Jest bezpośrednim skutkiem sposób <xref:System.Windows.RoutedEvent> tunele i bąbelki od obiektu, który wywołuje zdarzenie.  
  
 W niektórych sytuacjach <xref:System.Windows.Input.CommandBinding> jest dołączony do docelowego polecenia, takie jak za pomocą <xref:System.Windows.Controls.TextBox> klasy i <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, i <xref:System.Windows.Input.ApplicationCommands.Paste%2A> poleceń. Dość często jest bardziej wygodne dołączyć <xref:System.Windows.Input.CommandBinding> do elementu nadrzędnego w elemencie docelowym polecenia, takie jak główny <xref:System.Windows.Window> lub w obiekcie aplikacji zwłaszcza wtedy, gdy taka sama <xref:System.Windows.Input.CommandBinding> może służyć do wielu obiekty docelowe poleceń.  Są to należy wziąć pod uwagę podczas tworzenia sterująca infrastruktury decyzji projektowych.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Elemencie docelowym polecenia  
 Element docelowy polecenia jest element wykonywania polecenia.  W odniesieniu do <xref:System.Windows.Input.RoutedCommand>, element docelowy polecenia jest elementem, na które routing <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandManager.CanExecute> rozpoczyna się.  Jak wspomniano wcześniej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> właściwość <xref:System.Windows.Input.ICommandSource> dotyczy tylko kiedy <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand>.  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona na <xref:System.Windows.Input.ICommandSource> i odpowiednie polecenie nie jest <xref:System.Windows.Input.RoutedCommand>, jest ignorowana w elemencie docelowym polecenia.  
  
 Źródło polecenia można jawnie ustawić w elemencie docelowym polecenia.  Jeśli element docelowy polecenia nie jest zdefiniowany, element z fokusem klawiatury będzie służyć jako element docelowy polecenia.  Jedną z korzyści z używania element z fokusem klawiatury, jako element docelowy polecenia jest możliwość dla deweloperów aplikacji do użycia tego samego źródła polecenie do wywołania polecenia w wielu lokalizacjach docelowych bez informacji o elemencie docelowym polecenia.  Na przykład jeśli <xref:System.Windows.Controls.MenuItem> wywołuje **Wklej** polecenia w aplikacji, która ma <xref:System.Windows.Controls.TextBox> kontroli i <xref:System.Windows.Controls.PasswordBox> formant, element docelowy może być albo <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.PasswordBox> zależności od Kontrolka ma fokus klawiatury.  
  
 Poniższy przykład przedstawia sposób jawnego ustawienia celu polecenia, w znacznikach i w kodzie.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>CommandManager  
 <xref:System.Windows.Input.CommandManager> Służy na numer polecenia powiązanych z funkcji.  Udostępnia zestaw metod statycznych do dodawania i usuwania <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>, i <xref:System.Windows.Input.CommandManager.CanExecute> procedury obsługi zdarzeń do i z określonego elementu.  Zapewnia środek do zarejestrowania <xref:System.Windows.Input.CommandBinding> i <xref:System.Windows.Input.InputBinding> obiekty do określonej klasy.  <xref:System.Windows.Input.CommandManager> Umożliwia też, za pośrednictwem <xref:System.Windows.Input.CommandManager.RequerySuggested> zdarzeń do powiadamiania polecenia, które go, powinny wywoływać <xref:System.Windows.Input.ICommand.CanExecuteChanged> zdarzeń.  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> Metoda wymusza <xref:System.Windows.Input.CommandManager> podnieść <xref:System.Windows.Input.CommandManager.RequerySuggested> zdarzeń.  Jest to przydatne w przypadku warunki, które powinny Włącz/Wyłącz polecenie to warunki <xref:System.Windows.Input.CommandManager> zna.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Biblioteka poleceń  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia zestaw wstępnie zdefiniowanych poleceń.  Biblioteka poleceń składa się z następujących klas: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands>i <xref:System.Windows.Input.ComponentCommands>.  Te klasy oferują polecenia <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> i <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>, i <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Wiele z tych poleceń zawierają zestaw domyślne powiązania danych wejściowych.  Na przykład, jeśli określisz, że aplikacja obsługuje polecenie Kopiuj, automatycznie uzyskują klawiatury powiązania "CTRL + C" uzyskasz także powiązania dla innych urządzeń wejściowych, takich jak [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] piórem gestów i informacje mowy.  
  
 Gdy odwołujesz się polecenia w różnych bibliotek polecenia przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zazwyczaj można pominąć nazwę klasy, klasy biblioteki, która ujawnia właściwość polecenia statyczne. Ogólnie rzecz biorąc nazwy polecenia są jednoznaczne jako ciągi, a będąca właścicielem typów przede wszystkim zapewniają polecenia powodują ustawienie logicznego grupowania, ale nie są niezbędne do uściślania. Na przykład można określić `Command="Cut"` zamiast bardziej szczegółowy `Command="ApplicationCommands.Cut"`. Jest to mechanizm wygody, która jest wbudowana w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora poleceń (bardziej precyzyjne jest zachowanie konwertera typu <xref:System.Windows.Input.ICommand>, który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odwołania procesora w czasie ładowania).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Tworzenie niestandardowych poleceń  
 Polecenia w klasy biblioteki poleceń nie odpowiada Twoim potrzebom, można utworzyć własne polecenia.  Istnieją dwa sposoby tworzenia niestandardowych poleceń.  Pierwsza to do rozpoczęcia od podstaw i zaimplementować <xref:System.Windows.Input.ICommand> interfejsu.  Inny sposób i bardziej powszechne podejście dotyczy tworzenie <xref:System.Windows.Input.RoutedCommand> lub <xref:System.Windows.Input.RoutedUICommand>.  
  
 Aby uzyskać przykład tworzenia niestandardowego <xref:System.Windows.Input.RoutedCommand>, zobacz [Tworzenie niestandardowych przykładowej routedcommand —](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Przegląd danych wejściowych](input-overview.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Implementowanie elementu ICommandSource](how-to-implement-icommandsource.md)
- [Instrukcje: Dodawanie polecenia do element MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Tworzenie przykładowej routedcommand — niestandardowe](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
