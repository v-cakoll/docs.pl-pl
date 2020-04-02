---
title: 'Porady: mierzenie wydajności zapytań PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 4cb0d408798d66c8491654c90f33255c700690a3
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587792"
---
# <a name="how-to-measure-plinq-query-performance"></a>Porady: mierzenie wydajności zapytań PLINQ
W tym przykładzie <xref:System.Diagnostics.Stopwatch> pokazano, jak używać klasy do pomiaru czasu potrzebnym do wykonania kwerendy PLINQ.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `foreach` użyto pustej pętli (w`For Each` języku Visual Basic) do pomiaru czasu potrzebnym do wykonania kwerendy. W kodzie w świecie rzeczywistym pętla zazwyczaj zawiera dodatkowe kroki przetwarzania, które dodają do całkowitego czasu wykonywania kwerendy. Należy zauważyć, że stoper nie jest uruchamiany dopiero tuż przed pętlą, ponieważ jest to, gdy rozpoczyna się wykonywanie kwerendy. Jeśli potrzebujesz bardziej szczegółowego pomiaru, `ElapsedTicks` `ElapsedMilliseconds`możesz użyć właściwości zamiast .  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Całkowity czas wykonywania jest metryką przydatne podczas eksperymentowania z implementacji kwerendy, ale nie zawsze powiedzieć całą historię. Aby uzyskać głębszy i bogatszy widok interakcji wątków kwerendy ze sobą i z innymi uruchomionymi procesami, należy użyć wizualizatora współbieżności. Aby uzyskać więcej informacji, zobacz [Wizualizator współbieżności](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
