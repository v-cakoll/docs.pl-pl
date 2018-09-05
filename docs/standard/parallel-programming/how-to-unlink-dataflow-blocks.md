---
title: 'Porady: Rozłączanie bloków przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 65d42597c572a85a95f9e2b4407df42c6fb7bb3d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674117"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Porady: Rozłączanie bloków przepływu danych
Ten dokument zawiera opis sposobu odłączania docelowej bloku przepływu danych ze źródła.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektów, każdy która wywołuje metodę `TrySolution` metodę w celu obliczenia wartości. W tym przykładzie wymaga tylko wyniki z pierwszym wywołaniu `TrySolution` na zakończenie.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Aby otrzymać wartość od pierwszego <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektu, który zakończy się, w tym przykładzie definiuje `ReceiveFromAny(T)` metody. `ReceiveFromAny(T)` Metoda przyjmuje tablicę <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektów i każdy z tych obiektów do łączy <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu. Kiedy używasz <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metodę, aby połączyć bloku przepływu danych źródłowych do bloku docelowego, źródłowego propaguje komunikatów do obiektu docelowego danych staje się dostępna. Ponieważ <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> klasy akceptuje tylko pierwszy komunikat, który jest dostępna, `ReceiveFromAny(T)` generuje jej wynik, wywołując <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody. Daje to pierwszy komunikat, który jest oferowany <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda ma przeciążona wersja, która przyjmuje <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> obiekt z <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> właściwości, gdy jest równa `1`, powoduje, że blok źródłowy można odłączyć od obiektu docelowego, gdy docelowym otrzyma jeden komunikat ze źródła . Ważne jest, aby <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu można odłączyć od źródła, ponieważ relacja między tablicą źródeł i <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt nie jest już wymagane po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt otrzymuje komunikat.  
  
 Aby włączyć pozostałe wywołania do `TrySolution` kończy się po jednej z nich oblicza wartość `TrySolution` metoda przyjmuje <xref:System.Threading.CancellationToken> obiektów, które zostało anulowane po wywołaniu `ReceiveFromAny(T)` zwraca. <xref:System.Threading.SpinWait.SpinUntil%2A> Metoda zwraca, kiedy to <xref:System.Threading.CancellationToken> obiektu zostanie anulowane.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.  
  
 Visual C#  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  

## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
