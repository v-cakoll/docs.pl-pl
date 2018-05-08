---
title: 'Porady: tworzenie RoutedCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: 75e6c435516fe2a174cf991bd41f24e1b30a212a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-routedcommand"></a>Porady: tworzenie RoutedCommand
W tym przykładzie przedstawiono sposób tworzenia niestandardowego <xref:System.Windows.Input.RoutedCommand> i implementowania polecenia niestandardowych tworząc <xref:System.Windows.Input.ExecutedRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> i dołączać do <xref:System.Windows.Input.CommandBinding>.  Aby uzyskać więcej informacji na wydawanie poleceń, zobacz [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Przykład  
 Pierwszym krokiem tworzenia <xref:System.Windows.Input.RoutedCommand> jest zdefiniowanie polecenia i uruchomieniu jej wystąpienia.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 Aby można było używać polecenia w aplikacji, można utworzyć procedury obsługi zdarzeń, które określają, jak działa polecenie  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 Następnie <xref:System.Windows.Input.CommandBinding> jest tworzony, który kojarzy polecenie z obsługi zdarzeń. <xref:System.Windows.Input.CommandBinding> Jest tworzona na konkretny obiekt.  Ten obiekt definiuje zakres <xref:System.Windows.Input.CommandBinding> w drzewie — element  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 Ostatnim krokiem jest wywoływanie polecenia.  Jednym ze sposobów Wywołaj polecenie ma skojarzyć go z <xref:System.Windows.Input.ICommandSource>, takich jak <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 Po kliknięciu przycisku <xref:System.Windows.Input.RoutedCommand.Execute%2A> metoda niestandardowa <xref:System.Windows.Input.RoutedCommand> jest wywoływana.  <xref:System.Windows.Input.RoutedCommand> Zgłasza <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> kierowane zdarzenia.  Te zdarzenia przechodzenia drzewa element wyszukiwanie <xref:System.Windows.Input.CommandBinding> dla tego konkretnego polecenia.  Jeśli <xref:System.Windows.Input.CommandBinding> zostanie znaleziony, <xref:System.Windows.Input.ExecutedRoutedEventHandler> skojarzone z <xref:System.Windows.Input.CommandBinding> jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Input.RoutedCommand>  
 [Przegląd poleceń](../../../../docs/framework/wpf/advanced/commanding-overview.md)
