---
title: Generowanie poleceń za pomocą CommandBuilders
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: a8767ca492a514f3ee7a2d4688858282ec706ef7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150839"
---
# <a name="generating-commands-with-commandbuilders"></a>Generowanie poleceń za pomocą CommandBuilders
Gdy `SelectCommand` w czasie wykonywania, dynamicznie określono właściwości, takie jak przy użyciu narzędzia kwerendy, wykorzystującej tekstową polecenia od użytkownika, nie można określić odpowiednią `InsertCommand`, `UpdateCommand`, lub `DeleteCommand` w czasie projektowania. Jeśli Twoje <xref:System.Data.DataTable> mapuje lub jest generowana z tabeli pojedynczej bazy danych, możesz korzystać z zalet <xref:System.Data.Common.DbCommandBuilder> obiektu w celu automatycznego generowania `DeleteCommand`, `InsertCommand`, i `UpdateCommand` z <xref:System.Data.Common.DbDataAdapter>.  
  
 Jako minimalne wymaganie, należy ustawić `SelectCommand` właściwości w kolejności do generowania automatycznego polecenia do pracy. Schemat tabeli pobierane przez `SelectCommand` właściwość określa składnię automatycznie generowanych instrukcji INSERT, UPDATE i DELETE.  
  
 <xref:System.Data.Common.DbCommandBuilder> Muszą być wykonywane `SelectCommand` celu zwrócenia niezbędnych do tworzenia poleceń INSERT, UPDATE i Usuń SQL metadanych. W rezultacie niezbędne jest dodatkowe podróży do źródła danych, a to może zmniejszyć wydajność. Aby osiągnąć optymalną wydajność, jawnie określić poleceń, a nie przy użyciu <xref:System.Data.Common.DbCommandBuilder>.  
  
 `SelectCommand` Musi także zwracać co najmniej jeden klucz podstawowy lub unikatowy kolumny. Jeśli żaden nie jest obecny, `InvalidOperation` wygenerowany wyjątek, a polecenia nie są generowane.  
  
 Jeśli są skojarzone z `DataAdapter`, <xref:System.Data.Common.DbCommandBuilder> automatycznie generuje `InsertCommand`, `UpdateCommand`, i `DeleteCommand` właściwości `DataAdapter` przypadku odwołania o wartości null. Jeśli `Command` już istnieje dla właściwości istniejącego `Command` jest używany.  
  
 Widoki bazy danych, które są tworzone przez łączenie dwóch lub więcej tabel nie są uwzględniane tabeli pojedynczej bazy danych. W tym wystąpieniu nie można użyć <xref:System.Data.Common.DbCommandBuilder> można automatycznie wygenerować polecenia; należy jawnie określić poleceń. Informacje o ustawianiu jawnie polecenia, aby rozwiązać aktualizacje `DataSet` do źródła danych, zobacz [aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Możesz chcieć mapowania parametrów wyjściowych zaktualizowany wiersz `DataSet`. Typowe zadania może być pobranie wartości pól identity automatycznie generowanych lub czasu sygnatury ze źródła danych. <xref:System.Data.Common.DbCommandBuilder> Nie będzie mapował parametry wyjściowe do kolumn w zaktualizowany wiersz domyślnie. W tym wystąpieniu należy jawnie określić polecenia. Aby uzyskać przykład mapowania pól automatycznie generowanych identity kolumny wstawionego wiersza, zobacz [pobieranie tożsamości lub wartości automatycznych numerów](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Zasady generowane automatycznie poleceń  
 W poniższej tabeli przedstawiono reguły dla jak automatycznie generowane że polecenia są generowane.  
  
|Polecenie|Reguła|  
|-------------|----------|  
|`InsertCommand`|Wstawia wiersz w źródle danych we wszystkich wierszach w tabeli z <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Added>. Wstawia wartości dla wszystkich kolumn, które są aktualizowalne (ale nie kolumny tożsamości, wyrażenia lub sygnatur czasowych).|  
|`UpdateCommand`|Aktualizuje wierszy w źródle danych we wszystkich wierszach w tabeli z `RowState` z <xref:System.Data.DataRowState.Modified>. Aktualizuje wartości wszystkie kolumny z wyjątkiem kolumn, które nie są aktualizowalne, takich jak tożsamości lub wyrażenia. Aktualizuje wszystkie wiersze, gdzie wartości kolumn w źródle danych pasuje do wartości kolumny klucza podstawowego, wiersza, a pozostałe kolumny w źródle danych pasują do siebie oryginalnych wartości wiersza. Aby uzyskać więcej informacji zobacz "Optymistycznej współbieżności modelu dla aktualizacji i usuwania" w dalszej części tego tematu.|  
|`DeleteCommand`|Usuwa wiersze w źródle danych we wszystkich wierszach w tabeli z `RowState` z <xref:System.Data.DataRowState.Deleted>. Powoduje usunięcie wszystkich wierszy, gdzie wartości kolumny pasują do wartości kolumny klucza podstawowego, wiersza, a pozostałe kolumny w źródle danych pasują do siebie oryginalnych wartości wiersza. Aby uzyskać więcej informacji zobacz "Optymistycznej współbieżności modelu dla aktualizacji i usuwania" w dalszej części tego tematu.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Model optymistycznej współbieżności dla aktualizacji i usunięć  
 Generowanie poleceń automatycznie dla instrukcji UPDATE i DELETE logikę opiera się na *optymistycznej współbieżności*— czyli rekordów nie są zablokowane do edycji i może być modyfikowana przez innych użytkowników lub procesów w dowolnym momencie. Ponieważ może rekord został zmodyfikowany po został zwrócony z instrukcji SELECT, ale przed wystawieniem instrukcji UPDATE lub DELETE automatycznie wygenerowana instrukcja UPDATE lub DELETE zawiera klauzulę WHERE, określając, że wiersza są aktualizowane tylko, jeśli go zawiera wszystkie pierwotne wartości i nie został usunięty ze źródła danych. Odbywa się, aby uniknąć zastąpienia nowych danych. Gdzie aktualizację automatycznie generowanych próbuje zaktualizować wiersza, który został usunięty lub nie zawiera oryginalnej wartości znajdujących się w <xref:System.Data.DataSet>, polecenie nie ma wpływu na wszystkie rekordy i <xref:System.Data.DBConcurrencyException> zgłaszany.  
  
 Jeśli chcesz, UPDATE lub DELETE, aby ukończyć niezależnie od oryginalnych wartości, musisz jawnie ustawić `UpdateCommand` dla `DataAdapter` i nie zależą od generacji automatycznej polecenia.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Ograniczenia polecenia automatyczne generowanie logiki  
 Poniższe ograniczenia mają zastosowanie do automatycznego polecenia generacji.  
  
### <a name="unrelated-tables-only"></a>Tylko niepowiązane tabele  
 Generowanie polecenia automatycznego logika generuje INSERT, AKTUALIZOWANIA lub usuwania instrukcji dla autonomicznych tabel nie biorąc pod uwagę wszystkie relacje z innymi tabelami w źródle danych. W rezultacie mogą wystąpić błąd podczas wywoływania `Update` na przesyłanie zmian do kolumn, które uczestniczą w ograniczenie klucza obcego w bazie danych. Aby uniknąć tego wyjątku, nie należy używać <xref:System.Data.Common.DbCommandBuilder> aktualizowania kolumn uczestniczących w ograniczenie klucza obcego; zamiast tego należy jawnie określić instrukcji używany do wykonania tej operacji.  
  
### <a name="table-and-column-names"></a>Nazw kolumn i tabel  
 Polecenie automatyczne generowanie logiki może zakończyć się niepowodzeniem, jeśli nazwy kolumn lub tabel zawierać żadnych znaków specjalnych, takich jak spacji, kropki, znaki cudzysłowu ani innych znaków innych niż alfanumeryczne nawet wtedy, gdy rozdzielany nawiasami kwadratowymi. W zależności od dostawcy Ustawianie parametrów QuotePrefix i QuoteSuffix może umożliwić logikę generowania procesu miejsca do magazynowania, ale nie można wyeliminować, znaki specjalne. W pełni kwalifikowane nazwy tabeli w formie *catalog.schema.table* są obsługiwane.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Za pomocą CommandBuilder, aby automatycznie wygenerować instrukcji SQL  
 Aby automatycznie wygenerować instrukcji SQL dla `DataAdapter`, najpierw ustawić `SelectCommand` właściwość `DataAdapter`, następnie utwórz `CommandBuilder` obiektu i określona jako argument `DataAdapter` dla którego `CommandBuilder` automatycznie Generuj instrukcje SQL.  
  
```vb  
' Assumes that connection is a valid SqlConnection object   
' inside of a Using block.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", connection)  
Dim builder As SqlCommandBuilder = New SqlCommandBuilder(adapter)  
builder.QuotePrefix = "["  
builder.QuoteSuffix = "]"  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object  
// inside of a using block.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", connection);  
SqlCommandBuilder builder = new SqlCommandBuilder(adapter);  
builder.QuotePrefix = "[";  
builder.QuoteSuffix = "]";  
```  
  
## <a name="modifying-the-selectcommand"></a>Modyfikowanie polecenia SelectCommand  
 Jeśli zmodyfikujesz `CommandText` z `SelectCommand` po polecenia INSERT, UPDATE lub DELETE zostały wygenerowane automatycznie, może wystąpić wyjątek. Jeśli zmodyfikowanego `SelectCommand.CommandText` zawiera informacje o schemacie, która jest niezgodna z `SelectCommand.CommandText` używane podczas wstawiania, aktualizowania lub usuwania polecenia zostały automatycznie generowanych, przyszłe wywołania `DataAdapter.Update` metoda może podejmować prób dostępu do kolumny, istnieje już w bieżącej tabeli odwołuje się `SelectCommand`, i zostanie zgłoszony wyjątek.  
  
 Możesz odświeżyć informacje o schemacie, używane przez `CommandBuilder` do automatycznego generowania poleceń, wywołując `RefreshSchema` metody `CommandBuilder`.  
  
 Jeśli chcesz wiedzieć, jakie polecenia został wygenerowany automatycznie, można uzyskać odwołanie do automatycznie generowanego poleceń przy użyciu `GetInsertCommand`, `GetUpdateCommand`, i `GetDeleteCommand` metody `CommandBuilder` obiektu i sprawdzanie `CommandText`właściwość skojarzone polecenie.  
  
 Poniższy przykład kodu zapisuje do konsoli polecenia update, wygenerowana automatycznie.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 Poniższy przykład tworzy ponownie `Customers` tabelę `custDS` zestawu danych. **RefreshSchema** metoda jest wywoływana, aby odświeżyć automatycznie generowanych poleceń z tym nowych informacji o kolumnie.  
  
```vb  
' Assumes an open SqlConnection and SqlDataAdapter inside of a Using block.  
adapter.SelectCommand.CommandText = _  
  "SELECT CustomerID, ContactName FROM dbo.Customers"  
builder.RefreshSchema()  
  
custDS.Tables.Remove(custDS.Tables("Customers"))  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
// Assumes an open SqlConnection and SqlDataAdapter inside of a using block.  
adapter.SelectCommand.CommandText =   
  "SELECT CustomerID, ContactName FROM dbo.Customers";  
builder.RefreshSchema();  
  
custDS.Tables.Remove(custDS.Tables["Customers"]);  
adapter.Fill(custDS, "Customers");  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Wykonywanie polecenia](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [DbConnection, DbCommand i DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
