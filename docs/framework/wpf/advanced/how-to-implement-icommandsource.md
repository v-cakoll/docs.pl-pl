---
title: 'Porady: implementowanie ICommandSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 9308bfbbb7fff86ca5e93c1155cc29e4ee0d05f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-icommandsource"></a>Porady: implementowanie ICommandSource
W tym przykładzie pokazano, jak utworzyć źródło polecenia zaimplementowanie <xref:System.Windows.Input.ICommandSource>.  Źródło polecenia jest obiekt, który umożliwia wywołanie polecenia.  <xref:System.Windows.Input.ICommandSource> Interfejsu udostępnia trzy elementy członkowskie: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, i <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> to polecenie, które zostanie wywołany. <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> Jest typem danych zdefiniowane przez użytkownika, który jest przekazywany z źródło polecenia do metody, która obsługuje polecenie. <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> To polecenie jest wykonywana na obiekt.  
  
 W tym przykładzie klasa jest tworzony które podklasy <xref:System.Windows.Controls.Slider> kontroli i implementuje <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia szereg klas, które implementują <xref:System.Windows.Input.ICommandSource>, takich jak <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, i <xref:System.Windows.Controls.ListBoxItem>.  Źródło polecenia definiuje sposób wywołuje polecenie.   <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.MenuItem> wywołania polecenia, gdy są one kliknięty.  A <xref:System.Windows.Controls.ListBoxItem> wywołuje polecenie, po kliknięciu double. Te klasy tylko staną się polecenie źródło ich <xref:System.Windows.Input.ICommandSource.Command%2A> właściwość jest ustawiona.  
  
 W tym przykładzie mamy wywoła polecenie, gdy zostanie przesunięty suwak lub dokładniej, gdy <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> właściwości zostanie zmieniona.  
  
 Poniżej znajduje się definicja klasy.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 Następnym krokiem jest zaimplementowanie <xref:System.Windows.Input.ICommandSource> elementów członkowskich.  W tym przykładzie właściwości są zaimplementowane jako <xref:System.Windows.DependencyProperty> obiektów.  Dzięki temu właściwości do używania wiązania z danymi.  Aby uzyskać więcej informacji na temat <xref:System.Windows.DependencyProperty> , zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Aby uzyskać więcej informacji na temat wiązania danych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Tylko <xref:System.Windows.Input.ICommandSource.Command%2A> pokazane właściwości.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Poniżej przedstawiono <xref:System.Windows.DependencyProperty> zmienić wywołania zwrotnego.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 Następnym krokiem jest dodawanie i usuwanie polecenia, który jest skojarzony ze źródłem polecenia.  <xref:System.Windows.Input.ICommandSource.Command%2A> Właściwości nie można po prostu zastąpione po dodaniu nowego polecenia, ponieważ obsługi zdarzeń skojarzonych z poprzedniego polecenia, jeśli wystąpił jeden z nich, najpierw należy usunąć.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 Ostatnim krokiem jest utworzenie logikę <xref:System.Windows.Input.ICommand.CanExecuteChanged> obsługi i <xref:System.Windows.Input.ICommand.Execute%2A> metody.  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged> Zdarzeń powiadamia źródło polecenia, który mógł ulec zmianie możliwości polecenia do wykonania na aktualnym elemencie docelowym polecenia.  Gdy źródło polecenia odbiera to zdarzenie, zwykle wywołuje <xref:System.Windows.Input.ICommand.CanExecute%2A> metody w poleceniu.  Jeśli polecenie nie można wykonać na bieżącym elemencie docelowym polecenia, źródło polecenia zwykle sam się wyłączy.  Jeśli polecenie można wykonać na bieżącym elemencie docelowym polecenia, źródło polecenia zwykle Włącz samej siebie.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 Ostatnim krokiem jest <xref:System.Windows.Input.ICommand.Execute%2A> metody.  Jeśli polecenie jest <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> metoda jest wywołana; w przeciwnym razie <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> metoda jest wywoływana.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Input.ICommandSource>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.Input.RoutedCommand>  
 [Przegląd poleceń](../../../../docs/framework/wpf/advanced/commanding-overview.md)
