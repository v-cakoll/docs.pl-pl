---
title: 'Instrukcje: formatowanie danych w kontrolce DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: 62701edfdb3cf2729cb401ad12a12ee4f524287b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941417"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="0acd4-102">Instrukcje: formatowanie danych w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0acd4-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0acd4-103">Poniższe procedury przedstawiają podstawowe formatowanie wartości komórki za pomocą <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwość <xref:System.Windows.Forms.DataGridView> kontroli i określonych kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="0acd4-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="0acd4-104">Informacje na temat zaawansowanych danych formatowania, zobacz [jak: Dostosowywanie formatowania danych w formancie DataGridView formularzy Windows](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="0acd4-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="0acd4-105">Formatowanie waluty i wartości daty</span><span class="sxs-lookup"><span data-stu-id="0acd4-105">To format currency and date values</span></span>  
  
- <span data-ttu-id="0acd4-106">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="0acd4-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="0acd4-107">Poniższy przykład kodu ustawia format dla określonych kolumn przy użyciu <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości kolumn.</span><span class="sxs-lookup"><span data-stu-id="0acd4-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="0acd4-108">Wartości w `UnitPrice` kolumna jest wyświetlana w bieżącym formacie waluty specyficzny dla kultury za pomocą wartości ujemnych, ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="0acd4-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="0acd4-109">Wartości w `ShipDate` kolumna jest wyświetlana w formacie bieżącej daty krótkiej dla kultury.</span><span class="sxs-lookup"><span data-stu-id="0acd4-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="0acd4-110">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> wartości, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="0acd4-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="0acd4-111">Aby dostosować wyświetlanie wartości null bazy danych</span><span class="sxs-lookup"><span data-stu-id="0acd4-111">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="0acd4-112">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="0acd4-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="0acd4-113">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwość, aby wyświetlić "puste" we wszystkich komórkach zawiera wartości równą <xref:System.DBNull.Value?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0acd4-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="0acd4-114">Aby włączyć wordwrap komórek na podstawie tekstu</span><span class="sxs-lookup"><span data-stu-id="0acd4-114">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="0acd4-115">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> do jednego z <xref:System.Windows.Forms.DataGridViewTriState> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0acd4-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="0acd4-116">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości, aby ustawić tryb zawijania dla całego formantu.</span><span class="sxs-lookup"><span data-stu-id="0acd4-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="0acd4-117">Aby określić wyrównanie tekstu w komórkach kontrolki DataGridView</span><span class="sxs-lookup"><span data-stu-id="0acd4-117">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="0acd4-118">Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> do jednego z <xref:System.Windows.Forms.DataGridViewContentAlignment> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0acd4-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="0acd4-119">Poniższy przykład kodu Ustawia wyrównanie dla określonej kolumny za pomocą <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości kolumny.</span><span class="sxs-lookup"><span data-stu-id="0acd4-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="0acd4-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="0acd4-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0acd4-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0acd4-121">Compiling the Code</span></span>  
 <span data-ttu-id="0acd4-122">Wymagaj tych przykładach:</span><span class="sxs-lookup"><span data-stu-id="0acd4-122">These examples require:</span></span>  
  
- <span data-ttu-id="0acd4-123">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawierającą kolumnę o nazwie `UnitPrice`, kolumna o nazwie `ShipDate`, a kolumna o nazwie `CustomerName`.</span><span class="sxs-lookup"><span data-stu-id="0acd4-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="0acd4-124">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="0acd4-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0acd4-125">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="0acd4-125">Robust Programming</span></span>  
 <span data-ttu-id="0acd4-126">W przypadku maksymalnej skalowalności powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki, które używają tego samego style, zamiast oddzielnie ustawienie ponownego obliczenia właściwości stylu dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="0acd4-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="0acd4-127">Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="0acd4-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0acd4-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0acd4-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="0acd4-129">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0acd4-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="0acd4-130">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0acd4-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="0acd4-131">Formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0acd4-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="0acd4-132">Instrukcje: Dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0acd4-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="0acd4-133">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="0acd4-133">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
