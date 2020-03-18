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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091486"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Porady: Implementowanie wzorca przepływu danych producent — konsument
W tym dokumencie opisano sposób używania biblioteki przepływu danych TPL do implementowania wzorca producent-konsument. W tym wzorcu *producent* wysyła wiadomości do bloku komunikatów, a *konsument* odczytuje wiadomości z tego bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono podstawowy model producenta- konsumenta, który używa przepływu danych. Metoda `Produce` zapisuje tablice, które zawierają losowe <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> bajty `Consume` danych do obiektu i <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> metoda odczytuje bajty z obiektu. Działając na <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> interfejsy i <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> zamiast ich typów pochodnych, można napisać kod wielokrotnego użytku, który może działać na różnych typów bloków przepływu danych. W tym <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> przykładzie użyto klasy. Ponieważ <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> klasa działa zarówno jako blok źródłowy, jak i jako blok docelowy, producent i konsument mogą używać obiektu udostępnionego do przesyłania danych.  
  
 Metoda `Produce` wywołuje <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metodę w pętli do synchronicznie zapisywać dane do bloku docelowego. Po `Produce` metoda zapisuje wszystkie dane do bloku docelowego, wywołuje <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metodę, aby wskazać, że blok nigdy nie będzie miał dodatkowe dane dostępne. Metoda `Consume` używa [asynchronicznych](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) operatorów[(Async](../../visual-basic/language-reference/modifiers/async.md) i [Await](../../visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic) do asynchronicznie obliczyć całkowitą liczbę bajtów, które są odbierane z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektu. Aby działać asynchronicznie, `Consume` <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> metoda wywołuje metodę, aby otrzymać powiadomienie, gdy blok źródłowy ma dostępne dane i gdy blok źródłowy nigdy nie będzie miał dodatkowe dane dostępne.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poprzednim przykładzie używa tylko jednego konsumenta do przetwarzania danych źródłowych. Jeśli masz wielu konsumentów w aplikacji, użyj <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metody do odczytu danych z bloku źródłowego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 Metoda <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> zwraca, `False` gdy nie są dostępne żadne dane. Gdy wielu konsumentów musi jednocześnie uzyskać dostęp do bloku źródłowego, mechanizm <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>ten gwarantuje, że dane są nadal dostępne po wywołaniu .  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
