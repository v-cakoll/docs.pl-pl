---
title: Dodawanie istniejących ograniczeń do zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: c3c28392a9e4bee0e2f9e0dcf553e13b67c378dd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="d42ba-102">Dodawanie istniejących ograniczeń do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d42ba-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="d42ba-103">**Wypełnienia** metody **element DataAdapter** wypełnia <xref:System.Data.DataSet> tylko z tabeli kolumn i wierszy ze źródła danych; jednak ograniczenia są często ustawione przez źródło danych **wypełnienia** — metoda nie dodaje te informacje schematu **DataSet** domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d42ba-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="d42ba-104">Aby wypełnić **zestawu danych** z istniejących informacji ograniczenia klucza podstawowego źródła danych, możesz albo wywołanie **FillSchema** metody **element DataAdapter**, lub ustaw **MissingSchemaAction** właściwość **element DataAdapter** do **AddWithKey** przed wywołaniem **wypełnienia**.</span><span class="sxs-lookup"><span data-stu-id="d42ba-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="d42ba-105">Daje to pewność, że klucz podstawowy ograniczeń **DataSet** odzwierciedlają w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="d42ba-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="d42ba-106">Ograniczenie klucza obcego informacji nie jest dołączana i muszą być tworzone jawne, jak pokazano w [ograniczenia DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="d42ba-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="d42ba-107">Dodawanie informacji o schemacie **DataSet** przed wypełnianie danymi zapewnia, że ograniczenia klucza podstawowego są dołączone do <xref:System.Data.DataTable> obiekty w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="d42ba-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="d42ba-108">W rezultacie, gdy dodatkowe wywołania do wypełnienia **zestawu danych** zostają podstawową informacji o kolumnie klucza jest używany do dopasowywania nowych wierszy ze źródła danych z bieżącej wierszy w każdym **DataTable**i bieżące dane w tabele zostały zastąpione danych ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d42ba-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="d42ba-109">Bez informacji o schemacie, nowych wierszy ze źródła danych są dołączane do **DataSet**, co zduplikowane wiersze.</span><span class="sxs-lookup"><span data-stu-id="d42ba-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d42ba-110">Jeśli kolumny w źródle danych została zidentyfikowana jako automatyczne zwiększanie **FillSchema** metody, lub **wypełnienia** metody z **MissingSchemaAction** z  **AddWithKey**, tworzy **DataColumn** z **AutoIncrement** ustawioną właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="d42ba-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="d42ba-111">Jednak należy ustawić **elementu AutoIncrementStep** i **AutoIncrementSeed** wartości samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="d42ba-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="d42ba-112">Aby uzyskać więcej informacji o kolumnach zwiększanie automatycznego, zobacz [Tworzenie kolumny typu AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="d42ba-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="d42ba-113">Przy użyciu **FillSchema** lub ustawienie **MissingSchemaAction** do **AddWithKey** wymaga dodatkowego przetwarzania w źródle danych, aby ustalić informacji o kolumnie klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="d42ba-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="d42ba-114">To dodatkowe przetwarzanie może zmniejszyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="d42ba-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="d42ba-115">Jeśli znasz informacje o kluczu podstawowym w czasie projektowania, zaleca się, że zostaną jawnie określone kolumny klucza podstawowego lub kolumny w celu osiągnięcia optymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="d42ba-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="d42ba-116">Aby dowiedzieć się, jak jawne ustawienie informacje o kluczu podstawowym dla tabeli, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="d42ba-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="d42ba-117">W poniższym przykładzie przedstawiono sposób dodawania informacji o schemacie **DataSet** przy użyciu **FillSchema**.</span><span class="sxs-lookup"><span data-stu-id="d42ba-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 <span data-ttu-id="d42ba-118">W poniższym przykładzie przedstawiono sposób dodawania informacji o schemacie **DataSet** przy użyciu **MissingSchemaAction.AddWithKey** właściwość **wypełnienia** metody.</span><span class="sxs-lookup"><span data-stu-id="d42ba-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="d42ba-119">Obsługa wielu zestawów wyników</span><span class="sxs-lookup"><span data-stu-id="d42ba-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="d42ba-120">Jeśli **element DataAdapter** napotka zwrócony z wielu zestawów wyników **SelectCommand**, utworzy on wiele tabel w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="d42ba-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="d42ba-121">Tabele otrzymają liczony od zera przyrostowe domyślną nazwę **tabeli** *N*począwszy **tabeli** zamiast "Table0".</span><span class="sxs-lookup"><span data-stu-id="d42ba-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="d42ba-122">Jeśli nazwa tabeli jest przekazywany jako argument **FillSchema** metody tabele otrzymają liczony od zera nazwę przyrostowe **TableName** *N*począwszy **TableName** zamiast "TableName0".</span><span class="sxs-lookup"><span data-stu-id="d42ba-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d42ba-123">Jeśli **FillSchema** metody **elementu OleDbDataAdapter** obiektu po wywołaniu polecenia, która zwraca wiele zestawów wyników jest zwracany tylko informacji schematu z pierwszego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="d42ba-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="d42ba-124">Gdy zwracanie informacji o schemacie dla wielu wyników ustawia przy użyciu **elementu OleDbDataAdapter**, zaleca się, że podajesz **MissingSchemaAction** z **AddWithKey** i uzyskiwanie informacji o schemacie podczas wywoływania metody **wypełnienia** metody.</span><span class="sxs-lookup"><span data-stu-id="d42ba-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d42ba-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d42ba-125">See Also</span></span>  
 [<span data-ttu-id="d42ba-126">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="d42ba-126">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="d42ba-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="d42ba-127">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d42ba-128">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d42ba-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="d42ba-129">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="d42ba-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
