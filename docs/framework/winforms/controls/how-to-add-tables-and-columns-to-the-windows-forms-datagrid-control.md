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
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="02669-102">Porady: dodawanie tabel i kolumn do formantu DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="02669-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="02669-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="02669-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="02669-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="02669-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="02669-105">Dane można wyświetlać w formularzach systemu Windows <xref:System.Windows.Forms.DataGrid> kontrolki tabele i kolumny, tworząc **Element DataGridTableStyle** obiektów oraz dodanie ich do **GridTableStylesCollection** obiektu, który jest dostępne za pośrednictwem <xref:System.Windows.Forms.DataGrid> formantu **TableStyles** właściwości.</span><span class="sxs-lookup"><span data-stu-id="02669-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="02669-106">Każdy styl tabeli Wyświetla zawartość niezależnie od tabeli danych jest określona w **Element DataGridTableStyle** obiektu **MappingName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="02669-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="02669-107">Domyślny styl tabeli o nie style kolumny określone będą wyświetlane wszystkie kolumny w tabeli danych.</span><span class="sxs-lookup"><span data-stu-id="02669-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="02669-108">Można ograniczyć, które kolumny z tabeli są wyświetlane przez dodanie **DataGridColumnStyle** obiekty do **kolekcji GridColumnStylesCollection** obiektu, który jest dostępny za pośrednictwem  **GridColumnStyles** właściwości każdego **Element DataGridTableStyle** obiektu.</span><span class="sxs-lookup"><span data-stu-id="02669-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="02669-109">Aby programowo Dodawanie tabel i kolumn do formantu DataGrid</span><span class="sxs-lookup"><span data-stu-id="02669-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="02669-110">Aby wyświetlić dane w tabeli, należy najpierw powiązać <xref:System.Windows.Forms.DataGrid> formantu do zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="02669-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="02669-111">Aby uzyskać więcej informacji, zobacz [porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="02669-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="02669-112">Podczas określania programowo Style kolumn, Zawsze twórz **DataGridColumnStyle** obiekty i dodaj je do **kolekcji GridColumnStylesCollection** obiektu przed dodaniem  **Element DataGridTableStyle** obiekty do **GridTableStylesCollection** obiektu.</span><span class="sxs-lookup"><span data-stu-id="02669-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="02669-113">Po dodaniu pustą **Element DataGridTableStyle** obiektu do kolekcji, **DataGridColumnStyle** obiekty są generowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="02669-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="02669-114">W związku z tym, zostanie wygenerowany wyjątek przy próbie dodania nowych **DataGridColumnStyle** obiektów ze zduplikowaną **MappingName** wartości do **kolekcji GridColumnStylesCollection**obiektu.</span><span class="sxs-lookup"><span data-stu-id="02669-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2.  <span data-ttu-id="02669-115">Deklarowanie nowy styl tabeli, a następnie ustaw nazwę jego mapowanie.</span><span class="sxs-lookup"><span data-stu-id="02669-115">Declare a new table style and set its mapping name.</span></span>  
  
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
  
3.  <span data-ttu-id="02669-116">Deklarowanie nowy styl kolumny i ustaw jego nazwę mapowania i inne właściwości.</span><span class="sxs-lookup"><span data-stu-id="02669-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
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
  
4.  <span data-ttu-id="02669-117">Wywołanie **Dodaj** metody **kolekcji GridColumnStylesCollection** obiekt, aby dodać kolumnę do styl tabeli</span><span class="sxs-lookup"><span data-stu-id="02669-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  <span data-ttu-id="02669-118">Wywołanie **Dodaj** metody **GridTableStylesCollection** obiekt do dodania stylów tabeli siatki danych.</span><span class="sxs-lookup"><span data-stu-id="02669-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="02669-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02669-119">See Also</span></span>  
 [<span data-ttu-id="02669-120">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="02669-120">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="02669-121">Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02669-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
