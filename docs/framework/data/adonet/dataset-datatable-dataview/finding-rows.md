---
title: Znajdowanie wierszy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 57ed6045ca0ea9f9579640839e8198716cf79fe0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760885"
---
# <a name="finding-rows"></a><span data-ttu-id="ad4ec-102">Znajdowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="ad4ec-102">Finding Rows</span></span>
<span data-ttu-id="ad4ec-103">Możesz wyszukać wierszy, zgodnie z ich wartości klucza sortowania za pomocą <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="ad4ec-104">Uwzględniana wielkość liter wyszukiwania wartości w **znaleźć** i **FindRows** metod jest określany przez **CaseSensitive** właściwości podstawowych <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="ad4ec-105">Wartości wyszukiwania musi być zgodna istniejące wartości klucza sortowania w całości w celu zwrócony wynik.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="ad4ec-106">**Znaleźć** metoda zwraca liczbę całkowitą z indeksem <xref:System.Data.DataRowView> odpowiadającego kryteriom wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="ad4ec-107">Jeśli więcej niż jeden wiersz spełnia kryteria wyszukiwania, indeks pierwszego dopasowania **DataRowView** jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="ad4ec-108">W przypadku nieodnalezienia żadnych dopasowań **znaleźć** zwraca wartość -1.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="ad4ec-109">Aby zwrócić wyników wyszukiwania, które odpowiada wiele wierszy, należy użyć **FindRows** metody.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="ad4ec-110">**FindRows** działa podobnie do **znaleźć** metody, z wyjątkiem, że zwraca **DataRowView** tablica, która odwołuje się do wszystkich zgodnych wierszy w **DataView**.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="ad4ec-111">W przypadku nieodnalezienia żadnych dopasowań **DataRowView** tablica jest pusta.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="ad4ec-112">Umożliwia **znaleźć** lub **FindRows** metody sortowania należy określić kolejność, albo ustawiając **ApplyDefaultSort** do **true** lub za pomocą **Sortowania** właściwości.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="ad4ec-113">Jeśli określono żadnego porządku sortowania, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="ad4ec-114">**Znaleźć** i **FindRows** metody przyjmują tablicy wartości jako dane wejściowe, którego długość jest zgodna z liczbą kolumn w kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="ad4ec-115">W przypadku sortowania w jednej kolumnie można przekazać pojedynczą wartość.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="ad4ec-116">Do sortowania zawierających wiele kolumn należy przekazać tablicę obiektów.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="ad4ec-117">Należy pamiętać, sortować na wiele kolumn, wartości w tablicy object musi odpowiadać kolejność kolumn określonych w **sortowania** właściwość **DataView**.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="ad4ec-118">Poniższy kod przedstawia przykład **znaleźć** metoda jest wywoływana względem **DataView** z kolejnością sortowania jednej kolumny.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="ad4ec-119">Jeśli Twoje **sortowania** właściwość określa wiele kolumn, należy przekazać tablicy obiektów o wartości wyszukiwania dla każdej kolumny w kolejności określonej przez **sortowania** właściwości, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="ad4ec-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad4ec-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad4ec-120">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="ad4ec-121">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="ad4ec-121">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="ad4ec-122">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="ad4ec-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
