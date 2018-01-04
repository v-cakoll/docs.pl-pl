---
title: "Porady: określanie trybu edycji dla formantu DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42773e29d7071c5bc5f3d5de3660c9891788b422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="5700f-102">Porady: określanie trybu edycji dla formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5700f-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5700f-103">Domyślnie użytkownicy mogą edytować zawartość bieżącego <xref:System.Windows.Forms.DataGridView> komórki pola tekstowego, wpisując w nim lub naciskając klawisz F2.</span><span class="sxs-lookup"><span data-stu-id="5700f-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="5700f-104">Komórka to umieszcza w trybie edycji, jeśli są spełnione wszystkie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="5700f-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="5700f-105">Źródła danych obsługuje edycję.</span><span class="sxs-lookup"><span data-stu-id="5700f-105">The underlying data source supports editing.</span></span>  
  
-   <span data-ttu-id="5700f-106"><xref:System.Windows.Forms.DataGridView> Formant jest włączony.</span><span class="sxs-lookup"><span data-stu-id="5700f-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
-   <span data-ttu-id="5700f-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A> Wartość właściwości jest <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="5700f-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
-   <span data-ttu-id="5700f-108">`ReadOnly` Właściwości komórek, wierszy, kolumny i kontroli mają ustawione `false`.</span><span class="sxs-lookup"><span data-stu-id="5700f-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="5700f-109">W trybie edycji użytkownik może zmienić wartość komórki i naciśnij klawisz ENTER, aby zatwierdzić zmiany lub ESC, aby przywrócić komórki do wartości oryginalnej.</span><span class="sxs-lookup"><span data-stu-id="5700f-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="5700f-110">Można skonfigurować <xref:System.Windows.Forms.DataGridView> , aby komórki wprowadza tryb edycji, jak staje się bieżącą komórką.</span><span class="sxs-lookup"><span data-stu-id="5700f-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="5700f-111">W takim przypadku zachowanie klawiszy ENTER i ESC pozostanie niezmieniona, ale komórki pozostaje w trybie edycji po zatwierdzenia lub przywrócono wartość.</span><span class="sxs-lookup"><span data-stu-id="5700f-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="5700f-112">Można również skonfigurować formantu, aby komórek przejść do trybu edycji tylko wtedy, gdy użytkownicy wpisują w komórce lub tylko, gdy użytkowników klawisz F2.</span><span class="sxs-lookup"><span data-stu-id="5700f-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="5700f-113">Na koniec można zapobiec komórek trybu edycji z wyjątkiem przypadków, gdy jest wywoływana <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5700f-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="5700f-114">Aby zmienić tryb edycji formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="5700f-114">To change the edit mode of a DataGridView control</span></span>  
  
-   <span data-ttu-id="5700f-115">Ustaw <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> właściwości do odpowiedniego <xref:System.Windows.Forms.DataGridViewEditMode> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5700f-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5700f-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5700f-116">Compiling the Code</span></span>  
 <span data-ttu-id="5700f-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5700f-117">This example requires:</span></span>  
  
-   <span data-ttu-id="5700f-118">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="5700f-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="5700f-119">Odwołuje się do <xref:System> i <xref:System.Windows.Forms> zestawów.</span><span class="sxs-lookup"><span data-stu-id="5700f-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5700f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5700f-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="5700f-121">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5700f-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
