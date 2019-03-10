---
title: Używanie delegatów działania
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 38b99446e38551a9954228eaa3682e2e81753ddb
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707537"
---
# <a name="using-activity-delegates"></a>Używanie delegatów działania
Działania delegatach Włącz autorzy działania do udostępnienia wywołania zwrotne z określonych podpisów, dla których użytkownicy, działania mogą podać obsługi na podstawie działania. Dostępne są dwa typy działania delegatach: <xref:System.Activities.ActivityAction%601> służy do definiowania delegatów działania, które nie mają wartości zwracanej i <xref:System.Activities.ActivityFunc%601> służy do definiowania delegatów działania, które mają wartość zwracaną.  
  
 Działania delegatach są przydatne w scenariuszach, gdzie działanie podrzędne muszą być ograniczone do o niektórych podpisu. Na przykład <xref:System.Activities.Statements.While> działanie może zawierać dowolnego typu działania podrzędnego bez ograniczeń, ale treść <xref:System.Activities.Statements.ForEach%601> działanie jest <xref:System.Activities.ActivityAction%601>, a działanie podrzędne, które ostatecznie jest wykonywana przez <xref:System.Activities.Statements.ForEach%601> musi mieć <xref:System.Activities.InArgument%601> , jest tego samego typu elementów członkowskich kolekcji, <xref:System.Activities.Statements.ForEach%601> wylicza.  
  
## <a name="using-activityaction"></a>Za pomocą elementu ActivityAction.  
 Kilka [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] działania korzystają akcje działania <xref:System.Activities.Statements.Catch> działania i <xref:System.Activities.Statements.ForEach%601> działania. W każdym przypadku akcja działania reprezentuje lokalizację, w których autor przepływu pracy określa działania, aby zapewnić żądane zachowanie podczas tworzenia przepływu pracy przy użyciu jednej z tych działań. W poniższym przykładzie <xref:System.Activities.Statements.ForEach%601> to działanie służy do wyświetlania tekstu w oknie konsoli. Treść <xref:System.Activities.Statements.ForEach%601> zostanie określony za pomocą <xref:System.Activities.ActivityAction%601> który jest zgodny z typem <xref:System.Activities.Statements.ForEach%601> czyli ciąg. <xref:System.Activities.Statements.WriteLine> Działania określonego w <xref:System.Activities.ActivityDelegate.Handler%2A> ma jego <xref:System.Activities.Statements.WriteLine.Text%2A> argument powiązany z wartości ciągu w kolekcji, <xref:System.Activities.Statements.ForEach%601> działanie wykonuje iterację.  
  
 [!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]  
  
 ActionArgument jest używany do poszczególnych elementów w kolekcji, WriteLine przepływu. Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
 ``` 
 HelloWorld.
 ```  
W przykładach w tym temacie używany składni inicjowania obiektu. Składnia inicjalizacji obiektu może być przydatny sposób do tworzenia definicji przepływu pracy w kodzie, ponieważ udostępnia hierarchiczny widok działań w przepływie pracy i przedstawiono relację między działaniami. Nie jest wymagane do programowego tworzenia przepływów pracy, użyj składni inicjowania obiektu. Poniższy przykład jest funkcjonalnie równoważny do poprzedniego przykładu.  
  
 [!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]  
  
 Aby uzyskać więcej informacji na temat inicjatorów obiektów zobacz [jak: Inicjowanie obiektów bez wywoływania konstruktora (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=161015) i [jak: Deklarowanie obiektu za pomocą inicjatora obiektów](https://go.microsoft.com/fwlink/?LinkId=161016).  
  
 W poniższym przykładzie <xref:System.Activities.Statements.TryCatch> działanie jest używane w przepływie pracy. <xref:System.ApplicationException> Jest generowany przez przepływ pracy i jest obsługiwany przez <xref:System.Activities.Statements.Catch%601> działania. Obsługa <xref:System.Activities.Statements.Catch%601> Akcja działania tego działania jest <xref:System.Activities.Statements.WriteLine> działanie i szczegóły wyjątku jest przekazane za pośrednictwem do niego przy użyciu `ex` <xref:System.Activities.DelegateInArgument%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Podczas tworzenia niestandardowego działania, który definiuje <xref:System.Activities.ActivityAction%601>, użyj <xref:System.Activities.Statements.InvokeAction%601> do wywołania tego modelu <xref:System.Activities.ActivityAction%601>. W tym przykładzie niestandardową `WriteLineWithNotification` działania jest zdefiniowana. To działanie składa się z <xref:System.Activities.Statements.Sequence> zawierający <xref:System.Activities.Statements.WriteLine> następuje działanie <xref:System.Activities.Statements.InvokeAction%601> wywołującej <xref:System.Activities.ActivityAction%601> przyjmującą jeden argument ciągu.  
  
 [!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]  
  
 Po utworzeniu przepływu pracy przy użyciu `WriteLineWithNotification` działanie, autor przepływu pracy określa odpowiednią logikę niestandardową w działaniu działania <xref:System.Activities.ActivityDelegate.Handler%2A>. W tym przykładzie przepływ pracy jest tworzony używające `WriteLineWithNotification` działania, a <xref:System.Activities.Statements.WriteLine> działania jest używana jako <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]  
  
 Istnieje wiele wersji ogólnych <xref:System.Activities.Statements.InvokeAction%601> i <xref:System.Activities.ActivityAction%601> dostarczone do przekazywania jeden lub więcej argumentów.  
  
## <a name="using-activityfunc"></a>Za pomocą ActivityFunc  
 <xref:System.Activities.ActivityAction%601> jest przydatne, gdy nie ma żadnej wartości wyniku z działania, a <xref:System.Activities.ActivityFunc%601> jest używany, gdy zostanie zwrócona wartość wyniku. Podczas tworzenia niestandardowego działania, który definiuje <xref:System.Activities.ActivityFunc%601>, użyj <xref:System.Activities.Expressions.InvokeFunc%601> do wywołania tego modelu <xref:System.Activities.ActivityFunc%601>. W poniższym przykładzie `WriteFillerText` działania jest zdefiniowana. Można podać tekst wypełniacza <xref:System.Activities.Expressions.InvokeFunc%601> jest określony, która przyjmuje argument, liczba całkowita i ma wynik w postaci ciągu. Po pobraniu wypełniacza tekst jest wyświetlany za pomocą konsoli <xref:System.Activities.Statements.WriteLine> działania.  
  
 [!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]  
  
 Umożliwiają określanie wartości tekstu, działania należy użyć, ma jedną `int` argumentu i ma wynik w postaci ciągu. W tym przykładzie `TextGenerator` działanie, które spełnia te wymagania.  
  
 [!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]  
  
 Aby użyć `TextGenerator` działanie przy użyciu `WriteFillerText` działania, określ ją jako <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
