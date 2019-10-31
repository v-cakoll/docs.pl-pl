---
title: 'Porady: Określanie stopnia równoległości w bloku przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
ms.openlocfilehash: 50399d6cd32fe310089395ac8c660b08151ba808
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141653"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Porady: Określanie stopnia równoległości w bloku przepływu danych
W tym dokumencie opisano sposób ustawiania właściwości <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType>, aby umożliwić blokowi przepływu danych wykonywania przetwarzanie więcej niż jednego komunikatu w danym momencie. Jest to przydatne w przypadku, gdy istnieje blok przepływu danych, który wykonuje długotrwałe obliczenia i może korzystać z równoległego przetwarzania komunikatów. Ten przykład używa klasy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> do wykonywania wielu operacji przepływu danych jednocześnie; można jednak określić maksymalny stopień równoległości w dowolnym wstępnie zdefiniowanym typie bloku wykonywania, który udostępnia Biblioteka TPL przepływu danych, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje dwa obliczenia przepływu danych i drukuje czas, który jest wymagany dla każdego obliczenia. Pierwsze obliczenie określa maksymalny stopień równoległości 1, który jest wartością domyślną. Maksymalny stopień równoległości 1 powoduje, że blok przepływu danych przetwarza komunikaty sekwencyjnie. Drugie obliczenie jest podobne do pierwszego, z tą różnicą, że określa maksymalny stopień równoległości równy liczbie dostępnych procesorów. Dzięki temu blok przepływu danych może wykonywać wiele operacji równolegle.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Domyślnie każdy wstępnie zdefiniowany blok przepływu danych propaguje komunikaty w kolejności, w jakiej komunikaty są odbierane.  Chociaż wiele komunikatów jest przetwarzanych jednocześnie, gdy określisz maksymalny stopień równoległości większy niż 1, są one nadal rozmnożone w kolejności, w której zostały odebrane.  
  
 Ponieważ właściwość <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> reprezentuje maksymalny stopień równoległości, blok przepływu danych może być wykonywany z mniejszym stopieńem równoległości niż określono. Blok przepływu danych może używać mniejszego stopnia równoległości w celu spełnienia wymagań funkcjonalnych lub w przypadku braku dostępnych zasobów systemowych. Blok przepływu danych nigdy nie wybiera większego stopnia równoległości niż określono.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
