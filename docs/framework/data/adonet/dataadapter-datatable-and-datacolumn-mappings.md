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
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Element DataAdapter DataTable i mapowania elementu DataColumn
A **DataAdapter** zawiera kolekcję <xref:System.Data.Common.DataTableMapping> zero lub więcej obiektów w jego **TableMappings** właściwości. **DataTableMapping** zapewnia mapowanie wzorcowe między danymi zwróconych z <xref:System.Data.DataTable>kwerendy względem źródła danych i . **Nazwa DataTableMapping** może być przekazywana zamiast nazwy **DataTable** do **metody Wypełnianie** **dataAdapter**. Poniższy przykład tworzy **DataTableMapping** o nazwie **AuthorsMapping** dla **autorzy** tabeli.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **DataTableMapping** umożliwia użycie nazw kolumn w **DataTable,** które różnią się od tych w bazie danych. **DataAdapter** używa mapowania, aby dopasować kolumny, gdy tabela jest aktualizowana.  
  
 Jeśli nazwa **TableName** lub **DataTableMapping** nie zostanie określona podczas wywoływania metody **Wypełniania** lub **aktualizacji** **programu DataAdapter,** **program DataAdapter** wyszukuje **mapowanie tabeli danych** o nazwie "Tabela". Jeśli **datatableMapping** nie istnieje, **TableName** **datatable** jest "Tabela". Można określić domyślny **DataTableMapping,** tworząc **DataTableMapping** o nazwie "Tabela".  
  
 Poniższy przykład kodu tworzy **DataTableMapping** (z obszaru <xref:System.Data.Common> nazw) i sprawia, że domyślne mapowanie dla określonego **DataAdapter** przez nadanie jej nazwy "Tabela". W przykładzie następnie mapuje kolumny z pierwszej tabeli w wyniku kwerendy (tabela **Klienci** bazy danych **Northwind)** do <xref:System.Data.DataSet>zestawu bardziej przyjaznych dla użytkownika nazw w tabeli **Klienci Northwind** w tabeli . W przypadku kolumn, które nie są mapowane, używana jest nazwa kolumny ze źródła danych.  
  
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
  
 W bardziej zaawansowanych sytuacjach można zdecydować, że chcesz, aby ten sam **DataAdapter** obsługiwać ładowanie różnych tabel z różnych mapowań. Aby to zrobić, wystarczy dodać dodatkowe **obiekty DataTableMapping.**  
  
 Gdy **Fill** metoda jest przekazywana wystąpienie **DataSet** i **DataTableMapping** nazwę, jeśli mapowanie o tej nazwie istnieje jest używany; w przeciwnym razie **datatable** o tej nazwie jest używany.  
  
 Poniższe przykłady tworzą **DataTableMapping** z nazwą **klientów** i nazwą **DataTable** **programu BizTalkSchema**. W przykładzie następnie mapuje wiersze zwrócone przez select instrukcji do **BizTalkSchema** **DataTable**.  
  
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
> Jeśli nazwa kolumny źródłowej nie jest podana dla mapowania kolumn lub nazwa tabeli źródłowej nie jest podana dla mapowania tabeli, nazwy domyślne zostaną wygenerowane automatycznie. Jeśli dla mapowania kolumn nie jest dostarczana żadna kolumna źródłowa, mapowanie kolumn otrzymuje przyrostową domyślną nazwę **SourceColumn** *N,* zaczynając od **SourceColumn1**. Jeśli dla mapowania tabeli nie podano żadnej nazwy tabeli źródłowej, mapowanie tabeli otrzymuje przyrostową domyślną nazwę **Tabeli SourceTable** *N,* zaczynając od **tabeli SourceTable1**.  
  
> [!NOTE]
> Zaleca się unikanie konwencji nazewnictwa **SourceColumn** *N* dla mapowania kolumn lub **SourceTable** *N* dla mapowania tabeli, ponieważ podana nazwa może kolidować z istniejącą domyślną nazwą mapowania kolumn w **nazwie mapowania kolumn lub** mapowania tabeli w **datatablemappingcollection**. Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.  
  
## <a name="handling-multiple-result-sets"></a>Obsługa wielu zestawów wyników  
 Jeśli **selectcommand** zwraca wiele tabel, **Fill** automatycznie generuje nazwy tabel z wartościami przyrostowymi dla tabel w **Zestawie danych,** począwszy od określonej nazwy tabeli i kontynuując w **formularzu TableName** *N*, począwszy od **TableName1**. Za pomocą mapowań tabel można mapować automatycznie wygenerowaną nazwę tabeli na nazwę określoną dla tabeli w **zestawie danych**. Na przykład dla **SelectCommand,** który zwraca dwie tabele, **Klienci** i **Zamówienia**, wystawić następujące wywołanie **Fill**.  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 W zestawie **danych**tworzone są dwie tabele: **Klienci** i **Klienci1**. Można użyć mapowań tabel, aby upewnić się, że druga tabela ma nazwę **Zamówienia** zamiast **Customers1**. Aby to zrobić, mapuj tabelę źródłową **Customers1** do tabeli **DataSet** **Zamówienia**, jak pokazano w poniższym przykładzie.  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a>Zobacz też

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
- [Omówienie ADO.NET](ado-net-overview.md)
