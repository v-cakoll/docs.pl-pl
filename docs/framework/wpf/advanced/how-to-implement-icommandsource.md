---
title: 'Porady: implementowanie ICommandSource'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6c18e0b77ec53d9bd3e7ce610f2940effe603c88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174696"
---
# <a name="how-to-implement-icommandsource"></a>Porady: implementowanie ICommandSource

W tym przykładzie pokazano, jak <xref:System.Windows.Input.ICommandSource>utworzyć źródło poleceń przez zaimplementowanie . Źródło polecenia jest obiektem, który wie, jak wywołać polecenie. Interfejs <xref:System.Windows.Input.ICommandSource> udostępnia trzy elementy członkowskie:

- <xref:System.Windows.Input.ICommandSource.Command%2A>: polecenie, które zostanie wywołane.
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: typ danych zdefiniowany przez użytkownika, który jest przekazywany ze źródła polecenia do metody obsługującej polecenie.
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: obiekt, na który jest wykonywane polecenie.

W tym przykładzie jest tworzony klasy, <xref:System.Windows.Controls.Slider> która dziedziczy <xref:System.Windows.Input.ICommandSource> z formantu i implementuje interfejs.
  
## <a name="example"></a>Przykład

WPF WPF udostępnia szereg <xref:System.Windows.Input.ICommandSource>klas, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.MenuItem>które <xref:System.Windows.Documents.Hyperlink>implementują , takich jak , i . Źródło polecenia definiuje sposób wywoływania polecenia. Te klasy wywołać polecenie po kliknięciu i stają się one <xref:System.Windows.Input.ICommandSource.Command%2A> tylko źródłem poleceń, gdy ich właściwość jest ustawiona.

W tym przykładzie wywołasz polecenie, gdy suwak zostanie przeniesiony lub dokładniej <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> po zmianie właściwości.

Poniżej przedstawiono definicję klasy:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

Następnym krokiem jest <xref:System.Windows.Input.ICommandSource> zaimplementowanie elementów członkowskich. W tym przykładzie właściwości są <xref:System.Windows.DependencyProperty> implementowane jako obiekty. Dzięki temu właściwości do korzystania z powiązania danych. Aby uzyskać więcej <xref:System.Windows.DependencyProperty> informacji na temat klasy, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md). Aby uzyskać więcej informacji na temat powiązania danych, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).

W <xref:System.Windows.Input.ICommandSource.Command%2A> tym miejscu znajduje się tylko właściwość.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
Poniżej znajduje <xref:System.Windows.DependencyProperty> się wywołanie zwrotne zmiany:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

Następnym krokiem jest dodanie i usunięcie polecenia skojarzonego ze źródłem polecenia. Właściwość <xref:System.Windows.Input.ICommandSource.Command%2A> nie może być po prostu zastąpione po dodaniu nowego polecenia, ponieważ programy obsługi zdarzeń skojarzone z poprzednim poleceniem, jeśli istnieje, muszą zostać usunięte najpierw.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

Następnym krokiem jest utworzenie <xref:System.Windows.Input.ICommand.CanExecuteChanged> logiki dla programu obsługi.

Zdarzenie <xref:System.Windows.Input.ICommand.CanExecuteChanged> powiadamia źródło polecenia, że zdolność polecenia do wykonania na bieżącym celu polecenia może ulec zmianie. Gdy źródło polecenia odbiera to zdarzenie, <xref:System.Windows.Input.ICommand.CanExecute%2A> zazwyczaj wywołuje metodę w poleceniu. Jeśli polecenie nie może wykonać na bieżącym celu polecenia, źródło polecenia zwykle wyłączy się. Jeśli polecenie można wykonać na bieżącym celu polecenia, źródło polecenia zazwyczaj włącza się.

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

Ostatnim krokiem <xref:System.Windows.Input.ICommand.Execute%2A> jest metoda. Jeśli polecenie jest <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> metoda jest wywoływana; <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> w przeciwnym razie metoda jest wywoływana.

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Przegląd poleceń](commanding-overview.md)
