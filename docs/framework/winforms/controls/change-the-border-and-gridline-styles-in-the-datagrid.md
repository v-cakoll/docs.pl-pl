---
title: Zmienianie stylów obramowania i linii siatki w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: 918102a87ee29a3d3b78d6e6eedce57237135a51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744699"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="432ef-102">Porady: zmienianie stylów obramowania i linii siatki w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="432ef-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="432ef-103">Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można dostosować wygląd obramowania i linii siatki kontrolki w celu ulepszenia środowiska użytkownika.</span><span class="sxs-lookup"><span data-stu-id="432ef-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="432ef-104">Oprócz stylów obramowania komórek w kontrolce, można zmodyfikować kolor linii siatki i styl obramowania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="432ef-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="432ef-105">Można również zastosować różne style obramowania komórek dla zwykłych komórek, komórek nagłówka wiersza i komórek nagłówka kolumny.</span><span class="sxs-lookup"><span data-stu-id="432ef-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="432ef-106">Kolor linii siatki jest używany tylko z wartościami <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>i <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> wyliczenia <xref:System.Windows.Forms.DataGridViewCellBorderStyle> i <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> wartości wyliczenia <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="432ef-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="432ef-107">Pozostałe wartości tych wyliczeń używają kolorów określonych przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="432ef-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="432ef-108">Ponadto, gdy style wizualizacji są włączone w systemie Windows XP i w rodzinie systemu Windows Server 2003 za pomocą metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>, wartość właściwości <xref:System.Windows.Forms.DataGridView.GridColor%2A> nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="432ef-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="432ef-109">Aby zmienić kolor linii siatki programowo</span><span class="sxs-lookup"><span data-stu-id="432ef-109">To change the gridline color programmatically</span></span>  
  
- <span data-ttu-id="432ef-110">Ustaw właściwość <xref:System.Windows.Forms.DataGridView.GridColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="432ef-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="432ef-111">Aby zmienić styl obramowania całego formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="432ef-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
- <span data-ttu-id="432ef-112">Ustaw właściwość <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> na jedną z <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="432ef-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="432ef-113">Aby programowo zmienić style obramowania dla komórek DataGridView</span><span class="sxs-lookup"><span data-stu-id="432ef-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
- <span data-ttu-id="432ef-114">Ustaw właściwości <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>i <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="432ef-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="432ef-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="432ef-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="432ef-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="432ef-116">Compiling the Code</span></span>  
 <span data-ttu-id="432ef-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="432ef-117">This example requires:</span></span>  
  
- <span data-ttu-id="432ef-118">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="432ef-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="432ef-119">Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>i <xref:System.Drawing?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="432ef-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="432ef-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="432ef-120">See also</span></span>

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [<span data-ttu-id="432ef-121">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="432ef-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
