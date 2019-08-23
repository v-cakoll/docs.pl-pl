---
title: 'Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy systemu Windows'
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
ms.openlocfilehash: 70229abddb831788f521f85747db1093c941ba8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967376"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy systemu Windows
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Można programowo usunąć lub ukryć kolumny w kontrolce Windows Forms <xref:System.Windows.Forms.DataGrid> przy użyciu właściwości i metod <xref:System.Windows.Forms.GridColumnStylesCollection> obiektów i <xref:System.Windows.Forms.DataGridColumnStyle> (które są elementami członkowskimi <xref:System.Windows.Forms.DataGridTableStyle> klasy).  
  
 Usunięte lub ukryte kolumny nadal istnieją w źródle danych, z którym jest powiązana siatka, i nadal można uzyskać do nich dostęp programowo. Nie są już widoczne w elemencie DataGrid.  
  
> [!NOTE]
> Jeśli aplikacja nie uzyskuje dostępu do określonych kolumn danych i nie chcesz ich wyświetlać w elemencie DataGrid, prawdopodobnie nie trzeba będzie uwzględniać ich w źródle danych w pierwszym miejscu.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Aby usunąć kolumnę z elementu DataGrid programowo  
  
1. W obszarze deklaracji formularza Zadeklaruj nowe wystąpienie <xref:System.Windows.Forms.DataGridTableStyle> klasy.  
  
2. <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> Ustaw właściwość na tabelę w źródle danych, do której chcesz zastosować styl. W poniższym przykładzie zastosowano <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> już właściwość, którą przyjmuje.  
  
3. Dodaj nowy <xref:System.Windows.Forms.DataGridTableStyle> obiekt do kolekcji Style tabeli elementu DataGrid.  
  
4. Wywołaj <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metodę <xref:System.Windows.Forms.DataGrid> kolekcji,określającindekskolumn<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolumny do usunięcia.  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Aby programowo ukryć kolumnę w elemencie DataGrid  
  
1. W obszarze deklaracji formularza Zadeklaruj nowe wystąpienie <xref:System.Windows.Forms.DataGridTableStyle> klasy.  
  
2. <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> Ustaw właściwość <xref:System.Windows.Forms.DataGridTableStyle> na tabelę w źródle danych, do której chcesz zastosować styl. Poniższy przykład kodu używa <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwości, która zakłada, że została już ustawiona.  
  
3. Dodaj nowy <xref:System.Windows.Forms.DataGridTableStyle> obiekt do kolekcji Style tabeli elementu DataGrid.  
  
4. Ukryj kolumnę, ustawiając jej `Width` właściwość na 0, określając indeks kolumn kolumny do ukrycia.  
  
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

- [Instrukcje: Zmień wyświetlane dane w czasie wykonywania w kontrolce DataGrid Windows Forms](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
