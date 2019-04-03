---
title: Dostrajanie aplikacji Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 88b26aea0740bb4a5c5e9d87790746a708bf45a1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838019"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="f1c3e-102">Dostrajanie aplikacji Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1c3e-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="f1c3e-103">Aby asynchroniczna aplikacja można dodać precyzyjna i elastyczna za pomocą metod i właściwości, <xref:System.Threading.Tasks.Task> udostępnia typu.</span><span class="sxs-lookup"><span data-stu-id="f1c3e-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="f1c3e-104">W tematach w tej sekcji opisano przykłady z zastosowaniem <xref:System.Threading.CancellationToken> i ważnych `Task` metody takie jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1c3e-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f1c3e-105">Za pomocą `WhenAny` i `WhenAll`, można łatwiej uruchomić wiele zadań i czekać na ich zakończenie poprzez monitorowanie pojedynczego zadania.</span><span class="sxs-lookup"><span data-stu-id="f1c3e-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="f1c3e-106">`WhenAny` Zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f1c3e-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="f1c3e-107">Aby uzyskać przykłady, które używają `WhenAny`, zobacz [anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)i [uruchomić wielu zadań asynchronicznych i proces ich jako ich pełny (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="f1c3e-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="f1c3e-108">`WhenAll` Zwraca klasę task, który zostaje ukończony po zakończeniu wszystkich zadań w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f1c3e-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="f1c3e-109">Aby uzyskać więcej informacji i przykład wykorzystujący `WhenAll`, zobacz [jak: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="f1c3e-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="f1c3e-110">Ta sekcja zawiera następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="f1c3e-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="f1c3e-111">[Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="f1c3e-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="f1c3e-112">Anulowanie zadań asynchronicznych po upływie określonego czasu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1c3e-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="f1c3e-113">Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1c3e-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="f1c3e-114">Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich po ich zakończeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1c3e-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="f1c3e-115">Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f1c3e-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="f1c3e-116">Projekty tworzą interfejs użytkownika zawierający przycisk, który uruchamia proces i przycisk, który go anuluje, co pokazuje poniższa ilustracja.</span><span class="sxs-lookup"><span data-stu-id="f1c3e-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="f1c3e-117">Przyciski nazywają się `startButton` i `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="f1c3e-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="f1c3e-118">![Okno WPF za pomocą przycisku Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "okno dialogowe z przyciskiem rozpoczęcie i zakończenie")</span><span class="sxs-lookup"><span data-stu-id="f1c3e-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="f1c3e-119">Możesz pobrać pełne projekty Windows Presentation Foundation (WPF) z [próbka asynchroniczna: Dostrajania aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="f1c3e-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c3e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1c3e-120">See also</span></span>

- [<span data-ttu-id="f1c3e-121">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1c3e-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
