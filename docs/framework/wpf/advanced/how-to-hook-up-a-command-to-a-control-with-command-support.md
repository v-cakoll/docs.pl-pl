---
title: 'Instrukcje: Podepnij polecenie do formantu za pomocą obsługi poleceń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
ms.openlocfilehash: 4eded4812d8894b58331f26ec75c592c15e95419
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663209"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>Instrukcje: Podepnij polecenie do formantu za pomocą obsługi poleceń
Poniższy przykład pokazuje, jak podpiąć <xref:System.Windows.Input.RoutedCommand> do <xref:System.Windows.Controls.Control> ma wbudowane Obsługa polecenia.  Aby uzyskać pełny przykład, który przechwytuje się polecenia do wielu źródeł, zobacz [tworzenie przykładowej routedcommand — niestandardowe](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) próbki.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawiera bibliotekę typowych poleceń, które napotykają Programiści aplikacji, regularnie.  Klasy, które obejmują Biblioteka poleceń są: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, i <xref:System.Windows.Documents.EditingCommands>.  
  
 Statyczne <xref:System.Windows.Input.RoutedCommand> obiekty, które tworzą te klasy nie trzeba dostarczać logiki polecenia.  Logiki dla polecenia jest skojarzony z polecenie <xref:System.Windows.Input.CommandBinding>.  Niektóre kontrolki zostały wbudowane CommandBindings dla niektórych poleceń.  Ten mechanizm pozwala zmienić semantykę polecenie pozostają takie same, w trakcie rzeczywiste wdrożenie.  A <xref:System.Windows.Controls.TextBox>, na przykład obsługuje <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenia inaczej niż kontrolki przeznaczone do obsługi obrazów, ale już podstawowe informacje o tym, co oznacza wklejeniu powrócisz pozostaje taka sama.  Logika polecenia nie może dostarczyć za pomocą polecenia, ale raczej muszą być dostarczane przez formant lub aplikacji.  
  
 Wiele kontrolek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają wbudowaną obsługą dla niektórych poleceń w bibliotece poleceń.  <xref:System.Windows.Controls.TextBox>, na przykład obsługuje wiele poleceń edycji aplikacji, takie jak <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, i <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Deweloper aplikacji nie trzeba wykonywać żadnych specjalnych, aby uzyskać następujące polecenia, aby pracować z tych kontrolek czynności.  Jeśli <xref:System.Windows.Controls.TextBox> jest miejscem docelowym polecenia podczas wykonywania polecenia obsłuży polecenie, używając <xref:System.Windows.Input.CommandBinding> utworzonego w formancie.  
  
 Poniżej pokazano sposób użycia <xref:System.Windows.Controls.MenuItem> jako źródło polecenia <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie, gdzie <xref:System.Windows.Controls.TextBox> jest miejscem docelowym polecenia.  Całą logikę, która definiuje sposób, w jaki <xref:System.Windows.Controls.TextBox> wykonuje wklejanie jest wbudowana w <xref:System.Windows.Controls.TextBox> kontroli.  
  
 A <xref:System.Windows.Controls.MenuItem> zostanie utworzony i będzie <xref:System.Windows.Controls.MenuItem.Command%2A> właściwość jest ustawiona na <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenia.  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> Nie jest jawnie ustawiony na <xref:System.Windows.Controls.TextBox> obiektu.  Gdy <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> nie jest ustawiony, element docelowy polecenia jest element, który ma fokus klawiatury.  Jeśli element, który ma fokus klawiatury nie obsługuje <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie lub obecnie nie można wykonać polecenia Wklej (Schowek jest pusta, na przykład), a następnie <xref:System.Windows.Controls.MenuItem> będą wyszarzone.  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd poleceń](../../../../docs/framework/wpf/advanced/commanding-overview.md)
- [Podpinanie polecenia do kontrolki bez użycia obsługi poleceń](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
