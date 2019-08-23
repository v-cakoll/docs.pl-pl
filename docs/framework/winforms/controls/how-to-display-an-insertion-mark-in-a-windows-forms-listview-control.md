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
ms.openlocfilehash: f5de00fd41b24fc1a7f1ff4484c3a126e98952a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967832"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="d7ef3-102">Instrukcje: wyświetlanie znacznika wstawiania w kontrolce ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d7ef3-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="d7ef3-103">Znacznik wstawiania w <xref:System.Windows.Forms.ListView> kontrolce pokazuje użytkownikom punkt, w którym zostaną wstawione przeciągane elementy.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="d7ef3-104">Gdy użytkownik przeciągnie element do punktu między dwoma innymi elementami, znacznik wstawiania pokazuje oczekiwaną nową lokalizację elementu.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7ef3-105">Funkcja znacznika wstawiania jest dostępna tylko [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] wtedy, gdy aplikacja <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d7ef3-106">We wcześniejszych systemach operacyjnych każdy kod odnoszący się do znacznika wstawiania nie ma żadnego efektu i znacznik wstawiania nie zostanie wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="d7ef3-107">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="d7ef3-108">Na poniższej ilustracji przedstawiono znacznik wstawiania:</span><span class="sxs-lookup"><span data-stu-id="d7ef3-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="d7ef3-109">![Zrzut ekranu pokazujący znacznik wstawiania elementu ListView.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="d7ef3-109">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="d7ef3-110">Poniższy przykład kodu demonstruje, jak używać tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7ef3-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7ef3-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7ef3-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d7ef3-112">Compiling the Code</span></span>  
 <span data-ttu-id="d7ef3-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d7ef3-113">This example requires:</span></span>  
  
- <span data-ttu-id="d7ef3-114">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ef3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7ef3-115">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="d7ef3-116">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="d7ef3-116">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="d7ef3-117">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d7ef3-117">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="d7ef3-118">Przewodnik: Wykonywanie operacji przeciągania i upuszczania w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7ef3-118">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
