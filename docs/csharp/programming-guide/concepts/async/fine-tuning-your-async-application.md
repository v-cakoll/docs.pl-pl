---
title: Dostrajanie aplikacji asynchronicznej (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cff50e62ff62b70e97e7ea6e03714326d774e407
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970241"
---
# <a name="fine-tuning-your-async-application-c"></a>Dostrajanie aplikacji asynchronicznej (C#)
Możesz dodać precyzję i elastyczność do swoich aplikacji asynchronicznych, korzystając z metod i właściwości, które udostępnia typ <xref:System.Threading.Tasks.Task>. W tematach w tej sekcji przedstawiono przykłady, które używają <xref:System.Threading.CancellationToken> i ważnych metod `Task`, takich jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Korzystając z `WhenAny` i `WhenAll`, można łatwiej uruchamiać wiele zadań i czekać ich na ukończenie przez monitorowanie jednego zadania.  
  
- `WhenAny` zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.  
  
     Aby zapoznać się z przykładami, które używają `WhenAny`, zobacz [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednegoC#()](./cancel-remaining-async-tasks-after-one-is-complete.md) i [Uruchamianie wielu zadań asynchronicznych iC#przetwarzanie ich w miarę ich ukończenia ()](./start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` zwraca zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji.  
  
     Aby uzyskać więcej informacji i przykład, który używa `WhenAll`, zobacz [jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task.C#WhenAll ()](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Ta sekcja zawiera następujące przykłady.  
  
- [Anulowanie zadania asynchronicznego lub listy zadańC#()](./cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Anulowanie zadań asynchronicznych po upływie czasu (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ichC#ukończenia ()](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.  
  
 Projekty tworzą interfejs użytkownika, który zawiera przycisk uruchamiający proces i przycisk, który go anuluje, jak pokazano na poniższej ilustracji. Przyciski mają nazwę `startButton` i `cancelButton`.  
  
 ![Okno WPF z przyciskiem Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Okno dialogowe z przyciskiem uruchamiania i zatrzymywania")  
  
 Możesz pobrać kompletne projekty Windows Presentation Foundation (WPF) z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await (C#)](./index.md)
