---
title: 'Instrukcje: Implementowanie formularza korzystającego z operacji w tle'
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
ms.openlocfilehash: 9ace37b1c79ff2e5cd06fce08557dc6cdf2fcc11
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261311"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="5abdd-102">Instrukcje: Implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="5abdd-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="5abdd-103">Poniższy przykład program tworzy formularz, który oblicza Fibonacci liczb.</span><span class="sxs-lookup"><span data-stu-id="5abdd-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="5abdd-104">Obliczenie jest uruchamiane w wątku, który jest oddzielony od wątku interfejsu użytkownika, dzięki czemu interfejs użytkownika będzie nadal działać bez opóźnień w trakcie wykonywania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="5abdd-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="5abdd-105">Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5abdd-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="5abdd-106">Zobacz też [instruktażu: Implementowanie formularza korzystającego z operacji w tle](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="5abdd-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5abdd-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="5abdd-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5abdd-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5abdd-108">Compiling the Code</span></span>  
 <span data-ttu-id="5abdd-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5abdd-109">This example requires:</span></span>  
  
-   <span data-ttu-id="5abdd-110">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="5abdd-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5abdd-111">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5abdd-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5abdd-112">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="5abdd-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5abdd-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5abdd-113">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5abdd-114">Korzystając z wielowątkowością jakiegokolwiek rodzaju, możesz potencjalnie się narazić na bardzo poważne i złożone usterek.</span><span class="sxs-lookup"><span data-stu-id="5abdd-114">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="5abdd-115">Zapoznaj się z [zarządzana wątkowość najlepsze](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem dowolne rozwiązanie, który używa wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="5abdd-115">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5abdd-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5abdd-116">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="5abdd-117">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="5abdd-117">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="5abdd-118">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5abdd-118">Managed Threading Best Practices</span></span>](../../../../docs/standard/threading/managed-threading-best-practices.md)
