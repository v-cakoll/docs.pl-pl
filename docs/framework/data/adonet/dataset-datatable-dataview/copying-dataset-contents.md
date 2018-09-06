---
title: Kopiowanie zawartości elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: b85fb6ebf56b110330be121c87d2492b0cfac536
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43804072"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="48c56-102">Kopiowanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="48c56-102">Copying DataSet Contents</span></span>
<span data-ttu-id="48c56-103">Można utworzyć kopię <xref:System.Data.DataSet> tak, aby pracować z danymi bez wywierania wpływu na oryginalnych danych lub pracy przy użyciu podzestawu danych z **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="48c56-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="48c56-104">Podczas kopiowania **DataSet**, możesz:</span><span class="sxs-lookup"><span data-stu-id="48c56-104">When copying a **DataSet**, you can:</span></span>  
  
-   <span data-ttu-id="48c56-105">Utworzyć dokładną kopię **zestawu danych**, w tym schematu, danych, informacje o stanie wiersza i wersje wiersza.</span><span class="sxs-lookup"><span data-stu-id="48c56-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
-   <span data-ttu-id="48c56-106">Tworzenie **DataSet** zawiera schemat z istniejącej **zestawu danych**, ale tylko wiersze, które zostały zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="48c56-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="48c56-107">Zwracanie wszystkich wierszy, które zostały zmodyfikowane lub określić konkretną **właściwością DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="48c56-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="48c56-108">Aby uzyskać więcej informacji na temat stany wiersza zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="48c56-108">For more information about row states, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
-   <span data-ttu-id="48c56-109">Kopia schematu lub relacyjnej struktury **DataSet** tylko, bez kopiowania żadnych wierszy.</span><span class="sxs-lookup"><span data-stu-id="48c56-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="48c56-110">Wiersze mogą być importowane do istniejącego <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="48c56-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="48c56-111">Aby utworzyć dokładną kopię **zestawu danych** zawierającą zarówno schematu, jak i dane, użyj <xref:System.Data.DataSet.Copy%2A> metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="48c56-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="48c56-112">Poniższy przykład kodu pokazuje, jak utworzyć dokładną kopię **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="48c56-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="48c56-113">Aby utworzyć kopię **zestawu danych** zawierającego schemat i tylko dane reprezentujące **dodano**, **zmodyfikowane**, lub **usunięte** wierszy, użyj <xref:System.Data.DataSet.GetChanges%2A> metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="48c56-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="48c56-114">Można również użyć **GetChanges —** zwracać tylko wiersze ze stanem określony wiersz, przekazując **właściwością DataRowState** wartości podczas wywoływania **GetChanges —**.</span><span class="sxs-lookup"><span data-stu-id="48c56-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="48c56-115">Poniższy przykład kodu pokazuje sposób przekazywania **właściwością DataRowState** podczas wywoływania **GetChanges —**.</span><span class="sxs-lookup"><span data-stu-id="48c56-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="48c56-116">Aby utworzyć kopię **DataSet** zawiera tylko schemat, należy użyć <xref:System.Data.DataSet.Clone%2A> metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="48c56-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="48c56-117">Można również dodać istniejące wiersze do sklonowanego **DataSet** przy użyciu **ImportRow** metody **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="48c56-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="48c56-118">**ImportRow** dodaje dane, stan wiersza i informacje o wersji wierszy do określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="48c56-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="48c56-119">Wartości w kolumnie są dodawane, tylko jeśli odpowiada nazwa kolumny i dane typ jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="48c56-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="48c56-120">Poniższy przykład kodu tworzy klon **zestawu danych** , a następnie dodaje wiersze z oryginalnego **DataSet** do **klientów** tabelę **zestawu danych**  klonowania dla klientów, którym **tekst** kolumna ma wartość "Germany".</span><span class="sxs-lookup"><span data-stu-id="48c56-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48c56-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48c56-121">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="48c56-122">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="48c56-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="48c56-123">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="48c56-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
