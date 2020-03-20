---
title: Formant formatowania danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
ms.openlocfilehash: 180f837c7d60f49af880faefc05da262be061d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182147"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Porady: format formantu DataGrid formularzy systemu Windows
> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.DataGrid> do formantu; jednak <xref:System.Windows.Forms.DataGrid> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [Różnice między formami Windows DataGridView i DataGrid Formantów](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Zastosowanie różnych kolorów do różnych <xref:System.Windows.Forms.DataGrid> części formantu może ułatwić odczytanie i interpretację informacji w nim. Kolor można stosować do wierszy i kolumn. Wiersze i kolumny mogą być również ukryte lub wyświetlane według własnego uznania.  
  
 Istnieją trzy podstawowe aspekty formatowania <xref:System.Windows.Forms.DataGrid> formantu. Można ustawić właściwości, aby ustanowić domyślny styl, w którym dane są wyświetlane. Z tej bazy można następnie dostosować sposób wyświetlania niektórych tabel w czasie wykonywania. Na koniec można zmodyfikować kolumny, które są wyświetlane w siatce danych, a także kolory i inne formatowanie, które jest wyświetlane.  
  
 Jako początkowy krok w formatowaniu siatki danych można ustawić <xref:System.Windows.Forms.DataGrid> właściwości samego. Te opcje kolorów i formatów tworzą podstawę, z której można następnie wprowadzać zmiany w zależności od wyświetlanych tabel danych i kolumn.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Aby ustanowić domyślny styl dla formantu DataGrid  
  
1. Odpowiednio ustaw następujące właściwości:  
  
    |Właściwość|Opis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|Właściwość <xref:System.Windows.Forms.DataGrid.BackColor%2A> definiuje kolor wierszy parzyste siatki. Po ustawieniu <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwości na inny kolor, co drugi wiersz jest ustawiony na ten nowy kolor (wiersze 1, 3, 5 i tak dalej).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Kolor tła wierszy siatki o numerach parzyste (wiersze 0, 2, 4, 6 itd.).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Natomiast <xref:System.Windows.Forms.DataGrid.BackColor%2A> i <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwości określa kolor wierszy w siatce, <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> właściwość określa kolor obszaru nonrow, który jest widoczny tylko wtedy, gdy siatka jest przewijana do dołu lub jeśli tylko kilka wierszy są zawarte w siatce.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl obramowania siatki, jedna <xref:System.Windows.Forms.BorderStyle> z wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kolor tła podpisu okna siatki, który pojawia się bezpośrednio nad siatką.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Czcionka podpisu w górnej części siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Kolor tła podpisu okna siatki.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Czcionka używana do wyświetlania tekstu w siatce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Kolor czcionki wyświetlany przez dane w wierszach siatki danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Kolor linii siatki siatki danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl linii oddzielających komórki siatki, jedną z <xref:System.Windows.Forms.DataGridLineStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Kolor tła nagłówków wierszy i kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Czcionka używana dla nagłówków kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kolor pierwszego planu nagłówków kolumn siatki, w tym tekst nagłówka kolumny i glify plus/minus (aby rozwinąć wiersze, gdy wyświetlanych jest wiele powiązanych tabel).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Kolor tekstu wszystkich łączy w siatce danych, w tym łącza do tabel podrzędnych, nazwy relacji i tak dalej.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|W tabeli podrzędnej jest to kolor tła wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|W tabeli podrzędnej jest to kolor pierwszego planu wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Określa, czy nazwy tabel i kolumn są wyświetlane w wierszu nadrzędnym za pomocą wyliczenia. <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Domyślna szerokość (w pikselach) kolumn w siatce. Ustaw tę właściwość <xref:System.Windows.Forms.DataGrid.DataSource%2A> przed <xref:System.Windows.Forms.DataGrid.DataMember%2A> zresetowaniem właściwości i (oddzielnie <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> lub za pomocą metody) lub właściwość nie będzie miała wpływu.<br /><br /> Właściwości nie można ustawić na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Wysokość wiersza (w pikselach) wierszy w siatce. Ustaw tę właściwość <xref:System.Windows.Forms.DataGrid.DataSource%2A> przed <xref:System.Windows.Forms.DataGrid.DataMember%2A> zresetowaniem właściwości i (oddzielnie <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> lub za pomocą metody) lub właściwość nie będzie miała wpływu.<br /><br /> Właściwości nie można ustawić na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Szerokość nagłówków wierszy siatki.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Gdy zaznaczony jest wiersz lub komórka, jest to kolor tła.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Gdy zaznaczony jest wiersz lub komórka, jest to kolor pierwszego planu.|  
  
    > [!NOTE]
    > Należy pamiętać, podczas dostosowywania kolorów formantów, że jest możliwe, aby formant niedostępny, ze względu na zły wybór koloru (na przykład czerwony i zielony). Aby uniknąć tego problemu, użyj kolorów dostępnych na palecie **Kolory systemowe.**  
  
     Poniższe procedury zakładają, że formularz ma <xref:System.Windows.Forms.DataGrid> formant powiązany z tabelą danych. Aby uzyskać więcej informacji, zobacz [Powiązanie formantu DataGrid formularzy systemu Windows ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Aby programowo ustawić styl tabeli i kolumny tabeli danych  
  
1. Utwórz nowy styl tabeli i ustaw jej właściwości.  
  
2. Utwórz styl kolumny i ustaw jej właściwości.  
  
3. Dodaj styl kolumny do kolekcji stylów kolumnowych stylu tabeli.  
  
4. Dodaj styl tabeli do kolekcji stylów tabeli siatki danych.  
  
5. W poniższym przykładzie utwórz <xref:System.Windows.Forms.DataGridTableStyle> wystąpienie <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> nowego i ustaw jego właściwość.  
  
6. Utwórz nowe wystąpienie **GridColumnStyle** i ustaw jego **Nazwa mapowania** (oraz niektóre inne właściwości układu i wyświetlania).  
  
7. Powtórz kroki od 2 do 6 dla każdego stylu kolumny, który chcesz utworzyć.  
  
     Poniższy przykład ilustruje sposób <xref:System.Windows.Forms.DataGridTextBoxColumn> tworzenia, ponieważ nazwa ma być wyświetlana w kolumnie. Ponadto do tego dodajesz styl <xref:System.Windows.Forms.GridColumnStylesCollection> kolumny w stylu tabeli i dodajesz styl tabeli do <xref:System.Windows.Forms.GridTableStylesCollection> siatki danych.  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName
       ' to the name of a DataColumn in the DataTable.
       ' Set the HeaderText and Width properties.
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to
       ' the GridTableStylesCollection.
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName
       // to the name of a DataColumn in the DataTable.
       // Set the HeaderText and Width properties.
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to
       // the GridTableStylesCollection.
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName
          // to the name of a DataColumn in the DataTable.
          // Set the HeaderText and Width properties.
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to
          // the GridTableStylesCollection.
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Porady: usuwanie lub ukrywanie kolumn w formancie DataGrid formularzy systemu Windows](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
