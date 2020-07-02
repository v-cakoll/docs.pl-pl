---
title: Formatowanie danych w formancie DataGridView
description: Dowiedz się, jak sformatować wartości komórek przy użyciu Windows Forms właściwości DefaultCellStyle kontrolki DataGridView i określonych kolumn w kontrolce.
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
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622812"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="136da-103">Porady: formatowanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="136da-103">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="136da-104">W poniższych procedurach przedstawiono podstawowe formatowanie wartości komórek przy użyciu <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwości <xref:System.Windows.Forms.DataGridView> kontrolki i określonych kolumn w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="136da-104">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="136da-105">Aby uzyskać informacje o zaawansowanym formatowaniu danych, zobacz [How to: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="136da-105">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="136da-106">Aby sformatować wartości walutowe i daty</span><span class="sxs-lookup"><span data-stu-id="136da-106">To format currency and date values</span></span>  
  
- <span data-ttu-id="136da-107">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> właściwość obiektu <xref:System.Windows.Forms.DataGridViewCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="136da-107">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="136da-108">Poniższy przykład kodu ustawia format dla konkretnych kolumn przy użyciu <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości kolumn.</span><span class="sxs-lookup"><span data-stu-id="136da-108">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="136da-109">Wartości w `UnitPrice` kolumnie są wyświetlane w bieżącym formacie waluty specyficznej dla kultury, z wartościami ujemnymi otoczonymi nawiasami.</span><span class="sxs-lookup"><span data-stu-id="136da-109">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="136da-110">Wartości w `ShipDate` kolumnie są wyświetlane w bieżącym formacie daty krótkiej specyficznej dla kultury.</span><span class="sxs-lookup"><span data-stu-id="136da-110">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="136da-111">Aby uzyskać więcej informacji o <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> wartościach, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="136da-111">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="136da-112">Aby dostosować wyświetlanie wartości null bazy danych</span><span class="sxs-lookup"><span data-stu-id="136da-112">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="136da-113">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> właściwość obiektu <xref:System.Windows.Forms.DataGridViewCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="136da-113">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="136da-114">Poniższy przykład kodu używa <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości do wyświetlania "No entry" we wszystkich komórkach zawierających wartości równe <xref:System.DBNull.Value?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="136da-114">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="136da-115">Aby włączyć WordWrap w komórkach tekstowych</span><span class="sxs-lookup"><span data-stu-id="136da-115">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="136da-116">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> Właściwość a <xref:System.Windows.Forms.DataGridViewCellStyle> na jedną z <xref:System.Windows.Forms.DataGridViewTriState> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="136da-116">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="136da-117">Poniższy przykład kodu używa właściwości, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> Aby ustawić tryb zawijania dla całej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="136da-117">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="136da-118">Aby określić wyrównanie tekstu dla komórek DataGridView</span><span class="sxs-lookup"><span data-stu-id="136da-118">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="136da-119">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> Właściwość a <xref:System.Windows.Forms.DataGridViewCellStyle> na jedną z <xref:System.Windows.Forms.DataGridViewContentAlignment> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="136da-119">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="136da-120">Poniższy przykład kodu ustawia wyrównanie dla określonej kolumny przy użyciu <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> Właściwości kolumny.</span><span class="sxs-lookup"><span data-stu-id="136da-120">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="136da-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="136da-121">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="136da-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="136da-122">Compiling the Code</span></span>  
 <span data-ttu-id="136da-123">Te przykłady wymagają:</span><span class="sxs-lookup"><span data-stu-id="136da-123">These examples require:</span></span>  
  
- <span data-ttu-id="136da-124"><xref:System.Windows.Forms.DataGridView>Kontrolka o nazwie, `dataGridView1` która zawiera kolumnę o nazwie `UnitPrice` , kolumnę o nazwie `ShipDate` i kolumnę o nazwie `CustomerName` .</span><span class="sxs-lookup"><span data-stu-id="136da-124">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="136da-125">Odwołania do <xref:System?displayProperty=nameWithType> zestawów, <xref:System.Drawing?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="136da-125">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="136da-126">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="136da-126">Robust Programming</span></span>  
 <span data-ttu-id="136da-127">Aby uzyskać maksymalną skalowalność, należy udostępnić <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów zamiast ustawiania właściwości stylu dla każdego elementu osobno.</span><span class="sxs-lookup"><span data-stu-id="136da-127">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="136da-128">Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="136da-128">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136da-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="136da-129">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="136da-130">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="136da-130">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="136da-131">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="136da-131">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="136da-132">Formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="136da-132">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="136da-133">Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="136da-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="136da-134">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="136da-134">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
