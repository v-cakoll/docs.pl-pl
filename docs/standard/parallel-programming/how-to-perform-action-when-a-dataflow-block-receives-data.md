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
ms.openlocfilehash: 54eb9723f44924919ca1b4631e35e1e4da4af2af
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666343"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Instrukcje: Wykonywanie akcji w przypadku odebrania danych przez blok przepływu danych
Typy *bloku wykonywania przepływu danych* wywołują delegata dostarczony przez użytkownika po odebraniu danych. Klasy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> i<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> są typu przepływu danych wykonywania. Możesz użyć `delegate` słowa kluczowego (`Sub` w Visual Basic), <xref:System.Action%601>, <xref:System.Func%602>lub wyrażenia lambda, gdy podajesz funkcję służbową do bloku przepływu danych wykonywania. W tym dokumencie opisano sposób użycia <xref:System.Func%602> i wyrażenia lambda do wykonania akcji w blokach wykonywania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 W poniższym przykładzie za pomocą przepływu danych można odczytać plik z dysku i oblicza liczbę bajtów w tym pliku, które są równe zero. Służy <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> on do odczytywania pliku i obliczania liczby bajtów zero oraz <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> do drukowania liczby 0 bajtów do konsoli. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Obiekt<xref:System.Func%602> określa obiekt, który ma być wykonywany, gdy bloki odbierają dane. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiekt używa wyrażenia lambda do drukowania do konsoli o liczbie bajtów, które są odczytywane.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Chociaż można podać wyrażenie lambda do <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektu, w tym przykładzie używa <xref:System.Func%602> się, aby włączyć `CountBytes` inny kod, aby użyć metody. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiekt używa wyrażenia lambda, ponieważ wykonana operacja jest specyficzna dla tego zadania i prawdopodobnie nie jest przydatna w innym kodzie. Aby uzyskać więcej informacji o tym, jak wyrażenia lambda działają w bibliotece zadań równoległych, zobacz [wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Podsumowanie sekcji typów delegatów w dokumencie [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) podsumowuje typy delegatów, które można dostarczyć <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> obiektów. W tabeli określono również, czy typ delegata działa synchronicznie, czy asynchronicznie.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ten przykład udostępnia delegata typu <xref:System.Func%602> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> do obiektu, aby wykonać zadanie synchronicznie bloku przepływu danych. Aby włączyć blok przepływu danych, aby zachowywać się asynchronicznie, podaj delegata typu <xref:System.Func%601> do bloku przepływu danych. Gdy blok przepływu danych zachowuje się asynchronicznie, zadanie bloku przepływu danych jest wykonywane tylko wtedy, gdy zwracany <xref:System.Threading.Tasks.Task%601> obiekt zostaje zakończony. Poniższy przykład modyfikuje `CountBytes` metodę i używa operatorów [asynchronicznych](../../csharp/language-reference/keywords/async.md) i [oczekujących](../../csharp/language-reference/keywords/await.md) ([asynchronicznych](../../visual-basic/language-reference/modifiers/async.md) i [oczekujących](../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic), aby asynchronicznie obliczyć łączną liczbę bajtów, które są równe zero w podanym pliku. <xref:System.IO.FileStream.ReadAsync%2A> Metoda wykonuje operacje odczytu pliku asynchronicznie.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Można również użyć asynchronicznych wyrażeń lambda do wykonania akcji w bloku przepływu danych wykonywania. Poniższy przykład modyfikuje <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiekt, który jest używany w poprzednim przykładzie, tak aby używał wyrażenia lambda do wykonywania pracy asynchronicznie.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
