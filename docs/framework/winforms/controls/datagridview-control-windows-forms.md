---
title: DataGridView — Formant
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
ms.openlocfilehash: fc40c0f08c0c11fa9acc94ce12caab8766658f1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746950"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="67108-102">DataGridView — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="67108-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="67108-103">Formant `DataGridView` zapewnia zaawansowany i elastyczny sposób wyświetlania danych w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="67108-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="67108-104">Za pomocą kontrolki `DataGridView` można wyświetlić widoki z niewielką ilością danych tylko do odczytu lub można skalować ją w celu wyświetlenia edytowalnych widoków bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="67108-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="67108-105">Formant `DataGridView` można rozbudować na kilka sposobów, aby tworzyć niestandardowe zachowania w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="67108-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="67108-106">Można na przykład programowo określić własne algorytmy sortowania i można utworzyć własne typy komórek.</span><span class="sxs-lookup"><span data-stu-id="67108-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="67108-107">Wygląd formantu `DataGridView` można łatwo dostosować, wybierając spośród kilku właściwości.</span><span class="sxs-lookup"><span data-stu-id="67108-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="67108-108">Wiele typów magazynów danych może służyć jako źródło danych lub formant `DataGridView` może działać bez powiązanego ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="67108-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="67108-109">W tematach w tej sekcji opisano koncepcje i techniki, których można użyć do kompilowania `DataGridView` funkcji w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="67108-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67108-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="67108-110">In This Section</span></span>  
 [<span data-ttu-id="67108-111">DataGridView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="67108-111">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="67108-112">Zawiera tematy opisujące architekturę i podstawowe koncepcje Windows Forms `DataGridView` kontroli.</span><span class="sxs-lookup"><span data-stu-id="67108-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="67108-113">Funkcje domyślne w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-114">Opisuje domyślny wygląd i zachowanie kontrolki `DataGridView` Windows Forms, gdy jest ona powiązana ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="67108-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="67108-115">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-115">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-116">Opisuje typy kolumn w kontrolce `DataGridView` Windows Forms używane do wyświetlania danych i Zezwalanie użytkownikom na modyfikowanie i Dodawanie danych.</span><span class="sxs-lookup"><span data-stu-id="67108-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="67108-117">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="67108-118">Zawiera tematy opisujące często używane właściwości komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="67108-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="67108-119">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-120">Zawiera tematy opisujące sposób modyfikowania podstawowego wyglądu kontrolki i formatowania wyświetlania danych komórek.</span><span class="sxs-lookup"><span data-stu-id="67108-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="67108-121">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-122">Zawiera tematy opisujące sposób wypełniania kontrolki danymi ręcznie lub z zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="67108-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="67108-123">Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-124">Zawiera tematy opisujące sposób automatycznego dopasowywania rozmiaru wierszy i kolumn w celu dopasowania do zawartości komórki lub dopasowania do dostępnej szerokości formantu.</span><span class="sxs-lookup"><span data-stu-id="67108-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="67108-125">Sortowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-126">Zawiera tematy opisujące funkcje sortowania w formancie.</span><span class="sxs-lookup"><span data-stu-id="67108-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="67108-127">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-127">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-128">Zawiera tematy opisujące sposób zmiany sposobu, w jaki użytkownicy mogą dodawać i modyfikować dane w formancie.</span><span class="sxs-lookup"><span data-stu-id="67108-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="67108-129">Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-130">Zawiera tematy opisujące funkcje wyboru komórek, wierszy i kolumn w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="67108-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="67108-131">Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="67108-132">Zawiera tematy opisujące sposób programowania z obiektami komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="67108-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="67108-133">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-133">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-134">Zawiera tematy opisujące niestandardowe malowanie `DataGridView` komórek i wierszy oraz tworzenie pochodnej komórki, kolumny i typów wierszy.</span><span class="sxs-lookup"><span data-stu-id="67108-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="67108-135">Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-136">Zawiera tematy opisujące sposób efektywnego używania kontrolki w celu uniknięcia problemów z wydajnością podczas pracy z dużymi ilościami danych.</span><span class="sxs-lookup"><span data-stu-id="67108-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="67108-137">Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67108-138">Opisuje sposób, w jaki użytkownicy mogą korzystać z formantu `DataGridView` za pomocą klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="67108-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="67108-139">Różnice między kontrolkami DataGridView i DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="67108-140">Opisuje, w jaki sposób formant `DataGridView` jest ulepszony i zastępuje formant <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="67108-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="67108-141">Zobacz również [Korzystanie z projektanta z Windows Forms formant DataGridView](using-the-designer-with-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="67108-141">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="67108-142">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="67108-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="67108-143">Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="67108-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="67108-144">Zawiera dokumentację referencyjną składnika <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="67108-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="67108-145">Kontrolka <xref:System.Windows.Forms.DataGridView> i składnik <xref:System.Windows.Forms.BindingSource> zostały zaprojektowane tak, aby ściśle współpracować.</span><span class="sxs-lookup"><span data-stu-id="67108-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67108-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67108-146">See also</span></span>

- [<span data-ttu-id="67108-147">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67108-147">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
