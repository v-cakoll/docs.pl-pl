---
title: Kopiowanie zawartości elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151367"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="7e239-102">Kopiowanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="7e239-102">Copying DataSet Contents</span></span>
<span data-ttu-id="7e239-103">Można utworzyć kopię, <xref:System.Data.DataSet> aby można było pracować z danymi bez wpływu na oryginalne dane lub pracować z podzbiorem danych z **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="7e239-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="7e239-104">Podczas kopiowania **zestawu danych**można:</span><span class="sxs-lookup"><span data-stu-id="7e239-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="7e239-105">Utwórz dokładną kopię **zestawu danych,** w tym schemat, dane, informacje o stanie wiersza i wersje wierszy.</span><span class="sxs-lookup"><span data-stu-id="7e239-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="7e239-106">Utwórz **zestaw danych** zawierający schemat istniejącego zestawu **danych,** ale tylko wiersze, które zostały zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="7e239-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="7e239-107">Można zwrócić wszystkie wiersze, które zostały zmodyfikowane, lub określić określony **DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="7e239-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="7e239-108">Aby uzyskać więcej informacji o stanach wierszy, zobacz [Stany wierszy i Wersje wierszy](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="7e239-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="7e239-109">Skopiuj tylko schemat lub strukturę relacyjne **zestawu danych,** nie kopiując żadnych wierszy.</span><span class="sxs-lookup"><span data-stu-id="7e239-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="7e239-110">Wiersze można zaimportować <xref:System.Data.DataTable> <xref:System.Data.DataTable.ImportRow%2A>do istniejącego za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="7e239-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="7e239-111">Aby utworzyć dokładną kopię **zestawu danych** zawierającego zarówno schemat, jak i dane, użyj <xref:System.Data.DataSet.Copy%2A> metody zestawu **danych**.</span><span class="sxs-lookup"><span data-stu-id="7e239-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="7e239-112">W poniższym przykładzie kodu pokazano, jak utworzyć dokładną kopię **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="7e239-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="7e239-113">Aby utworzyć kopię **zestawu danych** zawierającego schemat i tylko dane reprezentujące wiersze **Dodane,** <xref:System.Data.DataSet.GetChanges%2A> **Zmodyfikowane**lub **Usunięte,** należy użyć metody zestawu **danych**.</span><span class="sxs-lookup"><span data-stu-id="7e239-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="7e239-114">Za pomocą **funkcji GetChanges** można również zwrócić tylko wiersze z określonym stanem wiersza, przekazując wartość **DataRowState** podczas wywoływania **getchanges**.</span><span class="sxs-lookup"><span data-stu-id="7e239-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="7e239-115">W poniższym przykładzie kodu pokazano, jak przekazać **DataRowState** podczas wywoływania **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="7e239-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="7e239-116">Aby utworzyć kopię **zestawu danych** zawierającego tylko schemat, należy użyć <xref:System.Data.DataSet.Clone%2A> metody zestawu **danych**.</span><span class="sxs-lookup"><span data-stu-id="7e239-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="7e239-117">Można również dodać istniejące wiersze do sklonowanego **zestawu danych** przy użyciu metody **ImportRow** **tabeli DataTable**.</span><span class="sxs-lookup"><span data-stu-id="7e239-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="7e239-118">**ImportRow** dodaje dane, stan wiersza i informacje o wersji wiersza do określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7e239-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="7e239-119">Wartości kolumn są dodawane tylko wtedy, gdy nazwa kolumny jest zgodna, a typ danych jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="7e239-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="7e239-120">Poniższy przykład kodu tworzy klon **zestawu danych,** a następnie dodaje wiersze z oryginalnego **zestawu danych** do tabeli **Klienci** w pliku **DataSet** klon dla klientów, gdzie kolumna **CountryRegion** ma wartość "Niemcy".</span><span class="sxs-lookup"><span data-stu-id="7e239-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e239-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e239-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="7e239-122">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="7e239-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7e239-123">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7e239-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
