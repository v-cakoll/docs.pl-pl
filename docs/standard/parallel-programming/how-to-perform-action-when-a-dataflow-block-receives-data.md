---
title: 'Porady: Wykonaj operację, kiedy blok przepływu danych odbiera dane'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 99f2f7184f869902f89eb0ac0fc8427533978cc3
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Porady: Wykonaj operację, kiedy blok przepływu danych odbiera dane
*Wykonanie bloku przepływu danych* typy wywołać delegata dostarczane przez użytkownika, po odebraniu danych. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, I <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> klasy są typy bloku przepływu danych wykonywania. Można użyć `delegate` — słowo kluczowe (`Sub` w języku Visual Basic), <xref:System.Action%601>, <xref:System.Func%602>, lub wyrażenia lambda, podając funkcję Praca do wykonywania bloku przepływu danych. W tym dokumencie opisano sposób użycia <xref:System.Func%602> i wyrażenia lambda do wykonania akcji w blokach wykonywania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład korzysta z przepływu danych w celu odczytania pliku z dysku i oblicza liczbę bajtów w pliku, które są równe zero. Używa <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> do odczytania danego pliku i obliczanie liczby zero bajtów i <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> do drukowania liczby zero bajtów do konsoli. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Określa obiekt <xref:System.Func%602> obiektu do wykonywania pracy, gdy bloki odbierać dane. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiekt używa wyrażenia lambda drukowanie do konsoli liczba zero bajtów, które są do odczytu.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Chociaż można podać wyrażenia lambda do <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektu, w tym przykładzie użyto <xref:System.Func%602> umożliwiające inny kod, aby użyć `CountBytes` metody. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiekt używa wyrażenia lambda, ponieważ pracy do wykonania jest specyficzne dla tego zadania, a nie mogą być użyteczne z innych kodu. Aby uzyskać więcej informacji na temat działania wyrażeń lambda w bibliotece równoległych zadań, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Sekcja Podsumowanie delegować typów w [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokumencie przedstawiono podsumowanie typów delegata, które można udostępniać użytkownikom <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> obiektów. Tabela określa również, czy typ delegata działa synchronicznie lub asynchronicznie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowExecutionBlocks.cs` (`DataflowExecutionBlocks.vb` w języku Visual Basic), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 Visual C#  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poniższym przykładzie przedstawiono delegowanego typu <xref:System.Func%602> do <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektu w celu wykonania zadań w bloku przepływu danych synchronicznie. Aby włączyć bloku przepływu danych zachowanie asynchronicznie, podaj delegowanego typu <xref:System.Func%601> do bloku przepływu danych. Gdy bloku przepływu danych działa w sposób asynchroniczny, zadanie bloku przepływu danych jest pełny tylko wtedy, gdy zwracana <xref:System.Threading.Tasks.Task%601> obiekt zakończenie. Poniższy przykład modyfikuje `CountBytes` — metoda i używa [async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) operatory ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w Visual Basic), aby asynchronicznie obliczać całkowita liczba bajtów, które są zero w wybrany plik. <xref:System.IO.FileStream.ReadAsync%2A> Metoda wykonuje operacje odczytu pliku asynchronicznie.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Umożliwia także wyrażenia asynchroniczne lambda do wykonania akcji w bloku przepływu danych wykonywania. Poniższy przykład modyfikuje <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiekt, który jest używany w poprzednim przykładzie, tak aby były używane do wykonywania pracy asynchronicznego wyrażenia lambda.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
