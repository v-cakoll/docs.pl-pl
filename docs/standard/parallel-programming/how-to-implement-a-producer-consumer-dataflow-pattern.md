---
title: 'Instrukcje: Implementowanie wzorca przepływu danych producent — konsument'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ad212117cc51c17b2a0f68a98bee24e1dd3fa05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962555"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Instrukcje: Implementowanie wzorca przepływu danych producent — konsument
W tym dokumencie opisano sposób umożliwia Implementowanie wzorca producent — konsument Biblioteka przepływu danych TPL. W tym wzorcu *producentów* wysyła komunikaty do bloku komunikatu i *konsumenta* odczytuje komunikaty z tego bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano modelu podstawowe producent — konsument, która używa przepływu danych. `Produce` Metoda zapisuje tablic, które zawierają losowych bajtów danych do <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> obiektu i `Consume` metoda odczytuje bajtów z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> obiektu. Działając na <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> i <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfejsów, zamiast ich typów pochodnych napisania kodu wielokrotnego użytku, które mogą działać na różnych typów bloków przepływu danych. W tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> klasy. Ponieważ <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> block klasa działa jako oba źródła i blok docelowy, producenta i konsumenta przy użyciu udostępnionych obiektów transferu danych.  
  
 `Produce` Wywołania metody <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metody w pętli synchronicznie zapisu danych do bloku docelowego. Po `Produce` metoda zapisuje wszystkie dane blok docelowy wywołuje <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metodę w celu wskazania bloku nigdy nie będzie miała dostępnych dodatkowych danych. `Consume` Metoda używa [async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) operatorów ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic) do asynchronicznego Całkowita liczba bajtów odebranych od obliczenia <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektu. Aby działają asynchronicznie, `Consume` wywołania metody <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> metodę, aby otrzymywać powiadomienia, gdy blok źródłowy ma dostępnych danych i gdy blok źródłowy nigdy nie ma dostępnych dodatkowych danych.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w wierszu polecenia dla deweloperów programu Visual Studio okna.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Poprzedni przykład wykorzystuje tylko jednego użytkownika do przetwarzania danych źródłowych. Jeśli masz wielu odbiorców w aplikacji, użyj <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metody, które można odczytać danych z blok źródłowy, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metoda zwraca `False` gdy dane są niedostępne. Po wielu odbiorców musi uzyskać dostęp do bloku źródłowego jednocześnie, ten mechanizm gwarantuje, że dane są nadal dostępne po wywołaniu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
