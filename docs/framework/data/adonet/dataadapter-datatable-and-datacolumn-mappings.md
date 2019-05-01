---
title: Element DataAdapter DataTable i mapowania elementu DataColumn
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 54af7c2f449f8eb289841fb3eca357c6916404aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032698"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="d8972-102">Element DataAdapter DataTable i mapowania elementu DataColumn</span><span class="sxs-lookup"><span data-stu-id="d8972-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="d8972-103">A **DataAdapter** zawiera zbiór zero lub więcej <xref:System.Data.Common.DataTableMapping> obiekty w jego **TableMappings** właściwości.</span><span class="sxs-lookup"><span data-stu-id="d8972-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="d8972-104">A **DataTableMapping** zapewnia głównej mapowania między danymi zwrócone przez zapytanie w odniesieniu do źródła danych i <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="d8972-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d8972-105">**DataTableMapping** nazwa może być przekazywany zamiast **DataTable** nazwy do **wypełnienia** metody **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="d8972-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="d8972-106">Poniższy przykład tworzy **DataTableMapping** o nazwie **AuthorsMapping** dla **autorzy** tabeli.</span><span class="sxs-lookup"><span data-stu-id="d8972-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="d8972-107">A **DataTableMapping** pozwala na użycie nazwy kolumn w **DataTable** różnią od tych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="d8972-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="d8972-108">**DataAdapter** wykorzystuje mapowanie, aby dopasować kolumny, gdy zostanie zaktualizowany w tabeli.</span><span class="sxs-lookup"><span data-stu-id="d8972-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="d8972-109">Jeśli nie określisz **TableName** lub **DataTableMapping** nazwy podczas wywoływania **wypełnienia** lub **aktualizacji** metody  **Element DataAdapter**, **DataAdapter** szuka **DataTableMapping** o nazwie "Table".</span><span class="sxs-lookup"><span data-stu-id="d8972-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="d8972-110">Jeśli to **DataTableMapping** nie istnieje, **TableName** z **DataTable** jest "Table".</span><span class="sxs-lookup"><span data-stu-id="d8972-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="d8972-111">Można określić domyślną **DataTableMapping** , tworząc **DataTableMapping** o nazwie "Table".</span><span class="sxs-lookup"><span data-stu-id="d8972-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="d8972-112">Poniższy przykład kodu tworzy **DataTableMapping** (z <xref:System.Data.Common> przestrzeni nazw) i sprawia, że do domyślnego mapowania dla określonego **DataAdapter** , nadając mu nazwę "Table".</span><span class="sxs-lookup"><span data-stu-id="d8972-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="d8972-113">Przykład następnie mapuje kolumn z pierwszej tabeli, w wyniku kwerendy ( **klientów** tabeli **Northwind** bazy danych) do zestawu bardziej przyjazny dla użytkownika nazw **klientów Northwind**  tabelę <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d8972-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d8972-114">Dla kolumn, które nie są mapowane nazwa kolumny ze źródła danych jest używana.</span><span class="sxs-lookup"><span data-stu-id="d8972-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="d8972-115">W bardziej zaawansowanych sytuacjach może zadecydować, ma taki sam **DataAdapter** do obsługi ładowania różnych tabel za pomocą innego mapowania.</span><span class="sxs-lookup"><span data-stu-id="d8972-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="d8972-116">Aby to zrobić, po prostu dodaj dodatkowe **DataTableMapping** obiektów.</span><span class="sxs-lookup"><span data-stu-id="d8972-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="d8972-117">Gdy **wypełnienia** metoda przechodzi przez wystąpienie **zestawu danych** i **DataTableMapping** nazwę, jeśli mapowanie o tej nazwie istnieje, jest używany; w przeciwnym razie  **DataTable** za pomocą którego nazwa jest używana.</span><span class="sxs-lookup"><span data-stu-id="d8972-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="d8972-118">Poniższe przykłady tworzą **DataTableMapping** o nazwie **klientów** i **DataTable** nazwa **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="d8972-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="d8972-119">Przykład następnie mapuje wierszy zwracanych przez instrukcję SELECT do **BizTalkSchema** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="d8972-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
>  <span data-ttu-id="d8972-120">Jeśli nazwa kolumny źródłowej nie jest podany dla mapowania kolumny lub nie podano nazwy tabeli źródłowej dla mapowania tabeli, domyślne nazwy będą automatycznie generowane.</span><span class="sxs-lookup"><span data-stu-id="d8972-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="d8972-121">Jeśli nie dostarczono żadnej kolumny źródłowej dla mapowania kolumn, mapowania kolumn otrzymuje przyrostowe domyślną nazwę **SourceColumn** *N,* począwszy od **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="d8972-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="d8972-122">Jeśli nie dostarczono żadnych nazwy tabeli źródłowej dla mapowania tabeli, Mapowanie tabeli podano przyrostowe domyślną nazwę **SourceTable** *N*, począwszy od **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="d8972-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8972-123">Firma Microsoft zaleca, aby unikać konwencji nazewnictwa **SourceColumn** *N* dla mapowania kolumn, lub **SourceTable** *N* dla tabeli mapowania, ponieważ nazwa podasz może spowodować konflikt z istniejącą nazwą kolumny domyślne mapowanie w **ColumnMappingCollection** lub nazwę mapowania tabeli **DataTableMappingCollection** .</span><span class="sxs-lookup"><span data-stu-id="d8972-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="d8972-124">Podana nazwa już istnieje, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d8972-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="d8972-125">Obsługa wielu zestawów wyników</span><span class="sxs-lookup"><span data-stu-id="d8972-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="d8972-126">Jeśli Twoje **SelectCommand** zwraca wiele tabel **wypełnienia** automatycznie generuje nazw tabel z wartościami przyrostowych dla tabel w **zestawu danych**, począwszy od Określa nazwę tabeli i kontynuowanie na w formularzu **TableName** *N*, począwszy od **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="d8972-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="d8972-127">Mapowania tabel służy do mapowania nazwy tabeli automatycznie wygenerowaną nazwę określoną dla tabeli w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="d8972-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="d8972-128">Na przykład w przypadku **SelectCommand** zwracającego dwie tabele **klientów** i **zamówienia**, wydać następujące wywołanie do **wypełnienia**.</span><span class="sxs-lookup"><span data-stu-id="d8972-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="d8972-129">Dwie tabele zostały utworzone w **zestawu danych**: **Klienci** i **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="d8972-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="d8972-130">Mapowania tabel można użyć, aby upewnić się, że druga tabela ma nazwę **zamówienia** zamiast **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="d8972-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="d8972-131">Aby to zrobić, mapy źródłowej tabeli **Customers1** do **DataSet** tabeli **zamówienia**, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d8972-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8972-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8972-132">See also</span></span>

- [<span data-ttu-id="d8972-133">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="d8972-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="d8972-134">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d8972-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="d8972-135">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d8972-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
