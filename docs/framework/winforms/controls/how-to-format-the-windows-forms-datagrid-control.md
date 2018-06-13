---
title: 'Porady: format formantu DataGrid formularzy systemu Windows'
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
ms.openlocfilehash: ffcb84059dfceb85cdb347c3ddf1b80ab96c2aac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540452"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Porady: format formantu DataGrid formularzy systemu Windows
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Stosowanie różnych kolorów do różnych części <xref:System.Windows.Forms.DataGrid> formant może pomóc udostępnia informacje w nim łatwiej odczytywać i interpretowania. Kolor można zastosować do wierszy i kolumn. Wiersze i kolumny można również ukryte lub pokazane według uznania.  
  
 Istnieją trzy podstawowe aspekty formatowania <xref:System.Windows.Forms.DataGrid> formantu. Można ustawić właściwości, aby ustanowić domyślny styl wyświetlania danych. Z tego elementu bazowego można dostosować sposób wyświetlania określonych tabel w czasie wykonywania. Na koniec można zmodyfikować kolumny, które są wyświetlane w siatce danych, a także kolory i inne formatowania, który jest wyświetlany.  
  
 Na etapie wstępnym w formatowaniu siatkę danych, można ustawić właściwości <xref:System.Windows.Forms.DataGrid> samej siebie. Te opcje kolor i format tworzą podstawowy, z którego można następnie wprowadzić zmiany w zależności od danych tabele i kolumny wyświetlane.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Aby ustanowić domyślny styl formantu DataGrid  
  
1.  Ustaw następujące właściwości odpowiednio:  
  
    |Właściwość|Opis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> Właściwość określa kolor wierszach parzystych siatki. Podczas ustawiania <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwość inny kolor, każdego wiersza jest ustawiona na nowy kolor (wiersze, 1, 3, 5 i tak dalej).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Kolor tła wierszy parzystych siatki (wiersze, 0, 2, 4, 6 itd.).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Podczas gdy <xref:System.Windows.Forms.DataGrid.BackColor%2A> i <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwości określa kolor wierszy w siatce <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> właściwość określa kolor obszaru nonrow, która jest widoczna tylko siatki jest przewijane w dół lub tylko kilka wierszy są zawarte w Siatka.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl obramowania siatki, jeden z <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kolor tła tytuł okna siatki, które pojawia się powyżej siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Czcionka podpisu w górnej części siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Kolor tła tytuł okna siatki.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Czcionka używana do wyświetlania tekstu w siatce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Kolor czcionki wyświetlanego przez dane w wiersze siatki danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Kolor linii siatki w siatce danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl linii oddzielających komórki siatki, jeden z <xref:System.Windows.Forms.DataGridLineStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Kolor tła nagłówków wierszy i kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Czcionka używana dla nagłówków kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kolor pierwszego planu nagłówków kolumn siatki, w tym tekst nagłówka kolumny i symboli plus/minus (do wyświetlania wielu powiązanych tabel, rozwiń węzeł wierszy).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Kolor tekstu wszystkich łączy w siatce danych oraz łącza do tabele podrzędne, Nazwa relacji i tak dalej.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|W tabeli podrzędnej jest to kolor tła wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|W tabeli podrzędnej jest to kolor pierwszego planu wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Określa, czy nazwy tabel i kolumn są wyświetlane w wierszu nadrzędnego za pomocą klasy <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Domyślna szerokość (w pikselach) kolumn w siatce. Ta właściwość jest ustawiana przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę), lub właściwość nie odniesie żadnego skutku.<br /><br /> Nie można ustawić właściwości na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Wysokość wiersza (w pikselach) wierszy w siatce. Ta właściwość jest ustawiana przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę), lub właściwość nie odniesie żadnego skutku.<br /><br /> Nie można ustawić właściwości na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Szerokość nagłówków wiersza siatki.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Po zaznaczeniu wiersza lub komórki jest to kolor tła.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Po zaznaczeniu wiersza lub komórki jest to kolor pierwszego planu.|  
  
    > [!NOTE]
    >  Należy pamiętać, gdy dostosowywanie kolorów formantów, czy jest możliwe formantu niedostępny z powodu słabej kolory do wyboru (na przykład czerwony i zielony). Użyj kolorów, które są dostępne na **kolorów systemu** palety, aby uniknąć tego problemu.  
  
     W poniższych procedurach założono formularz zawiera <xref:System.Windows.Forms.DataGrid> formant powiązany z tabelą danych. Aby uzyskać więcej informacji, zobacz [powiązanie formantu DataGrid formularzy systemu Windows ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Aby ustawić programowo styl tabel i kolumn w tabeli danych  
  
1.  Utwórz nowy styl tabeli i ustawienia swoich właściwości.  
  
2.  Utwórz styl kolumny i ustawienia swoich właściwości.  
  
3.  Dodać kolumnę do Kolekcja styli kolumn styl tabeli.  
  
4.  Styl tabeli należy dodać do Kolekcja stylów tabeli siatki danych.  
  
5.  W poniższym przykładzie Utwórz wystąpienie nowej <xref:System.Windows.Forms.DataGridTableStyle> i ustawić jej <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwości.  
  
6.  Utwórz nowe wystąpienie klasy **GridColumnStyle** i ustawić jej **MappingName** (i innych układu i wyświetlania właściwości).  
  
7.  Powtórz kroki od 2 do 6 dla każdego stylu kolumn, który chcesz utworzyć.  
  
     Poniższy przykład przedstawia sposób <xref:System.Windows.Forms.DataGridTextBoxColumn> jest tworzony, ponieważ jest nazwa będzie wyświetlana w kolumnie. Ponadto możesz dodać styl kolumny do <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabeli i Dodaj styl tabeli do <xref:System.Windows.Forms.GridTableStylesCollection> siatki danych.  
  
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
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
