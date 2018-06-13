---
title: 'Porady: dekodowanie zadania zagnieżdżonego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9cee6817378503a3b98424ff4166725a46f7a29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580734"
---
# <a name="how-to-unwrap-a-nested-task"></a>Porady: dekodowanie zadania zagnieżdżonego
Można zwrócić zadania przy użyciu metody, a następnie zaczekaj na lub kontynuować z tego zadania, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 W poprzednim przykładzie <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość jest typu `string` (`String` w języku Visual Basic).  
  
 Jednak w niektórych scenariuszach, można utworzyć zadanie w ramach innego zadania, a następnie wróć zadania zagnieżdżonego. W takim przypadku `TResult` otaczającego zadania jest zadanie. W poniższym przykładzie jest właściwość Result `Task<Task<string>>` w języku C# lub `Task(Of Task(Of String))` w języku Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Chociaż można napisać kod dekodowanie zadania zewnętrznego i pobrać oryginalnego zadania i jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość, taki kod nie jest łatwa do zapisu, ponieważ musi obsłużyć wyjątki, a także żądań anulowania. W takiej sytuacji, firma Microsoft zaleca, użyj jednej z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Metod można użyć do przekształcania żadnego `Task<Task>` lub `Task<Task<TResult>>` (`Task(Of Task)` lub `Task(Of Task(Of TResult))` w języku Visual Basic) do `Task` lub `Task<TResult>` (`Task(Of TResult)` w języku Visual Basic). Nowe zadanie w pełni reprezentuje wewnętrzny zadania zagnieżdżonego i obejmuje stan anulowania oraz wszystkie wyjątki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
