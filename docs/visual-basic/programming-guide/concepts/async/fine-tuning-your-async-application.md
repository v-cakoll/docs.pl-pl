---
title: Dostrajanie aplikacji Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 6e919d3998719186d0355b9bd187782fcb0e5332
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696679"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Dostrajanie aplikacji Async (Visual Basic)
Można dodać precision i elastyczności do aplikacji async przy użyciu metody i właściwości który <xref:System.Threading.Tasks.Task> udostępnia typu. Tematy w tej sekcji przedstawiono przykłady, które używają <xref:System.Threading.CancellationToken> i ważnych `Task` metod, takich jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Za pomocą `WhenAny` i `WhenAll`, można łatwiej Rozpoczynanie wielu zadań i poczekać na zakończenie przez jednego zadania monitorowania.  
  
-   `WhenAny` Zwraca klasę task, który zostaje ukończony po ukończeniu zadań w kolekcji.  
  
     Aby uzyskać przykłady pokazujące, które używają `WhenAny`, zobacz [anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)i [uruchomić wielu zadań asynchronicznych i procesu je jako ich pełne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll` Zwraca klasę task, którego działanie jest kończone po zakończeniu wszystkich zadań w kolekcji.  
  
     Więcej informacji oraz przykład `WhenAll`, zobacz [porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Ta sekcja zawiera następujące przykłady.  
  
-   [Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Anulowanie zadań asynchronicznych po upływie określonego czasu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Anulowanie pozostałych zadań asynchronicznych po jednym jest pełna (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
 Projekty Tworzenie interfejsu użytkownika, który zawiera przyciski, która rozpoczyna się proces i anulujące, jak przedstawiono na poniższym obrazie. Nazywania przyciski `startButton` i `cancelButton`.  
  
 ![Okno WPF przy użyciu przycisku Anuluj](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "anulowania")  
  
 Możesz pobrać pełną projekty systemu Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
