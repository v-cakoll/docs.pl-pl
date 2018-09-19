---
title: Dostrajanie aplikacji Async (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 23557c0c920fbd858e9bdf8ae629bd5ef5f0355b
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46008684"
---
# <a name="fine-tuning-your-async-application-c"></a>Dostrajanie aplikacji Async (C#)
Aby asynchroniczna aplikacja można dodać precyzyjna i elastyczna za pomocą metod i właściwości, <xref:System.Threading.Tasks.Task> udostępnia typu. W tematach w tej sekcji opisano przykłady z zastosowaniem <xref:System.Threading.CancellationToken> i ważnych `Task` metody takie jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Za pomocą `WhenAny` i `WhenAll`, można łatwiej uruchomić wiele zadań i czekać na ich zakończenie poprzez monitorowanie pojedynczego zadania.  
  
-   `WhenAny` Zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.  
  
     Aby uzyskać przykłady, które używają `WhenAny`, zobacz [anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) i [uruchomić wielu zadań asynchronicznych i proces ich jako ich pełny (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll` Zwraca klasę task, który zostaje ukończony po zakończeniu wszystkich zadań w kolekcji.  
  
     Aby uzyskać więcej informacji i przykład wykorzystujący `WhenAll`, zobacz [porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Ta sekcja zawiera następujące przykłady.  
  
-   [Anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich, po ich zakończeniu (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
 Projekty tworzą interfejs użytkownika zawierający przycisk, który uruchamia proces i przycisk, który go anuluje, co pokazuje poniższa ilustracja. Przyciski nazywają się `startButton` i `cancelButton`.  
  
 ![Okno WPF za pomocą przycisku Anuluj](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "anulowania")  
  
 Możesz pobrać pełne projekty Windows Presentation Foundation (WPF) z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
