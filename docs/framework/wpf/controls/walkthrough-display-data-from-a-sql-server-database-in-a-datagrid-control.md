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
ms.openlocfilehash: 1398d8408a0b85d6603d638312e92ba35c5e77d3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591036"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Przewodnik: wyświetlanie danych z SQL Serverj bazy danych w kontrolce DataGrid

W tym instruktażu pobierasz dane z bazy danych SQL Server i wyświetlają te dane w <xref:System.Windows.Controls.DataGrid> kontrolce. Za pomocą Entity Framework ADO.NET można tworzyć klasy jednostek, które reprezentują dane, i używać LINQ do zapisywania zapytania pobierającego określone dane z klasy jednostki.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Program Visual Studio.

- Dostęp do uruchomionego wystąpienia SQL Server lub SQL Server Express z dołączoną przykładową bazą danych AdventureWorks. Bazę danych AdventureWorks można pobrać z witryny [GitHub](https://github.com/Microsoft/sql-server-samples/releases).

## <a name="create-entity-classes"></a>Tworzenie klas jednostek

1. Utwórz nowy projekt aplikacji WPF w Visual Basic lub C#, a następnie nadaj mu nazwę `DataGridSQLExample` .

2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż polecenie **Dodaj**, a następnie wybierz pozycję **nowy element**.

     Zostanie wyświetlone okno dialogowe Dodawanie nowego elementu.

3. W okienku zainstalowane szablony wybierz pozycję **dane** , a następnie na liście szablony wybierz pozycję **ADO.NET Entity Data Model**.

     ![Szablon elementu Entity Data Model ADO.NET](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4. Nazwij plik `AdventureWorksModel.edmx` , a następnie kliknij przycisk **Dodaj**.

     Zostanie wyświetlony Kreator modelu Entity Data Model.

5. Na ekranie Wybierz zawartość modelu wybierz pozycję **Dr Designer z bazy danych** , a następnie kliknij przycisk **dalej**.

6. Na ekranie wybierz połączenie danych podaj połączenie z bazą danych AdventureWorksLT2008. Aby uzyskać więcej informacji, zobacz [okno dialogowe Wybieranie połączenia danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).

    Upewnij się, że nazwa jest `AdventureWorksLT2008Entities` i że zaznaczono pole wyboru **Zapisz ustawienia połączenia jednostki w pliku App. config jako** zaznaczone, a następnie kliknij przycisk **dalej**.

7. Na ekranie Wybierz obiekty bazy danych rozwiń węzeł tabele, a następnie wybierz tabele **produkt** i **ProductCategory** .

     Można generować klasy jednostek dla wszystkich tabel; Jednak w tym przykładzie pobierasz tylko dane z tych dwóch tabel.

     ![Wybierz produkt i ProductCategory z tabel](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")

8. Kliknij przycisk **Zakończ**.

     Jednostki Product i ProductCategory są wyświetlane w Entity Designer.

     ![Modele jednostek produktu i ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")

## <a name="retrieve-and-present-the-data"></a>Pobieranie i prezentowanie danych

1. Otwórz plik MainWindow. XAML.

2. Ustaw <xref:System.Windows.FrameworkElement.Width%2A> Właściwość na <xref:System.Windows.Window> 450.

3. W edytorze XAML Dodaj następujący <xref:System.Windows.Controls.DataGrid> tag między `<Grid>` tagami i, `</Grid>` Aby dodać <xref:System.Windows.Controls.DataGrid> nazwę `dataGrid1` .

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     ![Okno z elementem DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")

4. Wybierz pozycję <xref:System.Windows.Window> .

5. Za pomocą okno Właściwości lub edytora XAML Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Window> nazwanego `Window_Loaded` <xref:System.Windows.FrameworkElement.Loaded> zdarzenia. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie prostego programu obsługi zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

     Poniżej przedstawiono kod XAML dla MainWindow. XAML.

    > [!NOTE]
    > Jeśli używasz Visual Basic, w pierwszym wierszu MainWindow. XAML Zastąp ciąg `x:Class="DataGridSQLExample.MainWindow"` opcją `x:Class="MainWindow"` .

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. Otwórz plik związany z kodem (MainWindow. XAML. vb lub MainWindow.xaml.cs) dla <xref:System.Windows.Window> .

7. Dodaj następujący kod, aby pobrać tylko określone wartości z sprzężonych tabel i ustawić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Właściwość <xref:System.Windows.Controls.DataGrid> do wyników zapytania.

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. Uruchom przykład.

     Powinna zostać wyświetlona wartość <xref:System.Windows.Controls.DataGrid> , która wyświetla dane.

     ![DataGrid z danymi z bazy danych SQL](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.DataGrid>
