---
title: Dostrajanie aplikacji Async
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: e33f86177a3680d41ec04842dbc120713a48f61c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396652"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Dostrajanie aplikacji asynchronicznej (Visual Basic)
Możesz dodać precyzję i elastyczność do aplikacji asynchronicznych przy użyciu metod i właściwości, które udostępnia <xref:System.Threading.Tasks.Task> Typ. W tematach w tej sekcji przedstawiono przykłady użycia <xref:System.Threading.CancellationToken> i ważnych `Task` metod, takich jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> .  
  
 Za pomocą `WhenAny` i `WhenAll` , można łatwiej uruchomić wiele zadań i oczekiwać ich ukończenia przez monitorowanie jednego zadania.  
  
- `WhenAny`zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.  
  
     Aby zapoznać się z przykładami `WhenAny` , zobacz [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)i [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich ukończenia (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`zwraca zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji.  
  
     Aby uzyskać więcej informacji i przykład korzystania z programu `WhenAll` , zobacz [How to: rozszerzając Przewodnik Async przy użyciu Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Ta sekcja zawiera następujące przykłady.  
  
- [Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Anulowanie zadań asynchronicznych po upływie czasu (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)  
  
- [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich kończenia (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.  
  
 Projekty tworzą interfejs użytkownika, który zawiera przycisk uruchamiający proces i przycisk, który go anuluje, jak pokazano na poniższej ilustracji. Przyciski mają nazwę `startButton` i `cancelButton` .  
  
 ![Okno WPF z przyciskiem Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Okno dialogowe z przyciskiem uruchamiania i zatrzymywania")  
  
 Możesz pobrać kompletne projekty Windows Presentation Foundation (WPF) z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne z Async i Await (Visual Basic)](index.md)
