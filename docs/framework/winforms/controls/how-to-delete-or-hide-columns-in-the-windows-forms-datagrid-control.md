---
title: 'Porady: usuwanie lub ukrywanie kolumn w formancie DataGrid formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d89f14d034c1050d364282c04424b1326bcff9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Porady: usuwanie lub ukrywanie kolumn w formancie DataGrid formularzy systemu Windows
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Można programistycznie usunąć lub ukrywanie kolumn w formularzach systemu Windows <xref:System.Windows.Forms.DataGrid> formantu przy użyciu właściwości i metod <xref:System.Windows.Forms.GridColumnStylesCollection> i <xref:System.Windows.Forms.DataGridColumnStyle> obiektów (które są członkami <xref:System.Windows.Forms.DataGridTableStyle> klasy).  
  
 Usunięto lub ukrytych kolumn nadal istnieć w źródle danych, jest powiązany z siatki i nadal można uzyskać programistycznie. Nie są one tylko widoczne w elemencie datagrid.  
  
> [!NOTE]
>  Jeśli aplikacja nie dostępu do niektórych kolumn danych, a nie chcesz, aby były wyświetlane w elemencie datagrid, następnie prawdopodobnie nie jest konieczne do uwzględnienia w źródle danych, w pierwszej kolejności.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Aby usunąć kolumnę z elementu DataGrid programowo  
  
1.  W obszarze deklaracje w formularzu zadeklarować nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle> klasy.  
  
2.  Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> właściwości do tabeli w źródle danych, który chcesz zastosować styl. W poniższym przykładzie użyto <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwość, która przyjęto założenie, że jest już ustawiony.  
  
3.  Dodaj nowe <xref:System.Windows.Forms.DataGridTableStyle> obiekt Kolekcja stylów tabeli w elemencie datagrid.  
  
4.  Wywołanie <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.DataGrid>w <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> zbierania, określając indeks kolumny kolumny do usunięcia.  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Aby programowo ukrywanie kolumn w elemencie DataGrid  
  
1.  W obszarze deklaracje w formularzu zadeklarować nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle> klasy.  
  
2.  Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość <xref:System.Windows.Forms.DataGridTableStyle> do tabeli w źródle danych, który chcesz zastosować styl. Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwość, która przyjęto założenie, że jest już ustawiony.  
  
3.  Dodaj nowe <xref:System.Windows.Forms.DataGridTableStyle> obiekt Kolekcja stylów tabeli w elemencie datagrid.  
  
4.  Ukryj kolumnę przez ustawienie jej `Width` właściwości na wartość 0, określając indeks kolumny kolumny, aby ukryć.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid formularzy systemu Windows](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 [Porady: Dodawanie tabel i kolumn do systemu Windows formantu DataGrid formularzy](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
