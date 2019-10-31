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
ms.openlocfilehash: b49cfc9730ba154202baf15093a54ba3ce0e2a8a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139294"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Porady: Rozłączanie bloków przepływu danych
W tym dokumencie opisano sposób odłączania docelowego bloku przepływu danych od jego źródła.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektów, z których każdy wywołuje metodę `TrySolution` w celu obliczenia wartości. Ten przykład wymaga tylko wyniku pierwszego wywołania do `TrySolution`.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Aby otrzymać wartość z pierwszego obiektu <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, który zakończy, ten przykład definiuje metodę `ReceiveFromAny(T)`. Metoda `ReceiveFromAny(T)` akceptuje tablicę obiektów <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> i łączy każdy z tych obiektów do obiektu <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>. W przypadku używania metody <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> do łączenia źródłowego bloku przepływu danych z blokiem docelowym, Źródło propaguje komunikaty do obiektu docelowego, ponieważ dane staną się dostępne. Ponieważ Klasa <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> akceptuje tylko pierwszy komunikat, który jest oferowany, Metoda `ReceiveFromAny(T)` generuje swój wynik, wywołując metodę <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>. Spowoduje to wygenerowanie pierwszej wiadomości, która jest oferowana dla obiektu <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>. Metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> ma przeciążoną wersję, która przyjmuje obiekt <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> z właściwością <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages>, która, gdy jest ustawiona na `1`, instruuje blok źródłowy, aby odłączyć od elementu docelowego po odebraniu przez obiekt docelowy jednej wiadomości ze źródła. Ważne jest, aby obiekt <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> rozłączył się ze źródła, ponieważ relacja między tablicą źródeł i obiektem <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nie jest już wymagana po odebraniu komunikatu przez obiekt <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>.  
  
 Aby umożliwić zakończenie pozostałych wywołań `TrySolution`, gdy jeden z nich obliczy wartość, Metoda `TrySolution` pobiera <xref:System.Threading.CancellationToken> obiekt, który zostanie anulowany po wywołaniu `ReceiveFromAny(T)` zwraca. Metoda <xref:System.Threading.SpinWait.SpinUntil%2A> zwraca, gdy ten obiekt <xref:System.Threading.CancellationToken> zostanie anulowany.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
