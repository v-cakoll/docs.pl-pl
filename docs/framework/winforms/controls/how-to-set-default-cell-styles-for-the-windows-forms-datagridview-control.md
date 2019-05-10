---
title: 'Instrukcje: ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: de939051b613a0622f60178a566fd19dbca53694
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638167"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="c5fa2-102">Instrukcje: ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c5fa2-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c5fa2-103">Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolę, można określić domyślnych stylów komórki dla całego kontroli i określonych kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="c5fa2-104">Te ustawienia domyślne odfiltrować z poziomu kontroli na poziomie kolumny, a następnie na poziomie wiersza, a następnie na poziomie komórki.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="c5fa2-105">Jeśli konkretny <xref:System.Windows.Forms.DataGridViewCellStyle> właściwość nie jest ustawiona na poziomie komórki, używane jest domyślne ustawienie właściwości na poziomie wiersza.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="c5fa2-106">Jeśli właściwość nie jest również ustawiona na poziomie wiersza, używane jest domyślne ustawienie kolumny.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="c5fa2-107">Na koniec Jeśli właściwość również nie jest ustawiony na poziomie kolumny, a wartość domyślna <xref:System.Windows.Forms.DataGridView> ustawienie jest używane.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="c5fa2-108">To ustawienie można uniknąć konieczności duplikowania ustawienia właściwości na różnych poziomach.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="c5fa2-109">Na każdym poziomie wystarczy określić style, które różnią się od poziomami wyższymi.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="c5fa2-110">Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy Windows](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="c5fa2-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="c5fa2-111">Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="c5fa2-112">Zobacz też [jak: Ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView, które przy użyciu narzędzia Projektant formularzy Windows](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="c5fa2-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="c5fa2-113">Aby ustawić wartości domyślne style komórki programowe</span><span class="sxs-lookup"><span data-stu-id="c5fa2-113">To set the default cell styles programmatically</span></span>  
  
1. <span data-ttu-id="c5fa2-114">Ustawianie właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> pobierane w drodze <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. <span data-ttu-id="c5fa2-115">Utwórz i zainicjuj nowe <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty do użycia przez wiele wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. <span data-ttu-id="c5fa2-116">Ustaw `DefaultCellStyle` właściwości określonych wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="c5fa2-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5fa2-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c5fa2-118">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c5fa2-118">Compiling the Code</span></span>  
 <span data-ttu-id="c5fa2-119">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c5fa2-119">This example requires:</span></span>  
  
- <span data-ttu-id="c5fa2-120">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="c5fa2-121">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c5fa2-122">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="c5fa2-122">Robust Programming</span></span>  
 <span data-ttu-id="c5fa2-123">Aby osiągnąć maksymalną skalowalność podczas pracy z bardzo dużych zestawów danych, powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki, które za pomocą tego samego stylów, zamiast ponownego obliczenia właściwości stylu dla poszczególnych elementów osobno.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="c5fa2-124">Ponadto należy utworzyć udostępnione wiersze i uzyskiwać do nich dostęp za pomocą <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5fa2-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c5fa2-125">Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="c5fa2-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fa2-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5fa2-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c5fa2-127">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5fa2-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="c5fa2-128">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5fa2-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="c5fa2-129">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5fa2-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="c5fa2-130">Instrukcje: Ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5fa2-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
