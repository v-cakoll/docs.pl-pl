---
title: 'Instrukcje: Zaimplementuj ICommandSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6d42c3a936114c01eb7b7493a9732597a7d2fab9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593943"
---
# <a name="how-to-implement-icommandsource"></a>Instrukcje: Zaimplementuj ICommandSource
W tym przykładzie przedstawiono sposób tworzenia źródło polecenia poprzez implementację <xref:System.Windows.Input.ICommandSource>.  Źródło polecenia jest obiektem, który wie, jak wywołać polecenie.  <xref:System.Windows.Input.ICommandSource> Interfejsu udostępnia trzy elementy członkowskie: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, i <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> to polecenie, które zostaną wywołane. <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> Jest typem danych zdefiniowane przez użytkownika, który jest przekazywany ze źródła polecenia do metody, która obsługuje polecenie. <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> To polecenie jest wykonywane na obiekt.  
  
 W tym przykładzie tworzenia których podklasy klasy <xref:System.Windows.Controls.Slider> kontroli i implementuje <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia wiele klas implementujących <xref:System.Windows.Input.ICommandSource>, takich jak <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, i <xref:System.Windows.Controls.ListBoxItem>.  Źródło polecenia definiuje, jak je wywołuje polecenie.   <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.MenuItem> Wywołaj polecenie, po ich kliknięciu.  A <xref:System.Windows.Controls.ListBoxItem> wywołuje polecenie, gdy zostanie dwukrotnie kliknięta. W ramach tych zajęć stają się tylko polecenie źródło, gdy ich <xref:System.Windows.Input.ICommandSource.Command%2A> właściwość jest ustawiona.  
  
 W tym przykładzie firma Microsoft będzie wywoływał dane polecenie po przeniesieniu suwak lub dokładniej, gdy <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zmienić właściwości.  
  
 Jest definicją klasy.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 Następnym krokiem jest zaimplementowanie <xref:System.Windows.Input.ICommandSource> elementów członkowskich.  W tym przykładzie właściwości są implementowane jako <xref:System.Windows.DependencyProperty> obiektów.  Dzięki temu właściwości do użycia powiązanie danych.  Aby uzyskać więcej informacji na temat <xref:System.Windows.DependencyProperty> klasy, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Aby uzyskać więcej informacji na temat tworzenia powiązań danych, zobacz [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Tylko <xref:System.Windows.Input.ICommandSource.Command%2A> właściwości jest wyświetlana w tym miejscu.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Poniżej przedstawiono <xref:System.Windows.DependencyProperty> zmienić wywołania zwrotnego.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 Następnym krokiem jest do dodawania i usuwania polecenia, które jest skojarzone z obiektem źródłowym polecenia.  <xref:System.Windows.Input.ICommandSource.Command%2A> Właściwości nie po prostu można zastąpić po dodaniu nowego polecenia, ponieważ programy obsługi zdarzeń skojarzonych z poprzedniego polecenia, jeśli wystąpił jeden z nich, najpierw należy usunąć.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 Ostatnim krokiem jest utworzenie logikę <xref:System.Windows.Input.ICommand.CanExecuteChanged> obsługi i <xref:System.Windows.Input.ICommand.Execute%2A> metody.  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged> Zdarzenie powiadamia źródła polecenia, które mogły ulec zmianie możliwości polecenia do wykonania w bieżącym elemencie docelowym polecenia.  Gdy źródło polecenia odbiera to zdarzenie, zwykle wywołuje <xref:System.Windows.Input.ICommand.CanExecute%2A> metody w poleceniu.  Jeśli polecenie nie można wykonać na aktualnym elemencie docelowym polecenia, źródło polecenia zazwyczaj sam się wyłączy.  Jeśli polecenie można wykonać na aktualnym elemencie docelowym polecenia, źródło polecenia zazwyczaj włączyć sam.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 Ostatnim krokiem jest <xref:System.Windows.Input.ICommand.Execute%2A> metody.  Jeśli polecenie jest <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> metoda jest wywołana; w przeciwnym razie <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> metoda jest wywoływana.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Przegląd poleceń](../../../../docs/framework/wpf/advanced/commanding-overview.md)
