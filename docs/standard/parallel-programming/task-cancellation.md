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
ms.openlocfilehash: 17cabde95644dbc1584dd85b99e26ff7c5cb686d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139972"
---
# <a name="task-cancellation"></a>Anulowanie zadania
Klasy <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obsługują anulowanie przy użyciu tokenów anulowania w .NET Framework. Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md). W klasach Task anulowanie pociąga za sobą współpracę pełnomocnika użytkownika, który reprezentuje możliwości anulowania operacji i kodu, który zażądał anulowania.  Pomyślne anulowanie obejmuje żądanie kodu wywołującego metodę <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> i delegata użytkownika kończącego operację w odpowiednim czasie. Można zakończyć operację przy użyciu jednej z następujących opcji:  
  
- Powracając po prostu od pełnomocnika. W wielu scenariuszach jest to wystarczające. Jednak wystąpienie zadania, które zostało anulowane w ten sposób, przechodzi do stanu <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>, a nie do stanu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType>.  
  
- Przez wyrzucanie <xref:System.OperationCanceledException> i przekazywanie go tokenem, na którym zażądano anulowania. Preferowanym sposobem wykonania tej czynności jest użycie metody <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>. Zadanie, które zostało anulowane w ten sposób, przechodzi do stanu Canceled, którego kod wywołujący może użyć do sprawdzenia, czy zadanie odpowiedziało na żądanie anulowania.  
  
 Poniższy przykład przedstawia podstawowy wzorzec anulowania zadania ze zgłoszeniem wyjątku. Należy zauważyć, że token jest przekazywany do pełnomocnika użytkownika i do samego wystąpienia zadania.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Aby zapoznać się z bardziej kompletnym przykładem, zobacz [How to: Anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Gdy wystąpienie zadania obserwuje <xref:System.OperationCanceledException> zgłoszone przez kod użytkownika, porównuje token wyjątku ze skojarzonym tokenem (ten, który został przesłany do interfejsu API, który utworzył zadanie). Jeśli są takie same, a właściwość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> tokenu zwraca wartość true, zadanie interpretuje je jako potwierdzenie anulowania i przejścia do stanu anulowane. Jeśli nie używasz metody <xref:System.Threading.Tasks.Task.Wait%2A> lub <xref:System.Threading.Tasks.Task.WaitAll%2A> do oczekiwania na zadanie, zadanie po prostu ustawi jego stan na <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Jeśli oczekujesz na zadanie, które przechodzi do stanu anulowanego, zostanie zgłoszony wyjątek <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> (opakowany w wyjątek <xref:System.AggregateException>). Należy zauważyć, że ten wyjątek wskazuje pomyślne anulowanie, a nie błędną sytuację. W związku z tym, właściwość <xref:System.Threading.Tasks.Task.Exception%2A> zadania zwraca `null`.  
  
 Jeśli właściwość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> tokenu zwraca wartość false lub jeśli token wyjątku nie jest zgodny z tokenem zadania, <xref:System.OperationCanceledException> jest traktowany jak normalny wyjątek, powodując przejście zadania do stanu błędu. Należy także zauważyć, że obecność innych wyjątków także spowoduje przejście zadania do stanu Faulted. Stan ukończonego zadania można uzyskać we właściwości <xref:System.Threading.Tasks.Task.Status%2A>.  
  
 Możliwe jest, że zadanie będzie kontynuować przetwarzanie niektórych elementy po żądania anulowania.  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
