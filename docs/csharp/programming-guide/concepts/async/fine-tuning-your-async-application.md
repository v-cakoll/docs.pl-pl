---
title: Dostrajanie aplikacji asynchronicznej (C#)
description: Te przykłady w języku C# używają CancellationToken i ważnych metod zadań, takich jak Task. WhenAll i Task. WhenAny, do dostrajania aplikacji asynchronicznych.
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 46457f889a78932e306d2bd21dca666625d744eb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925322"
---
# <a name="fine-tuning-your-async-application-c"></a>Dostrajanie aplikacji asynchronicznej (C#)
Możesz dodać precyzję i elastyczność do aplikacji asynchronicznych przy użyciu metod i właściwości, które udostępnia <xref:System.Threading.Tasks.Task> Typ. W tematach w tej sekcji przedstawiono przykłady użycia <xref:System.Threading.CancellationToken> i ważnych `Task` metod, takich jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> .  
  
 Za pomocą `WhenAny` i `WhenAll` , można łatwiej uruchomić wiele zadań i oczekiwać ich ukończenia przez monitorowanie jednego zadania.  
  
- `WhenAny`zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.  
  
     Aby zapoznać się z przykładami `WhenAny` , zobacz [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego (c#)](./cancel-remaining-async-tasks-after-one-is-complete.md) i [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich ukończenia (c#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`zwraca zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji.  
  
     Aby uzyskać więcej informacji i przykład używany przez `WhenAll` program, zobacz [jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Ta sekcja zawiera następujące przykłady.  
  
- [Anulowanie zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Anulowanie zadań asynchronicznych po upływie czasu (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich kończenia (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.  
  
 Projekty tworzą interfejs użytkownika, który zawiera przycisk uruchamiający proces i przycisk, który go anuluje, jak pokazano na poniższej ilustracji. Przyciski mają nazwę `startButton` i `cancelButton` .  
  
 ![Okno WPF z przyciskiem Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Okno dialogowe z przyciskiem uruchamiania i zatrzymywania")  
  
 Możesz pobrać kompletne projekty Windows Presentation Foundation (WPF) z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await (C#)](./index.md)
