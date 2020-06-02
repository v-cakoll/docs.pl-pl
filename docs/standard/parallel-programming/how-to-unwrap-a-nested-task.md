---
title: 'Instrukcje: Odpakowywanie zadania zagnieżdżonego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: 9a69fa42da41ee4a071a6571042fd96fb5a009d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288033"
---
# <a name="how-to-unwrap-a-nested-task"></a>Instrukcje: Odpakowywanie zadania zagnieżdżonego
Można zwrócić zadanie z metody, a następnie zaczekać lub kontynuować z tego zadania, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 W poprzednim przykładzie <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość jest typu `string` ( `String` w Visual Basic).  
  
 Jednak w niektórych scenariuszach można utworzyć zadanie w innym zadaniu, a następnie zwrócić zagnieżdżone zadanie. W takim przypadku załączane `TResult` zadanie jest zadaniem. W poniższym przykładzie właściwość wynik jest `Task<Task<string>>` w języku C# lub `Task(Of Task(Of String))` w Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Chociaż istnieje możliwość napisania kodu w celu odpakowania zewnętrznego zadania i pobrania oryginalnego zadania i jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości, taki kod nie jest łatwy do zapisu, ponieważ należy obsługiwać wyjątki, a także żądania anulowania. W tej sytuacji zalecamy użycie jednej z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metod rozszerzających, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>Metody mogą służyć do przekształcania dowolnego `Task<Task>` lub `Task<Task<TResult>>` ( `Task(Of Task)` lub `Task(Of Task(Of TResult))` w Visual Basic) na `Task` lub `Task<TResult>` ( `Task(Of TResult)` w Visual Basic). Nowe zadanie w pełni reprezentuje wewnętrzne zagnieżdżone zadanie i zawiera stan anulowania oraz wszystkie wyjątki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób używania <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metod rozszerzających.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Programowanie asynchroniczne oparte na zadaniach](task-based-asynchronous-programming.md)
