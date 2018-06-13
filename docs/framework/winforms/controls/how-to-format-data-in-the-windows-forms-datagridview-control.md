---
title: 'Porady: formatowanie danych w formancie DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: 7e3e281a766e22ed76bbf6ae7726cba092a9741d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538864"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="cafe5-102">Porady: formatowanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cafe5-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="cafe5-103">W poniższych procedurach pokazano podstawowe formatowanie wartości komórki za pomocą <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwość <xref:System.Windows.Forms.DataGridView> kontroli i określonych kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="cafe5-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="cafe5-104">Aby dowiedzieć się, jak formatowanie danych zaawansowanych, zobacz [porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="cafe5-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="cafe5-105">Format waluty i wartości daty</span><span class="sxs-lookup"><span data-stu-id="cafe5-105">To format currency and date values</span></span>  
  
-   <span data-ttu-id="cafe5-106">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="cafe5-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="cafe5-107">Poniższy przykład kodu Określa format określonych kolumn za pomocą <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości kolumn.</span><span class="sxs-lookup"><span data-stu-id="cafe5-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="cafe5-108">Wartości w `UnitPrice` kolumny wyświetlane w bieżącym formacie waluty specyficzne dla kultury ze ujemne wartości ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="cafe5-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="cafe5-109">Wartości w `ShipDate` kolumny są wyświetlane w formacie bieżącej daty krótkiej specyficzne dla kultury.</span><span class="sxs-lookup"><span data-stu-id="cafe5-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="cafe5-110">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> wartości, zobacz [typy formatowania](../../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="cafe5-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="cafe5-111">Aby dostosować wyświetlanie wartości null bazy danych</span><span class="sxs-lookup"><span data-stu-id="cafe5-111">To customize the display of null database values</span></span>  
  
-   <span data-ttu-id="cafe5-112">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="cafe5-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="cafe5-113">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwość, aby wyświetlić "nie wpisu" z komórek zawierających wartości równej <xref:System.DBNull.Value?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cafe5-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="cafe5-114">Aby włączyć zawijania tekstu w komórkach tekstowych</span><span class="sxs-lookup"><span data-stu-id="cafe5-114">To enable wordwrap in text-based cells</span></span>  
  
-   <span data-ttu-id="cafe5-115">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> do jednego z <xref:System.Windows.Forms.DataGridViewTriState> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cafe5-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="cafe5-116">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości, aby ustawić tryb zawijania dla całego formantu.</span><span class="sxs-lookup"><span data-stu-id="cafe5-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="cafe5-117">Aby określić wyrównanie tekstu komórek DataGridView</span><span class="sxs-lookup"><span data-stu-id="cafe5-117">To specify the text alignment of DataGridView cells</span></span>  
  
-   <span data-ttu-id="cafe5-118">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> do jednego z <xref:System.Windows.Forms.DataGridViewContentAlignment> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cafe5-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="cafe5-119">Poniższy przykład kodu Ustawia wyrównanie dla określonej kolumny za pomocą <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości kolumny.</span><span class="sxs-lookup"><span data-stu-id="cafe5-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="cafe5-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="cafe5-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cafe5-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cafe5-121">Compiling the Code</span></span>  
 <span data-ttu-id="cafe5-122">Wymagaj te przykłady:</span><span class="sxs-lookup"><span data-stu-id="cafe5-122">These examples require:</span></span>  
  
-   <span data-ttu-id="cafe5-123">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawiera kolumny o nazwie `UnitPrice`, kolumna o nazwie `ShipDate`, a kolumna o nazwie `CustomerName`.</span><span class="sxs-lookup"><span data-stu-id="cafe5-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
-   <span data-ttu-id="cafe5-124">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="cafe5-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cafe5-125">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="cafe5-125">Robust Programming</span></span>  
 <span data-ttu-id="cafe5-126">Skalowalność maksymalna powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki, które używają tego samego style niż ustawienie właściwości stylu dla każdego elementu oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="cafe5-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="cafe5-127">Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="cafe5-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cafe5-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cafe5-128">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="cafe5-129">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cafe5-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="cafe5-130">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cafe5-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="cafe5-131">Formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cafe5-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="cafe5-132">Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cafe5-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="cafe5-133">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="cafe5-133">Formatting Types</span></span>](../../../../docs/standard/base-types/formatting-types.md)
