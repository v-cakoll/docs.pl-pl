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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd9e3a0ead62450e87225212f4fc6ecec6ec9489
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618769"
---
# <a name="how-to-measure-plinq-query-performance"></a>Porady: mierzenie wydajności zapytań PLINQ
Ten przykład pokazuje jak używać <xref:System.Diagnostics.Stopwatch> klasy, aby zmierzyć czas potrzebny do wykonania zapytania PLINQ.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto pustą `foreach` pętli (`For Each` w języku Visual Basic) do pomiaru czas potrzebny na wykonanie kwerendy. W kodzie rzeczywistych pętli zazwyczaj zawiera kroki dodatkowego przetwarzania, które dodać do zapytania łączny czas wykonywania. Należy zauważyć, że stoper nie jest uruchomione, dopóki tylko przed pętli, ponieważ jest to, kiedy rozpoczyna się wykonanie zapytania. Jeśli potrzebujesz więcej szczegółowych pomiarów, możesz użyć `ElapsedTicks` właściwości zamiast `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Łączny czas wykonywania jest przydatne metryki, gdy są eksperymentowanie z implementacjami zapytania, ale nie zawsze rozpozna przedstawiającym. Aby uzyskać lepszą i bardziej rozbudowane widok interakcji wątków zapytania ze sobą oraz z innych uruchomionych procesów, należy użyć narzędzia Concurrency Visualizer. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
