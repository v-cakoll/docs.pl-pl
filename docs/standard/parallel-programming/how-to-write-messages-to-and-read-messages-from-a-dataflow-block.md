---
title: 'Porady: Pisanie i odbieranie wiadomości w bloku przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
ms.openlocfilehash: 58927803b741acf6c1964b35f6603e6901f9cbf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139288"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Porady: Pisanie i odbieranie wiadomości w bloku przepływu danych
W tym dokumencie opisano sposób używania biblioteki przepływu danych TPL do zapisywania wiadomości i odczytywania wiadomości z bloku przepływu danych. Biblioteka przepływu danych TPL udostępnia zarówno synchroniczne, jak i asynchroniczne metody zapisywania wiadomości i odczytywania wiadomości z bloku przepływu danych. Ten dokument <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> używa klasy. Klasa <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> buforuje komunikaty i zachowuje się zarówno jako źródło wiadomości, jak i jako obiekt docelowy wiadomości.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Synchronicznie zapisywanie i odczytywanie z bloku przepływu danych  
 W poniższym <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> przykładzie użyto <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> metody do zapisu do bloku przepływu danych i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody do odczytu z tego samego obiektu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Można również użyć <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metody do odczytu z bloku przepływu danych, jak pokazano w poniższym przykładzie. Metoda <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> nie blokuje bieżącego wątku i jest przydatna podczas okazjonalnie sondowania danych.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metoda działa synchronicznie, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiekt w poprzednich przykładach odbiera wszystkie dane przed drugą pętlą odczytuje dane. Poniższy przykład rozszerza pierwszy przykład <xref:System.Threading.Tasks.Parallel.Invoke%2A> za pomocą do odczytu i zapisu do bloku komunikatów jednocześnie. Ponieważ <xref:System.Threading.Tasks.Parallel.Invoke%2A> wykonuje akcje jednocześnie, wartości nie są <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> zapisywane do obiektu w określonej kolejności.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Asynchroniczne zapisywanie i odczytywanie z bloku przepływu danych  
 W poniższym <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> przykładzie użyto metody do zapisu asynchronicznego do <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiektu i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> metody asynchronicznie odczytywane z tego samego obiektu. W tym przykładzie [użyto async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) operatorów[(Async](../../visual-basic/language-reference/modifiers/async.md) i [Await](../../visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic) do asynchronicznego wysyłania danych do i odczytu danych z bloku docelowego. Metoda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> jest przydatna, gdy należy włączyć blok przepływu danych, aby odroczyć wiadomości. Metoda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> jest przydatna, gdy chcesz działać na danych, gdy te dane staną się dostępne. Aby uzyskać więcej informacji na temat sposobu propagowania wiadomości między blokami komunikatów, zobacz sekcję Przekazywanie komunikatów w [przepływie danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Pełny przykład  
 W poniższym przykładzie przedstawiono pełny kod tego dokumentu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przykładzie pokazano, jak odczytywać i zapisywać bezpośrednio do bloku wiadomości. Można również połączyć bloki przepływu danych do tworzenia *potoków,* które są liniowymi sekwencjami bloków przepływu danych lub *sieci*, które są wykresami bloków przepływu danych. W potoku lub sieci źródła asynchronicznie propagować dane do obiektów docelowych, jak te dane stają się dostępne. Na przykład, który tworzy podstawowy potok przepływu danych, zobacz [Instruktaż: Tworzenie potoku przepływu danych](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Na przykład, który tworzy bardziej złożoną sieć przepływu danych, zobacz [Instruktaż: Korzystanie z przepływu danych w aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
