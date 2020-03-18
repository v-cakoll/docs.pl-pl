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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139294"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Porady: Rozłączanie bloków przepływu danych
W tym dokumencie opisano sposób odłączenia docelowego bloku przepływu danych od źródła.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> trzy obiekty, z `TrySolution` których każdy wywołuje metodę do obliczenia wartości. W tym przykładzie wymaga tylko wynik `TrySolution` z pierwszego wywołania do zakończenia.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Aby otrzymać wartość z <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pierwszego obiektu, który kończy, `ReceiveFromAny(T)` w tym przykładzie definiuje metodę. Metoda `ReceiveFromAny(T)` akceptuje tablicę <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektów i łączy każdy z <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> tych obiektów do obiektu. Korzystając z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metody, aby połączyć blok przepływu danych źródłowych do bloku docelowego, źródło propaguje wiadomości do obiektu docelowego, gdy dane stają się dostępne. Ponieważ <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> klasa akceptuje tylko pierwszą wiadomość, która `ReceiveFromAny(T)` jest oferowana, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metoda daje jej wynik, wywołując metodę. Spowoduje to wygenerowanie pierwszej wiadomości, która jest oferowana do <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obiektu. Metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> ma przeciążoną wersję, <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> która przyjmuje <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> obiekt z właściwością, `1`która, gdy jest ustawiona na , instruuje blok źródłowy, aby odłączyć od obiektu docelowego po obiekt docelowy odbiera jeden komunikat ze źródła. Ważne jest, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> aby obiekt odłączał się od jego źródeł, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> ponieważ relacja między tablicą <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> źródeł a obiektem nie jest już wymagana po odebraniu wiadomości przez obiekt.  
  
 Aby włączyć pozostałe `TrySolution` wywołania do końca po jednym z `TrySolution` nich <xref:System.Threading.CancellationToken> oblicza wartość, metoda przyjmuje `ReceiveFromAny(T)` obiekt, który jest anulowany po wywołaniu zwraca. Metoda <xref:System.Threading.SpinWait.SpinUntil%2A> zwraca, <xref:System.Threading.CancellationToken> gdy ten obiekt jest anulowany.  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
