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
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="a9e6a-102">Dostrajanie aplikacji asynchronicznej (C#)</span><span class="sxs-lookup"><span data-stu-id="a9e6a-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="a9e6a-103">Możesz dodać precyzję i elastyczność do swoich aplikacji asynchronicznych, korzystając z metod i właściwości, które udostępnia typ <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="a9e6a-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="a9e6a-104">W tematach w tej sekcji przedstawiono przykłady, które używają <xref:System.Threading.CancellationToken> i ważnych metod `Task`, takich jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a9e6a-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a9e6a-105">Korzystając z `WhenAny` i `WhenAll`, można łatwiej uruchamiać wiele zadań i czekać ich na ukończenie przez monitorowanie jednego zadania.</span><span class="sxs-lookup"><span data-stu-id="a9e6a-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="a9e6a-106">`WhenAny` zwraca zadanie, które kończy się po zakończeniu każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a9e6a-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="a9e6a-107">Aby zapoznać się z przykładami, które używają `WhenAny`, zobacz [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednegoC#()](./cancel-remaining-async-tasks-after-one-is-complete.md) i [Uruchamianie wielu zadań asynchronicznych iC#przetwarzanie ich w miarę ich ukończenia ()](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="a9e6a-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="a9e6a-108">`WhenAll` zwraca zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a9e6a-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="a9e6a-109">Aby uzyskać więcej informacji i przykład, który używa `WhenAll`, zobacz [jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task.C#WhenAll ()](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="a9e6a-109">For more information and an example that uses `WhenAll`, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="a9e6a-110">Ta sekcja zawiera następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="a9e6a-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="a9e6a-111">[Anulowanie zadania asynchronicznego lub listy zadańC#()](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="a9e6a-111">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="a9e6a-112">Anulowanie zadań asynchronicznych po upływie czasu (C#)</span><span class="sxs-lookup"><span data-stu-id="a9e6a-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="a9e6a-113">Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)</span><span class="sxs-lookup"><span data-stu-id="a9e6a-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="a9e6a-114">Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ichC#ukończenia ()</span><span class="sxs-lookup"><span data-stu-id="a9e6a-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="a9e6a-115">Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="a9e6a-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="a9e6a-116">Projekty tworzą interfejs użytkownika, który zawiera przycisk uruchamiający proces i przycisk, który go anuluje, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="a9e6a-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="a9e6a-117">Przyciski mają nazwę `startButton` i `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="a9e6a-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="a9e6a-118">![Okno WPF z przyciskiem Anuluj](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Okno dialogowe z przyciskiem uruchamiania i zatrzymywania")</span><span class="sxs-lookup"><span data-stu-id="a9e6a-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="a9e6a-119">Możesz pobrać kompletne projekty Windows Presentation Foundation (WPF) z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="a9e6a-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e6a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9e6a-120">See also</span></span>

- [<span data-ttu-id="a9e6a-121">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="a9e6a-121">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
