---
title: 'Instrukcje: Tworzenie RoutedCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: 4119a762bd0db63108d08a9db9367e367adb6b58
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372090"
---
# <a name="how-to-create-a-routedcommand"></a>Instrukcje: Tworzenie RoutedCommand
W tym przykładzie pokazano, jak utworzyć niestandardową <xref:System.Windows.Input.RoutedCommand> i jak implementować polecenia niestandardowego przez utworzenie <xref:System.Windows.Input.ExecutedRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> i dołączania ich do <xref:System.Windows.Input.CommandBinding>.  Aby uzyskać więcej informacji na temat polecenia, zobacz [polecenia Przegląd](commanding-overview.md).  
  
## <a name="example"></a>Przykład  
 Pierwszym krokiem w tworzeniu <xref:System.Windows.Input.RoutedCommand> jest definiowanie polecenia i tworzenia jego wystąpienia.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 Aby można było używać polecenia w aplikacji, można utworzyć procedury obsługi zdarzeń, które definiują, polecenie powoduje  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 Następnie <xref:System.Windows.Input.CommandBinding> jest tworzony, który kojarzy polecenie z programami obsługi zdarzeń. <xref:System.Windows.Input.CommandBinding> Jest tworzona w określonym obiektem.  Ten obiekt definiuje zakres <xref:System.Windows.Input.CommandBinding> w drzewie elementów  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 Ostatnim krokiem jest wywoływanie polecenia.  Jednym ze sposobów, aby wywołać polecenie jest skojarz ją z <xref:System.Windows.Input.ICommandSource>, takich jak <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 Po kliknięciu przycisku <xref:System.Windows.Input.RoutedCommand.Execute%2A> metody na niestandardowej <xref:System.Windows.Input.RoutedCommand> jest wywoływana.  <xref:System.Windows.Input.RoutedCommand> Zgłasza <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> zdarzeń.  Te zdarzenia przechodzić przez drzewo elementów, wyszukiwanie <xref:System.Windows.Input.CommandBinding> dla tego określonego polecenia.  Jeśli <xref:System.Windows.Input.CommandBinding> zostanie znaleziony, <xref:System.Windows.Input.ExecutedRoutedEventHandler> skojarzony <xref:System.Windows.Input.CommandBinding> jest wywoływana.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Input.RoutedCommand>
- [Przegląd poleceń](commanding-overview.md)
