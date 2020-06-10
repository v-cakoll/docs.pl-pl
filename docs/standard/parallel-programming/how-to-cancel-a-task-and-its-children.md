---
title: 'Instrukcje: Anulowanie zadania i jego elementów podrzędnych'
description: Zobacz przykłady sposobów anulowania zadania i jego elementów podrzędnych w programie .NET. Przykłady obejmują kroki z możliwością anulowania zadań, aby zauważyć, że zadanie zostało anulowane.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 66daf00680b65aace1ce6367761e3ed81596d33b
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662683"
---
# <a name="how-to-cancel-a-task-and-its-children"></a>Instrukcje: Anulowanie zadania i jego elementów podrzędnych
W poniższych przykładach pokazano, jak wykonywać następujące zadania:  
  
1. Utwórz i uruchom zadanie z możliwością anulowania.  
  
2. Przekaż token anulowania do delegata użytkownika i opcjonalnie do wystąpienia zadania.  
  
3. Zwróć uwagę i Odpowiedz na żądanie anulowania w oddelegowaniu użytkownika.  
  
4. Opcjonalnie Zwróć uwagę na wątek wywołujący, że zadanie zostało anulowane.  
  
 Wątek wywołujący nie wymusi zakończyć zadania; tylko sygnalizuje to żądanie anulowania. Jeśli zadanie jest już uruchomione, należy do delegata użytkownika, aby zwrócić uwagę na żądanie i odpowiednio odpowiedzieć. Jeśli przed uruchomieniem zadania zostanie wysłane żądanie anulowania, delegat użytkownika nigdy nie zostanie wykonany, a obiekt zadania przechodzi do stanu anulowane.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak przerwać a <xref:System.Threading.Tasks.Task> i jego elementy podrzędne w odpowiedzi na żądanie anulowania. Pokazuje również, że gdy delegat użytkownika kończy działanie przez wyrzucanie <xref:System.Threading.Tasks.TaskCanceledException> , wątek wywołujący może opcjonalnie użyć <xref:System.Threading.Tasks.Task.Wait%2A> metody lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metody, aby poczekać na zakończenie zadań. W takim przypadku należy użyć `try/catch` bloku, aby obsłużyć wyjątki w wątku wywołującym.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Klasa jest w pełni zintegrowana z modelem anulowania opartym na <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> typach i <xref:System.Threading.CancellationToken?displayProperty=nameWithType> . Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](../threading/cancellation-in-managed-threads.md) i [Anulowanie zadania](task-cancellation.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Programowanie asynchroniczne oparte na zadaniach](task-based-asynchronous-programming.md)
- [Dołączone i odłączone zadania podrzędne](attached-and-detached-child-tasks.md)
- [Wyrażenia lambda w PLINQ i TPL](lambda-expressions-in-plinq-and-tpl.md)
