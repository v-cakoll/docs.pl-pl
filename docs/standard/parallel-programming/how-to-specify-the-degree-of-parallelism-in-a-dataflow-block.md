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
ms.openlocfilehash: 4239e57087cc6eb3b644dbcd8d25a0e1adb1ed0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581111"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Porady: Określanie stopnia równoległości w bloku przepływu danych
Ten dokument zawiera opis sposobu ustawiania <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> właściwości, aby umożliwić wykonanie bloku przepływu danych do jednoczesnego przetwarzania więcej niż jeden komunikat. Jest to przydatne w przypadku ma bloku przepływu danych, która wykonuje obliczenia długotrwałe oraz mogą korzystać z przetwarzanie komunikatów równolegle. W tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> klasy w celu wykonania wielu operacji przepływu danych, jednocześnie; jednak, można określić maksymalny stopień równoległości w żadnym z typów bloku wykonania wstępnie zdefiniowanych, które udostępnia przepływu danych tpl, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 W poniższym przykładzie wykonuje dwie obliczenia przepływu danych i wyświetla czas, który upłynął wymaganego do każdego obliczeń. Pierwszy obliczenia określa maksymalny stopień równoległości 1, co jest ustawieniem domyślnym. Maksymalny stopień równoległości 1 powoduje, że blok przepływu danych do przetwarzania komunikatów pojedynczo. Drugi obliczenia podobny pierwsza strona, z tą różnicą, że określa maksymalny stopień równoległości, który jest taki sam, jak liczba dostępnych procesorów. Dzięki temu bloku przepływu danych do wykonywania wielu operacji równolegle.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` w języku Visual Basic), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 Visual C#  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Domyślnie każdy blok przepływu danych wstępnie zdefiniowanych propaguje wiadomości w kolejności, w którym są odbierane wiadomości.  Mimo że wiele komunikatów przetwarzanych jednocześnie po określeniu maksymalny stopień równoległości, która jest większa niż 1, są nadal propagowane w kolejności, w którym są odbierane.  
  
 Ponieważ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> właściwość reprezentuje maksymalny stopień równoległości, bloku przepływu danych może być wykonywane za pomocą niższy stopień równoległości nie określisz. W bloku przepływu danych można użyć niższy stopień równoległości do swoich wymagań funkcjonalnych lub konto z powodu braku dostępnych zasobów systemowych. Bloku przepływu danych nigdy nie wybierze większy stopień równoległości nie określisz.  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
