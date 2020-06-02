---
title: 'Instrukcje: Zapisywanie komunikatów w bloku przepływu danych i odczytywanie ich z tego bloku'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
ms.openlocfilehash: 917892e16a3517800953437f2fce877a57a64575
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290710"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Instrukcje: Zapisywanie komunikatów w bloku przepływu danych i odczytywanie ich z tego bloku
W tym dokumencie opisano sposób używania biblioteki przepływu danych TPL do zapisywania komunikatów do i odczytywania komunikatów z bloku przepływu danych. Biblioteka TPL przepływu danych zapewnia metody synchroniczne i asynchroniczne do pisania komunikatów i odczytywania komunikatów z bloku przepływu danych. Ten dokument używa <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> klasy. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>Klasa buforuje komunikaty i zachowuje się jako źródło wiadomości oraz jako cel wiadomości.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Zapisywanie do i odczytywanie z bloku przepływu danych synchronicznie  
 Poniższy przykład używa <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metody do zapisu w <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> bloku przepływu danych i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody odczytu z tego samego obiektu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Można również użyć <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metody do odczytu z bloku przepływu danych, jak pokazano w poniższym przykładzie. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>Metoda nie blokuje bieżącego wątku i jest przydatna, gdy okresowo sondowasz o dane.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> Metoda działa synchronicznie, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiekt w poprzednich przykładach odbiera wszystkie dane, zanim Druga pętla odczytuje dane. Poniższy przykład rozszerza pierwszy przykład przy użyciu, <xref:System.Threading.Tasks.Parallel.Invoke%2A> aby odczytywać i zapisywać w bloku komunikatów współbieżnie. Ponieważ <xref:System.Threading.Tasks.Parallel.Invoke%2A> wykonuje akcje współbieżnie, wartości nie są zapisywane do <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiektu w żadnej określonej kolejności.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Asynchroniczne pisanie i odczytywanie z bloku przepływu danych  
 Poniższy przykład używa <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> metody do asynchronicznego zapisu do <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiektu i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> metody do asynchronicznego odczytu z tego samego obiektu. W tym przykładzie zastosowano operatory [Async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) i [await](../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic), aby asynchronicznie wysyłać dane do i odczytywać dane z bloku docelowego. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A>Metoda jest przydatna, gdy konieczne jest włączenie bloku przepływu danych w celu odłożenia komunikatów. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>Metoda jest przydatna, gdy chcesz działać na danych, gdy dane staną się dostępne. Aby uzyskać więcej informacji na temat sposobu propagowania komunikatów między blokami komunikatów, zobacz sekcję przekazywanie komunikatu w [przepływu danych](dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego dokumentu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 Ten przykład pokazuje, jak odczytywać i zapisywać bezpośrednio w bloku komunikatów. Można również połączyć bloki przepływu danych z *potokami*, które są sekwencjami liniowymi bloków przepływu danych lub *sieci*, które są wykresami bloków przepływu danych. W potoku lub sieci źródła asynchronicznie propagują dane do obiektów docelowych, ponieważ te dane staną się dostępne. Aby uzyskać przykład, który tworzy podstawowy potok przepływu danych, zobacz [Przewodnik: Tworzenie potoku przepływu danych](walkthrough-creating-a-dataflow-pipeline.md). Aby uzyskać przykład, który tworzy bardziej złożoną sieć przepływu danych, zobacz [Przewodnik: używanie przepływu danych w aplikacji Windows Forms](walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](dataflow-task-parallel-library.md)
