---
title: 'Instrukcje: Włączanie polecenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
ms.openlocfilehash: bf01066a35672e1996f193abc6d76153e5e9dd46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181704"
---
# <a name="how-to-enable-a-command"></a>Instrukcje: Włączanie polecenia
Poniższy przykład ilustruje sposób użycia polecenia w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  W przykładzie pokazano, jak skojarzyć <xref:System.Windows.Input.RoutedCommand> do <xref:System.Windows.Controls.Button>, Utwórz <xref:System.Windows.Input.CommandBinding>i utworzyć procedury obsługi zdarzeń, które implementują <xref:System.Windows.Input.RoutedCommand>.  Aby uzyskać więcej informacji na temat polecenia, zobacz [polecenia Przegląd](commanding-overview.md).  
  
## <a name="example"></a>Przykład  
 Pierwszą część kodu tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], który składa się z <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.StackPanel>i tworzy <xref:System.Windows.Input.CommandBinding> który kojarzy programy obsługi poleceń z <xref:System.Windows.Input.RoutedCommand>.  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A> Właściwość <xref:System.Windows.Controls.Button> jest skojarzony z <xref:System.Windows.Input.ApplicationCommands.Close%2A> polecenia.  
  
 <xref:System.Windows.Input.CommandBinding> Jest dodawany do <xref:System.Windows.Input.CommandBindingCollection> głównego <xref:System.Windows.Window>. <xref:System.Windows.Input.CommandBinding.Executed> i <xref:System.Windows.Input.CommandBinding.CanExecute> procedury obsługi zdarzeń są dołączone do tego powiązania i skojarzone z <xref:System.Windows.Input.ApplicationCommands.Close%2A> polecenia.  
  
 Bez <xref:System.Windows.Input.CommandBinding> nie ma żadnych logiki polecenia, tylko mechanizm wywołać polecenie.  Gdy <xref:System.Windows.Controls.Button> po kliknięciu <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> jest zgłaszane w elemencie docelowym polecenia, a następnie <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.  Te zdarzenia przechodzić przez drzewo elementów, wyszukiwanie <xref:System.Windows.Input.CommandBinding> na tym konkretnym poleceniem.  Warto zauważyć, że ponieważ <xref:System.Windows.RoutedEvent> tunel i bąbelkowych za pośrednictwem drzewa elementów, należy zachować ostrożność w przypadku gdy <xref:System.Windows.Input.CommandBinding> jest umieszczany.   Jeśli <xref:System.Windows.Input.CommandBinding> znajduje się na element równorzędny w elemencie docelowym polecenia lub w innym węźle, który nie znajduje się na trasa <xref:System.Windows.RoutedEvent>, <xref:System.Windows.Input.CommandBinding> nie jest dostępna.  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 Następna sekcja kod implementuje <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandBinding.CanExecute> procedury obsługi zdarzeń.  
  
 <xref:System.Windows.Input.CommandManager.Executed> Obsługi wyjątku wywołuje metodę, aby zamknąć otwartego pliku.  <xref:System.Windows.Input.CommandBinding.CanExecute> Obsługi wyjątku wywołuje metodę, aby określić, czy plik jest otwarty.  Jeśli plik jest otwarty, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> ustawiono `true`; w przeciwnym razie jest równa `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd Polecenia](commanding-overview.md)
