---
title: Dostrajanie aplikacji Async (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c42f51d627f827e216e6c25b3bde60e32b9ba027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="fine-tuning-your-async-application-c"></a>Dostrajanie aplikacji Async (C#)
Można dodać precision i elastyczności do aplikacji async przy użyciu metody i właściwości który <xref:System.Threading.Tasks.Task> udostępnia typu. Tematy w tej sekcji przedstawiono przykłady, które używają <xref:System.Threading.CancellationToken> i ważnych `Task` metod, takich jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Za pomocą `WhenAny` i `WhenAll`, można łatwiej Rozpoczynanie wielu zadań i poczekać na zakończenie przez jednego zadania monitorowania.  
  
-   `WhenAny`Zwraca klasę task, który zostaje ukończony po ukończeniu zadań w kolekcji.  
  
     Aby uzyskać przykłady pokazujące, które używają `WhenAny`, zobacz [anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) i [uruchomić wielu zadań asynchronicznych i procesu je jako ich pełne (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll`Zwraca klasę task, którego działanie jest kończone po zakończeniu wszystkich zadań w kolekcji.  
  
     Więcej informacji oraz przykład `WhenAll`, zobacz [porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Ta sekcja zawiera następujące przykłady.  
  
-   [Anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Anulowanie pozostałych zadań asynchronicznych po jednym jest pełna (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
 Projekty Tworzenie interfejsu użytkownika, który zawiera przyciski, która rozpoczyna się proces i anulujące, jak przedstawiono na poniższym obrazie. Nazywania przyciski `startButton` i `cancelButton`.  
  
 ![Okno WPF przy użyciu przycisku Anuluj](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "anulowania")  
  
 Możesz pobrać pełną projekty systemu Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
