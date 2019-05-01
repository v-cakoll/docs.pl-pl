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
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Element DataAdapter DataTable i mapowania elementu DataColumn
A **DataAdapter** zawiera zbiór zero lub więcej <xref:System.Data.Common.DataTableMapping> obiekty w jego **TableMappings** właściwości. A **DataTableMapping** zapewnia głównej mapowania między danymi zwrócone przez zapytanie w odniesieniu do źródła danych i <xref:System.Data.DataTable>. **DataTableMapping** nazwa może być przekazywany zamiast **DataTable** nazwy do **wypełnienia** metody **DataAdapter**. Poniższy przykład tworzy **DataTableMapping** o nazwie **AuthorsMapping** dla **autorzy** tabeli.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping** pozwala na użycie nazwy kolumn w **DataTable** różnią od tych w bazie danych. **DataAdapter** wykorzystuje mapowanie, aby dopasować kolumny, gdy zostanie zaktualizowany w tabeli.  
  
 Jeśli nie określisz **TableName** lub **DataTableMapping** nazwy podczas wywoływania **wypełnienia** lub **aktualizacji** metody  **Element DataAdapter**, **DataAdapter** szuka **DataTableMapping** o nazwie "Table". Jeśli to **DataTableMapping** nie istnieje, **TableName** z **DataTable** jest "Table". Można określić domyślną **DataTableMapping** , tworząc **DataTableMapping** o nazwie "Table".  
  
 Poniższy przykład kodu tworzy **DataTableMapping** (z <xref:System.Data.Common> przestrzeni nazw) i sprawia, że do domyślnego mapowania dla określonego **DataAdapter** , nadając mu nazwę "Table". Przykład następnie mapuje kolumn z pierwszej tabeli, w wyniku kwerendy ( **klientów** tabeli **Northwind** bazy danych) do zestawu bardziej przyjazny dla użytkownika nazw **klientów Northwind**  tabelę <xref:System.Data.DataSet>. Dla kolumn, które nie są mapowane nazwa kolumny ze źródła danych jest używana.  
  
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
  
 W bardziej zaawansowanych sytuacjach może zadecydować, ma taki sam **DataAdapter** do obsługi ładowania różnych tabel za pomocą innego mapowania. Aby to zrobić, po prostu dodaj dodatkowe **DataTableMapping** obiektów.  
  
 Gdy **wypełnienia** metoda przechodzi przez wystąpienie **zestawu danych** i **DataTableMapping** nazwę, jeśli mapowanie o tej nazwie istnieje, jest używany; w przeciwnym razie  **DataTable** za pomocą którego nazwa jest używana.  
  
 Poniższe przykłady tworzą **DataTableMapping** o nazwie **klientów** i **DataTable** nazwa **BizTalkSchema**. Przykład następnie mapuje wierszy zwracanych przez instrukcję SELECT do **BizTalkSchema** **DataTable**.  
  
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
>  Jeśli nazwa kolumny źródłowej nie jest podany dla mapowania kolumny lub nie podano nazwy tabeli źródłowej dla mapowania tabeli, domyślne nazwy będą automatycznie generowane. Jeśli nie dostarczono żadnej kolumny źródłowej dla mapowania kolumn, mapowania kolumn otrzymuje przyrostowe domyślną nazwę **SourceColumn** *N,* począwszy od **SourceColumn1**. Jeśli nie dostarczono żadnych nazwy tabeli źródłowej dla mapowania tabeli, Mapowanie tabeli podano przyrostowe domyślną nazwę **SourceTable** *N*, począwszy od **SourceTable1**.  
  
> [!NOTE]
>  Firma Microsoft zaleca, aby unikać konwencji nazewnictwa **SourceColumn** *N* dla mapowania kolumn, lub **SourceTable** *N* dla tabeli mapowania, ponieważ nazwa podasz może spowodować konflikt z istniejącą nazwą kolumny domyślne mapowanie w **ColumnMappingCollection** lub nazwę mapowania tabeli **DataTableMappingCollection** . Podana nazwa już istnieje, zostanie zgłoszony wyjątek.  
  
## <a name="handling-multiple-result-sets"></a>Obsługa wielu zestawów wyników  
 Jeśli Twoje **SelectCommand** zwraca wiele tabel **wypełnienia** automatycznie generuje nazw tabel z wartościami przyrostowych dla tabel w **zestawu danych**, począwszy od Określa nazwę tabeli i kontynuowanie na w formularzu **TableName** *N*, począwszy od **TableName1**. Mapowania tabel służy do mapowania nazwy tabeli automatycznie wygenerowaną nazwę określoną dla tabeli w **zestawu danych**. Na przykład w przypadku **SelectCommand** zwracającego dwie tabele **klientów** i **zamówienia**, wydać następujące wywołanie do **wypełnienia**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 Dwie tabele zostały utworzone w **zestawu danych**: **Klienci** i **Customers1**. Mapowania tabel można użyć, aby upewnić się, że druga tabela ma nazwę **zamówienia** zamiast **Customers1**. Aby to zrobić, mapy źródłowej tabeli **Customers1** do **DataSet** tabeli **zamówienia**, jak pokazano w poniższym przykładzie.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
