---
title: 'Instrukcje: Zwracanie wartości z zadania'
description: Zobacz, jak używać typu System. Threading. Tasks. Task <TResult> do zwracania wartości z właściwości wynik w programie .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 051cef7cac654e4369ec1486884876004370ba0b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767978"
---
# <a name="how-to-return-a-value-from-a-task"></a>Instrukcje: Zwracanie wartości z zadania
W tym przykładzie pokazano, jak za pomocą <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typu zwrócić wartość z <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości. Wymaga, aby folder C:\Users\Public\Pictures\Sample obrazy \ katalog istnieje i zawierał pliki.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A>Właściwość blokuje wątek wywołujący do momentu zakończenia zadania.  
  
 Aby dowiedzieć się, jak przekazać wynik jednego <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> do zadania kontynuacji, zobacz Tworzenie [łańcucha zadań przy użyciu zadań kontynuacji](chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne oparte na zadaniach](task-based-asynchronous-programming.md)
- [Wyrażenia lambda w PLINQ i TPL](lambda-expressions-in-plinq-and-tpl.md)
