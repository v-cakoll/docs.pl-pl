---
title: Ustaw domyślne style komórek dla kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 6b2d7de671e48ae8f55987c262e15717138b3fb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744868"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="43b57-102">Porady: ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="43b57-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="43b57-103">Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można określić domyślne style komórek dla całej kontrolki i dla konkretnych kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="43b57-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="43b57-104">Te wartości domyślne są filtrowane z poziomu formantu do poziomu kolumny, a następnie do poziomu wiersza, a następnie do poziomu komórki.</span><span class="sxs-lookup"><span data-stu-id="43b57-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="43b57-105">Jeśli określona właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> nie jest ustawiona na poziomie komórki, zostanie użyta wartość domyślna ustawienia właściwości na poziomie wiersza.</span><span class="sxs-lookup"><span data-stu-id="43b57-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="43b57-106">Jeśli właściwość nie jest również ustawiona na poziomie wiersza, używane jest ustawienie domyślne kolumny.</span><span class="sxs-lookup"><span data-stu-id="43b57-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="43b57-107">Na koniec, jeśli właściwość nie jest również ustawiona na poziomie kolumny, używane jest domyślne ustawienie <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="43b57-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="43b57-108">Przy użyciu tego ustawienia można uniknąć duplikowania ustawień właściwości na wielu poziomach.</span><span class="sxs-lookup"><span data-stu-id="43b57-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="43b57-109">Na każdym poziomie wystarczy określić style, które różnią się od poziomów powyżej.</span><span class="sxs-lookup"><span data-stu-id="43b57-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="43b57-110">Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="43b57-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="43b57-111">W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.</span><span class="sxs-lookup"><span data-stu-id="43b57-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="43b57-112">Zobacz również [instrukcje: Ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView Windows Forms przy użyciu narzędzia Projektant](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="43b57-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="43b57-113">Aby programowo ustawić domyślne style komórek</span><span class="sxs-lookup"><span data-stu-id="43b57-113">To set the default cell styles programmatically</span></span>  
  
1. <span data-ttu-id="43b57-114">Ustaw właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> pobierane za pomocą właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="43b57-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. <span data-ttu-id="43b57-115">Utwórz i zainicjuj nowe obiekty <xref:System.Windows.Forms.DataGridViewCellStyle> do użycia przez wiele wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="43b57-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. <span data-ttu-id="43b57-116">Ustaw właściwość `DefaultCellStyle` określonych wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="43b57-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="43b57-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="43b57-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43b57-118">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="43b57-118">Compiling the Code</span></span>  
 <span data-ttu-id="43b57-119">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="43b57-119">This example requires:</span></span>  
  
- <span data-ttu-id="43b57-120">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="43b57-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="43b57-121">Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="43b57-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="43b57-122">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="43b57-122">Robust Programming</span></span>  
 <span data-ttu-id="43b57-123">Aby osiągnąć maksymalną skalowalność podczas pracy z bardzo dużymi zestawami danych, należy udostępnić <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów, zamiast ustawiać właściwości stylu poszczególnych elementów osobno.</span><span class="sxs-lookup"><span data-stu-id="43b57-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="43b57-124">Ponadto należy utworzyć wiersze udostępnione i uzyskać do nich dostęp przy użyciu właściwości <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="43b57-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="43b57-125">Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="43b57-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b57-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43b57-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [<span data-ttu-id="43b57-127">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43b57-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="43b57-128">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43b57-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="43b57-129">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43b57-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="43b57-130">Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43b57-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
