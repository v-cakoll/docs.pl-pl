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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af0f82e66da1c8db5e17863dfad861c8a7d195e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217220"
---
# <a name="how-to-return-a-value-from-a-task"></a>Porady: zwracanie wartości z zadania
W tym przykładzie pokazano, jak używać <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typu w celu zwrócenia wartości z <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości. Wymaga czy C:\Users\Public\Pictures\Sample Pictures\ katalog istnieje i czy zawiera on pliki.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość blokuje wątek wywołujący, aż do zakończenia zadania.  
  
 Aby zobaczyć, jak przekazać wynik jednego <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> do kontynuacji zadania, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
