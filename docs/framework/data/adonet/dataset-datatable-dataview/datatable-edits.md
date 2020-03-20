---
title: Edycje elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 9e8c4204b51121b147fc7614066d9b849a687574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151263"
---
# <a name="datatable-edits"></a><span data-ttu-id="deed1-102">Edycje elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="deed1-102">DataTable Edits</span></span>
<span data-ttu-id="deed1-103">Po wprowadzeniu zmian w wartościach kolumn w <xref:System.Data.DataRow>, zmiany są natychmiast umieszczane w bieżącym stanie wiersza.</span><span class="sxs-lookup"><span data-stu-id="deed1-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="deed1-104">Następnie <xref:System.Data.DataRowState> ustawiono na **Zmodyfikowane,** a zmiany są akceptowane <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> lub odrzucane przy użyciu lub metod **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="deed1-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="deed1-105">**DataRow** zawiera również trzy metody, których można użyć do zawieszenia stanu wiersza podczas edytowania go.</span><span class="sxs-lookup"><span data-stu-id="deed1-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="deed1-106">Metody te <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A>są <xref:System.Data.DataRow.CancelEdit%2A>, i .</span><span class="sxs-lookup"><span data-stu-id="deed1-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="deed1-107">Podczas modyfikowania wartości kolumn bezpośrednio w **datarowy** **datarowy, DataRow** zarządza wartościami kolumn przy użyciu **bieżących,** **domyślnych**i **oryginalnych** wersji wierszy.</span><span class="sxs-lookup"><span data-stu-id="deed1-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="deed1-108">Oprócz tych wersji wiersza, **BeginEdit**, **EndEdit**i **CancelEdit** metody użyć wersji czwartego **wiersza: Proponowane**.</span><span class="sxs-lookup"><span data-stu-id="deed1-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="deed1-109">Aby uzyskać więcej informacji na temat wersji wierszy, zobacz [Stany wierszy i Wersje wierszy](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="deed1-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="deed1-110">**Proponowana** wersja wiersza istnieje podczas operacji edycji, która rozpoczyna się od wywołania **BeginEdit** i która kończy się za pomocą **EndEdit** lub **CancelEdit** lub wywołując **AcceptChanges** lub **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="deed1-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="deed1-111">Podczas operacji edycji można zastosować logikę sprawdzania poprawności do poszczególnych kolumn, oceniając **proposedValue** w **columnchanged** zdarzenia **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="deed1-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="deed1-112">**Zdarzenie ColumnChanged** zawiera **dane DataColumnChangeEventArgs,** które zachowują odwołanie do kolumny, która się zmienia, oraz do **wartości ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="deed1-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="deed1-113">Po dokonaniu oceny proponowanej wartości można ją zmodyfikować lub anulować.</span><span class="sxs-lookup"><span data-stu-id="deed1-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="deed1-114">Po zakończeniu edycji wiersz zostanie przeniesiony ze stanu **Proponowane.**</span><span class="sxs-lookup"><span data-stu-id="deed1-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="deed1-115">Możesz potwierdzić zmiany, dzwoniąc do **EndEdit**lub możesz je anulować, dzwoniąc do **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="deed1-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="deed1-116">Należy zauważyć, że podczas **endedit** potwierdzić zmiany, **DataSet** faktycznie nie akceptuje zmian, dopóki **AcceptChanges** jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="deed1-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="deed1-117">Należy również zauważyć, że jeśli wywołasz **AcceptChanges** przed zakończeniem edycji z **EndEdit** lub **CancelEdit**, edycja zostanie zakończona, a wartości **wiersza Proponowane** zostaną zaakceptowane zarówno dla wersji **wiersza Bieżący,** jak i **Oryginalny.**</span><span class="sxs-lookup"><span data-stu-id="deed1-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="deed1-118">W ten sam sposób wywołanie **RejectChanges** kończy edycję i odrzuca **bieżące** i **proponowane** wersje wierszy.</span><span class="sxs-lookup"><span data-stu-id="deed1-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="deed1-119">Wywołanie **EndEdit** lub **CancelEdit** po wywołaniu **AcceptChanges** lub **RejectChanges** nie ma wpływu, ponieważ edycja została już zakończona.</span><span class="sxs-lookup"><span data-stu-id="deed1-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="deed1-120">W poniższym przykładzie pokazano, jak używać **BeginEdit** z **EndEdit** i **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="deed1-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="deed1-121">W przykładzie sprawdza również **ProposedValue** w **ColumnChanged** zdarzenia i decyduje, czy anulować edycję.</span><span class="sxs-lookup"><span data-stu-id="deed1-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="deed1-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="deed1-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="deed1-123">Operowanie na danych w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="deed1-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="deed1-124">Obsługa zdarzeń elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="deed1-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="deed1-125">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="deed1-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
