---
title: 'Instrukcje: grupowanie, sortowanie i filtrowanie danych w formancie DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 2632566b5b55ae641d2750e903bf94cdc681f8f8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460241"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Instrukcje: grupowanie, sortowanie i filtrowanie danych w formancie DataGrid

Często warto wyświetlać dane w <xref:System.Windows.Controls.DataGrid> na różne sposoby, grupując, sortując i filtrując dane. Aby grupować, sortować i filtrować dane w <xref:System.Windows.Controls.DataGrid>, należy powiązać ją z <xref:System.Windows.Data.CollectionView>, która obsługuje te funkcje. Następnie można korzystać z danych w <xref:System.Windows.Data.CollectionView> bez wpływu na bazowe dane źródłowe. Zmiany w widoku kolekcji zostaną odzwierciedlone w interfejsie użytkownika <xref:System.Windows.Controls.DataGrid>.

Klasa <xref:System.Windows.Data.CollectionView> udostępnia funkcje grupowania i sortowania dla źródła danych, które implementuje interfejs <xref:System.Collections.IEnumerable>. Klasa <xref:System.Windows.Data.CollectionViewSource> umożliwia ustawianie właściwości <xref:System.Windows.Data.CollectionView> z XAML.

W tym przykładzie kolekcja obiektów `Task` jest powiązana z <xref:System.Windows.Data.CollectionViewSource>. <xref:System.Windows.Data.CollectionViewSource> jest używany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid>. Grupowanie, sortowanie i filtrowanie są wykonywane na <xref:System.Windows.Data.CollectionViewSource> i są wyświetlane w interfejsie użytkownika <xref:System.Windows.Controls.DataGrid>.

![Grupowanie danych w elemencie DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Grupowanie danych w elemencie DataGrid

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Używanie elementu CollectionViewSource jako ItemsSource

Aby grupować, sortować i filtrować dane w kontrolce <xref:System.Windows.Controls.DataGrid>, należy powiązać <xref:System.Windows.Controls.DataGrid> z <xref:System.Windows.Data.CollectionView>, który obsługuje te funkcje. W tym przykładzie <xref:System.Windows.Controls.DataGrid> jest powiązany z <xref:System.Windows.Data.CollectionViewSource>, który udostępnia te funkcje dla <xref:System.Collections.Generic.List%601> `Task` obiektów.

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Aby powiązać element DataGrid z CollectionViewSource

1. Utwórz kolekcję danych, która implementuje interfejs <xref:System.Collections.IEnumerable>.

    Jeśli używasz <xref:System.Collections.Generic.List%601> do tworzenia kolekcji, należy utworzyć nową klasę, która dziedziczy po <xref:System.Collections.Generic.List%601> zamiast tworzenia wystąpienia <xref:System.Collections.Generic.List%601>. Dzięki temu można powiązać dane z kolekcją w języku XAML.

    > [!NOTE]
    > Obiekty w kolekcji muszą implementować <xref:System.ComponentModel.INotifyPropertyChanged> zmieniony interfejs i interfejs <xref:System.ComponentModel.IEditableObject>, aby <xref:System.Windows.Controls.DataGrid> prawidłowo reagować na zmiany i modyfikacje właściwości. Aby uzyskać więcej informacji, zobacz [implementacja powiadomienia o zmianie właściwości](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. W języku XAML Utwórz wystąpienie klasy kolekcji i ustaw [dyrektywę x:Key](../../xaml-services/x-key-directive.md).

3. W języku XAML Utwórz wystąpienie klasy <xref:System.Windows.Data.CollectionViewSource>, ustaw [dyrektywę x:Key](../../xaml-services/x-key-directive.md)i ustaw wystąpienie klasy kolekcji jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. Utwórz wystąpienie klasy <xref:System.Windows.Controls.DataGrid> i ustaw właściwość <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Data.CollectionViewSource>.

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Aby uzyskać dostęp do <xref:System.Windows.Data.CollectionViewSource> z kodu, użyj metody <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A>, aby uzyskać odwołanie do <xref:System.Windows.Data.CollectionViewSource>.

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>Grupowanie elementów w elemencie DataGrid

Aby określić sposób grupowania elementów w <xref:System.Windows.Controls.DataGrid>, należy użyć typu <xref:System.Windows.Data.PropertyGroupDescription> do grupowania elementów w widoku źródła.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>Aby pogrupować elementy w elemencie DataGrid przy użyciu języka XAML

1. Utwórz <xref:System.Windows.Data.PropertyGroupDescription>, który określa właściwość do grupowania. Możesz określić właściwość w języku XAML lub w kodzie.

   1. W języku XAML Ustaw <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na nazwę właściwości, według której ma zostać pogrupuj.

   2. W polu kod przekaż nazwę właściwości, aby zgrupować ją do konstruktora.

2. Dodaj <xref:System.Windows.Data.PropertyGroupDescription> do kolekcji <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType>.

3. Dodaj dodatkowe wystąpienia <xref:System.Windows.Data.PropertyGroupDescription> do kolekcji <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>, aby dodać więcej poziomów grupowania.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Aby usunąć grupę, Usuń <xref:System.Windows.Data.PropertyGroupDescription> z kolekcji <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>.

5. Aby usunąć wszystkie grupy, wywołaj metodę <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji.

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Gdy elementy są zgrupowane w <xref:System.Windows.Controls.DataGrid>, można zdefiniować <xref:System.Windows.Controls.GroupStyle>, który określa wygląd każdej grupy. <xref:System.Windows.Controls.GroupStyle> należy zastosować, dodając go do kolekcji <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> DataGrid. Jeśli masz wiele poziomów grupowania, możesz zastosować różne style do poszczególnych poziomów grup. Style są stosowane w kolejności, w jakiej zostały zdefiniowane. Na przykład, jeśli zdefiniujesz dwa style, pierwsza zostanie zastosowana do grup wierszy najwyższego poziomu. Drugi styl zostanie zastosowany do wszystkich grup wierszy na drugim poziomie i niższy. <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> jest <xref:System.Windows.Data.CollectionViewGroup>, którą reprezentuje grupa.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Aby zmienić wygląd nagłówków grup wierszy

1. Utwórz <xref:System.Windows.Controls.GroupStyle>, który definiuje wygląd grupy wierszy.

2. Umieść <xref:System.Windows.Controls.GroupStyle> wewnątrz tagów `<DataGrid.GroupStyle>`.

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>Sortowanie elementów w elemencie DataGrid

Aby określić sposób sortowania elementów w <xref:System.Windows.Controls.DataGrid>, należy użyć typu <xref:System.ComponentModel.SortDescription> do sortowania elementów w widoku źródła.

### <a name="to-sort-items-in-a-datagrid"></a>Aby posortować elementy w elemencie DataGrid

1. Utwórz <xref:System.ComponentModel.SortDescription>, który określa właściwość, według której ma zostać wykonane sortowanie. Możesz określić właściwość w języku XAML lub w kodzie.

    1. W języku XAML Ustaw <xref:System.ComponentModel.SortDescription.PropertyName%2A> na nazwę właściwości, według której ma zostać wykonane sortowanie.

    2. W polu kod przekaż nazwę właściwości, według której ma zostać wykonane sortowanie, oraz <xref:System.ComponentModel.ListSortDirection> do konstruktora.

2. Dodaj <xref:System.ComponentModel.SortDescription> do kolekcji <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType>.

3. Dodaj dodatkowe wystąpienia <xref:System.ComponentModel.SortDescription> do kolekcji <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A>, aby posortować według dodatkowych właściwości.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>Filtrowanie elementów w elemencie DataGrid

Aby odfiltrować elementy w <xref:System.Windows.Controls.DataGrid> przy użyciu <xref:System.Windows.Data.CollectionViewSource>, należy dostarczyć logiki filtrowania w programie obsługi dla zdarzenia <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>.

### <a name="to-filter-items-in-a-datagrid"></a>Aby odfiltrować elementy w elemencie DataGrid

1. Dodaj procedurę obsługi dla zdarzenia <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>.

2. W obsłudze zdarzeń <xref:System.Windows.Data.CollectionViewSource.Filter> Zdefiniuj logikę filtrowania.

    Filtr zostanie zastosowany za każdym razem, gdy widok zostanie odświeżony.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Alternatywnie można filtrować elementy w <xref:System.Windows.Controls.DataGrid>, tworząc metodę, która udostępnia logikę filtrowania i ustawiając właściwość <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType>, aby zastosować filtr. Aby zobaczyć przykład tej metody, zobacz [filtrowanie danych w widoku](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Przykład

Poniższy przykład demonstruje grupowanie, sortowanie i filtrowanie danych `Task` w <xref:System.Windows.Data.CollectionViewSource> i wyświetlanie pogrupowanych, posortowanych i filtrowanych `Task` danych w <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Data.CollectionViewSource> jest używany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid>. Grupowanie, sortowanie i filtrowanie są wykonywane na <xref:System.Windows.Data.CollectionViewSource> i są wyświetlane w interfejsie użytkownika <xref:System.Windows.Controls.DataGrid>.

Aby przetestować ten przykład, należy dostosować nazwę DGGroupSortFilterExample tak, aby odpowiadała nazwie projektu. Jeśli używasz Visual Basic, musisz zmienić nazwę klasy dla <xref:System.Windows.Window> na poniżej.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tworzenie i powiązywanie z ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [Filtrowanie danych w widoku](../data/how-to-filter-data-in-a-view.md)
- [Sortowanie danych w widoku](../data/how-to-sort-data-in-a-view.md)
- [Sortowanie i grupowanie danych przy użyciu widoku w XAML](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
