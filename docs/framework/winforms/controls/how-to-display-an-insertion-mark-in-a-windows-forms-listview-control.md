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
ms.openlocfilehash: 62d105dc3c0b9aabc3699c12259e1624ac31a3a0
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960438"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="6d71f-102">Porady: wyświetlanie znacznika wstawiania w formancie ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6d71f-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="6d71f-103">Znacznik wstawiania w kontrolce <xref:System.Windows.Forms.ListView> pokazuje użytkownikom punkt, w którym zostaną wstawione przeciągane elementy.</span><span class="sxs-lookup"><span data-stu-id="6d71f-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="6d71f-104">Gdy użytkownik przeciągnie element do punktu między dwoma innymi elementami, znacznik wstawiania pokazuje oczekiwaną nową lokalizację elementu.</span><span class="sxs-lookup"><span data-stu-id="6d71f-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
 <span data-ttu-id="6d71f-105">Na poniższej ilustracji przedstawiono znacznik wstawiania:</span><span class="sxs-lookup"><span data-stu-id="6d71f-105">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="6d71f-106">![Zrzut ekranu pokazujący znacznik wstawiania elementu ListView.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="6d71f-106">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="6d71f-107">Poniższy przykład kodu demonstruje, jak używać tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="6d71f-107">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d71f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d71f-108">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6d71f-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6d71f-109">Compiling the Code</span></span>  
 <span data-ttu-id="6d71f-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6d71f-110">This example requires:</span></span>  
  
- <span data-ttu-id="6d71f-111">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="6d71f-111">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d71f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d71f-112">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="6d71f-113">ListView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6d71f-113">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="6d71f-114">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6d71f-114">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="6d71f-115">Przewodnik: wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d71f-115">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
