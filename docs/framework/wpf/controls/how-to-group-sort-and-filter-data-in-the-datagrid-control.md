---
title: 'Instrukcje: Grupowanie, sortowanie i filtrowanie danych w formancie DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 81fdb0a6d5602f612c55d7e790ca9a0fe56c144e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771094"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="1fbe5-102">Instrukcje: Grupować, sortować i filtrować dane w DataGrid kontrolce</span><span class="sxs-lookup"><span data-stu-id="1fbe5-102">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="1fbe5-103">Często jest to przydatne do wyświetlania danych w <xref:System.Windows.Controls.DataGrid> na różne sposoby grupowania, sortowania i filtrowania danych.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="1fbe5-104">Aby grupować, sortować i filtrować dane w <xref:System.Windows.Controls.DataGrid>, aby powiązać <xref:System.Windows.Data.CollectionView> , która obsługuje te funkcje.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="1fbe5-105">Możesz następnie można pracować z danymi w <xref:System.Windows.Data.CollectionView> bez wywierania wpływu na podstawowe źródło danych.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="1fbe5-106">Zmiany w widoku kolekcji są odzwierciedlane w <xref:System.Windows.Controls.DataGrid> interfejsu użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="1fbe5-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="1fbe5-107"><xref:System.Windows.Data.CollectionView> Klasa udostępnia grupowania i sortowania funkcjonalność dla źródła danych, który implementuje <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="1fbe5-108"><xref:System.Windows.Data.CollectionViewSource> Klasa służy do ustawiania właściwości <xref:System.Windows.Data.CollectionView> z XAML.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="1fbe5-109">W tym przykładzie, Kolekcja `Task` obiektów jest powiązany z <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="1fbe5-110"><xref:System.Windows.Data.CollectionViewSource> Służy jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="1fbe5-111">Grupowanie, sortowania i filtrowania są wykonywane na <xref:System.Windows.Data.CollectionViewSource> i są wyświetlane w <xref:System.Windows.Controls.DataGrid> interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="1fbe5-112">![Grupowane dane w DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") grupowane dane w DataGrid</span><span class="sxs-lookup"><span data-stu-id="1fbe5-112">![Grouped data in a DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="1fbe5-113">Przy użyciu CollectionViewSource ItemsSource</span><span class="sxs-lookup"><span data-stu-id="1fbe5-113">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="1fbe5-114">Aby grupować, sortować i filtrować dane w <xref:System.Windows.Controls.DataGrid> kontroli można powiązać <xref:System.Windows.Controls.DataGrid> do <xref:System.Windows.Data.CollectionView> , która obsługuje te funkcje.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-114">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="1fbe5-115">W tym przykładzie <xref:System.Windows.Controls.DataGrid> jest powiązany z <xref:System.Windows.Data.CollectionViewSource> zapewniający te funkcje do <xref:System.Collections.Generic.List%601> z `Task` obiektów.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-115">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="1fbe5-116">Aby powiązać CollectionViewSource elementem DataGrid</span><span class="sxs-lookup"><span data-stu-id="1fbe5-116">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="1fbe5-117">Utwórz kolekcję danych, która implementuje <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-117">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="1fbe5-118">Jeśli używasz <xref:System.Collections.Generic.List%601> do utworzenia kolekcji, należy utworzyć nową klasę, która dziedziczy <xref:System.Collections.Generic.List%601> zamiast tworzenia wystąpienia wystąpienie <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-118">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="1fbe5-119">Dzięki temu można utworzyć powiązania danych do kolekcji w XAML.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-119">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1fbe5-120">Obiekty w kolekcji musi implementować <xref:System.ComponentModel.INotifyPropertyChanged> zmienione interfejsu i <xref:System.ComponentModel.IEditableObject> interfejsu, aby <xref:System.Windows.Controls.DataGrid> odpowiedzieć poprawnie zmian właściwości i modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-120">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="1fbe5-121">Aby uzyskać więcej informacji, zobacz [powiadomienie o zmianie właściwości Implementowanie](../data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="1fbe5-121">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="1fbe5-122">W XAML, należy utworzyć wystąpienie klasy kolekcji i ustaw [x: Key — dyrektywa](../../xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="1fbe5-122">In XAML, create an instance of the collection class and set the [x:Key Directive](../../xaml-services/x-key-directive.md).</span></span>

3. <span data-ttu-id="1fbe5-123">W XAML, Utwórz wystąpienie obiektu <xref:System.Windows.Data.CollectionViewSource> klasy, należy ustawić [x: Key — dyrektywa](../../xaml-services/x-key-directive.md), a wystąpienie klasy kolekcji, jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-123">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="1fbe5-124">Utwórz wystąpienie obiektu <xref:System.Windows.Controls.DataGrid> klasy, a następnie ustaw <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-124">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="1fbe5-125">Aby uzyskać dostęp do <xref:System.Windows.Data.CollectionViewSource> w kodzie, należy użyć <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodę, aby pobrać odwołanie do <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-125">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="1fbe5-126">Grupowanie elementów w DataGrid</span><span class="sxs-lookup"><span data-stu-id="1fbe5-126">Grouping items in a DataGrid</span></span>

<span data-ttu-id="1fbe5-127">Aby określić sposób grupowania elementów w <xref:System.Windows.Controls.DataGrid>, możesz użyć <xref:System.Windows.Data.PropertyGroupDescription> typu do grupowania elementów w widoku źródła.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-127">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="1fbe5-128">Aby grupować elementy DataGrid, przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="1fbe5-128">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="1fbe5-129">Utwórz <xref:System.Windows.Data.PropertyGroupDescription> , który określa właściwości do Grupuj według.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-129">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="1fbe5-130">Można określić właściwości, XAML lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-130">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="1fbe5-131">W XAML, ustaw <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na nazwę właściwości do Grupuj według.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-131">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="1fbe5-132">W kodzie należy przekazać nazwę właściwości do grupy, do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-132">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="1fbe5-133">Dodaj <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-133">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="1fbe5-134">Dodaj dodatkowe wystąpienia <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji, aby dodać więcej poziomy grupowania.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-134">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="1fbe5-135">Aby usunąć grupę, Usuń <xref:System.Windows.Data.PropertyGroupDescription> z <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-135">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="1fbe5-136">Aby usunąć wszystkie grupy, należy wywołać <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> metody <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-136">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="1fbe5-137">Gdy elementy są pogrupowane w <xref:System.Windows.Controls.DataGrid>, można zdefiniować <xref:System.Windows.Controls.GroupStyle> , który określa wygląd każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-137">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="1fbe5-138">Należy zastosować <xref:System.Windows.Controls.GroupStyle> przez dodanie jej do <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> kolekcji elementu DataGrid.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-138">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="1fbe5-139">Jeśli masz wiele poziomów grupowania, można zastosować różne style do każdego poziomu grupy.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-139">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="1fbe5-140">Style są stosowane w kolejności, w której są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-140">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="1fbe5-141">Na przykład jeśli zdefiniujesz dwa style, pierwszy będą stosowane do grupy najwyższego poziomu wierszy.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-141">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="1fbe5-142">Drugi stylu będą stosowane do wszystkich grup wierszy na drugim poziomie i niższych.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-142">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="1fbe5-143"><xref:System.Windows.FrameworkElement.DataContext%2A> z <xref:System.Windows.Controls.GroupStyle> jest <xref:System.Windows.Data.CollectionViewGroup> reprezentujący grupy.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-143">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="1fbe5-144">Aby zmienić wygląd nagłówków grup wierszy</span><span class="sxs-lookup"><span data-stu-id="1fbe5-144">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="1fbe5-145">Utwórz <xref:System.Windows.Controls.GroupStyle> definiuje wygląd grupę wierszy.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-145">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="1fbe5-146">Umieść <xref:System.Windows.Controls.GroupStyle> wewnątrz `<DataGrid.GroupStyle>` tagów.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-146">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="1fbe5-147">Sortowanie elementów w DataGrid</span><span class="sxs-lookup"><span data-stu-id="1fbe5-147">Sorting items in a DataGrid</span></span>

<span data-ttu-id="1fbe5-148">Aby określić, jak elementy są sortowane według <xref:System.Windows.Controls.DataGrid>, możesz użyć <xref:System.ComponentModel.SortDescription> typu, aby posortować elementy w widoku źródła.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-148">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="1fbe5-149">Aby posortować elementy w DataGrid</span><span class="sxs-lookup"><span data-stu-id="1fbe5-149">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="1fbe5-150">Utwórz <xref:System.ComponentModel.SortDescription> , który określa właściwość, aby posortować według.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-150">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="1fbe5-151">Można określić właściwości, XAML lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-151">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="1fbe5-152">W XAML, ustaw <xref:System.ComponentModel.SortDescription.PropertyName%2A> na nazwę właściwości, aby posortować według.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-152">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="1fbe5-153">W kodzie, należy przekazać nazwę właściwości, aby posortować według i <xref:System.ComponentModel.ListSortDirection> do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-153">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="1fbe5-154">Dodaj <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-154">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="1fbe5-155">Dodaj dodatkowe wystąpienia <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> kolekcji, aby posortować według dodatkowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-155">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="1fbe5-156">Filtrowanie elementów w DataGrid</span><span class="sxs-lookup"><span data-stu-id="1fbe5-156">Filtering items in a DataGrid</span></span>

<span data-ttu-id="1fbe5-157">Na potrzeby filtrowania elementów w <xref:System.Windows.Controls.DataGrid> przy użyciu <xref:System.Windows.Data.CollectionViewSource>, zapewnić logikę filtrowania w obsłudze dla <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-157">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="1fbe5-158">Aby odfiltrować elementy w DataGrid</span><span class="sxs-lookup"><span data-stu-id="1fbe5-158">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="1fbe5-159">Dodaj program obsługi <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-159">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="1fbe5-160">W <xref:System.Windows.Data.CollectionViewSource.Filter> procedura obsługi zdarzeń, definiować logikę filtrowania.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-160">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="1fbe5-161">Filtr zostanie zastosowany, za każdym razem, gdy odświeżeniem widoku.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-161">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="1fbe5-162">Alternatywnie możesz filtrować elementy w <xref:System.Windows.Controls.DataGrid> przez tworzenie metody, która udostępnia logikę filtrowania i ustawienie <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> właściwości, aby zastosować filtr.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-162">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="1fbe5-163">Aby zobaczyć przykład tej metody, zobacz [filtrować dane w widoku](../data/how-to-filter-data-in-a-view.md).</span><span class="sxs-lookup"><span data-stu-id="1fbe5-163">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1fbe5-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fbe5-164">Example</span></span>

<span data-ttu-id="1fbe5-165">W poniższym przykładzie pokazano grupowania, sortowanie i filtrowanie `Task` dane w <xref:System.Windows.Data.CollectionViewSource> i wyświetlanie zgrupowane, posortowane i przefiltrowane `Task` dane w <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-165">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="1fbe5-166"><xref:System.Windows.Data.CollectionViewSource> Służy jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-166">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="1fbe5-167">Grupowanie, sortowania i filtrowania są wykonywane na <xref:System.Windows.Data.CollectionViewSource> i są wyświetlane w <xref:System.Windows.Controls.DataGrid> interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-167">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="1fbe5-168">Aby przetestować w tym przykładzie, należy dostosować nazwy DGGroupSortFilterExample, aby dopasować nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-168">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="1fbe5-169">Jeśli używasz języka Visual Basic, należy zmienić nazwę klasy <xref:System.Windows.Window> do następującego.</span><span class="sxs-lookup"><span data-stu-id="1fbe5-169">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="1fbe5-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fbe5-170">See also</span></span>

- [<span data-ttu-id="1fbe5-171">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="1fbe5-171">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="1fbe5-172">Tworzenie i powiązywanie z ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="1fbe5-172">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [<span data-ttu-id="1fbe5-173">Filtrowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="1fbe5-173">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="1fbe5-174">Sortowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="1fbe5-174">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="1fbe5-175">Sortowanie i grupowanie danych przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="1fbe5-175">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
