---
title: DataGrid — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- DataGrid
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- columns [Windows Forms], DataGrid control
- data sources [Windows Forms], binding to DataGrid control
- tables [Windows Forms], binding to DataGrid control
- DataGrid control [Windows Forms], data binding
- DataGrid control [Windows Forms], about DataGrid control
- parent tables in DataGrid control
- tables [Windows Forms], displaying in DataGrid control
- data grids [Windows Forms], about data grids
- multiple tables in DataGrid control
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- parent table navigation in DataGrid
- child tables [Windows Forms], dataGrid control
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
ms.openlocfilehash: 34bf38a59e4f2b1f975cf1836973d24d8a3bae32
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304741"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Formularze Windows <xref:System.Windows.Forms.DataGrid> kontrolka wyświetla dane w serii wierszy i kolumn. Najprostszym przypadku jest, gdy siatki jest powiązana ze źródłem danych za pomocą pojedynczej tabeli, która zawiera żadnych relacji. W takim przypadku dane są wyświetlane w prostych wierszy i kolumn, tak jak w arkuszu kalkulacyjnym. Aby uzyskać więcej informacji na temat powiązanie danych z innych kontrolek, zobacz [powiązanie danych oraz Windows Forms](../data-binding-and-windows-forms.md).  
  
 Jeśli <xref:System.Windows.Forms.DataGrid> jest powiązany z danymi z wielu powiązanych tabel i włączenie nawigacyjne siatki siatki będą wyświetlane ekspanderów znajdujących w każdym wierszu. Ekspander użytkownika umożliwia przeniesienie z tabeli nadrzędnej do tabeli podrzędnej. Kliknięcie węzła wyświetla tabeli podrzędnej oraz kliknięcie przycisku Wstecz oryginalnej tabeli nadrzędnej. W ten sposób Siatka wyświetla hierarchiczne relacje między tabelami.  
  
 Poniższy zrzut ekranu pokazuje, że elementem DataGrid powiązany z danymi z wielu tabel:  
  
 ![Aplikacja WinForms, wyświetlanie elementu DataGrid powiązany z danymi z wielu tabel.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)  
  
 <xref:System.Windows.Forms.DataGrid> Może zapewnić interfejsu użytkownika dla zestawu danych, nawigację między powiązanymi tabelami i rozbudowane, formatowania i edycji możliwości.  
  
 Wyświetlanie i manipulowanie danych są odrębne funkcje: Formant obsługuje interfejs użytkownika, natomiast aktualizacji danych są obsługiwane przez architekturę powiązanie danych formularzy Windows oraz przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych. W związku z tym wiele formantów powiązany z tego samego źródła danych zostanie zsynchronizowany.  
  
> [!NOTE]
>  Osoby zaznajomione z kontrolką DataGrid w Visual Basic 6.0 można zauważyć pewne istotne różnice w formularzach Windows Forms <xref:System.Windows.Forms.DataGrid> kontroli.  
  
 Siatka jest powiązany z <xref:System.Data.DataSet>, kolumny i wiersze są automatycznie tworzone, sformatowany i wypełnione. Aby uzyskać więcej informacji, zobacz [powiązanie danych i formularze Windows](../data-binding-and-windows-forms.md). Następujące Generowanie <xref:System.Windows.Forms.DataGrid> kontrolki, można dodać, usunąć, zmienić kolejność i formatować kolumnami i wierszami, zależnie od potrzeb.  
  
## <a name="binding-data-to-the-control"></a>Wiązanie danych do kontrolki  
 Aby uzyskać <xref:System.Windows.Forms.DataGrid> sterowania do pracy, należy można powiązać źródła danych przy użyciu <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości w czasie projektowania lub <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody w czasie wykonywania. Wskazuje to powiązanie <xref:System.Windows.Forms.DataGrid> do obiektu wystąpień źródła danych, takich jak <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>). <xref:System.Windows.Forms.DataGrid> Kontrolka pokazuje wyniki akcji, które są wykonywane na danych. Większość czynności dotyczące danych nie są wykonywane za pośrednictwem <xref:System.Windows.Forms.DataGrid> , ale zamiast tego w źródle danych.  
  
 Jeśli dane w zestawie danych powiązane są aktualizowane przy użyciu dowolnego mechanizmu <xref:System.Windows.Forms.DataGrid> kontroli zmiany zostały uwzględnione. Jeśli masz siatki danych i jego style tabeli i Style kolumn `ReadOnly` właściwością `false`, można zaktualizować dane w zestawie danych za pośrednictwem <xref:System.Windows.Forms.DataGrid> kontroli.  
  
 Tylko jedna tabela może być wyświetlana w <xref:System.Windows.Forms.DataGrid> w danym momencie. Jeśli nie zdefiniowano relacji nadrzędny podrzędny między tabelami, użytkownik może poruszać się między powiązanymi tabelami o wybranie tabeli, które mają być wyświetlane w <xref:System.Windows.Forms.DataGrid> kontroli. Aby uzyskać informacje na temat tworzenia powiązań <xref:System.Windows.Forms.DataGrid> kontrolę [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] źródła danych w czasie projektowania lub wykonywania, zobacz [jak: Powiązywanie formantu DataGrid formularzy Windows ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
 Źródła danych prawidłowe <xref:System.Windows.Forms.DataGrid> obejmują:  
  
-   <xref:System.Data.DataTable> class  
  
-   <xref:System.Data.DataView> class  
  
-   <xref:System.Data.DataSet> class  
  
-   <xref:System.Data.DataViewManager> class  
  
 Jeśli źródłem jest zestaw danych, zestaw danych może być w formie lub obiektu przekazanego do formularza przez usługi sieci Web XML. Możesz powiązać typizowany lub nietypizowany zestawów danych.  
  
 Możesz również powiązać <xref:System.Windows.Forms.DataGrid> kontroli do dodatkowych struktur, jeśli obiekty w strukturze, takich jak elementy w tablicy, udostępnianie właściwości publiczne. Siatki będą wyświetlane wszystkie właściwości publiczne elementy w strukturze. Na przykład, jeżeli powiążesz <xref:System.Windows.Forms.DataGrid> obiekty formantu do tablicy klienta siatki będą wyświetlane wszystkie publiczne właściwości tych obiektów klienta. W niektórych przypadkach oznacza to, że mimo że można powiązać struktury, wynikowa struktura powiązanej może nie mieć praktycznego zastosowania. Na przykład, można powiązać tablicy liczb całkowitych, ale ponieważ `Integer` typu danych nie obsługuje właściwości publicznej, siatki nie zawiera żadnych danych.  
  
 Następujące struktury można powiązać, jeśli ich elementy udostępnianie właściwości publicznej:  
  
-   Dowolny składnik, który implementuje <xref:System.Collections.IList> interfejsu. W tym tablice jednego wymiaru.  
  
-   Dowolny składnik, który implementuje <xref:System.ComponentModel.IListSource> interfejsu.  
  
-   Dowolny składnik, który implementuje <xref:System.ComponentModel.IBindingList> interfejsu.  
  
 Aby uzyskać więcej informacji na temat źródeł danych, zobacz [źródła danych obsługiwane przez formularze Windows](../data-sources-supported-by-windows-forms.md).  
  
## <a name="grid-display"></a>Wyświetl siatkę  
 Typowym zastosowaniem <xref:System.Windows.Forms.DataGrid> formantu są wyświetlane w pojedynczej tabeli danych z zestawu danych. Jednak kontrolki można również wyświetlić wiele tabel, łącznie z powiązanych tabel. Wyświetlanie siatki jest automatycznie dostosowywany zgodnie ze źródła danych. W poniższej tabeli przedstawiono, co jest wyświetlane dla różnych konfiguracji.  
  
|Zawartość zestawu danych|Co to jest wyświetlana|  
|--------------------------|-----------------------|  
|Pojedynczą tabelę.|Tabela jest wyświetlana na siatce.|  
|Wiele tabel.|Siatka można wyświetlić widoku drzewa, które użytkownicy mogą przejść do zlokalizowania w tabeli, które mają być wyświetlane treści.|  
|Wieloma powiązanymi tabelami.|Siatka można wyświetlić widok drzewa, aby wybrać tabele zawierające lub można określić, czy siatka wyświetlania tabeli nadrzędnej. Rekordy w tabeli nadrzędnej umożliwiają użytkownikom przechodzenie do podrzędnych względem wierszy.|  
  
> [!NOTE]
> Tabele w zestawie danych są powiązane, za pomocą <xref:System.Data.DataRelation>. Zobacz też [tworzenie relacji między zestawami danych](/visualstudio/data-tools/relationships-in-datasets).
  
 Gdy <xref:System.Windows.Forms.DataGrid> kontroli jest wyświetlanie tabeli i <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> właściwość jest ustawiona na `true`, dane mogą mieć zastosowanie, klikając nagłówki kolumn. Użytkownik może również dodawanie wierszy i edytować komórek.  
  
 Relacje między tabelami są widoczne dla użytkowników przy użyciu struktury nadrzędny/podrzędny nawigacji. Tabele są najwyższy poziom danych, a tabele podrzędne są tymi tabelami danych, które są uzyskiwane z poszczególnych ofert w tabelach nadrzędnej. Ekspanderów znajdujących są wyświetlane w każdym wierszu nadrzędnego, który zawiera tabeli podrzędnej. Kliknięcie przycisku ekspandera generuje listę łączy stylu sieci Web do tabel podrzędnych. Gdy użytkownik wybierze link, zostanie wyświetlona tabela podrzędna. Pokaż/Ukryj nadrzędnego wierszy ikonę (kliknięcie![Pokaż/Ukryj ikona wierszy nadrzędnego](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) będzie ukryć informacje dotyczące tabeli nadrzędnej lub spowodować, że pojawią się ponownie, jeśli użytkownik wcześniej została ukryta. Użytkownik może kliknąć przycisk Wstecz, aby powrócić do poprzednio czytanego tabeli.  
  
## <a name="columns-and-rows"></a>Kolumnami i wierszami  
 <xref:System.Windows.Forms.DataGrid> Składa się z kolekcją <xref:System.Windows.Forms.DataGridTableStyle> obiekty, które są zawarte w <xref:System.Windows.Forms.DataGrid> kontrolki <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości. Styl tabeli, który może zawierać zbiór <xref:System.Windows.Forms.DataGridColumnStyle> obiekty, które są zawarte w <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwość <xref:System.Windows.Forms.DataGridTableStyle>... Możesz edytować <xref:System.Windows.Forms.DataGrid.TableStyles%2A> i <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości przy użyciu edytory kolekcji udostępniane za pośrednictwem **właściwości** okna.  
  
 Wszelkie <xref:System.Windows.Forms.DataGridTableStyle> skojarzone z <xref:System.Windows.Forms.DataGrid> kontroli jest możliwy za pośrednictwem <xref:System.Windows.Forms.GridTableStylesCollection>. <xref:System.Windows.Forms.GridTableStylesCollection> Mogą być edytowane w Projektancie z <xref:System.Windows.Forms.DataGridTableStyle> Edytor kolekcji lub programowo za pomocą <xref:System.Windows.Forms.DataGrid> kontrolki <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości.  

 Poniższa ilustracja przedstawia obiektów uwzględnionych w formancie DataGrid:

 ![Diagram przedstawiający obiektów uwzględnionych w formancie DataGrid.](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)  
  
 Style tabeli i kolumn, które są synchronizowane z <xref:System.Data.DataTable> obiektów i <xref:System.Data.DataColumn> obiektów, ustawiając ich `MappingName` właściwości do odpowiednich <xref:System.Data.DataTable.TableName%2A> i <xref:System.Data.DataColumn.ColumnName%2A> właściwości. Gdy <xref:System.Windows.Forms.DataGridTableStyle> , nie ma kolumny style zostanie dodany do <xref:System.Windows.Forms.DataGrid> formant powiązany z poprawnego źródła danych i <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość stylu tabeli jest ustawiona na prawidłową <xref:System.Data.DataTable.TableName%2A> właściwość, zbiór <xref:System.Windows.Forms.DataGridColumnStyle> obiektów jest tworzony w tym Styl tabeli. Dla każdego <xref:System.Data.DataColumn> w <xref:System.Data.DataTable.Columns%2A> zbiór <xref:System.Data.DataTable>, odpowiedni <xref:System.Windows.Forms.DataGridColumnStyle> jest dodawany do <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection> jest dostępny za pośrednictwem <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwość <xref:System.Windows.Forms.DataGridTableStyle>. Kolumny można dodać lub usunąć z przy użyciu siatki <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> lub <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> metody <xref:System.Windows.Forms.GridColumnStylesCollection>. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie tabel i kolumn do Windows formantu DataGrid formularzy](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) i [jak: Usuwanie lub ukrywanie kolumn w Windows formantu DataGrid formularzy](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).  
  
 Kolekcja typów kolumn rozszerza <xref:System.Windows.Forms.DataGridColumnStyle> klasy za pomocą zaawansowanych formatowania i edycji możliwości. Wszystkie typy kolumn dziedziczyć <xref:System.Windows.Forms.DataGridColumnStyle> klasy bazowej. Klasa, która jest tworzona jest zależna od <xref:System.Data.DataColumn.DataType%2A> właściwość <xref:System.Data.DataColumn> z którego <xref:System.Web.UI.WebControls.DataGridColumn> opiera się. Na przykład <xref:System.Data.DataColumn> zawierający jego <xref:System.Data.DataColumn.DataType%2A> właściwością <xref:System.Boolean> zostaną skojarzone z <xref:System.Windows.Forms.DataGridBoolColumn>. W poniższej tabeli opisano każdy z tych typów kolumn.  
  
|Typ kolumny|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Akceptuje i wyświetla dane w postaci ciągów w układzie sformatowanym lub niesformatowanym. Możliwość edycji są takie same, jak do edycji danych w prostych <xref:System.Windows.Forms.TextBox>. Dziedziczy <xref:System.Windows.Forms.DataGridColumnStyle>.|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|Akceptuje i wyświetla `true`, `false`i wartości null. Dziedziczy <xref:System.Windows.Forms.DataGridColumnStyle>.|  
  
 Dwukrotne kliknięcie prawą krawędzią kolumna zmienia rozmiar kolumny, aby wyświetlić jego pełny podpis i możliwie najszerszej wpisu.  
  
## <a name="table-styles-and-column-styles"></a>Style tabeli i kolumn  
 Jak najszybciej po upewnieniu się, domyślnym formacie <xref:System.Windows.Forms.DataGrid> kontrolki, można dostosować kolory, które będą używane podczas niektórych tabel są wyświetlane w siatce danych.  
  
 Jest to osiągane przez utworzenie wystąpienia <xref:System.Windows.Forms.DataGridTableStyle> klasy. Style tabeli określić formatowanie określonych tabel, różne od domyślnego formatowania <xref:System.Windows.Forms.DataGrid> samej kontrolki. Każda tabela może mieć stylu tylko jedną tabelę dla niej zdefiniowane w danym momencie.  
  
 Czasami chcesz różni się od pozostałych kolumn w tabeli danych Obejrzyj określonej kolumny. Można utworzyć dostosowany zestaw Style kolumn przy użyciu <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości.  
  
 Style kolumn odnoszą się do kolumn w zestawie danych, tak samo, jak style tabeli są powiązane z tabelami danych. Tak, jak każda tabela może mieć tylko jedną styl tabeli zdefiniowano dla niego naraz, więc zbyt można każda kolumna tylko jeden styl do kolumny zdefiniowano, w stylu określonej tabeli. Ta relacja jest zdefiniowany w tej kolumnie <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> właściwości.  
  
 Jeśli utworzono styl tabeli bez Style kolumn, które dodano do niego, Visual Studio doda domyślne style kolumn podczas tworzenia formularza i siatki w czasie wykonywania. Jednak jeśli masz utworzony styl tabeli i do niej dodać wszystkie style kolumn, Visual Studio nie utworzy wszystkie style kolumn. Ponadto należy zdefiniować style kolumn i przypisać je o nazwie mapowania, aby mieć kolumn, które mają być wyświetlane w siatce.  
  
 Należy określić kolumny, które znajdują się w siatce danych, przypisując im styl kolumny, a żaden styl kolumna została przypisana do kolumny, dlatego może zawierać kolumn danych w zestawie danych, które nie są wyświetlane w siatce. Jednak ponieważ ta kolumna danych jest uwzględniony w zestawie danych, programowo edytować dane, które nie są wyświetlane.  
  
> [!NOTE]
>  Ogólnie rzecz biorąc Utwórz style kolumn i dodać je do kolekcji Style kolumn przed dodaniem style tabeli do kolekcji style tabeli. Po dodaniu styl pustej tabeli do kolekcji Style kolumn są generowane automatycznie dla Ciebie. W związku z tym, zostanie zgłoszony wyjątek, Jeśli spróbujesz dodać nowe style kolumn ze zduplikowanymi <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> wartości do kolekcji Style kolumn.  
>   
>  Czasami można dostosować tylko jedną kolumnę między wiele kolumn; na przykład zestaw danych zawiera kolumny 50 i chcesz tylko 49 z nich. W tym przypadku jest łatwiejsze zaimportować wszystkie kolumny 50 i programowo usunąć jedno zamiast programowe Dodawanie każdego 49 poszczególnych kolumn ma.  
  
## <a name="formatting"></a>Formatowanie  
 Formatowanie, które mogą być stosowane do <xref:System.Windows.Forms.DataGrid> kontroli zawiera style obramowania, style linii siatki, czcionki, właściwości podpisu, wyrównanie danych i alternatywnych kolory tła między wierszami. Aby uzyskać więcej informacji, zobacz [jak: Formatowanie kontrolki DataGrid formularzy Windows Forms](how-to-format-the-windows-forms-datagrid-control.md).  
  
## <a name="events"></a>Zdarzenia  
 Oprócz typowe kontrolować zdarzenia takie jak <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>, i <xref:System.Windows.Forms.DataGrid.Scroll>, <xref:System.Windows.Forms.DataGrid> kontrolka obsługuje zdarzenia związane z edycji i nawigacji w obrębie siatki. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> Właściwość określa komórki, która jest zaznaczone. <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> Zdarzenie jest wywoływane, gdy użytkownik przechodzi do nowej komórki. Gdy użytkownik przechodzi do nowej tabeli za pomocą relacji nadrzędny/podrzędny <xref:System.Windows.Forms.DataGrid.Navigate> zdarzenie jest wywoływane. <xref:System.Windows.Forms.DataGrid.BackButtonClick> Zdarzenie jest wywoływane, gdy użytkownik kliknie przycisk Wstecz, gdy użytkownik przegląda tabeli podrzędnej i <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> zdarzenie jest wywoływane po kliknięciu ikonę Pokaż/Ukryj nadrzędnego wierszy.  
  
## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy systemu Windows](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy systemu Windows](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Instrukcje: format kontrolki DataGrid formularzy systemu Windows](how-to-format-the-windows-forms-datagrid-control.md)
