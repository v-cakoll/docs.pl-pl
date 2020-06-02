---
title: Konfigurowanie parametrów i typów danych parametrów
description: Obiekty poleceń używają parametrów do przekazywania wartości do instrukcji SQL lub procedur składowanych, zapewniając sprawdzanie typu i weryfikację w ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: a426eeae785274b0484a84a2fae2dce4572fb4c4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287119"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Konfigurowanie parametrów i typów danych parametrów

Obiekty poleceń używają parametrów do przekazywania wartości do instrukcji SQL lub procedur składowanych, zapewniając sprawdzanie typu i weryfikację. W przeciwieństwie do tekstu polecenia, wprowadzanie parametrów jest traktowane jako wartość literału, a nie jako kod wykonywalny. Pomaga to chronić przed atakami "iniekcji SQL", w których osoba atakująca wstawia polecenie naruszające zabezpieczenia serwera do instrukcji SQL.

Polecenia sparametryzowane mogą również zwiększyć wydajność wykonywania zapytań, ponieważ ułatwiają one serwerowi bazy danych dokładne dopasowanie do polecenia przychodzącego z prawidłowym buforowanym planem zapytań. Aby uzyskać więcej informacji, zobacz [buforowanie i ponowne użycie planu wykonywania](/sql/relational-databases/query-processing-architecture-guide#execution-plan-caching-and-reuse) oraz ponowne używanie [parametrów i planu wykonania](/sql/relational-databases/query-processing-architecture-guide#PlanReuse). Oprócz korzyści związanych z zabezpieczeniami i wydajnością, polecenia sparametryzowane zapewniają wygodną metodę organizowania wartości przesyłanych do źródła danych.

<xref:System.Data.Common.DbParameter>Obiekt można utworzyć za pomocą jego konstruktora lub przez dodanie go do obiektu <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> przez wywołanie `Add` metody <xref:System.Data.Common.DbParameterCollection> kolekcji. `Add`Metoda przyjmuje jako dane wejściowe argumenty konstruktora lub istniejący obiekt parametru, w zależności od dostawcy danych.

## <a name="supplying-the-parameterdirection-property"></a>Dostarczanie właściwości ParameterDirection

Podczas dodawania parametrów należy podać <xref:System.Data.ParameterDirection> Właściwość parametrów innych niż parametry wejściowe. W poniższej tabeli przedstawiono `ParameterDirection` wartości, których można użyć z <xref:System.Data.ParameterDirection> wyliczeniem.

|Nazwa elementu członkowskiego|Opis|
|-----------------|-----------------|
|<xref:System.Data.ParameterDirection.Input>|Parametr jest parametrem wejściowym. Domyślnie włączone.|
|<xref:System.Data.ParameterDirection.InputOutput>|Parametr może wykonywać zarówno dane wejściowe, jak i wyjściowe.|
|<xref:System.Data.ParameterDirection.Output>|Parametr jest parametrem wyjściowym.|
|<xref:System.Data.ParameterDirection.ReturnValue>|Parametr reprezentuje wartość zwracaną z operacji, takiej jak procedura składowana, wbudowana funkcja lub funkcja zdefiniowana przez użytkownika.|

## <a name="working-with-parameter-placeholders"></a>Praca z symbolami zastępczymi parametrów

Składnia symboli zastępczych parametrów zależy od źródła danych. Dostawcy danych .NET Framework obsługują nazewnictwo i Określanie parametrów i symboli zastępczych parametrów w różny sposób. Ta składnia jest dostosowana do określonego źródła danych, zgodnie z opisem w poniższej tabeli.

|Dostawca danych|Składnia nazewnictwa parametrów|
|-------------------|-----------------------------|
|<xref:System.Data.SqlClient>|Używa nazwanych parametrów w formacie `@` *ParameterName*.|
|<xref:System.Data.OleDb>|Używa znaczników parametrów pozycyjnych wskazanych przez znak zapytania ( `?` ).|
|<xref:System.Data.Odbc>|Używa znaczników parametrów pozycyjnych wskazanych przez znak zapytania ( `?` ).|
|<xref:System.Data.OracleClient>|Używa nazwanych parametrów w formacie `:` *parmname* (lub *parmname*).|

## <a name="specifying-parameter-data-types"></a>Określanie typów danych parametrów

Typ danych parametru jest specyficzny dla dostawcy danych .NET Framework. Określenie typu spowoduje konwersję wartości `Parameter` do typu .NET Framework dostawcy danych przed przekazaniem wartości do źródła danych. Można również określić typ a `Parameter` w ogólny sposób, ustawiając `DbType` Właściwość `Parameter` obiektu na konkretną <xref:System.Data.DbType> .

Typ dostawcy danych .NET Frameworkgo `Parameter` obiektu jest wywnioskowany na podstawie typu .NET Framework `Value` `Parameter` obiektu lub z `DbType` `Parameter` obiektu. W poniższej tabeli przedstawiono typ wnioskowany `Parameter` na podstawie obiektu przekazanego jako `Parameter` wartość lub określony `DbType` .

|Typ programu .NET Framework|DbType|DbType|OleDbType|OdbcType|OracleType|
|-------------------------|------------|---------------|---------------|--------------|----------------|
|<xref:System.Boolean>|Boolean (wartość logiczna)|Bit|Boolean (wartość logiczna)|Bit|Byte|
|<xref:System.Byte>|Byte|TinyInt|UnsignedTinyInt|TinyInt|Byte|
|Byte []|Binarne|Liczby. Ta niejawna konwersja zakończy się niepowodzeniem, jeśli tablica bajtów jest większa niż maksymalny rozmiar VarBinary, czyli 8000 bajtów. W przypadku tablic bajtowych o rozmiarze większym niż 8000 bajtów jawnie ustaw wartość <xref:System.Data.SqlDbType> .|Liczby|Binarne|Nieprzetworzone|
|<xref:System.Char>| |Wnioskowanie typu <xref:System.Data.SqlDbType> from nie jest obsługiwane.|Char|Char|Byte|
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|
|<xref:System.DateTimeOffset>|DateTimeOffset|DateTimeOffset w SQL Server 2008. Wnioskowanie z klasy <xref:System.Data.SqlDbType> DateTimeOffset nie jest obsługiwane w wersjach SQL Server starszych niż SQL Server 2008.|||DateTime|
|<xref:System.Decimal>|Wartość dziesiętna|Wartość dziesiętna|Wartość dziesiętna|Liczbowe|Liczba|
|<xref:System.Double>|Double|Float|Double|Double|Double|
|<xref:System.Single>|Single|Rzeczywiste|Single|Rzeczywiste|Float|
|<xref:System.Guid>|Guid (identyfikator GUID)|UniqueIdentifier|Guid (identyfikator GUID)|UniqueIdentifier|Nieprzetworzone|
|<xref:System.Int16>|Int16|SmallInt|SmallInt|SmallInt|Int16|
|<xref:System.Int32>|Int32|int|int|int|Int32|
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Liczba|
|<xref:System.Object>|Obiekt|Wariant|Wariant|Wnioskowanie OdbcType z obiektu nie jest obsługiwane.|Obiekt blob|
|<xref:System.String>|String (ciąg)|NVarChar. Ta niejawna konwersja zakończy się niepowodzeniem, jeśli ciąg jest większy niż maksymalny rozmiar elementu NVarChar, który jest 4000 znaków. W przypadku ciągów o rozmiarze większym niż 4000 znaków jawnie ustaw wartość <xref:System.Data.SqlDbType> .|VarWChar|NVarChar|NVarChar|
|<xref:System.TimeSpan>|Godzina|Czas w SQL Server 2008. Wnioskowanie z elementu <xref:System.Data.SqlDbType> TimeSpan nie jest obsługiwane w wersjach SQL Server starszych niż SQL Server 2008.|Czas|Godzina|DateTime|
|<xref:System.UInt16>|UInt16|Wnioskowanie <xref:System.Data.SqlDbType> z UInt16 nie jest obsługiwane.|UnsignedSmallInt|int|UInt16|
|<xref:System.UInt32>|UInt32|Wnioskowanie z typu <xref:System.Data.SqlDbType> UInt32 nie jest obsługiwane.|UnsignedInt|BigInt|UInt32|
|<xref:System.UInt64>|UInt64|Wnioskowanie <xref:System.Data.SqlDbType> z UInt64 nie jest obsługiwane.|UnsignedBigInt|Liczbowe|Liczba|
||AnsiString|VarChar|VarChar|VarChar|VarChar|
||AnsiStringFixedLength|Char|Char|Char|Char|
||Waluta|Pieniądze|Waluta|Wnioskowanie `OdbcType` z `Currency` nie jest obsługiwane.|Liczba|
||Data|Data w SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> z daty od nie jest obsługiwane w wersjach SQL Server starszych niż SQL Server 2008.|DBDate|Data|DateTime|
||SByte|Wnioskowanie typu <xref:System.Data.SqlDbType> from nie jest obsługiwane.|TinyInt|Wywnioskowanie z niezgodnego elementu `OdbcType` nie jest obsługiwane.|SByte|
||StringFixedLength|NChar|WChar|NChar|NChar|
||Godzina|Czas w SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> z czasu od nie jest obsługiwane w wersjach SQL Server starszych niż SQL Server 2008.|Czas|Godzina|DateTime|
||VarNumeric|Wnioskowanie <xref:System.Data.SqlDbType> z VARNUMERIC nie jest obsługiwane.|VarNumeric|Wnioskowanie `OdbcType` z VARNUMERIC nie jest obsługiwane.|Liczba|
|typ zdefiniowany przez użytkownika (obiekt z<xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Obiekt lub ciąg, w zależności od dostawcy (SqlClient zawsze zwraca obiekt, ODBC zawsze zwraca ciąg, a dostawca danych zarządzanych OleDb może zobaczyć|SqlDbType. UDT <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> , jeśli jest obecny, w przeciwnym razie wariant|OleDbtype. VarWChar (Jeśli wartość jest równa null) w przeciwnym wypadku OleDbtype. Variant.|OdbcType. NVarChar|nieobsługiwane|

> [!NOTE]
> Konwersje z wartości dziesiętnych na inne typy są zawężanymi konwersjemi, które zaokrąglią wartość dziesiętną do najbliższej wartości całkowitej w kierunku zera. Jeśli wynik konwersji nie zostanie zaprezentowany w typie docelowym, <xref:System.OverflowException> zostanie zgłoszony.

> [!NOTE]
> W przypadku wysyłania wartości parametru o wartości null do serwera należy określić wartość <xref:System.DBNull> , a nie `null` ( `Nothing` w Visual Basic). Wartość null w systemie jest pustym obiektem, który nie ma wartości. <xref:System.DBNull>służy do reprezentowania wartości null. Aby uzyskać więcej informacji na temat wartości null bazy danych, zobacz [Obsługa wartości null](./sql/handling-null-values.md).

## <a name="deriving-parameter-information"></a>Wyprowadzanie informacji o parametrach

Parametry mogą również pochodzić z procedury składowanej przy użyciu `DbCommandBuilder` klasy. `SqlCommandBuilder` `OleDbCommandBuilder` Klasy i zapewniają metodę statyczną, `DeriveParameters` która automatycznie wypełnia kolekcję parametrów obiektu polecenia, który używa informacji o parametrach z procedury składowanej. Należy zauważyć, że `DeriveParameters` zastępuje wszystkie istniejące informacje o parametrach dla polecenia.

> [!NOTE]
> Wyprowadzanie informacji o parametrach powoduje spadek wydajności, ponieważ wymaga dodatkowej podróży do źródła danych w celu pobrania informacji. Jeśli informacje o parametrach są znane w czasie projektowania, można zwiększyć wydajność aplikacji przez ustawienie parametrów jawnie.

Aby uzyskać więcej informacji, zobacz [Generowanie poleceń z CommandBuilders](generating-commands-with-commandbuilders.md).

## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Używanie parametrów z SqlCommand i procedurą składowaną

Procedury składowane oferują wiele korzyści w aplikacjach opartych na danych. Korzystając z procedur składowanych, operacje bazy danych mogą być hermetyzowane w pojedynczym poleceniu, zoptymalizowane pod kątem najlepszej wydajności i ulepszone z dodatkowymi zabezpieczeniami. Chociaż procedura składowana może być wywoływana przez przekazanie nazwy procedury składowanej, a następnie argumentów parametrów jako instrukcji SQL, przy użyciu <xref:System.Data.Common.DbCommand.Parameters%2A> kolekcji obiektu ADO.NET, <xref:System.Data.Common.DbCommand> można dokładniej definiować parametry procedury składowanej oraz uzyskać dostęp do parametrów wyjściowych i zwracanych wartości.

> [!NOTE]
> Instrukcje sparametryzowane są wykonywane na serwerze przy użyciu `sp_executesql,` , który umożliwia ponowne użycie planu zapytania. Lokalne kursory lub zmienne w `sp_executesql` partii nie są widoczne dla partii, która wywołuje `sp_executesql` . Zmiany kontekstu bazy danych są ostatnie na końcu `sp_executesql` instrukcji. Aby uzyskać więcej informacji, zobacz [sp_executesql (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql).

W przypadku używania parametrów z <xref:System.Data.SqlClient.SqlCommand> do wykonywania SQL Server procedury składowanej, nazwy parametrów dodawane do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji muszą być zgodne z nazwami znaczników parametrów w procedurze składowanej. Dostawca danych .NET Framework dla SQL Server nie obsługuje symbolu zastępczego znaku zapytania (?) do przekazywania parametrów do instrukcji SQL lub procedury składowanej. Traktuje parametry w procedurze składowanej jako parametry nazwane i wyszukuje pasujące znaczniki parametrów. Na przykład `CustOrderHist` procedura składowana jest definiowana przy użyciu parametru o nazwie `@CustomerID` . Gdy kod wykonuje procedurę składowaną, musi również użyć parametru o nazwie `@CustomerID` .

```sql
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)
```

### <a name="example"></a>Przykład

W tym przykładzie pokazano, jak wywołać procedurę składowaną SQL Server w `Northwind` przykładowej bazie danych. Nazwa procedury składowanej jest `dbo.SalesByCategory` i ma parametr wejściowy o nazwie `@CategoryName` z typem danych `nvarchar(15)` . Kod tworzy nowy <xref:System.Data.SqlClient.SqlConnection> wewnątrz bloku using, aby połączenie zostało usunięte po zakończeniu procedury. <xref:System.Data.SqlClient.SqlCommand>Obiekty i <xref:System.Data.SqlClient.SqlParameter> są tworzone i ich właściwości są ustawione. A <xref:System.Data.SqlClient.SqlDataReader> wykonuje `SqlCommand` i zwraca zestaw wyników z procedury składowanej, wyświetlając dane wyjściowe w oknie konsoli.

> [!NOTE]
> Zamiast tworzyć obiekty i a `SqlCommand` `SqlParameter` następnie ustawiać właściwości w oddzielnych instrukcjach, zamiast tego można wybrać opcję użycia jednego z przeciążonych konstruktorów, aby ustawić wiele właściwości w jednej instrukcji.

[!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]

## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Używanie parametrów z OleDbCommand lub OdbcCommand

W przypadku używania parametrów z <xref:System.Data.OleDb.OleDbCommand> lub <xref:System.Data.Odbc.OdbcCommand> , kolejność parametrów dodanych do `Parameters` kolekcji musi być zgodna z kolejnością parametrów zdefiniowanych w procedurze składowanej. .NET Framework Dostawca danych dla OLE DB i .NET Framework Dostawca danych dla ODBC Traktuj parametry w procedurze składowanej jako symbole zastępcze i Zastosuj wartości parametrów w podanej kolejności. Ponadto parametry wartości zwracanej muszą być pierwszymi parametrami dodawanymi do `Parameters` kolekcji.

Dostawca danych .NET Framework dla OLE DB i .NET Framework Dostawca danych dla ODBC nie obsługują parametrów nazwanych do przekazywania parametrów do instrukcji SQL lub procedury składowanej. W takim przypadku należy użyć symbolu zastępczego znaku zapytania (?), jak w poniższym przykładzie.

```sql
SELECT * FROM Customers WHERE CustomerID = ?
```

W związku z tym kolejność, w jakiej `Parameter` obiekty są dodawane do `Parameters` kolekcji, musi być bezpośrednio zgodna z pozycją? Symbol zastępczy dla parametru.

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
