---
title: "Porady: Rozłączanie bloków przepływu danych"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db3c0d3a6d94e2e9eb65046267f14feff0c056cb
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-unlink-dataflow-blocks"></a>Porady: Rozłączanie bloków przepływu danych
Ten dokument zawiera opis sposobu odłączania docelowy bloku przepływu danych ze źródła.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiekty, każdy z których wywołania `TrySolution` metodę w celu obliczenia wartości. W tym przykładzie wymaga tylko wyników z pierwszego wywołania `TrySolution` aby zakończyć.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Aby otrzymać wartość od pierwszego <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektu, który zakończy, w tym przykładzie definiuje `ReceiveFromAny(T)` metody. `ReceiveFromAny(T)` Metoda przyjmuje tablicę <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektów, a każdy z tych obiektów do łącza <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu. Jeśli używasz <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metodę, aby połączyć źródła bloku przepływu danych bloku docelowego, źródłowego propaguje komunikatów do obiektu docelowego, wraz ze wzrostem dostępności danych. Ponieważ <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> klasy akceptuje tylko pierwszy komunikat, który ma jej na liście, `ReceiveFromAny(T)` generuje wyniku przez wywołanie metody <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody. Daje to pierwszy komunikat, który jest oferowana <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda ma zastąpionej wersji, która przyjmuje <xref:System.Boolean> parametru `unlinkAfterOne` , jeśli jest równa `True`, powoduje, że blok źródła, aby odłączyć element docelowy, gdy element docelowy otrzyma jeden komunikat ze źródła. Ważne jest, aby <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt, aby odłączyć od źródła, ponieważ relacja między tablicy źródeł i <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt nie jest już wymagane po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt odbiera wiadomości.  
  
 Aby włączyć pozostałe wywołania do `TrySolution` kończy się po jednej z nich oblicza wartość, `TrySolution` ma metodę <xref:System.Threading.CancellationToken> obiekt, który jest anulowane po wywołaniu `ReceiveFromAny(T)` zwraca. <xref:System.Threading.SpinWait.SpinUntil%2A> Metoda zwraca, kiedy to <xref:System.Threading.CancellationToken> obiektu została anulowana.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  

## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
