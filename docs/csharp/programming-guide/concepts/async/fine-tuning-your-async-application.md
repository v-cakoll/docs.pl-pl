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
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="a903c-102">Dostrajanie aplikacji asynchronicznej (C#)</span><span class="sxs-lookup"><span data-stu-id="a903c-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="a903c-103">Można dodać precyzji i elastyczności do aplikacji asynchronicznej przy <xref:System.Threading.Tasks.Task> użyciu metod i właściwości, które typ udostępnia.</span><span class="sxs-lookup"><span data-stu-id="a903c-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="a903c-104">Tematy w tej sekcji pokazują <xref:System.Threading.CancellationToken> przykłady, `Task` które używają <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>i ważne metody, takie jak i .</span><span class="sxs-lookup"><span data-stu-id="a903c-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a903c-105">Za `WhenAny` pomocą `WhenAll`i , można łatwiej uruchomić wiele zadań i czekać na ich zakończenie poprzez monitorowanie jednego zadania.</span><span class="sxs-lookup"><span data-stu-id="a903c-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="a903c-106">`WhenAny`zwraca zadanie, które zostanie ukończone po zakończeniu dowolnego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a903c-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="a903c-107">Przykłady, które `WhenAny`używają , zobacz [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego z nich (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) i [uruchom wiele zadań asynchronicznych i przetwórz je w miarę ich ukończenia (C#).](./start-multiple-async-tasks-and-process-them-as-they-complete.md)</span><span class="sxs-lookup"><span data-stu-id="a903c-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="a903c-108">`WhenAll`zwraca zadanie, które zostanie ukończone po zakończeniu wszystkich zadań w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a903c-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="a903c-109">Aby uzyskać więcej informacji `WhenAll`i przykład, który używa , zobacz [Jak rozszerzyć instruktażu asynchronicznego przy użyciu Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="a903c-109">For more information and an example that uses `WhenAll`, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="a903c-110">Ta sekcja zawiera następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="a903c-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="a903c-111">[Anulowanie zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="a903c-111">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="a903c-112">Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)</span><span class="sxs-lookup"><span data-stu-id="a903c-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="a903c-113">Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego z nich (C#)</span><span class="sxs-lookup"><span data-stu-id="a903c-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="a903c-114">Uruchom wiele zadań asynchronicznych i przetwarzaj je po ich ukończeniu (C#)</span><span class="sxs-lookup"><span data-stu-id="a903c-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="a903c-115">Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a903c-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="a903c-116">Projekty utworzyć ui, który zawiera przycisk, który uruchamia proces i przycisk, który anuluje go, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="a903c-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="a903c-117">Przyciski są `startButton` `cancelButton`nazwane i .</span><span class="sxs-lookup"><span data-stu-id="a903c-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="a903c-118">![Okno WPF z przyciskiem Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Okno dialogowe z przyciskiem Start i Stop")</span><span class="sxs-lookup"><span data-stu-id="a903c-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="a903c-119">Pełne projekty programu Windows Presentation Foundation (WPF) można pobrać z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="a903c-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a903c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a903c-120">See also</span></span>

- [<span data-ttu-id="a903c-121">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="a903c-121">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
