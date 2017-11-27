---
title: "DataGridView — Formant (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08a0cc15cff39bb936a78db95c73568aa643d0b6
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="b3c5c-102">DataGridView — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="b3c5c-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="b3c5c-103">`DataGridView` Kontrola zapewnia wydajny i elastyczny sposób wyświetlania danych w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="b3c5c-104">Można użyć `DataGridView` sterowania do wyświetlenia w widokach tylko do odczytu małe ilości danych lub można skalować, aby pokazać widokach edytowalnych bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="b3c5c-105">Można rozszerzyć `DataGridView` sterowania na kilka różnych sposobów tworzenia niestandardowych zachowania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="b3c5c-106">Na przykład można programowo określić własne sortowanie algorytmów i własnych typów komórek.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="b3c5c-107">Można łatwo dostosować wygląd `DataGridView` kontroli, wybierając spośród kilku właściwości.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="b3c5c-108">Wiele typów magazynów danych może służyć jako źródła danych lub `DataGridView` formant może działać bez powiązane z nim źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="b3c5c-109">W tematach w tej sekcji opisano pojęcia i techniki, które służy do tworzenia `DataGridView` funkcje do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3c5c-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b3c5c-110">In This Section</span></span>  
 [<span data-ttu-id="b3c5c-111">Informacje o formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="b3c5c-111">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="b3c5c-112">Udostępnia tematów dotyczących architektury i podstawowe pojęcia formularzy systemu Windows `DataGridView` formantu.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="b3c5c-113">Domyślna funkcjonalność w oknach formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="b3c5c-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-114">Opis domyślny wygląd i zachowanie formularzy systemu Windows `DataGridView` kontroli, gdy jest ona powiązana ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="b3c5c-115">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-115">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-116">W tym artykule opisano typy kolumn w formularzach systemu Windows `DataGridView` kontrolkę służącą do wyświetlania danych i Zezwalaj użytkownikom na modyfikowanie lub dodawanie danych.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="b3c5c-117">Wierszy i kolumn podstawowe funkcje komórek w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="b3c5c-118">Udostępnia tematów opisujących najczęściej używanych właściwości komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="b3c5c-119">Podstawowe formatowanie i style w oknach formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="b3c5c-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-120">Udostępnia tematach opisano sposób modyfikowania podstawowe wygląd formantu i formatowania wyświetlania danych komórki.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="b3c5c-121">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-122">Zawiera tematy, które opisują sposób wypełnienia formantu z danymi w sposób ręczny lub z zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="b3c5c-123">Zmiana rozmiaru wierszy i kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-124">Udostępnia tematów opisujących sposób rozmiaru wierszy i kolumn można dostosować automatycznie dopasowana do zawartości komórki lub aby dopasować dostępne szerokość formantu.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="b3c5c-125">Sortowanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-126">Udostępnia tematów opisujących funkcji sortowania w formancie.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="b3c5c-127">Formantu DataGridView formularzy wprowadzania danych w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-127">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-128">Udostępnia tematów opisujących sposób zmiany przez użytkowników, dodawanie i modyfikowanie danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="b3c5c-129">Wybór i używanie Schowka z formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-130">Udostępnia tematów opisujących funkcje wyboru komórek, wierszy i kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="b3c5c-131">Programowanie przy użyciu komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="b3c5c-132">Zawiera tematy dotyczące sposobu programu z komórek, wierszy i kolumn obiektów.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="b3c5c-133">Dostosowywanie formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-133">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-134">Udostępnia tematów opisujących rysowania niestandardowych `DataGridView` komórek i wierszy oraz tworzenie pochodnych komórki, kolumny i typy wierszy.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="b3c5c-135">Dostrajanie wydajności w systemu Windows do formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="b3c5c-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-136">Udostępnia tematów opisujących sposób efektywnie wykorzystać formantu, aby uniknąć problemów z wydajnością, podczas pracy z dużą ilością danych.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="b3c5c-137">Domyślna obsługa w formancie DataGridView formularzy systemu Windows myszy i klawiatury</span><span class="sxs-lookup"><span data-stu-id="b3c5c-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b3c5c-138">Zawiera opis sposobu interakcji użytkowników z `DataGridView` sterowanie za pośrednictwem klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="b3c5c-139">Różnice między formantami DataGrid i DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="b3c5c-140">Opisuje sposób `DataGridView` kontroli poprawia i zastępuje <xref:System.Windows.Forms.DataGrid> formantu.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="b3c5c-141">Zobacz też [z formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b3c5c-141">Also see [Using the Designer with the Windows Forms DataGridView Control](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b3c5c-142">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b3c5c-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b3c5c-143">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="b3c5c-144">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="b3c5c-145"><xref:System.Windows.Forms.DataGridView> Kontroli i <xref:System.Windows.Forms.BindingSource> składnika są przeznaczone do ściśle współpracować.</span><span class="sxs-lookup"><span data-stu-id="b3c5c-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c5c-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3c5c-146">See Also</span></span>  
 [<span data-ttu-id="b3c5c-147">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3c5c-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
