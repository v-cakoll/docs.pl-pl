---
title: Dodawanie istniejących ograniczeń do zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 05f95a9c4f250100ca97e3ab52e4073d027df1b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932198"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="ff988-102">Dodawanie istniejących ograniczeń do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ff988-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="ff988-103">Metoda **Fill** elementu **DataAdapter** wypełnia <xref:System.Data.DataSet> tylko za pomocą kolumn tabeli i wierszy ze źródła danych; Chociaż ograniczenia są zwykle ustawiane przez źródło danych, Metoda **Fill** nie dodaje do niego **informacji o schemacie. Domyślnie zestaw danych** .</span><span class="sxs-lookup"><span data-stu-id="ff988-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="ff988-104">Aby wypełnić **zestaw danych** istniejącymi informacjami o ograniczeniach klucza podstawowego ze źródła danych, można wywołać metodę **FillSchema** obiektu **DataAdapter**lub ustawić właściwość **MissingSchemaAction** elementu **DataAdapter** do **AddWithKey** przed wywołaniem **Fill**.</span><span class="sxs-lookup"><span data-stu-id="ff988-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="ff988-105">Zapewni to, że ograniczenia PRIMARY KEY w **zestawie danych** odzwierciedlają te w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="ff988-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="ff988-106">Informacje o ograniczeniu klucza obcego nie są uwzględniane i muszą zostać utworzone jawnie, jak pokazano w [ograniczeniach DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="ff988-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="ff988-107">Dodawanie informacji o schemacie do **zestawu danych** przed wypełnieniem go danymi gwarantuje, że ograniczenia PRIMARY KEY <xref:System.Data.DataTable> są dołączone do obiektów w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="ff988-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="ff988-108">W związku z tym po wprowadzeniu dodatkowych wywołań w celu wypełnienia **zestawu danych** informacje o kolumnie klucza podstawowego są używane do dopasowania nowych wierszy ze źródła danych z bieżącymi wierszami w każdej **DataTable**, a bieżące dane w tabelach są zastępowane danymi z Źródło danych.</span><span class="sxs-lookup"><span data-stu-id="ff988-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="ff988-109">Bez informacji o schemacie nowe wiersze ze źródła danych są dołączane do **zestawu danych**, co powoduje duplikowanie wierszy.</span><span class="sxs-lookup"><span data-stu-id="ff988-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff988-110">Jeśli kolumna w źródle danych jest identyfikowana jako funkcja autozwiększania, Metoda **FillSchema** lub metoda **Fill** z MissingSchemaActionem **AddWithKey**, tworzy **kolumnę DataColumn** z właściwością **AutoIncrement** Ustaw wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="ff988-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="ff988-111">Należy jednak ręcznie ustawić wartości **AutoIncrementStep** i **AutoIncrementSeed** .</span><span class="sxs-lookup"><span data-stu-id="ff988-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="ff988-112">Aby uzyskać więcej informacji na temat autouzupełniania kolumn, zobacz [Tworzenie kolumn typu AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="ff988-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="ff988-113">Użycie **FillSchema** lub ustawienie **MissingSchemaAction** na **AddWithKey** wymaga dodatkowego przetwarzania w źródle danych, aby określić informacje o kolumnie klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ff988-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="ff988-114">To dodatkowe przetwarzanie może utrudnić wydajność.</span><span class="sxs-lookup"><span data-stu-id="ff988-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="ff988-115">Jeśli znasz informacje o kluczu podstawowym w czasie projektowania, zalecamy jawne określenie kolumny klucza podstawowego lub kolumn w celu uzyskania optymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="ff988-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="ff988-116">Aby uzyskać informacje na temat jawnego ustawiania informacji o kluczu podstawowym dla tabeli, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="ff988-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="ff988-117">Poniższy przykład kodu pokazuje, jak dodać informacje o schemacie do **zestawu danych** przy użyciu **FillSchema**.</span><span class="sxs-lookup"><span data-stu-id="ff988-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
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
  
 <span data-ttu-id="ff988-118">Poniższy przykład kodu pokazuje, jak dodać informacje o schemacie do **zestawu danych** przy użyciu właściwości **MissingSchemaAction. AddWithKey** metody **Fill** .</span><span class="sxs-lookup"><span data-stu-id="ff988-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
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
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="ff988-119">Obsługa wielu zestawów wyników</span><span class="sxs-lookup"><span data-stu-id="ff988-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="ff988-120">Jeśli obiekt **DataAdapter** napotka wiele zestawów wyników zwróconych z elementu **SelectCommand**, utworzy wiele tabel w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="ff988-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="ff988-121">W tabelach zostanie nadana przyrostowa, zerowa nazwa domyślna **tabeli** *N*, rozpoczynając od **tabeli** zamiast "TABLE0".</span><span class="sxs-lookup"><span data-stu-id="ff988-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="ff988-122">Jeśli nazwa tabeli jest przenoszona jako argument do metody **FillSchema** , w tabelach zostanie nadana przyrostowa, różna od zera nazwa tabeliname *N*, rozpoczynająca się od nazwy TableName zamiast "TableName0".</span><span class="sxs-lookup"><span data-stu-id="ff988-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff988-123">Jeśli metoda **FillSchema** obiektu **elementu OleDbDataAdapter** jest wywoływana dla polecenia, które zwraca wiele zestawów wyników, zwracane są tylko informacje o schemacie z pierwszego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="ff988-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="ff988-124">Podczas zwracania informacji o schemacie dla wielu zestawów wyników przy użyciu **elementu OleDbDataAdapter**zaleca się określenie **MissingSchemaAction** **AddWithKey** i uzyskanie informacji o schemacie podczas wywoływania **wypełnienia** . Method.</span><span class="sxs-lookup"><span data-stu-id="ff988-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff988-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff988-125">See also</span></span>

- [<span data-ttu-id="ff988-126">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="ff988-126">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="ff988-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="ff988-127">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="ff988-128">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ff988-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="ff988-129">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ff988-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
