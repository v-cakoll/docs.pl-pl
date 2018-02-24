---
title: Dostrajanie aplikacji Async (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d8e655845f2d71e35ac72ba4f5a5b12027e2e1b
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="714b4-102">Dostrajanie aplikacji Async (C#)</span><span class="sxs-lookup"><span data-stu-id="714b4-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="714b4-103">Można dodać precision i elastyczności do aplikacji async przy użyciu metody i właściwości który <xref:System.Threading.Tasks.Task> udostępnia typu.</span><span class="sxs-lookup"><span data-stu-id="714b4-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="714b4-104">Tematy w tej sekcji przedstawiono przykłady, które używają <xref:System.Threading.CancellationToken> i ważnych `Task` metod, takich jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="714b4-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="714b4-105">Za pomocą `WhenAny` i `WhenAll`, można łatwiej Rozpoczynanie wielu zadań i poczekać na zakończenie przez jednego zadania monitorowania.</span><span class="sxs-lookup"><span data-stu-id="714b4-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="714b4-106">`WhenAny` Zwraca klasę task, który zostaje ukończony po ukończeniu zadań w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="714b4-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="714b4-107">Aby uzyskać przykłady pokazujące, które używają `WhenAny`, zobacz [anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) i [uruchomić wielu zadań asynchronicznych i procesu je jako ich pełne (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="714b4-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="714b4-108">`WhenAll` Zwraca klasę task, którego działanie jest kończone po zakończeniu wszystkich zadań w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="714b4-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="714b4-109">Więcej informacji oraz przykład `WhenAll`, zobacz [porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="714b4-109">For more information and an example that uses `WhenAll`, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="714b4-110">Ta sekcja zawiera następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="714b4-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="714b4-111">[Anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="714b4-111">[Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="714b4-112">Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)</span><span class="sxs-lookup"><span data-stu-id="714b4-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="714b4-113">Anulowanie pozostałych zadań asynchronicznych po jednym jest pełna (C#)</span><span class="sxs-lookup"><span data-stu-id="714b4-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="714b4-114">Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (C#)</span><span class="sxs-lookup"><span data-stu-id="714b4-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="714b4-115">Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="714b4-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="714b4-116">Projekty Tworzenie interfejsu użytkownika, który zawiera przyciski, która rozpoczyna się proces i anulujące, jak przedstawiono na poniższym obrazie.</span><span class="sxs-lookup"><span data-stu-id="714b4-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="714b4-117">Nazywania przyciski `startButton` i `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="714b4-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="714b4-118">![Okno WPF przy użyciu przycisku Anuluj](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "anulowania")</span><span class="sxs-lookup"><span data-stu-id="714b4-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="714b4-119">Możesz pobrać pełną projekty systemu Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="714b4-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714b4-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="714b4-120">See Also</span></span>  
 [<span data-ttu-id="714b4-121">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="714b4-121">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
