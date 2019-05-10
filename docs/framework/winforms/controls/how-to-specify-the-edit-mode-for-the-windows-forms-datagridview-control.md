---
title: 'Instrukcje: określanie trybu edycji dla kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: a999582aeb629646fa1843f973b10a039c29e1a3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630525"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="d1883-102">Instrukcje: określanie trybu edycji dla kontrolki DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d1883-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d1883-103">Domyślnie użytkownicy mogą edytować zawartość bieżącego <xref:System.Windows.Forms.DataGridView> komórka pole tekstu, wpisując ją lub naciskając klawisz F2.</span><span class="sxs-lookup"><span data-stu-id="d1883-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="d1883-104">Komórka to umieszczenie w trybie edycji, jeśli są spełnione wszystkie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="d1883-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
- <span data-ttu-id="d1883-105">Źródła danych obsługuje edycję.</span><span class="sxs-lookup"><span data-stu-id="d1883-105">The underlying data source supports editing.</span></span>  
  
- <span data-ttu-id="d1883-106"><xref:System.Windows.Forms.DataGridView> Kontrolka jest włączona.</span><span class="sxs-lookup"><span data-stu-id="d1883-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
- <span data-ttu-id="d1883-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A> Wartość właściwości jest <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="d1883-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
- <span data-ttu-id="d1883-108">`ReadOnly` Właściwości komórek, wierszy, kolumny i kontrolki są gotowi do `false`.</span><span class="sxs-lookup"><span data-stu-id="d1883-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="d1883-109">W trybie edycji użytkownik może zmienić wartość komórki i naciśnij klawisz ENTER, aby zatwierdzić zmiany lub ESC, aby przywrócić komórki do oryginalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="d1883-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="d1883-110">Można skonfigurować <xref:System.Windows.Forms.DataGridView> kontrolki komórki przejdzie do trybu edycji tak szybko, jak staje się bieżącej komórki.</span><span class="sxs-lookup"><span data-stu-id="d1883-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="d1883-111">W tym przypadku zachowanie klawisze ENTER i ESC jest bez zmian, ale komórki pozostaje w trybie edycji po wartość nie zostanie przekazana lub przywrócić.</span><span class="sxs-lookup"><span data-stu-id="d1883-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="d1883-112">Można również skonfigurować kontrolkę tak, aby komórek trybu edycji tylko wtedy, gdy użytkownicy wpisują się w komórce lub tylko gdy użytkownicy naciśnij klawisz F2.</span><span class="sxs-lookup"><span data-stu-id="d1883-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="d1883-113">Na koniec można zapobiec komórek do trybu edycji z wyjątkiem sytuacji, gdy zostanie wywołana <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d1883-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="d1883-114">Aby zmienić tryb edycji kontrolki DataGridView</span><span class="sxs-lookup"><span data-stu-id="d1883-114">To change the edit mode of a DataGridView control</span></span>  
  
- <span data-ttu-id="d1883-115">Ustaw <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> właściwości do odpowiednich <xref:System.Windows.Forms.DataGridViewEditMode> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d1883-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1883-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d1883-116">Compiling the Code</span></span>  
 <span data-ttu-id="d1883-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d1883-117">This example requires:</span></span>  
  
- <span data-ttu-id="d1883-118">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="d1883-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="d1883-119">Odwołuje się do <xref:System> i <xref:System.Windows.Forms> zestawów.</span><span class="sxs-lookup"><span data-stu-id="d1883-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1883-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1883-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d1883-121">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1883-121">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
