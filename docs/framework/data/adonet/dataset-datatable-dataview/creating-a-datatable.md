---
title: Tworzenie elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: b56d2f8cd46f3184f1001c8bd6a70dbfc4968968
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937031"
---
# <a name="creating-a-datatable"></a>Tworzenie elementu DataTable
A <xref:System.Data.DataTable>, który reprezentuje jedną tabelę danych relacyjnych w pamięci, może być tworzony i używany niezależnie lub może być używany przez inne obiekty .NET Framework, najczęściej jako element członkowski <xref:System.Data.DataSet>.  
  
 Obiekt **DataTable** można utworzyć przy użyciu odpowiedniego konstruktora **DataTable** . Możesz dodać go do **zestawu danych** za pomocą metody **Add** , aby dodać go do kolekcji **tabel** obiektu **DataTable** .  
  
 Można również tworzyć obiekty **DataTable** w ramach **zestawu danych** przy użyciu metod **Fill** lub **FillSchema** obiektu **DataAdapter** lub ze wstępnie zdefiniowanego lub wywnioskowanego schematu XML przy użyciu **ReadXml**, **ReadXmlSchema** lub **InferXmlSchema** metody **zestawu danych**. Należy pamiętać, że po dodaniu **DataTable** jako członka kolekcji **tabel** jednego **zestawu danych**nie można dodać go do kolekcji tabel innego **zestawu danych**.  
  
 Podczas pierwszej tworzenia **elementu DataTable**nie ma schematu (czyli struktury). Aby zdefiniować schemat tabeli, należy utworzyć i dodać <xref:System.Data.DataColumn> obiekty do kolekcji **kolumn** tabeli. Istnieje również możliwość zdefiniowania kolumny klucza podstawowego dla tabeli oraz utworzenia i dodania obiektów **ograniczeń** do kolekcji **ograniczenia** tabeli. Po zdefiniowaniu schematu dla **elementu DataTable**można dodać wiersze danych do tabeli przez dodanie obiektów **DataRow** do kolekcji **Rows** tabeli.  
  
 Nie trzeba podawać wartości <xref:System.Data.DataTable.TableName%2A> właściwości podczas tworzenia **elementu DataTable**; można określić właściwość w innym czasie lub pozostawić ją pustą. Jednak po dodaniu tabeli bez wartości TableName do **zestawu danych**w tabeli zostanie nadana przyrostowa domyślna nazwa tabeli*N*, rozpoczynając od "Tabela" dla TABLE0.  
  
> [!NOTE]
> Zalecamy uniknięcie konwencji nazewnictwa "Table*N*" w przypadku podania wartości **TableName** , ponieważ wprowadzona nazwa może powodować konflikt z istniejącą domyślną nazwą tabeli w **zestawie danych**. Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.  
  
 Poniższy przykład tworzy wystąpienie obiektu **DataTable** i przypisuje mu nazwę "Customers".  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Poniższy przykład tworzy wystąpienie **elementu DataTable** przez dodanie go do kolekcji **Tables** **zestawu danych**.  
  
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
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
