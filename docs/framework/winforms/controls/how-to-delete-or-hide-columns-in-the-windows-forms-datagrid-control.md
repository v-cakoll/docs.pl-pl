---
title: 'Instrukcje: Usuń lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: 635fbc112a241c4c8b17d2b49c22042c6bd59a21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653947"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Instrukcje: Usuń lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Możesz programowo Usuń lub ukrywanie kolumn w formularzach Windows Forms <xref:System.Windows.Forms.DataGrid> kontroli przy użyciu właściwości i metod <xref:System.Windows.Forms.GridColumnStylesCollection> i <xref:System.Windows.Forms.DataGridColumnStyle> obiektów (które są członkami <xref:System.Windows.Forms.DataGridTableStyle> klasy).  
  
 Usunięto lub ukrytych kolumn nadal istnieją w źródle danych, jest powiązany z siatki i nadal można uzyskać programistycznie. Oni po prostu nie są już widoczne w elemencie datagrid.  
  
> [!NOTE]
>  Jeśli aplikacja nie uzyskuje dostępu do niektórych kolumn danych, a nie chcesz, aby były wyświetlane w elemencie datagrid, następnie prawdopodobnie nie jest to konieczne uwzględnić je w pierwszej kolejności w źródle danych.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Aby programowo usunąć kolumnę z elementu DataGrid  
  
1.  W obszarze deklaracje w formularzu, należy zadeklarować nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle> klasy.  
  
2.  Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> właściwości do tabeli w źródle danych, którą chcesz zastosować styl. W poniższym przykładzie użyto <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwość, która zakłada, że jest już ustawiona.  
  
3.  Dodaj nowy <xref:System.Windows.Forms.DataGridTableStyle> obiektu do kolekcji style tabeli w elemencie datagrid.  
  
4.  Wywołaj <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.DataGrid>firmy <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> zbierania, określając indeks kolumny kolumny do usunięcia.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Aby ukryć kolumnę w elemencie DataGrid programowe  
  
1.  W obszarze deklaracje w formularzu, należy zadeklarować nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle> klasy.  
  
2.  Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość <xref:System.Windows.Forms.DataGridTableStyle> do tabeli w źródle danych, którą chcesz zastosować styl. Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwość, która zakłada, że jest już ustawiona.  
  
3.  Dodaj nowy <xref:System.Windows.Forms.DataGridTableStyle> obiektu do kolekcji style tabeli w elemencie datagrid.  
  
4.  Ukryj kolumnę, ustawiając jego `Width` właściwości na wartość 0, określając indeks kolumny, aby ukryć kolumny.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
