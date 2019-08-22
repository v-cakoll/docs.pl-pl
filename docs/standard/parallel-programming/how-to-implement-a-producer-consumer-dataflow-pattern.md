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
ms.openlocfilehash: 044e726a1c668335780fe3d4322fbce83d8dcbba
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666363"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Instrukcje: Implementowanie wzorca przepływu danych producent — konsument
W tym dokumencie opisano sposób użycia biblioteki TPL przepływu danych do wdrożenia wzorca producenta. W tym wzorcu *producent* wysyła komunikaty do bloku komunikatów, a *konsument* odczytuje komunikaty z tego bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano podstawowy model konsumencki-konsumenta, który używa przepływu danych. Metoda zapisuje tablice zawierające losowe bajty danych <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> do obiektu, a `Consume` Metoda odczytuje bajty z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> obiektu. `Produce` Działając na <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> interfejsach i <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> zamiast ich typach pochodnych można napisać kod wielokrotnego użytku, który może działać na różnych typach bloków przepływu danych. W <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> tym przykładzie używa klasy. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Ponieważ Klasa działa jako blok źródłowy i jako blok docelowy, producent i odbiorca mogą używać obiektu udostępnionego do transferowania danych.  
  
 `Produce` Metoda<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> wywołuje metodę w pętli, aby synchronicznie zapisywać dane w bloku docelowym. Gdy metoda zapisuje wszystkie dane w bloku docelowym, <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> wywołuje metodę, aby wskazać, że blok nigdy nie będzie miał dostępnych dodatkowych danych. `Produce` <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> [](../../visual-basic/language-reference/operators/await-operator.md) [](../../csharp/language-reference/keywords/async.md) [](../../visual-basic/language-reference/modifiers/async.md) [](../../csharp/language-reference/keywords/await.md) Metoda używa operatorów Async i Await (Async i await w Visual Basic), aby asynchronicznie obliczyć łączną liczbę bajtów odebranych z obiektu. `Consume` Aby działać asynchronicznie, `Consume` metoda wywołuje metodę <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> , aby otrzymać powiadomienie, gdy blok źródłowy ma dostępne dane i gdy blok źródłowy nigdy nie będzie miał dodatkowych dostępnych danych.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poprzednim przykładzie jest wykorzystywany tylko jeden odbiorca do przetwarzania danych źródłowych. Jeśli masz wielu odbiorców w aplikacji, użyj <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metody w celu odczytania danych z bloku źródłowego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 Metoda <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> zwraca wartość `False` , gdy żadne dane nie są dostępne. Gdy wielu odbiorców musi uzyskać dostęp do bloku źródłowego współbieżnie, ten mechanizm gwarantuje, że dane są nadal dostępne po wywołaniu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
