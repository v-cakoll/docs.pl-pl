---
title: "Jak włączyć polecenie"
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
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e90f7f69aebf48bbc27321d3808468a2df49f793
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enable-a-command"></a>Jak włączyć polecenie
W poniższym przykładzie pokazano sposób użycia droższe w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  W przykładzie przedstawiono sposób skojarzyć <xref:System.Windows.Input.RoutedCommand> do <xref:System.Windows.Controls.Button>, Utwórz <xref:System.Windows.Input.CommandBinding>i tworzenie obsługi zdarzeń, które implementują <xref:System.Windows.Input.RoutedCommand>.  Aby uzyskać więcej informacji na wydawanie poleceń, zobacz [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Przykład  
 W pierwszej sekcji kodu tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], który składa się z <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.StackPanel>i tworzy <xref:System.Windows.Input.CommandBinding> który kojarzy programy obsługi poleceń z <xref:System.Windows.Input.RoutedCommand>.  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A> Właściwość <xref:System.Windows.Controls.Button> jest skojarzony z <xref:System.Windows.Input.ApplicationCommands.Close%2A> polecenia.  
  
 <xref:System.Windows.Input.CommandBinding> Jest dodawany do <xref:System.Windows.Input.CommandBindingCollection> głównego <xref:System.Windows.Window>. <xref:System.Windows.Input.CommandBinding.Executed> i <xref:System.Windows.Input.CommandBinding.CanExecute> procedury obsługi zdarzeń są dołączone do tego powiązania i skojarzone z <xref:System.Windows.Input.ApplicationCommands.Close%2A> polecenia.  
  
 Bez <xref:System.Windows.Input.CommandBinding> nie logiki polecenia, tylko mechanizm Wywołaj polecenie nie istnieje.  Gdy <xref:System.Windows.Controls.Button> zostanie kliknięty <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> jest wywoływane na elemencie docelowym polecenia, a następnie <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.  Te zdarzenia przechodzenia drzewa element wyszukiwanie <xref:System.Windows.Input.CommandBinding> dla tego konkretnego polecenia.  Warto zauważyć, że ponieważ <xref:System.Windows.RoutedEvent> tunelu i bąbelków w drzewie element, należy zachować ostrożność w przypadku gdy <xref:System.Windows.Input.CommandBinding> jest umieszczany.   Jeśli <xref:System.Windows.Input.CommandBinding> znajduje się na element równorzędny element docelowy polecenia lub innego węzła, który nie jest na trasie o <xref:System.Windows.RoutedEvent>, <xref:System.Windows.Input.CommandBinding> nie jest dostępna.  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 W następnej sekcji kod implementuje <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandBinding.CanExecute> procedury obsługi zdarzeń.  
  
 <xref:System.Windows.Input.CommandManager.Executed> Obsługi wywołuje metodę Zamknij otwarty plik.  <xref:System.Windows.Input.CommandBinding.CanExecute> Obsługi wywołuje metodę, aby określić, czy plik jest otwarty.  Jeśli plik jest otwarty, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> ustawiono `true`; w przeciwnym razie wartość jest równa `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>Zobacz też  
 [Sterująca — omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md)
