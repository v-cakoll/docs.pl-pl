---
title: Element DataAdapter DataTable i mapowania elementu DataColumn
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: eb6841dd24c4c7587cc2424cc1e606194da34585
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944064"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="b04cc-102">Element DataAdapter DataTable i mapowania elementu DataColumn</span><span class="sxs-lookup"><span data-stu-id="b04cc-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="b04cc-103">Element **DataAdapter** zawiera kolekcję zero lub więcej <xref:System.Data.Common.DataTableMapping> obiektów we właściwości **TableMappings** .</span><span class="sxs-lookup"><span data-stu-id="b04cc-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="b04cc-104">**DataTableMapping** zapewnia mapowanie wzorca między danymi zwracanymi z zapytania do źródła danych i <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="b04cc-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="b04cc-105">Nazwę **DataTableMapping** można przesłać zamiast nazwy **DataTable** do metody **Fill** elementu **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="b04cc-106">Poniższy przykład tworzy **DataTableMapping** o nazwie **AuthorsMapping** dla tabeli **autorów** .</span><span class="sxs-lookup"><span data-stu-id="b04cc-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="b04cc-107">**DataTableMapping** umożliwia używanie nazw kolumn w **elemencie DataTable** , które różnią się od tych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="b04cc-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="b04cc-108">Element **DataAdapter** używa mapowania, aby dopasować kolumny po zaktualizowaniu tabeli.</span><span class="sxs-lookup"><span data-stu-id="b04cc-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="b04cc-109">Jeśli nie określisz nazwy **TableName** lub **DataTableMapping** podczas wywoływania metody **Fill** lub **Update** elementu **DataAdapter**, obiekt **DataAdapter** szuka **DataTableMapping** o nazwie "Table".</span><span class="sxs-lookup"><span data-stu-id="b04cc-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="b04cc-110">Jeśli **DataTableMapping** nie istnieje, **tabelaname tabeli** **DataTable** ma wartość "Table".</span><span class="sxs-lookup"><span data-stu-id="b04cc-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="b04cc-111">Można określić domyślny **DataTableMapping** , tworząc **DataTableMapping** o nazwie "Table".</span><span class="sxs-lookup"><span data-stu-id="b04cc-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="b04cc-112">Poniższy przykład kodu tworzy **DataTableMapping** (z <xref:System.Data.Common> przestrzeni nazw) i tworzy mapowanie domyślne dla określonego elementu **DataAdapter** przez nadanie jej nazwy "Table".</span><span class="sxs-lookup"><span data-stu-id="b04cc-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="b04cc-113">Następnie przykład mapuje kolumny z pierwszej tabeli w wyniku zapytania (tabela **Customers** bazy danych **Northwind** ) do zestawu większej liczby przyjaznych nazw użytkowników w tabeli <xref:System.Data.DataSet> **Klienci Northwind** w.</span><span class="sxs-lookup"><span data-stu-id="b04cc-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b04cc-114">W przypadku kolumn, które nie są zamapowane, używana jest nazwa kolumny ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b04cc-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="b04cc-115">W bardziej zaawansowanych sytuacjach możesz zdecydować, że chcesz, aby ten sam element **DataAdapter** obsługiwał ładowanie różnych tabel z różnymi mapowaniami.</span><span class="sxs-lookup"><span data-stu-id="b04cc-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="b04cc-116">W tym celu wystarczy dodać dodatkowe obiekty **DataTableMapping** .</span><span class="sxs-lookup"><span data-stu-id="b04cc-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="b04cc-117">Gdy metoda **Fill** jest przenoszona do wystąpienia **zestawu danych** i nazwy **DataTableMapping** , jeśli istnieje mapowanie o tej nazwie, jest ono używane; w przeciwnym razie zostanie użyta **tabela DataTable** o tej nazwie.</span><span class="sxs-lookup"><span data-stu-id="b04cc-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="b04cc-118">Poniższe przykłady umożliwiają utworzenie **DataTableMapping** z nazwą **klientów** i nazwą **elementu DataTable** **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="b04cc-119">Następnie przykład mapuje wiersze zwracane przez instrukcję SELECT do **elementu DataTable** **BizTalkSchema** .</span><span class="sxs-lookup"><span data-stu-id="b04cc-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="b04cc-120">Jeśli nie podano nazwy kolumny źródłowej dla mapowania kolumn lub nie podano nazwy tabeli źródłowej dla mapowania tabeli, automatycznie generowane są domyślne nazwy.</span><span class="sxs-lookup"><span data-stu-id="b04cc-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="b04cc-121">Jeśli nie podano kolumny źródłowej dla mapowania kolumn, mapowanie kolumny otrzymuje przyrostową domyślną nazwę **SourceColumn** *N,* rozpoczynając od **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="b04cc-122">Jeśli nie podano nazwy tabeli źródłowej dla mapowania tabeli, mapowanie tabeli uzyskuje przyrostową domyślną nazwę elementu **SourceName** *N*, rozpoczynając od **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b04cc-123">Zalecamy uniknięcie konwencji nazewnictwa elementu **SourceColumn** *N* dla mapowania kolumn lub elementu **sources** *n* dla mapowania tabeli, ponieważ dostarczona nazwa może powodować konflikt z istniejącą domyślną nazwą mapowania kolumn wNazwa ColumnMappingCollection lub mapowanie tabeli w **DataTableMappingCollection**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="b04cc-124">Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b04cc-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="b04cc-125">Obsługa wielu zestawów wyników</span><span class="sxs-lookup"><span data-stu-id="b04cc-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="b04cc-126">Jeśli **Właściwość SelectCommand** zwraca wiele tabel, **Wypełnij** automatycznie generuje nazwy tabel z przyrostowymi wartościami dla tabel w **zestawie danych**, rozpoczynając od określonej nazwy tabeli i kontynuując w formularzu TableName *N*, zaczynając od **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="b04cc-127">Mapowania tabeli można użyć, aby zamapować automatycznie wygenerowaną nazwę tabeli na nazwę, która ma być określona dla tabeli w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="b04cc-128">Na przykład dla elementu **SelectCommand** , który zwraca dwie tabele, **klienci** i **zamówienia**, wydaj następujące wywołanie do **wypełnienia**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="b04cc-129">W **zestawie danych**są tworzone dwie tabele: **Klienci** i **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="b04cc-130">Mapowania tabel można użyć, aby upewnić się, że druga tabela ma nazwę Orders zamiast **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="b04cc-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="b04cc-131">W tym celu należy zmapować tabelę źródłową **Customers1** do **kolejności**tabel **zestawu danych** , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b04cc-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="b04cc-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b04cc-132">See also</span></span>

- [<span data-ttu-id="b04cc-133">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="b04cc-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="b04cc-134">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b04cc-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="b04cc-135">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="b04cc-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
