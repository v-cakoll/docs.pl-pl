---
title: Dodawanie danych do elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: ec4ad84a39afe21ef77507732e5e0e417d45f3e7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104289"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="30afa-102">Dodawanie danych do elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="30afa-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="30afa-103">Po utworzeniu <xref:System.Data.DataTable> i zdefiniuj strukturę przy użyciu kolumn i ograniczeń, można dodać nowe wiersze danych do tabeli.</span><span class="sxs-lookup"><span data-stu-id="30afa-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="30afa-104">Aby dodać nowy wiersz, należy zadeklarować nową zmienną jako typ <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="30afa-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="30afa-105">Nowy **DataRow** obiekt jest zwracany po wywołaniu <xref:System.Data.DataTable.NewRow%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="30afa-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="30afa-106">**DataTable** utworzy **DataRow** obiektu na podstawie struktury tabeli, zgodnie z definicją <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="30afa-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="30afa-107">Poniższy przykład przedstawia sposób tworzenia nowego wiersza, wywołując **NewRow** metody.</span><span class="sxs-lookup"><span data-stu-id="30afa-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="30afa-108">Możesz następnie manipulować wiersz nowo dodane przy użyciu indeksu lub nazwa kolumny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="30afa-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="30afa-109">Po wstawieniu danych do nowego wiersza **Dodaj** metoda służy do dodawania wierszy do <xref:System.Data.DataRowCollection>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="30afa-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="30afa-110">Można również wywołać **Dodaj** metodę, aby dodać nowy wiersz, przekazując tablicę wartości, wpisanych w formie <xref:System.Object>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="30afa-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="30afa-111">Przekazując tablicę wartości, wpisanych w formie **obiektu**, **Dodaj** metoda tworzy nowy wiersz w tabeli i ustawia jego wartości kolumny wartości w tablicy obiektu.</span><span class="sxs-lookup"><span data-stu-id="30afa-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="30afa-112">Należy pamiętać, że wartości w tablicy są dopasowywane sekwencyjnie do kolumn, w kolejności, w jakiej są wyświetlane w tabeli.</span><span class="sxs-lookup"><span data-stu-id="30afa-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="30afa-113">Poniższy przykład dodaje 10 wierszy do nowo utworzonego **klientów** tabeli.</span><span class="sxs-lookup"><span data-stu-id="30afa-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30afa-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30afa-114">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="30afa-115">Operowanie na danych w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="30afa-115">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="30afa-116">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="30afa-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
