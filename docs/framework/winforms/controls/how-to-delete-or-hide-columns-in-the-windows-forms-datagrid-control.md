---
title: 'Instrukcje: Usuń lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms'
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
ms.openlocfilehash: 42a697992d4c6c75fe5958a7a17d6df8a7b4f6e4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724529"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="49a89-102">Instrukcje: Usuń lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49a89-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="49a89-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="49a89-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="49a89-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="49a89-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="49a89-105">Możesz programowo Usuń lub ukrywanie kolumn w formularzach Windows Forms <xref:System.Windows.Forms.DataGrid> kontroli przy użyciu właściwości i metod <xref:System.Windows.Forms.GridColumnStylesCollection> i <xref:System.Windows.Forms.DataGridColumnStyle> obiektów (które są członkami <xref:System.Windows.Forms.DataGridTableStyle> klasy).</span><span class="sxs-lookup"><span data-stu-id="49a89-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="49a89-106">Usunięto lub ukrytych kolumn nadal istnieją w źródle danych, jest powiązany z siatki i nadal można uzyskać programistycznie.</span><span class="sxs-lookup"><span data-stu-id="49a89-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="49a89-107">Oni po prostu nie są już widoczne w elemencie datagrid.</span><span class="sxs-lookup"><span data-stu-id="49a89-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49a89-108">Jeśli aplikacja nie uzyskuje dostępu do niektórych kolumn danych, a nie chcesz, aby były wyświetlane w elemencie datagrid, następnie prawdopodobnie nie jest to konieczne uwzględnić je w pierwszej kolejności w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="49a89-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="49a89-109">Aby programowo usunąć kolumnę z elementu DataGrid</span><span class="sxs-lookup"><span data-stu-id="49a89-109">To delete a column from the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="49a89-110">W obszarze deklaracje w formularzu, należy zadeklarować nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle> klasy.</span><span class="sxs-lookup"><span data-stu-id="49a89-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="49a89-111">Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> właściwości do tabeli w źródle danych, którą chcesz zastosować styl.</span><span class="sxs-lookup"><span data-stu-id="49a89-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="49a89-112">W poniższym przykładzie użyto <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwość, która zakłada, że jest już ustawiona.</span><span class="sxs-lookup"><span data-stu-id="49a89-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="49a89-113">Dodaj nowy <xref:System.Windows.Forms.DataGridTableStyle> obiektu do kolekcji style tabeli w elemencie datagrid.</span><span class="sxs-lookup"><span data-stu-id="49a89-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="49a89-114">Wywołaj <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.DataGrid>firmy <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> zbierania, określając indeks kolumny kolumny do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="49a89-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="49a89-115">Aby ukryć kolumnę w elemencie DataGrid programowe</span><span class="sxs-lookup"><span data-stu-id="49a89-115">To hide a column in the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="49a89-116">W obszarze deklaracje w formularzu, należy zadeklarować nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle> klasy.</span><span class="sxs-lookup"><span data-stu-id="49a89-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="49a89-117">Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość <xref:System.Windows.Forms.DataGridTableStyle> do tabeli w źródle danych, którą chcesz zastosować styl.</span><span class="sxs-lookup"><span data-stu-id="49a89-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="49a89-118">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwość, która zakłada, że jest już ustawiona.</span><span class="sxs-lookup"><span data-stu-id="49a89-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="49a89-119">Dodaj nowy <xref:System.Windows.Forms.DataGridTableStyle> obiektu do kolekcji style tabeli w elemencie datagrid.</span><span class="sxs-lookup"><span data-stu-id="49a89-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="49a89-120">Ukryj kolumnę, ustawiając jego `Width` właściwości na wartość 0, określając indeks kolumny, aby ukryć kolumny.</span><span class="sxs-lookup"><span data-stu-id="49a89-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49a89-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49a89-121">See also</span></span>
- [<span data-ttu-id="49a89-122">Instrukcje: Zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49a89-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="49a89-123">Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49a89-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
