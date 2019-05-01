---
title: Dane daty i godziny
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 80b7df4922e1398c7290e769e53627a1d46ebc83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877750"
---
# <a name="date-and-time-data"></a>Dane daty i godziny
Program SQL Server 2008 wprowadzono nowe typy danych do obsługi informacji daty i godziny. Nowe typy danych to oddzielne typy dla daty i godziny i typy danych rozszerzonej z większego zakresu, dokładność i świadomości strefy czasowej. Począwszy od wersji programu .NET Framework 3.5 z dodatkiem Service Pack (SP1), .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) zapewnia pełną obsługę wszystkie nowe funkcje aparatu bazy danych programu SQL Server 2008. Należy zainstalować .NET Framework 3.5 z dodatkiem SP1 (lub nowszym) te nowe funkcje za pomocą SqlClient.  
  
 Wersje programu SQL Server starszych niż SQL Server 2008 ma tylko dwa typy danych do pracy z wartości daty i godziny: `datetime` i `smalldatetime`. Oba typy danych zawierają wartość daty i wartości czasu, która sprawia, że trudno pracować tylko datę lub tylko wartości czasu. Ponadto te typy danych obsługują tylko daty, które występują po wprowadzeniu kalendarza gregoriańskiego w Anglii w 1753. Innym ograniczeniem jest to, że te starsze typy danych nie są strefy czasowej wiedzieć, co czyni go trudno pracować z danymi, które pochodzą z wielu stref czasowych.  
  
 Pełną dokumentację dla typów danych programu SQL Server jest dostępny w dokumentacji SQL Server — książki Online. Poniższa tabela zawiera listę tematów klasy podstawowej określonej wersji dla danych daty i godziny.  
  
 **SQL Server Books Online**  
  
1. [Za pomocą dane daty i godziny](https://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Typy danych, które wprowadzono w programie SQL Server 2008 daty/godziny  
 W poniższej tabeli opisano nowe typy danych daty i godziny.  
  
|Typ danych programu SQL Server|Opis|  
|--------------------------|-----------------|  
|`date`|`date` Typ danych ma zakres od 1 stycznia, 01 do 31 grudnia 9999 r z dokładnością do 1 dzień. Wartość domyślna to 1 stycznia 1900. Rozmiar magazynu jest 3 bajtów.|  
|`time`|`time` — Typ danych są przechowywane wyłącznie wartości typu time na podstawie zegara 24-godzinnym. `time` — Typ danych oferuje szeroką gamę 00:00:00.0000000 za pośrednictwem 23:59:59.9999999 z dokładnością 100 nanosekund. Wartość domyślna to 00:00:00.0000000 (północ). `time` — Typ danych obsługuje zdefiniowanych przez użytkownika dokładność ułamkowych części sekundy, a rozmiar magazynu różni się od 3 do 6 bajtów, oparte na dokładność określona.|  
|`datetime2`|`datetime2` — Typ danych łączy zakres i dokładność `date` i `time` typy danych do jednego typu danych.<br /><br /> Wartości domyślne i formaty literału ciągu są takie same, jak te określone w `date` i `time` typy danych.|  
|`datetimeoffset`|`datetimeoffset` — Typ danych zawiera wszystkie funkcje wersji `datetime2` z przesunięciem dodatkowe strefy czasowej. Przesunięcie strefy czasowej jest reprezentowany jako [+&#124;-] hh: mm. HH oznacza cyfr 2 z zakresu od 00 do 14, które reprezentują liczbę godzin w przesunięcia strefy czasowej. MM jest cyfr 2 z zakresu od 00 do 59 reprezentujące liczba dodatkowe minuty w przesunięcia strefy czasowej. Formaty czasu są obsługiwane na 100 nanosekund. Obowiązkowy + lub - znak wskazuje, czy przesunięcie strefy czasowej dodania lub odjęcia od czasu UTC (koordynować uniwersalny czas lub czas uniwersalny Greenwich) można uzyskać czasu lokalnego.|  
  
> [!NOTE]
>  Aby uzyskać więcej informacji o korzystaniu z `Type System Version` — słowo kluczowe, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Format daty i kolejność dat  
 Jak program SQL Server, analizuje wartości daty i godziny zależy nie tylko w wersji systemu i wersją serwera, ale na ustawieniach domyślnych serwer język i format. Ciąg daty, które działa w przypadku formatów daty z jednym języku mogą być nierozpoznawalną, jeśli zapytanie jest wykonywane za pomocą połączenia używającej inny język i ustawienia format daty.  
  
 Wykonywanie instrukcji języka Transact-SQL z zestawu niejawnie ustawia DATEFORMAT, która określa kolejność części daty. Instrukcję Ustaw DATEFORMAT Transact-SQL w połączeniu służy do odróżniania wartości daty, zamawiania części daty w kolejności MDY, DMY, YMD YDM, MYD lub DYM.  
  
 Jeśli nie określisz żadnych DATEFORMAT połączenia programu SQL Server używa domyślny język skojarzonych z tym połączeniem. Na przykład ciąg daty "01/02/03" może być interpretowany jako MDY (2 stycznia 2003) na serwerze z ustawieniem języka angielskiego Stanów Zjednoczonych, a jako DMY (1 lutego 2003) na serwerze z ustawieniem języka angielskiego. Rok jest określana za pomocą reguły rok odcięcia programu SQL Server, która definiuje dacie do przypisywania wartości wieku. Aby uzyskać więcej informacji, zobacz [opcji dwucyfrowe odcięcie roku](https://go.microsoft.com/fwlink/?LinkId=120473) w dokumentacji SQL Server — książki Online.  
  
> [!NOTE]
>  Format daty YDM nie jest obsługiwana podczas konwersji z formatu ciągu, aby `date`, `time`, `datetime2`, lub `datetimeoffset`.  
  
 Aby uzyskać więcej informacji na temat interpretowanie danych daty i godziny w programie SQL Server, zobacz [dane przy użyciu daty i godziny](https://go.microsoft.com/fwlink/?LinkID=98361) w dokumentacji programu SQL Server 2008 — książki Online.  
  
## <a name="datetime-data-types-and-parameters"></a>Dane daty/godziny typów i parametry  
 Dodano następujące wyliczenia <xref:System.Data.SqlDbType> do obsługi nowych typów danych daty i godziny.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Można określić typu danych <xref:System.Data.SqlClient.SqlParameter> przy użyciu jednej z poprzednim <xref:System.Data.SqlDbType> wyliczenia. 

> [!NOTE]
> Nie można ustawić `DbType` właściwość `SqlParameter` do `SqlDbType.Date`.

 Można również określić typ <xref:System.Data.SqlClient.SqlParameter> objęty przez ustawienie <xref:System.Data.SqlClient.SqlParameter.DbType%2A> właściwość `SqlParameter` obiektu do określonego <xref:System.Data.DbType> wartość wyliczenia. Dodano następujące wartości wyliczenia <xref:System.Data.DbType> do obsługi `datetime2` i `datetimeoffset` typów danych:  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
 Te nowe wyliczenia uzupełniają `Date`, `Time`, i `DateTime` wyliczenia, które istniały w starszych wersjach programu .NET Framework.  
  
 Typ dostawcy danych .NET Framework obiektu parametru jest wnioskowany z typu .NET Framework wartości obiektu parametrów lub z `DbType` parametr obiektu. Brak opcji new <xref:System.Data.SqlTypes> typy danych zostały wprowadzone do obsługi nowych typów danych daty i godziny. W poniższej tabeli opisano mapowania między datą programu SQL Server 2008 i typy danych czasu i typy danych CLR.  
  
|Typ danych programu SQL Server|Typ programu .NET Framework|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Data|System.DateTime|Data|Data|  
|czas|System.TimeSpan|Godzina|Godzina|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|Datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DataGodzina|DataGodzina|  
|smalldatetime|System.DateTime|DataGodzina|DataGodzina|  
  
### <a name="sqlparameter-properties"></a>Parametr SqlParameter właściwości  
 W poniższej tabeli opisano `SqlParameter` właściwości, które są istotne dla typów danych daty i godziny.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Pobiera lub ustawia informację, czy dana wartość jest wartością null. Wartość parametru o wartości null jest wysyłany do serwera, należy określić <xref:System.DBNull>, zamiast `null` (`Nothing` w języku Visual Basic). Aby uzyskać więcej informacji o wartości null w bazie danych, zobacz [Obsługa wartości zerowych](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Pobiera lub ustawia maksymalną liczbę cyfr używana do reprezentowania wartości. To ustawienie jest ignorowane dla typów danych daty i godziny.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Pobiera lub ustawia liczbę miejsc dziesiętnych, do których część godzinowa wartość nie zostanie rozwiązany dla `Time`, `DateTime2`, i `DateTimeOffset`. Wartość domyślna to 0, co oznacza, że rzeczywiste skalowanie jest wnioskowany z wartości i wysyłane do serwera.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignorowane dla typów danych daty i godziny.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Pobiera lub ustawia wartość tego parametru.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Pobiera lub ustawia wartość tego parametru.|  
  
> [!NOTE]
>  Wartości czasu, w których wartość jest mniejsza od zera i mniejszy niż 24 godziny będzie zgłaszać wyjątek <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Tworzenie parametrów  
 Możesz utworzyć <xref:System.Data.SqlClient.SqlParameter> obiektu za pomocą jej konstruktora lub przez dodanie jej do <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji przez wywołanie metody `Add` metody <xref:System.Data.SqlClient.SqlParameterCollection>. `Add` Metoda zajmie się jako dane wejściowe w argumentach konstruktora lub istniejący obiekt parametru.  
  
 Następnych sekcjach tego tematu zawierają przykłady sposobu określania parametrów daty i godziny. Aby uzyskać dodatkowe przykłady pracy z parametrami, zobacz [konfigurowania parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) i [parametry elementu DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
### <a name="date-example"></a>Przykład daty  
 Poniższy fragment kodu pokazuje, jak określić `date` parametru.  
  
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
 Poniższy fragment kodu pokazuje, jak określić `time` parametru.  
  
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
 Poniższy fragment kodu pokazuje, jak określić `datetime2` parametrem części daty i godziny.  
  
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
 Poniższy fragment kodu pokazuje, jak określić `DateTimeOffSet` parametrem datę, godzinę i przesunięcia strefy czasowej 0.  
  
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
 Można też podać parametry przy użyciu `AddWithValue` metody <xref:System.Data.SqlClient.SqlCommand>, jak pokazano na następujący fragment kodu. Jednak `AddWithValue` metody nie pozwalają na określenie <xref:System.Data.SqlClient.SqlParameter.DbType%2A> lub <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> dla parametru.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date` Parametru można zamapować na `date`, `datetime`, lub `datetime2` typu danych na serwerze. Podczas pracy z nowym `datetime` typy danych, musisz jawnie ustawić wartości parametru <xref:System.Data.SqlDbType> właściwość na typ danych wystąpienia. Za pomocą <xref:System.Data.SqlDbType.Variant> lub niejawnie, podając wartości parametru może spowodować problemy z zgodności z poprzednimi wersjami `datetime` i `smalldatetime` typy danych.  
  
 W poniższej tabeli przedstawiono, które `SqlDbTypes` są dedukowane z jakie typy CLR:  
  
|Typ CLR|Wywnioskowane SqlDbType|  
|--------------|------------------------|  
|DataGodzina|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Trwa pobieranie dane daty i godziny  
 W poniższej tabeli opisano metody, które są używane do pobierania wartości daty i godziny dla programu SQL Server 2008.  
  
|Metoda SqlClient|Opis|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Pobiera wartość określonej kolumny jako <xref:System.DateTime> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Pobiera wartość określonej kolumny jako <xref:System.DateTimeOffset> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Zwraca typ, który jest typem podstawowym właściwe dla dostawcy dla pola. Zwraca te same typy jako `GetFieldType` dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Pobiera wartość określonej kolumny. Zwraca te same typy jako `GetValue` dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Pobiera wartości w określonej tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Pobiera wartość kolumny jako <xref:System.Data.SqlTypes.SqlString>. <xref:System.InvalidCastException> Występuje, gdy dane nie mogą być wyrażone jako `SqlString`.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Pobiera dane w kolumnie jako jego domyślny `SqlDbType`. Zwraca te same typy jako `GetValue` dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Pobiera wartości w określonej tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Pobiera wartość kolumny jako ciąg, jeśli wersja systemu typu jest ustawiona na program SQL Server 2005. <xref:System.InvalidCastException> Występuje, gdy dane nie mogą być wyrażone jako ciąg.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Pobiera wartość określonej kolumny jako <xref:System.TimeSpan> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Pobiera wartość określonej kolumny jako jego podstawowy typ środowiska CLR.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Pobiera wartości kolumn w tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Zwraca <xref:System.Data.DataTable> opisujący metadanych zestawu wyników.|  
  
> [!NOTE]
>  Nowa data i godzina `SqlDbTypes` nie są obsługiwane dla kodu, który jest wykonywany w trakcie w programie SQL Server. Wyjątek zostanie wygenerowany, jeśli jeden z tych typów jest przekazywany do serwera.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Określanie wartości daty i godziny jako literały  
 Można określić typów danych daty i godziny przy użyciu różnych formatów inny ciąg literału, programem SQL Server, następnie obliczane w czasie wykonywania, konwertowania go na potrzeby struktur wewnętrznych daty/godziny. Program SQL Server rozpoznaje dane daty i godziny, który jest ujęty w znaki pojedynczego cudzysłowu ('). W poniższych przykładach pokazano niektóre formaty:  
  
- Alfabetyczne Data formatów, takich jak `'October 15, 2006'`.  
  
- Takich jak formaty liczbowe data `'10/15/2006'`.  
  
- Nieoddzielone formaty ciągów, takich jak `'20061015'`, który może być interpretowany jako 15 października 2006, jeśli jest używany format standardowy format daty ISO.  
  
> [!NOTE]
>  Pełną dokumentację można znaleźć wszystkie formaty ciągu literału i innych funkcji, typów danych daty i godziny w dokumentacji SQL Server — książki Online.  
  
 Wartości czasu, w których wartość jest mniejsza od zera i mniejszy niż 24 godziny będzie zgłaszać wyjątek <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Zasoby programu SQL Server 2008 — książki Online  
 Aby uzyskać więcej informacji na temat pracy z wartości daty i godziny w programie SQL Server 2008 zobacz następujące zasoby w programie SQL Server 2008 — książki Online.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Dane daty i godziny typy i funkcje (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Zawiera omówienie Data języka Transact-SQL i typy danych czasu i funkcji.|  
|[Za pomocą dane daty i godziny](https://go.microsoft.com/fwlink/?LinkId=98361)|Informacje na temat typów danych daty i godziny oraz funkcji i przykłady ich użycia.|  
|[Typy danych (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|Zawiera opis typów danych w programie SQL Server 2008.|  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Typy danych programu SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
