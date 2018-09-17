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
ms.openlocfilehash: 224f9273b0c8c9445a6a9e25f064e9726acc84f0
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750196"
---
# <a name="how-to-unwrap-a-nested-task"></a>Porady: dekodowanie zadania zagnieżdżonego
Może zwracać zadanie z metody, a następnie poczekaj lub kontynuować z tego zadania, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 W poprzednim przykładzie <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość jest typu `string` (`String` w języku Visual Basic).  
  
 Jednak w niektórych przypadkach warto utworzyć zadanie w ramach innego zadania, a następnie wróć zadania zagnieżdżonego. W tym przypadku `TResult` otaczającej zadania jest zadaniem. W poniższym przykładzie jest właściwości wyniku `Task<Task<string>>` w języku C# lub `Task(Of Task(Of String))` w języku Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Chociaż istnieje możliwość napisać kod odpakowywanie zadania zewnętrznego i pobrać, oryginalnym zadaniem i jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości takiego kodu nie jest łatwo zapisać, ponieważ musi obsłużyć wyjątki, a także żądań anulowania. W takiej sytuacji firma Microsoft zaleca, użyj jednej z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Metody może służyć do przekształcania dowolne `Task<Task>` lub `Task<Task<TResult>>` (`Task(Of Task)` lub `Task(Of Task(Of TResult))` w języku Visual Basic) do `Task` lub `Task<TResult>` (`Task(Of TResult)` w języku Visual Basic). Nowe zadanie pełni reprezentuje wewnętrzne zadanie zagnieżdżone, a obejmują stan anulowania i wszystkie wyjątki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
