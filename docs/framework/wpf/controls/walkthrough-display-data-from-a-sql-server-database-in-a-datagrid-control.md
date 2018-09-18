---
title: 'Wskazówki: Wyświetlanie danych z serwera bazy danych SQL w formancie DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: dba2ec98b25c9c65a795c462b18504a799df04bc
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972270"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Wskazówki: Wyświetlanie danych z serwera bazy danych SQL w formancie DataGrid
W tym przewodniku możesz pobierać dane z bazy danych programu SQL Server i wyświetlić te dane w <xref:System.Windows.Controls.DataGrid> kontroli. ADO.NET Entity Framework umożliwia tworzenie klas jednostek, które reprezentują dane, a następnie napisz zapytanie, które pobiera określone dane z klasą jednostki za pomocą LINQ.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
-   Dostęp do uruchomionego wystąpienia programu SQL Server lub SQL Server Express, który zawiera przykładową bazę danych AdventureWorks podłączone do niego. Możesz pobrać bazy danych AdventureWorks z [GitHub](https://github.com/Microsoft/sql-server-samples/releases).  
  
### <a name="to-create-entity-classes"></a>Do tworzenia klas jednostek  
  
1.  Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub C# i nadaj mu nazwę `DataGridSQLExample`.  
  
2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż opcję **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
     Zostanie wyświetlone okno dialogowe Dodaj nowy element.  
  
3.  W okienku zainstalowane szablony zaznacz **danych** i na liście szablonów wybierz **ADO.NET Entity Data Model**.  
  
     ![Wybierz Model danych jednostki ADO.NET](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")  
  
4.  Nadaj plikowi nazwę `AdventureWorksModel.edmx` a następnie kliknij przycisk **Dodaj**.  
  
     Zostanie wyświetlony Kreator modelu Entity Data Model.  
  
5.  Na ekranie Wybierz zawartość modelu wybierz **Generuj z bazy danych** a następnie kliknij przycisk **dalej**.  
  
     ![Wybierz Generuj z bazy danych opcji](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")  
  
6.  Na ekranie Wybierz połączenie danych zapewnia połączenie z bazą danych AdventureWorksLT2008. Aby uzyskać więcej informacji, zobacz [wybierz Your Data połączenie — okno dialogowe](https://go.microsoft.com/fwlink/?LinkId=160190).  
  
     ![Zapewnia połączenie z bazą danych](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")  
  
7.  Upewnij się, że nazwa jest `AdventureWorksLT2008Entities` i **zapisywanie ustawień połączenia w pliku App.Config jako jednostki** pole wyboru jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
8.  Na ekranie Wybierz obiekty bazy danych, rozwiń węzeł tabele, a następnie wybierz **produktu** i **ProductCategory** tabel.  
  
     Można wygenerować klas jednostek dla wszystkich tabel. Jednak w tym przykładzie możesz tylko pobierać dane z tych dwóch tabel.  
  
     ![Wybierz z tabel Product i ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")  
  
9. Kliknij przycisk **Zakończ**.  
  
     W Projektancie jednostki wyświetlania obiektów Product i ProductCategory.  
  
     ![Modele jednostki Product i ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")  
  
### <a name="to-retrieve-and-present-the-data"></a>Aby pobrać i prezentowania danych  
  
1.  Otwórz plik MainWindow.xaml.  
  
2.  Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwość <xref:System.Windows.Window> do 450.  
  
3.  W edytorze XAML, Dodaj następujący kod <xref:System.Windows.Controls.DataGrid> tag między `<Grid>` i `</Grid>` tagi do dodania <xref:System.Windows.Controls.DataGrid> o nazwie `dataGrid1`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     ![Okno z DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")  
  
4.  Wybierz <xref:System.Windows.Window>.  
  
5.  Za pomocą okna właściwości lub Edytor XAML, Utwórz program obsługi zdarzeń dla <xref:System.Windows.Window> o nazwie `Window_Loaded` dla <xref:System.Windows.FrameworkElement.Loaded> zdarzeń. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie prostego programu obsługi zdarzeń](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).  
  
     Poniżej przedstawiono XAML dla pliku MainWindow.xaml.  
  
    > [!NOTE]
    >  Jeśli używasz języka Visual Basic w pierwszym wierszu pliku MainWindow.xaml, Zastąp `x:Class="DataGridSQLExample.MainWindow"` z `x:Class="MainWindow"`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  Otwórz plik związany z kodem (pliku MainWindow.xaml.vb lub MainWindow.xaml.cs) dla <xref:System.Windows.Window>.  
  
7.  Dodaj następujący kod, aby pobrać tylko określone wartości z połączonych tabel i ustawić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.DataGrid> do wyników zapytania.  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  Uruchom przykład.  
  
     Powinien zostać wyświetlony <xref:System.Windows.Controls.DataGrid> wyświetlającą dane.  
  
     ![DataGrid — przy użyciu danych z bazy danych SQL](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")  
  
## <a name="next-steps"></a>Następne kroki  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.DataGrid>  
 [Jak I: rozpocząć korzystanie z programu Entity Framework w aplikacjach WPF?](https://go.microsoft.com/fwlink/?LinkId=159868)
