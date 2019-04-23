---
title: Podstawowe formatowanie i style w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: 5e967c1bbe54095cc11e48b014600158da7fe6a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189900"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3e04e-102">Podstawowe formatowanie i style w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3e04e-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3e04e-103">`DataGridView` Kontroli można łatwo zdefiniować podstawowego wyglądu komórek i formatowania wyświetlania wartości komórek.</span><span class="sxs-lookup"><span data-stu-id="3e04e-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="3e04e-104">Można zdefiniować wygląd i formatowanie style pojedyncze komórki, komórki w określonych kolumn i wierszy lub wszystkie komórki w formancie przez ustawienie właściwości `DataGridViewCellStyle` obiekty dostępne za pośrednictwem różnych `DataGridView` właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="3e04e-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="3e04e-105">Ponadto można modyfikować te style dynamicznie na podstawie czynników, takich jak wartość komórki obsługi `CellFormatting` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3e04e-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e04e-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3e04e-106">In This Section</span></span>  
 [<span data-ttu-id="3e04e-107">Instrukcje: Zmiana obramowania i style linii siatki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e04e-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="3e04e-108">W tym artykule opisano sposób ustawiania `DataGridView` właściwości, które definiują wygląd obramowania formantu oraz linie granic między komórkami.</span><span class="sxs-lookup"><span data-stu-id="3e04e-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="3e04e-109">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e04e-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3e04e-110">W tym artykule opisano `DataGridViewCellStyle` klasy i interakcje właściwości tego typu, aby zdefiniować sposób wyświetlania komórek w formancie.</span><span class="sxs-lookup"><span data-stu-id="3e04e-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="3e04e-111">Instrukcje: Ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e04e-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3e04e-112">Opisuje sposób używania `DataGridViewCellStyle` właściwości, aby zdefiniować domyślny wygląd komórki w określonych wierszy i kolumn i w całej kontrolce.</span><span class="sxs-lookup"><span data-stu-id="3e04e-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="3e04e-113">Instrukcje: Formatowanie danych w Windows formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="3e04e-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3e04e-114">W tym artykule opisano sposób formatowania wartości wyświetlane komórki za pomocą `DataGridViewCellStyle` właściwości.</span><span class="sxs-lookup"><span data-stu-id="3e04e-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="3e04e-115">Instrukcje: Ustawianie stylów czcionek i koloru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e04e-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3e04e-116">Opisuje sposób używania `DefaultCellStyle` właściwości do ustawienia podstawowe wyświetlić właściwości dla wszystkich komórek w formancie.</span><span class="sxs-lookup"><span data-stu-id="3e04e-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="3e04e-117">Instrukcje: Ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e04e-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3e04e-118">Opisuje sposób tworzenia efekt jak rejestr w kontroli przy użyciu przemienne wiersze, które są wyświetlane inaczej.</span><span class="sxs-lookup"><span data-stu-id="3e04e-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="3e04e-119">Instrukcje: Użycie szablonu wiersza do dostosowania wierszy w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e04e-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="3e04e-120">Opisuje sposób używania `RowTemplate` właściwości do ustawienia właściwości wiersza, które będą używane dla wszystkich wierszy w formancie.</span><span class="sxs-lookup"><span data-stu-id="3e04e-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3e04e-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="3e04e-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="3e04e-122">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3e04e-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="3e04e-123">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewCellStyle> klasy.</span><span class="sxs-lookup"><span data-stu-id="3e04e-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="3e04e-124">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3e04e-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="3e04e-125">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3e04e-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3e04e-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3e04e-126">Related Sections</span></span>  
 [<span data-ttu-id="3e04e-127">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e04e-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3e04e-128">Zawiera tematy, które opisują niestandardowego rysowania <xref:System.Windows.Forms.DataGridView> komórek i wierszy oraz tworzenie pochodnych komórki, kolumny i typy wierszy.</span><span class="sxs-lookup"><span data-stu-id="3e04e-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="3e04e-129">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e04e-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="3e04e-130">Zawiera tematy, które opisują często używanych właściwości komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="3e04e-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e04e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e04e-131">See also</span></span>

- [<span data-ttu-id="3e04e-132">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="3e04e-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
