---
title: 'Instrukcje: Podepnij polecenie do formantu bez użycia obsługi poleceń'
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
ms.openlocfilehash: 66b371f4d67c1102ddf341dd4b70aac66aa41605
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352675"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Instrukcje: Podepnij polecenie do formantu bez użycia obsługi poleceń
Poniższy przykład pokazuje, jak podpiąć <xref:System.Windows.Input.RoutedCommand> do <xref:System.Windows.Controls.Control> który nie ma wbudowaną obsługą dla polecenia.  Aby uzyskać pełny przykład, który przechwytuje się polecenia do wielu źródeł, zobacz [tworzenie przykładowej routedcommand — niestandardowe](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) próbki.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawiera bibliotekę typowych poleceń, które napotykają Programiści aplikacji, regularnie.  Klasy, które obejmują Biblioteka poleceń są: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, i <xref:System.Windows.Documents.EditingCommands>.  
  
 Statyczne <xref:System.Windows.Input.RoutedCommand> obiekty, które tworzą te klasy nie trzeba dostarczać logiki polecenia.  Logiki dla polecenia jest skojarzony z polecenie <xref:System.Windows.Input.CommandBinding>.  Wiele kontrolek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają wbudowaną obsługą dla niektórych poleceń w bibliotece poleceń.  <xref:System.Windows.Controls.TextBox>, na przykład obsługuje wiele poleceń edycji aplikacji, takie jak <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, i <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Deweloper aplikacji nie trzeba wykonywać żadnych specjalnych, aby uzyskać następujące polecenia, aby pracować z tych kontrolek czynności.  Jeśli <xref:System.Windows.Controls.TextBox> jest miejscem docelowym polecenia podczas wykonywania polecenia obsłuży polecenie, używając <xref:System.Windows.Input.CommandBinding> utworzonego w formancie.  
  
 Poniżej pokazano sposób użycia <xref:System.Windows.Controls.Button> jako źródło polecenia <xref:System.Windows.Input.ApplicationCommands.Open%2A> polecenia.  A <xref:System.Windows.Input.CommandBinding> jest tworzony w tym kojarzy określonego <xref:System.Windows.Input.CanExecuteRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> z <xref:System.Windows.Input.RoutedCommand>.  
  
 Najpierw tworzone jest źródło polecenia.  Element <xref:System.Windows.Controls.Button> jest używany jako źródło polecenia.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Następnie <xref:System.Windows.Input.ExecutedRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> są tworzone.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Po prostu otwiera <xref:System.Windows.MessageBox> oznaczającego, że polecenie jest wykonywane.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Ustawia <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> właściwość `true`.  Zazwyczaj można wykonać procedury obsługi wykona sprawdza bardziej niezawodne, jeśli polecenie można wykonać na aktualnym elemencie docelowym polecenia.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Na koniec <xref:System.Windows.Input.CommandBinding> jest tworzony w katalogu głównym <xref:System.Windows.Window> aplikacji, które kojarzy programów obsługi zdarzeń trasowanych do <xref:System.Windows.Input.ApplicationCommands.Open%2A> polecenia.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd poleceń](commanding-overview.md)
- [Podpinanie polecenia do kontrolki za pomocą obsługi poleceń](how-to-hook-up-a-command-to-a-control-with-command-support.md)
