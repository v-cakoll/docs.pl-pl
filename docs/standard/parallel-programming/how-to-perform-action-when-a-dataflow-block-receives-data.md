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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124217"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Porady: Wykonaj operację, kiedy blok przepływu danych odbiera dane
*Typy bloków przepływu danych wykonywania* wywołać delegata dostarczonego przez użytkownika podczas odbierania danych. Typy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>bloków <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> przepływu danych i klasy są wykonywaniem bloków przepływu danych. Można użyć `delegate` słowa`Sub` kluczowego (w języku Visual Basic), <xref:System.Action%601>, <xref:System.Func%602>, lub wyrażenia lambda podczas dostarczania funkcji pracy do bloku przepływu danych wykonywania. W tym dokumencie <xref:System.Func%602> opisano sposób używania i lambda wyrażeń do wykonywania akcji w blokach wykonywania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto przepływu danych do odczytu pliku z dysku i oblicza liczbę bajtów w tym pliku, które są równe zero. Używa <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> się do odczytu pliku i obliczyć liczbę <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> bajtów zerowych oraz wydrukować liczbę bajtów zerowych do konsoli. Obiekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> określa <xref:System.Func%602> obiekt do wykonywania pracy, gdy bloki odbierają dane. Obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> używa wyrażenia lambda do drukowania do konsoli liczbę bajtów zerowych, które są odczytywane.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Mimo że można podać wyrażenie lambda do <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> <xref:System.Func%602> obiektu, w tym `CountBytes` przykładzie używa się, aby włączyć inny kod do korzystania z metody. Obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> używa wyrażenia lambda, ponieważ praca do wykonania jest specyficzna dla tego zadania i prawdopodobnie nie będzie przydatna z innego kodu. Aby uzyskać więcej informacji na temat działania wyrażeń lambda w bibliotece równoległej zadań, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Sekcja Podsumowanie typów delegatów w dokumencie [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) podsumowuje typy delegatów, które można podać <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>do , <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> obiekty. Tabela określa również, czy typ delegata działa synchronicznie, czy asynchronicznie.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W tym przykładzie przedstawiono <xref:System.Func%602> delegata <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> typu do obiektu do wykonywania zadania bloku przepływu danych synchronicznie. Aby włączyć blok przepływu danych zachowywać się asynchronicznie, <xref:System.Func%601> należy podać pełnomocnika typu do bloku przepływu danych. Gdy blok przepływu danych zachowuje się asynchronicznie, zadanie bloku przepływu danych jest <xref:System.Threading.Tasks.Task%601> zakończone tylko po zakończeniu zwracanego obiektu. Poniższy przykład modyfikuje `CountBytes` metodę i używa [asynchronicznych](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) operatorów[(Async](../../visual-basic/language-reference/modifiers/async.md) i [Await](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic) do asynchronicznie obliczyć całkowitą liczbę bajtów, które są zero we podanyplik. Metoda <xref:System.IO.FileStream.ReadAsync%2A> wykonuje operacje odczytu pliku asynchronicznie.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Można również użyć asynchronicznych wyrażeń lambda do wykonywania akcji w bloku przepływu danych wykonywania. Poniższy przykład modyfikuje <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiekt, który jest używany w poprzednim przykładzie, tak aby używał wyrażenia lambda do wykonywania pracy asynchronicznie.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
