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
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="73a05-103">Dostrajanie aplikacji asynchronicznej (C#)</span><span class="sxs-lookup"><span data-stu-id="73a05-103">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="73a05-104">Możesz dodać precyzję i elastyczność do aplikacji asynchronicznych przy użyciu metod i właściwości, które udostępnia <xref:System.Threading.Tasks.Task> Typ.</span><span class="sxs-lookup"><span data-stu-id="73a05-104">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="73a05-105">W tematach w tej sekcji przedstawiono przykłady użycia <xref:System.Threading.CancellationToken> i ważnych `Task` metod, takich jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73a05-105">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="73a05-106">Za pomocą `WhenAny` i `WhenAll` , można łatwiej uruchomić wiele zadań i oczekiwać ich ukończenia przez monitorowanie jednego zadania.</span><span class="sxs-lookup"><span data-stu-id="73a05-106">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="73a05-107">`WhenAny`zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="73a05-107">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="73a05-108">Aby zapoznać się z przykładami `WhenAny` , zobacz [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego (c#)](./cancel-remaining-async-tasks-after-one-is-complete.md) i [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich ukończenia (c#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="73a05-108">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="73a05-109">`WhenAll`zwraca zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="73a05-109">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="73a05-110">Aby uzyskać więcej informacji i przykład używany przez `WhenAll` program, zobacz [jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="73a05-110">For more information and an example that uses `WhenAll`, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="73a05-111">Ta sekcja zawiera następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="73a05-111">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="73a05-112">[Anulowanie zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="73a05-112">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="73a05-113">Anulowanie zadań asynchronicznych po upływie czasu (C#)</span><span class="sxs-lookup"><span data-stu-id="73a05-113">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="73a05-114">Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)</span><span class="sxs-lookup"><span data-stu-id="73a05-114">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="73a05-115">Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich kończenia (C#)</span><span class="sxs-lookup"><span data-stu-id="73a05-115">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="73a05-116">Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="73a05-116">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="73a05-117">Projekty tworzą interfejs użytkownika, który zawiera przycisk uruchamiający proces i przycisk, który go anuluje, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="73a05-117">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="73a05-118">Przyciski mają nazwę `startButton` i `cancelButton` .</span><span class="sxs-lookup"><span data-stu-id="73a05-118">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="73a05-119">![Okno WPF z przyciskiem Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Okno dialogowe z przyciskiem uruchamiania i zatrzymywania")</span><span class="sxs-lookup"><span data-stu-id="73a05-119">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="73a05-120">Możesz pobrać kompletne projekty Windows Presentation Foundation (WPF) z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="73a05-120">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a05-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73a05-121">See also</span></span>

- [<span data-ttu-id="73a05-122">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="73a05-122">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
