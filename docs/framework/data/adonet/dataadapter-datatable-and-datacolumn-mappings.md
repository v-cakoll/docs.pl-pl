---
title: Element DataAdapter DataTable i mapowania elementu DataColumn
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151562"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="bd3e0-102">Element DataAdapter DataTable i mapowania elementu DataColumn</span><span class="sxs-lookup"><span data-stu-id="bd3e0-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="bd3e0-103">A **DataAdapter** zawiera kolekcję <xref:System.Data.Common.DataTableMapping> zero lub więcej obiektów w jego **TableMappings** właściwości.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="bd3e0-104">**DataTableMapping** zapewnia mapowanie wzorcowe między danymi zwróconych z <xref:System.Data.DataTable>kwerendy względem źródła danych i .</span><span class="sxs-lookup"><span data-stu-id="bd3e0-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="bd3e0-105">**Nazwa DataTableMapping** może być przekazywana zamiast nazwy **DataTable** do **metody Wypełnianie** **dataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="bd3e0-106">Poniższy przykład tworzy **DataTableMapping** o nazwie **AuthorsMapping** dla **autorzy** tabeli.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="bd3e0-107">**DataTableMapping** umożliwia użycie nazw kolumn w **DataTable,** które różnią się od tych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="bd3e0-108">**DataAdapter** używa mapowania, aby dopasować kolumny, gdy tabela jest aktualizowana.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="bd3e0-109">Jeśli nazwa **TableName** lub **DataTableMapping** nie zostanie określona podczas wywoływania metody **Wypełniania** lub **aktualizacji** **programu DataAdapter,** **program DataAdapter** wyszukuje **mapowanie tabeli danych** o nazwie "Tabela".</span><span class="sxs-lookup"><span data-stu-id="bd3e0-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="bd3e0-110">Jeśli **datatableMapping** nie istnieje, **TableName** **datatable** jest "Tabela".</span><span class="sxs-lookup"><span data-stu-id="bd3e0-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="bd3e0-111">Można określić domyślny **DataTableMapping,** tworząc **DataTableMapping** o nazwie "Tabela".</span><span class="sxs-lookup"><span data-stu-id="bd3e0-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="bd3e0-112">Poniższy przykład kodu tworzy **DataTableMapping** (z obszaru <xref:System.Data.Common> nazw) i sprawia, że domyślne mapowanie dla określonego **DataAdapter** przez nadanie jej nazwy "Tabela".</span><span class="sxs-lookup"><span data-stu-id="bd3e0-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="bd3e0-113">W przykładzie następnie mapuje kolumny z pierwszej tabeli w wyniku kwerendy (tabela **Klienci** bazy danych **Northwind)** do <xref:System.Data.DataSet>zestawu bardziej przyjaznych dla użytkownika nazw w tabeli **Klienci Northwind** w tabeli .</span><span class="sxs-lookup"><span data-stu-id="bd3e0-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="bd3e0-114">W przypadku kolumn, które nie są mapowane, używana jest nazwa kolumny ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="bd3e0-115">W bardziej zaawansowanych sytuacjach można zdecydować, że chcesz, aby ten sam **DataAdapter** obsługiwać ładowanie różnych tabel z różnych mapowań.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="bd3e0-116">Aby to zrobić, wystarczy dodać dodatkowe **obiekty DataTableMapping.**</span><span class="sxs-lookup"><span data-stu-id="bd3e0-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="bd3e0-117">Gdy **Fill** metoda jest przekazywana wystąpienie **DataSet** i **DataTableMapping** nazwę, jeśli mapowanie o tej nazwie istnieje jest używany; w przeciwnym razie **datatable** o tej nazwie jest używany.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="bd3e0-118">Poniższe przykłady tworzą **DataTableMapping** z nazwą **klientów** i nazwą **DataTable** **programu BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="bd3e0-119">W przykładzie następnie mapuje wiersze zwrócone przez select instrukcji do **BizTalkSchema** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
> <span data-ttu-id="bd3e0-120">Jeśli nazwa kolumny źródłowej nie jest podana dla mapowania kolumn lub nazwa tabeli źródłowej nie jest podana dla mapowania tabeli, nazwy domyślne zostaną wygenerowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="bd3e0-121">Jeśli dla mapowania kolumn nie jest dostarczana żadna kolumna źródłowa, mapowanie kolumn otrzymuje przyrostową domyślną nazwę **SourceColumn** *N,* zaczynając od **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="bd3e0-122">Jeśli dla mapowania tabeli nie podano żadnej nazwy tabeli źródłowej, mapowanie tabeli otrzymuje przyrostową domyślną nazwę **Tabeli SourceTable** *N,* zaczynając od **tabeli SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd3e0-123">Zaleca się unikanie konwencji nazewnictwa **SourceColumn** *N* dla mapowania kolumn lub **SourceTable** *N* dla mapowania tabeli, ponieważ podana nazwa może kolidować z istniejącą domyślną nazwą mapowania kolumn w **nazwie mapowania kolumn lub** mapowania tabeli w **datatablemappingcollection**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="bd3e0-124">Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="bd3e0-125">Obsługa wielu zestawów wyników</span><span class="sxs-lookup"><span data-stu-id="bd3e0-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="bd3e0-126">Jeśli **selectcommand** zwraca wiele tabel, **Fill** automatycznie generuje nazwy tabel z wartościami przyrostowymi dla tabel w **Zestawie danych,** począwszy od określonej nazwy tabeli i kontynuując w **formularzu TableName** *N*, począwszy od **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="bd3e0-127">Za pomocą mapowań tabel można mapować automatycznie wygenerowaną nazwę tabeli na nazwę określoną dla tabeli w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="bd3e0-128">Na przykład dla **SelectCommand,** który zwraca dwie tabele, **Klienci** i **Zamówienia**, wystawić następujące wywołanie **Fill**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="bd3e0-129">W zestawie **danych**tworzone są dwie tabele: **Klienci** i **Klienci1**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="bd3e0-130">Można użyć mapowań tabel, aby upewnić się, że druga tabela ma nazwę **Zamówienia** zamiast **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="bd3e0-131">Aby to zrobić, mapuj tabelę źródłową **Customers1** do tabeli **DataSet** **Zamówienia**, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bd3e0-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="bd3e0-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd3e0-132">See also</span></span>

- [<span data-ttu-id="bd3e0-133">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="bd3e0-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="bd3e0-134">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bd3e0-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="bd3e0-135">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bd3e0-135">ADO.NET Overview</span></span>](ado-net-overview.md)
