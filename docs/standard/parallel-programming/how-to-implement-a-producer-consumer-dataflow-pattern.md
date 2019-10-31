---
title: 'Porady: Implementowanie wzorca przepływu danych producent — konsument'
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
ms.openlocfilehash: 2db8cfcfc26b001703e08a501c430be4313aca03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091486"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Porady: Implementowanie wzorca przepływu danych producent — konsument
W tym dokumencie opisano sposób użycia biblioteki TPL przepływu danych do wdrożenia wzorca producenta. W tym wzorcu *producent* wysyła komunikaty do bloku komunikatów, a *konsument* odczytuje komunikaty z tego bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano podstawowy model konsumencki-konsumenta, który używa przepływu danych. Metoda `Produce` zapisuje tablice zawierające losowe bajty danych do obiektu <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType>, a metoda `Consume` odczytuje bajty z obiektu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType>. Działając na <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> i <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfejsy zamiast ich typów pochodnych można napisać kod wielokrotnego użytku, który może działać na różnych typach bloków przepływu danych. Ten przykład używa klasy <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>. Ponieważ Klasa <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> działa jako blok źródłowy i jako blok docelowy, producent i odbiorca mogą wykorzystać obiekt współużytkowany do transferowania danych.  
  
 Metoda `Produce` wywołuje metodę <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> w pętli, aby synchronicznie zapisywać dane w bloku docelowym. Po `Produce` Metoda zapisuje wszystkie dane w bloku docelowym, wywołuje metodę <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>, aby wskazać, że blok nigdy nie będzie miał dodatkowych dostępnych danych. Metoda `Consume` używa operatorów [Async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) i [await](../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic), aby asynchronicznie obliczyć łączną liczbę bajtów odebranych z obiektu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>. Aby działać asynchronicznie, Metoda `Consume` wywołuje metodę <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>, aby otrzymać powiadomienie, gdy blok źródłowy ma dostępne dane, a blok źródłowy nigdy nie będzie miał dodatkowych dostępnych danych.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poprzednim przykładzie jest wykorzystywany tylko jeden odbiorca do przetwarzania danych źródłowych. Jeśli masz wielu odbiorców w aplikacji, użyj metody <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>, aby odczytać dane z bloku źródłowego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 Metoda <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> zwraca `False`, gdy żadne dane nie są dostępne. Gdy wielu odbiorców musi uzyskać dostęp do bloku źródłowego współbieżnie, ten mechanizm gwarantuje, że dane są nadal dostępne po wywołaniu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
