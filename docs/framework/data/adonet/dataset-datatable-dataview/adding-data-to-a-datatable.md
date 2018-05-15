---
title: Dodawanie danych do elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: c58f64dba0bceb4a35c67e16193a6627837436e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="41428-102">Dodawanie danych do elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="41428-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="41428-103">Po utworzeniu <xref:System.Data.DataTable> i zdefiniować jego struktury, przy użyciu kolumn i ograniczeń, można dodać nowe wiersze danych do tabeli.</span><span class="sxs-lookup"><span data-stu-id="41428-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="41428-104">Aby dodać nowy wiersz, należy zadeklarować nowej zmiennej jako typ <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="41428-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="41428-105">Nowy **DataRow** obiekt jest zwracany w przypadku wywołania <xref:System.Data.DataTable.NewRow%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="41428-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="41428-106">**DataTable** tworzy następnie **DataRow** obiekt na podstawie struktury tabeli, zgodnie z definicją w <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="41428-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="41428-107">Poniższy przykład przedstawia sposób tworzenia nowego wiersza przez wywołanie metody **NewRow** metody.</span><span class="sxs-lookup"><span data-stu-id="41428-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="41428-108">Następnie można manipulować, korzystając nowo dodany wiersz za pomocą indeksu lub nazwa kolumny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="41428-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="41428-109">Po wstawieniu danych do nowego wiersza **Dodaj** metoda jest używana do dodania do wiersza <xref:System.Data.DataRowCollection>, pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="41428-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="41428-110">Możesz także wywołać **Dodaj** metodę, aby dodać nowy wiersz przekazując w tablicy wartości wpisanych jako <xref:System.Object>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="41428-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="41428-111">Przekazanie tablicy wartości wpisanych jako **obiektu**, do **Dodaj** — metoda tworzy nowy wiersz w tabeli i ustawia jej wartości w kolumnach wartości w tablicy object.</span><span class="sxs-lookup"><span data-stu-id="41428-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="41428-112">Należy pamiętać, sekwencyjnie zgodne wartości w tablicy kolumn, na podstawie kolejności, w którym są wyświetlane w tabeli.</span><span class="sxs-lookup"><span data-stu-id="41428-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="41428-113">W poniższym przykładzie dodano 10 wierszy do nowo utworzony **klientów** tabeli.</span><span class="sxs-lookup"><span data-stu-id="41428-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="41428-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41428-114">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="41428-115">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="41428-115">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="41428-116">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="41428-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
