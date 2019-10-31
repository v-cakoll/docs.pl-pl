---
title: 'Porady: anulowanie zadania i jego elementów podrzędnych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 4e0e783a4dfe3bf3a55795d7baef461369d7405a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134203"
---
# <a name="how-to-cancel-a-task-and-its-children"></a>Porady: anulowanie zadania i jego elementów podrzędnych
W poniższych przykładach pokazano, jak wykonywać następujące zadania:  
  
1. Utwórz i uruchom zadanie z możliwością anulowania.  
  
2. Przekaż token anulowania do delegata użytkownika i opcjonalnie do wystąpienia zadania.  
  
3. Zwróć uwagę i Odpowiedz na żądanie anulowania w oddelegowaniu użytkownika.  
  
4. Opcjonalnie Zwróć uwagę na wątek wywołujący, że zadanie zostało anulowane.  
  
 Wątek wywołujący nie wymusi zakończyć zadania; tylko sygnalizuje to żądanie anulowania. Jeśli zadanie jest już uruchomione, należy do delegata użytkownika, aby zwrócić uwagę na żądanie i odpowiednio odpowiedzieć. Jeśli przed uruchomieniem zadania zostanie wysłane żądanie anulowania, delegat użytkownika nigdy nie zostanie wykonany, a obiekt zadania przechodzi do stanu anulowane.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak przerwać <xref:System.Threading.Tasks.Task> i jego elementy podrzędne w odpowiedzi na żądanie anulowania. Pokazuje również, że po zakończeniu delegata użytkownika przez wyrzucanie <xref:System.Threading.Tasks.TaskCanceledException>, wątek wywołujący może opcjonalnie użyć metody <xref:System.Threading.Tasks.Task.Wait%2A> lub metody <xref:System.Threading.Tasks.Task.WaitAll%2A>, aby poczekać na zakończenie zadań. W takim przypadku należy użyć bloku `try/catch`, aby obsłużyć wyjątki w wątku wywołującym.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 Klasa <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest w pełni zintegrowana z modelem anulowania opartym na typach <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> i <xref:System.Threading.CancellationToken?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md) i [Anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
