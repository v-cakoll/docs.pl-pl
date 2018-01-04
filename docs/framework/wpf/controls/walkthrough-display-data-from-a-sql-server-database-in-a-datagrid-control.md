---
title: "Wskazówki: Wyświetlanie danych z serwera bazy danych SQL w formancie DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c8ed596706c8d656842191262c25301db595ee3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Wskazówki: Wyświetlanie danych z serwera bazy danych SQL w formancie DataGrid
W tym przewodniku, pobieranie danych z bazy danych programu SQL Server i wyświetlić dane w <xref:System.Windows.Controls.DataGrid> formantu. ADO.NET Entity Framework umożliwia tworzenie klasy jednostki, które reprezentują dane i użyć LINQ, aby zapisać kwerendę, która pobiera określone dane z klasy jednostka.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].,  
  
-   Dostęp do działającego wystąpienia programu SQL Server lub SQL Server Express zawierający przykładową bazę danych AdventureWorks do niego dołączony. Możesz pobrać z bazy danych AdventureWorks z [GitHub](https://github.com/Microsoft/sql-server-samples/releases).  
  
### <a name="to-create-entity-classes"></a>Do tworzenia klas jednostki  
  
1.  Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub C# i nadaj mu nazwę `DataGridSQLExample`.  
  
2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż pozycję **Dodaj**, a następnie wybierz **nowy element**.  
  
     Zostanie wyświetlone okno dialogowe Dodaj nowy element.  
  
3.  Wybierz w okienku zainstalowane szablony **danych** i na liście szablonów wybierz **Tryb danych jednostki ADO.NET**l.  
  
     ![Wybierz modelu danych jednostki ADO.NET](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")  
  
4.  Nadaj nazwę plikowi `AdventureWorksModel.edmx` , a następnie kliknij przycisk **Dodaj**.  
  
     Zostanie wyświetlony Kreator modelu Entity Data Model.  
  
5.  Na ekranie Wybierz zawartość modelu wybierz **generowania z bazy danych** , a następnie kliknij przycisk **dalej**.  
  
     ![Generuj należy wybierać opcji bazy danych](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")  
  
6.  Na ekranie Wybierz połączenie danych Podaj połączenia z bazą danych AdventureWorksLT2008. Aby uzyskać więcej informacji, zobacz [wybierz Twoje dane okno dialogowe połączenia](http://go.microsoft.com/fwlink/?LinkId=160190).  
  
     ![Podaj połączenia z bazą danych](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")  
  
7.  Upewnij się, że nazwa jest `AdventureWorksLT2008Entities` i **Zapisz ustawienia połączenia w pliku App.Config jako jednostki** pole wyboru jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
8.  Na ekranie Wybierz obiekty bazy danych użytkownika, rozwiń węzeł tabele, a następnie wybierz **produktu** i **ProductCategory** tabel.  
  
     Można wygenerować klas jednostek dla wszystkich tabel. Jednak w tym przykładzie można tylko pobieranie danych z tych dwóch tabel.  
  
     ![Wybierz produkt i ProductCategory z tabel](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")  
  
9. Kliknij przycisk **Zakończ**.  
  
     Obiekty produktu i ProductCategory są wyświetlane w programie Entity Designer.  
  
     ![Modele jednostki produktu i ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")  
  
### <a name="to-retrieve-and-present-the-data"></a>Aby pobrać i przedstawiają dane  
  
1.  Otwórz plik MainWindow.xaml.  
  
2.  Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwość <xref:System.Windows.Window> do 450.  
  
3.  W edytorze XAML, Dodaj następujący <xref:System.Windows.Controls.DataGrid> tagu między `<Grid>` i `</Grid>` znaczniki, aby dodać <xref:System.Windows.Controls.DataGrid> o nazwie `dataGrid1`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     ![Okno z elementu DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")  
  
4.  Wybierz <xref:System.Windows.Window>.  
  
5.  Przy użyciu okna właściwości lub edytora XAML, utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Window> o nazwie `Window_Loaded` dla <xref:System.Windows.FrameworkElement.Loaded> zdarzeń. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie prostego obsługi zdarzeń](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).  
  
     Poniżej przedstawiono XAML MainWindow.xaml.  
  
    > [!NOTE]
    >  Jeśli korzystasz z języka Visual Basic w pierwszym wierszu MainWindow.xaml, Zastąp `x:Class="DataGridSQLExample.MainWindow"` z `x:Class="MainWindow"`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  Otwórz plik CodeBehind (MainWindow.xaml.vb lub MainWindow.xaml.cs) dla <xref:System.Windows.Window>.  
  
7.  Dodaj następujący kod, aby pobrać tylko określone wartości z połączonych tabel i ustawić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.DataGrid> do wyników zapytania.  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  Można uruchomić przykład.  
  
     Powinny pojawić się <xref:System.Windows.Controls.DataGrid> wyświetlający dane.  
  
     ![DataGrid z danymi z bazy danych SQL](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")  
  
## <a name="next-steps"></a>Następne kroki  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.DataGrid>  
 [Jak I: wprowadzenie do programu Entity Framework w aplikacjach WPF?](http://go.microsoft.com/fwlink/?LinkId=159868)
