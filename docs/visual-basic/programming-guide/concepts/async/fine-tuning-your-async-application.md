---
title: Dostrajanie aplikacji asynchronicznych
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 51786993cf16cd12b39cde3d47832191b3fdca8d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345833"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="22a53-102">Dostrajanie aplikacji asynchronicznej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22a53-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="22a53-103">Możesz dodać precyzję i elastyczność do swoich aplikacji asynchronicznych, korzystając z metod i właściwości, które udostępnia typ <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="22a53-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="22a53-104">W tematach w tej sekcji przedstawiono przykłady, które używają <xref:System.Threading.CancellationToken> i ważnych metod `Task`, takich jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22a53-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="22a53-105">Korzystając z `WhenAny` i `WhenAll`, można łatwiej uruchamiać wiele zadań i czekać ich na ukończenie przez monitorowanie jednego zadania.</span><span class="sxs-lookup"><span data-stu-id="22a53-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="22a53-106">`WhenAny` zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="22a53-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="22a53-107">Aby zapoznać się z przykładami, które używają `WhenAny`, zobacz [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)i [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich kończenia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="22a53-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="22a53-108">`WhenAll` zwraca zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="22a53-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="22a53-109">Aby uzyskać więcej informacji i przykład, który używa `WhenAll`, zobacz [How to: rozszerzając Przewodnik Async przy użyciu Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="22a53-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="22a53-110">Ta sekcja zawiera następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="22a53-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="22a53-111">[Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="22a53-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="22a53-112">Anulowanie zadań asynchronicznych po upływie czasu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22a53-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="22a53-113">Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22a53-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="22a53-114">Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich kończenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22a53-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="22a53-115">Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="22a53-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="22a53-116">Projekty tworzą interfejs użytkownika, który zawiera przycisk uruchamiający proces i przycisk, który go anuluje, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="22a53-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="22a53-117">Przyciski mają nazwę `startButton` i `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="22a53-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="22a53-118">![Okno WPF z przyciskiem Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Okno dialogowe z przyciskiem uruchamiania i zatrzymywania")</span><span class="sxs-lookup"><span data-stu-id="22a53-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="22a53-119">Możesz pobrać kompletne projekty Windows Presentation Foundation (WPF) z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="22a53-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a53-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22a53-120">See also</span></span>

- [<span data-ttu-id="22a53-121">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22a53-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
