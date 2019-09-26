---
title: 'Porady: Podepnij polecenie do formantu bez użycia obsługi poleceń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
ms.openlocfilehash: 3ae45c9a9e33a3cb53ada6e1e5430ae0f9e6c198
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "71263305"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Instrukcje: Podepnij polecenie do formantu bez użycia obsługi poleceń
Poniższy przykład pokazuje, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Controls.Control> jak podłączyć do programu, który nie ma wbudowanej obsługi polecenia.  Aby uzyskać kompletny przykład, który łączy polecenia z wieloma źródłami, zobacz przykład [Create a Custom RoutedCommand Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) .  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]udostępnia bibliotekę typowych poleceń, które programiści aplikacji napotykają regularnie.  Klasy wchodzące w skład biblioteki poleceń to: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands> <xref:System.Windows.Input.MediaCommands>, i <xref:System.Windows.Documents.EditingCommands>.  
  
 Obiekty statyczne <xref:System.Windows.Input.RoutedCommand> , które tworzą te klasy, nie dostarczają logiki poleceń.  Logika polecenia jest skojarzona z poleceniem <xref:System.Windows.Input.CommandBinding>.  Wiele kontrolek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w programie wbudowano obsługę niektórych poleceń w bibliotece poleceń.  <xref:System.Windows.Controls.TextBox>Program obsługuje na przykład wiele poleceń edycji aplikacji, takich jak <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>i <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Deweloper aplikacji nie musi wykonywać żadnych specjalnych czynności, aby te polecenia mogły pracować z tymi kontrolkami.  Jeśli jest obiektem docelowym polecenia, gdy polecenie jest wykonywane, będzie obsługiwać polecenie <xref:System.Windows.Input.CommandBinding> przy użyciu wbudowanej kontrolki. <xref:System.Windows.Controls.TextBox>  
  
 Poniżej przedstawiono sposób użycia <xref:System.Windows.Controls.Button> jako źródła <xref:System.Windows.Input.ApplicationCommands.Open%2A> poleceń polecenia.  Jest tworzony, który kojarzy określony <xref:System.Windows.Input.CanExecuteRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> z <xref:System.Windows.Input.RoutedCommand>. <xref:System.Windows.Input.CommandBinding>  
  
 Najpierw tworzone jest źródło polecenia.  <xref:System.Windows.Controls.Button> Jest używany jako źródło polecenia.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Następnie są<xref:System.Windows.Input.CanExecuteRoutedEventHandler> tworzone i.<xref:System.Windows.Input.ExecutedRoutedEventHandler>  Po prostu otwiera a <xref:System.Windows.MessageBox> , aby oznacza, że polecenie zostało wykonane. <xref:System.Windows.Input.ExecutedRoutedEventHandler>  Ustawia właściwość na`true`. <xref:System.Windows.Input.CanExecuteRoutedEventHandler> <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>  Zwykle program obsługi może wykonywać bardziej niezawodne testy, aby sprawdzić, czy polecenie może zostać wykonane na bieżącym obiekcie docelowym polecenia.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Na koniec <xref:System.Windows.Window> <xref:System.Windows.Input.ApplicationCommands.Open%2A> jest tworzony w folderze głównym aplikacji, która kojarzy procedury obsługi zdarzeń kierowanych z poleceniem. <xref:System.Windows.Input.CommandBinding>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd poleceń](commanding-overview.md)
- [Podpinanie polecenia do kontrolki za pomocą obsługi poleceń](how-to-hook-up-a-command-to-a-control-with-command-support.md)
