---
title: 'Porady: wyświetlanie znacznika wstawiania w formancie ListView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: b9b6e1911d3e372861ebcdc5a175314d69c89175
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555308"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="e1076-102">Porady: wyświetlanie znacznika wstawiania w formancie ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e1076-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="e1076-103">Znacznika wstawiania w <xref:System.Windows.Forms.ListView> kontrolka pokazuje użytkowników punktu, w którym zostanie wstawiony przeciąganych elementów.</span><span class="sxs-lookup"><span data-stu-id="e1076-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="e1076-104">Gdy użytkownik przeciąga element do punktu między dwoma innymi elementami, znacznika wstawiania pokazuje oczekiwanych nową lokalizację elementu.</span><span class="sxs-lookup"><span data-stu-id="e1076-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1076-105">Funkcja znacznika wstawiania jest dostępna tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e1076-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e1076-106">W starszych systemach operacyjnych każdy kod odnoszących się do znacznika wstawiania nie ma wpływu i znacznika wstawiania nie będą widoczne.</span><span class="sxs-lookup"><span data-stu-id="e1076-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="e1076-107">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="e1076-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="e1076-108">Na poniższej ilustracji przedstawiono znacznika wstawiania:</span><span class="sxs-lookup"><span data-stu-id="e1076-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="e1076-109">![Znacznika wstawiania ListView](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="e1076-109">![A ListView Insertion Mark](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="e1076-110">Poniższy przykład kodu pokazuje, jak korzystać z tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e1076-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1076-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1076-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1076-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e1076-112">Compiling the Code</span></span>  
 <span data-ttu-id="e1076-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e1076-113">This example requires:</span></span>  
  
-   <span data-ttu-id="e1076-114">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e1076-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e1076-115">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e1076-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e1076-116">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="e1076-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e1076-117">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e1076-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1076-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1076-118">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewInsertionMark>  
 [<span data-ttu-id="e1076-119">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="e1076-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="e1076-120">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="e1076-120">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="e1076-121">Funkcje systemu Windows XP i kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1076-121">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="e1076-122">Przewodnik: wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1076-122">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
