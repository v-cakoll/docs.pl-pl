---
title: 'Instrukcje: Sortowanie kolumny GridView po kliknięciu nagłówka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], GridView
- controls [WPF], ListView
- ListView controls [WPF], sorting GridView columns
- GridView controls [WPF], ListView control
ms.assetid: 4865d720-d147-40ed-83a7-af7587f8aad8
ms.openlocfilehash: 3438ab91045a144a7fa1d531e9d7d55ad30e89ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052030"
---
# <a name="how-to-sort-a-gridview-column-when-a-header-is-clicked"></a><span data-ttu-id="1d956-102">Instrukcje: Sortowanie kolumny GridView po kliknięciu nagłówka</span><span class="sxs-lookup"><span data-stu-id="1d956-102">How to: Sort a GridView Column When a Header Is Clicked</span></span>

<span data-ttu-id="1d956-103">W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.ListView> formant, który implementuje <xref:System.Windows.Controls.GridView> wyświetlanie trybu i sortowania danych zawartości, gdy użytkownik kliknie nagłówek kolumny.</span><span class="sxs-lookup"><span data-stu-id="1d956-103">This example shows how to create a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView> view mode and sorts the data content when a user clicks a column header.</span></span>

## <a name="example"></a><span data-ttu-id="1d956-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d956-104">Example</span></span>

<span data-ttu-id="1d956-105">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GridView> z trzech kolumn, które należy powiązać <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, i <xref:System.DateTime.Day%2A>, właściwości <xref:System.DateTime> struktury.</span><span class="sxs-lookup"><span data-stu-id="1d956-105">The following example defines a <xref:System.Windows.Controls.GridView> with three columns that bind to the <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>, properties of the <xref:System.DateTime> structure.</span></span>

```xaml
<GridView>
  <GridViewColumn DisplayMemberBinding="{Binding Path=Year}"
                  Header="Year"
                  Width="100"/>
  <GridViewColumn DisplayMemberBinding="{Binding Path=Month}"
                  Header="Month"
                  Width="100"/>
  <GridViewColumn DisplayMemberBinding="{Binding Path=Day}"
                  Header="Day"
                  Width="100"/>
</GridView>
```

<span data-ttu-id="1d956-106">W poniższym przykładzie pokazano elementów danych, które są zdefiniowane jako <xref:System.Collections.ArrayList> z <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1d956-106">The following example shows the data items that are defined as an <xref:System.Collections.ArrayList> of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="1d956-107"><xref:System.Collections.ArrayList> Jest zdefiniowany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1d956-107">The <xref:System.Collections.ArrayList> is defined as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> control.</span></span>

```xaml
<ListView.ItemsSource>
  <s:ArrayList>
    <p:DateTime>1993/1/1 12:22:02</p:DateTime>
    <p:DateTime>1993/1/2 13:2:01</p:DateTime>
    <p:DateTime>1997/1/3 2:1:6</p:DateTime>
    <p:DateTime>1997/1/4 13:6:55</p:DateTime>
    <p:DateTime>1999/2/1 12:22:02</p:DateTime>
    <p:DateTime>1998/2/2 13:2:01</p:DateTime>
    <p:DateTime>2000/2/3 2:1:6</p:DateTime>
    <p:DateTime>2002/2/4 13:6:55</p:DateTime>
    <p:DateTime>2001/3/1 12:22:02</p:DateTime>
    <p:DateTime>2006/3/2 13:2:01</p:DateTime>
    <p:DateTime>2004/3/3 2:1:6</p:DateTime>
    <p:DateTime>2004/3/4 13:6:55</p:DateTime>
  </s:ArrayList>
</ListView.ItemsSource>
```

<span data-ttu-id="1d956-108">`s` i `p` identyfikatorów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tagi odnoszą się do mapowania przestrzeni nazw, które są zdefiniowane w metadanych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony.</span><span class="sxs-lookup"><span data-stu-id="1d956-108">The `s` and `p` identifiers in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tags refer to namespace mappings that are defined in the metadata of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="1d956-109">Poniższy przykład przedstawia definicję metadanych.</span><span class="sxs-lookup"><span data-stu-id="1d956-109">The following example shows the metadata definition.</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="ListViewSort.Window1"
    xmlns:s="clr-namespace:System.Collections;assembly=mscorlib"
    xmlns:p="clr-namespace:System;assembly=mscorlib">
```

<span data-ttu-id="1d956-110">Aby posortować dane zgodnie z zawartością kolumny, w przykładzie zdefiniowano program obsługi zdarzeń, aby obsłużyć <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń, która występuje po naciśnięciu przycisku nagłówka kolumny.</span><span class="sxs-lookup"><span data-stu-id="1d956-110">To sort the data according to the contents of a column, the example defines an event handler to handle the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event that occurs when you press the column header button.</span></span> <span data-ttu-id="1d956-111">Poniższy przykład pokazuje, jak określić program obsługi zdarzeń dla <xref:System.Windows.Controls.GridViewColumnHeader> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1d956-111">The following example shows how to specify an event handler for the <xref:System.Windows.Controls.GridViewColumnHeader> control.</span></span>

```xaml
<ListView x:Name='lv' Height="150" HorizontalAlignment="Center"
  VerticalAlignment="Center"
  GridViewColumnHeader.Click="GridViewColumnHeaderClickedHandler"
 >
```

<span data-ttu-id="1d956-112">W przykładzie zdefiniowano program obsługi zdarzeń, tak aby kierunek sortowania zmienia się między kolejności rosnącej i malejącej każdym naciśnięciu przycisku nagłówek kolumny.</span><span class="sxs-lookup"><span data-stu-id="1d956-112">The example defines the event handler so that the sort direction changes between ascending order and descending order each time you press the column header button.</span></span> <span data-ttu-id="1d956-113">Poniższy przykład pokazuje programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1d956-113">The following example shows the event handler.</span></span>

```csharp
public partial class Window1 : Window
{
    public Window1()
    {
        InitializeComponent();
    }

    GridViewColumnHeader _lastHeaderClicked = null;
    ListSortDirection _lastDirection = ListSortDirection.Ascending;

    void GridViewColumnHeaderClickedHandler(object sender,
                                            RoutedEventArgs e)
    {
        var headerClicked = e.OriginalSource as GridViewColumnHeader;
        ListSortDirection direction;

        if (headerClicked != null)
        {
            if (headerClicked.Role != GridViewColumnHeaderRole.Padding)
            {
                if (headerClicked != _lastHeaderClicked)
                {
                    direction = ListSortDirection.Ascending;
                }
                else
                {
                    if (_lastDirection == ListSortDirection.Ascending)
                    {
                        direction = ListSortDirection.Descending;
                    }
                    else
                    {
                        direction = ListSortDirection.Ascending;
                    }
                }

                var columnBinding = headerClicked.Column.DisplayMemberBinding as Binding;
                var sortBy = columnBinding?.Path.Path ?? headerClicked.Column.Header as string;

                Sort(sortBy, direction);

                if (direction == ListSortDirection.Ascending)
                {
                    headerClicked.Column.HeaderTemplate =
                      Resources["HeaderTemplateArrowUp"] as DataTemplate;
                }
                else
                {
                    headerClicked.Column.HeaderTemplate =
                      Resources["HeaderTemplateArrowDown"] as DataTemplate;
                }

                // Remove arrow from previously sorted header
                if (_lastHeaderClicked != null && _lastHeaderClicked != headerClicked)
                {
                    _lastHeaderClicked.Column.HeaderTemplate = null;
                }

                _lastHeaderClicked = headerClicked;
                _lastDirection = direction;
            }
        }
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Public Sub New()
        InitializeComponent()
    End Sub

    Private _lastHeaderClicked As GridViewColumnHeader = Nothing
    Private _lastDirection As ListSortDirection = ListSortDirection.Ascending

    Private Sub GridViewColumnHeaderClickedHandler(ByVal sender As Object, ByVal e As RoutedEventArgs)
        Dim headerClicked = TryCast(e.OriginalSource, GridViewColumnHeader)
        Dim direction As ListSortDirection

        If headerClicked IsNot Nothing Then
            If headerClicked.Role <> GridViewColumnHeaderRole.Padding Then
                If headerClicked IsNot _lastHeaderClicked Then
                    direction = ListSortDirection.Ascending
                Else
                    If _lastDirection = ListSortDirection.Ascending Then
                        direction = ListSortDirection.Descending
                    Else
                        direction = ListSortDirection.Ascending
                    End If
                End If

                Dim columnBinding = TryCast(headerClicked.Column.DisplayMemberBinding, Binding)
                Dim sortBy = If(columnBinding?.Path.Path, TryCast(headerClicked.Column.Header, String))

                Sort(sortBy, direction)

                If direction = ListSortDirection.Ascending Then
                    headerClicked.Column.HeaderTemplate = TryCast(Resources("HeaderTemplateArrowUp"), DataTemplate)
                Else
                    headerClicked.Column.HeaderTemplate = TryCast(Resources("HeaderTemplateArrowDown"), DataTemplate)
                End If

                ' Remove arrow from previously sorted header
                If _lastHeaderClicked IsNot Nothing AndAlso _lastHeaderClicked IsNot headerClicked Then
                    _lastHeaderClicked.Column.HeaderTemplate = Nothing
                End If

                _lastHeaderClicked = headerClicked
                _lastDirection = direction
            End If
        End If
    End Sub
End Class
```

<span data-ttu-id="1d956-114">Poniższy przykład przedstawia algorytm sortowania, która jest wywoływana przez program obsługi zdarzeń, aby posortować dane.</span><span class="sxs-lookup"><span data-stu-id="1d956-114">The following example shows the sorting algorithm that is called by the event handler to sort the data.</span></span> <span data-ttu-id="1d956-115">Sortowanie jest wykonywane przez utworzenie nowego <xref:System.ComponentModel.SortDescription> struktury.</span><span class="sxs-lookup"><span data-stu-id="1d956-115">The sort is performed by creating a new <xref:System.ComponentModel.SortDescription> structure.</span></span>

```csharp
private void Sort(string sortBy, ListSortDirection direction)
{
    ICollectionView dataView =
      CollectionViewSource.GetDefaultView(lv.ItemsSource);

    dataView.SortDescriptions.Clear();
    SortDescription sd = new SortDescription(sortBy, direction);
    dataView.SortDescriptions.Add(sd);
    dataView.Refresh();
}
```

```vb
Private Sub Sort(ByVal sortBy As String, ByVal direction As ListSortDirection)
    Dim dataView As ICollectionView = CollectionViewSource.GetDefaultView(lv.ItemsSource)

    dataView.SortDescriptions.Clear()
    Dim sd As New SortDescription(sortBy, direction)
    dataView.SortDescriptions.Add(sd)
    dataView.Refresh()
End Sub
```

## <a name="see-also"></a><span data-ttu-id="1d956-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d956-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="1d956-117">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="1d956-117">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="1d956-118">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="1d956-118">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="1d956-119">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1d956-119">How-to Topics</span></span>](listview-how-to-topics.md)
