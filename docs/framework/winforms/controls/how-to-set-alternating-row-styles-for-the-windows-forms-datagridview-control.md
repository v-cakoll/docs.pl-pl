---
title: Ustaw style wierszy przemiennych dla kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: b87ad50ef7e5118a95998949bc62299955856b27
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747138"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="3d74b-102">Porady: ustawianie alternatywnych stylów wierszy dla formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3d74b-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3d74b-103">Dane tabelaryczne są często prezentowane użytkownikom w formacie podobnym do finansów, gdzie przemienne wiersze mają różne kolory tła.</span><span class="sxs-lookup"><span data-stu-id="3d74b-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="3d74b-104">Ten format ułatwia użytkownikom informowanie, które komórki znajdują się w każdym wierszu, szczególnie w przypadku szerokich tabel z wieloma kolumnami.</span><span class="sxs-lookup"><span data-stu-id="3d74b-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="3d74b-105">Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można określić pełne informacje o stylu dla przemiennych wierszy.</span><span class="sxs-lookup"><span data-stu-id="3d74b-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="3d74b-106">Dzięki temu można używać cech stylu, takich jak kolor i czcionka pierwszego planu, oprócz koloru tła w celu odróżnienia przemiennych wierszy.</span><span class="sxs-lookup"><span data-stu-id="3d74b-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="3d74b-107">To zadanie jest obsługiwane w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d74b-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="3d74b-108">Zobacz również [instrukcje: Ustawianie przemiennych stylów wierszy dla kontrolki DataGridView Windows Forms przy użyciu narzędzia Projektant](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="3d74b-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="3d74b-109">Aby programowo ustawić style przemiennych wierszy</span><span class="sxs-lookup"><span data-stu-id="3d74b-109">To set alternating row styles programmatically</span></span>  
  
- <span data-ttu-id="3d74b-110">Ustaw właściwości obiektów <xref:System.Windows.Forms.DataGridViewCellStyle> zwracanych przez właściwości <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="3d74b-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > <span data-ttu-id="3d74b-111">Style określone za pomocą właściwości <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> przesłaniają style określone na poziomie kolumny i <xref:System.Windows.Forms.DataGridView>, ale są przesłonięte przez style ustawione na poziomie poszczególnych wierszy i komórek.</span><span class="sxs-lookup"><span data-stu-id="3d74b-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="3d74b-112">Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="3d74b-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3d74b-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3d74b-113">Compiling the Code</span></span>  
 <span data-ttu-id="3d74b-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="3d74b-114">This example requires:</span></span>  
  
- <span data-ttu-id="3d74b-115">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="3d74b-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="3d74b-116">Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d74b-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3d74b-117">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="3d74b-117">Robust Programming</span></span>  
 <span data-ttu-id="3d74b-118">Aby uzyskać maksymalną skalowalność, należy udostępnić <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów, zamiast ustawiania właściwości stylu dla każdego elementu osobno.</span><span class="sxs-lookup"><span data-stu-id="3d74b-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="3d74b-119">Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="3d74b-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d74b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d74b-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="3d74b-121">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d74b-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3d74b-122">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d74b-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3d74b-123">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d74b-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3d74b-124">Instrukcje: ustawianie stylów czcionek i koloru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d74b-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
