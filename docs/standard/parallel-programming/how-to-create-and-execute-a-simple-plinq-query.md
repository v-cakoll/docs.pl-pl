---
title: 'Porady: tworzenie i wykonywanie prostych zapytań PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: 0cdef6d3826e4e7522bf3f6ed69060b8ef1c5e1b
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588294"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Porady: tworzenie i wykonywanie prostych zapytań PLINQ
W poniższym przykładzie pokazano, jak utworzyć proste <xref:System.Linq.ParallelEnumerable.AsParallel%2A> parallel LINQ kwerendy przy użyciu metody <xref:System.Linq.ParallelEnumerable.ForAll%2A> rozszerzenia w sekwencji źródłowej i wykonywania kwerendy przy użyciu metody.  
  
> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 W tym przykładzie pokazano podstawowy wzorzec do tworzenia i wykonywania dowolnej równoległej kwerendy LINQ, gdy kolejność sekwencji wyników nie jest ważne; niezaudłone zapytania są zazwyczaj szybsze niż uporządkowane kwerendy. Kwerenda dzieli źródło na zadania, które są wykonywane asynchronicznie w wielu wątkach. Kolejność, w jakiej każde zadanie jest wykonywane, zależy nie tylko od ilości pracy związanej z przetwarzaniem elementów w partycji, ale także od czynników zewnętrznych, takich jak sposób planowania każdego wątku przez system operacyjny. W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Aby uzyskać więcej informacji na temat zachowania kolejności elementów w kwerendzie, zobacz [Jak: Sterowanie porządkowanie w PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
