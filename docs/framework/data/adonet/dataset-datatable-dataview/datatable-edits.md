---
title: Edycje elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: a970ebda76f5bb6bdea704dabef2ee305436c613
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205018"
---
# <a name="datatable-edits"></a><span data-ttu-id="98042-102">Edycje elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="98042-102">DataTable Edits</span></span>
<span data-ttu-id="98042-103">Po wprowadzeniu zmian w wartościach kolumn w <xref:System.Data.DataRow>, zmiany są natychmiast umieszczane w bieżącym stanie wiersza.</span><span class="sxs-lookup"><span data-stu-id="98042-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="98042-104"><xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A>Następnie jest ustawiona na wartość zmodyfikowano, a zmiany zostaną zaakceptowane lub odrzucone przy użyciu metod lub obiektu DataRow. <xref:System.Data.DataRowState></span><span class="sxs-lookup"><span data-stu-id="98042-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="98042-105">Ten element **DataRow** zawiera również trzy metody, których można użyć w celu zawieszenia stanu wiersza podczas jego edytowania.</span><span class="sxs-lookup"><span data-stu-id="98042-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="98042-106">Te metody to <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>i <xref:System.Data.DataRow.CancelEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="98042-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="98042-107">W przypadku bezpośredniej modyfikacji wartości kolumn w elemencie **DataRow** element **DataRow** zarządza wartościami kolumn przy użyciu **bieżących**, **domyślnych**i **oryginalnych** wersji wiersza.</span><span class="sxs-lookup"><span data-stu-id="98042-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="98042-108">Oprócz tych wersji wiersza metody **elementu BeginEdit**, **EndEdit**i **CancelEdit** używają czwartej wersji wiersza: **Proponowane**.</span><span class="sxs-lookup"><span data-stu-id="98042-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="98042-109">Aby uzyskać więcej informacji o wersjach wierszy, zobacz [Stany wiersza i wersje wierszy](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="98042-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="98042-110">**Proponowana** wersja wiersza istnieje podczas operacji edycji rozpoczynającej się od wywołania **elementu BeginEdit** i kończącą się za pomocą **EndEdit** lub **CancelEdit** lub przez wywołanie metody **AcceptChanges** lub **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="98042-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="98042-111">Podczas operacji edycji można zastosować logikę walidacji do poszczególnych kolumn, oceniając **ProposedValue** w zdarzeniu **ColumnChanged** **elementu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="98042-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="98042-112">Zdarzenie **ColumnChanged** przechowuje **DataColumnChangeEventArgs** , które zachowuje odwołanie do kolumny, która jest zmieniana, oraz do **ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="98042-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="98042-113">Po obliczeniu proponowanej wartości można ją zmodyfikować lub anulować edycję.</span><span class="sxs-lookup"><span data-stu-id="98042-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="98042-114">Po zakończeniu edycji wiersz jest przenoszony z proponowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="98042-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="98042-115">Można potwierdzić zmiany przez wywołanie **EndEdit**lub anulować je przez wywołanie **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="98042-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="98042-116">Należy pamiętać, że podczas gdy **EndEdit** potwierdza modyfikacje, **zestaw danych** nie akceptuje zmian do momentu wywołania metody **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="98042-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="98042-117">Należy również pamiętać, że w przypadku wywołania metody **AcceptChanges** przed zakończeniem edycji przy użyciu **EndEdit** lub **CancelEdit**, Edycja zostanie zakończona, a **proponowane** wartości wierszy są akceptowane zarówno dla **bieżącej** , jak i **oryginalnej** wersji wiersza.</span><span class="sxs-lookup"><span data-stu-id="98042-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="98042-118">W ten sam sposób wywołanie **RejectChanges** powoduje zakończenie edycji i odrzucenie **bieżącej** i proponowanej wersji wiersza.</span><span class="sxs-lookup"><span data-stu-id="98042-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="98042-119">Wywołanie **EndEdit** lub **CancelEdit** po wywołaniu metody **AcceptChanges** lub **RejectChanges** nie ma żadnego efektu, ponieważ edytowanie już się zakończyło.</span><span class="sxs-lookup"><span data-stu-id="98042-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="98042-120">W poniższym przykładzie pokazano, jak używać **elementu BeginEdit** z **EndEdit** i **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="98042-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="98042-121">Przykład sprawdza także **ProposedValue** w zdarzeniu **ColumnChanged** i decyduje o tym, czy anulować edycję.</span><span class="sxs-lookup"><span data-stu-id="98042-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""       
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=   
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";       
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);    
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="98042-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98042-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="98042-123">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="98042-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="98042-124">Obsługa zdarzeń elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="98042-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="98042-125">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="98042-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
