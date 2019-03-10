---
title: 'Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms'
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
ms.openlocfilehash: e222227d6283555fa4ec25fe1e5d8e661296034f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709162"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="50ccf-102">Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50ccf-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="50ccf-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="50ccf-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="50ccf-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="50ccf-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="50ccf-105">Można wyświetlić dane w formularzach Windows Forms <xref:System.Windows.Forms.DataGrid> formantu w tabelach i kolumnach, tworząc **Element DataGridTableStyle** obiektów oraz dodać je do **GridTableStylesCollection** obiektu, który jest dostępne za pośrednictwem <xref:System.Windows.Forms.DataGrid> kontrolki **TableStyles** właściwości.</span><span class="sxs-lookup"><span data-stu-id="50ccf-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="50ccf-106">Każdy styl tabeli Wyświetla zawartość tabeli niezależnie od danych jest określona w **Element DataGridTableStyle** obiektu **MappingName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="50ccf-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="50ccf-107">Domyślnie styl tabeli za pomocą nie style kolumny określone wyświetli wszystkie kolumny w tabeli danych.</span><span class="sxs-lookup"><span data-stu-id="50ccf-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="50ccf-108">Można ograniczyć, które kolumny z tabeli są wyświetlane, dodając **DataGridColumnStyle** obiekty do **kolekcji GridColumnStylesCollection** obiektu, który jest dostępny za pośrednictwem  **GridColumnStyles** właściwości każdego **Element DataGridTableStyle** obiektu.</span><span class="sxs-lookup"><span data-stu-id="50ccf-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="50ccf-109">Aby programowo dodać tabel i kolumn z elementem DataGrid</span><span class="sxs-lookup"><span data-stu-id="50ccf-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="50ccf-110">Aby wyświetlić dane w tabeli, najpierw musisz powiązać <xref:System.Windows.Forms.DataGrid> kontrolki do zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="50ccf-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="50ccf-111">Aby uzyskać więcej informacji, zobacz [jak: Powiązywanie formantu DataGrid formularzy Windows ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="50ccf-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="50ccf-112">Podczas określania programowo Style kolumn, Zawsze twórz **DataGridColumnStyle** obiektów i dodaj je do **kolekcji GridColumnStylesCollection** obiektu przed dodaniem  **Element DataGridTableStyle** obiekty do **GridTableStylesCollection** obiektu.</span><span class="sxs-lookup"><span data-stu-id="50ccf-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="50ccf-113">Po dodaniu pustą **Element DataGridTableStyle** obiektu do kolekcji, **DataGridColumnStyle** obiekty są generowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="50ccf-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="50ccf-114">W związku z tym, zostanie zgłoszony wyjątek, Jeśli spróbujesz dodać nowe **DataGridColumnStyle** obiekty ze zduplikowanymi **MappingName** wartości **kolekcji GridColumnStylesCollection**obiektu.</span><span class="sxs-lookup"><span data-stu-id="50ccf-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2.  <span data-ttu-id="50ccf-115">Zadeklaruj nowy styl tabeli i ustaw jego nazwę mapowania.</span><span class="sxs-lookup"><span data-stu-id="50ccf-115">Declare a new table style and set its mapping name.</span></span>  
  
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
  
3.  <span data-ttu-id="50ccf-116">Zadeklaruj nowy styl kolumny i ustaw jego nazwę mapowania i inne właściwości.</span><span class="sxs-lookup"><span data-stu-id="50ccf-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
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
  
4.  <span data-ttu-id="50ccf-117">Wywołaj **Dodaj** metody **kolekcji GridColumnStylesCollection** obiekt, aby dodać kolumnę do styl tabeli</span><span class="sxs-lookup"><span data-stu-id="50ccf-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  <span data-ttu-id="50ccf-118">Wywołaj **Dodaj** metody **GridTableStylesCollection** obiekt do dodania styl tabeli do siatki danych.</span><span class="sxs-lookup"><span data-stu-id="50ccf-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="50ccf-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50ccf-119">See also</span></span>
- [<span data-ttu-id="50ccf-120">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="50ccf-120">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="50ccf-121">Instrukcje: Usuń lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50ccf-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
