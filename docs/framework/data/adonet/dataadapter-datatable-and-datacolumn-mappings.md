---
title: Element DataAdapter DataTable i mapowania elementu DataColumn
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e104ba75026c2ff387eb7c74b11c505e34085f41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="98fa4-102">Element DataAdapter DataTable i mapowania elementu DataColumn</span><span class="sxs-lookup"><span data-stu-id="98fa4-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="98fa4-103">A **element DataAdapter** zawiera kolekcję zero lub więcej <xref:System.Data.Common.DataTableMapping> obiekty w jego **TableMappings** właściwości.</span><span class="sxs-lookup"><span data-stu-id="98fa4-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="98fa4-104">A **DataTableMapping** zapewnia wzorca mapowania między dane zwrócone w wyniku zapytania względem źródła danych, a <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="98fa4-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="98fa4-105">**DataTableMapping** nazwy mogą być przekazywane zamiast **DataTable** nazwie do **wypełnienia** metody **element DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="98fa4-106">Poniższy przykład tworzy **DataTableMapping** o nazwie **AuthorsMapping** dla **autorów** tabeli.</span><span class="sxs-lookup"><span data-stu-id="98fa4-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="98fa4-107">A **DataTableMapping** pozwala na użycie nazwy kolumn w **DataTable** różnią od tych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="98fa4-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="98fa4-108">**Element DataAdapter** wykorzystuje mapowanie do dopasowania kolumn, gdy tabela jest aktualizowana.</span><span class="sxs-lookup"><span data-stu-id="98fa4-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="98fa4-109">Jeśli nie określisz **TableName** lub **DataTableMapping** nazwy podczas wywoływania metody **wypełnienia** lub **aktualizacji** metody  **Element DataAdapter**, **element DataAdapter** szuka **DataTableMapping** o nazwie "Tabela".</span><span class="sxs-lookup"><span data-stu-id="98fa4-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="98fa4-110">Jeśli **DataTableMapping** nie istnieje, **TableName** z **DataTable** jest "Tabela".</span><span class="sxs-lookup"><span data-stu-id="98fa4-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="98fa4-111">Można określić domyślną **DataTableMapping** tworząc **DataTableMapping** o nazwie "Tabela".</span><span class="sxs-lookup"><span data-stu-id="98fa4-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="98fa4-112">Poniższy przykład kodu tworzy **DataTableMapping** (z <xref:System.Data.Common> przestrzeni nazw) i umożliwia domyślne mapowanie dla określonego **element DataAdapter** za pomocą nazw, jego "Table".</span><span class="sxs-lookup"><span data-stu-id="98fa4-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="98fa4-113">Przykład następnie mapuje kolumn z pierwszej tabeli, w wyniku zapytania ( **klientów** spis **Northwind** bazy danych) z zestawem użytkownikom większy komfort nazw **klientów Northwind**  w tabeli <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="98fa4-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="98fa4-114">Dla kolumn, które nie zostały zamapowane jest używana nazwa kolumny ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="98fa4-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="98fa4-115">W sytuacjach bardziej zaawansowanych, może zadecydować, które mają taki sam **element DataAdapter** do obsługi różnych tabel z innego mapowania ładowania.</span><span class="sxs-lookup"><span data-stu-id="98fa4-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="98fa4-116">Aby to zrobić, po prostu dodaj dodatkowe **DataTableMapping** obiektów.</span><span class="sxs-lookup"><span data-stu-id="98fa4-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="98fa4-117">Gdy **wypełnienia** metody jest przekazywany wystąpienia **zestawu danych** i **DataTableMapping** nazwa, jeśli mapowanie o tej nazwie istnieje on jest używany; w przeciwnym razie  **Element DataTable** z którego nazwa jest używana.</span><span class="sxs-lookup"><span data-stu-id="98fa4-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="98fa4-118">Utwórz następujące przykłady **DataTableMapping** o nazwie **klientów** i **DataTable** nazwa **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="98fa4-119">Przykład następnie mapuje wierszy zwracanych przez instrukcję SELECT do **BizTalkSchema** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
>  <span data-ttu-id="98fa4-120">Jeśli nazwa kolumny źródłowej nie jest dostarczony dla mapowania kolumn lub nie podano nazwy tabeli źródłowej mapowania tabeli, będą automatycznie generowane domyślne nazwy.</span><span class="sxs-lookup"><span data-stu-id="98fa4-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="98fa4-121">Jeśli nie kolumny źródłowej nie jest dostarczony dla mapowania kolumn, mapowanie kolumn podano przyrostowe domyślną nazwę **SourceColumn** *N,* począwszy **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="98fa4-122">Jeśli nie nazwy tabeli źródłowej nie jest dostarczony dla mapowania tabeli, mapowania tabeli podano przyrostowe domyślną nazwę **elementu SourceTable** *N*począwszy **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98fa4-123">Firma Microsoft zaleca, aby uniknąć z konwencją nazewnictwa **SourceColumn** *N* dla mapowania kolumn, lub **elementu SourceTable** *N* dla tabeli mapowanie, ponieważ musisz podać nazwę może spowodować konflikt z istniejącą nazwą kolumny domyślne mapowanie w **ColumnMappingCollection** lub nazwę mapowania tabeli w **DataTableMappingCollection** .</span><span class="sxs-lookup"><span data-stu-id="98fa4-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="98fa4-124">Jeśli podanej nazwie już istnieje, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="98fa4-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="98fa4-125">Obsługa wielu zestawów wyników</span><span class="sxs-lookup"><span data-stu-id="98fa4-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="98fa4-126">Jeśli Twoje **SelectCommand** zwraca wiele tabel **wypełnienia** automatycznie generuje nazwy tabeli z wartościami przyrostowe w tabelach w **zestawu danych**począwszy Określona nazwa tabeli i kontynuowanie na w formularzu **TableName** *N*począwszy **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="98fa4-127">Mapowania tabeli można użyć do mapowania nazwy tabeli automatycznie generowanych na nazwę, która ma określony dla tabeli w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="98fa4-128">Na przykład w przypadku **SelectCommand** zwracającą dwóch tabel, **klientów** i **zamówień**, wydać następujące wywołanie do **wypełnienia**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="98fa4-129">Dwie tabele są tworzone w **DataSet**: **klientów** i **przekształcana w nazwę Klienci1**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="98fa4-130">Można użyć mapowania tabeli, aby upewnić się, że drugiej tabeli ma nazwę **zamówień** zamiast **przekształcana w nazwę Klienci1**.</span><span class="sxs-lookup"><span data-stu-id="98fa4-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="98fa4-131">Aby to zrobić, mapowania tabeli źródłowej **przekształcana w nazwę Klienci1** do **DataSet** tabeli **zamówień**, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="98fa4-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="98fa4-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98fa4-132">See Also</span></span>  
 [<span data-ttu-id="98fa4-133">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="98fa4-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="98fa4-134">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="98fa4-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="98fa4-135">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="98fa4-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
