---
title: Używanie delegatów działania
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8b30882ef2e75f21c3b90d0e13ff06b52fe5229
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="using-activity-delegates"></a>Używanie delegatów działania
Działanie delegatów Włącz autorów działania do udostępnienia wywołań zwrotnych z określonych podpisów, dla których użytkownik działania można podać oparte na działaniu programów obsługi. Dostępne są dwa typy delegatów działania: <xref:System.Activities.ActivityAction%601> służy do definiowania obiektów delegowanych działania, które nie mają zwracanych wartości, i <xref:System.Activities.ActivityFunc%601> służy do definiowania delegatów działania, które mają wartość zwracaną.  
  
 Działanie delegatów są przydatne w scenariuszach, w którym działanie podrzędne musi ograniczonym do elementu o niektórych podpisu. Na przykład <xref:System.Activities.Statements.While> działania może zawierać działania podrzędnego z ograniczeniami nie dowolnego typu, ale treść <xref:System.Activities.Statements.ForEach%601> działanie jest <xref:System.Activities.ActivityAction%601>, a ostatecznie jest wykonywana przez działanie podrzędne <xref:System.Activities.Statements.ForEach%601> musi mieć <xref:System.Activities.InArgument%601> który jest ten sam typ elementów członkowskich kolekcji które <xref:System.Activities.Statements.ForEach%601> wylicza.  
  
## <a name="using-activityaction"></a>Przy użyciu ActivityAction  
 Kilka [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] działania użyj akcji działania, takie jak <xref:System.Activities.Statements.Catch> działania i <xref:System.Activities.Statements.ForEach%601> działania. W każdym przypadku akcja działania reprezentuje lokalizację gdzie Autor przepływu pracy określa działania, aby zapewnić zachowanie podczas tworzenia przepływu pracy przy użyciu jednej z tych działań. W poniższym przykładzie <xref:System.Activities.Statements.ForEach%601> to działanie służy do wyświetlania tekstu w oknie konsoli. Treść <xref:System.Activities.Statements.ForEach%601> jest określana za pomocą <xref:System.Activities.ActivityAction%601> odpowiadającego typu <xref:System.Activities.Statements.ForEach%601> który jest ciągiem. <xref:System.Activities.Statements.WriteLine> Działania określone w <xref:System.Activities.ActivityDelegate.Handler%2A> ma jego <xref:System.Activities.Statements.WriteLine.Text%2A> argument powiązany z ciągami w kolekcji które <xref:System.Activities.Statements.ForEach%601> iteruje działania.  
  
 [!code-csharp[CFX_ActivityExample#6](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]  
  
 ActionArgument służy do poszczególnych elementów w kolekcji do WriteLine przepływu. Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
 ``` 
 HelloWorld.
 ```  
Przykłady w tym temacie należy użyć składni inicjalizacji obiektu. Składnia inicjalizacji obiektu może być przydatne do tworzenia definicji przepływu pracy w kodzie, ponieważ zawiera hierarchiczny widok działań w przepływie pracy i przedstawiono relacje między działaniami. Nie jest wymagany do programowego tworzenia przepływów pracy, użyj składni inicjalizacji obiektu. Poniższy przykład jest funkcjonalnym odpowiednikiem poprzedniego przykładu.  
  
 [!code-csharp[CFX_ActivityExample#7](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]  
  
 Aby uzyskać więcej informacji na temat inicjatory obiektów, zobacz [porady: Inicjowanie obiektów bez wywoływania konstruktora (C# przewodnik programowania w języku)](http://go.microsoft.com/fwlink/?LinkId=161015) i [porady: deklarowanie obiektu za pomocą inicjatora obiektów](http://go.microsoft.com/fwlink/?LinkId=161016).  
  
 W poniższym przykładzie <xref:System.Activities.Statements.TryCatch> działanie jest używane w przepływie pracy. <xref:System.ApplicationException> Jest generowany przez przepływ pracy i jest obsługiwany przez <xref:System.Activities.Statements.Catch%601> działania. Program obsługi dla <xref:System.Activities.Statements.Catch%601> Akcja działania działania jest <xref:System.Activities.Statements.WriteLine> działania i szczegóły wyjątku jest umieszczane za pośrednictwem do niej przy użyciu `ex` <xref:System.Activities.DelegateInArgument%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Podczas tworzenia działań niestandardowych, który definiuje <xref:System.Activities.ActivityAction%601>, użyj <xref:System.Activities.Statements.InvokeAction%601> do wywołania w tym modelu <xref:System.Activities.ActivityAction%601>. W tym przykładzie niestandardowego `WriteLineWithNotification` zdefiniowano działania. To działanie składa się z <xref:System.Activities.Statements.Sequence> zawierający <xref:System.Activities.Statements.WriteLine> następuje działanie <xref:System.Activities.Statements.InvokeAction%601> który wywołuje <xref:System.Activities.ActivityAction%601> który przyjmuje jeden argument ciągu.  
  
 [!code-csharp[CFX_ActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]  
  
 Po utworzeniu przepływu pracy przy użyciu `WriteLineWithNotification` działania, autor przepływu pracy określa żądaną niestandardowej logiki w akcji działania <xref:System.Activities.ActivityDelegate.Handler%2A>. W tym przykładzie przepływ pracy jest tworzony używające `WriteLineWithNotification` działania, a <xref:System.Activities.Statements.WriteLine> to działanie służy jako <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]  
  
 Istnieje wiele wersji ogólnego <xref:System.Activities.Statements.InvokeAction%601> i <xref:System.Activities.ActivityAction%601> przewidzianych przekazywanie jednego lub więcej argumentów.  
  
## <a name="using-activityfunc"></a>Przy użyciu ActivityFunc  
 <xref:System.Activities.ActivityAction%601> jest przydatne, gdy nie ma żadnej wartości wyników z działania, a <xref:System.Activities.ActivityFunc%601> jest używany, gdy zostanie zwrócona wartość wyniku. Podczas tworzenia działań niestandardowych, który definiuje <xref:System.Activities.ActivityFunc%601>, użyj <xref:System.Activities.Expressions.InvokeFunc%601> do wywołania w tym modelu <xref:System.Activities.ActivityFunc%601>. W poniższym przykładzie `WriteFillerText` zdefiniowano działania. Przydzielenie tekst wypełniacza <xref:System.Activities.Expressions.InvokeFunc%601> jest określony, które przyjmuje argument liczby całkowitej i ma wynik ciągu. Po pobraniu wypełniacza tekstu jest wyświetlana na konsoli za pomocą <xref:System.Activities.Statements.WriteLine> działania.  
  
 [!code-csharp[CFX_ActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]  
  
 Przydzielenie tekstu, działanie musi być używany przyjmuje jeden `int` argumentu i ma wynik ciągu. W tym przykładzie pokazano `TextGenerator` działanie, które spełnia te wymagania.  
  
 [!code-csharp[CFX_ActivityExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]  
  
 Aby użyć `TextGenerator` działania o `WriteFillerText` działania, określ go jako <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#5](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Uwidacznianie i wywoływanie działań ActivityActions](../../../docs/framework/windows-workflow-foundation/samples/exposing-and-invoking-activityactions.md)
