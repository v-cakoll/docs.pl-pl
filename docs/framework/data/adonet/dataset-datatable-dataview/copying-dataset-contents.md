---
title: Kopiowanie zawartości elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: d8a7762c4ec5d650295ca0626180285723549051
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786515"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="3b8c0-102">Kopiowanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="3b8c0-102">Copying DataSet Contents</span></span>
<span data-ttu-id="3b8c0-103">Można utworzyć kopię <xref:System.Data.DataSet> programu, aby można było korzystać z danych bez wpływania na oryginalne dane, lub pracy z podzbiorem danych z **elementu DataSet**.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="3b8c0-104">Podczas kopiowania **zestawu danych**można:</span><span class="sxs-lookup"><span data-stu-id="3b8c0-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="3b8c0-105">Utwórz dokładną kopię **zestawu danych**, włącznie z schematem, danymi, informacjami o stanie wiersza i wersjami wierszy.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="3b8c0-106">Utwórz **zestaw danych** , który zawiera schemat istniejącego **zestawu danych**, ale tylko wiersze, które zostały zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="3b8c0-107">Można zwrócić wszystkie wiersze, które zostały zmodyfikowane, lub określić określony **DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="3b8c0-108">Aby uzyskać więcej informacji na temat stanów wiersza, zobacz [Stany wiersza i wersje wierszy](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="3b8c0-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="3b8c0-109">Skopiuj schemat lub strukturę relacyjną tylko **zestawu danych** , bez kopiowania żadnych wierszy.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="3b8c0-110">Wiersze można importować do istniejącej <xref:System.Data.DataTable> funkcji using. <xref:System.Data.DataTable.ImportRow%2A></span><span class="sxs-lookup"><span data-stu-id="3b8c0-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="3b8c0-111">Aby utworzyć dokładną kopię **zestawu danych** , który zawiera schemat i dane, użyj <xref:System.Data.DataSet.Copy%2A> metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="3b8c0-112">Poniższy przykład kodu pokazuje, jak utworzyć dokładną kopię **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="3b8c0-113">Aby utworzyć kopię **zestawu danych** , który zawiera schemat i tylko dane reprezentujące **dodane**, **zmodyfikowane**lub **usunięte** wiersze, użyj <xref:System.Data.DataSet.GetChanges%2A> metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="3b8c0-114">Można również użyć metody **Getchangs** , aby zwrócić tylko wiersze z określonym stanem wiersza przez przekazanie wartości **DataRowState** podczas wywoływania metody **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="3b8c0-115">Poniższy przykład kodu pokazuje, jak przekazać **DataRowState** podczas wywoływania metody **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="3b8c0-116">Aby utworzyć kopię **zestawu danych** , który zawiera tylko schemat, użyj <xref:System.Data.DataSet.Clone%2A> metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="3b8c0-117">Istnieje również możliwość dodania istniejących wierszy do sklonowanego **zestawu danych** przy użyciu metody **ImportRow** **tabeli DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="3b8c0-118">**ImportRow** dodaje informacje o stanie wiersza i wersji wiersza do określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="3b8c0-119">Wartości kolumn są dodawane tylko wtedy, gdy nazwa kolumny jest zgodna i typ danych jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="3b8c0-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="3b8c0-120">Poniższy przykład kodu tworzy klon **zestawu danych** , a następnie dodaje wiersze z oryginalnego **zestawu** danych do tabeli **Customers** w sklonowanym **zestawie danych** dla klientów, których kolumna **CountryRegion** ma wartość "Niemcy" ".</span><span class="sxs-lookup"><span data-stu-id="3b8c0-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b8c0-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b8c0-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="3b8c0-122">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="3b8c0-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="3b8c0-123">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3b8c0-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
