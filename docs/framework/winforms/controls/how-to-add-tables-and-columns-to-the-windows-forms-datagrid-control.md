---
title: 'Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy systemu Windows'
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
ms.openlocfilehash: bfb0296566fecc2029df16d91c9c04d7daa4b4b5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046152"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy systemu Windows

> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Dane można wyświetlić w kontrolce Windows Forms <xref:System.Windows.Forms.DataGrid> w tabelach i kolumnach, tworząc obiekty **Element DataGridTableStyle** i dodając je do obiektu **GridTableStylesCollection** <xref:System.Windows.Forms.DataGrid> , który jest dostępny za pomocą kontrolki Właściwość **TableStyles** . Każdy styl tabeli wyświetla zawartość dowolnej tabeli danych, która jest określona we właściwości MappingName obiektu **Element DataGridTableStyle** . Domyślnie styl tabeli bez określonych stylów kolumn będzie wyświetlał wszystkie kolumny w tej tabeli danych. Można ograniczyć, które kolumny z tabeli pojawiają się przez dodanie obiektów **DataGridColumnStyle** do obiektu **GridColumnStylesCollection** , do którego dostęp jest uzyskiwany za pośrednictwem właściwości **GridColumnStyles** każdego **Element DataGridTableStyle** Stream.

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Aby programowo dodać tabelę i kolumnę do składnika DataGrid

1. Aby wyświetlić dane w tabeli, należy najpierw powiązać <xref:System.Windows.Forms.DataGrid> formant z zestawem danych. Aby uzyskać więcej informacji, zobacz [jak: Powiąż formant DataGrid Windows Forms ze źródłem](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)danych.

    > [!CAUTION]
    > Podczas programowego określania stylów kolumn, zawsze twórz obiekty **DataGridColumnStyle** i Dodaj je do obiektu **GridColumnStylesCollection** przed dodaniem obiektów **Element DataGridTableStyle** do  **Obiekt GridTableStylesCollection** . Po dodaniu pustego obiektu **Element DataGridTableStyle** do kolekcji, obiekty **DataGridColumnStyle** są generowane automatycznie. W związku z tym, zostanie zgłoszony wyjątek, jeśli spróbujesz dodać nowe obiekty **DataGridColumnStyle** ze zduplikowanymi wartościami **mapowanianame** do obiektu **GridColumnStylesCollection** .

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
- [Instrukcje: Usuwanie lub ukrywanie kolumn w kontrolce DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
