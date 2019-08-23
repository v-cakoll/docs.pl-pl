---
title: 'Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy systemu Windows'
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
ms.openlocfilehash: 70229abddb831788f521f85747db1093c941ba8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967376"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="a2eb6-102">Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a2eb6-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="a2eb6-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="a2eb6-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="a2eb6-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a2eb6-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="a2eb6-105">Można programowo usunąć lub ukryć kolumny w kontrolce Windows Forms <xref:System.Windows.Forms.DataGrid> przy użyciu właściwości i metod <xref:System.Windows.Forms.GridColumnStylesCollection> obiektów i <xref:System.Windows.Forms.DataGridColumnStyle> (które są elementami członkowskimi <xref:System.Windows.Forms.DataGridTableStyle> klasy).</span><span class="sxs-lookup"><span data-stu-id="a2eb6-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="a2eb6-106">Usunięte lub ukryte kolumny nadal istnieją w źródle danych, z którym jest powiązana siatka, i nadal można uzyskać do nich dostęp programowo.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="a2eb6-107">Nie są już widoczne w elemencie DataGrid.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2eb6-108">Jeśli aplikacja nie uzyskuje dostępu do określonych kolumn danych i nie chcesz ich wyświetlać w elemencie DataGrid, prawdopodobnie nie trzeba będzie uwzględniać ich w źródle danych w pierwszym miejscu.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="a2eb6-109">Aby usunąć kolumnę z elementu DataGrid programowo</span><span class="sxs-lookup"><span data-stu-id="a2eb6-109">To delete a column from the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="a2eb6-110">W obszarze deklaracji formularza Zadeklaruj nowe wystąpienie <xref:System.Windows.Forms.DataGridTableStyle> klasy.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="a2eb6-111"><xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> Ustaw właściwość na tabelę w źródle danych, do której chcesz zastosować styl.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="a2eb6-112">W poniższym przykładzie zastosowano <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> już właściwość, którą przyjmuje.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="a2eb6-113">Dodaj nowy <xref:System.Windows.Forms.DataGridTableStyle> obiekt do kolekcji Style tabeli elementu DataGrid.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="a2eb6-114">Wywołaj <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metodę <xref:System.Windows.Forms.DataGrid> kolekcji,określającindekskolumn<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolumny do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="a2eb6-115">Aby programowo ukryć kolumnę w elemencie DataGrid</span><span class="sxs-lookup"><span data-stu-id="a2eb6-115">To hide a column in the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="a2eb6-116">W obszarze deklaracji formularza Zadeklaruj nowe wystąpienie <xref:System.Windows.Forms.DataGridTableStyle> klasy.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="a2eb6-117"><xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> Ustaw właściwość <xref:System.Windows.Forms.DataGridTableStyle> na tabelę w źródle danych, do której chcesz zastosować styl.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="a2eb6-118">Poniższy przykład kodu używa <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwości, która zakłada, że została już ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="a2eb6-119">Dodaj nowy <xref:System.Windows.Forms.DataGridTableStyle> obiekt do kolekcji Style tabeli elementu DataGrid.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="a2eb6-120">Ukryj kolumnę, ustawiając jej `Width` właściwość na 0, określając indeks kolumn kolumny do ukrycia.</span><span class="sxs-lookup"><span data-stu-id="a2eb6-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2eb6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2eb6-121">See also</span></span>

- [<span data-ttu-id="a2eb6-122">Instrukcje: Zmień wyświetlane dane w czasie wykonywania w kontrolce DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a2eb6-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="a2eb6-123">Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a2eb6-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
