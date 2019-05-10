---
title: Dostrajanie aplikacji Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 3e9a6d02ec4948103b892ae012b8c51f66dd06c4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624733"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Dostrajanie aplikacji Async (Visual Basic)
Aby asynchroniczna aplikacja można dodać precyzyjna i elastyczna za pomocą metod i właściwości, <xref:System.Threading.Tasks.Task> udostępnia typu. W tematach w tej sekcji opisano przykłady z zastosowaniem <xref:System.Threading.CancellationToken> i ważnych `Task` metody takie jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Za pomocą `WhenAny` i `WhenAll`, można łatwiej uruchomić wiele zadań i czekać na ich zakończenie poprzez monitorowanie pojedynczego zadania.  
  
- `WhenAny` Zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.  
  
     Aby uzyskać przykłady, które używają `WhenAny`, zobacz [anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)i [uruchomić wielu zadań asynchronicznych i proces ich jako ich pełny (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` Zwraca klasę task, który zostaje ukończony po zakończeniu wszystkich zadań w kolekcji.  
  
     Aby uzyskać więcej informacji i przykład wykorzystujący `WhenAll`, zobacz [jak: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Ta sekcja zawiera następujące przykłady.  
  
- [Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Anulowanie zadań asynchronicznych po upływie określonego czasu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich po ich zakończeniu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
 Projekty tworzą interfejs użytkownika zawierający przycisk, który uruchamia proces i przycisk, który go anuluje, co pokazuje poniższa ilustracja. Przyciski nazywają się `startButton` i `cancelButton`.  
  
 ![Okno WPF za pomocą przycisku Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "okno dialogowe z przyciskiem rozpoczęcie i zakończenie")  
  
 Możesz pobrać pełne projekty Windows Presentation Foundation (WPF) z [próbka asynchroniczna: Dostrajania aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
