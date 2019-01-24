---
title: Dodawanie istniejących ograniczeń do zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 39b1e9945a1cf6cd847fbe82c0b29e50f23bf785
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714152"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Dodawanie istniejących ograniczeń do zestawu danych
**Wypełnienia** metody **DataAdapter** wypełnia <xref:System.Data.DataSet> tylko z tabel, kolumn i wierszy ze źródła danych; jednak ograniczenia są zazwyczaj ustawiane przez źródło danych **wypełnienia** metoda nie dodaje te informacje schematu **DataSet** domyślnie. Aby wypełnić **zestawu danych** z istniejących informacji ograniczenia klucza podstawowego źródła danych, można wywołać **FillSchema** metody **DataAdapter**, lub ustaw **MissingSchemaAction** właściwość **DataAdapter** do **AddWithKey** przed wywołaniem **wypełnienia**. Pozwoli to zagwarantować, że klucz podstawowy ograniczeń **DataSet** odzwierciedlają poglądy w źródle danych. Informacje ograniczenie klucza obcego nie jest uwzględniona i muszą być jawnie, jak pokazano na tworzone [ograniczenia elementu DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Dodawanie informacji o schemacie do **DataSet** przed wypełnianie danych gwarantuje, że ograniczenia klucza podstawowego są dołączone do <xref:System.Data.DataTable> obiekty w **zestawu danych**. W rezultacie, gdy jest to dodatkowe wywołania do wypełnienia **zestawu danych** zostaną wprowadzone, podstawowy informacji o kolumnie klucza jest używany do dopasowywania nowych wierszy ze źródła danych z bieżącej wierszy w każdej **DataTable**oraz bieżące dane tabele zostały zastąpione danych ze źródła danych. Bez informacji o schemacie, nowych wierszy ze źródła danych są dołączane do **DataSet**, dając w efekcie w zduplikowane wiersze.  
  
> [!NOTE]
>  Jeśli kolumny w źródle danych została zidentyfikowana jako automatyczne zwiększanie **FillSchema** metody lub **wypełnienia** metody z **MissingSchemaAction** z  **AddWithKey**, tworzy **DataColumn** z **AutoIncrement** właściwością `true`. Jednakże, należy ustawić **AutoIncrementStep** i **AutoIncrementSeed** wartości samodzielnie. Aby uzyskać więcej informacji o kolumnach zwiększanie automatycznie zobacz [Tworzenie kolumn typu AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Za pomocą **FillSchema** lub ustawienie **MissingSchemaAction** do **AddWithKey** wymaga dodatkowego przetwarzania w źródle danych, aby sprawdzić informacje kolumna klucza podstawowego. To dodatkowe przetwarzanie może zmniejszyć wydajność. Jeśli znasz informacje o kluczu podstawowym w czasie projektowania, zaleca się, że jawnie określisz kolumna klucza podstawowego lub kolumny w celu uzyskania optymalnej wydajności. Aby dowiedzieć się, jak jawne ustawienie informacje o kluczu podstawowym dla tabeli, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 W poniższym przykładzie kodu przedstawiono sposób dodawania informacji o schemacie do **DataSet** przy użyciu **FillSchema**.  
  
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
  
 W poniższym przykładzie kodu przedstawiono sposób dodawania informacji o schemacie do **zestawu danych** przy użyciu **MissingSchemaAction.AddWithKey** właściwość **wypełnienia** metody.  
  
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
 Jeśli **DataAdapter** napotka wielu zestawów wyników zwrócone w wyniku **SelectCommand**, utworzy on wielu tabel w **zestawu danych**. Tabele otrzymają liczony od zera przyrostowe domyślną nazwę **tabeli** *N*, począwszy od **tabeli** zamiast "Table0". Jeśli nazwa tabeli jest przekazywany jako argument do **FillSchema** metody tabel otrzymają liczony od zera nazwę przyrostowe **TableName** *N*, począwszy od **TableName** zamiast "TableName0".  
  
> [!NOTE]
>  Jeśli **FillSchema** metody **OleDbDataAdapter** obiektu jest wywoływana dla polecenia, które zwraca wiele zestawów wyników, informacje schematu pierwszy zestaw wyników jest zwracany. Podczas zwracania informacji o schemacie dla wielu wyników sets przy użyciu **OleDbDataAdapter**, zaleca się, że podajesz **MissingSchemaAction** z **AddWithKey** i uzyskiwanie informacji o schemacie podczas wywoływania **wypełnienia** metody.  
  
## <a name="see-also"></a>Zobacz także
- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
