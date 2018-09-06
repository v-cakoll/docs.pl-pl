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
ms.openlocfilehash: 544ea0f89dfa518c2ef18bffe2609d72e6fdee70
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891223"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Porady: tworzenie i wykonywanie prostych zapytań PLINQ
Poniższy przykład pokazuje, jak utworzyć proste zapytanie równoległe LINQ za pomocą <xref:System.Linq.ParallelEnumerable.AsParallel%2A> metody rozszerzenia w sekwencji źródłowej i wykonywania zapytania za pomocą <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody.  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 W tym przykładzie przedstawiono podstawowy wzorzec do tworzenia i wykonywanie dowolnego zapytania równoległe LINQ, gdy kolejność sekwencji wynik nie jest istotna; Nieuporządkowana zapytania są zwykle szybsze niż uporządkowane zapytanie. Zapytanie partycji źródłowej na zadania, które są wykonywane asynchronicznie w wielu wątkach. Kolejność, w którym kończy się każde zadanie zależy nie tylko na ilość pracy zaangażowane na przetworzenie elementów w partycji, ale także na czynniki zewnętrzne, takie jak jak system operacyjny planuje każdego wątku. W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty. Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Aby uzyskać więcej informacji o tym, jak zachować kolejność elementów w zapytaniu, zobacz [instrukcje: kontrolki szeregowaniem w zapytaniu PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
