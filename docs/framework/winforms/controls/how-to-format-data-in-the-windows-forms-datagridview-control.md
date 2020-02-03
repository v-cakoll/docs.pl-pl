---
title: Formatowanie danych w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 9ee2869cf4085b5acfdf1f8c440151be506dbe3e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736786"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f1547-102">Porady: formatowanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f1547-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f1547-103">W poniższych procedurach przedstawiono podstawowe formatowanie wartości komórek przy użyciu właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> kontrolki <xref:System.Windows.Forms.DataGridView> i określonych kolumn w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="f1547-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="f1547-104">Aby uzyskać informacje o zaawansowanym formatowaniu danych, zobacz [How to: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f1547-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="f1547-105">Aby sformatować wartości walutowe i daty</span><span class="sxs-lookup"><span data-stu-id="f1547-105">To format currency and date values</span></span>  
  
- <span data-ttu-id="f1547-106">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="f1547-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="f1547-107">Poniższy przykład kodu ustawia format dla konkretnych kolumn przy użyciu właściwości <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> kolumn.</span><span class="sxs-lookup"><span data-stu-id="f1547-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="f1547-108">Wartości w kolumnie `UnitPrice` są wyświetlane w bieżącym formacie waluty specyficznym dla kultury, z wartościami ujemnymi otoczonymi nawiasami.</span><span class="sxs-lookup"><span data-stu-id="f1547-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="f1547-109">Wartości w kolumnie `ShipDate` są wyświetlane w bieżącym formacie daty określonej dla kultury.</span><span class="sxs-lookup"><span data-stu-id="f1547-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="f1547-110">Aby uzyskać więcej informacji o <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> wartościach, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="f1547-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="f1547-111">Aby dostosować wyświetlanie wartości null bazy danych</span><span class="sxs-lookup"><span data-stu-id="f1547-111">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="f1547-112">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="f1547-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="f1547-113">Poniższy przykład kodu używa właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> do wyświetlania "No entry" we wszystkich komórkach zawierających wartości równe <xref:System.DBNull.Value?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1547-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="f1547-114">Aby włączyć WordWrap w komórkach tekstowych</span><span class="sxs-lookup"><span data-stu-id="f1547-114">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="f1547-115">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> <xref:System.Windows.Forms.DataGridViewCellStyle> na jedną z wartości wyliczenia <xref:System.Windows.Forms.DataGridViewTriState>.</span><span class="sxs-lookup"><span data-stu-id="f1547-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="f1547-116">Poniższy przykład kodu używa właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>, aby ustawić tryb zawijania dla całej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f1547-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="f1547-117">Aby określić wyrównanie tekstu dla komórek DataGridView</span><span class="sxs-lookup"><span data-stu-id="f1547-117">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="f1547-118">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> <xref:System.Windows.Forms.DataGridViewCellStyle> na jedną z wartości wyliczenia <xref:System.Windows.Forms.DataGridViewContentAlignment>.</span><span class="sxs-lookup"><span data-stu-id="f1547-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="f1547-119">Poniższy przykład kodu ustawia wyrównanie dla określonej kolumny przy użyciu właściwości <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> kolumny.</span><span class="sxs-lookup"><span data-stu-id="f1547-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="f1547-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1547-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f1547-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f1547-121">Compiling the Code</span></span>  
 <span data-ttu-id="f1547-122">Te przykłady wymagają:</span><span class="sxs-lookup"><span data-stu-id="f1547-122">These examples require:</span></span>  
  
- <span data-ttu-id="f1547-123">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`, która zawiera kolumnę o nazwie `UnitPrice`, kolumnę o nazwie `ShipDate`i kolumnę o nazwie `CustomerName`.</span><span class="sxs-lookup"><span data-stu-id="f1547-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="f1547-124">Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1547-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f1547-125">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="f1547-125">Robust Programming</span></span>  
 <span data-ttu-id="f1547-126">W celu uzyskania maksymalnej skalowalności należy udostępniać <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów zamiast ustawiania właściwości stylu dla każdego elementu osobno.</span><span class="sxs-lookup"><span data-stu-id="f1547-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="f1547-127">Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f1547-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1547-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1547-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="f1547-129">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f1547-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f1547-130">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f1547-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f1547-131">Formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f1547-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f1547-132">Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f1547-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f1547-133">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="f1547-133">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
