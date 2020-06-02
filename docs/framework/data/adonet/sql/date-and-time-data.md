---
title: Dane daty i godziny
description: Dowiedz się więcej o typach danych do obsługi informacji o dacie i godzinie w .NET Framework Dostawca danych dla SQL Server.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 9345e995dcb1179e7d0a86f62737f9fda5889f42
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286497"
---
# <a name="date-and-time-data"></a>Dane daty i godziny
SQL Server 2008 wprowadza nowe typy danych do obsługi informacji o dacie i godzinie. Nowe typy danych obejmują oddzielne typy dat i godzin oraz rozszerzone typy danych o większej dokładności, precyzji i świadomości strefy czasowej. Począwszy od .NET Framework w wersji 3,5 Service Pack (SP) 1, .NET Framework Dostawca danych dla SQL Server ( <xref:System.Data.SqlClient> ) zapewnia pełną obsługę wszystkich nowych funkcji aparatu bazy danych SQL Server 2008. Aby korzystać z nowych funkcji w programie SqlClient, należy zainstalować .NET Framework 3,5 SP1 (lub nowsze).  
  
 Wersje SQL Server starszej niż SQL Server 2008 mają tylko dwa typy danych do pracy z wartościami daty i godziny: `datetime` i `smalldatetime` . Oba te typy danych zawierają zarówno wartość daty, jak i wartość czasu, co utrudnia działanie tylko wartości daty i godziny. Ponadto te typy danych obsługują tylko daty, które wystąpiły po wprowadzeniu kalendarza gregoriańskiego w Anglii w 1753. Inne ograniczenie polega na tym, że te starsze typy danych nie są świadome strefy czasowej, co utrudnia pracy z danymi, które pochodzą z wielu stref czasowych.  
  
 Kompletna dokumentacja typów danych SQL Server jest dostępna w SQL Server Books Online. W poniższej tabeli przedstawiono tematy dotyczące poszczególnych wersji dla danych daty i godziny.  
  
 **SQL Server documentation (Dokumentacja programu SQL Server)**  
  
1. [Korzystanie z danych daty i godziny](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Typy danych daty/godziny wprowadzone w SQL Server 2008  
 W poniższej tabeli opisano nowe typy danych daty i godziny.  
  
|Typ danych SQL Server|Opis|  
|--------------------------|-----------------|  
|`date`|`date`Typ danych ma zakres od 1 stycznia do 31 grudnia 9999 z dokładnością wynoszącą 1 dzień. Wartość domyślna to 1 stycznia 1900. Rozmiar magazynu wynosi 3 bajty.|  
|`time`|`time`Typ danych przechowuje tylko wartości czasu w oparciu o zegar 24-godzinny. `time`Typ danych ma zakres 00:00:00.0000000 do 23:59:59.9999999 z dokładnością do 100 nanosekund. Wartość domyślna to 00:00:00.0000000 (północ). `time`Typ danych obsługuje zdefiniowaną przez użytkownika precyzję dziesiętną, a rozmiar magazynu różni się od 3 do 6 bajtów na podstawie określonej precyzji.|  
|`datetime2`|`datetime2`Typ danych łączy zakres i precyzję `date` `time` typów danych i w jeden typ danych.<br /><br /> Wartości domyślne i formaty literałów ciągów są takie same jak te zdefiniowane w `date` typach i `time` .|  
|`datetimeoffset`|`datetimeoffset`Typ danych zawiera wszystkie funkcje z `datetime2` dodatkowym przesunięciem strefy czasowej. Przesunięcie strefy czasowej jest reprezentowane jako [+&#124;-] HH: MM. HH to 2 cyfry od 00 do 14, które reprezentują liczbę godzin w przesunięciu strefy czasowej. MM to 2 cyfry od 00 do 59, które reprezentują liczbę dodatkowych minut w przesunięciu strefy czasowej. Formaty czasu są obsługiwane w 100 nanosekundach. Obowiązkowe + lub-znak wskazuje, czy przesunięcie strefy czasowej jest dodawane lub odejmowane od czasu UTC (uniwersalna Współrzędna czasu Greenwich lub czasu GMT), aby uzyskać czas lokalny.|  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat używania `Type System Version` słowa kluczowego, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> .  
  
## <a name="date-format-and-date-order"></a>Format daty i kolejność dat  
 Sposób, w jaki SQL Server analizuje wartości daty i godziny, zależy nie tylko od wersji systemu typu i wersji serwera, ale również w domyślnym języku i ustawieniach formatowania serwera. Ciąg daty, który działa w przypadku formatów daty jednego języka może być nierozpoznawalny, jeśli zapytanie jest wykonywane przez połączenie, które używa innego ustawienia język i format daty.  
  
 Instrukcja języka Transact-SQL SET niejawnie ustawia DATEFORMAT, który określa kolejność części daty. Można użyć instrukcji DATEFORMAT języka Transact-SQL w połączeniu, aby odróżnić wartości daty przez porządkowanie części daty w MDR, DMY, YMD, YDM, MYD lub DYM Order.  
  
 Jeśli nie określisz żadnych DATEFORMAT dla połączenia, SQL Server używa języka domyślnego skojarzonego z połączeniem. Na przykład ciąg daty "01/02/03" będzie interpretowany jako MDR (2 stycznia 2003) na serwerze z ustawieniem języka Stany Zjednoczone angielski i jako DMY (1 lutego 2003) na serwerze z ustawieniem języka brytyjskiego alfabetu angielskiego. Rok jest określany za pomocą reguły odcięcia roku SQL Server, która definiuje datę końcową przypisywania wartości wieku. Aby uzyskać więcej informacji, zobacz [dwubajtowa opcja odcięcia roku](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).  
  
> [!NOTE]
> Format daty YDM nie jest obsługiwany podczas konwersji z formatu ciągu na,, `date` `time` `datetime2` , lub `datetimeoffset` .  
  
 Aby uzyskać więcej informacji o tym, jak SQL Server interpretuje dane daty i godziny, zobacz [Korzystanie z danych daty i godziny](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).  
  
## <a name="datetime-data-types-and-parameters"></a>Typy danych daty/godziny i parametry  
 Następujące wyliczenia zostały dodane do programu <xref:System.Data.SqlDbType> w celu obsługi nowych typów danych daty i godziny.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Możesz określić typ danych z przy <xref:System.Data.SqlClient.SqlParameter> użyciu jednego z wcześniejszych <xref:System.Data.SqlDbType> wyliczeń.

> [!NOTE]
> Nie można ustawić `DbType` właściwości `SqlParameter` na `SqlDbType.Date` .

 Można również określić typ <xref:System.Data.SqlClient.SqlParameter> ogólny, ustawiając <xref:System.Data.SqlClient.SqlParameter.DbType%2A> Właściwość `SqlParameter` obiektu na określoną <xref:System.Data.DbType> wartość wyliczenia. Następujące wartości wyliczenia zostały dodane do programu <xref:System.Data.DbType> w celu obsługi `datetime2` `datetimeoffset` typów danych i:  
  
- DbType. DateTime2  
  
- DbType. DateTimeOffset  
  
 Te nowe wyliczenia uzupełniają `Date` wyliczenia, `Time` i, `DateTime` które istniały we wcześniejszych wersjach .NET Framework.  
  
 Typ dostawcy danych .NET Framework obiektu parametru jest wywnioskowany na podstawie typu .NET Framework wartości obiektu parametru lub z `DbType` obiektu Parameter. Nie <xref:System.Data.SqlTypes> wprowadzono nowych typów danych w celu obsługi nowych typów danych daty i godziny. W poniższej tabeli opisano mapowania między typami danych daty i godziny SQL Server 2008 oraz typami danych CLR.  
  
|Typ danych SQL Server|Typ programu .NET Framework|System. Data. SqlDbType|System. Data. DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|data|System. DateTime|Data|Data|  
|time|System. TimeSpan|Godzina|Godzina|  
|datetime2|System. DateTime|DateTime2|DateTime2|  
|datetimeoffset|System. DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System. DateTime|DateTime|DateTime|  
|smalldatetime|System. DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Właściwości SqlParameter  
 W poniższej tabeli opisano `SqlParameter` właściwości, które są istotne dla typów danych Data i godzina.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Pobiera lub ustawia czy wartość dopuszcza wartości null. W przypadku wysyłania wartości parametru o wartości null do serwera należy określić <xref:System.DBNull> , a nie `null` ( `Nothing` w Visual Basic). Aby uzyskać więcej informacji na temat wartości null bazy danych, zobacz [Obsługa wartości null](handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Pobiera lub ustawia maksymalną liczbę cyfr używanych do reprezentowania wartości. To ustawienie jest ignorowane dla typów danych Data i godzina.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Pobiera lub ustawia liczbę miejsc dziesiętnych, do których zostanie rozwiązany fragment czasu wartości `Time` , `DateTime2` i `DateTimeOffset` . Wartość domyślna to 0, co oznacza, że rzeczywista Skala jest wywnioskowana z wartości i wysyłana do serwera.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignorowany dla typów danych daty i godziny.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Pobiera lub ustawia wartość parametru.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Pobiera lub ustawia wartość parametru.|  
  
> [!NOTE]
> Wartość czasu, która jest mniejsza od zera lub większa lub równa 24 godzin, spowoduje wygenerowanie <xref:System.ArgumentException> .  
  
### <a name="creating-parameters"></a>Tworzenie parametrów  
 Można utworzyć <xref:System.Data.SqlClient.SqlParameter> obiekt za pomocą jego konstruktora lub przez dodanie go do <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji, wywołując `Add` metodę <xref:System.Data.SqlClient.SqlParameterCollection> . `Add`Metoda przyjmuje jako dane wejściowe argumenty konstruktora lub istniejący obiekt Parameter.  
  
 W następnych sekcjach tego tematu przedstawiono przykłady sposobu określania parametrów daty i godziny. Aby uzyskać dodatkowe przykłady pracy z parametrami, zobacz [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md) i [DataAdapter Parameters](../dataadapter-parameters.md).  
  
### <a name="date-example"></a>Przykład daty  
 Poniższy fragment kodu pokazuje, jak określić `date` parametr.  
  
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
 Poniższy fragment kodu pokazuje, jak określić `time` parametr.  
  
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
 Poniższy fragment kodu pokazuje, jak określić `datetime2` parametr z częściami daty i godziny.  
  
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
 Poniższy fragment kodu ilustruje sposób określania `DateTimeOffSet` parametru z datą, godziną i przesunięciem strefy czasowej równej 0.  
  
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
 Parametry można także podać przy użyciu `AddWithValue` metody <xref:System.Data.SqlClient.SqlCommand> , jak pokazano w poniższym fragmencie kodu. Jednak metoda nie `AddWithValue` pozwala na określenie <xref:System.Data.SqlClient.SqlParameter.DbType%2A> <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> parametru lub.  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date`Parametr może być mapowany na `date` `datetime` Typ danych, lub `datetime2` na serwerze. Podczas pracy z nowymi `datetime` typami danych należy jawnie ustawić <xref:System.Data.SqlDbType> Właściwość parametru na typ danych wystąpienia. Użycie <xref:System.Data.SqlDbType.Variant> lub niejawne dostarczenie wartości parametrów może spowodować problemy ze zgodnością z poprzednimi wersjami `datetime` i `smalldatetime` typami danych.  
  
 W poniższej tabeli przedstawiono, które `SqlDbTypes` są wywnioskowane z typów CLR:  
  
|Typ CLR|Wywnioskowane SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType. DateTime|  
|przedział_czasu|SqlDbType. Time|  
|DateTimeOffset|SqlDbType. DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Pobieranie danych daty i godziny  
 W poniższej tabeli opisano metody, które są używane do pobierania wartości daty i godziny SQL Server 2008.  
  
|Metoda SqlClient|Opis|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Pobiera określoną wartość kolumny jako <xref:System.DateTime> strukturę.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Pobiera określoną wartość kolumny jako <xref:System.DateTimeOffset> strukturę.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Zwraca typ, który jest podstawowym typem specyficznym dla danego dostawcy dla pola. Zwraca takie same typy jak `GetFieldType` dla nowych typów dat i godzin.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Pobiera wartość określonej kolumny. Zwraca takie same typy jak `GetValue` dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Pobiera wartości z określonej tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Pobiera wartość kolumny jako <xref:System.Data.SqlTypes.SqlString> . <xref:System.InvalidCastException>Występuje, jeśli dane nie mogą być wyrażone jako `SqlString` .|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Domyślnie pobiera dane z kolumny `SqlDbType` . Zwraca takie same typy jak `GetValue` dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Pobiera wartości z określonej tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Pobiera wartość kolumny jako ciąg, jeśli wersja systemu typu jest ustawiona na SQL Server 2005. <xref:System.InvalidCastException>Występuje, jeśli dane nie mogą być wyrażone jako ciąg.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Pobiera określoną wartość kolumny jako <xref:System.TimeSpan> strukturę.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Pobiera określoną wartość kolumny jako jej źródłowy typ CLR.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Pobiera wartości kolumn w tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Zwraca <xref:System.Data.DataTable> , który opisuje metadane zestawu wyników.|  
  
> [!NOTE]
> Nowa Data i godzina `SqlDbTypes` nie są obsługiwane dla kodu, który jest wykonywany w procesie w SQL Server. Jeśli jeden z tych typów zostanie przekazywać do serwera, zostanie zgłoszony wyjątek.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Określanie wartości daty i godziny jako literałów  
 Można określić typy danych daty i godziny przy użyciu różnych formatów ciągów literałów, które SQL Server następnie szacuje się w czasie wykonywania, konwertując je do wewnętrznych struktur daty/czasu. SQL Server rozpoznaje dane daty i godziny ujęte w znaki pojedynczego cudzysłowu ('). W poniższych przykładach przedstawiono niektóre formaty:  
  
- Alfabetyczne formaty dat, takie jak `'October 15, 2006'` .  
  
- Numeryczne formaty daty, takie jak `'10/15/2006'` .  
  
- Nierozdzielne formaty ciągów, takie jak `'20061015'` , które byłyby interpretowane jako 15 października 2006 w przypadku używania standardowego formatu daty ISO.  
  
> [!NOTE]
> Pełną dokumentację dotyczącą wszystkich formatów ciągów literałów i innych funkcji typów danych daty i godziny można znaleźć w temacie SQL Server Books Online.  
  
 Wartość czasu, która jest mniejsza od zera lub większa lub równa 24 godzin, spowoduje wygenerowanie <xref:System.ArgumentException> .  
  
## <a name="resources-in-sql-server-books-online"></a>Zasoby w SQL Server książki online  
 Aby uzyskać więcej informacji na temat pracy z wartościami daty i godziny w SQL Server, zobacz następujące zasoby w SQL Server Books Online.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Typy i funkcje danych daty i godziny (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|Zawiera przegląd wszystkich typów danych i funkcji języka Transact-SQL.|  
|[Korzystanie z danych daty i godziny](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))|Zawiera informacje na temat typów i funkcji danych daty i godziny oraz przykłady ich użycia.|  
|[Typy danych (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)|Opisuje systemowe typy danych w SQL Server.|  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie typu danych serwera SQL](../sql-server-data-type-mappings.md)
- [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md)
- [Typy danych programu SQL Server i ADO.NET](sql-server-data-types.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
