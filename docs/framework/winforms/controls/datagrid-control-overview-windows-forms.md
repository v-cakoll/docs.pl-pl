---
title: DataGrid — Informacje o formancie
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
ms.openlocfilehash: df559926dbc9141276f0a03deb99e340fd7212da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742566"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid — Informacje o formancie [Formularze systemu Windows]

> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Kontrolka <xref:System.Windows.Forms.DataGrid> Windows Forms wyświetla dane w serii wierszy i kolumn. Najprostszym przypadkiem jest powiązanie siatki ze źródłem danych z pojedynczą tabelą, która nie zawiera relacji. W takim przypadku dane pojawiają się w prostych wierszach i kolumnach, jak w arkuszu kalkulacyjnym. Aby uzyskać więcej informacji na temat powiązań danych z innymi kontrolkami, zobacz [powiązanie danych i Windows Forms](../data-binding-and-windows-forms.md).

Jeśli <xref:System.Windows.Forms.DataGrid> jest powiązany z danymi z wieloma powiązanymi tabelami, a w siatce zostanie włączona Nawigacja, w każdym wierszu zostanie wyświetlona tabela rozwijana. Przy użyciu ekspandera użytkownik może przenieść z tabeli nadrzędnej do tabeli podrzędnej. Kliknięcie węzła powoduje wyświetlenie tabeli podrzędnej, a kliknięcie przycisku Wstecz powoduje wyświetlenie oryginalnej tabeli nadrzędnej. W ten sposób Siatka wyświetla hierarchiczne relacje między tabelami.

Poniższy zrzut ekranu przedstawia element DataGrid powiązany z danymi z wieloma tabelami:

![Aplikacja WinForms pokazująca element DataGrid powiązany z danymi z wieloma tabelami.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)

<xref:System.Windows.Forms.DataGrid> może zapewnić interfejs użytkownika dla zestawu danych, Nawigowanie między powiązanymi tabelami oraz zaawansowane funkcje formatowania i edycji.

Wyświetlanie i manipulowanie danymi są osobnymi funkcjami: formant obsługuje interfejs użytkownika, podczas gdy aktualizacje danych są obsługiwane przez Windows Forms architekturę powiązań danych i .NET Framework dostawców danych. W związku z tym wielokrotne kontrolki powiązane z tym samym źródłem danych pozostaną zsynchronizowane.

> [!NOTE]
> Jeśli znasz formant DataGrid w Visual Basic 6,0, znajdziesz znaczące różnice w kontroli <xref:System.Windows.Forms.DataGrid> Windows Forms.

Gdy siatka jest powiązana z <xref:System.Data.DataSet>, kolumny i wiersze są automatycznie tworzone, formatowane i wypełniane. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych i Windows Forms](../data-binding-and-windows-forms.md). Po utworzeniu kontrolki <xref:System.Windows.Forms.DataGrid> można dodawać, usuwać, zmieniać kolejność i formatować kolumny i wiersze w zależności od potrzeb.

## <a name="binding-data-to-the-control"></a>Powiązywanie danych z kontrolką

Aby formant <xref:System.Windows.Forms.DataGrid> działał, należy powiązać ze źródłem danych przy użyciu właściwości <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> w czasie projektowania lub w metodzie <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> w czasie wykonywania. To powiązanie wskazuje <xref:System.Windows.Forms.DataGrid> do obiektu źródła danych, takiego jak <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>). Kontrolka <xref:System.Windows.Forms.DataGrid> pokazuje wyniki akcji wykonywanych na danych. Większość działań specyficznych dla danych nie jest przeprowadzana za pomocą <xref:System.Windows.Forms.DataGrid>, ale zamiast za pomocą źródła danych.

Jeśli dane w powiązanym zestawie danych są aktualizowane za pomocą dowolnego mechanizmu, formant <xref:System.Windows.Forms.DataGrid> odzwierciedla zmiany. Jeśli siatka danych i jego Style tabeli i kolumny mają ustawioną `ReadOnly` Właściwość `false`, dane w zestawie danych można aktualizować za pomocą kontrolki <xref:System.Windows.Forms.DataGrid>.

W <xref:System.Windows.Forms.DataGrid> można jednocześnie wyświetlić tylko jedną tabelę. Jeśli relacja nadrzędny-podrzędny jest zdefiniowana między tabelami, użytkownik może przechodzić między powiązanymi tabelami, aby wybrać tabelę, która ma być wyświetlana w kontrolce <xref:System.Windows.Forms.DataGrid>. Aby uzyskać informacje o powiązaniu formantu <xref:System.Windows.Forms.DataGrid> ze źródłem danych ADO.NET w czasie projektowania lub czasie wykonywania, zobacz [jak to zrobić: powiązać formant DataGrid Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

Prawidłowe źródła danych dla <xref:System.Windows.Forms.DataGrid> obejmują:

- Klasa <xref:System.Data.DataTable>

- Klasa <xref:System.Data.DataView>

- Klasa <xref:System.Data.DataSet>

- Klasa <xref:System.Data.DataViewManager>

Jeśli źródło jest zestawem danych, zestaw danych może być obiektem w formularzu lub obiektem przekazanym do formularza przez usługę sieci Web XML. Można powiązać z zestawami danych z wpisanymi lub nieokreślonymi typami.

Można również powiązać formant <xref:System.Windows.Forms.DataGrid> z dodatkowymi strukturami, jeśli obiekty w strukturze, takie jak elementy w tablicy, uwidaczniają właściwości publiczne. Siatka będzie wyświetlać wszystkie właściwości publiczne elementów w strukturze. Na przykład jeśli powiążesz formant <xref:System.Windows.Forms.DataGrid> z tablicą obiektów klienta, Siatka będzie wyświetlała wszystkie właściwości publiczne tych obiektów klienta. W niektórych przypadkach oznacza to, że chociaż można powiązać ze strukturą, powiązana struktura może nie mieć praktycznej aplikacji. Na przykład można powiązać z tablicą liczb całkowitych, ale ponieważ typ danych `Integer` nie obsługuje właściwości publicznej, siatka nie może wyświetlić żadnych danych.

Można powiązać z następującymi strukturami, jeśli ich elementy ujawniają właściwości publiczne:

- Dowolny składnik implementujący interfejs <xref:System.Collections.IList>. Obejmuje to tablice o pojedynczym wymiarze.

- Dowolny składnik implementujący interfejs <xref:System.ComponentModel.IListSource>.

- Dowolny składnik implementujący interfejs <xref:System.ComponentModel.IBindingList>.

 Aby uzyskać więcej informacji o możliwych źródłach danych, zobacz [źródła danych obsługiwane przez Windows Forms](../data-sources-supported-by-windows-forms.md).

## <a name="grid-display"></a>Wyświetlanie siatki

Typowym zastosowaniem formantu <xref:System.Windows.Forms.DataGrid> jest wyświetlenie pojedynczej tabeli danych z zestawu danych. Jednak formant może być również używany do wyświetlania wielu tabel, w tym powiązanych tabel. Wyświetlanie siatki jest dostosowywane automatycznie zgodnie ze źródłem danych. W poniższej tabeli pokazano, co jest wyświetlane w różnych konfiguracjach.

|Zawartość zestawu danych|Co jest wyświetlane|
|--------------------------|-----------------------|
|Pojedyncza tabela.|Tabela jest wyświetlana w siatce.|
|Wiele tabel.|Siatka może wyświetlić widok drzewa, który użytkownicy mogą nawigować, aby zlokalizować tabelę, która ma być wyświetlana.|
|Wiele powiązanych tabel.|Siatka może wyświetlić widok drzewa, w którym można wybrać tabele, lub określić, że siatka ma wyświetlać tabelę nadrzędną. Rekordy w tabeli nadrzędnej umożliwiają użytkownikom przechodzenie do powiązanych wierszy podrzędnych.|

> [!NOTE]
> Tabele w zestawie danych są powiązane z użyciem <xref:System.Data.DataRelation>. Zobacz też temat [Tworzenie relacji między zestawami danych](/visualstudio/data-tools/relationships-in-datasets).

Gdy kontrolka <xref:System.Windows.Forms.DataGrid> Wyświetla tabelę, a właściwość <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> jest ustawiona na `true`, dane można dowiązać, klikając nagłówki kolumn. Użytkownik może również dodawać wiersze i edytować komórki.

Relacje między zestawem tabel są wyświetlane użytkownikom przy użyciu struktury nadrzędnej/podrzędnej nawigacji. Tabele nadrzędne są najwyższego poziomu danych, a tabele podrzędne są tabelami danych, które pochodzą z poszczególnych list w tabelach nadrzędnych. Elementy rozszerzające są wyświetlane w każdym wierszu nadrzędnym, który zawiera tabelę podrzędną. Kliknięcie ekspandera generuje listę linków przypominających sieć Web z tabelami podrzędnymi. Gdy użytkownik wybierze link, zostanie wyświetlona tabela podrzędna. Kliknij ikonę Pokaż/Ukryj wiersze nadrzędne (![Ikona Pokaż/Ukryj wiersze nadrzędne](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) ukrywa informacje o tabeli nadrzędnej lub powoduje, że zostanie ona ponownie wyświetlona, jeśli użytkownik wcześniej ją ukryć. Użytkownik może kliknąć przycisk Wstecz, aby przejść z powrotem do wcześniej wyświetlonej tabeli.

## <a name="columns-and-rows"></a>Kolumny i wiersze

<xref:System.Windows.Forms.DataGrid> składa się z kolekcji obiektów <xref:System.Windows.Forms.DataGridTableStyle>, które są zawarte we właściwości <xref:System.Windows.Forms.DataGrid.TableStyles%2A> kontrolki <xref:System.Windows.Forms.DataGrid>. Styl tabeli może zawierać kolekcję <xref:System.Windows.Forms.DataGridColumnStyle> obiektów, które są zawarte we właściwości <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> <xref:System.Windows.Forms.DataGridTableStyle>. Można edytować <xref:System.Windows.Forms.DataGrid.TableStyles%2A> i <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości przy użyciu edytorów kolekcji dostępnych za pośrednictwem okna **Właściwości** .

Do wszystkich <xref:System.Windows.Forms.DataGridTableStyle> skojarzonych z kontrolką <xref:System.Windows.Forms.DataGrid> można uzyskać dostęp za pomocą <xref:System.Windows.Forms.GridTableStylesCollection>. <xref:System.Windows.Forms.GridTableStylesCollection> można edytować w projektancie przy użyciu edytora kolekcji <xref:System.Windows.Forms.DataGridTableStyle> lub programowo poprzez Właściwość <xref:System.Windows.Forms.DataGrid.TableStyles%2A> kontrolki <xref:System.Windows.Forms.DataGrid>.

Na poniższej ilustracji przedstawiono obiekty zawarte w kontrolce DataGrid:

![Diagram przedstawiający obiekty zawarte w kontrolce DataGrid.](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)

Style tabeli i Style kolumn są synchronizowane z obiektami <xref:System.Data.DataTable> i obiektami <xref:System.Data.DataColumn> przez ustawienie ich właściwości `MappingName` na odpowiednie <xref:System.Data.DataTable.TableName%2A> i <xref:System.Data.DataColumn.ColumnName%2A> właściwości. Gdy <xref:System.Windows.Forms.DataGridTableStyle>, które nie ma żadnych stylów kolumn, jest dodawany do kontrolki <xref:System.Windows.Forms.DataGrid> powiązanej z prawidłowym źródłem danych, a właściwość <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> tego stylu tabeli jest ustawiona na prawidłową Właściwość <xref:System.Data.DataTable.TableName%2A>, kolekcja <xref:System.Windows.Forms.DataGridColumnStyle> obiektów zostanie utworzona dla tego stylu tabeli. Dla każdego <xref:System.Data.DataColumn> znajdującego się w kolekcji <xref:System.Data.DataTable.Columns%2A> <xref:System.Data.DataTable>do <xref:System.Windows.Forms.GridColumnStylesCollection>zostanie dodany odpowiedni <xref:System.Windows.Forms.DataGridColumnStyle>. <xref:System.Windows.Forms.GridColumnStylesCollection> jest dostępny za pomocą właściwości <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> <xref:System.Windows.Forms.DataGridTableStyle>. Kolumny można dodawać lub usuwać z siatki przy użyciu metody <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> lub <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> w <xref:System.Windows.Forms.GridColumnStylesCollection>. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie tabel i kolumn do kontrolki datagrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) i [instrukcje: usuwanie lub ukrywanie kolumn w formancie Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).

Kolekcja typów kolumn rozszerza klasę <xref:System.Windows.Forms.DataGridColumnStyle> z rozbudowanymi możliwościami formatowania i edycji. Wszystkie typy kolumn dziedziczą z klasy bazowej <xref:System.Windows.Forms.DataGridColumnStyle>. Utworzona Klasa zależy od właściwości <xref:System.Data.DataColumn.DataType%2A> <xref:System.Data.DataColumn> z której jest oparty <xref:System.Web.UI.WebControls.DataGridColumn>. Na przykład <xref:System.Data.DataColumn>, która ma właściwość <xref:System.Data.DataColumn.DataType%2A> ustawioną na <xref:System.Boolean>, zostanie skojarzona z <xref:System.Windows.Forms.DataGridBoolColumn>. W poniższej tabeli opisano każdy z tych typów kolumn.

|Typ kolumny|Opis|
|-----------------|-----------------|
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Akceptuje i wyświetla dane jako ciągi sformatowane lub niesformatowane. Możliwości edytowania są takie same, jak w przypadku edytowania danych w prostym <xref:System.Windows.Forms.TextBox>. Dziedziczy po <xref:System.Windows.Forms.DataGridColumnStyle>.|
|<xref:System.Windows.Forms.DataGridBoolColumn>|Akceptuje i wyświetla wartości `true`, `false`i null. Dziedziczy po <xref:System.Windows.Forms.DataGridColumnStyle>.|

Dwukrotne kliknięcie prawej krawędzi kolumny zmienia rozmiar kolumny, aby wyświetlić jej pełny podpis i szerszy wpis.

## <a name="table-styles-and-column-styles"></a>Style tabeli i kolumny

Po ustaleniu domyślnego formatu kontrolki <xref:System.Windows.Forms.DataGrid> można dostosować kolory, które będą używane podczas wyświetlania niektórych tabel w obrębie siatki danych.

Jest to osiągane przez utworzenie wystąpień klasy <xref:System.Windows.Forms.DataGridTableStyle>. Style tabeli określają formatowanie określonych tabel, odrębnie od domyślnego formatowania formantu <xref:System.Windows.Forms.DataGrid>. Dla każdej tabeli można zdefiniować tylko jeden styl tabeli w danym momencie.

Czasami chcesz, aby określona kolumna wyglądała inaczej niż reszta kolumn określonej tabeli danych. Można utworzyć dostosowany zestaw stylów kolumn za pomocą właściwości <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>.

Style kolumn są powiązane z kolumnami w zestawie danych, podobnie jak style tabeli, są powiązane z tabelami danych. Podobnie jak w przypadku każdej tabeli zdefiniowano tylko jeden styl tabeli w danym momencie, tak więc dla każdej z kolumn można zdefiniować tylko jeden styl kolumny w określonym stylu tabeli. Ta relacja jest definiowana w właściwości <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> kolumny.

Jeśli utworzono styl tabeli bez dodanych stylów kolumn, program Visual Studio doda domyślne style kolumn, gdy formularz i siatka zostaną utworzone w czasie wykonywania. Jednak w przypadku utworzenia stylu tabeli i dodania do niego stylów kolumn, program Visual Studio nie będzie tworzyć żadnych stylów kolumn. Ponadto należy zdefiniować Style kolumn i przypisać je z nazwą mapowania, aby mieć kolumny, które mają być wyświetlane w siatce.

Ponieważ określasz, które kolumny są uwzględniane w siatce danych przez przypisanie im stylu kolumn i nie przypisano stylu kolumn do kolumn, można uwzględnić kolumny danych w zestawie danych, które nie są wyświetlane w siatce. Jednak ponieważ kolumna danych jest uwzględniona w zestawie danych, można programowo edytować dane, które nie są wyświetlane.

> [!NOTE]
> Ogólnie rzecz biorąc, Utwórz Style kolumn i Dodaj je do kolekcji Style kolumn przed dodaniem stylów tabeli do kolekcji Style tabeli. Po dodaniu pustego stylu tabeli do kolekcji, Style kolumn są generowane automatycznie. W związku z tym wyjątek zostanie wygenerowany, jeśli spróbujesz dodać nowe style kolumn ze zduplikowanymi wartościami <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> do kolekcji Style kolumn.
>
> Czasami warto tylko dostosować jedną kolumnę do wielu kolumn; na przykład zestaw danych zawiera 50 kolumn i chcesz tylko 49 z nich. W takim przypadku łatwiejszym rozwiązaniem jest zaimportowanie wszystkich kolumn 50 i programowe usuwanie ich, zamiast programowo dodać każdą z 49 poszczególnych kolumn.

## <a name="formatting"></a>Formatowanie

Formatowanie, które można zastosować do kontrolki <xref:System.Windows.Forms.DataGrid>, zawiera style obramowania, style linii siatki, czcionki, właściwości podpisów, wyrównanie danych i przemienne kolory tła między wierszami. Aby uzyskać więcej informacji, zobacz [jak: formatowanie formantu DataGrid Windows Forms](how-to-format-the-windows-forms-datagrid-control.md).

## <a name="events"></a>Zdarzenia

Oprócz typowych zdarzeń kontroli, takich jak <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>i <xref:System.Windows.Forms.DataGrid.Scroll>, formant <xref:System.Windows.Forms.DataGrid> obsługuje zdarzenia związane z edycją i nawigacją w obrębie siatki. Właściwość <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> określa, która komórka jest zaznaczona. Zdarzenie <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> jest zgłaszane, gdy użytkownik nawiguje do nowej komórki. Gdy użytkownik nawiguje do nowej tabeli za pomocą relacji nadrzędny/podrzędny, zostanie zgłoszone zdarzenie <xref:System.Windows.Forms.DataGrid.Navigate>. Zdarzenie <xref:System.Windows.Forms.DataGrid.BackButtonClick> jest zgłaszane, gdy użytkownik kliknie przycisk Wstecz, gdy użytkownik przegląda tabelę podrzędną, a zdarzenie <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> zostanie wywołane, gdy zostanie kliknięta ikona Pokaż/Ukryj wiersze nadrzędne.

## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Instrukcje: formatowanie kontrolki DataGrid formularzy Windows Forms](how-to-format-the-windows-forms-datagrid-control.md)
