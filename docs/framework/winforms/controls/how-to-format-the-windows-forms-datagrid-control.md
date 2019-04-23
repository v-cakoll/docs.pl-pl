---
title: 'Instrukcje: format kontrolki DataGrid formularzy systemu Windows'
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
ms.openlocfilehash: 8e5c41d6f146e6abef8d7670e6191b587ac86c92
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336125"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Instrukcje: format kontrolki DataGrid formularzy systemu Windows
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Stosowanie różnych kolorów do różnych części <xref:System.Windows.Forms.DataGrid> kontroli może pomóc w ułatwienia informacje w nim odczytać i zinterpretować. Kolor może być stosowany do wierszy i kolumn. Wiersze i kolumny można również ukryte lub pokazane według uznania.  
  
 Istnieją trzy podstawowe aspekty formatowania <xref:System.Windows.Forms.DataGrid> kontroli. Można ustawić właściwości, aby ustanowić domyślnego stylu, w którym dane są wyświetlane. Z tego podstawowego można następnie dostosować sposób wyświetlania niektórych tabel w czasie wykonywania. Na koniec można zmodyfikować kolumny, które są wyświetlane w siatce danych, a także kolory i inne formatowania, które są wyświetlane.  
  
 Na etapie wstępnym w formatowaniu siatce danych, można ustawić właściwości <xref:System.Windows.Forms.DataGrid> sam. Te opcje kolor i format tworzą podstawowy, z którego można następnie wprowadzić zmiany w zależności od danych w tabelach i wyświetlane kolumny.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Ustanowienie domyślnego stylu dla formantu DataGrid  
  
1. Ustaw następujące właściwości zgodnie z potrzebami:  
  
    |Właściwość|Opis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> Właściwość definiuje kolor wierszach parzystych siatki. Po ustawieniu <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na inny kolor, co drugi wiersz jest właściwością ten nowy kolor (wiersze, 1, 3, 5 i tak dalej).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Kolor tła wierszy parzystych siatki (wiersze, 0, 2, 4, 6 i tak dalej).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Natomiast <xref:System.Windows.Forms.DataGrid.BackColor%2A> i <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwości określa kolor wierszy w siatce, <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> właściwość określa kolor obszar nonrow, który jest widoczna tylko siatki jest przewijane do dolnej lub tylko kilka wierszy są zawarte w Siatka.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl obramowania siatki, jeden z <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kolor tła tytuł okna siatki, które natychmiast pojawi się powyżej siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Czcionka napisów u góry strony siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Kolor tła tytuł okna siatki.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Czcionka używana do wyświetlania tekstu w siatce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Kolor czcionki wyświetlanej przez dane w wiersze siatki danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Kolor linii siatki w siatce danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl linii rozdzielających komórek siatki, jeden z <xref:System.Windows.Forms.DataGridLineStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Kolor tła w nagłówkach wierszy i kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Czcionka używana w nagłówkach kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kolor pierwszego planu nagłówków kolumn siatki, w tym tekst nagłówka kolumny i symbole plus/minus (w celu rozwiń wiersze, gdy wieloma powiązanymi tabelami są wyświetlane).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Kolor tekstu wszystkie linki w siatce danych, w tym łącza do tabele podrzędne, Nazwa relacji i tak dalej.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|W tabeli podrzędnej jest to kolor tła wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|W tabeli podrzędnej jest to kolor pierwszego planu wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Określa, czy nazwy tabel i kolumn są wyświetlane w wierszu nadrzędnym, przez <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Domyślna szerokość (w pikselach) kolumny w siatce. Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), lub właściwość nie odniesie żadnego skutku.<br /><br /> Nie można ustawić właściwość na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Wysokość wiersza (w pikselach) wierszy w siatce. Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), lub właściwość nie odniesie żadnego skutku.<br /><br /> Nie można ustawić właściwość na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Szerokość nagłówki wierszy siatki.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Po zaznaczeniu wiersza lub komórki jest to kolor tła.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Po zaznaczeniu wiersza lub komórki jest to kolor pierwszego planu.|  
  
    > [!NOTE]
    >  Pamiętać podczas dostosowywania kolory kontrolki, że jest to możliwe formant stał się niedostępny, ze względu na słabe wyboru (na przykład czerwonego i zielonego). Użyj kolorów, które są dostępne na **kolory systemowe** palety, aby uniknąć tego problemu.  
  
     W poniższych procedurach założono, formularz ma <xref:System.Windows.Forms.DataGrid> formant powiązany z tabelą danych. Aby uzyskać więcej informacji, zobacz [powiązania kontrolki DataGrid formularzy Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Aby programowo ustawić styl tabel i kolumn w tabeli danych  
  
1. Utwórz nowy styl tabeli i ustaw jego właściwości.  
  
2. Utwórz styl kolumny i ustaw jego właściwości.  
  
3. Dodaj style kolumny do kolekcji Style kolumn styl tabeli.  
  
4. Styl tabeli należy dodać do kolekcji style tabeli w siatce danych.  
  
5. W poniższym przykładzie Utwórz wystąpienie nowego <xref:System.Windows.Forms.DataGridTableStyle> i ustaw jego <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwości.  
  
6. Utwórz nowe wystąpienie klasy **GridColumnStyle** i ustaw jego **MappingName** (i inne układu i wyświetlania właściwości).  
  
7. Powtórz kroki od 2 do 6 dla każdego stylu kolumn, który chcesz utworzyć.  
  
     Poniższy przykład ilustruje sposób <xref:System.Windows.Forms.DataGridTextBoxColumn> zostanie utworzony, ponieważ jest nazwa będzie wyświetlana w kolumnie. Ponadto możesz dodać styl kolumny do <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabeli i Dodaj styl tabeli do <xref:System.Windows.Forms.GridTableStylesCollection> siatki danych.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Instrukcje: Usuń lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
