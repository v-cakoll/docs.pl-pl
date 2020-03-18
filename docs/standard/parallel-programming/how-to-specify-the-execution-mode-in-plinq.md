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
ms.openlocfilehash: c602aba6e18f80b007b15cd61dfd2b48a36dd2c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139247"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Porady: określanie trybu wykonywania w PLINQ
W tym przykładzie pokazano, jak wymusić PLINQ, aby ominąć jego domyślne heurystyki i równoległość kwerendy, niezależnie od kształtu kwerendy.  
  
> [!WARNING]
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ ma na celu wykorzystanie możliwości równoległości. Jednak nie wszystkie zapytania korzystają z wykonania równoległego. Na przykład gdy kwerenda zawiera delegata jednego użytkownika, który wykonuje bardzo mało pracy, kwerenda będzie zwykle działać szybciej sekwencyjnie. Jest tak, ponieważ obciążenie związane z włączeniem parallelizing wykonanie jest droższe niż przyspieszenie, które jest uzyskiwane. W związku z tym PLINQ nie automatycznie równoległy chorągwi każdej kwerendy. Najpierw bada kształt zapytania i różnych operatorów, które ją tworzą. Na podstawie tej analizy PLINQ w domyślnym trybie wykonywania może zdecydować się na wykonanie niektórych lub wszystkich kwerendssek sekwencyjnie. Jednak w niektórych przypadkach możesz wiedzieć więcej o zapytaniu niż PLINQ jest w stanie określić na podstawie jego analizy. Na przykład może się zorientować, że pełnomocnik jest bardzo kosztowne i że kwerenda na pewno skorzystają z równoległości. W takich przypadkach można <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> użyć metody <xref:System.Linq.ParallelExecutionMode.ForceParallelism> i określić wartość, aby poinstruować PLINQ, aby zawsze uruchamiać kwerendę jako równoległą.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wytnij i wklej ten kod do próbki `Main`danych [PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i wywołaj metodę z .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
