---
title: Znajdowanie wierszy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 2ff2b6b6d00c854d07f36d37986268a388c7f31b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203718"
---
# <a name="finding-rows"></a><span data-ttu-id="059b2-102">Znajdowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="059b2-102">Finding Rows</span></span>
<span data-ttu-id="059b2-103">Wiersze można wyszukiwać według ich wartości klucza sortowania przy użyciu <xref:System.Data.DataView.Find%2A> metod <xref:System.Data.DataView>i <xref:System.Data.DataView.FindRows%2A> .</span><span class="sxs-lookup"><span data-stu-id="059b2-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="059b2-104">Wielkość liter w wartościach wyszukiwania w metodach **Find** i **FindRows** jest określana przez właściwość **CaseSensitive** elementu bazowego <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="059b2-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="059b2-105">Wartości wyszukiwania muszą być zgodne z istniejącymi wartościami klucza sortowania w całości w celu zwrócenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="059b2-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="059b2-106">Metoda **Find** zwraca liczbę całkowitą z indeksem <xref:System.Data.DataRowView> odpowiadającym kryteriom wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="059b2-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="059b2-107">Jeśli więcej niż jeden wiersz pasuje do kryteriów wyszukiwania, zwracany jest tylko indeks pierwszego pasującej **DataRowView** .</span><span class="sxs-lookup"><span data-stu-id="059b2-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="059b2-108">Jeśli nie znaleziono żadnych dopasowań, **Znajdź** zwraca wartość-1.</span><span class="sxs-lookup"><span data-stu-id="059b2-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="059b2-109">Aby zwrócić wyniki wyszukiwania pasujące do wielu wierszy, użyj metody **FindRows** .</span><span class="sxs-lookup"><span data-stu-id="059b2-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="059b2-110">**FindRows** działa podobnie jak Metoda **Find** , z tą różnicą, że zwraca tablicę **DataRowView** , która odwołuje się do wszystkich pasujących wierszy w **widoku**danych.</span><span class="sxs-lookup"><span data-stu-id="059b2-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="059b2-111">Jeśli nie zostaną znalezione żadne dopasowania, tablica **DataRowView** będzie pusta.</span><span class="sxs-lookup"><span data-stu-id="059b2-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="059b2-112">Aby użyć metody **Find** lub **FindRows** , należy określić kolejność sortowania przez ustawienie **ApplyDefaultSort** na **true** lub przy użyciu właściwości **sort** .</span><span class="sxs-lookup"><span data-stu-id="059b2-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="059b2-113">Jeśli kolejność sortowania nie zostanie określona, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="059b2-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="059b2-114">Metody **Find** i **FindRows** pobierają tablicę wartości jako dane wejściowe, których długość jest zgodna z liczbą kolumn w kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="059b2-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="059b2-115">W przypadku sortowania pojedynczej kolumny można przekazać pojedynczą wartość.</span><span class="sxs-lookup"><span data-stu-id="059b2-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="059b2-116">W przypadku zamówień sortowania zawierających wiele kolumn należy przekazać tablicę obiektów.</span><span class="sxs-lookup"><span data-stu-id="059b2-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="059b2-117">Należy pamiętać, że w przypadku sortowania dla wielu kolumn wartości w tablicy obiektów muszą być zgodne z kolejnością kolumn określonych we właściwości **sort** elementu **DataView**.</span><span class="sxs-lookup"><span data-stu-id="059b2-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="059b2-118">Poniższy przykład kodu pokazuje metodę **Find** wywoływaną względem elementu **DataView** z kolejnością sortowania pojedynczej kolumny.</span><span class="sxs-lookup"><span data-stu-id="059b2-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="059b2-119">Jeśli właściwość **sortowania** określa wiele kolumn, należy przekazać tablicę obiektów z wartościami wyszukiwania dla każdej kolumny w kolejności określonej przez właściwość **sort** , jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="059b2-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="059b2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="059b2-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="059b2-121">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="059b2-121">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="059b2-122">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="059b2-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
