---
title: Anulowanie zadania
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84da3e1e896397b4e5dacec9d7dd0eeeed96d1c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908924"
---
# <a name="task-cancellation"></a>Anulowanie zadania
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> klasy obsługują anulowania przy użyciu tokenów anulowania w .NET Framework. Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md). W klasach Task anulowanie pociąga za sobą współpracę pełnomocnika użytkownika, który reprezentuje możliwości anulowania operacji i kodu, który zażądał anulowania.  Pomyślne anulowanie wiąże się żądania wywołania kodu <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda i zakończeniem operacji w sposób terminowy pełnomocnika użytkownika. Można zakończyć operację przy użyciu jednej z następujących opcji:  
  
- Powracając po prostu od pełnomocnika. W wielu sytuacjach jest to wystarczające; Jednak wystąpienie zadania, które zostało anulowane w ten sposób, przechodzi do <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> nie do stanu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanu.  
  
- Zgłaszając <xref:System.OperationCanceledException> i przekazanie do niej token zażądano anulowania. Preferowanym sposobem na to jest użycie <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody. Zadanie, które zostało anulowane w ten sposób, przechodzi do stanu Canceled, którego kod wywołujący może użyć do sprawdzenia, czy zadanie odpowiedziało na żądanie anulowania.  
  
 Poniższy przykład przedstawia podstawowy wzorzec anulowania zadania ze zgłoszeniem wyjątku. Należy zauważyć, że token jest przekazywany do pełnomocnika użytkownika i do samego wystąpienia zadania.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Aby uzyskać pełniejszy przykład, zobacz [jak: Anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Gdy wystąpienia zadania wykryje <xref:System.OperationCanceledException> zgłaszany przez kod użytkownika, porównuje token wyjątku ze skojarzonym tokenem (jeden, który został przekazany do interfejsu API, który utworzył zadanie). Jeśli są takie same, jak i token <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość zwraca wartość true, zadanie interpretuje to jako potwierdzenie anulowania i przechodzi do stanu Canceled. Jeśli nie używasz <xref:System.Threading.Tasks.Task.Wait%2A> lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metoda oczekiwania dla zadania, wówczas zadanie ustawienie tylko jego stan <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Jeśli czekasz na zadanie, które przechodzi do stanu Canceled <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> wyjątek (otoczona <xref:System.AggregateException> wyjątek) jest zgłaszany. Należy zauważyć, że ten wyjątek wskazuje pomyślne anulowanie, a nie błędną sytuację. W związku z tym, zadania podrzędnego <xref:System.Threading.Tasks.Task.Exception%2A> właściwość zwraca `null`.  
  
 Jeśli token <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość zwraca wartość false lub token wyjątku ze niezgodna zadania użytkownika tokenu, <xref:System.OperationCanceledException> jest traktowany jak normalny wyjątek, powodując przejście zadania do stanu Faulted. Należy także zauważyć, że obecność innych wyjątków także spowoduje przejście zadania do stanu Faulted. Możesz uzyskać stan ukończonego zadania we <xref:System.Threading.Tasks.Task.Status%2A> właściwości.  
  
 Możliwe jest, że zadanie będzie kontynuować przetwarzanie niektórych elementy po żądania anulowania.  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [Instrukcje: Anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
