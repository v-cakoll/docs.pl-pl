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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141672"
---
# <a name="how-to-return-a-value-from-a-task"></a>Porady: zwracanie wartości z zadania
W tym przykładzie pokazano, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> jak użyć <xref:System.Threading.Tasks.Task%601.Result%2A> tego typu, aby zwrócić wartość z właściwości. Wymaga ona, aby katalog C:\Users\Public\Pictures\Sample Pictures\ zawierał pliki.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje wątek wywołujący, dopóki zadanie nie zakończy.  
  
 Aby zobaczyć, jak przekazać <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> wynik jednego do zadania kontynuacji, zobacz [Łączenie zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
