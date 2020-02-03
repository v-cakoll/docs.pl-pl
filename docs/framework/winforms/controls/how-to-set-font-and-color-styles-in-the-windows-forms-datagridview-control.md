---
title: Ustawianie stylów czcionek i kolorów w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
ms.openlocfilehash: f1ee9131cfc0b28a5f6263dcd6254d27a092cc62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746761"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fcf24-102">Porady: ustawianie stylów czcionek i koloru w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fcf24-102">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fcf24-103">Aby określić wygląd komórek w kontrolce <xref:System.Windows.Forms.DataGridView>, należy ustawić właściwości klasy <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="fcf24-103">You can specify the visual appearance of cells within a <xref:System.Windows.Forms.DataGridView> control by setting properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span> <span data-ttu-id="fcf24-104">Można pobrać wystąpienia tej klasy z różnych właściwości klasy <xref:System.Windows.Forms.DataGridView> i jej klas towarzyszących lub można utworzyć wystąpienia obiektów <xref:System.Windows.Forms.DataGridViewCellStyle> do przypisywania do tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="fcf24-104">You can retrieve instances of this class from various properties of the <xref:System.Windows.Forms.DataGridView> class and its companion classes, or you can instantiate <xref:System.Windows.Forms.DataGridViewCellStyle> objects for assignment to these properties.</span></span>  
  
 <span data-ttu-id="fcf24-105">W poniższych procedurach przedstawiono podstawowe dostosowanie wyglądu komórki przy użyciu właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcf24-105">The following procedures demonstrate basic customization of cell appearance using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property.</span></span> <span data-ttu-id="fcf24-106">Każda komórka w kontrolce dziedziczy style określone za pomocą tej właściwości, chyba że zostaną zastąpione na poziomie kolumny, wiersza lub komórki.</span><span class="sxs-lookup"><span data-stu-id="fcf24-106">Every cell in the control inherits the styles specified through this property unless they are overridden at the column, row, or cell level.</span></span> <span data-ttu-id="fcf24-107">Aby zapoznać się z przykładem dziedziczenia stylu, zobacz [jak: Ustawianie domyślnych stylów komórek dla kontrolki DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fcf24-107">For an example of style inheritance, see [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="fcf24-108">Aby uzyskać informacje o dodatkowych zastosowaniach klasy <xref:System.Windows.Forms.DataGridViewCellStyle>, zobacz tematy wymienione w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="fcf24-108">For information about additional uses of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, see the topics listed in the See Also section.</span></span>  
  
 <span data-ttu-id="fcf24-109">W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.</span><span class="sxs-lookup"><span data-stu-id="fcf24-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="fcf24-110">Zobacz również [instrukcje: Ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView Windows Forms przy użyciu narzędzia Projektant](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="fcf24-110">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a><span data-ttu-id="fcf24-111">Aby określić czcionkę używaną przez komórki DataGridView</span><span class="sxs-lookup"><span data-stu-id="fcf24-111">To specify the font used by DataGridView cells</span></span>  
  
- <span data-ttu-id="fcf24-112">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="fcf24-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="fcf24-113">Poniższy przykład kodu używa właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> do ustawiania czcionki dla całej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fcf24-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the font for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a><span data-ttu-id="fcf24-114">Aby określić kolory pierwszego planu i tła dla komórek DataGridView</span><span class="sxs-lookup"><span data-stu-id="fcf24-114">To specify the foreground and background colors of DataGridView cells</span></span>  
  
- <span data-ttu-id="fcf24-115">Ustaw właściwości <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="fcf24-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="fcf24-116">Poniższy przykład kodu używa właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>, aby ustawić te style dla całej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fcf24-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a><span data-ttu-id="fcf24-117">Aby określić kolory pierwszego planu i tła wybranych komórek DataGridView</span><span class="sxs-lookup"><span data-stu-id="fcf24-117">To specify the foreground and background colors of selected DataGridView cells</span></span>  
  
- <span data-ttu-id="fcf24-118">Ustaw właściwości <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="fcf24-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="fcf24-119">Poniższy przykład kodu używa właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>, aby ustawić te style dla całej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fcf24-119">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a><span data-ttu-id="fcf24-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="fcf24-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fcf24-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fcf24-121">Compiling the Code</span></span>  
 <span data-ttu-id="fcf24-122">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="fcf24-122">This example requires:</span></span>  
  
- <span data-ttu-id="fcf24-123">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="fcf24-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="fcf24-124">Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcf24-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fcf24-125">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="fcf24-125">Robust Programming</span></span>  
 <span data-ttu-id="fcf24-126">Aby uzyskać maksymalną skalowalność, należy udostępnić <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów, zamiast ustawiania właściwości stylu dla każdego elementu osobno.</span><span class="sxs-lookup"><span data-stu-id="fcf24-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="fcf24-127">Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fcf24-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf24-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcf24-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="fcf24-129">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcf24-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fcf24-130">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcf24-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
