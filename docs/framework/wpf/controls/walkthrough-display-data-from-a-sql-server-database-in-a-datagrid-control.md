---
title: 'Przewodnik: wyświetlanie danych z serwera bazy danych SQL w kontrolce DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 274ec2e8ef16190da53061bb197bc3b1a1fadcf8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336112"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Przewodnik: Wyświetlanie danych z bazy danych programu SQL Server w formancie DataGrid

W tym przewodniku możesz pobierać dane z bazy danych programu SQL Server i wyświetlić te dane w <xref:System.Windows.Controls.DataGrid> kontroli. ADO.NET Entity Framework umożliwia tworzenie klas jednostek, które reprezentują dane, a następnie napisz zapytanie, które pobiera określone dane z klasą jednostki za pomocą LINQ.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   Program Visual Studio.

-   Dostęp do uruchomionego wystąpienia programu SQL Server lub SQL Server Express, który zawiera przykładową bazę danych AdventureWorks podłączone do niego. Możesz pobrać bazy danych AdventureWorks z [GitHub](https://github.com/Microsoft/sql-server-samples/releases).

## <a name="create-entity-classes"></a>Tworzenie klas jednostek

1. Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub C# i nadaj mu nazwę `DataGridSQLExample`.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż opcję **Dodaj**, a następnie wybierz pozycję **nowy element**.

     Zostanie wyświetlone okno dialogowe Dodaj nowy element.

3. W okienku zainstalowane szablony zaznacz **danych** i na liście szablonów wybierz **ADO.NET Entity Data Model**.

     ![Szablon elementu modelu Entity Data Model ADO.NET](../../wcf/feature-details/./media/ado-net-entity-data-model-item-template.png)

4. Nadaj plikowi nazwę `AdventureWorksModel.edmx` a następnie kliknij przycisk **Dodaj**.

     Zostanie wyświetlony Kreator modelu Entity Data Model.

5. Na ekranie Wybierz zawartość modelu wybierz **projektancie platformy EF z bazy danych** a następnie kliknij przycisk **dalej**.

6. Na ekranie Wybierz połączenie danych zapewnia połączenie z bazą danych AdventureWorksLT2008. Aby uzyskać więcej informacji, zobacz [wybierz Your Data połączenie — okno dialogowe](https://go.microsoft.com/fwlink/?LinkId=160190).

    Upewnij się, że nazwa jest `AdventureWorksLT2008Entities` i **zapisywanie ustawień połączenia w pliku App.Config jako jednostki** pole wyboru jest zaznaczone, a następnie kliknij przycisk **dalej**.

7. Na ekranie Wybierz obiekty bazy danych, rozwiń węzeł tabele, a następnie wybierz **produktu** i **ProductCategory** tabel.

     Można wygenerować klas jednostek dla wszystkich tabel. Jednak w tym przykładzie możesz tylko pobierać dane z tych dwóch tabel.

     ![Wybierz z tabel Product i ProductCategory](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")

8. Kliknij przycisk **Zakończ**.

     W Projektancie jednostki wyświetlania obiektów Product i ProductCategory.

     ![Modele jednostki Product i ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")

## <a name="retrieve-and-present-the-data"></a>Pobieranie i prezentowanie danych

1. Otwórz plik MainWindow.xaml.

2. Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwość <xref:System.Windows.Window> do 450.

3. W edytorze XAML, Dodaj następujący kod <xref:System.Windows.Controls.DataGrid> tag między `<Grid>` i `</Grid>` tagi do dodania <xref:System.Windows.Controls.DataGrid> o nazwie `dataGrid1`.

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     ![Okno z DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")

4. Wybierz <xref:System.Windows.Window>.

5. Za pomocą okna właściwości lub Edytor XAML, Utwórz program obsługi zdarzeń dla <xref:System.Windows.Window> o nazwie `Window_Loaded` dla <xref:System.Windows.FrameworkElement.Loaded> zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: Utwórz procedurę obsługi zdarzenia prostego](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

     Poniżej przedstawiono XAML dla pliku MainWindow.xaml.

    > [!NOTE]
    > Jeśli używasz języka Visual Basic w pierwszym wierszu pliku MainWindow.xaml, Zastąp `x:Class="DataGridSQLExample.MainWindow"` z `x:Class="MainWindow"`.

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. Otwórz plik związany z kodem (pliku MainWindow.xaml.vb lub MainWindow.xaml.cs) dla <xref:System.Windows.Window>.

7. Dodaj następujący kod, aby pobrać tylko określone wartości z połączonych tabel i ustawić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.DataGrid> do wyników zapytania.

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. Uruchom przykład.

     Powinien zostać wyświetlony <xref:System.Windows.Controls.DataGrid> wyświetlającą dane.

     ![DataGrid — przy użyciu danych z bazy danych SQL](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DataGrid>
- [Jak mogę Rozpoczynanie pracy z platformą Entity Framework w aplikacjach WPF?](https://go.microsoft.com/fwlink/?LinkId=159868)