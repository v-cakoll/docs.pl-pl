---
title: 'Porady: implementowanie formularza korzystającego z operacji w tle'
description: Dowiedz się, jak zaimplementować formularz systemu Windows, który używa operacji w tle, tak aby jedna operacja mogła nadal działać, podczas gdy inna operacja jest kontynuowana.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 23bf4bc02fbf998d92dfce6d84e4e337cbefe7d9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174526"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="c44d0-103">Porady: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="c44d0-103">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="c44d0-104">Poniższy przykładowy program tworzy formularz, który oblicza numery Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="c44d0-104">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="c44d0-105">Obliczenie jest wykonywane w wątku, który jest oddzielony od wątku interfejsu użytkownika, dzięki czemu interfejs użytkownika będzie nadal działać bez opóźnień w miarę kontynuowania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="c44d0-105">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="c44d0-106">W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.</span><span class="sxs-lookup"><span data-stu-id="c44d0-106">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="c44d0-107">Zobacz również [Przewodnik: Implementowanie formularza korzystającego z operacji w tle](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="c44d0-107">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c44d0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c44d0-108">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c44d0-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c44d0-109">Compiling the Code</span></span>  
 <span data-ttu-id="c44d0-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c44d0-110">This example requires:</span></span>  
  
- <span data-ttu-id="c44d0-111">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="c44d0-111">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c44d0-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="c44d0-112">Robust Programming</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="c44d0-113">W przypadku korzystania z wielowątkowości dowolnego sortowania użytkownik może ujawnić sobie bardzo poważne i złożone usterki.</span><span class="sxs-lookup"><span data-stu-id="c44d0-113">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="c44d0-114">Przed zaimplementowaniem dowolnego rozwiązania, które używa wielowątkowości, należy zapoznać się z [zarządzanymi wątkami](../../../standard/threading/managed-threading-best-practices.md) .</span><span class="sxs-lookup"><span data-stu-id="c44d0-114">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c44d0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c44d0-115">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="c44d0-116">Asynchroniczny wzorzec oparty na zdarzeniach — przegląd</span><span class="sxs-lookup"><span data-stu-id="c44d0-116">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="c44d0-117">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="c44d0-117">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
