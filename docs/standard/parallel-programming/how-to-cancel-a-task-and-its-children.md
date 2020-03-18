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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134203"
---
# <a name="how-to-cancel-a-task-and-its-children"></a>Porady: anulowanie zadania i jego elementów podrzędnych
W poniższych przykładach przedstawiono sposób wykonywania następujących zadań:  
  
1. Tworzenie i rozpoczynanie zadania możliwego do anulowania.  
  
2. Przekaż token anulowania do delegata użytkownika i opcjonalnie do wystąpienia zadania.  
  
3. Zwiaduj i odpowiedz na żądanie anulowania w pełnomocniku użytkownika.  
  
4. Opcjonalnie należy zauważyć w wątku wywołującego, że zadanie zostało anulowane.  
  
 Wątek wywołujący nie powoduje wymuszenia zakończenia zadania; sygnalizuje jedynie, że wymagane jest anulowanie. Jeśli zadanie jest już uruchomione, to do delegata użytkownika, aby zauważyć żądanie i odpowiednio odpowiedzieć. Jeśli odwołanie jest wymagane przed wykonaniem zadania, delegat użytkownika nigdy nie jest wykonywany, a obiekt zadania przechodzi w stan Anulowane.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zakończyć a <xref:System.Threading.Tasks.Task> i jego podrzędne w odpowiedzi na żądanie anulowania. Pokazuje również, że gdy delegat użytkownika kończy <xref:System.Threading.Tasks.TaskCanceledException>się przez zgłaszanie , <xref:System.Threading.Tasks.Task.Wait%2A> wątek <xref:System.Threading.Tasks.Task.WaitAll%2A> wywołujący może opcjonalnie użyć metody lub metody, aby poczekać na zakończenie zadań. W takim przypadku należy `try/catch` użyć bloku do obsługi wyjątków w wątku wywołującego.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 Klasa <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest w pełni zintegrowany z modelem <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> <xref:System.Threading.CancellationToken?displayProperty=nameWithType> anulowania, który jest oparty na i typów. Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątków](../../../docs/standard/threading/cancellation-in-managed-threads.md) i [anulowanie zadań](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
