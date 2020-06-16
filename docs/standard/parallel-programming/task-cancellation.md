---
title: Anulowanie zadania
description: Zrozumienie anulowania zadań, które są obsługiwane w klasach zadań i zadań <TResult> za pomocą tokenów anulowania w programie .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
ms.openlocfilehash: 1d9b7b35341961c27107f007e0eafa51ef49e232
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768667"
---
# <a name="task-cancellation"></a>Anulowanie zadania
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Klasy i <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> obsługują anulowanie przy użyciu tokenów anulowania w .NET Framework. Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](../threading/cancellation-in-managed-threads.md). W klasach Task anulowanie pociąga za sobą współpracę pełnomocnika użytkownika, który reprezentuje możliwości anulowania operacji i kodu, który zażądał anulowania.  Pomyślne anulowanie obejmuje żądanie kodu wywołującego <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę, a delegat użytkownika przerywa operację w odpowiednim czasie. Można zakończyć operację przy użyciu jednej z następujących opcji:  
  
- Powracając po prostu od pełnomocnika. W wielu scenariuszach jest to wystarczające. Jednak wystąpienie zadania, które zostało anulowane w ten sposób, przechodzi do <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> stanu, a nie do <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanu.  
  
- Przez wyrzucanie <xref:System.OperationCanceledException> i przekazywanie go tokenem, na którym zażądano anulowania. Preferowanym sposobem wykonania tych czynności jest użycie <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody. Zadanie, które zostało anulowane w ten sposób, przechodzi do stanu Canceled, którego kod wywołujący może użyć do sprawdzenia, czy zadanie odpowiedziało na żądanie anulowania.  
  
 Poniższy przykład przedstawia podstawowy wzorzec anulowania zadania ze zgłoszeniem wyjątku. Należy zauważyć, że token jest przekazywany do pełnomocnika użytkownika i do samego wystąpienia zadania.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Aby zapoznać się z bardziej kompletnym przykładem, zobacz [How to: Anulowanie zadania i jego elementów podrzędnych](how-to-cancel-a-task-and-its-children.md).  
  
 Gdy wystąpienie zadania obserwuje <xref:System.OperationCanceledException> zgłoszone przez kod użytkownika, porównuje token wyjątku ze skojarzonym tokenem (ten, który został przesłany do interfejsu API, który utworzył zadanie). Jeśli są takie same, a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość tokenu zwraca wartość true, zadanie interpretuje je jako potwierdzenie anulowania i przejścia do stanu anulowane. Jeśli nie używasz <xref:System.Threading.Tasks.Task.Wait%2A> <xref:System.Threading.Tasks.Task.WaitAll%2A> metody lub do oczekiwania na zadanie, zadanie po prostu ustawi jego stan na <xref:System.Threading.Tasks.TaskStatus.Canceled> .  
  
 Jeśli oczekujesz na zadanie, które przechodzi do stanu anulowanego, <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> zostanie zgłoszony wyjątek (opakowany jako <xref:System.AggregateException> wyjątek). Należy zauważyć, że ten wyjątek wskazuje pomyślne anulowanie, a nie błędną sytuację. W związku z tym <xref:System.Threading.Tasks.Task.Exception%2A> Właściwość zadania zwraca wartość `null` .  
  
 Jeśli <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość tokenu zwraca wartość false lub jeśli token wyjątku nie jest zgodny z tokenem zadania, <xref:System.OperationCanceledException> jest traktowany jak normalny wyjątek, powodując przejście zadania do stanu błędu. Należy także zauważyć, że obecność innych wyjątków także spowoduje przejście zadania do stanu Faulted. Stan ukończonego zadania można uzyskać we <xref:System.Threading.Tasks.Task.Status%2A> właściwości.  
  
 Możliwe jest, że zadanie będzie kontynuować przetwarzanie niektórych elementy po żądania anulowania.  
  
## <a name="see-also"></a>Zobacz też

- [Anulowanie w zarządzanych wątkach](../threading/cancellation-in-managed-threads.md)
- [Instrukcje: Anulowanie zadania i jego elementów podrzędnych](how-to-cancel-a-task-and-its-children.md)
