---
title: Znajdowanie wierszy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 72af4b049153ce647cc1ceb2d40c3b17cc7ed988
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206554"
---
# <a name="finding-rows"></a><span data-ttu-id="2a86b-102">Znajdowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="2a86b-102">Finding Rows</span></span>
<span data-ttu-id="2a86b-103">Możesz wyszukać wierszy, zgodnie z ich wartości kluczy sortowania + przy użyciu <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="2a86b-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="2a86b-104">Rozróżnianie wielkości liter wyszukiwania wartości w **znaleźć** i **FindRows** metody jest określana przez **CaseSensitive** właściwości podstawowych <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="2a86b-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="2a86b-105">Wyszukiwanie wartości muszą być zgodne istniejącej wartości kluczy sortowania + w całości w celu zwrócenia wyników.</span><span class="sxs-lookup"><span data-stu-id="2a86b-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="2a86b-106">**Znaleźć** metoda zwraca liczbę całkowitą z indeksem <xref:System.Data.DataRowView> który pasuje do kryteriów wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="2a86b-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="2a86b-107">Jeśli więcej niż jeden wiersz pasujących do kryteriów wyszukiwania, indeks pierwszego dopasowania **DataRowView** jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="2a86b-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="2a86b-108">W przypadku nieodnalezienia żadnych dopasowań **znaleźć** zwraca wartość -1.</span><span class="sxs-lookup"><span data-stu-id="2a86b-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="2a86b-109">Aby zwrócić wyniki wyszukiwania, które pasuje wiele wierszy, użyj **FindRows** metody.</span><span class="sxs-lookup"><span data-stu-id="2a86b-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="2a86b-110">**FindRows** działa podobnie jak w przypadku **znaleźć** metody, z wyjątkiem, że zwraca **DataRowView** tablica, która odwołuje się do wszystkich zgodnych wierszy w **DataView**.</span><span class="sxs-lookup"><span data-stu-id="2a86b-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="2a86b-111">W przypadku nieodnalezienia żadnych dopasowań **DataRowView** tablica jest pusta.</span><span class="sxs-lookup"><span data-stu-id="2a86b-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="2a86b-112">Do użycia **znaleźć** lub **FindRows** metody, należy określić sortowania order, albo ustawiając **ApplyDefaultSort** do **true** lub za pomocą **Sortowania** właściwości.</span><span class="sxs-lookup"><span data-stu-id="2a86b-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="2a86b-113">Jeśli nie kolejność sortowania jest określony, zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2a86b-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="2a86b-114">**Znaleźć** i **FindRows** metody przyjmują tablicę wartości jako dane wejściowe, którego długość jest zgodna z liczbą kolumn w porządku sortowania.</span><span class="sxs-lookup"><span data-stu-id="2a86b-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="2a86b-115">W przypadku sortowania w jednej kolumnie można przekazać wartość typu single.</span><span class="sxs-lookup"><span data-stu-id="2a86b-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="2a86b-116">Do sortowania, zawierających wiele kolumn należy przekazać tablicę obiektów.</span><span class="sxs-lookup"><span data-stu-id="2a86b-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="2a86b-117">Należy pamiętać, że sortowania na wiele kolumn, wartości w tablicy obiektu musi odpowiadać kolejność kolumn określonych w **sortowania** właściwość **DataView**.</span><span class="sxs-lookup"><span data-stu-id="2a86b-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="2a86b-118">Poniższy kod przedstawia przykład **znaleźć** metoda jest wywoływana względem **DataView** z porządkiem sortowania jedną kolumnę.</span><span class="sxs-lookup"><span data-stu-id="2a86b-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 <span data-ttu-id="2a86b-119">Jeśli Twoje **sortowania** właściwość określa wiele kolumn, należy przekazać tablicę obiektów przy użyciu wartości wyszukiwania dla każdej kolumny w kolejności określonej przez **sortowania** właściwości, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2a86b-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a86b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a86b-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="2a86b-121">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="2a86b-121">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [<span data-ttu-id="2a86b-122">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2a86b-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
