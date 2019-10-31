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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106907"
---
# <a name="how-to-unwrap-a-nested-task"></a>Porady: dekodowanie zadania zagnieżdżonego
Można zwrócić zadanie z metody, a następnie zaczekać lub kontynuować z tego zadania, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 W poprzednim przykładzie właściwość <xref:System.Threading.Tasks.Task%601.Result%2A> jest typu `string` (`String` w Visual Basic).  
  
 Jednak w niektórych scenariuszach można utworzyć zadanie w innym zadaniu, a następnie zwrócić zagnieżdżone zadanie. W takim przypadku `TResult` zadania otaczającego to zadanie. W poniższym przykładzie właściwość Result jest `Task<Task<string>>` w C# lub `Task(Of Task(Of String))` w Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Chociaż istnieje możliwość napisania kodu w celu odpakowania zewnętrznego zadania i pobrania oryginalnego zadania i jego właściwości <xref:System.Threading.Tasks.Task%601.Result%2A>, taki kod nie jest łatwy do zapisu, ponieważ należy obsługiwać wyjątki, a także żądania anulowania. W tej sytuacji zalecamy użycie jednej z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metod rozszerzenia, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 Metody <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> mogą służyć do przekształcania dowolnego `Task<Task>` lub `Task<Task<TResult>>` (`Task(Of Task)` lub `Task(Of Task(Of TResult))` w Visual Basic) na `Task` lub `Task<TResult>` (`Task(Of TResult)` w Visual Basic). Nowe zadanie w pełni reprezentuje wewnętrzne zagnieżdżone zadanie i zawiera stan anulowania oraz wszystkie wyjątki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób używania metod rozszerzenia <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
