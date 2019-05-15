---
title: 'Instrukcje: Wykonywanie akcji w przypadku odebrania danych przez blok przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f79b244f35bfe006b1f83f2689fe5fafcca4e6fd
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592030"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Instrukcje: Wykonywanie akcji w przypadku odebrania danych przez blok przepływu danych
*Wykonanie bloku przepływu danych* typy wywołanie delegata dostarczone przez użytkownika, po otrzymaniu danych. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, I <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> klasy są typami bloku przepływu danych wykonywania. Możesz użyć `delegate` — słowo kluczowe (`Sub` w języku Visual Basic), <xref:System.Action%601>, <xref:System.Func%602>, lub wyrażenie lambda, gdy zawierają funkcję pracy do wykonania bloku przepływu danych. W tym dokumencie opisano, jak używać <xref:System.Func%602> i wyrażenia lambda do wykonania akcji w blokach wykonywania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład używa przepływu danych do odczytu pliku z dysku i oblicza liczbę bajtów w pliku, które są równe zero. Używa ona <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> odczytać pliku do obliczenia liczby zero bajtów i <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> do drukowania liczby zero bajtów do konsoli. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Obiekt Określa <xref:System.Func%602> obiekt do wykonywania pracy po bloki odbierać dane. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiektu używa wyrażenia lambda do drukowania w konsoli liczba zero bajtów, które są do odczytu.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Chociaż można podać w wyrażeniu lambda <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiekt, w tym przykładzie użyto <xref:System.Func%602> umożliwiające inny kod, aby użyć `CountBytes` metody. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiektu używa wyrażenia lambda, ponieważ wykonanie pracy jest specyficzne dla tego zadania, a nie mogą być użyteczne z innego kodu. Aby uzyskać więcej informacji o działaniu wyrażeń lambda w bibliotece zadań równoległych, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Sekcja Podsumowanie delegować typów w [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokumencie przedstawiono podsumowanie typy delegatów, które można udostępnić <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> obiektów. Tabela określa również, czy typ delegata działa synchronicznie lub asynchronicznie.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poniższym przykładzie przedstawiono delegat typu <xref:System.Func%602> do <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektu w celu wykonania zadań w bloku przepływu danych synchronicznie. Aby włączyć bloku przepływu danych zachowywać się asynchronicznie, podaj delegat typu <xref:System.Func%601> blok przepływu danych. Gdy bloku przepływu danych działa w sposób asynchroniczny, zadanie bloku przepływu danych jest pełny tylko wtedy, gdy zwrócony <xref:System.Threading.Tasks.Task%601> obiektu zostanie zakończone. Poniższy przykład modyfikuje `CountBytes` metody i używa [async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) operatorów ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w Visual Basic), aby asynchronicznie obliczać całkowita liczba bajtów, które mają wartość zero w podanego pliku. <xref:System.IO.FileStream.ReadAsync%2A> Metoda asynchronicznie wykonuje operacje odczytu pliku.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Można również użyć wyrażenia asynchroniczne lambda do wykonania akcji w bloku przepływu danych wykonywania. Poniższy przykład modyfikuje <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiekt, który jest używany w poprzednim przykładzie, tak aby używał wyrażenia lambda do wykonywania pracy asynchronicznie.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
