---
title: Zmiany elementu DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 82fda2b5e92746b36ab7eb14eb645eca75e1e4bb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="datatable-edits"></a><span data-ttu-id="55ba3-102">Zmiany elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="55ba3-102">DataTable Edits</span></span>
<span data-ttu-id="55ba3-103">Podczas wprowadzania zmian do wartości kolumn <xref:System.Data.DataRow>, zmiany natychmiast są umieszczane w bieżącym stanie wiersza.</span><span class="sxs-lookup"><span data-stu-id="55ba3-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="55ba3-104"><xref:System.Data.DataRowState> Następnie ustawiono **zmodyfikowane**, a zmiany są akceptowane lub odrzucone, za pomocą <xref:System.Data.DataRow.AcceptChanges%2A> lub <xref:System.Data.DataRow.RejectChanges%2A> metody **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="55ba3-105">**DataRow** również udostępnia trzy metody, które umożliwia wstrzymanie stanu wiersza podczas edytowania go.</span><span class="sxs-lookup"><span data-stu-id="55ba3-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="55ba3-106">Te metody są <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, i <xref:System.Data.DataRow.CancelEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="55ba3-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="55ba3-107">Po zmodyfikowaniu wartości kolumn **DataRow** bezpośrednio, **DataRow** zarządza przy użyciu wartości w kolumnie **bieżącego**, **domyślne**, i **Oryginalnego** wiersz wersji.</span><span class="sxs-lookup"><span data-stu-id="55ba3-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="55ba3-108">Oprócz tych wersji wierszy **BeginEdit**, **EndEdit**, i **metoda CancelEdit** metody Użyj wersji czwartego wiersza: **proponowany**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="55ba3-109">Aby uzyskać więcej informacji dotyczących wersji wierszy, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="55ba3-109">For more information about row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="55ba3-110">**Proponowany** wersja wiersza istnieje podczas operacji edycji rozpoczynającego wywołując **BeginEdit** i który kończy się za pomocą **EndEdit** lub **metoda CancelEdit,**  , przez wywołanie **AcceptChanges** lub **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="55ba3-111">Podczas operacji edycji można zastosować logikę weryfikacji do poszczególnych kolumn wyniku obliczenia **ProposedValue** w **ColumnChanged** zdarzenie **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="55ba3-112">**ColumnChanged** przechowuje zdarzenia **DataColumnChangeEventArgs** tym najnowsze odwołanie do kolumny, która jest zmiana i **ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="55ba3-113">Po przeprowadzeniu oceny proponowanej wartości, możesz go zmodyfikować lub anulować edycję.</span><span class="sxs-lookup"><span data-stu-id="55ba3-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="55ba3-114">Po zakończeniu edycji wiersza są przenoszone poza **proponowany** stanu.</span><span class="sxs-lookup"><span data-stu-id="55ba3-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="55ba3-115">Można potwierdzić zmiany wywołując **EndEdit**, możesz je anulować przez wywołanie metody lub **metoda CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="55ba3-116">Należy pamiętać, że podczas **EndEdit** potwierdzenie edycji, **DataSet** faktycznie nie akceptuje zmian do **AcceptChanges** jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="55ba3-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="55ba3-117">Należy zauważyć, że jeśli wywołujesz **AcceptChanges** przed zakończył edycję z **EndEdit** lub **metoda CancelEdit**, zakończeniu edycji i **proponowany** wartości wierszy uznane za zaakceptowane dla obu **bieżącego** i **oryginalnego** wiersz wersji.</span><span class="sxs-lookup"><span data-stu-id="55ba3-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="55ba3-118">W ten sam sposób wywoływania **RejectChanges** kończy się Edycja i odrzuca **bieżącego** i **proponowany** wiersz wersji.</span><span class="sxs-lookup"><span data-stu-id="55ba3-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="55ba3-119">Wywoływanie **EndEdit** lub **metoda CancelEdit** po wywołaniu **AcceptChanges** lub **RejectChanges** nie obowiązuje, ponieważ Edycja zawiera już zakończone.</span><span class="sxs-lookup"><span data-stu-id="55ba3-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="55ba3-120">W poniższym przykładzie pokazano sposób użycia **BeginEdit** z **EndEdit** i **metoda CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="55ba3-121">Przykład sprawdza również **ProposedValue** w **ColumnChanged** zdarzeń i decyduje o tym, czy anulować edycję.</span><span class="sxs-lookup"><span data-stu-id="55ba3-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55ba3-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55ba3-122">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [<span data-ttu-id="55ba3-123">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="55ba3-123">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="55ba3-124">Obsługa zdarzeń elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="55ba3-124">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="55ba3-125">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="55ba3-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
