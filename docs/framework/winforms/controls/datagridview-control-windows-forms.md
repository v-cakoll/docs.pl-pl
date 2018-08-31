---
title: DataGridView — Formant (Formularze systemu Windows)
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
ms.openlocfilehash: 2ef387437befe3df67e261b719140456a3fde9dd
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332510"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="b22a3-102">DataGridView — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="b22a3-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="b22a3-103">`DataGridView` Kontrola zapewnia wydajny i elastyczny sposób wyświetlania danych w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="b22a3-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="b22a3-104">Możesz użyć `DataGridView` sterowania do wyświetlenia w widokach tylko do odczytu z małą ilością danych oraz skalowania, aby pokazać widokach edytowalnych bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="b22a3-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="b22a3-105">Możesz rozszerzyć `DataGridView` kontroli na wiele sposobów, aby tworzyć niestandardowe zachowania w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="b22a3-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="b22a3-106">Na przykład można programowo określić własny algorytmy sortujące i swój własny typ komórki.</span><span class="sxs-lookup"><span data-stu-id="b22a3-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="b22a3-107">Można łatwo dostosować wygląd `DataGridView` kontroli, wybierając między kilka właściwości.</span><span class="sxs-lookup"><span data-stu-id="b22a3-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="b22a3-108">Wiele typów magazynów danych może służyć jako źródła danych lub `DataGridView` kontroli może działać bez źródła danych powiązane z nim.</span><span class="sxs-lookup"><span data-stu-id="b22a3-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="b22a3-109">W tematach w tej sekcji opisano pojęć i technik, które służą do tworzenia `DataGridView` funkcji w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="b22a3-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b22a3-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b22a3-110">In This Section</span></span>  
 [<span data-ttu-id="b22a3-111">DataGridView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="b22a3-111">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="b22a3-112">Zawiera tematy, które opisują architekturę i podstawowe pojęcia formularzy Windows Forms `DataGridView` kontroli.</span><span class="sxs-lookup"><span data-stu-id="b22a3-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="b22a3-113">Funkcje domyślne w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-114">W tym artykule opisano domyślny wygląd i zachowanie formularzy Windows `DataGridView` kontroli, gdy jest powiązana ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="b22a3-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="b22a3-115">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-115">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-116">W tym artykule opisano typy kolumn w formularzach Windows Forms `DataGridView` kontrolkę służącą do wyświetlania danych i Zezwalaj użytkownikom na modyfikowanie lub dodawanie danych.</span><span class="sxs-lookup"><span data-stu-id="b22a3-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="b22a3-117">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="b22a3-118">Zawiera tematy, które opisują najczęściej używanych właściwości komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="b22a3-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="b22a3-119">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-120">Zawiera tematy, które opisują sposób modyfikowania wyglądu podstawowego formantu i formatowania wyświetlania danych komórki.</span><span class="sxs-lookup"><span data-stu-id="b22a3-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="b22a3-121">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-122">Zawiera tematy, które opisują sposób wypełnienia kontrolki z danymi ręczny lub z zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b22a3-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="b22a3-123">Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-124">Zawiera tematy, które opisują, jak rozmiar wierszy i kolumn można dostosować automatycznie Dopasuj zawartość komórki lub Dopasuj dostępne szerokość kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b22a3-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="b22a3-125">Sortowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-126">Zawiera tematy, które opisują funkcje sortowania w formancie.</span><span class="sxs-lookup"><span data-stu-id="b22a3-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="b22a3-127">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-127">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-128">Zawiera tematy, które opisują sposób zmiany przez użytkowników, dodawanie i modyfikowanie danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="b22a3-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="b22a3-129">Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-130">Zawiera tematy, które opisano funkcje Zaznaczanie komórek, wierszy i kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="b22a3-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="b22a3-131">Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="b22a3-132">Zawiera tematy, które opisują sposób programowania przy użyciu komórek, wierszy i kolumn obiektów.</span><span class="sxs-lookup"><span data-stu-id="b22a3-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="b22a3-133">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-133">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-134">Zawiera tematy, które opisują niestandardowego rysowania `DataGridView` komórek i wierszy oraz tworzenie pochodnych komórki, kolumny i typy wierszy.</span><span class="sxs-lookup"><span data-stu-id="b22a3-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="b22a3-135">Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-136">Zawiera tematy, które opisują sposób efektywnie wykorzystać formantu, aby uniknąć problemów z wydajnością podczas pracy z dużymi ilościami danych.</span><span class="sxs-lookup"><span data-stu-id="b22a3-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="b22a3-137">Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b22a3-138">W tym artykule opisano, jak użytkownicy mogą korzystać z `DataGridView` sterowanie za pośrednictwem klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="b22a3-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="b22a3-139">Różnice między kontrolkami DataGridView i DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="b22a3-140">W tym artykule opisano sposób, w jaki `DataGridView` kontroli poprawia i zastępuje <xref:System.Windows.Forms.DataGrid> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b22a3-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="b22a3-141">Zobacz też [przy użyciu narzędzia Projektant z formantu DataGridView formularzy Windows](using-the-designer-with-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b22a3-141">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b22a3-142">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b22a3-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b22a3-143">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b22a3-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="b22a3-144">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="b22a3-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="b22a3-145"><xref:System.Windows.Forms.DataGridView> Kontroli i <xref:System.Windows.Forms.BindingSource> składnika są przeznaczone do ściśle współpracować.</span><span class="sxs-lookup"><span data-stu-id="b22a3-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b22a3-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b22a3-146">See Also</span></span>  
 [<span data-ttu-id="b22a3-147">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b22a3-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
