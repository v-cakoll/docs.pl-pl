---
title: 'Instrukcje: Implementowanie wzorca przepływu danych producent — konsument'
description: Zapoznaj się z tematem implementowania wzorca przepływu danych konsumenta w programie przy użyciu biblioteki przepływu danych TPL w środowisku .NET.
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
ms.openlocfilehash: e9ed8f84f1daca64fa60d8aed18aa2d9be1380e0
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768927"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Instrukcje: Implementowanie wzorca przepływu danych producent — konsument
W tym dokumencie opisano sposób użycia biblioteki TPL przepływu danych do wdrożenia wzorca producenta. W tym wzorcu *producent* wysyła komunikaty do bloku komunikatów, a *konsument* odczytuje komunikaty z tego bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano podstawowy model konsumencki-konsumenta, który używa przepływu danych. `Produce`Metoda zapisuje tablice zawierające losowe bajty danych do <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> obiektu, a `Consume` Metoda odczytuje bajty z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> obiektu. Działając na <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfejsach i zamiast ich typach pochodnych można napisać kod wielokrotnego użytku, który może działać na różnych typach bloków przepływu danych. W tym przykładzie używa <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> klasy. Ponieważ <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Klasa działa jako blok źródłowy i jako blok docelowy, producent i odbiorca mogą używać obiektu udostępnionego do transferowania danych.  
  
 `Produce`Metoda wywołuje <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metodę w pętli, aby synchronicznie zapisywać dane w bloku docelowym. Gdy `Produce` Metoda zapisuje wszystkie dane w bloku docelowym, wywołuje <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metodę, aby wskazać, że blok nigdy nie będzie miał dostępnych dodatkowych danych. `Consume`Metoda używa operatorów [Async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) i [await](../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic), aby asynchronicznie obliczyć łączną liczbę bajtów odebranych z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektu. Aby działać asynchronicznie, `Consume` Metoda wywołuje <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> metodę, aby otrzymać powiadomienie, gdy blok źródłowy ma dostępne dane i gdy blok źródłowy nigdy nie będzie miał dodatkowych dostępnych danych.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W poprzednim przykładzie jest wykorzystywany tylko jeden odbiorca do przetwarzania danych źródłowych. Jeśli masz wielu odbiorców w aplikacji, użyj <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metody w celu odczytania danych z bloku źródłowego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>Metoda zwraca wartość, `False` gdy żadne dane nie są dostępne. Gdy wielu odbiorców musi uzyskać dostęp do bloku źródłowego współbieżnie, ten mechanizm gwarantuje, że dane są nadal dostępne po wywołaniu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> .  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](dataflow-task-parallel-library.md)
