---
title: 'Porady: grupy, sortować i filtrować dane w elemencie DataGrid kontroli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 49ed0f43f0ebebe1aff7ef2f12f667ca656a774a
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028009"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Porady: grupowanie, sortowanie i filtrowanie danych w formancie DataGrid

Często jest to przydatne do wyświetlania danych w <xref:System.Windows.Controls.DataGrid> w różny sposób grupowania, sortowania i filtrowania danych. Do grupy, sortować i filtrować dane w <xref:System.Windows.Controls.DataGrid>, możesz powiązać <xref:System.Windows.Data.CollectionView> która obsługuje te funkcje. Potem można pracować z danymi w <xref:System.Windows.Data.CollectionView> bez wpływu na podstawowe źródło danych. Zmiany w widoku kolekcji są uwzględniane w <xref:System.Windows.Controls.DataGrid> interfejsu użytkownika (UI).

<xref:System.Windows.Data.CollectionView> Klasa udostępnia grupowanie i sortowanie funkcji dla źródła danych, który implementuje <xref:System.Collections.IEnumerable> interfejsu. <xref:System.Windows.Data.CollectionViewSource> Klasa służy do ustawiania właściwości <xref:System.Windows.Data.CollectionView> z XAML.

W tym przykładzie zbiór `Task` obiektów jest powiązany z <xref:System.Windows.Data.CollectionViewSource>. <xref:System.Windows.Data.CollectionViewSource> Jest używany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.DataGrid>. Grupowanie, sortowania i filtrowania są wykonywane na <xref:System.Windows.Data.CollectionViewSource> i są wyświetlane w <xref:System.Windows.Controls.DataGrid> interfejsu użytkownika.

![Grupowane dane w DataGrid](./media/wpf-datagridgroups.png "WPF_DataGridGroups") grupowane dane w DataGrid

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Przy użyciu CollectionViewSource jako ItemsSource.

Do grupy, sortowanie i filtrowanie danych <xref:System.Windows.Controls.DataGrid> bind formant, <xref:System.Windows.Controls.DataGrid> do <xref:System.Windows.Data.CollectionView> która obsługuje te funkcje. W tym przykładzie <xref:System.Windows.Controls.DataGrid> jest powiązany z <xref:System.Windows.Data.CollectionViewSource> zapewnia następujące funkcje dla <xref:System.Collections.Generic.List%601> z `Task` obiektów.

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Aby powiązać CollectionViewSource DataGrid

1. Utwórz kolekcję danych, która implementuje <xref:System.Collections.IEnumerable> interfejsu.

    Jeśli używasz <xref:System.Collections.Generic.List%601> do utworzenia kolekcji, należy utworzyć nową klasę, która dziedziczy <xref:System.Collections.Generic.List%601> zamiast instancji <xref:System.Collections.Generic.List%601>. Dzięki temu można utworzyć powiązania danych do kolekcji w języku XAML.

    > [!NOTE]
    > Obiekty w kolekcji musi implementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu zmienione i <xref:System.ComponentModel.IEditableObject> interfejsu, aby <xref:System.Windows.Controls.DataGrid> do poprawnej odpowiedzi do zmian właściwości i modyfikacji. Aby uzyskać więcej informacji, zobacz [powiadomienia o zmianie właściwości wdrożenie](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. W języku XAML, należy utworzyć wystąpienia klasy kolekcji i ustawić [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md).

3. W języku XAML, Utwórz wystąpienie <xref:System.Windows.Data.CollectionViewSource> klasy, ustaw [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md)i ustaw wystąpienia klasy kolekcji jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. Utwórz wystąpienie <xref:System.Windows.Controls.DataGrid> klasy, a następnie ustaw <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości <xref:System.Windows.Data.CollectionViewSource>.

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Aby uzyskać dostęp do <xref:System.Windows.Data.CollectionViewSource> w kodzie, użyj <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodę, aby pobrać odwołanie do <xref:System.Windows.Data.CollectionViewSource>.

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>Grupowanie elementów w DataGrid

Aby określić sposób grupowania elementów w <xref:System.Windows.Controls.DataGrid>, możesz użyć <xref:System.Windows.Data.PropertyGroupDescription> typu grupować elementy w widoku źródła.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>Grupowanie elementów w DataGrid przy użyciu kodu XAML

1. Utwórz <xref:System.Windows.Data.PropertyGroupDescription> , który określa właściwość do grupy przez. Można określić właściwości, w języku XAML, lub w kodzie.

   1. W języku XAML, ustaw <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na nazwę właściwości do grupowania.

   2. W kodzie należy przekazać nazwę właściwości do grupy przez konstruktora.

2. Dodaj <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> kolekcji.

3. Dodaj kolejne wystąpienia <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji można dodać więcej poziomy grupowania.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Aby usunąć grupę, Usuń <xref:System.Windows.Data.PropertyGroupDescription> z <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji.

5. Aby usunąć wszystkie grupy, należy wywołać <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> metody <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji.

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Gdy elementy są zgrupowane w <xref:System.Windows.Controls.DataGrid>, można zdefiniować <xref:System.Windows.Controls.GroupStyle> , który określa wygląd każdej grupy. Należy zastosować <xref:System.Windows.Controls.GroupStyle> przez dodanie go do <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> kolekcji elementu DataGrid. Jeśli masz wiele poziomów grupowania różnych stylów można zastosować do każdego poziomu grupy. Style są stosowane w kolejności, w którym jest zdefiniowany. Na przykład w przypadku definiowania dwa style, pierwszy będą stosowane do grup najwyższego poziomu wiersza. Drugi styl będą stosowane do wszystkich grup wierszy na drugim poziomie i niższych. <xref:System.Windows.FrameworkElement.DataContext%2A> z <xref:System.Windows.Controls.GroupStyle> jest <xref:System.Windows.Data.CollectionViewGroup> reprezentujący grupy.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Aby zmienić wygląd nagłówki grupy wierszy

1. Utwórz <xref:System.Windows.Controls.GroupStyle> która definiuje wygląd grupy wierszy.

2. Umieść <xref:System.Windows.Controls.GroupStyle> wewnątrz `<DataGrid.GroupStyle>` tagów.

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>Sortowanie elementów w DataGrid

Aby określić sposób sortowania elementów w <xref:System.Windows.Controls.DataGrid>, możesz użyć <xref:System.ComponentModel.SortDescription> typu, aby posortować elementy w widoku źródła.

### <a name="to-sort-items-in-a-datagrid"></a>Aby posortować elementy DataGrid

1. Utwórz <xref:System.ComponentModel.SortDescription> , który określa właściwość, aby posortować według. Można określić właściwości, w języku XAML, lub w kodzie.

    1. W języku XAML, ustaw <xref:System.ComponentModel.SortDescription.PropertyName%2A> do nazwy właściwości, aby posortować według.

    2. W kodzie, przekaż nazwę właściwości, aby posortować według i <xref:System.ComponentModel.ListSortDirection> do konstruktora.

2. Dodaj <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> kolekcji.

3. Dodaj kolejne wystąpienia <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> kolekcji, aby posortować według dodatkowych właściwości.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>Filtrowanie elementów w DataGrid

Aby filtrować elementy w <xref:System.Windows.Controls.DataGrid> przy użyciu <xref:System.Windows.Data.CollectionViewSource>, podaj filtrowania logikę programu obsługi <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> zdarzeń.

### <a name="to-filter-items-in-a-datagrid"></a>Aby filtrować elementy w DataGrid

1. Dodaj obsługę <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> zdarzeń.

2. W <xref:System.Windows.Data.CollectionViewSource.Filter> program obsługi zdarzeń, zdefiniuj logiki filtrowania.

    Za każdym razem, gdy widok jest odświeżany, będzie stosowany filtr.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Alternatywnie można filtrować elementy <xref:System.Windows.Controls.DataGrid> tworząc metodę, która zawiera wartości logiczne i ustawienia filtrowania <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> właściwości, aby zastosować filtr. Aby wyświetlić przykład tej metody, zobacz [filtrowanie danych w widoku](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano grupowania, sortowania i filtrowania `Task` danych w <xref:System.Windows.Data.CollectionViewSource> i wyświetlanie zgrupowane, posortowane i przefiltrowane `Task` danych w <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Data.CollectionViewSource> Jest używany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.DataGrid>. Grupowanie, sortowania i filtrowania są wykonywane na <xref:System.Windows.Data.CollectionViewSource> i są wyświetlane w <xref:System.Windows.Controls.DataGrid> interfejsu użytkownika.

Aby przetestować w tym przykładzie, należy dostosować nazwę DGGroupSortFilterExample do dopasowania nazwę projektu. Jeśli używasz programu Visual Basic, musisz zmienić nazwę klasy dla <xref:System.Windows.Window> do następującego.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Zobacz także

[Powiązanie danych — omówienie](../data/data-binding-overview.md)  
[Tworzenie i powiązywanie z ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)  
[Filtrowanie danych w widoku](../data/how-to-filter-data-in-a-view.md)  
[Sortowanie danych w widoku](../data/how-to-sort-data-in-a-view.md)  
[Sortowanie i grupowanie danych przy użyciu widoku w XAML](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  