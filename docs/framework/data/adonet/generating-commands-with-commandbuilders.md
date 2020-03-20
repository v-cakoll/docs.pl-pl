---
title: Generowanie poleceń za pomocą CommandBuilders
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: 76c2a6cb0661a0e39fc3a0dd599fcbb3c046f382
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149615"
---
# <a name="generating-commands-with-commandbuilders"></a>Generowanie poleceń za pomocą CommandBuilders
Gdy `SelectCommand` właściwość jest dynamicznie określona w czasie wykonywania, na przykład za pośrednictwem narzędzia kwerendy, które pobiera `InsertCommand` `UpdateCommand`polecenie `DeleteCommand` tekstowe od użytkownika, nie można określić odpowiedniego , lub w czasie projektowania. Jeśli <xref:System.Data.DataTable> mapy do lub jest generowany z jednej tabeli <xref:System.Data.Common.DbCommandBuilder> bazy danych, można `DeleteCommand` `InsertCommand`skorzystać `UpdateCommand` z <xref:System.Data.Common.DbDataAdapter>obiektu, aby automatycznie wygenerować , i .  
  
 Jako wymóg minimalny należy ustawić `SelectCommand` właściwość, aby automatyczne generowanie poleceń działało. Schemat tabeli pobrany `SelectCommand` przez właściwość określa składnię automatycznie generowanych instrukcji INSERT, UPDATE i DELETE.  
  
 Musi <xref:System.Data.Common.DbCommandBuilder> wykonać `SelectCommand` w celu zwrócenia metadanych niezbędnych do konstruowania wstawić, UPDATE i DELETE SQL poleceń. W rezultacie konieczna jest dodatkowa podróż do źródła danych, co może utrudniać działanie. Aby osiągnąć optymalną wydajność, należy określić <xref:System.Data.Common.DbCommandBuilder>polecenia jawnie, a nie za pomocą .  
  
 Musi `SelectCommand` również zwrócić co najmniej jeden klucz podstawowy lub unikatową kolumnę. Jeśli żaden z `InvalidOperation` nich nie jest obecny, wyjątek jest generowany, a polecenia nie są generowane.  
  
 Po skojarzeniu `DataAdapter`z <xref:System.Data.Common.DbCommandBuilder> , automatycznie generuje `InsertCommand` `UpdateCommand`, `DeleteCommand` i `DataAdapter` właściwości, jeśli są one null odwołania. Jeśli `Command` już istnieje dla właściwości, `Command` jest używany istniejący.  
  
 Widoki bazy danych, które są tworzone przez połączenie dwóch lub więcej tabel razem nie są uważane za jedną tabelę bazy danych. W tym przypadku nie <xref:System.Data.Common.DbCommandBuilder> można użyć do automatycznego generowania poleceń; należy określić polecenia jawnie. Aby uzyskać informacje dotyczące jawnego ustawiania `DataSet` poleceń rozpoznawania aktualizacji z powrotem do źródła danych, zobacz [Aktualizowanie źródeł danych za pomocą programów DataAdapters](updating-data-sources-with-dataadapters.md).  
  
 Można zamapować parametry wyjściowe z powrotem do zaktualizowanego wiersza pliku `DataSet`. Jednym z typowych zadań będzie pobieranie wartości automatycznie wygenerowanego pola tożsamości lub sygnatury czasowej ze źródła danych. Domyślnie <xref:System.Data.Common.DbCommandBuilder> nie mapuje parametrów wyjściowych na kolumny w zaktualizowanym wierszu. W tym przypadku należy jawnie określić polecenie. Na przykład mapowania automatycznie wygenerowanego pola tożsamości z powrotem do kolumny wstawionego wiersza zobacz [Pobieranie wartości tożsamości lub Autonumerowania](retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Reguły dla automatycznie generowanych poleceń  
 W poniższej tabeli przedstawiono reguły generowania automatycznie generowanych poleceń.  
  
|Polecenie|Reguła|  
|-------------|----------|  
|`InsertCommand`|Wstawia wiersz u źródła danych dla wszystkich wierszy w tabeli z <xref:System.Data.DataRow.RowState%2A> . <xref:System.Data.DataRowState.Added> Wstawia wartości dla wszystkich kolumn, które można aktualizować (ale nie kolumny, takie jak tożsamości, wyrażenia lub sygnatury czasowe).|  
|`UpdateCommand`|Aktualizuje wiersze w źródle danych dla wszystkich `RowState` wierszy w tabeli z . <xref:System.Data.DataRowState.Modified> Aktualizuje wartości wszystkich kolumn z wyjątkiem kolumn, które nie można aktualizować, takich jak tożsamości lub wyrażenia. Aktualizuje wszystkie wiersze, w których wartości kolumn w źródle danych są zgodne z wartościami kolumn klucza podstawowego wiersza i w których pozostałe kolumny w źródle danych są zgodne z oryginalnymi wartościami wiersza. Aby uzyskać więcej informacji, zobacz "Optymistyczny model współbieżności dla aktualizacji i usuwania", w dalszej części tego tematu.|  
|`DeleteCommand`|Usuwa wiersze u źródła danych dla wszystkich wierszy `RowState` <xref:System.Data.DataRowState.Deleted>w tabeli z plikiem . Usuwa wszystkie wiersze, w których wartości kolumn odpowiadają wartościom kolumny klucza podstawowego wiersza i w których pozostałe kolumny w źródle danych są zgodne z oryginalnymi wartościami wiersza. Aby uzyskać więcej informacji, zobacz "Optymistyczny model współbieżności dla aktualizacji i usuwania", w dalszej części tego tematu.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Optymistyczny model współbieżności dla aktualizacji i usuwania  
 Logika automatycznego generowania poleceń dla instrukcji UPDATE i DELETE opiera się na *optymistycznej współbieżności*- oznacza to, że rekordy nie są zablokowane do edycji i mogą być modyfikowane przez innych użytkowników lub procesy w dowolnym momencie. Ponieważ rekord mógł zostać zmodyfikowany po jego zwrocie z instrukcji SELECT, ale przed wydaniem instrukcji UPDATE lub DELETE, automatycznie wygenerowana instrukcja UPDATE lub DELETE zawiera klauzulę WHERE, określającą, że wiersz jest aktualizowany tylko wtedy, gdy jest aktualizowany zawiera wszystkie oryginalne wartości i nie został usunięty ze źródła danych. Ma to na celu uniknięcie zastępowania nowych danych. W przypadku, gdy automatycznie generowana aktualizacja próbuje zaktualizować wiersz, który został <xref:System.Data.DataSet>usunięty lub który nie zawiera oryginalnych wartości znalezionych w , polecenie nie wpływa na żadne rekordy i <xref:System.Data.DBConcurrencyException> jest wyrzucane.  
  
 Jeśli chcesz UPDATE lub DELETE, aby zakończyć niezależnie od oryginalnych wartości, należy jawnie ustawić `UpdateCommand` dla `DataAdapter` i nie polegać na automatyczne generowanie poleceń.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Ograniczenia logiki automatycznego generowania poleceń  
 Następujące ograniczenia dotyczą automatycznego generowania poleceń.  
  
### <a name="unrelated-tables-only"></a>Tylko niepowiązane tabele  
 Logika automatycznego generowania poleceń generuje instrukcje INSERT, UPDATE lub DELETE dla tabel autonomicznych bez uwzględnienia żadnych relacji z innymi tabelami w źródle danych. W rezultacie może wystąpić błąd podczas `Update` wywoływania do przesyłania zmian dla kolumny, która uczestniczy w ograniczeniu klucza obcego w bazie danych. Aby uniknąć tego wyjątku, <xref:System.Data.Common.DbCommandBuilder> nie należy używać do aktualizowania kolumn zaangażowanych w ograniczenie klucza obcego; zamiast tego jawnie określić instrukcje używane do wykonywania operacji.  
  
### <a name="table-and-column-names"></a>Nazwy tabel i kolumn  
 Logika automatycznego generowania poleceń może zakończyć się niepowodzeniem, jeśli nazwy kolumn lub tabel zawierają znaki specjalne, takie jak spacje, kropki, cudzysłowy lub inne znaki niealphanumeryczne, nawet jeśli są rozdzielone nawiasami. W zależności od dostawcy ustawienie parametrów QuotePrefix i QuoteSuffix może umożliwić logice generowania przetwarzanie spacji, ale nie może uciec przed znakami specjalnymi. Obsługiwane są w pełni kwalifikowane nazwy tabel w postaci *catalog.schema.table.*  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Automatyczne generowanie instrukcji SQL za pomocą narzędzia CommandBuilder  
 Aby automatycznie wygenerować `DataAdapter`instrukcje `SelectCommand` SQL dla `DataAdapter`, najpierw `CommandBuilder` ustaw właściwość , `DataAdapter` a następnie `CommandBuilder` utwórz obiekt i określ jako argument, dla którego będą automatycznie generować instrukcje SQL.  
  
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
  
## <a name="modifying-the-selectcommand"></a>Modyfikowanie selectcommand  
 Jeśli zmodyfikujesz `CommandText` `SelectCommand` polecenia po automatycznym wygenerowaniu poleceń INSERT, UPDATE lub DELETE, może wystąpić wyjątek. Jeśli zmodyfikowane `SelectCommand.CommandText` zawiera informacje o schemacie, który jest niezgodny z `SelectCommand.CommandText` używanym podczas automatycznego `DataAdapter.Update` generowania poleceń wstawiania, aktualizacji lub usuwania, `SelectCommand`przyszłe wywołania metody mogą próbować uzyskać dostęp do kolumn, które już nie istnieją w bieżącej tabeli, do których odwołuje się program , i zostanie zgłoszony wyjątek.  
  
 Można odświeżyć informacje o `CommandBuilder` schemacie używane przez polecenie `RefreshSchema` do `CommandBuilder`automatycznego generowania poleceń, wywołując metodę programu .  
  
 Jeśli chcesz wiedzieć, jakie polecenie zostało wygenerowane automatycznie, możesz uzyskać odwołanie do `GetInsertCommand`automatycznie `GetUpdateCommand`generowanych poleceń za pomocą , i `GetDeleteCommand` metod `CommandBuilder` obiektu i sprawdzania `CommandText` właściwości skojarzonego polecenia.  
  
 Poniższy przykład kodu zapisuje w konsoli polecenie aktualizacji, które zostało wygenerowane automatycznie.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 Poniższy przykład odtwarza `Customers` tabelę `custDS` w zestawie danych. **Metoda RefreshSchema** jest wywoływana w celu odświeżenia automatycznie generowanych poleceń za pomocą tych nowych informacji o kolumnie.  
  
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

- [Polecenia i parametry](commands-and-parameters.md)
- [Wykonywanie polecenia](executing-a-command.md)
- [DbConnection, DbCommand i DbException](dbconnection-dbcommand-and-dbexception.md)
- [Omówienie ADO.NET](ado-net-overview.md)
