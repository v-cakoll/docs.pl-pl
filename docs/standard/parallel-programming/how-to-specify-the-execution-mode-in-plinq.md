---
title: 'Instrukcje: Określanie trybu wykonywania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67b23da6742af3cb65da6da49dbab982a0248bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694623"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Instrukcje: Określanie trybu wykonywania w PLINQ
W tym przykładzie przedstawiono sposób wymusić PLINQ obejścia domyślnej heurystyki i równoległe przetwarzanie zapytania niezależnie od tego, w zapytaniu shape.  
  
> [!WARNING]
>  W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty. Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 Program PLINQ jest przeznaczony do możliwości przetwarzania równoległego. Jednak nie wszystkie kwerendy korzystają z przetwarzania równoległego. Na przykład, gdy zapytanie zawiera delegata pojedynczego użytkownika, który wykonuje bardzo małego wysiłku, zapytanie będzie najczęściej uruchamiane szybciej sekwencyjnie. Jest to spowodowane obciążenie związane z włączaniem przekształcają wykonywania jest droższe niż przyspieszenie, uzyskany. W związku z tym program PLINQ nie automatycznie równolegle wykonywać każdego zapytania. Najpierw sprawdza, czy kształt zapytania i różnych operatorów, które składają się go. Na podstawie tej analizy, PLINQ w domyślnym trybie wykonywania może podjąć decyzję o wykonanie niektórych lub wszystkich zapytanie sekwencyjnie. Jednak w niektórych przypadkach użytkownik może dowiedzieć się więcej o kwerendzie niż PLINQ jest możliwe ustalenie, z ich analizy. Na przykład wiadomo, że delegat jest bardzo kosztowny i czy zapytania zdecydowanie będą mogli korzystać z przetwarzaniem równoległym. W takich przypadkach można użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metodę i określić <xref:System.Linq.ParallelExecutionMode.ForceParallelism> wartość, aby nakazać PLINQ zawsze uruchamiaj zapytania jako równoległego.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wytnij i wklej go w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i wywołaj metodę z `Main`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
