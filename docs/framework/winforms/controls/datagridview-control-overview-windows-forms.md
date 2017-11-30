---
title: "DataGridView — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4209866f63931fb3d80f35e211bd5f9b35ed48bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="6cd32-102">DataGridView — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="6cd32-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="6cd32-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="6cd32-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="6cd32-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6cd32-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="6cd32-105">Z <xref:System.Windows.Forms.DataGridView> sterowania, można wyświetlić i edytować dane tabelaryczne z wielu różnych rodzajów źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="6cd32-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="6cd32-106">Wiązanie danych do <xref:System.Windows.Forms.DataGridView> formant jest bardzo proste i intuicyjne i w wielu przypadkach jest tak proste, jak ustawienie <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6cd32-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="6cd32-107">Jeśli możesz powiązać ze źródłem danych, który zawiera wiele list lub tabele, należy skonfigurować <xref:System.Windows.Forms.DataGridView.DataMember%2A> właściwości na ciąg, który określa listy lub tabeli, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="6cd32-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="6cd32-108"><xref:System.Windows.Forms.DataGridView> Sterowanie obsługuje standardowy model powiązanie danych formularzy systemu Windows, więc będzie powiązać wystąpienia klas opisane na liście:</span><span class="sxs-lookup"><span data-stu-id="6cd32-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
-   <span data-ttu-id="6cd32-109">Każda klasa implementująca <xref:System.Collections.IList> interfejs, w tym tablice jednowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="6cd32-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="6cd32-110">Każda klasa implementująca <xref:System.ComponentModel.IListSource> interfejsu, takich jak <xref:System.Data.DataTable> i <xref:System.Data.DataSet> klasy.</span><span class="sxs-lookup"><span data-stu-id="6cd32-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
-   <span data-ttu-id="6cd32-111">Każda klasa implementująca <xref:System.ComponentModel.IBindingList> interfejsu, takich jak <xref:System.ComponentModel.BindingList%601> klasy.</span><span class="sxs-lookup"><span data-stu-id="6cd32-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
-   <span data-ttu-id="6cd32-112">Każda klasa implementująca <xref:System.ComponentModel.IBindingListView> interfejsu, takich jak <xref:System.Windows.Forms.BindingSource> klasy.</span><span class="sxs-lookup"><span data-stu-id="6cd32-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="6cd32-113"><xref:System.Windows.Forms.DataGridView> Sterowanie obsługuje powiązanie danych właściwości publicznych zwracanych przez te interfejsy obiektów lub kolekcji właściwości zwróconej przez <xref:System.ComponentModel.ICustomTypeDescriptor> interfejsu, jeśli została zaimplementowana na zwracanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="6cd32-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="6cd32-114">Zazwyczaj będzie można powiązać <xref:System.Windows.Forms.BindingSource> składnika i powiązania <xref:System.Windows.Forms.BindingSource> składnika do innego źródła danych lub umieścić w nim obiektów biznesowych.</span><span class="sxs-lookup"><span data-stu-id="6cd32-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="6cd32-115"><xref:System.Windows.Forms.BindingSource> Składnika jest źródłem danych preferowane, ponieważ można powiązać z różnych źródeł danych i może automatycznie rozwiązać wiele problemów powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="6cd32-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="6cd32-116">Aby uzyskać więcej informacji, zobacz [BindingSource — składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="6cd32-116">For more information, see [BindingSource Component](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="6cd32-117"><xref:System.Windows.Forms.DataGridView> Formantu można używać w *niezwiązanego* trybie z nie odpowiedni magazyn danych.</span><span class="sxs-lookup"><span data-stu-id="6cd32-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="6cd32-118">W przykładzie kodu używającej niezwiązanego <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [wskazówki: utworzenie niezwiązanego formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6cd32-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="6cd32-119"><xref:System.Windows.Forms.DataGridView> Formant jest wysoce można konfigurować i rozszerzalny i oferuje wiele właściwości, metod i zdarzeń, aby dostosować wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="6cd32-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="6cd32-120">Do wyświetlania danych tabelarycznych aplikacji formularzy systemu Windows, należy rozważyć użycie <xref:System.Windows.Forms.DataGridView> kontroli przed innymi (na przykład <xref:System.Windows.Forms.DataGrid>).</span><span class="sxs-lookup"><span data-stu-id="6cd32-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="6cd32-121">W przypadku wyświetlania Mała siatka wartości tylko do odczytu lub Jeśli włączasz użytkownika do edytowania tabeli z miliony rekordów, <xref:System.Windows.Forms.DataGridView> kontroli pozwoli łatwo programowalny, pamięci wydajne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6cd32-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6cd32-122">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6cd32-122">In This Section</span></span>  
 [<span data-ttu-id="6cd32-123">Podsumowanie informacji o technologii formantów DataGridView</span><span class="sxs-lookup"><span data-stu-id="6cd32-123">DataGridView Control Technology Summary</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="6cd32-124">Podsumowanie <xref:System.Windows.Forms.DataGridView> kontrolować pojęcia i korzystanie z powiązanymi klasami.</span><span class="sxs-lookup"><span data-stu-id="6cd32-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="6cd32-125">DataGridView — architektura formantu</span><span class="sxs-lookup"><span data-stu-id="6cd32-125">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="6cd32-126">Zawiera opis architektury <xref:System.Windows.Forms.DataGridView> kontroli wyjaśniający, jego typ struktury hierarchii i dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="6cd32-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="6cd32-127">Scenariusze formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="6cd32-127">DataGridView Control Scenarios</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="6cd32-128">W tym artykule opisano najbardziej typowych scenariuszy, w którym <xref:System.Windows.Forms.DataGridView> formanty są używane.</span><span class="sxs-lookup"><span data-stu-id="6cd32-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="6cd32-129">Katalog kodu kontrolki DataGridView</span><span class="sxs-lookup"><span data-stu-id="6cd32-129">DataGridView Control Code Directory</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="6cd32-130">Zawiera łącza do przykładów kodu w dokumentacji dla różnych <xref:System.Windows.Forms.DataGridView> zadania.</span><span class="sxs-lookup"><span data-stu-id="6cd32-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="6cd32-131">Te przykłady są podzielone według typu zadań.</span><span class="sxs-lookup"><span data-stu-id="6cd32-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6cd32-132">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6cd32-132">Related Sections</span></span>  
 [<span data-ttu-id="6cd32-133">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6cd32-133">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6cd32-134">W tym artykule omówiono typy kolumn w formularzach systemu Windows <xref:System.Windows.Forms.DataGridView> kontrolkę służącą do wyświetlania informacji i Zezwalaj użytkownikom na modyfikowanie lub dodawanie informacji.</span><span class="sxs-lookup"><span data-stu-id="6cd32-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="6cd32-135">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6cd32-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6cd32-136">Zawiera tematy, które opisują sposób wypełnienia formantu z danymi w sposób ręczny lub z zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="6cd32-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="6cd32-137">Dostosowywanie formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6cd32-137">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6cd32-138">Udostępnia tematów opisujących rysowania niestandardowych <xref:System.Windows.Forms.DataGridView> komórek i wierszy oraz tworzenie pochodnych komórki, kolumny i typy wierszy.</span><span class="sxs-lookup"><span data-stu-id="6cd32-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="6cd32-139">Dostrajanie wydajności w systemu Windows do formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="6cd32-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6cd32-140">Udostępnia tematów opisujących sposób efektywnie wykorzystać formantu, aby uniknąć problemów z wydajnością, podczas pracy z dużą ilością danych.</span><span class="sxs-lookup"><span data-stu-id="6cd32-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd32-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cd32-141">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="6cd32-142">DataGridView — formant</span><span class="sxs-lookup"><span data-stu-id="6cd32-142">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="6cd32-143">Domyślna funkcjonalność w oknach formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="6cd32-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6cd32-144">Domyślna obsługa w formancie DataGridView formularzy systemu Windows myszy i klawiatury</span><span class="sxs-lookup"><span data-stu-id="6cd32-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
