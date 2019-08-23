---
title: Dostrajanie aplikacji asynchronicznej (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 49e57d56c4df79cd9a3e8d5f76d6fc76ebdfa722
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958179"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Dostrajanie aplikacji asynchronicznej (Visual Basic)
Możesz dodać precyzję i elastyczność do aplikacji asynchronicznych przy użyciu metod i właściwości, które <xref:System.Threading.Tasks.Task> udostępnia typ. W tematach w tej sekcji przedstawiono przykłady użycia <xref:System.Threading.CancellationToken> i ważnych `Task` metod, takich <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> jak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>i.  
  
 Za pomocą `WhenAny` i `WhenAll`, można łatwiej uruchomić wiele zadań i oczekiwać ich ukończenia przez monitorowanie jednego zadania.  
  
- `WhenAny`zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.  
  
     Aby zapoznać się z `WhenAny`przykładami, zobacz [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)i [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich ukończenia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`zwraca zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji.  
  
     Aby uzyskać więcej informacji i przykład korzystania `WhenAll`z programu, zobacz [How to: Rozwiń Przewodnik asynchroniczny za pomocą polecenia Task. WhenAll (Visual Basic](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)).  
  
 Ta sekcja zawiera następujące przykłady.  
  
- [Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Anulowanie zadań asynchronicznych po upływie czasu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich kończenia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.  
  
 Projekty tworzą interfejs użytkownika, który zawiera przycisk uruchamiający proces i przycisk, który go anuluje, jak pokazano na poniższej ilustracji. Przyciski mają nazwę `startButton` i `cancelButton`.  
  
 ![Okno WPF z przyciskiem Anuluj] Okno (./media/fine-tuning-your-async-application/cancellation-and-start-button.png "dialogowe z przyciskiem uruchamiania i zatrzymywania")  
  
 Możesz pobrać kompletne projekty Windows Presentation Foundation (WPF) z [przykładu asynchronicznego: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
