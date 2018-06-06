---
title: Jak podpiąć polecenie do formantu za pomocą obsługi poleceń
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
ms.openlocfilehash: 22aca20eb3f6bc2e31fb5a01ed7c153cccef0bd8
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805438"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>Jak podpiąć polecenie do formantu za pomocą obsługi poleceń
Poniższy przykład przedstawia sposób Podłączanie <xref:System.Windows.Input.RoutedCommand> do <xref:System.Windows.Controls.Control> są wbudowane Obsługa polecenia.  Dla kompletnego przykładu, który przechwytuje się poleceń do wielu źródeł, zobacz [utworzyć niestandardowe próbę RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) próbki.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia bibliotekę używanych poleceń, które programistom wystąpić regularnie.  Klasy, które obejmują biblioteki polecenia są: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, i <xref:System.Windows.Documents.EditingCommands>.  
  
 Statycznych <xref:System.Windows.Input.RoutedCommand> obiektów, które składają się następujące klasy nie zostanie podana logiki polecenia.  Logika dla polecenia jest skojarzony z polecenie z <xref:System.Windows.Input.CommandBinding>.  Niektóre formanty utworzone w CommandBindings dla niektórych poleceń.  Mechanizm ten umożliwia semantykę pozostają takie same, podczas rzeczywistego wykonania polecenia, można zmienić.  A <xref:System.Windows.Controls.TextBox>, na przykład obsługuje <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenia inaczej niż formantu przeznaczony do obsługi obrazów, ale podstawowe informacje o tym, co oznacza to wkleić coś pozostaje taki sam.  Logika polecenia nie może być dostarczone przez polecenie, ale raczej muszą zostać dostarczone przez formant lub aplikacji.  
  
 Wiele formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utworzone w obsłudze niektórych poleceń w bibliotece polecenia.  <xref:System.Windows.Controls.TextBox>, na przykład obsługuje wiele poleceń edycji aplikacji, takich jak <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, i <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Deweloper aplikacji nie trzeba wykonywać żadnych czynności specjalne do pobrania tych poleceń, aby pracować z tych kontrolek.  Jeśli <xref:System.Windows.Controls.TextBox> jest element docelowy polecenia po wykonaniu polecenia obsłuży przy użyciu polecenia <xref:System.Windows.Input.CommandBinding> wbudowane w formancie.  
  
 Poniżej pokazano, jak używać <xref:System.Windows.Controls.MenuItem> jako źródło polecenia <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie, gdzie <xref:System.Windows.Controls.TextBox> jest elementem docelowym polecenia.  Całą logikę, który definiuje sposób <xref:System.Windows.Controls.TextBox> wykonuje Wklej jest wbudowana w <xref:System.Windows.Controls.TextBox> formantu.  
  
 A <xref:System.Windows.Controls.MenuItem> jest tworzony i jest <xref:System.Windows.Controls.MenuItem.Command%2A> właściwość jest ustawiona na <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenia.  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> Nie jest jawnie ustawiona na <xref:System.Windows.Controls.TextBox> obiektu.  Gdy <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> nie jest ustawiona, element docelowy polecenia jest element, który ma fokus klawiatury.  Jeśli element, który ma fokus klawiatury nie obsługuje <xref:System.Windows.Input.ApplicationCommands.Paste%2A> polecenie lub obecnie nie można wykonać polecenia Wklej (Schowka jest pusta, na przykład), a następnie <xref:System.Windows.Controls.MenuItem> będzie szary.  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd poleceń](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Podpinanie polecenia do kontrolki bez użycia obsługi poleceń](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
