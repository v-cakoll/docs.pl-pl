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
ms.openlocfilehash: 349cc8d78e9a080d720e09a7e3e5e314752605c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106958"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Porady: tworzenie i wykonywanie prostych zapytań PLINQ
W poniższym przykładzie pokazano, jak utworzyć prostą <xref:System.Linq.ParallelEnumerable.AsParallel%2A> kwerendę Równoległego LINQ przy użyciu <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody rozszerzenia w sekwencji źródłowej i wykonywania kwerendy przy użyciu metody.  
  
> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 W tym przykładzie przedstawiono podstawowy wzorzec do tworzenia i wykonywania dowolnej kwerendy Równoległego LINQ, gdy kolejność sekwencji wyników nie jest ważna; zapytania nieuporządkowane są zazwyczaj szybsze niż zamówione zapytania. Kwerenda dzieli źródło na zadania, które są wykonywane asynchronicznie na wielu wątkach. Kolejność, w jakiej każde zadanie kończy zależy nie tylko od ilości pracy związanej z przetwarzaniem elementów w partycji, ale także od czynników zewnętrznych, takich jak sposób, w jaki system operacyjny planuje każdy wątek. W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Aby uzyskać więcej informacji na temat sposobu zachowywania kolejności elementów w kwerendzie, zobacz [Jak: Sterowanie kolejnością w kwerendzie PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
