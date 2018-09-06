---
title: Dostrajanie aplikacji Async (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 23557c0c920fbd858e9bdf8ae629bd5ef5f0355b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032263"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="091ff-102">Dostrajanie aplikacji Async (C#)</span><span class="sxs-lookup"><span data-stu-id="091ff-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="091ff-103">Aby asynchroniczna aplikacja można dodać precyzyjna i elastyczna za pomocą metod i właściwości, <xref:System.Threading.Tasks.Task> udostępnia typu.</span><span class="sxs-lookup"><span data-stu-id="091ff-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="091ff-104">W tematach w tej sekcji opisano przykłady z zastosowaniem <xref:System.Threading.CancellationToken> i ważnych `Task` metody takie jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="091ff-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="091ff-105">Za pomocą `WhenAny` i `WhenAll`, można łatwiej uruchomić wiele zadań i czekać na ich zakończenie poprzez monitorowanie pojedynczego zadania.</span><span class="sxs-lookup"><span data-stu-id="091ff-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="091ff-106">`WhenAny` Zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="091ff-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="091ff-107">Aby uzyskać przykłady, które używają `WhenAny`, zobacz [anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) i [uruchomić wielu zadań asynchronicznych i proces ich jako ich pełny (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="091ff-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="091ff-108">`WhenAll` Zwraca klasę task, który zostaje ukończony po zakończeniu wszystkich zadań w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="091ff-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="091ff-109">Aby uzyskać więcej informacji i przykład wykorzystujący `WhenAll`, zobacz [porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="091ff-109">For more information and an example that uses `WhenAll`, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="091ff-110">Ta sekcja zawiera następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="091ff-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="091ff-111">[Anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="091ff-111">[Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="091ff-112">Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)</span><span class="sxs-lookup"><span data-stu-id="091ff-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="091ff-113">Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)</span><span class="sxs-lookup"><span data-stu-id="091ff-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="091ff-114">Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich, po ich zakończeniu (C#)</span><span class="sxs-lookup"><span data-stu-id="091ff-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="091ff-115">Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="091ff-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="091ff-116">Projekty tworzą interfejs użytkownika zawierający przycisk, który uruchamia proces i przycisk, który go anuluje, co pokazuje poniższa ilustracja.</span><span class="sxs-lookup"><span data-stu-id="091ff-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="091ff-117">Przyciski nazywają się `startButton` i `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="091ff-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="091ff-118">![Okno WPF za pomocą przycisku Anuluj](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "anulowania")</span><span class="sxs-lookup"><span data-stu-id="091ff-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="091ff-119">Możesz pobrać pełne projekty Windows Presentation Foundation (WPF) z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="091ff-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="091ff-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="091ff-120">See Also</span></span>

- [<span data-ttu-id="091ff-121">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="091ff-121">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
