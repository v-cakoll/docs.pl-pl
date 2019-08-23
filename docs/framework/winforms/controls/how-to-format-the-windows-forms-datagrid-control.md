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
ms.openlocfilehash: 99acef0a7b29228ddf0406352ff5a88b77294b00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966672"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Instrukcje: format kontrolki DataGrid formularzy systemu Windows
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Stosowanie różnych kolorów do różnych części <xref:System.Windows.Forms.DataGrid> formantu może pomóc w ułatwianiu odczytywania i interpretowania informacji. Kolor można zastosować do wierszy i kolumn. Wiersze i kolumny można także ukryć lub pokazać według własnego uznania.  
  
 Istnieją trzy podstawowe aspekty formatowania <xref:System.Windows.Forms.DataGrid> formantu. Można ustawić właściwości, aby określić domyślny styl, w którym są wyświetlane dane. Z tej bazy można następnie dostosować sposób wyświetlania niektórych tabel w czasie wykonywania. Na koniec można modyfikować, które kolumny są wyświetlane w siatce danych, a także kolory i inne wyświetlane formatowanie.  
  
 Jako pierwszy krok formatowania siatki danych można ustawić właściwości <xref:System.Windows.Forms.DataGrid> samej siebie. Opcje tego koloru i formatu stanowią podstawę, z której można wprowadzać zmiany w zależności od wyświetlanych tabel i kolumn danych.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Aby określić styl domyślny dla kontrolki DataGrid  
  
1. Ustaw odpowiednio następujące właściwości:  
  
    |Właściwość|Opis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> Właściwość definiuje kolor wierszy z parzystymi numerami siatki. Po ustawieniu <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwości na inny kolor, każdy inny wiersz jest ustawiany na ten nowy kolor (wiersze 1, 3, 5 itd.).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Kolor tła wierszy z parzystymi numerami siatki (wiersze 0, 2, 4, 6 itd.).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Natomiast właściwości <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> i określają kolor wierszy w siatce, właściwość określa kolor obszaru nonrow, który jest widoczny tylko wtedy, gdy siatka jest przewijana do dołu lub w przypadku, gdy zawiera tylko kilka wierszy <xref:System.Windows.Forms.DataGrid.BackColor%2A> Siatka.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl obramowania siatki, jedna z <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kolor tła podpisu okna siatki, który pojawia się bezpośrednio nad siatką.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Czcionka napisu w górnej części siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Kolor tła podpisu okna siatki.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Czcionka używana do wyświetlania tekstu w siatce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Kolor czcionki wyświetlanej przez dane w wierszach siatki danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Kolor linii siatki siatki danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl linii oddzielających komórki siatki, jedną z <xref:System.Windows.Forms.DataGridLineStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Kolor tła nagłówków wierszy i kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Czcionka używana w nagłówkach kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kolor pierwszego planu nagłówka kolumny siatki, włącznie z tekstem nagłówka kolumny i symbolami plus/minus (do rozwijania wierszy w przypadku wyświetlenia wielu powiązanych tabel).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Kolor tekstu wszystkich łączy w siatce danych, w tym linki do tabel podrzędnych, nazwy relacji i tak dalej.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|W tabeli podrzędnej jest to kolor tła wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|W tabeli podrzędnej jest to kolor pierwszego planu wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Określa, czy nazwy tabel i kolumn są wyświetlane w wierszu nadrzędnym, za pomocą <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Domyślna szerokość (w pikselach) kolumn w siatce. Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości i <xref:System.Windows.Forms.DataGrid.DataMember%2A> ( <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> oddzielnie albo za pomocą metody) lub właściwość nie będzie mieć żadnego efektu.<br /><br /> Właściwość nie może być ustawiona na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Wysokość wiersza (w pikselach) wierszy w siatce. Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości i <xref:System.Windows.Forms.DataGrid.DataMember%2A> ( <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> oddzielnie albo za pomocą metody) lub właściwość nie będzie mieć żadnego efektu.<br /><br /> Właściwość nie może być ustawiona na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Szerokość nagłówków wierszy siatki.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Po wybraniu wiersza lub komórki jest to kolor tła.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Po wybraniu wiersza lub komórki jest to kolor pierwszego planu.|  
  
    > [!NOTE]
    > Należy pamiętać, że podczas dostosowywania kolorów formantów możliwe jest, że kontrolka jest niedostępna z powodu słabego wyboru koloru (na przykład czerwony i zielony). Użyj kolorów dostępnych na palecie **kolorów systemu** , aby uniknąć tego problemu.  
  
     W poniższych procedurach przyjęto założenie <xref:System.Windows.Forms.DataGrid> , że formularz zawiera kontrolkę powiązaną z tabelą danych. Aby uzyskać więcej informacji, zobacz [powiązywanie formantu Windows Forms DataGrid ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Aby programowo ustawić styl tabeli i kolumny tabeli danych  
  
1. Utwórz nowy styl tabeli i ustaw jego właściwości.  
  
2. Utwórz styl kolumny i ustaw jego właściwości.  
  
3. Dodaj styl kolumny do kolekcji Style kolumn stylu tabeli.  
  
4. Dodaj styl tabeli do kolekcji Style tabeli siatki danych.  
  
5. W poniższym przykładzie Utwórz wystąpienie nowego <xref:System.Windows.Forms.DataGridTableStyle> i ustaw jego <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość.  
  
6. Utwórz nowe wystąpienie elementu **GridColumnStyle** i ustaw jego mapowaniename (oraz inne właściwości układu i wyświetlania).  
  
7. Powtórz kroki od 2 do 6 dla każdego stylu kolumny, który chcesz utworzyć.  
  
     Poniższy przykład ilustruje sposób <xref:System.Windows.Forms.DataGridTextBoxColumn> tworzenia, ponieważ nazwa ma być wyświetlana w kolumnie. Dodatkowo należy dodać styl kolumny do <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabeli, a następnie dodać styl tabeli <xref:System.Windows.Forms.GridTableStylesCollection> do siatki danych.  
  
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
- [Instrukcje: Usuwanie lub ukrywanie kolumn w kontrolce DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
