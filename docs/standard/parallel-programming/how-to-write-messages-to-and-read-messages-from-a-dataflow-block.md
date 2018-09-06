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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47a61a1d01984eeefb2f1f09774374dc29a774d3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039228"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Porady: Pisanie i odbieranie wiadomości w bloku przepływu danych
W tym dokumencie opisano, jak przy użyciu biblioteki przepływu danych TPL pisanie i odbieranie wiadomości w bloku przepływu danych. Biblioteka przepływu danych TPL zapewnia synchroniczne i asynchroniczne metody zapisywania wiadomości i odczytywać wiadomości w bloku przepływu danych. Ten dokument używa <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> klasy. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Klasy buforuje wiadomości i działa jako źródła komunikatów i jako obiektu docelowego komunikatu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Zapisywanie i odczytywanie z bloku przepływu danych synchronicznie  
 W poniższym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metodę, aby zapisać <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> bloku przepływu danych i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metodę w celu odczytania z tego samego obiektu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Można również użyć <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metodę w celu odczytania z bloku przepływu danych, jak pokazano w poniższym przykładzie. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metoda blokują bieżący wątek i jest przydatne w przypadku sporadycznie sondować danych.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metoda działa synchronicznie, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiektu w poprzednich przykładach odbiera wszystkie dane, zanim drugi pętli odczytuje dane. Poniższy przykład rozszerza pierwszy przykład za pomocą <xref:System.Threading.Tasks.Parallel.Invoke%2A> do odczytu i zapisu do bloku wiadomości jednocześnie. Ponieważ <xref:System.Threading.Tasks.Parallel.Invoke%2A> wykonuje akcje równocześnie, wartości nie są zapisywane w <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiektu w dowolnej kolejności.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Zapisywanie i asynchronicznego odczytywania z bloku przepływu danych  
 W poniższym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> metody do asynchronicznego zapisu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiektu i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> metodę do asynchronicznego odczytania z tego samego obiektu. W tym przykładzie użyto [async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) operatorów ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic) do asynchronicznego wysyłania danych do odczytu pobiera dane z blok docelowy. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> Metoda jest przydatna, gdy należy włączyć bloku przepływu danych można odroczyć wiadomości. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> Metoda jest przydatna, gdy użytkownik chce działać na danych, po udostępnieniu tych danych. Aby uzyskać więcej informacji na temat sposobu wiadomości propagowane wśród bloki komunikatów, zobacz sekcję przekazywanie komunikatów w [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego dokumentu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowReadWrite.cs` (`DataflowReadWrite.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.  
  
 Visual C#  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## <a name="next-steps"></a>Następne kroki  
 Ten przykład pokazuje, jak odczytywanie i zapisywanie do bloku wiadomości bezpośrednio. Bloków przepływu danych można też połączyć do formularza *potoki*, służą do liniowej sekwencje bloków przepływu danych lub *sieci*, które są wykresy bloków przepływu danych. W potoku lub w sieci źródeł asynchronicznie propagowanie danych do celów danych staje się dostępna. Na przykład, który tworzy potok podstawowe przepływu danych, zobacz [wskazówki: tworzenie potoku przepływu danych](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Aby uzyskać przykład tworzenia bardziej złożonych sieci przepływu danych, zobacz [wskazówki: Korzystanie z przepływu danych w aplikacji Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
