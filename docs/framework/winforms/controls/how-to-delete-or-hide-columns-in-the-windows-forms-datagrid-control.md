---
title: Usuwanie lub ukrywanie kolumn w kontrolce DataGrid
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
ms.openlocfilehash: c730be934e9b978bdaf09bc7e668b4318077fba5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743296"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Porady: usuwanie lub ukrywanie kolumn w formancie DataGrid formularzy systemu Windows
> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Można programowo usunąć lub ukryć kolumny w kontrolce <xref:System.Windows.Forms.DataGrid> Windows Forms przy użyciu właściwości i metod <xref:System.Windows.Forms.GridColumnStylesCollection> i <xref:System.Windows.Forms.DataGridColumnStyle> obiektów (które są członkami klasy <xref:System.Windows.Forms.DataGridTableStyle>).  
  
 Usunięte lub ukryte kolumny nadal istnieją w źródle danych, z którym jest powiązana siatka, i nadal można uzyskać do nich dostęp programowo. Nie są już widoczne w elemencie DataGrid.  
  
> [!NOTE]
> Jeśli aplikacja nie uzyskuje dostępu do określonych kolumn danych i nie chcesz ich wyświetlać w elemencie DataGrid, prawdopodobnie nie trzeba będzie uwzględniać ich w źródle danych w pierwszym miejscu.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Aby usunąć kolumnę z elementu DataGrid programowo  
  
1. W obszarze deklaracji formularza Zadeklaruj nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2. Ustaw właściwość <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> na tabelę w źródle danych, do której chcesz zastosować styl. W poniższym przykładzie zastosowano już Właściwość <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, która została przyjęta.  
  
3. Dodaj nowy obiekt <xref:System.Windows.Forms.DataGridTableStyle> do kolekcji Style tabeli elementu DataGrid.  
  
4. Wywołaj metodę <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A>ową kolekcji <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> <xref:System.Windows.Forms.DataGrid>, określając indeks kolumn kolumny do usunięcia.  
  
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
  
1. W obszarze deklaracji formularza Zadeklaruj nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2. Ustaw właściwość <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> <xref:System.Windows.Forms.DataGridTableStyle> na tabelę w źródle danych, do której chcesz zastosować styl. Poniższy przykład kodu używa właściwości <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, która przyjmuje, że została już ustawiona.  
  
3. Dodaj nowy obiekt <xref:System.Windows.Forms.DataGridTableStyle> do kolekcji Style tabeli elementu DataGrid.  
  
4. Ukryj kolumnę, ustawiając jej Właściwość `Width` na 0, określając indeks kolumn kolumny do ukrycia.  
  
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

- [Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy Windows Forms](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
