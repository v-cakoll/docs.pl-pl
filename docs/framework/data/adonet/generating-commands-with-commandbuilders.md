---
title: "Generowanie poleceń CommandBuilders"
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
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e945b4b6c646a0210f781d1ba43b5cd931cfef6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generating-commands-with-commandbuilders"></a>Generowanie poleceń CommandBuilders
Gdy `SelectCommand` właściwość dynamicznie jest określona w czasie wykonywania, takie jak przy użyciu narzędzia kwerendy pobierającej tekstową polecenia od użytkownika, nie można określić odpowiednie `InsertCommand`, `UpdateCommand`, lub `DeleteCommand` w czasie projektowania. Jeśli Twoje <xref:System.Data.DataTable> mapuje lub jest generowany z jednej bazy danych, możesz korzystać z <xref:System.Data.Common.DbCommandBuilder> obiektu w celu automatycznego generowania `DeleteCommand`, `InsertCommand`, i `UpdateCommand` z <xref:System.Data.Common.DbDataAdapter>.  
  
 Jako minimalne wymaganie, należy ustawić `SelectCommand` właściwości, aby polecenie automatycznego generowania do pracy. Schemat tabeli pobierane przez `SelectCommand` właściwość określa składnię automatycznie generowanych instrukcje INSERT, UPDATE i DELETE.  
  
 <xref:System.Data.Common.DbCommandBuilder> Musi być wykonywany `SelectCommand` celu powrotu metadane wymagane do utworzenia polecenia INSERT, UPDATE i usunąć SQL. W związku z tym niezbędne jest dodatkowe podróży do źródła danych, a to może zmniejszyć wydajność. Aby osiągnąć optymalną wydajność, ustaw jawnie poleceniach zamiast <xref:System.Data.Common.DbCommandBuilder>.  
  
 `SelectCommand` Musi także zwracać co najmniej jeden klucz podstawowy lub unikatowy kolumny. Jeśli nie są obecne, `InvalidOperation` wygenerowany wyjątek i nie są generowane polecenia.  
  
 Jeśli są skojarzone z `DataAdapter`, <xref:System.Data.Common.DbCommandBuilder> automatycznie generuje `InsertCommand`, `UpdateCommand`, i `DeleteCommand` właściwości `DataAdapter` jeśli są puste odwołania. Jeśli `Command` już istnieje dla właściwości istniejącej `Command` jest używany.  
  
 Widoki bazy danych, które są tworzone przez łączenie co najmniej dwie tabele nie są uznawane za tabelę pojedynczej bazy danych. W tym wystąpieniu nie można użyć <xref:System.Data.Common.DbCommandBuilder> mają być automatycznie generowane polecenia; należy jawnie określić poleceniach. Informacje o ustawianiu jawnie poleceń, aby rozpoznać aktualizacje `DataSet` do źródła danych, zobacz [aktualizowanie źródła danych z obiektów DataAdapter](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Możesz chcieć mapowania parametrów wyjściowych zaktualizowany wiersz `DataSet`. Typowe zadania może być odczytywania wartości pola automatycznie wygenerowaną tożsamość lub czasu sygnatury ze źródła danych. <xref:System.Data.Common.DbCommandBuilder> Nie będzie mapował parametry wyjściowe do kolumn w zaktualizowany wiersz domyślnie. W tym wystąpieniu należy jawnie określić polecenia. Przykład mapowania pól automatycznie generowanych identity kolumny wstawionego wiersza, zobacz [pobierania tożsamości lub wartości automatycznie numerowane](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Zasady są generowane automatycznie poleceń  
 W poniższej tabeli przedstawiono zasady dla jak automatycznie generowane polecenia są wygenerowanych.  
  
|Polecenie|Reguła|  
|-------------|----------|  
|`InsertCommand`|Wstawia wiersz w źródle danych dla wszystkich wierszy w tabeli o <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Added>. Wstawia wartości dla wszystkich kolumn, które są aktualizowalne (ale nie kolumny tożsamości, wyrażenia lub sygnatury czasowe).|  
|`UpdateCommand`|Aktualizuje wierszy w źródle danych dla wszystkich wierszy w tabeli o `RowState` z <xref:System.Data.DataRowState.Modified>. Aktualizuje wartości wszystkich kolumn z wyjątkiem kolumny, które nie są aktualizowalne, takich jak tożsamości lub wyrażenia. Aktualizuje wszystkie wiersze, gdzie wartości w kolumnie w źródle danych pasuje do wartości kolumny klucza podstawowego wiersza, a pozostałe kolumny w źródle danych takie same jak oryginalne wartości wiersza. Aby uzyskać więcej informacji zobacz "Optymistycznej współbieżności modelu dla aktualizacji i usuwania" w dalszej części tego tematu.|  
|`DeleteCommand`|Usuwa wierszy w źródle danych dla wszystkich wierszy w tabeli o `RowState` z <xref:System.Data.DataRowState.Deleted>. Usuwa wszystkie wiersze, gdzie wartości kolumny pasują do wartości kolumny klucza podstawowego, wiersza, a pozostałe kolumny w źródle danych takie same jak oryginalne wartości wiersza. Aby uzyskać więcej informacji zobacz "Optymistycznej współbieżności modelu dla aktualizacji i usuwania" w dalszej części tego tematu.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Model optymistycznej współbieżności dla aktualizacji i usunięć  
 Logika generowania poleceń automatycznie dla instrukcji UPDATE i DELETE jest oparta na *optymistycznej współbieżności*— to znaczy rekordy nie są zablokowane do edycji i może być modyfikowany przez innych użytkowników lub procesów w dowolnym momencie. Ponieważ może rekord został zmodyfikowany po został zwrócony z instrukcją SELECT, ale przed wystawieniem instrukcji UPDATE lub DELETE automatycznie generowanego instrukcji UPDATE lub DELETE zawiera klauzulę WHERE, określając, czy wiersz jest aktualizowana tylko, jeśli go zawiera wszystkie pierwotne wartości i nie zostały usunięte ze źródła danych. Można to zrobić, aby uniknąć zastępowania nowych danych. Gdzie aktualizację automatycznie generowanych podejmuje próbę zaktualizowania wiersza, który został usunięty lub nie zawiera oryginalnej wartości znajdujących się w <xref:System.Data.DataSet>, polecenie nie ma wpływu na rekordy, a <xref:System.Data.DBConcurrencyException> jest generowany.  
  
 Jeśli chcesz, UPDATE lub DELETE, aby ukończyć niezależnie od oryginalnych wartości, musisz jawnie ustawić `UpdateCommand` dla `DataAdapter` i nie zależą od polecenia automatycznego generowania.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Ograniczenia polecenia automatycznego generowania logiki  
 Następujące ograniczenia mają zastosowanie do polecenia automatycznego generowania.  
  
### <a name="unrelated-tables-only"></a>Tylko niepowiązane tabele  
 Generacji polecenie automatyczne logiki generuje WSTAWIANIA, AKTUALIZOWANIA lub usuwania instrukcje dla autonomicznego tabel bez uwzględnienia żadnych relacji z innymi tabelami w źródle danych. W związku z tym można napotkać błąd podczas wywoływania metody `Update` można przesłać zmian dla kolumny, która uczestniczy w ograniczenie klucza obcego w bazie danych. Aby uniknąć tego wyjątku, nie należy używać <xref:System.Data.Common.DbCommandBuilder> dla aktualizowanie kolumn objętego ograniczenie klucza obcego; zamiast tego należy jawnie określić instrukcje używany do wykonania tej operacji.  
  
### <a name="table-and-column-names"></a>Tabela i nazwy kolumn  
 Polecenie automatyczne generowanie logiki może się niepowodzeniem, jeśli nazwy kolumny lub tabeli zawierać żadnych znaków specjalnych, takich jak spacje, kropki, znaki cudzysłowu lub innych znaków innych niż alfanumeryczne, nawet jeśli rozdzielany nawiasami kwadratowymi. W zależności od dostawcy Ustawianie parametrów QuotePrefix i QuoteSuffix mogą zezwolić logika generowania procesu spacje, ale nie mogą opuścić znaki specjalne. W pełni kwalifikowana nazwy tabeli w formie *catalog.schema.table* są obsługiwane.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Przy użyciu CommandBuilder można automatycznie wygenerować instrukcji SQL  
 Można automatycznie wygenerować instrukcji SQL dla `DataAdapter`, najpierw ustaw `SelectCommand` właściwość `DataAdapter`, następnie utwórz `CommandBuilder` obiekt, a następnie określ jako argument `DataAdapter` dla którego `CommandBuilder` automatycznie Generuj instrukcje SQL.  
  
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
  
## <a name="modifying-the-selectcommand"></a>Modyfikowanie właściwości polecenia SelectCommand  
 Jeśli zmodyfikujesz `CommandText` z `SelectCommand` po polecenia INSERT, UPDATE lub DELETE zostały wygenerowane automatycznie, może wystąpić wyjątek. Jeśli zmodyfikowanych `SelectCommand.CommandText` zawiera informacje o schemacie, która jest niespójna z `SelectCommand.CommandText` używane podczas wstawiania, aktualizowania lub usuwania polecenia zostały automatycznie wygenerowaną, przyszłych wywołaniach `DataAdapter.Update` metody może próbować uzyskują dostęp do kolumn który istnieje już w bieżącej tabeli odwołuje się `SelectCommand`, i zostanie wygenerowany wyjątek.  
  
 Można odświeżyć informacji o schemacie, używany przez `CommandBuilder` mają być automatycznie generowane polecenia przez wywołanie metody `RefreshSchema` metody `CommandBuilder`.  
  
 Jeśli chcesz dowiedzieć się, jakie polecenia została wygenerowana automatycznie, można uzyskać odwołania do automatycznie generowanego poleceń za pomocą `GetInsertCommand`, `GetUpdateCommand`, i `GetDeleteCommand` metody `CommandBuilder` obiektu i sprawdzanie `CommandText`właściwości skojarzone polecenie.  
  
 Poniższy przykład kodu zapisuje do konsoli polecenia update, który został wygenerowany automatycznie.  
  
```  
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```  
  
 Poniższy przykład tworzy ponownie `Customers` w tabeli `custDS` zestawu danych. **RefreshSchema** metoda jest wywoływana, aby odświeżyć automatycznie generowane polecenia o nowe informacje kolumny.  
  
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
 [Poleceń i parametrów](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Wykonywanie polecenia](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [Obiektu DbConnection, polecenie DbCommand i dbexception —](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
