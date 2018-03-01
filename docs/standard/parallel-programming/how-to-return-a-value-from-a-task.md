---
title: "Porady: zwracanie wartości z zadania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4497f7f9c6802a9b3d4edca66ceb4a894a59646a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-return-a-value-from-a-task"></a>Porady: zwracanie wartości z zadania
Ten przykład przedstawia sposób użycia <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typu w celu zwrócenia wartości z <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości. Wymaga ona, że C:\Users\Public\Pictures\Sample Pictures\ katalog istnieje i czy zawiera pliki.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość blokuje wątek wywołujący przed zakończeniem zadania.  
  
 Aby zobaczyć, jak przekazać wynik jednego <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> do kontynuacji zadania, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
