---
title: "Porady: mierzenie wydajności zapytań PLINQ"
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
helpviewer_keywords: PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fe19fd6ae7730a30a9ccc8a39b99a31981f838fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-measure-plinq-query-performance"></a>Porady: mierzenie wydajności zapytań PLINQ
W tym przykładzie przedstawiono sposób użycia <xref:System.Diagnostics.Stopwatch> klasy do mierzenia czas potrzebny na wykonanie zapytania PLINQ.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto pustą `foreach` pętli (`For Each` w języku Visual Basic) do mierzenia na czas potrzebny na wykonanie kwerendy. W kodzie rzeczywistych pętli zazwyczaj zawiera kroki dodatkowego przetwarzania, które czasu wykonywania kwerendy. Należy zauważyć, że stopera nie jest uruchomione, dopóki tylko przed pętli, ponieważ jest to, kiedy rozpoczyna się wykonanie zapytania. Jeśli potrzebujesz więcej szczegółowych pomiarów, możesz użyć `ElapsedTicks` właściwości zamiast `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Łączny czas wykonywania jest przydatne metryki, gdy są eksperymentowanie z implementacji kwerendy, ale nie zawsze powiadomi cały artykuł. Aby uzyskać bardziej i zaawansowaną widok interakcji wątków zapytania ze sobą oraz z innych procesów uruchomionych, korzystanie z wizualizatora współbieżności. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
