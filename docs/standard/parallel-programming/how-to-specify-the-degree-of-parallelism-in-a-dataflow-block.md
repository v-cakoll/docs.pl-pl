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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141653"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Porady: Określanie stopnia równoległości w bloku przepływu danych
W tym dokumencie opisano sposób ustawiania <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> właściwości, aby włączyć blok przepływu danych wykonywania do przetwarzania więcej niż jednej wiadomości naraz. Jest to przydatne, gdy masz blok przepływu danych, który wykonuje długotrwałe obliczenia i mogą korzystać z przetwarzania wiadomości równolegle. W tym <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> przykładzie używa klasy do wykonywania wielu operacji przepływu danych jednocześnie; można jednak określić maksymalny stopień równoległości w dowolnym z wstępnie zdefiniowanych typów bloków <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>wykonywania, które zapewnia biblioteka przepływu danych TPL, , i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje dwa obliczenia przepływu danych i drukuje czas, który jest wymagany dla każdego obliczenia. Pierwsze obliczenia określa maksymalny stopień równoległości 1, który jest domyślny. Maksymalny stopień równoległości 1 powoduje, że blok przepływu danych do przetwarzania wiadomości szeregowo. Drugie obliczenia przypomina pierwszy, z tą różnicą, że określa maksymalny stopień równoległości, który jest równy liczbie dostępnych procesorów. Dzięki temu blok przepływu danych do wykonywania wielu operacji równolegle.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Domyślnie każdy wstępnie zdefiniowany blok przepływu danych propaguje wiadomości w kolejności, w jakiej wiadomości są odbierane.  Mimo że wiele wiadomości są przetwarzane jednocześnie po określeniu maksymalny stopień równoległości, który jest większy niż 1, są one nadal propagowane w kolejności, w jakiej są odbierane.  
  
 Ponieważ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> właściwość reprezentuje maksymalny stopień równoległości, blok przepływu danych może być wykonywany z mniejszym stopniem równoległości niż określono. Blok przepływu danych może używać mniejszego stopnia równoległości, aby spełnić jego wymagania funkcjonalne lub uwzględnić brak dostępnych zasobów systemowych. Blok przepływu danych nigdy nie wybiera większego stopnia równoległości niż określono.  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
