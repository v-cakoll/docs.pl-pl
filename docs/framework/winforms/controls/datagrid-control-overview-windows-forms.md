---
title: "DataGrid — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataGrid
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10220efc0bb77ddcc7f0f9fa0e3f2793a032a1bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Formularze systemu Windows <xref:System.Windows.Forms.DataGrid> kontrola wyświetla danych w serii wierszy i kolumn. Najprostsza zdarza się, gdy siatki jest powiązana ze źródłem danych z pojedynczej tabeli, która zawiera Brak relacji. W takim przypadku dane są wyświetlane w prosty wierszy i kolumn w arkuszu kalkulacyjnym. Aby uzyskać więcej informacji na temat wiązania danych do innych kontrolek zobacz [powiązania danych i formularze systemu Windows](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
 Jeśli <xref:System.Windows.Forms.DataGrid> jest powiązany z danymi z wielu powiązanych tabel, i włączenie nawigacji w siatce siatki będą wyświetlane ekspanderów znajdujących w każdym wierszu. Element expander użytkownik może przenieść z tabelą nadrzędną tabeli podrzędnej. Klikając węzeł Wyświetla tabeli podrzędnej oraz kliknięcie przycisku Wstecz w oryginalnej tabeli nadrzędnej. W ten sposób Siatka wyświetla hierarchicznych relacji między tabelami.  
  
 Poniższy zrzut ekranu przedstawia DataGrid powiązany z danymi z wielu tabel.  
  
 ![DataGrid powiązany z danymi z wielu tabel](../../../../docs/framework/winforms/controls/media/vbcontrol1.gif "vbControl1")  
DataGrid powiązany z danymi z wielu tabel  
  
 <xref:System.Windows.Forms.DataGrid> Zapewnia interfejsu użytkownika dla zestawu danych, nawigacji między powiązane tabele i rozbudowane, formatowanie i możliwości edycji.  
  
 Wyświetlanie i modyfikowanie danych są odrębne funkcje: formantu obsługuje interfejs użytkownika, natomiast aktualizacje danych są obsługiwane przez architekturę powiązanie danych formularzy systemu Windows i przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych. W związku z tym pozostanie synchronizację wielu formantów związanych z tym samym źródle danych.  
  
> [!NOTE]
>  Jeśli znasz z formantem DataGrid w Visual Basic 6.0, dostępne są niektóre istotne różnice w formularzach systemu Windows <xref:System.Windows.Forms.DataGrid> formantu.  
  
 Siatka jest powiązany z <xref:System.Data.DataSet>, kolumn i wierszy są automatycznie tworzone, sformatowany i wypełnione. Aby uzyskać więcej informacji, zobacz [powiązania danych i formularze systemu Windows](../../../../docs/framework/winforms/data-binding-and-windows-forms.md). Następujące Generowanie <xref:System.Windows.Forms.DataGrid> sterowania, można dodać, usunąć, rozmieszczanie i formatować kolumnami i wierszami w zależności od potrzeb.  
  
## <a name="binding-data-to-the-control"></a>Wiązanie danych do kontrolki  
 Dla <xref:System.Windows.Forms.DataGrid> sterowania do pracy, powinny być powiązane do źródła danych przy użyciu <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości w czasie projektowania lub <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody w czasie wykonywania. Wskazuje to powiązanie <xref:System.Windows.Forms.DataGrid> do obiektu wystąpień źródła danych, takich jak <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>). <xref:System.Windows.Forms.DataGrid> Kontroli pokazuje wyniki akcji, które są wykonywane na danych. Większość akcji specyficzne dla danych nie są wykonywane za pośrednictwem <xref:System.Windows.Forms.DataGrid> , ale zamiast tego za pośrednictwem źródła danych.  
  
 Jeśli dane w zestawie danych powiązane są aktualizowane przy użyciu dowolnego mechanizmu <xref:System.Windows.Forms.DataGrid> kontroli odzwierciedla zmiany. Jeśli siatka danych i jego tabeli style i kolumny `ReadOnly` ustawioną właściwość `false`, danych w zestawie danych można aktualizować za pośrednictwem <xref:System.Windows.Forms.DataGrid> formantu.  
  
 Tylko jedna tabela może być wyświetlany w <xref:System.Windows.Forms.DataGrid> naraz. Jeśli jest zdefiniowana relacja nadrzędny podrzędny między tabelami, użytkownik może przechodzić między powiązane tabele, aby zaznaczyć tabelę, która ma być wyświetlany w <xref:System.Windows.Forms.DataGrid> formantu. Informacje o powiązaniu <xref:System.Windows.Forms.DataGrid> formant [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] źródła danych w czasie projektowania lub czas wykonywania, zobacz [porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
 Źródła danych prawidłową <xref:System.Windows.Forms.DataGrid> obejmują:  
  
-   <xref:System.Data.DataTable>klasy  
  
-   <xref:System.Data.DataView>klasy  
  
-   <xref:System.Data.DataSet>klasy  
  
-   <xref:System.Data.DataViewManager>klasy  
  
 Jeśli źródłem jest element dataset, zestawu danych może być w formie lub obiektu przekazany do formularza przez usługi XML sieci Web. Można powiązać typizowany lub nietypizowany zestaw danych.  
  
 Może także powiązać <xref:System.Windows.Forms.DataGrid> kontroli dodatkowe struktur, jeśli obiekty w strukturze, takich jak elementy w tablicy, udostępniają właściwości publicznej. Siatki będą wyświetlane wszystkie właściwości publiczne elementy w strukturze. Na przykład w przypadku powiązania <xref:System.Windows.Forms.DataGrid> obiekty formantu do tablicy klienta siatki będą wyświetlane wszystkie właściwości publiczne tych obiektów klienta. W niektórych przypadkach oznacza, że chociaż można powiązać struktury, wynikowy struktury powiązane może nie mają praktyczne aplikacji. Na przykład można powiązać tablica liczb całkowitych, ale ponieważ `Integer` — typ danych nie obsługuje właściwości publicznej, siatki nie zawiera żadnych danych.  
  
 Jeśli ich elementów ujawnić właściwości publiczne, można powiązać następujące struktury:  
  
-   Każdego składnika, który implementuje <xref:System.Collections.IList> interfejsu. W tym tablice jednowymiarowej.  
  
-   Każdego składnika, który implementuje <xref:System.ComponentModel.IListSource> interfejsu.  
  
-   Każdego składnika, który implementuje <xref:System.ComponentModel.IBindingList> interfejsu.  
  
 Aby uzyskać więcej informacji na temat źródeł danych, zobacz [danych źródła obsługiwane przez program Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
## <a name="grid-display"></a>Wyświetlania siatki  
 Typowym zastosowaniem <xref:System.Windows.Forms.DataGrid> formant jest do wyświetlania pojedynczej tabeli danych z zestawu danych. Jednak formantu można również wyświetlić wiele tabel, łącznie z powiązanych tabel. Wyświetlanie siatki jest automatycznie dostosowywany zgodnie ze źródła danych. W poniższej tabeli przedstawiono, co jest wyświetlane w przypadku różnych konfiguracji.  
  
|Zawartość zestawu danych|Co to jest wyświetlana|  
|--------------------------|-----------------------|  
|Pojedynczą tabelę.|Tabela jest wyświetlana w siatce.|  
|Wiele tabel.|Siatki można wyświetlić widoku drzewa, które użytkownicy mogą przejść do zlokalizowania w tabeli, które mają być wyświetlane.|  
|Wielu powiązanych tabel.|Siatki można wyświetlić widoku drzewa wybierz tabele, lub można określić, że siatki wyświetlać tabeli nadrzędnej. Rekordy w tabeli nadrzędnej umożliwiają użytkownikom przechodzenie do wierszy podrzędnych.|  
  
> [!NOTE]
>  Tabele w zestawie danych są powiązane za pomocą <xref:System.Data.DataRelation>.  Zobacz też [HYPERLINK "http://msdn.microsoft.com/library/dbwcse3d (v=vs.110)" relacje w zestawach danych](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.110\)) lub [relacje w zestawach danych](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.120\)).  
  
 Gdy <xref:System.Windows.Forms.DataGrid> sterowania są wyświetlane w tabeli i <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> właściwość jest ustawiona na `true`, dane mogą mieć zastosowanie, klikając nagłówki kolumn. Użytkownik może również dodawanie wierszy i edytować komórki.  
  
 Relacje między zestaw tabel są wyświetlane użytkownikom przy użyciu struktury nadrzędny/podrzędny nawigacji. Tabel nadrzędnych są najwyższy poziom danych i tabele podrzędne są te tabele danych, pochodzących z poszczególnych list w tabeli nadrzędnej. Ekspanderów znajdujących są wyświetlane w każdym wierszu nadrzędnego zawierający tabeli podrzędnej. Klikając przycisk rozwijania generuje listę łączy stylu sieci Web dla tabel podrzędnych. Gdy użytkownik wybierze link, zostanie wyświetlony tabelą podrzędną. Kliknięcie ikony wiersze nadrzędne Pokaż/Ukryj (![Pokaż &#47; Ukryj ikonę wiersze nadrzędne](../../../../docs/framework/winforms/controls/media/vbicon.gif "vbIcon")) będzie Ukryj informacji o tabeli nadrzędnej lub spowodować się ponownie, jeśli użytkownik wcześniej jest ukryty. Użytkownik może kliknąć przycisk Wstecz, aby powrócić do poprzednio czytanego tabeli.  
  
## <a name="columns-and-rows"></a>Kolumn i wierszy  
 <xref:System.Windows.Forms.DataGrid> Składa się z kolekcją <xref:System.Windows.Forms.DataGridTableStyle> obiektów, które są zawarte w <xref:System.Windows.Forms.DataGrid> formantu <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości. Styl tabeli może zawierać Kolekcja <xref:System.Windows.Forms.DataGridColumnStyle> obiektów, które są zawarte w <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwość <xref:System.Windows.Forms.DataGridTableStyle>... Można edytować <xref:System.Windows.Forms.DataGrid.TableStyles%2A> i <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości przy użyciu edytora kolekcji dostępne za pośrednictwem **właściwości** okna.  
  
 Wszelkie <xref:System.Windows.Forms.DataGridTableStyle> skojarzone z <xref:System.Windows.Forms.DataGrid> kontroli jest możliwy za pośrednictwem <xref:System.Windows.Forms.GridTableStylesCollection>. <xref:System.Windows.Forms.GridTableStylesCollection> Można edytowane w Projektancie z <xref:System.Windows.Forms.DataGridTableStyle> edytora kolekcji lub programistycznie za pomocą <xref:System.Windows.Forms.DataGrid> formantu <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości.  
  
 ![Liczba obiektów uwzględnionych w formancie DataGrid](../../../../docs/framework/winforms/controls/media/vbcolumns1.gif "vbColumns1")  
Na poniższej ilustracji przedstawiono obiektów uwzględnionych w formancie DataGrid.  
  
 Style tabeli i kolumny są synchronizowane z <xref:System.Data.DataTable> obiektów i <xref:System.Data.DataColumn> obiektów przez ustawienie ich `MappingName` właściwości do odpowiedniego <xref:System.Data.DataTable.TableName%2A> i <xref:System.Data.DataColumn.ColumnName%2A> właściwości. Gdy <xref:System.Windows.Forms.DataGridTableStyle> który nie ma kolumny style zostanie dodany do <xref:System.Windows.Forms.DataGrid> formant powiązany z poprawnego źródła danych i <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość tego stylu tabeli jest ustawiona na prawidłowy <xref:System.Data.DataTable.TableName%2A> właściwości, Kolekcja <xref:System.Windows.Forms.DataGridColumnStyle> obiektów jest tworzony w tym Styl tabeli. Dla każdego <xref:System.Data.DataColumn> w <xref:System.Data.DataTable.Columns%2A> Kolekcja <xref:System.Data.DataTable>, odpowiadający jej <xref:System.Windows.Forms.DataGridColumnStyle> jest dodawany do <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection>jest dostępny za pośrednictwem <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwość <xref:System.Windows.Forms.DataGridTableStyle>. Kolumny można dodawać lub usuwać z przy użyciu siatki <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> lub <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> metoda <xref:System.Windows.Forms.GridColumnStylesCollection>. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie tabel i kolumn do formantu DataGrid formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) i [porady: usuwanie lub ukrywanie kolumn w formancie DataGrid formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).  
  
 Kolekcja typów kolumn rozszerza <xref:System.Windows.Forms.DataGridColumnStyle> z zaawansowanych formatowanie i możliwości edycji. Wszystkie typy kolumn dziedziczyć <xref:System.Windows.Forms.DataGridColumnStyle> klasy podstawowej. Klasa, która jest tworzona jest zależna od <xref:System.Data.DataColumn.DataType%2A> właściwość <xref:System.Data.DataColumn> z którego <xref:System.Web.UI.WebControls.DataGridColumn> opiera się. Na przykład <xref:System.Data.DataColumn> mający jego <xref:System.Data.DataColumn.DataType%2A> ustawioną właściwość <xref:System.Boolean> zostaną skojarzone z <xref:System.Windows.Forms.DataGridBoolColumn>. W poniższej tabeli opisano każdy z tych typów kolumn.  
  
|Typ kolumny|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Akceptuje i wyświetla dane jako ciąg sformatowany lub niesformatowany. Funkcje edycji są takie same jak w przypadku edycji danych w prosty <xref:System.Windows.Forms.TextBox>. Dziedziczy <xref:System.Windows.Forms.DataGridColumnStyle>.|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|Akceptuje i wyświetla `true`, `false`i wartości null. Dziedziczy <xref:System.Windows.Forms.DataGridColumnStyle>.|  
  
 Dwukrotne kliknięcie prawą krawędzią kolumny zmienia rozmiar kolumny do wyświetlania jego pełny podpisu i najszerszego wpisu.  
  
## <a name="table-styles-and-column-styles"></a>Style tabel i kolumn  
 Jak najszybciej po ustanowieniu domyślny format <xref:System.Windows.Forms.DataGrid> sterowania, można dostosować kolory, które będą używane podczas niektórych tabele są wyświetlane w siatce danych.  
  
 Jest to osiągane przez utworzenie wystąpienia <xref:System.Windows.Forms.DataGridTableStyle> klasy. Określ styl tabeli formatowania określonych tabel, inny niż domyślny format <xref:System.Windows.Forms.DataGrid> samą kontrolką. Każda tabela może mieć tylko jedną tabelę style zdefiniowane w czasie.  
  
 Czasami ma mają różne od pozostałej części kolumny tabeli danych wygląd określonej kolumny. Można utworzyć dostosowany zbiór Style kolumn za pomocą <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości.  
  
 Style kolumn odnoszą się do kolumn w zestawie danych tak samo, jak style tabeli odnoszą się do tabel danych. Tak samo, jak każda tabela może mieć tylko jeden styl tabeli zdefiniowane w czasie, dlatego można zbyt każdej kolumny tylko jeden styl kolumny zdefiniowane, w stylu określonej tabeli. Ta relacja jest definiowana w tej kolumnie <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> właściwości.  
  
 Jeśli utworzono styl tabeli bez Style kolumn do momentu, [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] doda domyślne style kolumn podczas tworzenia formularza i siatki w czasie wykonywania. Jednak jeśli utworzono styl tabeli i dodać wszystkie style kolumn, [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] nie utworzy wszystkie style kolumn. Ponadto należy zdefiniować style kolumn i przypisać je o nazwie mapowania mieć kolumn, które mają być wyświetlane w siatce.  
  
 Określ, które kolumny mają zostać uwzględnione w siatce danych przypisywania do nich styl kolumny i żaden styl kolumny zostanie przypisana do kolumn, dlatego może zawierać kolumn danych w zestawie danych, które nie są wyświetlane w siatce. Jednak ponieważ kolumna danych jest uwzględniona w zestawie danych, można programowo edytować danych, które nie są wyświetlane.  
  
> [!NOTE]
>  Ogólnie rzecz biorąc Utwórz style kolumn i dodaj je do Kolekcja styli kolumn przed dodaniem stylów tabeli do Kolekcja stylów tabeli. Po dodaniu stylu pusta tabela do kolekcji Style kolumn są generowane automatycznie dla Ciebie. W związku z tym, zostanie wygenerowany wyjątek Jeśli próbujesz dodać nowe style kolumn ze zduplikowaną <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> wartości Kolekcja styli kolumn.  
>   
>  Czasami można dodawać tylko jedną kolumnę między wiele kolumn; na przykład zestaw danych zawiera kolumny 50 i mają 49 z nich. W takim przypadku jest łatwiejsze zaimportować wszystkie kolumny 50 i programowo Usuń jeden, a nie programowo Dodawanie każdego 49 poszczególnych kolumn ma.  
  
## <a name="formatting"></a>Formatowanie  
 Formatowanie, które mogą być stosowane do <xref:System.Windows.Forms.DataGrid> formant zawiera style obramowania, style linii siatki, czcionki, właściwości podpisu, wyrównanie danych i naprzemiennych kolorów tła między wierszami. Aby uzyskać więcej informacji, zobacz [porady: formatowanie formantu DataGrid formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md).  
  
## <a name="events"></a>Zdarzenia  
 Oprócz typowe kontrolowanie zdarzeń takich jak <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>, i <xref:System.Windows.Forms.DataGrid.Scroll>, <xref:System.Windows.Forms.DataGrid> sterowanie obsługuje zdarzenia związane z edycji i nawigacja w siatce. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> Określa właściwości komórki, która jest zaznaczona. <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> Zdarzenie jest wywoływane, gdy użytkownik przechodzi do nowego komórki. Gdy użytkownik przechodzi do nowej tabeli przy użyciu relacji nadrzędny/podrzędny <xref:System.Windows.Forms.DataGrid.Navigate> zdarzenia. <xref:System.Windows.Forms.DataGrid.BackButtonClick> Zdarzenie jest wywoływane, gdy użytkownik kliknie przycisk Wstecz, przeglądając użytkownika jest tabelą podrzędną i <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> zdarzenie jest wywoływane po kliknięciu ikony wiersze nadrzędne Pokaż/Ukryj.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Instrukcje: formatowanie kontrolki DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)
