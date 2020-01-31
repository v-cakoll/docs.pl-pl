---
title: Dostosuj formant DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744023"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="c5a8d-102">Dostosowywanie formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c5a8d-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c5a8d-103">Kontrolka `DataGridView` zawiera kilka właściwości, których można użyć do dostosowania wyglądu i podstawowego zachowania (wyglądu i działania) jego komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="c5a8d-104">W przypadku specjalnych potrzeb, które wykraczają poza możliwości klasy <xref:System.Windows.Forms.DataGridViewCellStyle>, można również zaimplementować rysowanie właściciela dla kontrolki lub zwiększyć jej możliwości przez utworzenie niestandardowych komórek, kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="c5a8d-105">Aby samodzielnie malować komórki i wiersze, możesz obsłużyć różne `DataGridView`ych zdarzeń rysowania.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="c5a8d-106">Aby zmodyfikować istniejące funkcje lub udostępnić nowe funkcje, można utworzyć własne typy pochodne na podstawie istniejących typów `DataGridViewCell`, `DataGridViewColumn`i `DataGridViewRow`.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="c5a8d-107">Możesz również udostępnić nowe możliwości edytowania, tworząc typy pochodne, które wyświetlają formant wyboru, gdy komórka jest w trybie edycji.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5a8d-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c5a8d-108">In This Section</span></span>  
 [<span data-ttu-id="c5a8d-109">Instrukcje: dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5a8d-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="c5a8d-110">Opisuje sposób obsługi zdarzenia <xref:System.Windows.Forms.DataGridView.CellPainting> w celu ręcznego malowania komórek.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="c5a8d-111">Instrukcje: dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5a8d-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="c5a8d-112">Opisuje sposób obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.RowPrePaint> i <xref:System.Windows.Forms.DataGridView.RowPostPaint> w celu malowania wierszy z niestandardowym tłem gradientu i zawartością obejmującą wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="c5a8d-113">Instrukcje: dostosowywanie komórek i kolumn w kontrolce DataGridView formularzy Windows Forms przez rozszerzanie ich zachowania i wyglądu</span><span class="sxs-lookup"><span data-stu-id="c5a8d-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="c5a8d-114">Opisuje sposób tworzenia typów niestandardowych pochodnych dla `DataGridViewCell` i `DataGridViewColumn` w celu wyróżnienia komórek, gdy wskaźnik myszy zatrzyma się na nich.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="c5a8d-115">Instrukcje: wyłączanie przycisków w kolumnie przycisków w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5a8d-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="c5a8d-116">Opisuje sposób tworzenia typów niestandardowych pochodnych dla <xref:System.Windows.Forms.DataGridViewButtonCell> i <xref:System.Windows.Forms.DataGridViewButtonColumn> w celu wyświetlenia wyłączonych przycisków w kolumnie przycisków.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="c5a8d-117">Instrukcje: kontrolki hosta w komórkach kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5a8d-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="c5a8d-118">Opisuje, jak zaimplementować interfejs `IDataGridViewEditingControl` i utworzyć niestandardowe typy pochodne od `DataGridViewCell` i `DataGridViewColumn` w celu wyświetlenia kontrolki <xref:System.Windows.Forms.DateTimePicker>, gdy komórka jest w trybie edycji.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c5a8d-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c5a8d-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c5a8d-120">Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="c5a8d-121">Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="c5a8d-122">Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="c5a8d-123">Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="c5a8d-124">Zawiera dokumentację referencyjną dla interfejsu <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c5a8d-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c5a8d-125">Related Sections</span></span>  
 [<span data-ttu-id="c5a8d-126">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5a8d-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c5a8d-127">Zawiera tematy opisujące sposób modyfikowania podstawowego wyglądu kontrolki i formatowania wyświetlania danych komórek.</span><span class="sxs-lookup"><span data-stu-id="c5a8d-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a8d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5a8d-128">See also</span></span>

- [<span data-ttu-id="c5a8d-129">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c5a8d-129">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="c5a8d-130">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5a8d-130">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
