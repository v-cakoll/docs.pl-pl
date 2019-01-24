---
title: 'Instrukcje: Uruchamianie operacji w tle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 99567897c90244c2768dfbcfe36762d1ec54a070
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510640"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="05633-102">Instrukcje: Uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="05633-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="05633-103">Jeśli operacja, która będzie zająć dużo czasu, i nie chcesz powodować opóźnienia w interfejsie użytkownika, możesz użyć <xref:System.ComponentModel.BackgroundWorker> klasy, aby uruchomić operację na inny wątek.</span><span class="sxs-lookup"><span data-stu-id="05633-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="05633-104">Poniższy przykład kodu pokazuje sposób uruchamiania czasochłonna operacja w tle.</span><span class="sxs-lookup"><span data-stu-id="05633-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="05633-105">Formularz zawiera **Start** i **anulować** przycisków.</span><span class="sxs-lookup"><span data-stu-id="05633-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="05633-106">Kliknij przycisk **Start** przycisk, aby uruchomić operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="05633-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="05633-107">Kliknij przycisk **anulować** przycisk, aby zatrzymać operację pracę asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="05633-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="05633-108">Wynikiem operacji jest wyświetlana w <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="05633-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="05633-109">Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05633-109">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="05633-110">Zobacz też [instruktażu: Przeprowadzanie operacji w tle](walkthrough-running-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="05633-110">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05633-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="05633-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="05633-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="05633-112">Compiling the Code</span></span>  
 <span data-ttu-id="05633-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="05633-113">This example requires:</span></span>  
  
-   <span data-ttu-id="05633-114">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="05633-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="05633-115">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="05633-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="05633-116">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="05633-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="05633-117">Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="05633-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05633-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05633-118">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="05633-119">Instrukcje: Implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="05633-119">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="05633-120">BackgroundWorker, składnik</span><span class="sxs-lookup"><span data-stu-id="05633-120">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
