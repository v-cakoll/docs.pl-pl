---
title: Daty i godziny
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 2130c79ba79ce7e327a2a1b3adccd92e52153d85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="date-and-time-data"></a>Daty i godziny
SQL Server 2008 wprowadzono nowe typy danych obsługi informacji o datę i godzinę. Nowe typy danych obejmują osobne typy daty i godziny i typy danych rozszerzonych z większego zakresu, dokładność i świadomości strefy czasowej. Począwszy od wersji .NET Framework 3.5 z dodatkiem Service Pack (SP1), .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) zapewnia pełną obsługę wszystkich nowych funkcji aparatu bazy danych programu SQL Server 2008. .NET Framework 3.5 z dodatkiem SP1 należy zainstalować (lub nowsza) do użycia z SqlClient te nowe funkcje.  
  
 Wersje programu SQL Server starszych niż SQL Server 2008 ma tylko dwa typy danych do pracy z wartości daty i godziny: `datetime` i `smalldatetime`. Oba typy danych zawierają zarówno wartość daty i czasu wartości, która utrudnia współpracować tylko datę lub tylko wartości czasu. Ponadto te typy danych obsługują tylko daty, które występują po wprowadzeniu kalendarza gregoriańskiego w Anglii w 1753. Innym ograniczeniem jest to, że te starsze typy danych nie są strefy czasowej wiedzieć, co utrudnia do pracy z danymi, które pochodzą z wielu strefach czasowych.  
  
 Pełną dokumentację dla typów danych programu SQL Server jest dostępny w dokumentacji SQL Server — książki Online. W poniższej tabeli wymieniono klasy podstawowej tematy dotyczące określonej wersji dla danych daty i godziny.  
  
 **SQL Server — książki Online**  
  
1.  [Przy użyciu daty i godziny](http://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Typy danych wprowadzonych w programie SQL Server 2008 daty/godziny  
 W poniższej tabeli opisano nowe typy danych daty i godziny.  
  
|Typ danych programu SQL Server|Opis|  
|--------------------------|-----------------|  
|`date`|`date` — Typ danych ma zakres 1 stycznia 01 do 31 grudnia 9999, z dokładnością do 1 dzień. Wartość domyślna to 1 stycznia 1900. Rozmiar magazynu jest 3 bajtów.|  
|`time`|`time` — Typ danych przechowuje wartości czasu, oparte na zegarze 24-godzinnym. `time` Zakres 00:00:00.0000000 za pośrednictwem 23:59:59.9999999 z dokładnością 100 nanosekundach ma typ danych. Wartość domyślna to 00:00:00.0000000 (północ). `time` — Typ danych obsługuje zdefiniowane przez użytkownika dokładność ułamkowych części sekundy, i rozmiar magazynu zależą od 3 do 6 bajtów, oparte na dokładność określona.|  
|`datetime2`|`datetime2` — Typ danych łączy zakresu i dokładność `date` i `time` typy danych do jednego typu danych.<br /><br /> Domyślne wartości i formaty literału ciągu, są takie same jak te zdefiniowane `date` i `time` typy danych.|  
|`datetimeoffset`|`datetimeoffset` Typ danych ma wszystkich funkcji `datetime2` z przesunięciem dodatkową strefę czasową. Przesunięcie strefy czasowej jest reprezentowany jako [+&#124;—] hh: mm. HH to 2 cyfry od 00 do 14 reprezentować liczbę godzin w przesunięcia strefy czasowej. MM to 2 cyfry od 00 do 59 reprezentować liczbę dodatkowych minut w przesunięcia strefy czasowej. Do 100 nanosekundach są obsługiwane formaty czasu. Obowiązkowe + lub - znak wskazuje, czy przesunięcie strefy czasowej jest dodane lub usunięte od czasu UTC (uniwersalny czas koordynować lub czas uniwersalny Greenwich) można uzyskać czasu lokalnego.|  
  
> [!NOTE]
>  Aby uzyskać więcej informacji o korzystaniu z `Type System Version` — słowo kluczowe, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Format daty i kolejność daty  
 Jak program SQL Server, analizuje wartości daty i godziny zależy nie tylko od wersji systemu i wersji serwera, ale także z serwera do domyślnych ustawień języka i formatu. Ciąg daty, która działa w przypadku formatów daty z jednym języku mogą być nierozpoznawalną, jeśli zapytanie jest wykonywane za pomocą połączenia używającej innego języka i formatu daty ustawienie.  
  
 Instrukcja SET LANGUAGE języka Transact-SQL niejawnie ustawia DATEFORMAT, który określa kolejność części daty. Instrukcja USTAWIĆ DATEFORMAT języka Transact-SQL połączenia służy do odróżniania przez zamawiania części daty w kolejności MDY, DMY, YMD, YDM, MYD lub DYM wartości daty.  
  
 Jeśli nie określisz DATEFORMAT dowolnego połączenia, program SQL Server używa domyślny język skojarzone z połączeniem. Na przykład ciąg daty 03-01 "-02" może zostać zinterpretowany jako MDY (2 stycznia 2003) na serwerze z ustawieniem języka z językiem angielskim i jako DMY (1 lutego 2003) na serwerze z ustawieniem języka angielskiego. Rok jest określany przy użyciu reguły rok odcięcia programu SQL Server, która definiuje Data progowa przypisywania wartości wieku. Aby uzyskać więcej informacji, zobacz [opcję cyfrę dwuletnie odcięcia](http://go.microsoft.com/fwlink/?LinkId=120473) w dokumentacji SQL Server — książki Online.  
  
> [!NOTE]
>  Format daty YDM nie jest obsługiwana podczas konwersji z formatu ciągu do `date`, `time`, `datetime2`, lub `datetimeoffset`.  
  
 Aby uzyskać więcej informacji na temat interpretowanie danych daty i godziny w programie SQL Server, zobacz [przy użyciu daty i godziny](http://go.microsoft.com/fwlink/?LinkID=98361) w dokumentacji SQL Server 2008 — książki Online.  
  
## <a name="datetime-data-types-and-parameters"></a>Data/Godzina danych typów i parametry  
 Dodano następujące wyliczenia <xref:System.Data.SqlDbType> do obsługi nowych typów danych daty i godziny.  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  

Można określić typu danych <xref:System.Data.SqlClient.SqlParameter> przy użyciu jednej z poprzednim <xref:System.Data.SqlDbType> wyliczenia. 

> [!NOTE]
> Nie można ustawić `DbType` właściwość `SqlParameter` do `SqlDbType.Date`.

 Można również określić typ <xref:System.Data.SqlClient.SqlParameter> objęty przez ustawienie <xref:System.Data.SqlClient.SqlParameter.DbType%2A> właściwość `SqlParameter` obiektu do określonego <xref:System.Data.DbType> wartości wyliczenia. Dodano następujące wartości wyliczenia <xref:System.Data.DbType> do obsługi `datetime2` i `datetimeoffset` typy danych:  
  
-   DbType.DateTime2  
  
-   DbType.DateTimeOffset  
  
 Te nowe wyliczenia uzupełnić `Date`, `Time`, i `DateTime` wyliczenia, które istniały w starszych wersjach programu .NET Framework.  
  
 Typ dostawcy danych .NET Framework parametr obiektu jest wywnioskowany na podstawie typu .NET Framework wartości obiektu parameter lub z `DbType` obiektu parameter. Żadna nowa <xref:System.Data.SqlTypes> typy danych zostały wprowadzone do obsługi nowych typów danych daty i godziny. W poniższej tabeli opisano mapowania między datą programu SQL Server 2008 i typów danych i typów CLR.  
  
|Typ danych programu SQL Server|Typ programu .NET Framework|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Data|System.DateTime|Data|Data|  
|czas|System.TimeSpan|Godzina|Godzina|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|Datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DataGodzina|DataGodzina|  
|smalldatetime|System.DateTime|DataGodzina|DataGodzina|  
  
### <a name="sqlparameter-properties"></a>Właściwości SqlParameter  
 W poniższej tabeli opisano `SqlParameter` właściwości, które mają zastosowanie do typów danych daty i godziny.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Pobiera lub ustawia, czy wartość jest wartością null. Wartość null parametru są wysyłane do serwera, należy określić <xref:System.DBNull>, a nie `null` (`Nothing` w języku Visual Basic). Aby uzyskać więcej informacji o wartości null bazy danych, zobacz [Obsługa wartości zerowych](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Pobiera lub ustawia maksymalną liczbę cyfr używana do reprezentowania wartości. To ustawienie jest ignorowane w przypadku typów danych daty i godziny.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Pobiera lub ustawia liczbę miejsc dziesiętnych, do których został rozwiązany dla części wartość `Time`, `DateTime2`, i `DateTimeOffset`. Wartość domyślna to 0, co oznacza, że rzeczywista skali jest wywnioskowany na podstawie wartości i wysłane do serwera.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignorowane dla typów danych daty i godziny.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Pobiera lub ustawia wartość parametru.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Pobiera lub ustawia wartość parametru.|  
  
> [!NOTE]
>  Wartości czasu jest większa niż zero lub większa niż 24 godziny zgłosi <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Tworzenie parametrów  
 Można utworzyć <xref:System.Data.SqlClient.SqlParameter> obiektu za pomocą jego konstruktora lub dodając go do <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji, wywołując `Add` metody <xref:System.Data.SqlClient.SqlParameterCollection>. `Add` Metoda będzie przyjmować jako danych wejściowych w argumentach konstruktora lub istniejący obiekt parametru.  
  
 Następnej części tego tematu zawierają przykłady sposobu określania parametrów daty i godziny. Dodatkowe przykłady pracy z parametrów, zobacz [konfigurowania parametrów i typ danych parametru](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) i [parametry element DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
### <a name="date-example"></a>Przykład daty  
 Poniższy fragment kodu przedstawia sposób określić `date` parametru.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a>Przykład czasu  
 Poniższy fragment kodu przedstawia sposób określić `time` parametru.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Przykład Datetime2  
 Poniższy fragment kodu przedstawia sposób określić `datetime2` parametru z częściami datę i godzinę.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>Przykład DateTimeOffSet  
 Poniższy fragment kodu przedstawia sposób określić `DateTimeOffSet` parametru datę, godzinę i przesunięcie strefy czasowej 0.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
 Może też podawać parametrów przy użyciu `AddWithValue` metody <xref:System.Data.SqlClient.SqlCommand>, jak pokazano w następującego fragmentu kodu. Jednak `AddWithValue` — metoda nie umożliwiają określenie <xref:System.Data.SqlClient.SqlParameter.DbType%2A> lub <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> dla parametru.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date` Parametru może mapować na `date`, `datetime`, lub `datetime2` typu danych na serwerze. Podczas pracy z nowym `datetime` typy danych, musisz jawnie ustawić parametr <xref:System.Data.SqlDbType> właściwości na typ danych wystąpienia. Przy użyciu <xref:System.Data.SqlDbType.Variant> lub niejawnie podawania wartości parametrów może spowodować problemy z zgodności z poprzednimi wersjami `datetime` i `smalldatetime` typy danych.  
  
 W poniższej tabeli przedstawiono, które `SqlDbTypes` są wywnioskować na podstawie typy CLR:  
  
|Typ CLR|Wywnioskowane SqlDbType|  
|--------------|------------------------|  
|DataGodzina|SqlDbType.DateTime|  
|Zakres czasu|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Podczas pobierania daty i godziny  
 W poniższej tabeli opisano metody, które są używane do pobierania wartości daty i godziny programu SQL Server 2008.  
  
|SqlClient — metoda|Opis|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Pobiera wartość określonej kolumny jako <xref:System.DateTime> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Pobiera wartość określonej kolumny jako <xref:System.DateTimeOffset> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Zwraca typ, który jest typem podstawowym specyficznych dla dostawcy dla pola. Zwraca te same typy jako `GetFieldType` dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Pobiera wartość określonej kolumny. Zwraca te same typy jako `GetValue` dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Pobiera wartości w określonej tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Pobiera wartość kolumny jako <xref:System.Data.SqlTypes.SqlString>. <xref:System.InvalidCastException> Występuje, gdy dane nie może być wyrażona jako `SqlString`.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Pobiera dane w kolumnie jako jego domyślny `SqlDbType`. Zwraca te same typy jako `GetValue` dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Pobiera wartości w określonej tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Pobiera wartość kolumny jako ciąg, jeśli ustawiono typ wersji systemu do wersji SQL Server 2005. <xref:System.InvalidCastException> Występuje, gdy dane nie może być wyrażona jako ciąg.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Pobiera wartość określonej kolumny jako <xref:System.TimeSpan> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Pobiera wartość określonej kolumny jako jego podstawowy typ CLR.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Pobiera wartości w kolumnie w tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Zwraca <xref:System.Data.DataTable> opisujący metadanych zestawu wyników.|  
  
> [!NOTE]
>  Nowa data i godzina `SqlDbTypes` nie są obsługiwane dla kodu, który jest wykonywany w trakcie w programie SQL Server. Wystąpił wyjątek zostanie wygenerowany, jeśli jeden z tych typów są przekazywane do serwera.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Określanie wartości daty i godziny jako literały  
 Można określić typy danych daty i godziny przy użyciu różnych formatach inny ciąg literału, programem SQL Server, następnie oblicza w czasie wykonywania, ich konwersji do struktur wewnętrznych daty/godziny. SQL Server rozpoznaje danych daty i godziny, która jest ujęta w znaki apostrofu ('). W poniższych przykładach pokazano niektóre formaty:  
  
-   Formatuje alfabetyczne Data, takich jak `'October 15, 2006'`.  
  
-   Formatuje liczbowego Data, takich jak `'10/15/2006'`.  
  
-   Nieoddzielone formaty ciągu, takich jak `'20061015'`, który zostanie zinterpretowany jako 15 października 2006 korzystania z formatu daty standardowe ISO.  
  
> [!NOTE]
>  Pełną dokumentację można znaleźć wszystkie formaty literału ciągu i inne funkcje typów danych daty i godziny w dokumentacji SQL Server — książki Online.  
  
 Wartości czasu jest większa niż zero lub większa niż 24 godziny zgłosi <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Zasoby programu SQL Server 2008 — książki Online  
 Aby uzyskać więcej informacji na temat pracy z wartości daty i godziny w programie SQL Server 2008 zobacz następujące zasoby w programie SQL Server 2008 — książki Online.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Daty i godziny typy i funkcje (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98360)|Zawiera omówienie Data języka Transact-SQL i typów danych i funkcji.|  
|[Przy użyciu daty i godziny](http://go.microsoft.com/fwlink/?LinkId=98361)|Informacje na temat typów danych daty i godziny i funkcje i przykłady ich użycia.|  
|[Typy danych (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98362)|Zawiera opis typów danych w programie SQL Server 2008.|  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Typy danych programu SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
