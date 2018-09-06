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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb520169f8e7925862d415a4dfb65af09263b0d2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868500"
---
# <a name="how-to-cancel-a-task-and-its-children"></a>Porady: anulowanie zadania i jego elementów podrzędnych
Te przykłady przedstawiają sposób wykonywania następujących zadań:  
  
1.  Tworzenie i uruchamianie można anulować zadania.  
  
2.  Przekaż token anulowania w swoim delegacie użytkownika i opcjonalnie wystąpienia zadania.  
  
3.  Zwróć uwagę, a odpowiedź na żądanie anulowania w swoim delegacie użytkownika.  
  
4.  Opcjonalnie Zwróć uwagę na wątku wywołującym czy zadanie zostało anulowane.  
  
 Wątek wywołujący nie kończy wymuszone zadania; tylko sygnalizuje, że zażądano anulowania. Jeśli zadanie jest już uruchomiony, jest do pełnomocnika użytkownika Zwróć uwagę, żądania i odpowiednio reagować. Czy zażądano anulowania przed uruchomieniem zadania, pełnomocnika użytkownika nigdy nie jest wykonywana, a obiekt zadania przechodzi do stanu Canceled.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zakończyć <xref:System.Threading.Tasks.Task> i jego elementy podrzędne w odpowiedzi na żądanie anulowania. Pokazano także, czy po użytkownik delegować kończy się, zwracając <xref:System.Threading.Tasks.TaskCanceledException>, opcjonalnie możesz skorzystać z wątku wywołującego <xref:System.Threading.Tasks.Task.Wait%2A> metody lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metodę, aby czekać na zakończenie zadań. W takim przypadku należy użyć `try/catch` bloku obsługi wyjątków na wątku wywołującym.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Klasy jest w pełni zintegrowana z anulowania, który jest oparty na <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> i <xref:System.Threading.CancellationToken?displayProperty=nameWithType> typów. Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md) i [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
- [Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
