---
title: Dostosowywanie formantu DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: ab8d1f07c608aca4f14f5e73860f8c3e263a4610
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091385"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="9f86f-102">Dostosowywanie formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9f86f-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9f86f-103">`DataGridView` Kontrola zapewnia kilka właściwości, których można dostosować wygląd i zachowanie podstawowe (wygląd i działanie), jej komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="9f86f-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="9f86f-104">Jeśli masz specjalne potrzeby, które wykraczają poza możliwości <xref:System.Windows.Forms.DataGridViewCellStyle> klasy, można jednak również zaimplementować rysowanie formantu przez właściciela lub rozszerzyć jej możliwości, tworząc niestandardowe komórek, kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="9f86f-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="9f86f-105">Aby rysować komórek i wierszy, samodzielnie, może obsługiwać różnych `DataGridView` zdarzenia rysowania.</span><span class="sxs-lookup"><span data-stu-id="9f86f-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="9f86f-106">Aby zmodyfikować istniejące funkcje lub zapewniają nowe funkcje, można utworzyć własne typy pochodzące z istniejących `DataGridViewCell`, `DataGridViewColumn`, i `DataGridViewRow` typów.</span><span class="sxs-lookup"><span data-stu-id="9f86f-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="9f86f-107">Możesz także podać nowe możliwości edytowania przez tworzenie typów pochodnych, które wyświetlają kontroli wybrane gdy komórka jest w trybie edycji.</span><span class="sxs-lookup"><span data-stu-id="9f86f-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f86f-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9f86f-108">In This Section</span></span>  
 [<span data-ttu-id="9f86f-109">Instrukcje: Dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f86f-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="9f86f-110">W tym artykule opisano sposób obsługi <xref:System.Windows.Forms.DataGridView.CellPainting> zdarzeń w celu rysowania komórek ręcznie.</span><span class="sxs-lookup"><span data-stu-id="9f86f-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="9f86f-111">Instrukcje: Dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f86f-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="9f86f-112">W tym artykule opisano sposób obsługi <xref:System.Windows.Forms.DataGridView.RowPrePaint> i <xref:System.Windows.Forms.DataGridView.RowPostPaint> zdarzenia w celu rysowania wiersze z niestandardowych, gradientu tła i zawartością, która obejmuje wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="9f86f-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="9f86f-113">Instrukcje: Dostosowywanie komórek i kolumn w kontrolce DataGridView formularzy Windows Forms przez rozszerzanie ich zachowania i wyglądu</span><span class="sxs-lookup"><span data-stu-id="9f86f-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="9f86f-114">W tym artykule opisano sposób tworzenia niestandardowych typów pochodnych typu `DataGridViewCell` i `DataGridViewColumn` celu Wyróżnij komórki, gdy wskaźnik myszy znajduje się na nich.</span><span class="sxs-lookup"><span data-stu-id="9f86f-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="9f86f-115">Instrukcje: Wyłączanie przycisków w kolumnie przycisków w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f86f-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="9f86f-116">W tym artykule opisano sposób tworzenia niestandardowych typów pochodnych typu <xref:System.Windows.Forms.DataGridViewButtonCell> i <xref:System.Windows.Forms.DataGridViewButtonColumn> w celu wyświetlenia wyłączone przycisków w kolumnie przycisków.</span><span class="sxs-lookup"><span data-stu-id="9f86f-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="9f86f-117">Instrukcje: Kontrolki hosta w komórkach kontrolki DataGridView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="9f86f-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="9f86f-118">Opisuje sposób implementacji `IDataGridViewEditingControl` interfejs i tworzenie niestandardowych typów pochodnych typu `DataGridViewCell` i `DataGridViewColumn` w celu wyświetlenia <xref:System.Windows.Forms.DateTimePicker> kontroli, gdy komórka jest w trybie edycji.</span><span class="sxs-lookup"><span data-stu-id="9f86f-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9f86f-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="9f86f-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="9f86f-120">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9f86f-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="9f86f-121">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewCell> klasy.</span><span class="sxs-lookup"><span data-stu-id="9f86f-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="9f86f-122">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewRow> klasy.</span><span class="sxs-lookup"><span data-stu-id="9f86f-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="9f86f-123">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewColumn> klasy.</span><span class="sxs-lookup"><span data-stu-id="9f86f-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="9f86f-124">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9f86f-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9f86f-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9f86f-125">Related Sections</span></span>  
 [<span data-ttu-id="9f86f-126">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f86f-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9f86f-127">Zawiera tematy, które opisują sposób modyfikowania wyglądu podstawowego formantu i formatowania wyświetlania danych komórki.</span><span class="sxs-lookup"><span data-stu-id="9f86f-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f86f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f86f-128">See also</span></span>

- [<span data-ttu-id="9f86f-129">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9f86f-129">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="9f86f-130">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f86f-130">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
