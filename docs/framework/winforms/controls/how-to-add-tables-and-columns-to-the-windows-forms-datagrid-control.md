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
ms.openlocfilehash: 55e30744f57364fb37c9fde5b6bade6bab60fa26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925093"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="77bf6-102">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="77bf6-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="77bf6-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="77bf6-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="77bf6-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="77bf6-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="77bf6-105">Dane można wyświetlić w kontrolce Windows Forms <xref:System.Windows.Forms.DataGrid> w tabelach i kolumnach, tworząc obiekty **Element DataGridTableStyle** i dodając je do obiektu **GridTableStylesCollection** <xref:System.Windows.Forms.DataGrid> , który jest dostępny za pomocą kontrolki Właściwość **TableStyles** .</span><span class="sxs-lookup"><span data-stu-id="77bf6-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="77bf6-106">Każdy styl tabeli wyświetla zawartość dowolnej tabeli danych, która jest określona we właściwości MappingName obiektu **Element DataGridTableStyle** .</span><span class="sxs-lookup"><span data-stu-id="77bf6-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="77bf6-107">Domyślnie styl tabeli bez określonych stylów kolumn będzie wyświetlał wszystkie kolumny w tej tabeli danych.</span><span class="sxs-lookup"><span data-stu-id="77bf6-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="77bf6-108">Można ograniczyć, które kolumny z tabeli pojawiają się przez dodanie obiektów **DataGridColumnStyle** do obiektu **GridColumnStylesCollection** , do którego dostęp jest uzyskiwany za pośrednictwem właściwości **GridColumnStyles** każdego **Element DataGridTableStyle** Stream.</span><span class="sxs-lookup"><span data-stu-id="77bf6-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="77bf6-109">Aby programowo dodać tabelę i kolumnę do składnika DataGrid</span><span class="sxs-lookup"><span data-stu-id="77bf6-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="77bf6-110">Aby wyświetlić dane w tabeli, należy najpierw powiązać <xref:System.Windows.Forms.DataGrid> formant z zestawem danych.</span><span class="sxs-lookup"><span data-stu-id="77bf6-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="77bf6-111">Aby uzyskać więcej informacji, zobacz [jak: Powiąż formant DataGrid Windows Forms ze źródłem](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)danych.</span><span class="sxs-lookup"><span data-stu-id="77bf6-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="77bf6-112">Podczas programowego określania stylów kolumn, zawsze twórz obiekty **DataGridColumnStyle** i Dodaj je do obiektu **GridColumnStylesCollection** przed dodaniem obiektów **Element DataGridTableStyle** do  **Obiekt GridTableStylesCollection** .</span><span class="sxs-lookup"><span data-stu-id="77bf6-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="77bf6-113">Po dodaniu pustego obiektu **Element DataGridTableStyle** do kolekcji, obiekty **DataGridColumnStyle** są generowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="77bf6-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="77bf6-114">W związku z tym, zostanie zgłoszony wyjątek, jeśli spróbujesz dodać nowe obiekty **DataGridColumnStyle** ze zduplikowanymi wartościami **mapowanianame** do obiektu **GridColumnStylesCollection** .</span><span class="sxs-lookup"><span data-stu-id="77bf6-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2. <span data-ttu-id="77bf6-115">Zadeklaruj nowy styl tabeli i ustaw jego nazwę mapowania.</span><span class="sxs-lookup"><span data-stu-id="77bf6-115">Declare a new table style and set its mapping name.</span></span>  
  
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
  
3. <span data-ttu-id="77bf6-116">Zadeklaruj nowy styl kolumny i ustaw jego nazwę mapowania oraz inne właściwości.</span><span class="sxs-lookup"><span data-stu-id="77bf6-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
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
  
4. <span data-ttu-id="77bf6-117">Wywołaj metodę **Add** obiektu **GridColumnStylesCollection** , aby dodać kolumnę do stylu tabeli</span><span class="sxs-lookup"><span data-stu-id="77bf6-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5. <span data-ttu-id="77bf6-118">Wywołaj metodę **Add** obiektu **GridTableStylesCollection** , aby dodać styl tabeli do siatki danych.</span><span class="sxs-lookup"><span data-stu-id="77bf6-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="77bf6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77bf6-119">See also</span></span>

- [<span data-ttu-id="77bf6-120">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="77bf6-120">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="77bf6-121">Instrukcje: Usuwanie lub ukrywanie kolumn w kontrolce DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="77bf6-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
