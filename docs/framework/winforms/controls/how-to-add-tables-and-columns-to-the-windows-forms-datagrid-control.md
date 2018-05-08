---
title: 'Porady: dodawanie tabel i kolumn do formantu DataGrid formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: fc8161ea29da92f5dcc2e76f956f3fecd6140acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Porady: dodawanie tabel i kolumn do formantu DataGrid formularzy systemu Windows
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Dane można wyświetlać w formularzach systemu Windows <xref:System.Windows.Forms.DataGrid> kontrolki tabele i kolumny, tworząc **Element DataGridTableStyle** obiektów oraz dodanie ich do **GridTableStylesCollection** obiektu, który jest dostępne za pośrednictwem <xref:System.Windows.Forms.DataGrid> formantu **TableStyles** właściwości. Każdy styl tabeli Wyświetla zawartość niezależnie od tabeli danych jest określona w **Element DataGridTableStyle** obiektu **MappingName** właściwości. Domyślny styl tabeli o nie style kolumny określone będą wyświetlane wszystkie kolumny w tabeli danych. Można ograniczyć, które kolumny z tabeli są wyświetlane przez dodanie **DataGridColumnStyle** obiekty do **kolekcji GridColumnStylesCollection** obiektu, który jest dostępny za pośrednictwem  **GridColumnStyles** właściwości każdego **Element DataGridTableStyle** obiektu.  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Aby programowo Dodawanie tabel i kolumn do formantu DataGrid  
  
1.  Aby wyświetlić dane w tabeli, należy najpierw powiązać <xref:System.Windows.Forms.DataGrid> formantu do zestawu danych. Aby uzyskać więcej informacji, zobacz [porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
    > [!CAUTION]
    >  Podczas określania programowo Style kolumn, Zawsze twórz **DataGridColumnStyle** obiekty i dodaj je do **kolekcji GridColumnStylesCollection** obiektu przed dodaniem  **Element DataGridTableStyle** obiekty do **GridTableStylesCollection** obiektu. Po dodaniu pustą **Element DataGridTableStyle** obiektu do kolekcji, **DataGridColumnStyle** obiekty są generowane automatycznie. W związku z tym, zostanie wygenerowany wyjątek przy próbie dodania nowych **DataGridColumnStyle** obiektów ze zduplikowaną **MappingName** wartości do **kolekcji GridColumnStylesCollection**obiektu.  
  
2.  Deklarowanie nowy styl tabeli, a następnie ustaw nazwę jego mapowanie.  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3.  Deklarowanie nowy styl kolumny i ustaw jego nazwę mapowania i inne właściwości.  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4.  Wywołanie **Dodaj** metody **kolekcji GridColumnStylesCollection** obiekt, aby dodać kolumnę do styl tabeli  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  Wywołanie **Dodaj** metody **GridTableStylesCollection** obiekt do dodania stylów tabeli siatki danych.  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
