---
title: 'Instrukcje: Obsługa wyjątków w pętlach równoległych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 87405425e85ed16d10b3e8b382c6e414fff10ddf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278535"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Instrukcje: Obsługa wyjątków w pętlach równoległych
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Przeciążenia i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nie mają żadnego specjalnego mechanizmu do obsługi wyjątków, które mogą być zgłaszane. W tym aspekcie przypominają one regularne `for` i `foreach` pętle ( `For` i `For Each` w Visual Basic); nieobsłużony wyjątek powoduje przerwanie działania pętli zaraz po zakończeniu wszystkich aktualnie uruchomionych iteracji.
  
 W przypadku dodawania własnej logiki obsługi wyjątków do pętli równoległych, należy obsłużyć przypadek, w którym mogą być zgłaszane podobne wyjątki w wielu wątkach jednocześnie, a w przypadku, gdy wyjątek zgłoszony w jednym wątku powoduje zgłoszenie innego wyjątku w innym wątku. Oba przypadki można obsługiwać, zawijając wszystkie wyjątki z pętli w <xref:System.AggregateException?displayProperty=nameWithType> . W poniższym przykładzie pokazano jedno z możliwych podejścia.  
  
> [!NOTE]
> Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które zostało przedstawione w poniższym przykładzie. Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wszystkie wyjątki są przechwytywane, a następnie zawijane w <xref:System.AggregateException?displayProperty=nameWithType> , które są generowane. Obiekt wywołujący może zdecydować, które wyjątki mają być obsługiwane.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](data-parallelism-task-parallel-library.md)
- [Wyrażenia lambda w PLINQ i TPL](lambda-expressions-in-plinq-and-tpl.md)
