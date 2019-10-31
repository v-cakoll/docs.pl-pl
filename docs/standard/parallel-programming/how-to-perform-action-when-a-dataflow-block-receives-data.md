---
title: 'Porady: Wykonaj operację, kiedy blok przepływu danych odbiera dane'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
ms.openlocfilehash: 89ab2bb18e5fe00a4d1b79d911bb0f7524b83104
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124217"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Porady: Wykonaj operację, kiedy blok przepływu danych odbiera dane
Typy *bloku wykonywania przepływu danych* wywołują delegata dostarczony przez użytkownika po odebraniu danych. Klasy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> są typu przepływu danych wykonywania. Można użyć słowa kluczowego `delegate` (`Sub` w Visual Basic), <xref:System.Action%601>, <xref:System.Func%602>lub wyrażenia lambda, gdy podajesz funkcję służbową do bloku przepływu danych wykonywania. W tym dokumencie opisano sposób używania <xref:System.Func%602> i wyrażeń lambda do wykonywania akcji w blokach wykonywania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 W poniższym przykładzie za pomocą przepływu danych można odczytać plik z dysku i oblicza liczbę bajtów w tym pliku, które są równe zero. Używa <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, aby odczytać plik i obliczyć liczbę bajtów równą zero, a <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, aby wydrukować liczbę 0 bajtów do konsoli. Obiekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> określa obiekt <xref:System.Func%602> do wykonania pracy, gdy bloki odbierają dane. Obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> używa wyrażenia lambda do drukowania do konsoli o liczbie bajtów, które są odczytywane.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Chociaż można podać wyrażenie lambda do obiektu <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, w tym przykładzie użyto <xref:System.Func%602>, aby umożliwić innemu kodowi użycie metody `CountBytes`. Obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> używa wyrażenia lambda, ponieważ wykonana operacja jest specyficzna dla tego zadania i prawdopodobnie nie jest przydatna w innym kodzie. Aby uzyskać więcej informacji o tym, jak wyrażenia lambda działają w bibliotece zadań równoległych, zobacz [wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Podsumowanie sekcji typów delegatów w dokumencie [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) podsumowuje typy delegatów, które można dostarczyć do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> obiektów. W tabeli określono również, czy typ delegata działa synchronicznie, czy asynchronicznie.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ten przykład udostępnia delegata typu <xref:System.Func%602> do obiektu <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> w celu synchronicznego wykonania zadania bloku przepływu danych. Aby włączyć blok przepływu danych, aby zachowywać się asynchronicznie, podaj delegata typu <xref:System.Func%601> do bloku przepływu danych. Gdy blok przepływu danych zachowuje się asynchronicznie, zadanie bloku przepływu danych jest uzupełniane tylko wtedy, gdy zwracany jest obiekt <xref:System.Threading.Tasks.Task%601>. Poniższy przykład modyfikuje metodę `CountBytes` i używa operatorów [Async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) i [await](../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic), aby asynchronicznie obliczyć łączną liczbę bajtów, które są równe zero w danym pliku. Metoda <xref:System.IO.FileStream.ReadAsync%2A> wykonuje operacje odczytu pliku asynchronicznie.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Można również użyć asynchronicznych wyrażeń lambda do wykonania akcji w bloku przepływu danych wykonywania. Poniższy przykład modyfikuje obiekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, który jest używany w poprzednim przykładzie, tak aby używał wyrażenia lambda do wykonywania pracy asynchronicznie.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
