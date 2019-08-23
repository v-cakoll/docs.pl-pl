---
title: 'Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: d113c45469f6a78c94b9489bd82f9e55b5b96bba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962277"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="f637a-102">Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f637a-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f637a-103">Dane tabelaryczne są często prezentowane użytkownikom w formacie podobnym do finansów, gdzie przemienne wiersze mają różne kolory tła.</span><span class="sxs-lookup"><span data-stu-id="f637a-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="f637a-104">Ten format ułatwia użytkownikom informowanie, które komórki znajdują się w każdym wierszu, szczególnie w przypadku szerokich tabel z wieloma kolumnami.</span><span class="sxs-lookup"><span data-stu-id="f637a-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="f637a-105">Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki można określić pełne informacje o stylu dla przemiennych wierszy.</span><span class="sxs-lookup"><span data-stu-id="f637a-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="f637a-106">Dzięki temu można używać cech stylu, takich jak kolor i czcionka pierwszego planu, oprócz koloru tła w celu odróżnienia przemiennych wierszy.</span><span class="sxs-lookup"><span data-stu-id="f637a-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="f637a-107">To zadanie jest obsługiwane w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f637a-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="f637a-108">Zapoznaj [się również z tematem: Ustaw style przemiennych wierszy dla kontrolki DataGridView Windows Forms przy użyciu](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="f637a-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="f637a-109">Aby programowo ustawić style przemiennych wierszy</span><span class="sxs-lookup"><span data-stu-id="f637a-109">To set alternating row styles programmatically</span></span>  
  
- <span data-ttu-id="f637a-110">Ustaw właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów zwracanych <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> przez i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f637a-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > <span data-ttu-id="f637a-111">Style określone za pomocą <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości zastępują style określone w kolumnie i <xref:System.Windows.Forms.DataGridView> na poziomie, ale są przesłonięte przez style ustawione na poziomie poszczególnych wierszy i komórek.</span><span class="sxs-lookup"><span data-stu-id="f637a-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="f637a-112">Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f637a-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f637a-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f637a-113">Compiling the Code</span></span>  
 <span data-ttu-id="f637a-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f637a-114">This example requires:</span></span>  
  
- <span data-ttu-id="f637a-115">Kontrolka o `dataGridView1`nazwie. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="f637a-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="f637a-116">Odwołania do <xref:System?displayProperty=nameWithType>zestawów, <xref:System.Drawing?displayProperty=nameWithType>i. <xref:System.Windows.Forms?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f637a-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f637a-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="f637a-117">Robust Programming</span></span>  
 <span data-ttu-id="f637a-118">Aby uzyskać maksymalną skalowalność, należy <xref:System.Windows.Forms.DataGridViewCellStyle> udostępnić obiekty w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów, zamiast ustawiania właściwości stylu dla każdego elementu osobno.</span><span class="sxs-lookup"><span data-stu-id="f637a-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="f637a-119">Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f637a-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f637a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f637a-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="f637a-121">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f637a-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f637a-122">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f637a-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f637a-123">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f637a-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f637a-124">Instrukcje: Ustawianie stylów czcionek i kolorów w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f637a-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
