---
title: Podstawowe formatowanie i style w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d295718b7bd4f3bc4c5f63b6e6cb911f733525fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731999"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="96ac4-102">Podstawowe formatowanie i style w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="96ac4-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="96ac4-103">Formant `DataGridView` ułatwia Definiowanie podstawowego wyglądu komórek i formatowanie wyświetlania wartości komórek.</span><span class="sxs-lookup"><span data-stu-id="96ac4-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="96ac4-104">Można definiować wygląd i style formatowania dla poszczególnych komórek, dla komórek w określonych kolumnach i wierszach lub dla wszystkich komórek w kontrolce przez ustawienie właściwości obiektów `DataGridViewCellStyle`, do których dostęp odbywa się za pomocą różnych właściwości kontrolki `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="96ac4-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="96ac4-105">Ponadto można modyfikować te style dynamicznie na podstawie takich czynników, jak wartość komórki przez obsługę zdarzenia `CellFormatting`.</span><span class="sxs-lookup"><span data-stu-id="96ac4-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96ac4-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="96ac4-106">In This Section</span></span>  
 [<span data-ttu-id="96ac4-107">Instrukcje: zmienianie stylów obramowania i linii siatki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96ac4-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="96ac4-108">Opisuje sposób ustawiania właściwości `DataGridView`, które definiują wygląd obramowania kontrolki i linie granicy między komórkami.</span><span class="sxs-lookup"><span data-stu-id="96ac4-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="96ac4-109">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96ac4-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96ac4-110">Opisuje klasę `DataGridViewCellStyle` i sposób, w jaki właściwości tego typu są używane do definiowania sposobu wyświetlania komórek w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="96ac4-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="96ac4-111">Instrukcje: ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96ac4-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96ac4-112">Opisuje sposób użycia właściwości `DataGridViewCellStyle` do definiowania domyślnego wyglądu komórek w określonych wierszach i kolumnach oraz w całej kontrolce.</span><span class="sxs-lookup"><span data-stu-id="96ac4-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="96ac4-113">Instrukcje: formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96ac4-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96ac4-114">Opisuje sposób formatowania wartości wyświetlania komórki przy użyciu właściwości `DataGridViewCellStyle`.</span><span class="sxs-lookup"><span data-stu-id="96ac4-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="96ac4-115">Instrukcje: ustawianie stylów czcionek i koloru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96ac4-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96ac4-116">Opisuje sposób użycia właściwości `DefaultCellStyle` do ustawiania podstawowych właściwości wyświetlania dla wszystkich komórek w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="96ac4-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="96ac4-117">Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96ac4-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96ac4-118">Opisuje sposób tworzenia efektu przypominającego finanse w formancie przy użyciu przemiennych wierszy, które są wyświetlane inaczej.</span><span class="sxs-lookup"><span data-stu-id="96ac4-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="96ac4-119">Instrukcje: użycie szablonu wiersza do dostosowania wierszy w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96ac4-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="96ac4-120">Opisuje sposób użycia właściwości `RowTemplate` do ustawiania właściwości wiersza, które będą używane dla wszystkich wierszy w formancie.</span><span class="sxs-lookup"><span data-stu-id="96ac4-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="96ac4-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="96ac4-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="96ac4-122">Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="96ac4-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="96ac4-123">Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="96ac4-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="96ac4-124">Zawiera dokumentację referencyjną dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting>.</span><span class="sxs-lookup"><span data-stu-id="96ac4-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="96ac4-125">Zawiera dokumentację referencyjną dla właściwości <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="96ac4-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="96ac4-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="96ac4-126">Related Sections</span></span>  
 [<span data-ttu-id="96ac4-127">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96ac4-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96ac4-128">Zawiera tematy opisujące niestandardowe malowanie <xref:System.Windows.Forms.DataGridView> komórek i wierszy oraz tworzenie pochodnej komórki, kolumny i typów wierszy.</span><span class="sxs-lookup"><span data-stu-id="96ac4-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="96ac4-129">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96ac4-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="96ac4-130">Zawiera tematy opisujące często używane właściwości komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="96ac4-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ac4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96ac4-131">See also</span></span>

- [<span data-ttu-id="96ac4-132">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="96ac4-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
