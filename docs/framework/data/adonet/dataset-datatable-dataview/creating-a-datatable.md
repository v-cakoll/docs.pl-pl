---
title: Tworzenie DataTable
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
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 68f8272aa0f525c04120f129057e6151e42ffee1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-datatable"></a>Tworzenie DataTable
A <xref:System.Data.DataTable>, który reprezentuje jednej tabeli w pamięci relacyjnej bazie danych, może być tworzone i używane są niezależnie lub może być używany przez inne obiekty .NET Framework najczęściej jako element członkowski <xref:System.Data.DataSet>.  
  
 Można utworzyć **DataTable** obiektu przy użyciu odpowiednich **DataTable** konstruktora. Można dodać go do **DataSet** za pomocą **Dodaj** metodę, aby dodać go do **DataTable** obiektu **tabel** kolekcji.  
  
 Można również utworzyć **DataTable** obiektów w ramach **DataSet** za pomocą **wypełnienia** lub **FillSchema** metody  **Element DataAdapter** obiekt, lub wstępnie zdefiniowanych lub wnioskowany XML schematu używającego **ReadXml**, **ReadXmlSchema**, lub **InferXmlSchema** metody **zestawu danych**. Należy pamiętać, że po dodaniu **DataTable** jako element członkowski **tabel** kolekcji jednego **DataSet**, nie można dodać go do kolekcji tabel innych **Zestawu danych**.  
  
 Po utworzeniu **DataTable**, nie ma schematu (struktury). Aby zdefiniować schemat tabeli, należy utworzyć i dodać <xref:System.Data.DataColumn> obiekty do **kolumn** kolekcji tabeli. Można również zdefiniować kolumna klucza podstawowego dla tabeli i Utwórz i Dodaj **ograniczenia** obiekty do **ograniczenia** kolekcji tabeli. Po zdefiniowaniu schematu **DataTable**, można dodać wiersze danych do tabeli przez dodanie **DataRow** obiekty do **wierszy** kolekcji tabeli.  
  
 Nie musisz podać wartość <xref:System.Data.DataTable.TableName%2A> właściwości po utworzeniu **DataTable**; można określić właściwości w późniejszym terminie, lub pozostawić pusty. Jednak podczas dodawania tabeli bez **TableName** do wartości **DataSet**, tabela zostanie podana przyrostowe domyślną nazwę tabeli*N*począwszy Table0 "tabeli".  
  
> [!NOTE]
>  Firma Microsoft zaleca, aby uniknąć "Tabela*N*" konwencji nazewnictwa, jeśli podasz **TableName** wartości, ponieważ musisz podać nazwę może spowodować konflikt z istniejącą nazwą tabeli domyślne w **zestawu danych** . Jeśli podanej nazwie już istnieje, jest zwracany wyjątek.  
  
 Poniższy przykład tworzy wystąpienie **DataTable** obiektów i przypisuje mu nazwę "Klienci".  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Poniższy przykład tworzy wystąpienie **DataTable** przez dodanie go do **tabel** Kolekcja **zestawu danych**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Wypełnianie zestawu danych z elementu DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
