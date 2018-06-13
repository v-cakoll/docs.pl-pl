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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e5bd27dda4bacc50672cca2db38a6eda746d79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580380"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Porady: tworzenie i wykonywanie prostych zapytań PLINQ
Poniższy przykład przedstawia sposób tworzenia prostego zapytania równoległe LINQ za pomocą <xref:System.Linq.ParallelEnumerable.AsParallel%2A> — metoda rozszerzenia w sekwencji źródłowej i wykonywania zapytania za pomocą <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody.  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażenia lambda, aby zdefiniować delegatów w PLINQ. Jeśli nie masz doświadczenia z wyrażenia lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 W tym przykładzie przedstawiono podstawowe wzorzec do tworzenia i wykonywania wszelkie zapytania równoległe LINQ, gdy kolejność sekwencji wynik nie jest istotna; nieuporządkowaną zapytania są zwykle szybsze niż uporządkowanych zapytań. Zapytanie partycji źródła do zadań, które są wykonywane asynchronicznie na wiele wątków. Kolejność, w którym kończy się każde zadanie zależy nie tylko ze względu na ilość pracy zaangażowany przetwarzania elementów w partycji, ale także na czynniki zewnętrzne, takie jak jak system operacyjny planuje każdy wątek. W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Aby uzyskać więcej informacji na temat zachowania kolejności elementów w zapytaniu, zobacz [porady: kontrolki szeregowaniem w zapytaniu PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
