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
ms.workload: dotnet
ms.openlocfilehash: 65257ec5f9ca51a795abca119e5449d6219042bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="59b40-102">Porady: usuwanie lub ukrywanie kolumn w formancie DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="59b40-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="59b40-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="59b40-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="59b40-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="59b40-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="59b40-105">Można programistycznie usunąć lub ukrywanie kolumn w formularzach systemu Windows <xref:System.Windows.Forms.DataGrid> formantu przy użyciu właściwości i metod <xref:System.Windows.Forms.GridColumnStylesCollection> i <xref:System.Windows.Forms.DataGridColumnStyle> obiektów (które są członkami <xref:System.Windows.Forms.DataGridTableStyle> klasy).</span><span class="sxs-lookup"><span data-stu-id="59b40-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="59b40-106">Usunięto lub ukrytych kolumn nadal istnieć w źródle danych, jest powiązany z siatki i nadal można uzyskać programistycznie.</span><span class="sxs-lookup"><span data-stu-id="59b40-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="59b40-107">Nie są one tylko widoczne w elemencie datagrid.</span><span class="sxs-lookup"><span data-stu-id="59b40-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59b40-108">Jeśli aplikacja nie dostępu do niektórych kolumn danych, a nie chcesz, aby były wyświetlane w elemencie datagrid, następnie prawdopodobnie nie jest konieczne do uwzględnienia w źródle danych, w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="59b40-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="59b40-109">Aby usunąć kolumnę z elementu DataGrid programowo</span><span class="sxs-lookup"><span data-stu-id="59b40-109">To delete a column from the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="59b40-110">W obszarze deklaracje w formularzu zadeklarować nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle> klasy.</span><span class="sxs-lookup"><span data-stu-id="59b40-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="59b40-111">Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> właściwości do tabeli w źródle danych, który chcesz zastosować styl.</span><span class="sxs-lookup"><span data-stu-id="59b40-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="59b40-112">W poniższym przykładzie użyto <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwość, która przyjęto założenie, że jest już ustawiony.</span><span class="sxs-lookup"><span data-stu-id="59b40-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="59b40-113">Dodaj nowe <xref:System.Windows.Forms.DataGridTableStyle> obiekt Kolekcja stylów tabeli w elemencie datagrid.</span><span class="sxs-lookup"><span data-stu-id="59b40-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="59b40-114">Wywołanie <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.DataGrid>w <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> zbierania, określając indeks kolumny kolumny do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="59b40-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="59b40-115">Aby programowo ukrywanie kolumn w elemencie DataGrid</span><span class="sxs-lookup"><span data-stu-id="59b40-115">To hide a column in the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="59b40-116">W obszarze deklaracje w formularzu zadeklarować nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridTableStyle> klasy.</span><span class="sxs-lookup"><span data-stu-id="59b40-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="59b40-117">Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość <xref:System.Windows.Forms.DataGridTableStyle> do tabeli w źródle danych, który chcesz zastosować styl.</span><span class="sxs-lookup"><span data-stu-id="59b40-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="59b40-118">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> właściwość, która przyjęto założenie, że jest już ustawiony.</span><span class="sxs-lookup"><span data-stu-id="59b40-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="59b40-119">Dodaj nowe <xref:System.Windows.Forms.DataGridTableStyle> obiekt Kolekcja stylów tabeli w elemencie datagrid.</span><span class="sxs-lookup"><span data-stu-id="59b40-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="59b40-120">Ukryj kolumnę przez ustawienie jej `Width` właściwości na wartość 0, określając indeks kolumny kolumny, aby ukryć.</span><span class="sxs-lookup"><span data-stu-id="59b40-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59b40-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59b40-121">See Also</span></span>  
 [<span data-ttu-id="59b40-122">Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59b40-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 [<span data-ttu-id="59b40-123">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59b40-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
