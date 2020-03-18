---
title: Dostrajanie aplikacji asynchronicznej (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cff50e62ff62b70e97e7ea6e03714326d774e407
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970241"
---
# <a name="fine-tuning-your-async-application-c"></a>Dostrajanie aplikacji asynchronicznej (C#)
Można dodać precyzji i elastyczności do aplikacji asynchronicznej przy <xref:System.Threading.Tasks.Task> użyciu metod i właściwości, które typ udostępnia. Tematy w tej sekcji pokazują <xref:System.Threading.CancellationToken> przykłady, `Task` które używają <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>i ważne metody, takie jak i .  
  
 Za `WhenAny` pomocą `WhenAll`i , można łatwiej uruchomić wiele zadań i czekać na ich zakończenie poprzez monitorowanie jednego zadania.  
  
- `WhenAny`zwraca zadanie, które zostanie ukończone po zakończeniu dowolnego zadania w kolekcji.  
  
     Przykłady, które `WhenAny`używają , zobacz [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego z nich (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) i [uruchom wiele zadań asynchronicznych i przetwórz je w miarę ich ukończenia (C#).](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
- `WhenAll`zwraca zadanie, które zostanie ukończone po zakończeniu wszystkich zadań w kolekcji.  
  
     Aby uzyskać więcej informacji `WhenAll`i przykład, który używa , zobacz [Jak rozszerzyć instruktażu asynchronicznego przy użyciu Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Ta sekcja zawiera następujące przykłady.  
  
- [Anulowanie zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego z nich (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Uruchom wiele zadań asynchronicznych i przetwarzaj je po ich ukończeniu (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.  
  
 Projekty utworzyć ui, który zawiera przycisk, który uruchamia proces i przycisk, który anuluje go, jak pokazano na poniższej ilustracji. Przyciski są `startButton` `cancelButton`nazwane i .  
  
 ![Okno WPF z przyciskiem Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Okno dialogowe z przyciskiem Start i Stop")  
  
 Pełne projekty programu Windows Presentation Foundation (WPF) można pobrać z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne z async i await (C#)](./index.md)
