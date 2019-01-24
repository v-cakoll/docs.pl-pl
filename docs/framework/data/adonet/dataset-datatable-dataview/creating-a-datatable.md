---
title: Tworzenie elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: f40a04156bee5ceee7490cf7bd941dc11a99b880
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608320"
---
# <a name="creating-a-datatable"></a>Tworzenie elementu DataTable
A <xref:System.Data.DataTable>, która reprezentuje jedną tabelę danych relacyjnych w pamięci, mogą być tworzone i używane niezależnie lub mogą być używane przez inne obiekty .NET Framework najczęściej jako członek <xref:System.Data.DataSet>.  
  
 Możesz utworzyć **DataTable** , używając odpowiedniego obiektu **DataTable** konstruktora. Możesz dodać go do **DataSet** przy użyciu **Dodaj** metodę, aby dodać go do **DataTable** obiektu **tabel** kolekcji.  
  
 Można również utworzyć **DataTable** obiektów w ramach **DataSet** przy użyciu **wypełnienia** lub **FillSchema** metody  **Element DataAdapter** obiektu, albo z wstępnie zdefiniowanych lub wywnioskowane uprawnienie XML przy użyciu schematu **ReadXml**, **ReadXmlSchema**, lub **InferXmlSchema** metody **zestawu danych**. Należy pamiętać, że po dodaniu **DataTable** jako członek **tabel** kolekcji jednego **DataSet**, nie można dodać go do kolekcji tabel innych **Zestawu danych**.  
  
 Kiedy należy najpierw utworzyć **DataTable**, nie ma schematu (struktury). Aby zdefiniować schemat tabeli, należy utworzyć i dodać <xref:System.Data.DataColumn> obiekty do **kolumn** kolekcji tabeli. Można również zdefiniować kolumna klucza podstawowego dla tabeli i utworzyć i dodać **ograniczenie** obiekty do **ograniczenia** kolekcji tabeli. Po zdefiniowaniu schematu dla **DataTable**, można dodać wiersze danych do tabeli przez dodanie **DataRow** obiekty do **wierszy** kolekcji tabeli.  
  
 Nie należy podać wartość <xref:System.Data.DataTable.TableName%2A> właściwości po utworzeniu **DataTable**; można określić właściwości w innym czasie, lub możesz pozostawić je puste. Jednak podczas dodawania tabeli bez **TableName** wartość **DataSet**, tabela zostanie podana przyrostowe domyślną nazwę tabeli*N*, począwszy od Table0 "tabeli".  
  
> [!NOTE]
>  Firma Microsoft zaleca, aby unikać "Tabela*N*" konwencji nazewnictwa, gdy użytkownik poda **TableName** wartości, ponieważ nazwa podasz może spowodować konflikt z istniejącą nazwą tabeli domyślne w **zestawu danych** . Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.  
  
 Poniższy przykład tworzy wystąpienie **DataTable** obiektu i przypisuje mu nazwę "Klientów."  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Poniższy przykład tworzy wystąpienie **DataTable** przez dodanie jej do **tabel** zbiór **zestawu danych**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [Wypełnianie zestawu danych z elementu DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
