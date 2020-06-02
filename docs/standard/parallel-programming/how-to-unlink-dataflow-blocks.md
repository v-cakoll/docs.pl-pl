---
title: 'Instrukcje: Rozłączanie bloków przepływu danych'
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
ms.openlocfilehash: 8af978ca2ca237988dae8328656d70574dbc1f14
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288059"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Instrukcje: Rozłączanie bloków przepływu danych
W tym dokumencie opisano sposób odłączania docelowego bloku przepływu danych od jego źródła.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiekty, z których każdy wywołuje `TrySolution` metodę w celu obliczenia wartości. Ten przykład wymaga tylko wyniku pierwszego wywołania do `TrySolution` końca.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Aby otrzymać wartość z pierwszego <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> obiektu, który zakończy, ten przykład definiuje `ReceiveFromAny(T)` metodę. `ReceiveFromAny(T)`Metoda akceptuje tablicę <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektów i łączy każdy z tych obiektów do <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu. Gdy używasz <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metody do łączenia źródłowego bloku przepływu danych z blokiem docelowym, Źródło propaguje komunikaty do obiektu docelowego, ponieważ dane staną się dostępne. Ponieważ <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> Klasa akceptuje tylko pierwszy komunikat, który jest oferowany, `ReceiveFromAny(T)` Metoda generuje swój wynik, wywołując <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metodę. Spowoduje to wygenerowanie pierwszej wiadomości, która jest oferowana dla <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>Metoda ma przeciążoną wersję, która pobiera <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> obiekt z <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> właściwością, która, gdy jest ustawiona na `1` , instruuje blok źródłowy, aby odłączyć od elementu docelowego po odebraniu przez element docelowy jednej wiadomości ze źródła. Ważne jest, aby <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiekt odłączył się od swoich źródeł, ponieważ relacja między tablicą źródeł a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektem nie jest już wymagana po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> odebraniu komunikatu przez obiekt.  
  
 Aby umożliwić zakończenie pozostałych wywołań `TrySolution` , gdy jeden z nich obliczy wartość, `TrySolution` Metoda przyjmuje <xref:System.Threading.CancellationToken> obiekt, który jest anulowany po wywołaniu metody `ReceiveFromAny(T)` Return. <xref:System.Threading.SpinWait.SpinUntil%2A>Metoda zwraca po <xref:System.Threading.CancellationToken> anulowaniu tego obiektu.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](dataflow-task-parallel-library.md)
