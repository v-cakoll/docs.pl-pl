---
title: Używanie delegatów działania
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: cbcc8f8e498be4f79f8fed5af7cd3557d7c55981
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837574"
---
# <a name="using-activity-delegates"></a>Używanie delegatów działania
Delegaty działań umożliwiają autorom działania udostępnianie wywołań zwrotnych z określonymi podpisami, dla których użytkownicy działania mogą udostępniać programy obsługi oparte na działaniach. Dostępne są dwa typy delegatów aktywności: <xref:System.Activities.ActivityAction%601> służy do definiowania delegatów działań, które nie mają wartości zwracanej, a <xref:System.Activities.ActivityFunc%601> służy do definiowania delegatów działań, które mają wartość zwracaną.

Delegaty działania są przydatne w scenariuszach, w których działanie podrzędne musi być ograniczone do posiadania określonego podpisu. Na przykład działanie <xref:System.Activities.Statements.While> może zawierać dowolny typ działania podrzędnego bez ograniczeń, ale treść działania <xref:System.Activities.Statements.ForEach%601> jest <xref:System.Activities.ActivityAction%601>, a działanie podrzędne, które jest ostatecznie wykonywane przez <xref:System.Activities.Statements.ForEach%601>, musi mieć <xref:System.Activities.InArgument%601>, który jest tym samym typem elementów członkowskich kolekcji, których <xref:System.Activities.Statements.ForEach%601> Wyliczenie.

## <a name="using-activityaction"></a>Korzystanie z ActivityAction

W kilku działaniach [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] są używane akcje działania, takie jak działanie <xref:System.Activities.Statements.Catch> i działanie <xref:System.Activities.Statements.ForEach%601>. W każdym przypadku akcja działania reprezentuje lokalizację, w której autor przepływu pracy określa działanie, aby zapewnić żądane zachowanie podczas redagowania przepływu pracy przy użyciu jednej z tych działań. W poniższym przykładzie działanie <xref:System.Activities.Statements.ForEach%601> służy do wyświetlania tekstu w oknie konsoli. Treść <xref:System.Activities.Statements.ForEach%601> jest określana przy użyciu <xref:System.Activities.ActivityAction%601> odpowiadającego typowi <xref:System.Activities.Statements.ForEach%601>, który jest ciągiem. Działanie <xref:System.Activities.Statements.WriteLine> określone w <xref:System.Activities.ActivityDelegate.Handler%2A> ma swój <xref:System.Activities.Statements.WriteLine.Text%2A> argument związany z wartościami ciągu w kolekcji, które wykonuje iteracja działania <xref:System.Activities.Statements.ForEach%601>.

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

ActionArgument jest używany do przepływu poszczególnych elementów w kolekcji do WriteLine. Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.

```console
HelloWorld.
```

W przykładach w tym temacie użyto składni inicjowania obiektu. Składnia inicjowania obiektu może być przydatnym sposobem tworzenia definicji przepływu pracy w kodzie, ponieważ zawiera hierarchiczny widok działań w przepływie pracy i pokazuje relację między działaniami. Nie ma potrzeby używania składni inicjowania obiektów podczas programistycznego tworzenia przepływów pracy. Poniższy przykład jest funkcjonalnie równoważny z poprzednim przykładem.

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

Aby uzyskać więcej informacji na temat inicjatorów obiektów, zobacz [How to: Initialize obiektów bez wywoływania konstruktoraC# (Przewodnik programowania)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) i [instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md).

W poniższym przykładzie działanie <xref:System.Activities.Statements.TryCatch> jest używane w przepływie pracy. Przepływ pracy jest generowany <xref:System.ApplicationException> i jest obsługiwany przez działanie <xref:System.Activities.Statements.Catch%601>. Procedura obsługi działania <xref:System.Activities.Statements.Catch%601> działania jest działaniem <xref:System.Activities.Statements.WriteLine>, a szczegóły wyjątku są przepływane do niego przy użyciu <xref:System.Activities.DelegateInArgument%601>`ex`.

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

Podczas tworzenia niestandardowego działania definiującego <xref:System.Activities.ActivityAction%601>należy użyć <xref:System.Activities.Statements.InvokeAction%601> do modelowania wywołania tego <xref:System.Activities.ActivityAction%601>. W tym przykładzie zdefiniowano niestandardowe działanie `WriteLineWithNotification`. To działanie składa się z <xref:System.Activities.Statements.Sequence>, który zawiera <xref:System.Activities.Statements.WriteLine> działania, po którym następuje <xref:System.Activities.Statements.InvokeAction%601>, który wywołuje <xref:System.Activities.ActivityAction%601>, który przyjmuje jeden argument ciągu.

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

Gdy przepływ pracy jest tworzony przy użyciu działania `WriteLineWithNotification`, autor przepływu pracy określa żądaną logikę niestandardową w <xref:System.Activities.ActivityDelegate.Handler%2A>akcji działania. W tym przykładzie zostanie utworzony przepływ pracy, który używa działania `WriteLineWithNotification`, a działanie <xref:System.Activities.Statements.WriteLine> jest używane jako <xref:System.Activities.ActivityDelegate.Handler%2A>.

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

Istnieje wiele ogólnych wersji <xref:System.Activities.Statements.InvokeAction%601> i <xref:System.Activities.ActivityAction%601> podano do przekazania co najmniej jednego argumentu.

## <a name="using-activityfunc"></a>Korzystanie z ActivityFunc

<xref:System.Activities.ActivityAction%601> jest przydatne, gdy nie ma wartości wyniku z działania, a <xref:System.Activities.ActivityFunc%601> jest używana w przypadku zwrócenia wartości wyniku. Podczas tworzenia niestandardowego działania definiującego <xref:System.Activities.ActivityFunc%601>należy użyć <xref:System.Activities.Expressions.InvokeFunc%601> do modelowania wywołania tego <xref:System.Activities.ActivityFunc%601>. W poniższym przykładzie zdefiniowano działanie `WriteFillerText`. Aby podać tekst Filler, określono <xref:System.Activities.Expressions.InvokeFunc%601>, która przyjmuje argument typu integer i ma wynik ciągu. Po pobraniu tekstu wypełniającego jest on wyświetlany w konsoli programu przy użyciu działania <xref:System.Activities.Statements.WriteLine>.

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

Aby podać tekst, należy użyć działania, które przyjmuje jeden `int` argument i ma wynik ciąg. Ten przykład przedstawia działanie `TextGenerator`, które spełnia te wymagania.

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

Aby użyć działania `TextGenerator` z działaniem `WriteFillerText`, określ je jako <xref:System.Activities.ActivityDelegate.Handler%2A>.

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
