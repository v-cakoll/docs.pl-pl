---
title: Określ tryb edycji kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743764"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="9e7cc-102">Porady: określanie trybu edycji dla formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9e7cc-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9e7cc-103">Domyślnie użytkownicy mogą edytować zawartość bieżącej <xref:System.Windows.Forms.DataGridView> komórce pola tekstowego, wpisując ją lub naciskając klawisz F2.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="9e7cc-104">Spowoduje to umieszczenie komórki w trybie edycji, jeśli spełnione są wszystkie z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="9e7cc-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
- <span data-ttu-id="9e7cc-105">Bazowe źródło danych obsługuje edytowanie.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-105">The underlying data source supports editing.</span></span>  
  
- <span data-ttu-id="9e7cc-106">Kontrolka <xref:System.Windows.Forms.DataGridView> jest włączona.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
- <span data-ttu-id="9e7cc-107">Wartość właściwości <xref:System.Windows.Forms.DataGridView.EditMode%2A> nie jest <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
- <span data-ttu-id="9e7cc-108">Właściwości `ReadOnly` komórki, wiersza, kolumny i kontrolki są ustawione na `false`.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="9e7cc-109">W trybie edycji użytkownik może zmienić wartość komórki i nacisnąć klawisz ENTER, aby zatwierdzić zmianę lub ESC, aby przywrócić oryginalną wartość komórki.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="9e7cc-110">Można skonfigurować kontrolkę <xref:System.Windows.Forms.DataGridView> tak, aby komórka przejdzie do trybu edycji, gdy tylko stanie się bieżącą komórką.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="9e7cc-111">Zachowanie klawiszy ENTER i ESC jest niezmienione w tym przypadku, ale komórka pozostaje w trybie edycji po zatwierdzeniu lub wycofaniu wartości.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="9e7cc-112">Można również skonfigurować kontrolkę tak, aby komórki były w trybie edycji tylko wtedy, gdy użytkownik naciśnie w komórce lub tylko wtedy, gdy użytkownicy naciśnij F2.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="9e7cc-113">Na koniec można uniemożliwić komórkom wprowadzanie trybu edycji z wyjątkiem wywołania metody <xref:System.Windows.Forms.DataGridView.BeginEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="9e7cc-114">Aby zmienić tryb edycji kontrolki DataGridView</span><span class="sxs-lookup"><span data-stu-id="9e7cc-114">To change the edit mode of a DataGridView control</span></span>  
  
- <span data-ttu-id="9e7cc-115">Ustaw właściwość <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> na odpowiednie Wyliczenie <xref:System.Windows.Forms.DataGridViewEditMode>.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9e7cc-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9e7cc-116">Compiling the Code</span></span>  
 <span data-ttu-id="9e7cc-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9e7cc-117">This example requires:</span></span>  
  
- <span data-ttu-id="9e7cc-118">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="9e7cc-119">Odwołania do zestawów <xref:System> i <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="9e7cc-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7cc-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e7cc-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9e7cc-121">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e7cc-121">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
