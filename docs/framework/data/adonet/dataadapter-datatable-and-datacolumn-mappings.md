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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e96eb8e48b5787db5296458af650133747687295
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Element DataAdapter DataTable i mapowania elementu DataColumn
A **element DataAdapter** zawiera kolekcję zero lub więcej <xref:System.Data.Common.DataTableMapping> obiekty w jego **TableMappings** właściwości. A **DataTableMapping** zapewnia wzorca mapowania między dane zwrócone w wyniku zapytania względem źródła danych, a <xref:System.Data.DataTable>. **DataTableMapping** nazwy mogą być przekazywane zamiast **DataTable** nazwie do **wypełnienia** metody **element DataAdapter**. Poniższy przykład tworzy **DataTableMapping** o nazwie **AuthorsMapping** dla **autorów** tabeli.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping** pozwala na użycie nazwy kolumn w **DataTable** różnią od tych w bazie danych. **Element DataAdapter** wykorzystuje mapowanie do dopasowania kolumn, gdy tabela jest aktualizowana.  
  
 Jeśli nie określisz **TableName** lub **DataTableMapping** nazwy podczas wywoływania metody **wypełnienia** lub **aktualizacji** metody  **Element DataAdapter**, **element DataAdapter** szuka **DataTableMapping** o nazwie "Tabela". Jeśli **DataTableMapping** nie istnieje, **TableName** z **DataTable** jest "Tabela". Można określić domyślną **DataTableMapping** tworząc **DataTableMapping** o nazwie "Tabela".  
  
 Poniższy przykład kodu tworzy **DataTableMapping** (z <xref:System.Data.Common> przestrzeni nazw) i umożliwia domyślne mapowanie dla określonego **element DataAdapter** za pomocą nazw, jego "Table". Przykład następnie mapuje kolumn z pierwszej tabeli, w wyniku zapytania ( **klientów** spis **Northwind** bazy danych) z zestawem użytkownikom większy komfort nazw **klientów Northwind**  w tabeli <xref:System.Data.DataSet>. Dla kolumn, które nie zostały zamapowane jest używana nazwa kolumny ze źródła danych.  
  
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
  
 W sytuacjach bardziej zaawansowanych, może zadecydować, które mają taki sam **element DataAdapter** do obsługi różnych tabel z innego mapowania ładowania. Aby to zrobić, po prostu dodaj dodatkowe **DataTableMapping** obiektów.  
  
 Gdy **wypełnienia** metody jest przekazywany wystąpienia **zestawu danych** i **DataTableMapping** nazwa, jeśli mapowanie o tej nazwie istnieje on jest używany; w przeciwnym razie  **Element DataTable** z którego nazwa jest używana.  
  
 Utwórz następujące przykłady **DataTableMapping** o nazwie **klientów** i **DataTable** nazwa **BizTalkSchema**. Przykład następnie mapuje wierszy zwracanych przez instrukcję SELECT do **BizTalkSchema** **DataTable**.  
  
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
>  Jeśli nazwa kolumny źródłowej nie jest dostarczony dla mapowania kolumn lub nie podano nazwy tabeli źródłowej mapowania tabeli, będą automatycznie generowane domyślne nazwy. Jeśli nie kolumny źródłowej nie jest dostarczony dla mapowania kolumn, mapowanie kolumn podano przyrostowe domyślną nazwę **SourceColumn** *N,* począwszy **SourceColumn1**. Jeśli nie nazwy tabeli źródłowej nie jest dostarczony dla mapowania tabeli, mapowania tabeli podano przyrostowe domyślną nazwę **elementu SourceTable** *N*począwszy **SourceTable1**.  
  
> [!NOTE]
>  Firma Microsoft zaleca, aby uniknąć z konwencją nazewnictwa **SourceColumn** *N* dla mapowania kolumn, lub **elementu SourceTable** *N* dla tabeli mapowanie, ponieważ musisz podać nazwę może spowodować konflikt z istniejącą nazwą kolumny domyślne mapowanie w **ColumnMappingCollection** lub nazwę mapowania tabeli w **DataTableMappingCollection** . Jeśli podanej nazwie już istnieje, zostanie zgłoszony wyjątek.  
  
## <a name="handling-multiple-result-sets"></a>Obsługa wielu zestawów wyników  
 Jeśli Twoje **SelectCommand** zwraca wiele tabel **wypełnienia** automatycznie generuje nazwy tabeli z wartościami przyrostowe w tabelach w **zestawu danych**począwszy Określona nazwa tabeli i kontynuowanie na w formularzu **TableName** *N*począwszy **TableName1**. Mapowania tabeli można użyć do mapowania nazwy tabeli automatycznie generowanych na nazwę, która ma określony dla tabeli w **zestawu danych**. Na przykład w przypadku **SelectCommand** zwracającą dwóch tabel, **klientów** i **zamówień**, wydać następujące wywołanie do **wypełnienia**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 Dwie tabele są tworzone w **DataSet**: **klientów** i **przekształcana w nazwę Klienci1**. Można użyć mapowania tabeli, aby upewnić się, że drugiej tabeli ma nazwę **zamówień** zamiast **przekształcana w nazwę Klienci1**. Aby to zrobić, mapowania tabeli źródłowej **przekształcana w nazwę Klienci1** do **DataSet** tabeli **zamówień**, jak pokazano w poniższym przykładzie.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obiektów DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Trwa pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
