---
title: DataGridView — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- DataGridView
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
ms.openlocfilehash: 74de5b449525be9ff93fcbef0ddabd041470177c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742497"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="64222-102">DataGridView — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="64222-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="64222-103">Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="64222-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="64222-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="64222-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="64222-105">Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można wyświetlać i edytować dane tabelaryczne z wielu różnych rodzajów źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="64222-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="64222-106">Powiązanie danych z formantem <xref:System.Windows.Forms.DataGridView> jest proste i intuicyjne, a w wielu przypadkach jest tak proste jak ustawienie właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="64222-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="64222-107">Po utworzeniu powiązania ze źródłem danych zawierającym wiele list lub tabel ustaw właściwość <xref:System.Windows.Forms.DataGridView.DataMember%2A> na ciąg, który określa listę lub tabelę, z którą ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="64222-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="64222-108">Kontrolka <xref:System.Windows.Forms.DataGridView> obsługuje model powiązań danych w warstwie Standardowa Windows Forms, więc zostanie powiązana z wystąpieniami klas opisanymi na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="64222-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
- <span data-ttu-id="64222-109">Każda klasa implementująca interfejs <xref:System.Collections.IList>, w tym tablice jednowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="64222-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
- <span data-ttu-id="64222-110">Każda klasa implementująca interfejs <xref:System.ComponentModel.IListSource>, taka jak klasy <xref:System.Data.DataTable> i <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="64222-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
- <span data-ttu-id="64222-111">Każda klasa implementująca interfejs <xref:System.ComponentModel.IBindingList>, taka jak Klasa <xref:System.ComponentModel.BindingList%601>.</span><span class="sxs-lookup"><span data-stu-id="64222-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
- <span data-ttu-id="64222-112">Każda klasa implementująca interfejs <xref:System.ComponentModel.IBindingListView>, taka jak Klasa <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="64222-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="64222-113">Formant <xref:System.Windows.Forms.DataGridView> obsługuje powiązanie danych z publicznymi właściwościami obiektów zwróconych przez te interfejsy lub do kolekcji właściwości zwracanych przez interfejs <xref:System.ComponentModel.ICustomTypeDescriptor>, jeśli zaimplementowano dla zwracanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="64222-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="64222-114">Zazwyczaj utworzysz powiązanie ze składnikiem <xref:System.Windows.Forms.BindingSource> i powiążesz składnik <xref:System.Windows.Forms.BindingSource> z innym źródłem danych lub wypełnij je obiektami biznesowymi.</span><span class="sxs-lookup"><span data-stu-id="64222-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="64222-115">Składnik <xref:System.Windows.Forms.BindingSource> jest preferowanym źródłem danych, ponieważ może być powiązany z wieloma różnymi źródłami danych i może automatycznie rozwiązywać wiele problemów z powiązaniem danych.</span><span class="sxs-lookup"><span data-stu-id="64222-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="64222-116">Aby uzyskać więcej informacji, zobacz [Składnik BindingSource](bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="64222-116">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="64222-117">Formant <xref:System.Windows.Forms.DataGridView> może być również używany w trybie *niezwiązanym* bez podstawowego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="64222-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="64222-118">Aby zapoznać się z przykładem kodu korzystającym z niepowiązanej kontrolki <xref:System.Windows.Forms.DataGridView>, zobacz [Przewodnik: Tworzenie niepowiązanego Windows Forms formantu DataGridView](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="64222-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="64222-119">Formant <xref:System.Windows.Forms.DataGridView> jest wysoce konfigurowalny i rozszerzalny oraz zawiera wiele właściwości, metod i zdarzeń, aby dostosować jego wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="64222-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="64222-120">Jeśli chcesz, aby aplikacja Windows Forms wyświetlała dane tabelaryczne, rozważ użycie kontrolki <xref:System.Windows.Forms.DataGridView> przed innymi (na przykład <xref:System.Windows.Forms.DataGrid>).</span><span class="sxs-lookup"><span data-stu-id="64222-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="64222-121">Jeśli jest wyświetlana Mała siatka wartości tylko do odczytu lub jeśli użytkownik chce edytować tabelę z milionami rekordów, formant <xref:System.Windows.Forms.DataGridView> zapewnia łatwo programowalne, wydajne rozwiązanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="64222-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64222-122">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="64222-122">In This Section</span></span>  
 [<span data-ttu-id="64222-123">DataGridView, kontrolka — podsumowanie technologii</span><span class="sxs-lookup"><span data-stu-id="64222-123">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="64222-124">Podsumowuje <xref:System.Windows.Forms.DataGridView> koncepcje kontroli i użycie powiązanych klas.</span><span class="sxs-lookup"><span data-stu-id="64222-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="64222-125">DataGridView, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="64222-125">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="64222-126">Opisuje architekturę formantu <xref:System.Windows.Forms.DataGridView>, co wyjaśnia jego hierarchię typów i strukturę dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="64222-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="64222-127">DataGridView, kontrolka — scenariusze</span><span class="sxs-lookup"><span data-stu-id="64222-127">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="64222-128">Opisuje najczęstsze scenariusze, w których są używane kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="64222-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="64222-129">DataGridView, kontrolka — katalog kodu</span><span class="sxs-lookup"><span data-stu-id="64222-129">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="64222-130">Zawiera łącza do przykładów kodu w dokumentacji dotyczącej różnych <xref:System.Windows.Forms.DataGridView> zadań.</span><span class="sxs-lookup"><span data-stu-id="64222-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="64222-131">Te przykłady są podzielone według typu zadania.</span><span class="sxs-lookup"><span data-stu-id="64222-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="64222-132">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="64222-132">Related Sections</span></span>  
 [<span data-ttu-id="64222-133">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64222-133">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="64222-134">W tym artykule omówiono typy kolumn w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms używane do wyświetlania informacji i Zezwalanie użytkownikom na modyfikowanie lub Dodawanie informacji.</span><span class="sxs-lookup"><span data-stu-id="64222-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="64222-135">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64222-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="64222-136">Zawiera tematy opisujące sposób wypełniania kontrolki danymi ręcznie lub z zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="64222-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="64222-137">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64222-137">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="64222-138">Zawiera tematy opisujące niestandardowe malowanie <xref:System.Windows.Forms.DataGridView> komórek i wierszy oraz tworzenie pochodnej komórki, kolumny i typów wierszy.</span><span class="sxs-lookup"><span data-stu-id="64222-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="64222-139">Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64222-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="64222-140">Zawiera tematy opisujące sposób efektywnego używania kontrolki w celu uniknięcia problemów z wydajnością podczas pracy z dużymi ilościami danych.</span><span class="sxs-lookup"><span data-stu-id="64222-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64222-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64222-141">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="64222-142">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="64222-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="64222-143">Funkcje domyślne w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64222-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="64222-144">Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64222-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
