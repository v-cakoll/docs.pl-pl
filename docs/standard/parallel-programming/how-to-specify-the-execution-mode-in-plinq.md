---
title: 'Porady: określanie trybu wykonywania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 6ef813937b731b417be31e189d89b81cccc75280
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588549"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Porady: określanie trybu wykonywania w PLINQ
W tym przykładzie pokazano, jak wymusić PLINQ, aby ominąć jego domyślne heurystyki i zrównoleglić kwerendy niezależnie od kształtu kwerendy.  
  
> [!WARNING]
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ został zaprojektowany, aby wykorzystać możliwości równoległości. Jednak nie wszystkie kwerendy korzystają z wykonywania równoległego. Na przykład, gdy kwerenda zawiera delegata jednego użytkownika, który wykonuje bardzo mało pracy, kwerenda będzie zwykle działać szybciej sekwencyjnie. Jest to spowodowane obciążenie związane z włączaniem wykonywania równoległości jest droższe niż przyspieszenie, które jest uzyskiwane. W związku z tym PLINQ nie automatycznie równoległościić każde zapytanie. Najpierw sprawdza kształt kwerendy i różnych operatorów, które go tworzą. Na podstawie tej analizy PLINQ w trybie wykonywania domyślnego może zdecydować o wykonaniu niektórych lub wszystkich kwerendy sekwencyjnie. Jednak w niektórych przypadkach możesz wiedzieć więcej o zapytaniu niż PLINQ jest w stanie określić na podstawie jego analizy. Na przykład może wiesz, że delegat jest bardzo drogie i że kwerenda na pewno skorzysta z równoległości. W takich przypadkach można <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> użyć metody <xref:System.Linq.ParallelExecutionMode.ForceParallelism> i określić wartość, aby poinstruować PLINQ, aby zawsze uruchamiać kwerendę jako równoległą.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wytnij i wklej ten kod do próbki `Main`danych [PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i wywołaj metodę z .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
