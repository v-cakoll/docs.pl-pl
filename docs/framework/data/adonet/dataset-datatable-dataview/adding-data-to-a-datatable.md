---
title: Dodawanie danych do elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 91c635e2bc2ed617e8c45171d9ec7d7359b9ca88
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205477"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="79f35-102">Dodawanie danych do elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="79f35-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="79f35-103">Po utworzeniu <xref:System.Data.DataTable> i zdefiniowaniu struktury przy użyciu kolumn i ograniczeń można dodać do tabeli nowe wiersze danych.</span><span class="sxs-lookup"><span data-stu-id="79f35-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="79f35-104">Aby dodać nowy wiersz, Zadeklaruj nową zmienną jako typ <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="79f35-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="79f35-105">Nowy obiekt **DataRow** jest zwracany po wywołaniu <xref:System.Data.DataTable.NewRow%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="79f35-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="79f35-106">Element **DataTable** następnie tworzy obiekt **DataRow** na podstawie struktury tabeli <xref:System.Data.DataColumnCollection>zdefiniowanej przez.</span><span class="sxs-lookup"><span data-stu-id="79f35-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="79f35-107">W poniższym przykładzie pokazano, jak utworzyć nowy wiersz przez wywołanie metody **NewRow** .</span><span class="sxs-lookup"><span data-stu-id="79f35-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="79f35-108">Następnie można manipulować nowo dodanym wierszem przy użyciu indeksu lub nazwy kolumny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="79f35-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="79f35-109">Po wstawieniu danych do nowego wiersza, Metoda **Dodaj** służy do dodawania wiersza do <xref:System.Data.DataRowCollection>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="79f35-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="79f35-110">Możesz również wywołać metodę **Add** , aby dodać nowy wiersz przez przekazanie tablicy wartości, <xref:System.Object>tak jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="79f35-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="79f35-111">Przekazanie tablicy wartości, wpisanej jako **obiekt**, do metody **Add** tworzy nowy wiersz wewnątrz tabeli i ustawia jego wartości kolumny na wartości w tablicy obiektów.</span><span class="sxs-lookup"><span data-stu-id="79f35-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="79f35-112">Należy zauważyć, że wartości w tablicy są dopasowane sekwencyjnie do kolumn, na podstawie kolejności ich wyświetlania w tabeli.</span><span class="sxs-lookup"><span data-stu-id="79f35-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="79f35-113">Poniższy przykład dodaje 10 wierszy do nowo utworzonej tabeli **Customers** .</span><span class="sxs-lookup"><span data-stu-id="79f35-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79f35-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79f35-114">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="79f35-115">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="79f35-115">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="79f35-116">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="79f35-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
