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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b597cf93cdf249936a34b2c07b38d000c96333f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520629"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Porady: Określanie stopnia równoległości w bloku przepływu danych
W tym dokumencie opisano sposób ustawiania <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> właściwości, aby umożliwić wykonanie bloku przepływu danych do przetwarzania więcej niż jeden komunikat w danym momencie. Jest to przydatne w po bloku przepływu danych, która wykonuje obliczenia długotrwałych i może być korzystne przetwarzanie komunikatów w sposób równoległy. W tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> klasy do wykonywania wielu operacji przepływu danych, jednocześnie; Jednakże, można określić maksymalny stopień równoległości w żadnym z typów bloków wykonywanie wstępnie zdefiniowanych, udostępniane Biblioteka przepływu danych TPL <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje dwa obliczeń przepływu danych i wyświetla czas, która jest wymagana dla każdego obliczenia. Pierwszy obliczeń określa maksymalny stopień równoległości, 1, co jest ustawieniem domyślnym. Maksymalny stopień równoległości 1 powoduje, że blok przepływu danych do przetwarzania komunikatów szeregowo. Drugi obliczeń przypomina pierwsze, z tą różnicą, że określa maksymalny stopień równoległości, która jest równa liczbie procesorów dostępnych. Dzięki temu bloku przepływu danych do wykonywania wielu operacji równoległych.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.  
  
 Visual C#  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Domyślnie każdy blok przepływu danych wstępnie zdefiniowanych propaguje wiadomości w kolejności, w jakiej komunikaty są odbierane.  Chociaż wiele wiadomości są przetwarzane jednocześnie w przypadku określenia maksymalny stopień równoległości, która jest większa niż 1, są nadal propagowane się w kolejności, w której zostały odebrane.  
  
 Ponieważ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> właściwość reprezentuje maksymalny stopień równoległości, bloku przepływu danych może być wykonywany z niższy stopień równoległości, niż można określić. W bloku przepływu danych można użyć niższy stopień równoległości, do swoich wymagań funkcjonalności lub konto z powodu braku dostępnych zasobów systemowych. W bloku przepływu danych nigdy nie wybiera większego stopnia równoległości nie określisz.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
