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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139972"
---
# <a name="task-cancellation"></a>Anulowanie zadania
I <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> klasy obsługują anulowanie za pomocą tokenów anulowania w .NET Framework. Aby uzyskać więcej informacji, zobacz [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md). W klasach Task anulowanie pociąga za sobą współpracę pełnomocnika użytkownika, który reprezentuje możliwości anulowania operacji i kodu, który zażądał anulowania.  Pomyślne anulowanie obejmuje żądający <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kod wywołujący metodę, a użytkownik delegować zakończenie operacji w odpowiednim czasie. Można zakończyć operację przy użyciu jednej z następujących opcji:  
  
- Powracając po prostu od pełnomocnika. W wielu scenariuszach jest to wystarczające; jednak wystąpienie zadania, które zostało anulowane w ten <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> sposób przechodzi <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> do stanu, a nie do stanu.  
  
- Przez wyrzucając <xref:System.OperationCanceledException> i przekazując mu token, na którym zażądano anulowania. Preferowanym sposobem na to jest <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> użycie metody. Zadanie, które zostało anulowane w ten sposób, przechodzi do stanu Canceled, którego kod wywołujący może użyć do sprawdzenia, czy zadanie odpowiedziało na żądanie anulowania.  
  
 Poniższy przykład przedstawia podstawowy wzorzec anulowania zadania ze zgłoszeniem wyjątku. Należy zauważyć, że token jest przekazywany do pełnomocnika użytkownika i do samego wystąpienia zadania.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Aby uzyskać pełniejszy przykład, zobacz [Jak: Anulować zadanie i jego podrzędne](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Gdy wystąpienie zadania obserwuje <xref:System.OperationCanceledException> wygenerowany przez kod użytkownika, porównuje token wyjątku z jego tokenskojarzony (ten, który został przekazany do interfejsu API, który utworzył zadanie). Jeśli są one takie same, <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> a właściwość tokenu zwraca true, zadanie interpretuje to jako potwierdzenie anulowania i przejścia do stanu Anulowane. Jeśli nie używasz <xref:System.Threading.Tasks.Task.Wait%2A> lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metody czekać na zadanie, a następnie zadanie <xref:System.Threading.Tasks.TaskStatus.Canceled>po prostu ustawia jego stan .  
  
 Jeśli oczekujesz na zadanie, które przechodzi do <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> Canceled stanu, <xref:System.AggregateException> wyjątek (opakowane w wyjątek) jest generowany. Należy zauważyć, że ten wyjątek wskazuje pomyślne anulowanie, a nie błędną sytuację. W związku z <xref:System.Threading.Tasks.Task.Exception%2A> tym `null`właściwość zadania zwraca .  
  
 Jeśli właściwość tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> zwraca false lub token wyjątku nie pasuje token zadania, <xref:System.OperationCanceledException> jest traktowany jak normalny wyjątek, powodując Task do przejścia do Faulted stanu. Należy także zauważyć, że obecność innych wyjątków także spowoduje przejście zadania do stanu Faulted. Stan ukończonego zadania można uzyskać we <xref:System.Threading.Tasks.Task.Status%2A> właściwości.  
  
 Możliwe jest, że zadanie będzie kontynuować przetwarzanie niektórych elementy po żądania anulowania.  
  
## <a name="see-also"></a>Zobacz też

- [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
