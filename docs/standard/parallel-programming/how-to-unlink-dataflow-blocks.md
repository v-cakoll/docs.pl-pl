---
title: "Porady: Rozłączanie bloków przepływu danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41f1b83fab6ff44e69ac2f010f70e6e254341f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a>Porady: Rozłączanie bloków przepływu danych
Ten dokument zawiera opis sposobu odłączania docelowy bloku przepływu danych ze źródła.  
  
> [!TIP]
>  Biblioteka przepływu danych tpl (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> przestrzeni nazw) nie jest rozpowszechniana z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aby zainstalować <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z menu projektu i wyszukaj w trybie online `Microsoft.Tpl.Dataflow` pakietu.  
  
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
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
