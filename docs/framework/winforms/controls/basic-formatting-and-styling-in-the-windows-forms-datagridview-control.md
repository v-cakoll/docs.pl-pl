---
title: Podstawowe formatowanie i style w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d38620c321fb12b9f489fd086e222b7780337ab3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="da244-102">Podstawowe formatowanie i style w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="da244-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="da244-103">`DataGridView` Formantu można łatwo zdefiniować podstawowe wygląd komórek i format wyświetlania wartości komórki.</span><span class="sxs-lookup"><span data-stu-id="da244-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="da244-104">Można zdefiniować wygląd i formatowanie style pojedynczych komórek, komórki w określonych kolumn i wierszy lub wszystkie komórki w formancie przez ustawienie właściwości `DataGridViewCellStyle` obiekty dostępne za pośrednictwem różnych `DataGridView` właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="da244-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="da244-105">Ponadto można zmodyfikować te style dynamicznie na podstawie czynników, takich jak wartość komórki Obsługa `CellFormatting` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="da244-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da244-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="da244-106">In This Section</span></span>  
 [<span data-ttu-id="da244-107">Instrukcje: zmienianie stylów obramowania i linii siatki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da244-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="da244-108">Opisuje sposób ustawiania `DataGridView` właściwości, które definiują wygląd obramowania formantu i linie granicę między komórkami.</span><span class="sxs-lookup"><span data-stu-id="da244-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="da244-109">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da244-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da244-110">W tym artykule opisano `DataGridViewCellStyle` klasy i interakcje właściwości tego typu, aby zdefiniować sposób wyświetlania komórki w formancie.</span><span class="sxs-lookup"><span data-stu-id="da244-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="da244-111">Instrukcje: ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da244-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da244-112">Informacje dotyczące używania `DataGridViewCellStyle` właściwości, aby zdefiniować domyślny wygląd komórek w określonych wierszy i kolumn i całego formantu.</span><span class="sxs-lookup"><span data-stu-id="da244-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="da244-113">Instrukcje: formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da244-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da244-114">Opisuje sposób formatowania wartości wyświetlane komórki za pomocą `DataGridViewCellStyle` właściwości.</span><span class="sxs-lookup"><span data-stu-id="da244-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="da244-115">Instrukcje: ustawianie stylów czcionek i koloru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da244-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da244-116">Informacje dotyczące używania `DefaultCellStyle` właściwości do ustawienia podstawowe wyświetlić właściwości dla wszystkich komórek w formancie.</span><span class="sxs-lookup"><span data-stu-id="da244-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="da244-117">Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da244-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da244-118">Opisuje sposób tworzenia efekt przypominającej księgi w formancie przy użyciu przemiennych wierszy, które są wyświetlane inaczej.</span><span class="sxs-lookup"><span data-stu-id="da244-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="da244-119">Instrukcje: użycie szablonu wiersza do dostosowania wierszy w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da244-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="da244-120">Informacje dotyczące używania `RowTemplate` właściwości można ustawić właściwości wierszy, które będą używane dla wszystkich wierszy w formancie.</span><span class="sxs-lookup"><span data-stu-id="da244-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="da244-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="da244-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="da244-122">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="da244-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="da244-123">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridViewCellStyle> klasy.</span><span class="sxs-lookup"><span data-stu-id="da244-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="da244-124">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="da244-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="da244-125">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="da244-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="da244-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="da244-126">Related Sections</span></span>  
 [<span data-ttu-id="da244-127">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da244-127">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da244-128">Udostępnia tematów opisujących rysowania niestandardowych <xref:System.Windows.Forms.DataGridView> komórek i wierszy oraz tworzenie pochodnych komórki, kolumny i typy wierszy.</span><span class="sxs-lookup"><span data-stu-id="da244-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="da244-129">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da244-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="da244-130">Zapewnia możliwość tematach opisano często używane właściwości komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="da244-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da244-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da244-131">See Also</span></span>  
 [<span data-ttu-id="da244-132">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="da244-132">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
