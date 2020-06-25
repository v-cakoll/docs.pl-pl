---
title: DataGridView — Formant
description: Dowiedz się, w jaki sposób używać `DataGridView` kontrolki do wyświetlania widoków niewielkiej ilości danych w trybie tylko do odczytu, czy skalować ją w celu wyświetlenia edytowalnych widoków bardzo dużych zestawów danych.
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
ms.openlocfilehash: f9a45e8be7975697ca5c0d019c6bc4119f562aea
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325894"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="3b3ee-103">DataGridView — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="3b3ee-103">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="3b3ee-104">`DataGridView`Formant zapewnia zaawansowany i elastyczny sposób wyświetlania danych w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-104">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="3b3ee-105">Można użyć `DataGridView` kontrolki do wyświetlania widoków z niewielką ilością danych tylko do odczytu lub można skalować ją w celu wyświetlenia edytowalnych widoków bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-105">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="3b3ee-106">Formant można rozbudować `DataGridView` na kilka sposobów, aby tworzyć niestandardowe zachowania w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-106">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="3b3ee-107">Można na przykład programowo określić własne algorytmy sortowania i można utworzyć własne typy komórek.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-107">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="3b3ee-108">Wygląd formantu można łatwo dostosować, `DataGridView` wybierając spośród kilku właściwości.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-108">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="3b3ee-109">Wiele typów magazynów danych może służyć jako źródło danych lub `DataGridView` kontrolka może działać bez powiązanego ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-109">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="3b3ee-110">W tematach w tej sekcji opisano koncepcje i techniki, których można użyć do tworzenia `DataGridView` funkcji w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-110">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b3ee-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3b3ee-111">In This Section</span></span>  
 [<span data-ttu-id="3b3ee-112">DataGridView — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="3b3ee-112">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="3b3ee-113">Zawiera tematy opisujące architekturę i podstawowe pojęcia związane z `DataGridView` formantem Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-113">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="3b3ee-114">Funkcje domyślne w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3b3ee-114">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-115">Opisuje domyślny wygląd i zachowanie kontrolki Windows Forms, `DataGridView` gdy jest ona powiązana ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-115">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="3b3ee-116">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3b3ee-116">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-117">Opisuje typy kolumn w `DataGridView` kontrolce Windows Forms używane do wyświetlania danych i Zezwalanie użytkownikom na modyfikowanie i Dodawanie danych.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-117">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="3b3ee-118">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="3b3ee-119">Zawiera tematy opisujące często używane właściwości komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-119">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="3b3ee-120">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-121">Zawiera tematy opisujące sposób modyfikowania podstawowego wyglądu kontrolki i formatowania wyświetlania danych komórek.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-121">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="3b3ee-122">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-122">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-123">Zawiera tematy opisujące sposób wypełniania kontrolki danymi ręcznie lub z zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-123">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="3b3ee-124">Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-124">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-125">Zawiera tematy opisujące sposób automatycznego dopasowywania rozmiaru wierszy i kolumn w celu dopasowania do zawartości komórki lub dopasowania do dostępnej szerokości formantu.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-125">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="3b3ee-126">Sortowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-126">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-127">Zawiera tematy opisujące funkcje sortowania w formancie.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-127">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="3b3ee-128">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-128">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-129">Zawiera tematy opisujące sposób zmiany sposobu, w jaki użytkownicy mogą dodawać i modyfikować dane w formancie.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-129">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="3b3ee-130">Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-130">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-131">Zawiera tematy opisujące funkcje wyboru komórek, wierszy i kolumn w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-131">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="3b3ee-132">Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-132">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="3b3ee-133">Zawiera tematy opisujące sposób programowania z obiektami komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-133">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="3b3ee-134">Dostosowywanie formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3b3ee-134">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-135">Zawiera tematy, które opisują niestandardowe `DataGridView` komórki i wiersze rysowania, a także tworzą pochodne komórki, kolumny i typy wierszy.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-135">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="3b3ee-136">Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-136">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-137">Zawiera tematy opisujące sposób efektywnego używania kontrolki w celu uniknięcia problemów z wydajnością podczas pracy z dużymi ilościami danych.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-137">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="3b3ee-138">Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-138">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3b3ee-139">Opisuje sposób, w jaki użytkownicy mogą korzystać z `DataGridView` kontrolki za pomocą klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-139">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="3b3ee-140">Różnice między kontrolkami DataGridView i DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ee-140">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="3b3ee-141">Opisuje, w jaki sposób `DataGridView` formant jest ulepszony i zastępuje <xref:System.Windows.Forms.DataGrid> formant.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-141">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="3b3ee-142">Zobacz również [Korzystanie z projektanta z Windows Forms formant DataGridView](using-the-designer-with-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="3b3ee-142">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3b3ee-143">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="3b3ee-143">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="3b3ee-144">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-144">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="3b3ee-145">Zawiera dokumentację referencyjną <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-145">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="3b3ee-146"><xref:System.Windows.Forms.DataGridView>Formant i <xref:System.Windows.Forms.BindingSource> składnik są zaprojektowane tak, aby ściśle współpracować.</span><span class="sxs-lookup"><span data-stu-id="3b3ee-146">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b3ee-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b3ee-147">See also</span></span>

- [<span data-ttu-id="3b3ee-148">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3b3ee-148">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
