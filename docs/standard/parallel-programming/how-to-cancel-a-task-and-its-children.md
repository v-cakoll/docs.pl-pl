---
title: "Porady: anulowanie zadania i jego elementów podrzędnych"
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
helpviewer_keywords: tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 374068694a3aa9724905964717dc5e77c09fc0ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-task-and-its-children"></a>Porady: anulowanie zadania i jego elementów podrzędnych
Następujące przykłady przedstawiają sposób wykonywania następujących zadań:  
  
1.  Tworzenie i uruchamianie zadań można anulować.  
  
2.  Przekaż token anulowania do pełnomocnika użytkownika i opcjonalnie wystąpienia zadania.  
  
3.  Zwróć uwagę i odpowiadać na żądania anulowania w pełnomocnika użytkownika.  
  
4.  Opcjonalnie Zwróć uwagę na wątek wywołujący czy zadanie zostało anulowane.  
  
 Wątek wywołujący nie wymuszanie kończy zadanie; sygnalizuje tylko, że zażądano anulowania. Jeśli zadanie jest już uruchomiona, jest delegowanie użytkownika Zwróć uwagę, żądanie i reagowania. Jeśli przed uruchomieniem zadania żądanie anulowania, delegat użytkownika nie został wykonany i obiekt zadania przechodzi do stanu Anulowano.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zakończyć <xref:System.Threading.Tasks.Task> i jego elementów podrzędnych w odpowiedzi na żądanie anulowania. Także pokazanie, gdy użytkownik delegować przerwanie przez zgłaszanie <xref:System.Threading.Tasks.TaskCanceledException>, wątek wywołujący może opcjonalnie korzystać <xref:System.Threading.Tasks.Task.Wait%2A> metody lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metody oczekiwania na zakończenie zadań. W takim przypadku należy użyć `try/catch` bloku obsługi wyjątków w wątku wywołującym.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Klasy jest w pełni zintegrowana z modelem anulowania, na podstawie <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> i <xref:System.Threading.CancellationToken?displayProperty=nameWithType> typów. Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md) i [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
 <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
 [Programowanie asynchroniczne opartego na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
 [Wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
