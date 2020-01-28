---
title: Dodawanie tabel i kolumn do kontrolki DataGrid
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
ms.openlocfilehash: 2db2e38c326cbcd78c58ee4fe00cd9ed20ae0e8a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747206"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Porady: dodawanie tabel i kolumn do formantu DataGrid formularzy systemu Windows

> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Dane można wyświetlić w kontrolce <xref:System.Windows.Forms.DataGrid> Windows Forms w tabelach i kolumnach przez utworzenie obiektów **Element DataGridTableStyle** i dodanie ich do obiektu **GridTableStylesCollection** , do którego dostęp można uzyskać za pomocą właściwości **TableStyles** kontrolki <xref:System.Windows.Forms.DataGrid>. Każdy styl tabeli wyświetla zawartość dowolnej tabeli danych, która jest określona we właściwości **MappingName** obiektu **Element DataGridTableStyle** . Domyślnie styl tabeli bez określonych stylów kolumn będzie wyświetlał wszystkie kolumny w tej tabeli danych. Można określić, które kolumny z tabeli mają być wyświetlane przez dodanie obiektów **DataGridColumnStyle** do obiektu **GridColumnStylesCollection** , do którego uzyskuje się dostęp za pośrednictwem właściwości **GridColumnStyles** każdego obiektu **Element DataGridTableStyle** .

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Aby programowo dodać tabelę i kolumnę do składnika DataGrid

1. Aby wyświetlić dane w tabeli, należy najpierw powiązać formant <xref:System.Windows.Forms.DataGrid> z zestawem danych. Aby uzyskać więcej informacji, zobacz [jak: powiązać formant DataGrid Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

    > [!CAUTION]
    > Podczas programowego określania stylów kolumn, zawsze twórz obiekty **DataGridColumnStyle** i Dodaj je do obiektu **GridColumnStylesCollection** przed dodaniem obiektów **Element DataGridTableStyle** do obiektu **GridTableStylesCollection** . Po dodaniu pustego obiektu **Element DataGridTableStyle** do kolekcji, obiekty **DataGridColumnStyle** są generowane automatycznie. W związku z tym, zostanie zgłoszony wyjątek, jeśli spróbujesz dodać nowe obiekty **DataGridColumnStyle** ze zduplikowanymi wartościami **mapowanianame** do obiektu **GridColumnStylesCollection** .

2. Zadeklaruj nowy styl tabeli i ustaw jego nazwę mapowania.

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

3. Zadeklaruj nowy styl kolumny i ustaw jego nazwę mapowania oraz inne właściwości.

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

4. Wywołaj metodę **Add** obiektu **GridColumnStylesCollection** , aby dodać kolumnę do stylu tabeli

    ```vb
    ts1.GridColumnStyles.Add(myDataCol)
    ```

    ```csharp
    ts1.GridColumnStyles.Add(myDataCol);
    ```

    ```cpp
    ts1->GridColumnStyles->Add(myDataCol);
    ```

5. Wywołaj metodę **Add** obiektu **GridTableStylesCollection** , aby dodać styl tabeli do siatki danych.

    ```vb
    DataGrid1.TableStyles.Add(ts1)
    ```

    ```csharp
    dataGrid1.TableStyles.Add(ts1);
    ```

    ```cpp
    dataGrid1->TableStyles->Add(ts1);
    ```

## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
