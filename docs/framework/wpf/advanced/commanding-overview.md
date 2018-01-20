---
title: "Przegląd Polecenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3eb7d05cdf5f6a80a0a247a5f429052cc9a8368b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="commanding-overview"></a>Przegląd Polecenia
<a name="introduction"></a>Steruje jest mechanizmem wejściowego w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewniające wejściowych obsługi na poziomie semantycznego więcej niż dane wejściowe urządzenia. Przykłady poleceń **kopiowania**, **Wytnij**, i **Wklej** odnaleźć operacji na wiele aplikacji.  
  
 To omówienie definiuje, jakie polecenia znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], klas, które są częścią sterująca modelu i używania i utworzyć polecenia w aplikacji.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Co to są polecenia?](#commands_at_10000_feet)  
  
-   [Przykład prostego polecenia na platformie WPF](#simple_command)  
  
-   [Cztery główne pojęcia w droższe WPF](#Four_main_Concepts)  
  
-   [Polecenie biblioteki](#Command_Library)  
  
-   [Tworzenie niestandardowych poleceń](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Co to są polecenia?  
 Polecenia mają wiele celów. Pierwszy ma na celu oddzielenia semantykę i obiekt, który wywołuje polecenie z logikę, która wykonuje polecenie. Dzięki temu wielu i różnych źródeł do wywołania tej samej logiki polecenia który umożliwia logika polecenia można dostosowywać dla poszczególnych obiektów docelowych. Na przykład operacje edycji **kopiowania**, **Wytnij**, i **Wklej**, które znajdują się w wiele aplikacji może być wywoływany przy użyciu różnych działań użytkownika, jeśli są one zaimplementowany przy użyciu poleceń. Aplikacja może zezwolić użytkownikowi na Wytnij zaznaczonych obiektów lub tekstu, klikając przycisk, wybierając element menu lub przy użyciu kombinacji klawiszy, np. CTRL + X. Za pomocą poleceń, można powiązać każdy typ akcji użytkownika z tej samej logiki.  
  
 Inny poleceń ma na celu wskazuje, czy akcja jest dostępna. Aby kontynuować przykład wycinanie obiektu lub tekstu, akcja ma sens tylko po wybraniu elementu. Jeśli użytkownik próbuje Wytnij obiektu lub tekstu bez żadnych zaznaczone, nic się stanie. Aby tę informację użytkownikowi, wiele aplikacji należy wyłączyć przycisków i elementów menu, aby użytkownik wie, czy jest możliwe do wykonania akcji. Polecenie można wskazać, czy akcja jest możliwe dzięki implementacji <xref:System.Windows.Input.ICommand.CanExecute%2A> metody. Przycisk mogą subskrybować <xref:System.Windows.Input.ICommand.CanExecuteChanged> zdarzeń i wyłączony, jeśli <xref:System.Windows.Input.ICommand.CanExecute%2A> zwraca `false` lub nie jest włączone, jeśli <xref:System.Windows.Input.ICommand.CanExecute%2A> zwraca `true`.  
  
 Semantyka polecenie może być zgodne w aplikacji i klasy, ale logiki akcji jest przeznaczony dla konkretnego obiektu reagować. Kombinacja klawiszy CTRL + X wywołuje **Wytnij** w tekst klasy, klasy obrazu i przeglądarki sieci Web, ale logikę wykonywania **Wytnij** operacji jest zdefiniowany przez aplikację, która wykonuje Wytnij. A <xref:System.Windows.Input.RoutedCommand> umożliwia klientom implementują logikę. Obiekt tekstu może Wytnij zaznaczonego tekstu do Schowka, podczas gdy obiekt obrazu mogą być obcięte wybranego obrazu. Jeśli aplikacja obsługuje <xref:System.Windows.Input.CommandManager.Executed> zdarzeń, ma dostęp do elementu docelowego polecenia, a można podjąć odpowiednie działania w zależności od typu elementu docelowego.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>Przykład prostego polecenia na platformie WPF  
 Najprostszym sposobem użycia polecenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma użyć wstępnie zdefiniowanej <xref:System.Windows.Input.RoutedCommand> z jednej z klas biblioteki polecenia; użyj formantu, który ma macierzystą obsługę obsługi polecenia; i używać formantu, który ma macierzystą obsługę wywoływania polecenia.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> Polecenia jest jednym z wstępnie zdefiniowanych poleceń w <xref:System.Windows.Input.ApplicationCommands> klasy.  <xref:System.Windows.Controls.TextBox> Formantu są wbudowane w logice obsługi <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenia.  I <xref:System.Windows.Controls.MenuItem> klasy ma obsługę natywną wywoływanie polecenia.  
  
 Poniższy przykład przedstawia sposób konfigurowania <xref:System.Windows.Controls.MenuItem> tak, aby po kliknięciu wywoła <xref:System.Windows.Input.ApplicationCommands.Paste%2A> na <xref:System.Windows.Controls.TextBox>, przyjmuje <xref:System.Windows.Controls.TextBox> ma fokus klawiatury.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>Cztery główne pojęcia w droższe WPF  
 Polecenie routingiem modelu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mogą być dzielone na cztery główne pojęcia: polecenie Źródło polecenia, element docelowy polecenia i powiązanie polecenia:  
  
-   *Polecenia* akcji do wykonania.  
  
-   *Źródło polecenia* jest obiekt, który wywołuje polecenia.  
  
-   *Elemencie docelowym polecenia* to polecenie jest wykonywana na obiekt.  
  
-   *Polecenia powiązania* to obiekt, który mapuje logiki polecenia do polecenia.  
  
 W poprzednim przykładzie <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie jest poleceniem, <xref:System.Windows.Controls.MenuItem> jest źródłem polecenia <xref:System.Windows.Controls.TextBox> jest element docelowy polecenia i powiązanie polecenia jest dostarczana przez <xref:System.Windows.Controls.TextBox> formantu.  Warto zauważyć, że nie jest on zawsze przypadku który <xref:System.Windows.Input.CommandBinding> jest dostarczana przez kontrolkę, która jest polecenie klasy docelowej.  Bardzo często <xref:System.Windows.Input.CommandBinding> musi zostać utworzony przez dewelopera aplikacji lub <xref:System.Windows.Input.CommandBinding> może zostać dołączony do elementu nadrzędnego elemencie docelowym polecenia.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Polecenia  
 Polecenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są tworzone z zastosowaniem <xref:System.Windows.Input.ICommand> interfejsu.  <xref:System.Windows.Input.ICommand>udostępnia dwie metody <xref:System.Windows.Input.ICommand.Execute%2A>, i <xref:System.Windows.Input.ICommand.CanExecute%2A>i zdarzenia <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A>wykonuje akcje, które są skojarzone z poleceniem. <xref:System.Windows.Input.ICommand.CanExecute%2A>Określa, czy polecenia można wykonywać w bieżącym elemencie docelowym polecenia. <xref:System.Windows.Input.ICommand.CanExecuteChanged>jest uruchamiany, jeśli Menedżer polecenia centralizuje sterująca operacji wykryje zmianę w źródle polecenia, które może unieważnić polecenie, które zostały zgłoszone, ale nie została jeszcze wykonana przez powiązanie polecenia.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Implementacja <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand> klasy i jest fokus w tym omówieniu.  
  
 Główne źródła danych wejściowych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] myszy, klawiatury, pismo odręczne i routingiem poleceń.  Użyj danych wejściowych więcej zorientowane na urządzeniu <xref:System.Windows.RoutedEvent> powiadomiono obiektów w aplikacji, strona wystąpiło zdarzenie wejściowe.  A <xref:System.Windows.Input.RoutedCommand> nie różni się.  <xref:System.Windows.Input.RoutedCommand.Execute%2A> i <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody <xref:System.Windows.Input.RoutedCommand> nie zawierają logiki aplikacji dla polecenia, ale raczej podnieść kierowane zdarzenia tego tunelu i bąbelkowy za pośrednictwem elementu drzewa, aż do napotkania obiektu z <xref:System.Windows.Input.CommandBinding>.  <xref:System.Windows.Input.CommandBinding> Zawiera programy obsługi dla tych zdarzeń i obsługi, które wykonuje polecenie.  Aby uzyskać więcej informacji na zdarzenie routingu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A> Metoda <xref:System.Windows.Input.RoutedCommand> zgłasza <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> zdarzenia w elemencie docelowym polecenia.  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> Metoda <xref:System.Windows.Input.RoutedCommand> zgłasza <xref:System.Windows.Input.CommandManager.CanExecute> i <xref:System.Windows.Input.CommandManager.PreviewCanExecute> zdarzenia w elemencie docelowym polecenia.  Te zdarzenia tunelu i bąbelków w drzewie element aż do napotkania obiektu, który ma <xref:System.Windows.Input.CommandBinding> dla tego konkretnego polecenia.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zestaw typowych poleceń routingiem rozmieszczenie do kilku klas dostaw: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands>, i <xref:System.Windows.Documents.EditingCommands>.  Te klasy składać się tylko z <xref:System.Windows.Input.RoutedCommand> obiektów i nie logiki wykonania polecenia.  Logika implementacji jest odpowiedzialny za obiektu, na którym jest wykonywana polecenia na.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Polecenie źródeł  
 Źródło polecenia jest obiekt, który wywołuje polecenia.  Przykłady źródeł polecenia <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button>, i <xref:System.Windows.Input.KeyGesture>.  
  
 Polecenie źródeł w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zazwyczaj zaimplementować <xref:System.Windows.Input.ICommandSource> interfejsu.  
  
 <xref:System.Windows.Input.ICommandSource>udostępnia trzy właściwości: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, i <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A>to polecenie do wykonania po wywołaniu polecenia źródła.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>jest obiektem, w którym można wykonać polecenia.  Warto zauważyć, że w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> właściwość <xref:System.Windows.Input.ICommandSource> ma zastosowanie tylko podczas <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand>.  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona na <xref:System.Windows.Input.ICommandSource> i odpowiadające jej polecenie nie jest <xref:System.Windows.Input.RoutedCommand>, element docelowy polecenia jest ignorowana. Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> nie jest ustawiona, element z fokusem klawiatury będzie elemencie docelowym polecenia.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>Typ danych zdefiniowany przez użytkownika, używany do przekazywania informacji do obsługi implementuje polecenia.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Klas, które implementują <xref:System.Windows.Input.ICommandSource> są <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>, i <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, i <xref:System.Windows.Documents.Hyperlink> wywołania polecenia, gdy są one kliknięty, a moduł <xref:System.Windows.Input.InputBinding> wywołuje polecenie po <xref:System.Windows.Input.InputGesture> skojarzone z jest wykonywana.  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.MenuItem> w <xref:System.Windows.Controls.ContextMenu> jako źródło polecenia <xref:System.Windows.Input.ApplicationCommands.Properties%2A> polecenia.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Zazwyczaj będzie nasłuchiwać źródło polecenia <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> zdarzeń.  To zdarzenie informuje źródło polecenia, który mógł ulec zmianie możliwości polecenia do wykonania na aktualnym elemencie docelowym polecenia.  Źródło polecenia można zbadać bieżący stan <xref:System.Windows.Input.RoutedCommand> przy użyciu <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody.  Źródło polecenia można następnie sam się wyłączy, jeśli nie można wykonać polecenia.  Na przykład jest <xref:System.Windows.Controls.MenuItem> graying sam się, gdy nie można wykonać polecenia.  
  
 <xref:System.Windows.Input.InputGesture> Mogą być używane jako źródło polecenia.  Dwa typy wejściowe gestów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są <xref:System.Windows.Input.KeyGesture> i <xref:System.Windows.Input.MouseGesture>.  Można potraktować <xref:System.Windows.Input.KeyGesture> skrótu klawiaturowego, np. CTRL + C.  A <xref:System.Windows.Input.KeyGesture> składa się z <xref:System.Windows.Input.Key> i zestaw <xref:System.Windows.Input.ModifierKeys>.  A <xref:System.Windows.Input.MouseGesture> składa się z <xref:System.Windows.Input.MouseAction> i opcjonalny zestaw <xref:System.Windows.Input.ModifierKeys>.  
  
 Aby <xref:System.Windows.Input.InputGesture> do działania jako źródło polecenia, muszą one zostać skojarzone z poleceniem. Są to zrobić na kilka sposobów.  Jednym ze sposobów jest użycie <xref:System.Windows.Input.InputBinding>.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Input.KeyBinding> między <xref:System.Windows.Input.KeyGesture> i <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Inny sposób, aby skojarzyć <xref:System.Windows.Input.InputGesture> do <xref:System.Windows.Input.RoutedCommand> jest dodanie <xref:System.Windows.Input.InputGesture> do <xref:System.Windows.Input.InputGestureCollection> na <xref:System.Windows.Input.RoutedCommand>.  
  
 Poniższy przykład przedstawia sposób dodawania <xref:System.Windows.Input.KeyGesture> do <xref:System.Windows.Input.InputGestureCollection> z <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 A <xref:System.Windows.Input.CommandBinding> kojarzy polecenie z obsługi zdarzeń, które implementują polecenia.  
  
 <xref:System.Windows.Input.CommandBinding> Klasa zawiera <xref:System.Windows.Input.CommandBinding.Command%2A> właściwości, oraz <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, i <xref:System.Windows.Input.CommandBinding.CanExecute> zdarzenia.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>to polecenie który <xref:System.Windows.Input.CommandBinding> jest skojarzona z.  Programy obsługi zdarzeń, które są dołączone do <xref:System.Windows.Input.CommandBinding.PreviewExecuted> i <xref:System.Windows.Input.CommandBinding.Executed> zdarzenia implementują logikę polecenia.  Programy obsługi zdarzeń jest dołączony do <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> i <xref:System.Windows.Input.CommandBinding.CanExecute> zdarzenia ustalić, czy polecenia można wykonywać w bieżącym elemencie docelowym polecenia.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Input.CommandBinding> w katalogu głównym <xref:System.Windows.Window> aplikacji.  <xref:System.Windows.Input.CommandBinding> Kojarzy <xref:System.Windows.Input.ApplicationCommands.Open%2A> z <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandBinding.CanExecute> programów obsługi.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Następnie <xref:System.Windows.Input.ExecutedRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> są tworzone.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Otwiera <xref:System.Windows.MessageBox> wyświetlający ciąg informujący o tym polecenie zostało wykonane.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Ustawia <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> właściwości `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> jest dołączony do określonego obiektu, takich jak katalog główny <xref:System.Windows.Window> aplikacji lub formantu.  Obiekt który <xref:System.Windows.Input.CommandBinding> jest dołączony do określa zakres powiązania.  Na przykład <xref:System.Windows.Input.CommandBinding> dołączony do elementu nadrzędnego polecenie docelowym może być osiągnięta poprzez <xref:System.Windows.Input.CommandBinding.Executed> zdarzeń, ale <xref:System.Windows.Input.CommandBinding> dołączony do obiektu podrzędnego polecenia docelowy jest nieosiągalny.  To jest bezpośrednim skutkiem sposób <xref:System.Windows.RoutedEvent> tunele i dymki z obiektu, który wywołuje zdarzenie.  
  
 W niektórych sytuacjach <xref:System.Windows.Input.CommandBinding> jest dołączony do docelowego polecenia, takich jak z <xref:System.Windows.Controls.TextBox> klasy i <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, i <xref:System.Windows.Input.ApplicationCommands.Paste%2A> poleceń. Bardzo często jednak jest wygodniejsze dołączyć <xref:System.Windows.Input.CommandBinding> do elementu nadrzędnego elementu docelowego polecenia, takich jak głównym <xref:System.Windows.Window> lub w obiekcie aplikacji, zwłaszcza, jeśli takie same <xref:System.Windows.Input.CommandBinding> może służyć do wielu obiekty docelowe poleceń.  Są to decyzji projektowych, które należy wziąć pod uwagę podczas tworzenia sterująca infrastruktury.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Polecenie docelowego  
 Element docelowy polecenia jest element, na którym jest wykonywane polecenie.  W odniesieniu do <xref:System.Windows.Input.RoutedCommand>, element docelowy polecenia jest element pod które routingu <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandManager.CanExecute> uruchamia.  Jak zanotowane wcześniej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> właściwość <xref:System.Windows.Input.ICommandSource> ma zastosowanie tylko podczas <xref:System.Windows.Input.ICommand> jest <xref:System.Windows.Input.RoutedCommand>.  Jeśli <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> jest ustawiona na <xref:System.Windows.Input.ICommandSource> i odpowiadające jej polecenie nie jest <xref:System.Windows.Input.RoutedCommand>, element docelowy polecenia jest ignorowana.  
  
 Źródło polecenia można ustawić jawnie elemencie docelowym polecenia.  Jeśli nie zdefiniowano celu polecenia, element z fokusem klawiatury będzie używany jako element docelowy polecenia.  Jedną z korzyści wynikające ze stosowania element z fokusem klawiatury jako element docelowy polecenia jest możliwość Deweloper aplikacji do użycia z tym samym źródłem polecenie do wywołania polecenia dla wielu elementów docelowych, bez konieczności informacje o elemencie docelowym polecenia.  Na przykład jeśli <xref:System.Windows.Controls.MenuItem> wywołuje **Wklej** polecenia w aplikacji, która ma <xref:System.Windows.Controls.TextBox> kontroli i <xref:System.Windows.Controls.PasswordBox> formant, element docelowy może być albo <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.PasswordBox> w zależności od formant ma fokus klawiatury.  
  
 Poniższy przykład pokazuje, jak jawnie Ustaw element docelowy polecenia w znaczniku i w kodzie.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>Menedżer poleceń  
 <xref:System.Windows.Input.CommandManager> Służy liczba polecenia powiązane funkcje.  Zapewnia zbiór metody statyczne do dodawania i usuwania <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>, i <xref:System.Windows.Input.CommandManager.CanExecute> procedury obsługi zdarzeń do i z określonym elementem.  Zapewnia sposób rejestrowania <xref:System.Windows.Input.CommandBinding> i <xref:System.Windows.Input.InputBinding> obiekty do określonej klasy.  <xref:System.Windows.Input.CommandManager> Umożliwia też, za pomocą <xref:System.Windows.Input.CommandManager.RequerySuggested> zdarzeń do powiadamiania polecenia należy podnieść go <xref:System.Windows.Input.ICommand.CanExecuteChanged> zdarzeń.  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> Wymusza metody <xref:System.Windows.Input.CommandManager> podnieść <xref:System.Windows.Input.CommandManager.RequerySuggested> zdarzeń.  Jest to przydatne w przypadku warunki, które powinny Włącz/Wyłącz polecenia nie są jednak warunki <xref:System.Windows.Input.CommandManager> zna.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Polecenie biblioteki  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera zestaw wstępnie zdefiniowanych poleceń.  Biblioteka polecenia składa się z następujących klas: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands>i <xref:System.Windows.Input.ComponentCommands>.  Te klasy udostępniają polecenia, takich jak <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> i <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>, i <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Wiele z tych poleceń obejmują zestaw powiązania wejściowe domyślne.  Na przykład, jeśli określono, że aplikacja obsługuje polecenie Kopiuj, automatycznie pobrać klawiatury powiązania "CTRL + C" umożliwia również wyświetlenie powiązania dla innych urządzeń wejściowych, takich jak [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] pióra gestów i informacje mowy.  
  
 Podczas odwoływania się poleceń w różnych bibliotek polecenia przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zwykle można pominąć nazwę klasy klasy biblioteki, która udostępnia właściwości statycznej polecenia. Ogólnie rzecz biorąc nazwy polecenia są jednoznaczne jako ciągi, a właścicielem typów istnieją umożliwiają logiczne grupowanie poleceń, ale nie są niezbędne dla Uściślanie. Na przykład można określić `Command="Cut"` zamiast pełniejsze `Command="ApplicationCommands.Cut"`. Jest to mechanizm wygody, który korzysta z wbudowanej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora poleceń (dokładniej, jest typu konwertera zachowania <xref:System.Windows.Input.ICommand>, który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odwołania procesora w czasie ładowania).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Tworzenie niestandardowych poleceń  
 Polecenia w klasach biblioteki polecenia nie spełniają potrzeb, można utworzyć własne polecenia.  Istnieją dwa sposoby tworzenia poleceń niestandardowych.  Pierwsza to od podstaw uruchamiania i zaimplementować <xref:System.Windows.Input.ICommand> interfejsu.  Inny sposób i częściej podejście jest utworzenie <xref:System.Windows.Input.RoutedCommand> lub <xref:System.Windows.Input.RoutedUICommand>.  
  
 Przykład tworzenia niestandardowego <xref:System.Windows.Input.RoutedCommand>, zobacz [tworzenia niestandardowych przykładu RoutedCommand](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Input.RoutedCommand>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Input.InputBinding>  
 <xref:System.Windows.Input.CommandManager>  
 [Przegląd danych wejściowych](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Implementowanie elementu ICommandSource](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)  
 [Porady: Dodawanie polecenia do elementu menu.](http://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)  
 [Tworzenie niestandardowych RoutedCommand przykładu](http://go.microsoft.com/fwlink/?LinkID=159980)
