---
title: Znajdowanie wierszy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151146"
---
# <a name="finding-rows"></a><span data-ttu-id="6f249-102">Znajdowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="6f249-102">Finding Rows</span></span>
<span data-ttu-id="6f249-103">Wiersze można wyszukiwać zgodnie z ich wartościami <xref:System.Data.DataView.FindRows%2A> klucza <xref:System.Data.DataView>sortowania przy użyciu <xref:System.Data.DataView.Find%2A> metod i metody programu .</span><span class="sxs-lookup"><span data-stu-id="6f249-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="6f249-104">Wielkość liter wartości wyszukiwania w find **and** **FindRows** metody jest określana przez **CaseSensitive** właściwość podstawowej <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="6f249-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="6f249-105">Wartości wyszukiwania muszą być zgodne z istniejącymi wartościami klucza sortowania w całości, aby uzyskać wynik.</span><span class="sxs-lookup"><span data-stu-id="6f249-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="6f249-106">**Find** Metoda zwraca liczbę całkowitą z indeksem, <xref:System.Data.DataRowView> który odpowiada kryteriom wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="6f249-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="6f249-107">Jeśli więcej niż jeden wiersz spełnia kryteria wyszukiwania, zwracany jest tylko indeks pierwszego pasującego **datarowview.**</span><span class="sxs-lookup"><span data-stu-id="6f249-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="6f249-108">Jeśli nie zostaną znalezione żadne dopasowania, **funkcja Znajdź** zwraca wartość -1.</span><span class="sxs-lookup"><span data-stu-id="6f249-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="6f249-109">Aby zwrócić wyniki wyszukiwania, które pasują do wielu wierszy, użyj **Metody FindRows.**</span><span class="sxs-lookup"><span data-stu-id="6f249-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="6f249-110">**Funkcja FindRows** działa podobnie jak metoda **Find,** z tą różnicą, że zwraca tablicę **DataRowView,** która odwołuje się do wszystkich pasujących wierszy w **pliku DataView**.</span><span class="sxs-lookup"><span data-stu-id="6f249-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="6f249-111">Jeśli nie zostaną znalezione żadne dopasowania, **datarowview** tablica będzie pusta.</span><span class="sxs-lookup"><span data-stu-id="6f249-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="6f249-112">Aby użyć **find** lub **FindRows** metody należy określić kolejność sortowania albo przez ustawienie **ApplyDefaultSort** **true** lub za pomocą **Sort właściwości.**</span><span class="sxs-lookup"><span data-stu-id="6f249-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="6f249-113">Jeśli nie określono kolejności sortowania, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6f249-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="6f249-114">**Find** i **FindRows** metody wziąć tablicę wartości jako dane wejściowe, których długość odpowiada liczbie kolumn w kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="6f249-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="6f249-115">W przypadku sortowania w jednej kolumnie można przekazać pojedynczą wartość.</span><span class="sxs-lookup"><span data-stu-id="6f249-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="6f249-116">W przypadku zamówień sortowania zawierających wiele kolumn należy przekazać tablicę obiektów.</span><span class="sxs-lookup"><span data-stu-id="6f249-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="6f249-117">Należy zauważyć, że w przypadku sortowania w wielu kolumnach wartości w tablicy obiektów muszą być zgodne z kolejnością kolumn określonych we właściwości **Sortowanie** **widoku DataView**.</span><span class="sxs-lookup"><span data-stu-id="6f249-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="6f249-118">Poniższy przykład kodu pokazuje **Find** metoda wywoływana dla **DataView** z kolejnością sortowania pojedynczej kolumny.</span><span class="sxs-lookup"><span data-stu-id="6f249-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="6f249-119">Jeśli właściwość **Sort** określa wiele kolumn, należy przekazać tablicę obiektów z wartościami wyszukiwania dla każdej kolumny w kolejności określonej przez **sortowanie** właściwości, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="6f249-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f249-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f249-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="6f249-121">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="6f249-121">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="6f249-122">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6f249-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
