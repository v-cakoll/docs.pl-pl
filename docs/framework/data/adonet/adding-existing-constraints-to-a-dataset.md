---
title: Dodawanie istniejących ograniczeń do zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: c3c28392a9e4bee0e2f9e0dcf553e13b67c378dd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Dodawanie istniejących ograniczeń do zestawu danych
**Wypełnienia** metody **element DataAdapter** wypełnia <xref:System.Data.DataSet> tylko z tabeli kolumn i wierszy ze źródła danych; jednak ograniczenia są często ustawione przez źródło danych **wypełnienia** — metoda nie dodaje te informacje schematu **DataSet** domyślnie. Aby wypełnić **zestawu danych** z istniejących informacji ograniczenia klucza podstawowego źródła danych, możesz albo wywołanie **FillSchema** metody **element DataAdapter**, lub ustaw **MissingSchemaAction** właściwość **element DataAdapter** do **AddWithKey** przed wywołaniem **wypełnienia**. Daje to pewność, że klucz podstawowy ograniczeń **DataSet** odzwierciedlają w źródle danych. Ograniczenie klucza obcego informacji nie jest dołączana i muszą być tworzone jawne, jak pokazano w [ograniczenia DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Dodawanie informacji o schemacie **DataSet** przed wypełnianie danymi zapewnia, że ograniczenia klucza podstawowego są dołączone do <xref:System.Data.DataTable> obiekty w **zestawu danych**. W rezultacie, gdy dodatkowe wywołania do wypełnienia **zestawu danych** zostają podstawową informacji o kolumnie klucza jest używany do dopasowywania nowych wierszy ze źródła danych z bieżącej wierszy w każdym **DataTable**i bieżące dane w tabele zostały zastąpione danych ze źródła danych. Bez informacji o schemacie, nowych wierszy ze źródła danych są dołączane do **DataSet**, co zduplikowane wiersze.  
  
> [!NOTE]
>  Jeśli kolumny w źródle danych została zidentyfikowana jako automatyczne zwiększanie **FillSchema** metody, lub **wypełnienia** metody z **MissingSchemaAction** z  **AddWithKey**, tworzy **DataColumn** z **AutoIncrement** ustawioną właściwość `true`. Jednak należy ustawić **elementu AutoIncrementStep** i **AutoIncrementSeed** wartości samodzielnie. Aby uzyskać więcej informacji o kolumnach zwiększanie automatycznego, zobacz [Tworzenie kolumny typu AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Przy użyciu **FillSchema** lub ustawienie **MissingSchemaAction** do **AddWithKey** wymaga dodatkowego przetwarzania w źródle danych, aby ustalić informacji o kolumnie klucza podstawowego. To dodatkowe przetwarzanie może zmniejszyć wydajność. Jeśli znasz informacje o kluczu podstawowym w czasie projektowania, zaleca się, że zostaną jawnie określone kolumny klucza podstawowego lub kolumny w celu osiągnięcia optymalnej wydajności. Aby dowiedzieć się, jak jawne ustawienie informacje o kluczu podstawowym dla tabeli, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 W poniższym przykładzie przedstawiono sposób dodawania informacji o schemacie **DataSet** przy użyciu **FillSchema**.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 W poniższym przykładzie przedstawiono sposób dodawania informacji o schemacie **DataSet** przy użyciu **MissingSchemaAction.AddWithKey** właściwość **wypełnienia** metody.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>Obsługa wielu zestawów wyników  
 Jeśli **element DataAdapter** napotka zwrócony z wielu zestawów wyników **SelectCommand**, utworzy on wiele tabel w **zestawu danych**. Tabele otrzymają liczony od zera przyrostowe domyślną nazwę **tabeli** *N*począwszy **tabeli** zamiast "Table0". Jeśli nazwa tabeli jest przekazywany jako argument **FillSchema** metody tabele otrzymają liczony od zera nazwę przyrostowe **TableName** *N*począwszy **TableName** zamiast "TableName0".  
  
> [!NOTE]
>  Jeśli **FillSchema** metody **elementu OleDbDataAdapter** obiektu po wywołaniu polecenia, która zwraca wiele zestawów wyników jest zwracany tylko informacji schematu z pierwszego zestawu wyników. Gdy zwracanie informacji o schemacie dla wielu wyników ustawia przy użyciu **elementu OleDbDataAdapter**, zaleca się, że podajesz **MissingSchemaAction** z **AddWithKey** i uzyskiwanie informacji o schemacie podczas wywoływania metody **wypełnienia** metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
