---
title: 'Instrukcje: wyświetlanie znacznika wstawiania w kontrolce ListView formularzy systemu Windows'
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
ms.openlocfilehash: 60b775408f5c43ff08fc5c7de72a8302b20b2264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969727"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="804d3-102">Instrukcje: wyświetlanie znacznika wstawiania w kontrolce ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="804d3-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="804d3-103">Znacznika wstawiania w <xref:System.Windows.Forms.ListView> kontrolka pokazuje użytkowników punktu, w którym zostanie wstawiony przeciąganych elementów.</span><span class="sxs-lookup"><span data-stu-id="804d3-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="804d3-104">Gdy użytkownik przeciąga element do punktu między dwoma innymi elementami, znacznika wstawiania pokazuje oczekiwanych nową lokalizację elementu.</span><span class="sxs-lookup"><span data-stu-id="804d3-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="804d3-105">Funkcja znacznika wstawiania jest dostępna tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="804d3-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="804d3-106">W starszych systemach operacyjnych każdy kod odnoszących się do znacznika wstawiania nie ma wpływu i znacznika wstawiania nie będą widoczne.</span><span class="sxs-lookup"><span data-stu-id="804d3-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="804d3-107">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="804d3-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="804d3-108">Na poniższej ilustracji przedstawiono znacznika wstawiania:</span><span class="sxs-lookup"><span data-stu-id="804d3-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="804d3-109">![Zrzut Ekranu pokazujący znacznika wstawiania ListView. ](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="804d3-109">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="804d3-110">Poniższy przykład kodu pokazuje, jak korzystać z tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="804d3-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="804d3-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="804d3-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="804d3-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="804d3-112">Compiling the Code</span></span>  
 <span data-ttu-id="804d3-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="804d3-113">This example requires:</span></span>  
  
- <span data-ttu-id="804d3-114">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="804d3-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="804d3-115">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="804d3-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="804d3-116">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="804d3-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804d3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="804d3-117">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="804d3-118">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="804d3-118">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="804d3-119">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="804d3-119">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="804d3-120">Przewodnik: Wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="804d3-120">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
