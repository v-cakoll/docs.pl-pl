---
title: 'Porady: zwracanie wartości z zadania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 495f68114bfe960b8182be4ab76b72043b2d0cc7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141672"
---
# <a name="how-to-return-a-value-from-a-task"></a>Porady: zwracanie wartości z zadania
W tym przykładzie pokazano, jak za pomocą typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> zwrócić wartość z właściwości <xref:System.Threading.Tasks.Task%601.Result%2A>. Wymaga, aby folder C:\Users\Public\Pictures\Sample obrazy \ katalog istnieje i zawierał pliki.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje wątek wywołujący do momentu zakończenia zadania.  
  
 Aby dowiedzieć się, jak przekazać wynik jednego <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> do zadania kontynuacji, zobacz Tworzenie [łańcucha zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
