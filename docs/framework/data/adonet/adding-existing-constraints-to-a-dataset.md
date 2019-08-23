---
title: Dodawanie istniejących ograniczeń do zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 05f95a9c4f250100ca97e3ab52e4073d027df1b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932198"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Dodawanie istniejących ograniczeń do zestawu danych
Metoda **Fill** elementu **DataAdapter** wypełnia <xref:System.Data.DataSet> tylko za pomocą kolumn tabeli i wierszy ze źródła danych; Chociaż ograniczenia są zwykle ustawiane przez źródło danych, Metoda **Fill** nie dodaje do niego **informacji o schemacie. Domyślnie zestaw danych** . Aby wypełnić **zestaw danych** istniejącymi informacjami o ograniczeniach klucza podstawowego ze źródła danych, można wywołać metodę **FillSchema** obiektu **DataAdapter**lub ustawić właściwość **MissingSchemaAction** elementu **DataAdapter** do **AddWithKey** przed wywołaniem **Fill**. Zapewni to, że ograniczenia PRIMARY KEY w **zestawie danych** odzwierciedlają te w źródle danych. Informacje o ograniczeniu klucza obcego nie są uwzględniane i muszą zostać utworzone jawnie, jak pokazano w [ograniczeniach DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Dodawanie informacji o schemacie do **zestawu danych** przed wypełnieniem go danymi gwarantuje, że ograniczenia PRIMARY KEY <xref:System.Data.DataTable> są dołączone do obiektów w **zestawie danych**. W związku z tym po wprowadzeniu dodatkowych wywołań w celu wypełnienia **zestawu danych** informacje o kolumnie klucza podstawowego są używane do dopasowania nowych wierszy ze źródła danych z bieżącymi wierszami w każdej **DataTable**, a bieżące dane w tabelach są zastępowane danymi z Źródło danych. Bez informacji o schemacie nowe wiersze ze źródła danych są dołączane do **zestawu danych**, co powoduje duplikowanie wierszy.  
  
> [!NOTE]
> Jeśli kolumna w źródle danych jest identyfikowana jako funkcja autozwiększania, Metoda **FillSchema** lub metoda **Fill** z MissingSchemaActionem **AddWithKey**, tworzy **kolumnę DataColumn** z właściwością **AutoIncrement** Ustaw wartość `true`. Należy jednak ręcznie ustawić wartości **AutoIncrementStep** i **AutoIncrementSeed** . Aby uzyskać więcej informacji na temat autouzupełniania kolumn, zobacz [Tworzenie kolumn typu AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Użycie **FillSchema** lub ustawienie **MissingSchemaAction** na **AddWithKey** wymaga dodatkowego przetwarzania w źródle danych, aby określić informacje o kolumnie klucza podstawowego. To dodatkowe przetwarzanie może utrudnić wydajność. Jeśli znasz informacje o kluczu podstawowym w czasie projektowania, zalecamy jawne określenie kolumny klucza podstawowego lub kolumn w celu uzyskania optymalnej wydajności. Aby uzyskać informacje na temat jawnego ustawiania informacji o kluczu podstawowym dla tabeli, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Poniższy przykład kodu pokazuje, jak dodać informacje o schemacie do **zestawu danych** przy użyciu **FillSchema**.  
  
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
  
 Poniższy przykład kodu pokazuje, jak dodać informacje o schemacie do **zestawu danych** przy użyciu właściwości **MissingSchemaAction. AddWithKey** metody **Fill** .  
  
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
 Jeśli obiekt **DataAdapter** napotka wiele zestawów wyników zwróconych z elementu **SelectCommand**, utworzy wiele tabel w **zestawie danych**. W tabelach zostanie nadana przyrostowa, zerowa nazwa domyślna **tabeli** *N*, rozpoczynając od **tabeli** zamiast "TABLE0". Jeśli nazwa tabeli jest przenoszona jako argument do metody **FillSchema** , w tabelach zostanie nadana przyrostowa, różna od zera nazwa tabeliname *N*, rozpoczynająca się od nazwy TableName zamiast "TableName0".  
  
> [!NOTE]
> Jeśli metoda **FillSchema** obiektu **elementu OleDbDataAdapter** jest wywoływana dla polecenia, które zwraca wiele zestawów wyników, zwracane są tylko informacje o schemacie z pierwszego zestawu wyników. Podczas zwracania informacji o schemacie dla wielu zestawów wyników przy użyciu **elementu OleDbDataAdapter**zaleca się określenie **MissingSchemaAction** **AddWithKey** i uzyskanie informacji o schemacie podczas wywoływania **wypełnienia** . Method.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
