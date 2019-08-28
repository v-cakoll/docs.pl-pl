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
ms.openlocfilehash: ce149ed25d3326daa9096596fe8d542a13759a96
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046216"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid — Informacje o formancie [Formularze systemu Windows]

> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Kontrolka <xref:System.Windows.Forms.DataGrid> Windows Forms wyświetla dane w serii wierszy i kolumn. Najprostszym przypadkiem jest powiązanie siatki ze źródłem danych z pojedynczą tabelą, która nie zawiera relacji. W takim przypadku dane pojawiają się w prostych wierszach i kolumnach, jak w arkuszu kalkulacyjnym. Aby uzyskać więcej informacji na temat powiązań danych z innymi kontrolkami, zobacz [powiązanie danych i Windows Forms](../data-binding-and-windows-forms.md).

<xref:System.Windows.Forms.DataGrid> Jeśli jest powiązany z danymi z wieloma powiązanymi tabelami, a w siatce zostanie włączona Nawigacja, w każdym wierszu zostanie wyświetlona tabela rozwijana. Przy użyciu ekspandera użytkownik może przenieść z tabeli nadrzędnej do tabeli podrzędnej. Kliknięcie węzła powoduje wyświetlenie tabeli podrzędnej, a kliknięcie przycisku Wstecz powoduje wyświetlenie oryginalnej tabeli nadrzędnej. W ten sposób Siatka wyświetla hierarchiczne relacje między tabelami.

Poniższy zrzut ekranu przedstawia element DataGrid powiązany z danymi z wieloma tabelami:

![Aplikacja WinForms pokazująca element DataGrid powiązany z danymi z wieloma tabelami.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)

<xref:System.Windows.Forms.DataGrid> Może zapewnić interfejs użytkownika dla zestawu danych, Nawigowanie między powiązanymi tabelami oraz zaawansowane funkcje formatowania i edycji.

Wyświetlanie i manipulowanie danymi są osobnymi funkcjami: Kontrolka obsługuje interfejs użytkownika, podczas gdy aktualizacje danych są obsługiwane przez Windows Forms architekturę powiązań danych i .NET Framework dostawców danych. W związku z tym wielokrotne kontrolki powiązane z tym samym źródłem danych pozostaną zsynchronizowane.

> [!NOTE]
> Jeśli znasz formant DataGrid w Visual Basic 6,0, znajdziesz znaczące różnice w kontrolce Windows Forms <xref:System.Windows.Forms.DataGrid> .

Gdy siatka jest powiązana z <xref:System.Data.DataSet>, kolumny i wiersze są automatycznie tworzone, formatowane i wypełniane. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych i Windows Forms](../data-binding-and-windows-forms.md). Po utworzeniu <xref:System.Windows.Forms.DataGrid> kontrolki można dodawać, usuwać, zmieniać kolejność i formatować kolumny i wiersze w zależności od potrzeb.

## <a name="binding-data-to-the-control"></a>Powiązywanie danych z kontrolką

Aby formant działał, należy powiązać ze źródłem danych <xref:System.Windows.Forms.DataGrid.DataSource%2A> przy użyciu właściwości i <xref:System.Windows.Forms.DataGrid.DataMember%2A> w czasie projektowania lub w <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodzie w czasie wykonywania. <xref:System.Windows.Forms.DataGrid> To powiązanie wskazuje <xref:System.Windows.Forms.DataGrid> obiekt do wystąpienia obiektu źródła danych, taki <xref:System.Data.DataSet> jak lub <xref:System.Data.DataTable>). <xref:System.Windows.Forms.DataGrid> Kontrolka pokazuje wyniki akcji wykonywanych na danych. Większość akcji specyficznych dla danych nie jest wykonywanych <xref:System.Windows.Forms.DataGrid> przez, ale zamiast za pomocą źródła danych.

Jeśli dane w powiązanym zestawie danych są aktualizowane za pomocą dowolnego mechanizmu <xref:System.Windows.Forms.DataGrid> , formant odzwierciedla zmiany. Jeśli do siatki danych i jego stylów tabeli i stylów kolumn ma `ReadOnly` `false`ustawioną właściwość, dane w zestawie danych <xref:System.Windows.Forms.DataGrid> można aktualizować za pomocą kontrolki.

W <xref:System.Windows.Forms.DataGrid> danej chwili może być pokazywana tylko jedna tabela. Jeśli relacja nadrzędny-podrzędny jest zdefiniowana między tabelami, użytkownik może przechodzić między powiązanymi tabelami, aby wybrać tabelę, która <xref:System.Windows.Forms.DataGrid> ma być wyświetlana w formancie. Aby uzyskać informacje na temat <xref:System.Windows.Forms.DataGrid> wiązania kontrolki ze źródłem danych ADO.NET w czasie projektowania lub czasie wykonywania, zobacz [How to: Powiąż formant DataGrid Windows Forms ze źródłem](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)danych.

Prawidłowe źródła danych dla <xref:System.Windows.Forms.DataGrid> dołączenia:

- <xref:System.Data.DataTable>określonej

- <xref:System.Data.DataView>określonej

- <xref:System.Data.DataSet>określonej

- <xref:System.Data.DataViewManager>określonej

Jeśli źródło jest zestawem danych, zestaw danych może być obiektem w formularzu lub obiektem przekazanym do formularza przez usługę sieci Web XML. Można powiązać z zestawami danych z wpisanymi lub nieokreślonymi typami.

Można również powiązać <xref:System.Windows.Forms.DataGrid> kontrolkę z dodatkowymi strukturami, jeśli obiekty w strukturze, takie jak elementy w tablicy, uwidaczniają właściwości publiczne. Siatka będzie wyświetlać wszystkie właściwości publiczne elementów w strukturze. Na przykład jeśli powiążesz <xref:System.Windows.Forms.DataGrid> formant z tablicą obiektów klienta, Siatka będzie wyświetlała wszystkie właściwości publiczne tych obiektów klienta. W niektórych przypadkach oznacza to, że chociaż można powiązać ze strukturą, powiązana struktura może nie mieć praktycznej aplikacji. Na przykład można powiązać z tablicą liczb całkowitych, ale ponieważ `Integer` typ danych nie obsługuje właściwości publicznej, siatka nie może wyświetlać żadnych danych.

Można powiązać z następującymi strukturami, jeśli ich elementy ujawniają właściwości publiczne:

- Dowolny składnik, który implementuje <xref:System.Collections.IList> interfejs. Obejmuje to tablice o pojedynczym wymiarze.

- Dowolny składnik, który implementuje <xref:System.ComponentModel.IListSource> interfejs.

- Dowolny składnik, który implementuje <xref:System.ComponentModel.IBindingList> interfejs.

 Aby uzyskać więcej informacji o możliwych źródłach danych, zobacz [źródła danych obsługiwane przez Windows Forms](../data-sources-supported-by-windows-forms.md).

## <a name="grid-display"></a>Wyświetlanie siatki

Typowym zastosowaniem <xref:System.Windows.Forms.DataGrid> formantu jest wyświetlenie pojedynczej tabeli danych z zestawu danych. Jednak formant może być również używany do wyświetlania wielu tabel, w tym powiązanych tabel. Wyświetlanie siatki jest dostosowywane automatycznie zgodnie ze źródłem danych. W poniższej tabeli pokazano, co jest wyświetlane w różnych konfiguracjach.

|Zawartość zestawu danych|Co jest wyświetlane|
|--------------------------|-----------------------|
|Pojedyncza tabela.|Tabela jest wyświetlana w siatce.|
|Wiele tabel.|Siatka może wyświetlić widok drzewa, który użytkownicy mogą nawigować, aby zlokalizować tabelę, która ma być wyświetlana.|
|Wiele powiązanych tabel.|Siatka może wyświetlić widok drzewa, w którym można wybrać tabele, lub określić, że siatka ma wyświetlać tabelę nadrzędną. Rekordy w tabeli nadrzędnej umożliwiają użytkownikom przechodzenie do powiązanych wierszy podrzędnych.|

> [!NOTE]
> Tabele w zestawie danych są powiązane przy użyciu <xref:System.Data.DataRelation>. Zobacz też temat [Tworzenie relacji między zestawami danych](/visualstudio/data-tools/relationships-in-datasets).

Gdy kontrolka Wyświetla tabelę, <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> a właściwość jest ustawiona na, dane `true`można dowiązać, klikając nagłówki kolumn. <xref:System.Windows.Forms.DataGrid> Użytkownik może również dodawać wiersze i edytować komórki.

Relacje między zestawem tabel są wyświetlane użytkownikom przy użyciu struktury nadrzędnej/podrzędnej nawigacji. Tabele nadrzędne są najwyższego poziomu danych, a tabele podrzędne są tabelami danych, które pochodzą z poszczególnych list w tabelach nadrzędnych. Elementy rozszerzające są wyświetlane w każdym wierszu nadrzędnym, który zawiera tabelę podrzędną. Kliknięcie ekspandera generuje listę linków przypominających sieć Web z tabelami podrzędnymi. Gdy użytkownik wybierze link, zostanie wyświetlona tabela podrzędna. Kliknij ikonę Pokaż/Ukryj wiersze nadrzędne (![Ikona Pokaż/Ukryj wiersze nadrzędne](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) ukrywa informacje o tabeli nadrzędnej lub powoduje, że zostanie ona ponownie wyświetlona, jeśli użytkownik wcześniej ją ukryć. Użytkownik może kliknąć przycisk Wstecz, aby przejść z powrotem do wcześniej wyświetlonej tabeli.

## <a name="columns-and-rows"></a>Kolumny i wiersze

Składa się z <xref:System.Windows.Forms.DataGridTableStyle> kolekcji obiektów <xref:System.Windows.Forms.DataGrid> , które są <xref:System.Windows.Forms.DataGrid.TableStyles%2A> zawarte we właściwości kontrolki. <xref:System.Windows.Forms.DataGrid> Styl tabeli może zawierać kolekcję <xref:System.Windows.Forms.DataGridColumnStyle> obiektów, które są zawarte <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> we właściwości <xref:System.Windows.Forms.DataGridTableStyle>... Właściwości <xref:System.Windows.Forms.DataGrid.TableStyles%2A> i <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> można edytować za pomocą edytorów kolekcji dostępnych za pośrednictwem okna **Właściwości** .

Wszystkie <xref:System.Windows.Forms.DataGridTableStyle> <xref:System.Windows.Forms.GridTableStylesCollection>skojarzone <xref:System.Windows.Forms.DataGrid> z formantami są dostępne za pomocą. Można edytować w projektancie <xref:System.Windows.Forms.DataGridTableStyle> z edytorem kolekcji lub <xref:System.Windows.Forms.DataGrid.TableStyles%2A> programowo za pomocą <xref:System.Windows.Forms.DataGrid> właściwości kontrolki. <xref:System.Windows.Forms.GridTableStylesCollection>

Na poniższej ilustracji przedstawiono obiekty zawarte w kontrolce DataGrid:

![Diagram przedstawiający obiekty zawarte w kontrolce DataGrid.](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)

Style tabeli i Style kolumn są synchronizowane z <xref:System.Data.DataTable> obiektami i <xref:System.Data.DataColumn> obiektami przez ustawienie ich `MappingName` właściwości na odpowiednie <xref:System.Data.DataTable.TableName%2A> i <xref:System.Data.DataColumn.ColumnName%2A> właściwości. <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridColumnStyle> <xref:System.Data.DataTable.TableName%2A> Gdy nie ma żadnych stylów kolumn do kontrolki powiązanej z prawidłowym źródłem danych i właściwość tego stylu tabeli jest ustawiona na prawidłową właściwość, kolekcja obiektów zostanie utworzona dla tego <xref:System.Windows.Forms.DataGridTableStyle> styl tabeli. Dla każdego <xref:System.Data.DataColumn> elementu znalezionego <xref:System.Data.DataTable.Columns%2A> w kolekcji <xref:System.Data.DataTable>, odpowiednie <xref:System.Windows.Forms.DataGridColumnStyle> jest dodawane do <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection>jest dostępny za pomocą <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości. <xref:System.Windows.Forms.DataGridTableStyle> Kolumny można dodawać lub usuwać z siatki przy użyciu <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> metody lub <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> w <xref:System.Windows.Forms.GridColumnStylesCollection>. Aby uzyskać więcej informacji, zobacz [jak: Dodaj tabele i kolumny do kontrolki](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) DataGrid Windows Forms i [instrukcje: Usuwanie lub ukrywanie kolumn w kontrolce](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)DataGrid Windows Forms.

Kolekcja typów kolumn rozszerza <xref:System.Windows.Forms.DataGridColumnStyle> klasę z rozbudowanymi możliwościami formatowania i edycji. Wszystkie typy kolumn dziedziczą z <xref:System.Windows.Forms.DataGridColumnStyle> klasy bazowej. Utworzona Klasa zależy <xref:System.Data.DataColumn.DataType%2A> od właściwości, <xref:System.Data.DataColumn> z której <xref:System.Web.UI.WebControls.DataGridColumn> bazuje. Na przykład, <xref:System.Data.DataColumn> która <xref:System.Data.DataColumn.DataType%2A> ma ustawioną właściwość na <xref:System.Boolean> , zostanie skojarzona z <xref:System.Windows.Forms.DataGridBoolColumn>. W poniższej tabeli opisano każdy z tych typów kolumn.

|Typ kolumny|Opis|
|-----------------|-----------------|
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Akceptuje i wyświetla dane jako ciągi sformatowane lub niesformatowane. Możliwości edytowania są takie same, jak w przypadku edytowania danych w prosty <xref:System.Windows.Forms.TextBox>sposób. Dziedziczy z <xref:System.Windows.Forms.DataGridColumnStyle>.|
|<xref:System.Windows.Forms.DataGridBoolColumn>|Akceptuje i wyświetla `true`wartości `false`, oraz wartość null. Dziedziczy z <xref:System.Windows.Forms.DataGridColumnStyle>.|

Dwukrotne kliknięcie prawej krawędzi kolumny zmienia rozmiar kolumny, aby wyświetlić jej pełny podpis i szerszy wpis.

## <a name="table-styles-and-column-styles"></a>Style tabeli i kolumny

Zaraz po ustaleniu domyślnego formatu <xref:System.Windows.Forms.DataGrid> formantu można dostosować kolory, które będą używane podczas wyświetlania niektórych tabel w obrębie siatki danych.

Jest to osiągane przez utworzenie wystąpień <xref:System.Windows.Forms.DataGridTableStyle> klasy. Style tabeli określają formatowanie określonych tabel, odrębnie od domyślnego formatowania <xref:System.Windows.Forms.DataGrid> formantu. Dla każdej tabeli można zdefiniować tylko jeden styl tabeli w danym momencie.

Czasami chcesz, aby określona kolumna wyglądała inaczej niż reszta kolumn określonej tabeli danych. Można utworzyć dostosowany zestaw stylów kolumn za pomocą <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości.

Style kolumn są powiązane z kolumnami w zestawie danych, podobnie jak style tabeli, są powiązane z tabelami danych. Podobnie jak w przypadku każdej tabeli zdefiniowano tylko jeden styl tabeli w danym momencie, tak więc dla każdej z kolumn można zdefiniować tylko jeden styl kolumny w określonym stylu tabeli. Ta relacja jest definiowana we <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> właściwości kolumny.

Jeśli utworzono styl tabeli bez dodanych stylów kolumn, program Visual Studio doda domyślne style kolumn, gdy formularz i siatka zostaną utworzone w czasie wykonywania. Jednak w przypadku utworzenia stylu tabeli i dodania do niego stylów kolumn, program Visual Studio nie będzie tworzyć żadnych stylów kolumn. Ponadto należy zdefiniować Style kolumn i przypisać je z nazwą mapowania, aby mieć kolumny, które mają być wyświetlane w siatce.

Ponieważ określasz, które kolumny są uwzględniane w siatce danych przez przypisanie im stylu kolumn i nie przypisano stylu kolumn do kolumn, można uwzględnić kolumny danych w zestawie danych, które nie są wyświetlane w siatce. Jednak ponieważ kolumna danych jest uwzględniona w zestawie danych, można programowo edytować dane, które nie są wyświetlane.

> [!NOTE]
> Ogólnie rzecz biorąc, Utwórz Style kolumn i Dodaj je do kolekcji Style kolumn przed dodaniem stylów tabeli do kolekcji Style tabeli. Po dodaniu pustego stylu tabeli do kolekcji, Style kolumn są generowane automatycznie. W związku z tym wyjątek zostanie wygenerowany, jeśli spróbujesz dodać nowe style kolumn ze zduplikowanymi <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> wartościami do kolekcji Style kolumn.
>
> Czasami warto tylko dostosować jedną kolumnę do wielu kolumn; na przykład zestaw danych zawiera 50 kolumn i chcesz tylko 49 z nich. W takim przypadku łatwiejszym rozwiązaniem jest zaimportowanie wszystkich kolumn 50 i programowe usuwanie ich, zamiast programowo dodać każdą z 49 poszczególnych kolumn.

## <a name="formatting"></a>Formatowanie

Formatowanie, które można zastosować do <xref:System.Windows.Forms.DataGrid> kontrolki, zawiera style obramowania, style linii siatki, czcionki, właściwości podpisów, wyrównanie danych i przemienne kolory tła między wierszami. Aby uzyskać więcej informacji, zobacz [jak: Sformatuj formant](how-to-format-the-windows-forms-datagrid-control.md)DataGrid Windows Forms.

## <a name="events"></a>Zdarzenia

Oprócz typowych zdarzeń kontroli, takich jak <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>, i <xref:System.Windows.Forms.DataGrid.Scroll>, <xref:System.Windows.Forms.DataGrid> formant obsługuje zdarzenia związane z edytowaniem i nawigacją w obrębie siatki. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> Właściwość określa, która komórka jest zaznaczona. <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> Zdarzenie jest zgłaszane, gdy użytkownik nawiguje do nowej komórki. Gdy użytkownik nawiguje do nowej tabeli za pomocą relacji nadrzędny/podrzędny, <xref:System.Windows.Forms.DataGrid.Navigate> zdarzenie jest zgłaszane. Zdarzenie jest zgłaszane, gdy użytkownik kliknie przycisk Wstecz, gdy użytkownik przegląda tabelę podrzędną, <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> a zdarzenie jest wywoływane po kliknięciu ikony Pokaż/Ukryj wiersze nadrzędne. <xref:System.Windows.Forms.DataGrid.BackButtonClick>

## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Instrukcje: Powiązywanie kontrolki DataGrid Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Instrukcje: Usuwanie lub ukrywanie kolumn w kontrolce DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Instrukcje: Formatowanie kontrolki DataGrid Windows Forms](how-to-format-the-windows-forms-datagrid-control.md)
