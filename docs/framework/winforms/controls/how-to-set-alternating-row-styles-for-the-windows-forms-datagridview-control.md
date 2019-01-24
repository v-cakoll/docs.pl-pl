---
title: 'Instrukcje: Ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: ba5aaec9e66f1d3c66bb50709f6fbd4afde893ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562729"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="9f3d9-102">Instrukcje: Ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f3d9-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9f3d9-103">Dane tabelaryczne często jest przesyłany do użytkowników w postaci księgi, gdzie przemienne wiersze mają różnych kolorów tła.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="9f3d9-104">Ten format ułatwia użytkownikom Poinformuj komórki, które są w każdym wierszu, szczególnie w przypadku szerokich tabel, które mają wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="9f3d9-105">Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolę, można określić dotycząca pełną styl naprzemiennych wierszach.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="9f3d9-106">Dzięki temu możesz użyć właściwości stylu, takich jak kolor pierwszego planu i czcionki, oprócz kolor tła do odróżnienia przemienne wiersze.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="9f3d9-107">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="9f3d9-108">Zobacz też [jak: Ustawianie przemiennych wierszy dla formantu DataGridView, które przy użyciu narzędzia Projektant formularzy Windows](https://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9f3d9-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="9f3d9-109">Aby ustawić programowo alternatywnych stylów wierszy</span><span class="sxs-lookup"><span data-stu-id="9f3d9-109">To set alternating row styles programmatically</span></span>  
  
-   <span data-ttu-id="9f3d9-110">Ustawianie właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów zwróconych przez <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  <span data-ttu-id="9f3d9-111">Style określony za pomocą <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości przesłaniają style określone na podstawie kolumny i <xref:System.Windows.Forms.DataGridView> poziomu, ale są zastępowane przez style ustawić na poziomie wierszy i komórek.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="9f3d9-112">Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9f3d9-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f3d9-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9f3d9-113">Compiling the Code</span></span>  
 <span data-ttu-id="9f3d9-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9f3d9-114">This example requires:</span></span>  
  
-   <span data-ttu-id="9f3d9-115">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="9f3d9-116">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9f3d9-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9f3d9-117">Robust Programming</span></span>  
 <span data-ttu-id="9f3d9-118">W przypadku maksymalnej skalowalności powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki, które używają tego samego style, zamiast oddzielnie ustawienie ponownego obliczenia właściwości stylu dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="9f3d9-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="9f3d9-119">Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9f3d9-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f3d9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f3d9-120">See also</span></span>
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="9f3d9-121">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f3d9-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9f3d9-122">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f3d9-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9f3d9-123">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f3d9-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9f3d9-124">Instrukcje: Ustawianie stylów czcionek i koloru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f3d9-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
