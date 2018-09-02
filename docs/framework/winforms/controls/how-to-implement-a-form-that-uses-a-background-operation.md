---
title: 'Porady: implementowanie formularza korzystającego z operacji w tle'
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
ms.openlocfilehash: 8f348097223d2db4c54d9ecbba89eb8d179b6680
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404539"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="8616a-102">Porady: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="8616a-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="8616a-103">Poniższy przykład program tworzy formularz, który oblicza Fibonacci liczb.</span><span class="sxs-lookup"><span data-stu-id="8616a-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="8616a-104">Obliczenie jest uruchamiane w wątku, który jest oddzielony od wątku interfejsu użytkownika, dzięki czemu interfejs użytkownika będzie nadal działać bez opóźnień w trakcie wykonywania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="8616a-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="8616a-105">Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8616a-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="8616a-106">Zobacz też [wskazówki: Implementowanie formularza korzystającego z operacji w tle](https://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8616a-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](https://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8616a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8616a-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8616a-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8616a-108">Compiling the Code</span></span>  
 <span data-ttu-id="8616a-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="8616a-109">This example requires:</span></span>  
  
-   <span data-ttu-id="8616a-110">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8616a-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8616a-111">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8616a-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8616a-112">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="8616a-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="8616a-113">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8616a-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8616a-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="8616a-114">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8616a-115">Korzystając z wielowątkowością jakiegokolwiek rodzaju, możesz potencjalnie się narazić na bardzo poważne i złożone usterek.</span><span class="sxs-lookup"><span data-stu-id="8616a-115">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="8616a-116">Zapoznaj się z [zarządzana wątkowość najlepsze](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem dowolne rozwiązanie, który używa wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="8616a-116">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8616a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8616a-117">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="8616a-118">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="8616a-118">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="8616a-119">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="8616a-119">Managed Threading Best Practices</span></span>](../../../../docs/standard/threading/managed-threading-best-practices.md)
