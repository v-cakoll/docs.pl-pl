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
ms.openlocfilehash: c72654a2bc21035fe706d76018bb163d8ba01ee8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106907"
---
# <a name="how-to-unwrap-a-nested-task"></a>Porady: dekodowanie zadania zagnieżdżonego
Można zwrócić zadanie z metody, a następnie poczekać lub kontynuować z tego zadania, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 W poprzednim przykładzie <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość jest `string` typu`String` (w języku Visual Basic).  
  
 Jednak w niektórych scenariuszach można utworzyć zadanie w ramach innego zadania, a następnie zwrócić zagnieżdżone zadanie. W takim przypadku `TResult` zadanie otaczające jest samo w sobie zadaniem. W poniższym przykładzie Result właściwość `Task<Task<string>>` jest w `Task(Of Task(Of String))` języku C# lub w języku Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Chociaż istnieje możliwość zapisania kodu, aby rozpakować zadanie <xref:System.Threading.Tasks.Task%601.Result%2A> zewnętrzne i pobrać oryginalne zadanie i jego właściwość, taki kod nie jest łatwy do napisania, ponieważ należy obsługiwać wyjątki, a także żądania anulowania. W tej sytuacji zaleca się użycie <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> jednej z metod rozszerzenia, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Metody mogą służyć do przekształcania `Task<Task<TResult>>` `Task(Of Task)` dowolnego `Task(Of Task(Of TResult))` `Task<Task>` lub ( lub `Task<TResult>` w`Task(Of TResult)` języku Visual Basic) do lub ( w języku `Task` Visual Basic). Nowe zadanie w pełni reprezentuje wewnętrzne zagnieżdżone zadanie i obejmuje stan anulowania i wszystkie wyjątki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak używać metod <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozszerzenia.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
