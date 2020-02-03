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
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="12d3d-102">Porady: dodawanie tabel i kolumn do formantu DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="12d3d-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>

> [!NOTE]
> <span data-ttu-id="12d3d-103">Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="12d3d-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="12d3d-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="12d3d-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

<span data-ttu-id="12d3d-105">Dane można wyświetlić w kontrolce <xref:System.Windows.Forms.DataGrid> Windows Forms w tabelach i kolumnach przez utworzenie obiektów **Element DataGridTableStyle** i dodanie ich do obiektu **GridTableStylesCollection** , do którego dostęp można uzyskać za pomocą właściwości **TableStyles** kontrolki <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="12d3d-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="12d3d-106">Każdy styl tabeli wyświetla zawartość dowolnej tabeli danych, która jest określona we właściwości **MappingName** obiektu **Element DataGridTableStyle** .</span><span class="sxs-lookup"><span data-stu-id="12d3d-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="12d3d-107">Domyślnie styl tabeli bez określonych stylów kolumn będzie wyświetlał wszystkie kolumny w tej tabeli danych.</span><span class="sxs-lookup"><span data-stu-id="12d3d-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="12d3d-108">Można określić, które kolumny z tabeli mają być wyświetlane przez dodanie obiektów **DataGridColumnStyle** do obiektu **GridColumnStylesCollection** , do którego uzyskuje się dostęp za pośrednictwem właściwości **GridColumnStyles** każdego obiektu **Element DataGridTableStyle** .</span><span class="sxs-lookup"><span data-stu-id="12d3d-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="12d3d-109">Aby programowo dodać tabelę i kolumnę do składnika DataGrid</span><span class="sxs-lookup"><span data-stu-id="12d3d-109">To add a table and column to a DataGrid programmatically</span></span>

1. <span data-ttu-id="12d3d-110">Aby wyświetlić dane w tabeli, należy najpierw powiązać formant <xref:System.Windows.Forms.DataGrid> z zestawem danych.</span><span class="sxs-lookup"><span data-stu-id="12d3d-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="12d3d-111">Aby uzyskać więcej informacji, zobacz [jak: powiązać formant DataGrid Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="12d3d-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>

    > [!CAUTION]
    > <span data-ttu-id="12d3d-112">Podczas programowego określania stylów kolumn, zawsze twórz obiekty **DataGridColumnStyle** i Dodaj je do obiektu **GridColumnStylesCollection** przed dodaniem obiektów **Element DataGridTableStyle** do obiektu **GridTableStylesCollection** .</span><span class="sxs-lookup"><span data-stu-id="12d3d-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="12d3d-113">Po dodaniu pustego obiektu **Element DataGridTableStyle** do kolekcji, obiekty **DataGridColumnStyle** są generowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="12d3d-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="12d3d-114">W związku z tym, zostanie zgłoszony wyjątek, jeśli spróbujesz dodać nowe obiekty **DataGridColumnStyle** ze zduplikowanymi wartościami **mapowanianame** do obiektu **GridColumnStylesCollection** .</span><span class="sxs-lookup"><span data-stu-id="12d3d-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>

2. <span data-ttu-id="12d3d-115">Zadeklaruj nowy styl tabeli i ustaw jego nazwę mapowania.</span><span class="sxs-lookup"><span data-stu-id="12d3d-115">Declare a new table style and set its mapping name.</span></span>

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

3. <span data-ttu-id="12d3d-116">Zadeklaruj nowy styl kolumny i ustaw jego nazwę mapowania oraz inne właściwości.</span><span class="sxs-lookup"><span data-stu-id="12d3d-116">Declare a new column style and set its mapping name and other properties.</span></span>

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

4. <span data-ttu-id="12d3d-117">Wywołaj metodę **Add** obiektu **GridColumnStylesCollection** , aby dodać kolumnę do stylu tabeli</span><span class="sxs-lookup"><span data-stu-id="12d3d-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>

    ```vb
    ts1.GridColumnStyles.Add(myDataCol)
    ```

    ```csharp
    ts1.GridColumnStyles.Add(myDataCol);
    ```

    ```cpp
    ts1->GridColumnStyles->Add(myDataCol);
    ```

5. <span data-ttu-id="12d3d-118">Wywołaj metodę **Add** obiektu **GridTableStylesCollection** , aby dodać styl tabeli do siatki danych.</span><span class="sxs-lookup"><span data-stu-id="12d3d-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>

    ```vb
    DataGrid1.TableStyles.Add(ts1)
    ```

    ```csharp
    dataGrid1.TableStyles.Add(ts1);
    ```

    ```cpp
    dataGrid1->TableStyles->Add(ts1);
    ```

## <a name="see-also"></a><span data-ttu-id="12d3d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12d3d-119">See also</span></span>

- [<span data-ttu-id="12d3d-120">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="12d3d-120">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="12d3d-121">Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12d3d-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
