---
title: 'Instrukcje: wykonywanie niestandardowej akcji na podstawie zmian w komórce kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: 23753a2c0ceab9452bde24a1c56348eabf87d655
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654433"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="ca2dd-102">Instrukcje: wykonywanie niestandardowej akcji na podstawie zmian w komórce kontrolki DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ca2dd-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ca2dd-103"><xref:System.Windows.Forms.DataGridView> Kontroli zawiera liczbę zdarzeń, można użyć do wykrywania zmian w stanie <xref:System.Windows.Forms.DataGridView> komórek.</span><span class="sxs-lookup"><span data-stu-id="ca2dd-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="ca2dd-104">Dwa najczęściej używane są <xref:System.Windows.Forms.DataGridView.CellValueChanged> i <xref:System.Windows.Forms.DataGridView.CellStateChanged> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ca2dd-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="ca2dd-105">Aby wykryć zmiany wartości komórek DataGridView</span><span class="sxs-lookup"><span data-stu-id="ca2dd-105">To detect changes in the values of DataGridView cells</span></span>  
  
- <span data-ttu-id="ca2dd-106">Pisanie programu obsługi dla <xref:System.Windows.Forms.DataGridView.CellValueChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ca2dd-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="ca2dd-107">Aby wykryć zmiany w Stanach komórek DataGridView</span><span class="sxs-lookup"><span data-stu-id="ca2dd-107">To detect changes in the states of DataGridView cells</span></span>  
  
- <span data-ttu-id="ca2dd-108">Pisanie programu obsługi dla <xref:System.Windows.Forms.DataGridView.CellStateChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ca2dd-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca2dd-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ca2dd-109">Compiling the Code</span></span>  
 <span data-ttu-id="ca2dd-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ca2dd-110">This example requires:</span></span>  
  
- <span data-ttu-id="ca2dd-111">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="ca2dd-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="ca2dd-112">Aby uzyskać C#, programy obsługi zdarzeń musi być podłączony do pokrewnych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ca2dd-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
- <span data-ttu-id="ca2dd-113">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="ca2dd-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca2dd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca2dd-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [<span data-ttu-id="ca2dd-115">Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ca2dd-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [<span data-ttu-id="ca2dd-116">Przewodnik: Sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ca2dd-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
