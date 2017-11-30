---
title: "Porady: ustawianie alternatywnych stylów wierszy dla formantu DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a31e8eb02949c0f6db487e3cd1a6976f2ed37222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="60c0c-102">Porady: ustawianie alternatywnych stylów wierszy dla formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="60c0c-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="60c0c-103">Dane tabelaryczne często jest przesyłany do użytkowników w postaci księgi, której przemiennych wierszy mają różnych kolorów tła.</span><span class="sxs-lookup"><span data-stu-id="60c0c-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="60c0c-104">Ten format ułatwia użytkownikom Poinformuj komórek, które są w każdym wierszu, szczególnie w przypadku szerokie tabele, które mają wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="60c0c-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="60c0c-105">Z <xref:System.Windows.Forms.DataGridView> sterowania, można określić informacji o pełną stylu dla wierszy zmiennych.</span><span class="sxs-lookup"><span data-stu-id="60c0c-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="60c0c-106">Kolor pierwszego planu i czcionki, oprócz kolor tła przemiennych wierszy rozróżnianie, takich jak ta umożliwia, użyj właściwości stylu.</span><span class="sxs-lookup"><span data-stu-id="60c0c-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="60c0c-107">Brak obsługi dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="60c0c-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="60c0c-108">Zobacz też [porady: Ustawianie zmiennych style wierszy dla systemu Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="60c0c-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="60c0c-109">Aby ustawić programowo przemiennych wierszy</span><span class="sxs-lookup"><span data-stu-id="60c0c-109">To set alternating row styles programmatically</span></span>  
  
-   <span data-ttu-id="60c0c-110">Ustawianie właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty zwrócone przez <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="60c0c-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  <span data-ttu-id="60c0c-111">Style określona za pomocą <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości zastąpienia style określony w kolumnie i <xref:System.Windows.Forms.DataGridView> poziomie, ale są zastępowane przez style ustawiony na poziomie wierszy i komórek.</span><span class="sxs-lookup"><span data-stu-id="60c0c-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="60c0c-112">Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="60c0c-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="60c0c-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="60c0c-113">Compiling the Code</span></span>  
 <span data-ttu-id="60c0c-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="60c0c-114">This example requires:</span></span>  
  
-   <span data-ttu-id="60c0c-115">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="60c0c-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="60c0c-116">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="60c0c-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="60c0c-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="60c0c-117">Robust Programming</span></span>  
 <span data-ttu-id="60c0c-118">Skalowalność maksymalna powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki, które używają tego samego style, zamiast oddzielnie ustawienie właściwości stylu dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="60c0c-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="60c0c-119">Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="60c0c-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c0c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60c0c-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="60c0c-121">Podstawowe formatowanie i style w oknach formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="60c0c-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="60c0c-122">Style komórki w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="60c0c-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="60c0c-123">Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="60c0c-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="60c0c-124">Porady: Ustawianie stylów czcionek i koloru w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="60c0c-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
