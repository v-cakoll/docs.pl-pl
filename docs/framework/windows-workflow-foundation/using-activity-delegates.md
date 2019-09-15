---
title: Używanie delegatów działania
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 63f550549456404b237067c98afdb18a8758dd7a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989083"
---
# <a name="using-activity-delegates"></a>Używanie delegatów działania
Delegaty działań umożliwiają autorom działania udostępnianie wywołań zwrotnych z określonymi podpisami, dla których użytkownicy działania mogą udostępniać programy obsługi oparte na działaniach. Dostępne są dwa typy delegatów aktywności: <xref:System.Activities.ActivityAction%601> służy do definiowania delegatów działań, które nie mają wartości zwracanej, i <xref:System.Activities.ActivityFunc%601> służy do definiowania delegatów działań, które mają wartość zwracaną.

Delegaty działania są przydatne w scenariuszach, w których działanie podrzędne musi być ograniczone do posiadania określonego podpisu. Na <xref:System.Activities.Statements.While> przykład działanie może zawierać dowolny typ działania podrzędnego bez ograniczeń, ale treść <xref:System.Activities.ActivityAction%601> <xref:System.Activities.Statements.ForEach%601> działania to, a działanie podrzędne, <xref:System.Activities.InArgument%601> które jest ostatecznie wykonywane przez <xref:System.Activities.Statements.ForEach%601> , musi mieć to jest tym samym typem elementów członkowskich kolekcji, których <xref:System.Activities.Statements.ForEach%601> Wyliczenie.

## <a name="using-activityaction"></a>Korzystanie z ActivityAction

Niektóre [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] działania wykorzystują akcje działania, takie <xref:System.Activities.Statements.Catch> jak działanie i <xref:System.Activities.Statements.ForEach%601> działanie. W każdym przypadku akcja działania reprezentuje lokalizację, w której autor przepływu pracy określa działanie, aby zapewnić żądane zachowanie podczas redagowania przepływu pracy przy użyciu jednej z tych działań. W poniższym przykładzie <xref:System.Activities.Statements.ForEach%601> działanie jest używane do wyświetlania tekstu w oknie konsoli. Treść <xref:System.Activities.Statements.ForEach%601> jest określana za <xref:System.Activities.ActivityAction%601> pomocą, która jest <xref:System.Activities.Statements.ForEach%601> zgodna z typem, który jest ciągiem. Działanie określone <xref:System.Activities.Statements.WriteLine.Text%2A> w elemencie <xref:System.Activities.Statements.ForEach%601> ma jego argument powiązany z wartościami ciągu w kolekcji, które wykonuje iteracja działania. <xref:System.Activities.ActivityDelegate.Handler%2A> <xref:System.Activities.Statements.WriteLine>

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

ActionArgument jest używany do przepływu poszczególnych elementów w kolekcji do WriteLine. Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.

```console
HelloWorld.
```

W przykładach w tym temacie użyto składni inicjowania obiektu. Składnia inicjowania obiektu może być przydatnym sposobem tworzenia definicji przepływu pracy w kodzie, ponieważ zawiera hierarchiczny widok działań w przepływie pracy i pokazuje relację między działaniami. Nie ma potrzeby używania składni inicjowania obiektów podczas programistycznego tworzenia przepływów pracy. Poniższy przykład jest funkcjonalnie równoważny z poprzednim przykładem.

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

Aby uzyskać więcej informacji na temat inicjatorów obiektów [, zobacz How to: Inicjuj obiekty bez wywoływania konstruktora (C# Przewodnik programowania)](https://go.microsoft.com/fwlink/?LinkId=161015) i [instrukcje: Zadeklaruj obiekt za pomocą inicjatora](https://go.microsoft.com/fwlink/?LinkId=161016)obiektów.

W poniższym przykładzie <xref:System.Activities.Statements.TryCatch> działanie jest używane w przepływie pracy. Jest generowany przez przepływ pracy i jest obsługiwany <xref:System.Activities.Statements.Catch%601> przez działanie. <xref:System.ApplicationException> Obsługa <xref:System.Activities.Statements.Catch%601> akcji działania działania <xref:System.Activities.Statements.WriteLine> jest działaniem, a szczegóły wyjątku są przepływane do niego przy użyciu `ex`. <xref:System.Activities.DelegateInArgument%601>

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

Podczas tworzenia niestandardowego działania, które definiuje <xref:System.Activities.ActivityAction%601>, należy <xref:System.Activities.Statements.InvokeAction%601> użyć do modelowania wywołania tego <xref:System.Activities.ActivityAction%601>elementu. W tym przykładzie zdefiniowano działanie `WriteLineWithNotification` niestandardowe. To działanie składa się z <xref:System.Activities.Statements.Sequence> , która <xref:System.Activities.Statements.WriteLine> zawiera działanie, po którym <xref:System.Activities.Statements.InvokeAction%601> następuje wywołanie <xref:System.Activities.ActivityAction%601> , które przyjmuje jeden argument ciągu.

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

Gdy przepływ pracy jest tworzony przy użyciu `WriteLineWithNotification` działania, autor przepływu pracy określa żądaną logikę niestandardową w ramach <xref:System.Activities.ActivityDelegate.Handler%2A>akcji działania. W tym przykładzie zostanie utworzony przepływ pracy, który używa `WriteLineWithNotification` działania, <xref:System.Activities.Statements.WriteLine> a <xref:System.Activities.ActivityDelegate.Handler%2A>działanie jest używane jako.

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

Istnieje wiele wersji <xref:System.Activities.Statements.InvokeAction%601> ogólnych i <xref:System.Activities.ActivityAction%601> dostarczonych do przekazywania co najmniej jednego argumentu.

## <a name="using-activityfunc"></a>Korzystanie z ActivityFunc

<xref:System.Activities.ActivityAction%601>jest przydatne, gdy nie ma wartości wyniku działania i <xref:System.Activities.ActivityFunc%601> jest używana w przypadku zwrócenia wartości wyniku. Podczas tworzenia niestandardowego działania, które definiuje <xref:System.Activities.ActivityFunc%601>, należy <xref:System.Activities.Expressions.InvokeFunc%601> użyć do modelowania wywołania tego <xref:System.Activities.ActivityFunc%601>elementu. W poniższym przykładzie `WriteFillerText` zdefiniowano działanie. Aby podać tekst wypełniający, jest określany jako <xref:System.Activities.Expressions.InvokeFunc%601> argument typu integer i ma wynik ciąg. Po pobraniu tekstu Filler jest on wyświetlany w konsoli programu przy użyciu <xref:System.Activities.Statements.WriteLine> działania.

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

Aby podać tekst, należy użyć działania, które przyjmuje jeden `int` argument i ma wynik ciąg. Ten przykład pokazuje `TextGenerator` działanie spełniające te wymagania.

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

Aby użyć `TextGenerator` działania `WriteFillerText` z działaniem <xref:System.Activities.ActivityDelegate.Handler%2A>, określ je jako.

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
