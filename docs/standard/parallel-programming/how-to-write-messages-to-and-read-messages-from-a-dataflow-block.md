---
title: "Porady: Pisanie i odbieranie wiadomości w bloku przepływu danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45cbf9fc6ecda5c1695ee3441fab7fde6c423861
ms.sourcegitcommit: 5bfcb8d341239df251351f318038d31cdc9159d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Porady: Pisanie i odbieranie wiadomości w bloku przepływu danych
Ten dokument zawiera opis sposobu przepływu danych tpl umożliwia pisanie i odbieranie wiadomości w bloku przepływu danych. Biblioteka przepływu danych tpl udostępnia metody synchroniczne i asynchroniczne do zapisywania wiadomości i odczytywania wiadomości w bloku przepływu danych. Ten dokument używa <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> klasy. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Klasy buforuje wiadomości i działa jako źródła komunikatów i jako obiektu docelowego komunikatu.  
  
> [!TIP]
>  Biblioteka przepływu danych tpl ( <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw) nie jest dystrybuowane z programu .NET Framework. Aby zainstalować <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w programie Visual Studio, wybierz pozycję **Zarządzaj pakietami NuGet** z **projektu** menu, a następnie wyszukaj w trybie online `System.Threading.Tasks.Dataflow` pakietu.  

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Zapisywania i odczytywania synchronicznie z bloku przepływu danych  
 W poniższym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metodę, aby zapisać <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> bloku przepływu danych i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody do odczytu z tego samego obiektu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Można również użyć <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metody do odczytu z bloku przepływu danych, jak pokazano w poniższym przykładzie. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> — Metoda nie blokuje bieżącego wątku co jest przydatne w przypadku czasami sondować danych.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metody działa synchronicznie, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiektu w poprzednich przykładach odbiera wszystkie dane, zanim drugiej pętli odczytuje dane. Poniższy przykład rozszerza pierwszym przykładzie przy użyciu <xref:System.Threading.Tasks.Parallel.Invoke%2A> do odczytu i zapisu bloku komunikatów jednocześnie. Ponieważ <xref:System.Threading.Tasks.Parallel.Invoke%2A> wykonuje akcje równocześnie, wartości nie są zapisywane w <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiektu w dowolnej kolejności.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Zapisywanie w i asynchronicznego odczytywania z bloku przepływu danych  
 W poniższym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> metody do asynchronicznego zapisu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> obiektu i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> metodę, aby asynchronicznie odczytywane z tego samego obiektu. W tym przykładzie użyto [async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) operatory ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic) do asynchronicznego wysyłania danych do odczytu dane z blok docelowy. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> Metoda jest przydatna, gdy należy włączyć bloku przepływu danych odłożyć wiadomości. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> Metody jest przydatne, gdy mają działanie w danych po udostępnieniu tych danych. Aby uzyskać więcej informacji na temat jak Propagacja wiadomości między bloki komunikatów, zobacz sekcję przekazywanie komunikatów w [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Pełny przykład  
 Poniższy przykład przedstawia kompletny kod dla tego dokumentu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowReadWrite.cs` (`DataflowReadWrite.vb` dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przykładzie pokazano, jak można odczytywać i zapisywać bezpośrednio do bloku komunikatów. Możesz również nawiązać bloków przepływu danych formularza *potoki*, liniowego sekwencji bloków przepływu danych, które są lub *sieci*, wykresy bloków przepływu danych, które są. W potoku lub w sieci źródeł asynchronicznie propagację danych do obiektów docelowych, wraz ze wzrostem dostępności danych. Na przykład, który tworzy potoku przepływu danych podstawowych, zobacz [wskazówki: tworzenie potoku przepływu danych](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Aby uzyskać przykład tworzenia bardziej złożonych sieci przepływu danych, zobacz [wskazówki: Korzystanie z przepływu danych w aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
