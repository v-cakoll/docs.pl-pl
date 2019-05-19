---
title: Konfigurowanie parametrów i typów danych parametrów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: 638e8177060c489a7469f80adde68cb9ba266365
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879970"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Konfigurowanie parametrów i typów danych parametrów

Obiekty poleceń parametry do przekazania wartości do instrukcji SQL lub procedur składowanych, zapewniając sprawdzania typu i weryfikacji. W przeciwieństwie do tekstu polecenia wprowadzanie parametrów jest traktowany jako literał, nie jako kod wykonywalny. Dzięki temu można zabezpieczyć się przed "SQL" wstrzyknięciu kodu, w których osoba atakująca Wstawia polecenie Zabezpieczenia naruszeń na serwerze do instrukcji SQL.

Poleceń sparametryzowanych może również zwiększyć wydajność wykonywania zapytań, ponieważ pomagają dokładne dopasowanie przychodzące polecenie z planu prawidłowego zapytania w pamięci podręcznej serwera bazy danych. Aby uzyskać więcej informacji, zobacz [wykonywania Plan pamięci podręcznej i ponowne użycie](/sql/relational-databases/query-processing-architecture-guide#execution-plan-caching-and-reuse) i [parametrów i wykonanie planu ponowne użycie](/sql/relational-databases/query-processing-architecture-guide#PlanReuse). Oprócz korzyści bezpieczeństwo i wydajność poleceń sparametryzowanych zapewniają wygodną metodę służący do organizowania wartości przekazane do źródła danych.

A <xref:System.Data.Common.DbParameter> obiektu można utworzyć za pomocą jej konstruktora lub przez dodanie jej do <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> przez wywołanie metody `Add` metody <xref:System.Data.Common.DbParameterCollection> kolekcji. `Add` Metoda zajmie się jako dane wejściowe w argumentach konstruktora lub parametr obiektu, w zależności od dostawcy danych.

## <a name="supplying-the-parameterdirection-property"></a>Udostępnia właściwości ParameterDirection

Dodając parametry, należy podać <xref:System.Data.ParameterDirection> właściwość parametrów innych niż parametrów wejściowych. W poniższej tabeli przedstawiono `ParameterDirection` wartości, które można używać z <xref:System.Data.ParameterDirection> wyliczenia.

|Nazwa elementu członkowskiego|Opis|
|-----------------|-----------------|
|<xref:System.Data.ParameterDirection.Input>|Parametr jest parametrem wejściowym. Domyślnie włączone.|
|<xref:System.Data.ParameterDirection.InputOutput>|Parametr można wykonywać zarówno dane wejściowe i wyjściowe.|
|<xref:System.Data.ParameterDirection.Output>|Parametr jest parametrem wyjściowym.|
|<xref:System.Data.ParameterDirection.ReturnValue>|Parametr reprezentuje wartość zwracana z operacji, takich jak procedury składowanej, funkcji wbudowanej lub funkcję zdefiniowaną przez użytkownika.|

## <a name="working-with-parameter-placeholders"></a>Praca z symbolami zastępczymi parametru

Składnia dla symboli zastępczych parametru zależy od źródła danych. Dostawcy danych .NET Framework obsługują nazewnictwa i określanie parametrów i symbole zastępcze parametr inaczej. Ta składnia jest dostosowane do określonego źródła danych, zgodnie z opisem w poniższej tabeli.

|Dostawca danych|Składnia nazwy parametru|
|-------------------|-----------------------------|
|<xref:System.Data.SqlClient>|Korzysta z nazwanych parametrów w formacie `@` *parametername*.|
|<xref:System.Data.OleDb>|Używa wskaźników parametr pozycyjne wskazywanym przez znak zapytania (`?`).|
|<xref:System.Data.Odbc>|Używa wskaźników parametr pozycyjne wskazywanym przez znak zapytania (`?`).|
|<xref:System.Data.OracleClient>|Korzysta z nazwanych parametrów w formacie `:` *parmname* (lub *parmname*).|

## <a name="specifying-parameter-data-types"></a>Określenie typów danych parametrów

Typ danych parametru jest specyficzne dla dostawcy danych .NET Framework. Określenie typu konwertuje wartość `Parameter` typ dostawcy danych .NET Framework przed przekazaniem wartości do źródła danych. Możesz również określić typ `Parameter` w sposób ogólny, ustawiając `DbType` właściwość `Parameter` obiektu do określonego <xref:System.Data.DbType>.

Typ dostawcy danych .NET Framework z `Parameter` obiektu jest wnioskowany z typu .NET Framework `Value` z `Parameter` obiektu, albo z `DbType` z `Parameter` obiektu. W poniższej tabeli przedstawiono wywnioskowane `Parameter` typ oparty na obiekcie, który został przekazany jako `Parameter` wartość lub określone `DbType`.

|Typ programu .NET Framework|DbType|SqlDbType|OleDbType|OdbcType|OracleType|
|-------------------------|------------|---------------|---------------|--------------|----------------|
|<xref:System.Boolean>|Boolean|Bit|Boolean|Bit|Byte|
|<xref:System.Byte>|Byte|TinyInt|UnsignedTinyInt|TinyInt|Byte|
|byte[]|plików binarnych|VarBinary. To niejawna konwersja nie powiedzie się, jeśli tablica bajtów jest większy niż maksymalny rozmiar wartości typu VarBinary, czyli 8000 bajtów. Dla tablic bajtów jest większa niż 8000 bajtów, należy jawnie ustawić <xref:System.Data.SqlDbType>.|VarBinary|plików binarnych|nieprzetworzone|
|<xref:System.Char>| |Wnioskowanie <xref:System.Data.SqlDbType> z char nie jest obsługiwane.|Char|Char|Byte|
|<xref:System.DateTime>|DataGodzina|DataGodzina|DBTimeStamp|DataGodzina|DataGodzina|
|<xref:System.DateTimeOffset>|DateTimeOffset|DateTimeOffset programu SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> z DateTimeOffset nie jest obsługiwany w wersjach programu SQL Server starszych niż SQL Server 2008.|||DataGodzina|
|<xref:System.Decimal>|Wartość dziesiętna|Wartość dziesiętna|Wartość dziesiętna|Numeric|Wartość liczbowa|
|<xref:System.Double>|Double|Float|Podwójne|Podwójne|Double|
|<xref:System.Single>|Single|Rzeczywiste|Single|Rzeczywiste|Float|
|<xref:System.Guid>|Guid|UniqueIdentifier|Guid|UniqueIdentifier|nieprzetworzone|
|<xref:System.Int16>|Int16|SmallInt|SmallInt|SmallInt|Int16|
|<xref:System.Int32>|Int32|int|int|int|Int32|
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Wartość liczbowa|
|<xref:System.Object>|Obiekt|Variant|Variant|Wnioskowanie OdbcType z obiektu nie jest obsługiwane.|Blob|
|<xref:System.String>|String|NVarChar. To niejawna konwersja nie powiedzie się, jeśli ciąg jest większy niż maksymalny rozmiar typu NVarChar to 4000 znaków. Ciągi większej niż 4000 znaków, należy jawnie ustawić <xref:System.Data.SqlDbType>.|VarWChar|NVarChar|NVarChar|
|<xref:System.TimeSpan>|Godzina|Czas w programie SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> z przedziału czasu nie jest obsługiwany w wersjach programu SQL Server starszych niż SQL Server 2008.|DBTime|Godzina|DataGodzina|
|<xref:System.UInt16>|UInt16|Wnioskowanie <xref:System.Data.SqlDbType> z UInt16 nie jest obsługiwane.|UnsignedSmallInt|int|UInt16|
|<xref:System.UInt32>|UInt32|Wnioskowanie <xref:System.Data.SqlDbType> z UInt32 nie jest obsługiwane.|unsignedInt|BigInt|UInt32|
|<xref:System.UInt64>|UInt64|Wnioskowanie <xref:System.Data.SqlDbType> z UInt64 nie jest obsługiwane.|UnsignedBigInt|Numeric|Wartość liczbowa|
||AnsiString|VarChar|VarChar|VarChar|VarChar|
||AnsiStringFixedLength|Char|Char|Char|Char|
||Waluta|money|Waluta|Wnioskowanie `OdbcType` z `Currency` nie jest obsługiwane.|Wartość liczbowa|
||Data|Data w programie SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> od daty nie jest obsługiwany w wersjach programu SQL Server starszych niż SQL Server 2008.|DBDate|Data|DataGodzina|
||SByte|Wnioskowanie <xref:System.Data.SqlDbType> z SByte nie jest obsługiwane.|TinyInt|Wnioskowanie `OdbcType` z SByte nie jest obsługiwane.|SByte|
||StringFixedLength|NChar|WChar|NChar|NChar|
||Godzina|Czas w programie SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> od czasu nie jest obsługiwany w wersjach programu SQL Server starszych niż SQL Server 2008.|DBTime|Godzina|DataGodzina|
||VarNumeric|Wnioskowanie <xref:System.Data.SqlDbType> z VarNumeric nie jest obsługiwane.|VarNumeric|Wnioskowanie `OdbcType` z VarNumeric nie jest obsługiwane.|Wartość liczbowa|
|Typ zdefiniowany przez użytkownika (obiektu przy użyciu <xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Obiekt lub ciąg, w zależności od dostawcy (SqlClient zawsze zwraca obiekt, Odbc zawsze zwraca wartość typu ciąg, a następnie zobaczyć albo dostawcy danych zarządzanych OleDb|SqlDbType.Udt Jeśli <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> jest obecna, w przeciwnym razie Variant|OleDbType.VarWChar (jeśli ma wartość null) OleDbType.Variant inaczej.|OdbcType.NVarChar|Nie jest obsługiwany|

> [!NOTE]
> Konwersja dziesiętne na inne typy są zawężających, które zaokrąglona wartość dziesiętną do najbliższej wartości całkowitej w kierunku zera. Jeśli wynik konwersji nie jest stałego w typie docelowym <xref:System.OverflowException> zgłaszany.

> [!NOTE]
> Wartość parametru o wartości null jest wysyłany do serwera, należy określić <xref:System.DBNull>, a nie `null` (`Nothing` w języku Visual Basic). Wartość null w systemie jest pusty obiekt, który nie ma wartości. <xref:System.DBNull> jest używana do reprezentowania wartości null. Aby uzyskać więcej informacji o wartości null w bazie danych, zobacz [Obsługa wartości zerowych](./sql/handling-null-values.md).

## <a name="deriving-parameter-information"></a>Wyprowadzanie informacje o parametrach

Parametry mogą również pochodzić z procedury składowanej przy użyciu `DbCommandBuilder` klasy. Zarówno `SqlCommandBuilder` i `OleDbCommandBuilder` klasy zapewniają statycznej metody `DeriveParameters`, który automatycznie wypełnia kolekcję parametrów obiektu polecenia, który używa parametru informacji z procedury składowanej. Należy pamiętać, że `DeriveParameters` zastępuje wszelkie istniejące informacje parametr dla polecenia.

> [!NOTE]
> Wyprowadzanie informacje o parametrach powoduje spadek wydajności, ponieważ wymaga ona dodatkowej komunikacji dwustronnej źródła danych, aby pobrać informacje. Jeśli informacje o parametrach jest znany w czasie projektowania, może zwiększyć wydajność aplikacji, jawnie ustawiając parametrów.

Aby uzyskać więcej informacji, zobacz [Generowanie poleceń za pomocą CommandBuilders](generating-commands-with-commandbuilders.md).

## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Przy użyciu parametrów SqlCommand i procedury składowanej

Procedury składowane oferują wiele zalet w aplikacjach opartych na danych. Za pomocą procedur składowanych, operacje bazy danych można być hermetyzowane w pojedynczym poleceniu, zoptymalizowane pod kątem uzyskania najlepszej wydajności i rozszerzone o dodatkowe zabezpieczenia. Chociaż procedury składowanej może być wywoływany przez przekazanie nazwy procedury składowanej, następuje argumenty parametrów jako instrukcji SQL przy użyciu <xref:System.Data.Common.DbCommand.Parameters%2A> zbiór ADO.NET <xref:System.Data.Common.DbCommand> obiektu pozwala na zdefiniowanie bardziej jawny sposób procedury składowanej Parametry i dostęp do danych wyjściowych, parametrów i wartości zwracane.

> [!NOTE]
> Sparametryzowanych instrukcji są wykonywane na serwerze przy użyciu `sp_executesql,` pozwalający do ponownego wykorzystania planu zapytania. Kursory lokalne lub zmiennych w `sp_executesql` usługi batch nie są widoczne dla usługi batch, która wywołuje `sp_executesql`. Ostatnie zmiany w kontekście bazy danych tylko na końcu `sp_executesql` instrukcji. Aby uzyskać więcej informacji, zobacz [sp_executesql (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql).

Podczas korzystania z parametrów za pomocą <xref:System.Data.SqlClient.SqlCommand> programu SQL Server wykonaj procedurę składowaną w, nazwy parametrów dodanych do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji musi być zgodne z nazwami znaczników parametr w procedurze składowanej. .NET Framework Data Provider for SQL Server nie obsługuje znaku zapytania (?) — symbol zastępczy przekazywania parametrów do instrukcji SQL lub procedury składowanej. Traktuje parametry w procedurze składowanej jako nazwane parametry, a szuka dopasowania z symbolami parametru. Na przykład `CustOrderHist` procedury składowanej jest definiowana za pomocą parametru o nazwie `@CustomerID`. Gdy kod wykonuje procedurę składowaną, należy również użyć parametru o nazwie `@CustomerID`.

```sql
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)
```

### <a name="example"></a>Przykład

W tym przykładzie przedstawiono sposób wywoływania procedur składowanych serwera SQL Server `Northwind` przykładowej bazy danych. Nazwa procedury składowanej jest `dbo.SalesByCategory` i ma parametr wejściowy o nazwie `@CategoryName` z typem danych `nvarchar(15)`. Ten kod tworzy nową <xref:System.Data.SqlClient.SqlConnection> wewnątrz using blokowania, tak aby połączenie zostanie usunięty po zakończeniu procedury. <xref:System.Data.SqlClient.SqlCommand> i <xref:System.Data.SqlClient.SqlParameter> obiekty są tworzone i ustaw jego właściwości. A <xref:System.Data.SqlClient.SqlDataReader> wykonuje `SqlCommand` i zwraca zestawu wyników z procedury składowanej, wyświetlanie danych wyjściowych w oknie konsoli.

> [!NOTE]
> Zamiast tworzyć `SqlCommand` i `SqlParameter` obiektów, a następnie ustawiając właściwości w osobnych instrukcji, możesz zamiast tego wybrać opcję Użyj jednej z przeciążenia konstruktorów do ustawiania wielu właściwości w pojedynczej instrukcji.

[!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]

## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Przy użyciu parametrów przy użyciu OleDbCommand lub OdbcCommand

Podczas korzystania z parametrów za pomocą <xref:System.Data.OleDb.OleDbCommand> lub <xref:System.Data.Odbc.OdbcCommand>, kolejność parametrów dodanych do `Parameters` kolekcji musi być zgodna z kolejnością parametrów zdefiniowanych w swojej przechowywanej procedurze. .NET Framework Data Provider for OLE DB i .NET Framework Data Provider for ODBC traktować parametry w procedurze składowanej jako symbole zastępcze i stosowanie wartości parametrów w kolejności. Ponadto, zwróć wartość parametry muszą być pierwsze parametry, które są dodawane do `Parameters` kolekcji.

.NET Framework Data Provider for OLE DB i .NET Framework Data Provider for ODBC nie obsługują parametrów nazwanych przekazywania parametrów do instrukcji SQL lub procedury składowanej. W takim przypadku należy użyć symbolu zastępczego znak zapytania (?), jak w poniższym przykładzie.

```sql
SELECT * FROM Customers WHERE CustomerID = ?
```

W rezultacie, kolejność, w której `Parameter` obiekty są dodawane do `Parameters` kolekcji bezpośrednio musi odpowiadać położenie? symbol zastępczy dla parametru.

### <a name="oledb-example"></a>Przykład OleDb

```vb
Dim command As OleDbCommand = New OleDbCommand( _
  "SampleProc", connection)
command.CommandType = CommandType.StoredProcedure

Dim parameter As OleDbParameter = command.Parameters.Add( _
  "RETURN_VALUE", OleDbType.Integer)
parameter.Direction = ParameterDirection.ReturnValue

parameter = command.Parameters.Add( _
  "@InputParm", OleDbType.VarChar, 12)
parameter.Value = "Sample Value"

parameter = command.Parameters.Add( _
  "@OutputParm", OleDbType.VarChar, 28)
parameter.Direction = ParameterDirection.Output
```

```csharp
OleDbCommand command = new OleDbCommand("SampleProc", connection);
command.CommandType = CommandType.StoredProcedure;

OleDbParameter parameter = command.Parameters.Add(
  "RETURN_VALUE", OleDbType.Integer);
parameter.Direction = ParameterDirection.ReturnValue;

parameter = command.Parameters.Add(
  "@InputParm", OleDbType.VarChar, 12);
parameter.Value = "Sample Value";

parameter = command.Parameters.Add(
  "@OutputParm", OleDbType.VarChar, 28);
parameter.Direction = ParameterDirection.Output;
```

## <a name="odbc-example"></a>Przykład ODBC

```vb
Dim command As OdbcCommand = New OdbcCommand( _
  "{ ? = CALL SampleProc(?, ?) }", connection)
command.CommandType = CommandType.StoredProcedure

Dim parameter As OdbcParameter = command.Parameters.Add("RETURN_VALUE", OdbcType.Int)
parameter.Direction = ParameterDirection.ReturnValue

parameter = command.Parameters.Add( _
  "@InputParm", OdbcType.VarChar, 12)
parameter.Value = "Sample Value"

parameter = command.Parameters.Add( _
  "@OutputParm", OdbcType.VarChar, 28)
parameter.Direction = ParameterDirection.Output
```

```csharp
OdbcCommand command = new OdbcCommand( _
  "{ ? = CALL SampleProc(?, ?) }", connection);
command.CommandType = CommandType.StoredProcedure;

OdbcParameter parameter = command.Parameters.Add( _
  "RETURN_VALUE", OdbcType.Int);
parameter.Direction = ParameterDirection.ReturnValue;

parameter = command.Parameters.Add( _
  "@InputParm", OdbcType.VarChar, 12);
parameter.Value = "Sample Value";

parameter = command.Parameters.Add( _
  "@OutputParm", OdbcType.VarChar, 28);
parameter.Direction = ParameterDirection.Output;
```

## <a name="see-also"></a>Zobacz także

- [Polecenia i parametry](commands-and-parameters.md)
- [Parametry elementu DataAdapter](dataadapter-parameters.md)
- [Mapowanie typu danych w ADO.NET](data-type-mappings-in-ado-net.md)
- [Omówienie ADO.NET](ado-net-overview.md)
