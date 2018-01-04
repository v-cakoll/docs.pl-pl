---
title: "Porady: Implementowanie wzorca przepływu danych producent — konsument"
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
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2cf5eea6a130d34df2cbcd84a08e63ff9c9bd260
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Porady: Implementowanie wzorca przepływu danych producent — konsument
Ten dokument zawiera opis sposobu umożliwia Implementowanie wzorca producent — konsument przepływu danych tpl. W tym wzorcu *producent* wysyła komunikaty do bloku komunikatów i *konsumenta* odczytuje wiadomości z tego bloku.  
  
> [!TIP]
>  Biblioteka przepływu danych tpl (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> przestrzeni nazw) nie jest rozpowszechniana z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aby zainstalować <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z menu projektu i wyszukaj w trybie online `Microsoft.Tpl.Dataflow` pakietu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano podstawowe producent — konsument modelu, który korzysta z przepływu danych. `Produce` Metoda zapisuje tablic zawierających losowych bajtów danych do <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> obiektu i `Consume` metoda odczytuje bajtów z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> obiektu. Działając w <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> i <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfejsów, zamiast ich typów pochodnych może zapisywać do ponownego użycia kodu, który może działać na różnych typów bloku przepływu danych. W tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> klasy. Ponieważ <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> klasa działa jako źródło zarówno zablokować, a także jako docelowy blok, producent i konsumenta można użyć obiektu współużytkowanego na przesyłanie danych.  
  
 `Produce` Wywołania metody <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> w pętli synchronicznie zapisu danych do blok docelowy. Po `Produce` metoda zapisuje wszystkie dane blok docelowy wywołuje <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metodę, aby wskazać, że blok nigdy nie będzie mieć dostępne dodatkowe dane. `Consume` Używa metody [async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) operatory ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) do asynchronicznie obliczać całkowita liczba bajtów odebranych z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektu. Do działania asynchronicznie, `Consume` wywołania metody <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> metody, aby otrzymać powiadomienie, gdy bloku źródłowego ma dostępnych danych i gdy bloku źródłowego nigdy nie będą miały dostępne dodatkowe dane.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W tym przykładzie używa tylko jednego użytkownika do przetwarzania danych źródłowych. Jeśli wielu klientów w aplikacji, użyj <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metody można odczytać danych z bloku źródłowego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metoda zwraca `False` kiedy dane są niedostępne. Gdy wielu klientów muszą uzyskać dostęp do bloku źródłowego współbieżnie, ten mechanizm gwarantuje, czy dane są nadal dostępne po wywołaniu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
