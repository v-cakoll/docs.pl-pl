---
title: Dane daty i godziny
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: d7a016b8911cee3091dec24bc26d1f1965f54749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148767"
---
# <a name="date-and-time-data"></a>Dane daty i godziny
Program SQL Server 2008 wprowadza nowe typy danych do obsługi informacji o datach i godzinie. Nowe typy danych obejmują oddzielne typy daty i godziny oraz rozszerzone typy danych z większym zakresem, precyzją i świadomością stref czasowych. Począwszy od programu .NET Framework w wersji 3.5 z dodatkiem Service Pack<xref:System.Data.SqlClient>(SP) 1, dostawca danych programu .NET Framework dla programu SQL Server ( ) zapewnia pełną obsługę wszystkich nowych funkcji aparatu baz danych programu SQL Server 2008. Aby korzystać z tych nowych funkcji w programie SqlClient, należy zainstalować dodatek SP1 (lub nowszy) programu .NET Framework 3.5.  
  
 Wersje programu SQL Server starsze niż SQL Server 2008 miały tylko `datetime` dwa `smalldatetime`typy danych do pracy z wartościami daty i godziny: i . Oba te typy danych zawierają zarówno wartość daty, jak i wartość czasu, co utrudnia pracę tylko z wartościami daty lub tylko godziny. Ponadto te typy danych obsługują tylko daty, które występują po wprowadzeniu kalendarza gregoriańskiego w Anglii w 1753 roku. Innym ograniczeniem jest to, że te starsze typy danych nie są świadome strefy czasowej, co utrudnia pracę z danymi pochodzącymi z wielu stref czasowych.  
  
 Pełna dokumentacja dla typów danych programu SQL Server jest dostępna w uiszczce SQL Server Books Online. W poniższej tabeli wymieniono tematy podstawowe specyficzne dla wersji dla danych daty i godziny.  
  
 **SQL Server documentation (Dokumentacja programu SQL Server)**  
  
1. [Korzystanie z danych daty i godziny](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Typy danych daty/godziny wprowadzone w programie SQL Server 2008  
 W poniższej tabeli opisano nowe typy danych daty i godziny.  
  
|Typ danych programu SQL Server|Opis|  
|--------------------------|-----------------|  
|`date`|Typ `date` danych ma zakres od 1 stycznia 01 do 31 grudnia 9999 z dokładnością 1 dnia. Wartością domyślną jest 1 stycznia 1900. Rozmiar magazynu wynosi 3 bajty.|  
|`time`|Typ `time` danych przechowuje tylko wartości czasu na podstawie zegara 24-godzinnego. Typ `time` danych ma zakres od 00:00:00.0000000 do 23:59:59.99999999 z dokładnością 100 nanosekund. Wartość domyślna to 00:00:00.0000000 (północ). Typ `time` danych obsługuje zdefiniowaną przez użytkownika ułamkową sekundę precyzji, a rozmiar magazynu waha się od 3 do 6 bajtów, na podstawie określonej precyzji.|  
|`datetime2`|Typ `datetime2` danych łączy zakres i dokładność `date` `time` typów danych i w jeden typ danych.<br /><br /> Wartości domyślne i formaty literału ciągów `date` są `time` takie same jak te zdefiniowane w typach danych i.|  
|`datetimeoffset`|Typ `datetimeoffset` danych ma wszystkie `datetime2` funkcje z dodatkowym przesunięciem strefy czasowej. Przesunięcie strefy czasowej jest reprezentowane jako [+&#124;-] HH:MM. HH to 2 cyfry od 00 do 14, które reprezentują liczbę godzin w przesunięciu strefy czasowej. MM to 2 cyfry od 00 do 59, które reprezentują liczbę dodatkowych minut w przesunięciu strefy czasowej. Formaty czasu są obsługiwane do 100 nanosekund. Obowiązkowy znak + lub - wskazuje, czy przesunięcie strefy czasowej jest dodawane lub odejmowane od czasu UTC (uniwersalna współrzędna czasu lub średni czas Greenwich) w celu uzyskania czasu lokalnego.|  
  
> [!NOTE]
> Aby uzyskać więcej `Type System Version` informacji na <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>temat używania słowa kluczowego, zobacz .  
  
## <a name="date-format-and-date-order"></a>Format daty i kolejność dat  
 Sposób analizowania wartości daty i godziny przez program SQL Server zależy nie tylko od wersji systemu typu i wersji serwera, ale także od domyślnych ustawień języka i formatu serwera. Ciąg daty, który działa dla formatów daty jednego języka może być nie do poznania, jeśli kwerenda jest wykonywana przez połączenie, które używa innego języka i ustawienia formatu daty.  
  
 Instrukcja Transact-SQL SET LANGUAGE niejawnie ustawia DATEFORMAT, który określa kolejność części daty. Instrukcji SET DATEFORMAT Transact-SQL można użyć w połączeniu, aby odróżnić wartości dat, porządkując części daty w kolejności MDY, DMY, YMD, YDM, MYD lub DYM.  
  
 Jeśli nie określisz żadnej funkcji DATEFORMAT dla połączenia, program SQL Server użyje domyślnego języka skojarzonego z połączeniem. Na przykład ciąg daty "01/02/03" będzie interpretowany jako MDY (2 stycznia 2003) na serwerze z ustawieniem języka języka angielskiego w Stanach Zjednoczonych i jako DMY (1 lutego 2003) na serwerze z ustawieniem języka języka angielskiego brytyjskiego. Rok jest określany przy użyciu reguły roku odcięcia programu SQL Server, która definiuje datę odcięcia dla przypisywania wartości stulecia. Aby uzyskać więcej informacji, zobacz [dwucyfrową opcję odcięcia roku](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).  
  
> [!NOTE]
> Format daty YDM nie jest obsługiwany podczas konwersji `datetime2`z `datetimeoffset`formatu ciągu na `date`, `time`, lub .  
  
 Aby uzyskać więcej informacji o interpretować dane daty i godziny przez program SQL Server, zobacz [Korzystanie z danych daty i godziny](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).  
  
## <a name="datetime-data-types-and-parameters"></a>Typy i parametry danych daty/godziny  
 Następujące wyliczenia zostały dodane <xref:System.Data.SqlDbType> do obsługi nowych typów danych daty i godziny.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Można określić typ danych <xref:System.Data.SqlClient.SqlParameter> a przy użyciu <xref:System.Data.SqlDbType> jednego z powyższych wyliczeń.

> [!NOTE]
> Nie można `DbType` ustawić właściwości `SqlParameter` `SqlDbType.Date`a do .

 Można również określić typ <xref:System.Data.SqlClient.SqlParameter> ogólny, ustawiając <xref:System.Data.SqlClient.SqlParameter.DbType%2A> właściwość `SqlParameter` obiektu <xref:System.Data.DbType> na określoną wartość wyliczenia. Do obsługi `datetime2` typów `datetimeoffset` danych i typów <xref:System.Data.DbType> danych dodano następujące wartości wyliczenia:  
  
- DbType.DateTime2  
  
- DbType.DateOffset  
  
 Te nowe wyliczenia `Date` `Time`uzupełniają `DateTime` , i wyliczenia, które istniały we wcześniejszych wersjach programu .NET Framework.  
  
 Typ dostawcy danych programu .NET Framework obiektu parametru jest wywnioskowany z typu .NET Framework wartości obiektu parametru lub z obiektu `DbType` parametru. Nie <xref:System.Data.SqlTypes> wprowadzono żadnych nowych typów danych do obsługi nowych typów danych daty i godziny. W poniższej tabeli opisano mapowania między typami danych daty i godziny programu SQL Server 2008 a typami danych CLR.  
  
|Typ danych programu SQL Server|Typ programu .NET Framework|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|System.datetime|Data|Data|  
|time|System.timespan|Time|Time|  
|datetime2|System.datetime|DateTime2|DateTime2|  
|datetimeoffset|System.DateTimeOffset|Datetimeoffset|Datetimeoffset|  
|datetime|System.datetime|DateTime|DateTime|  
|smalldatetime|System.datetime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Właściwości parametru SqlParameter  
 W poniższej `SqlParameter` tabeli opisano właściwości, które są istotne dla typów danych daty i godziny.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Pobiera lub ustawia, czy wartość jest nullable. Podczas wysyłania wartości parametru null do <xref:System.DBNull>serwera należy `null` `Nothing` określić , a nie ( w języku Visual Basic). Aby uzyskać więcej informacji na temat wartości null bazy danych, zobacz [Obsługa wartości null](handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Pobiera lub ustawia maksymalną liczbę cyfr używanych do reprezentowania wartości. To ustawienie jest ignorowane dla typów danych daty i godziny.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Pobiera lub ustawia liczbę miejsc dziesiętnych, do których część czasu `Time` `DateTime2`wartości `DateTimeOffset`jest rozpoznawana dla , i . Wartość domyślna to 0, co oznacza, że rzeczywista skala jest wywnioskowana z wartości i wysyłana do serwera.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignorowane dla typów danych daty i godziny.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Pobiera lub ustawia wartość parametru.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Pobiera lub ustawia wartość parametru.|  
  
> [!NOTE]
> Wartości czasu, które są mniejsze niż zero lub większe lub <xref:System.ArgumentException>równe 24 godzin, będą rzucać .  
  
### <a name="creating-parameters"></a>Tworzenie parametrów  
 <xref:System.Data.SqlClient.SqlParameter> Obiekt można utworzyć przy użyciu jego konstruktora <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> lub dodając `Add` go do <xref:System.Data.SqlClient.SqlParameterCollection>kolekcji, wywołując metodę . Metoda `Add` będzie przyjmować jako dane wejściowe argumenty konstruktora lub istniejący obiekt parametru.  
  
 Następne sekcje w tym temacie zawierają przykłady określania parametrów daty i godziny. Aby uzyskać dodatkowe przykłady pracy z parametrami, zobacz [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md) oraz [parametrów dataadapter](../dataadapter-parameters.md).  
  
### <a name="date-example"></a>Przykład daty  
 Poniższy fragment kodu pokazuje, `date` jak określić parametr.  
  
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
 Poniższy fragment kodu pokazuje, `time` jak określić parametr.  
  
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
 Poniższy fragment kodu pokazuje, `datetime2` jak określić parametr z częściami daty i godziny.  
  
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
  
### <a name="datetimeoffset-example"></a>Przykład datetimeoffset  
 Poniższy fragment kodu pokazuje, `DateTimeOffSet` jak określić parametr z datą, godziną i przesunięciem strefy czasowej równej 0.  
  
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
  
### <a name="addwithvalue"></a>Dodaj Wartość  
 Parametry można również podać `AddWithValue` przy użyciu <xref:System.Data.SqlClient.SqlCommand>metody , jak pokazano w poniższym fragmencie kodu. Jednak `AddWithValue` metoda nie pozwala na określenie <xref:System.Data.SqlClient.SqlParameter.DbType%2A> <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> lub dla parametru.  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 Parametr `@date` może być `date`mapowany na , `datetime`lub `datetime2` typ danych na serwerze. Podczas pracy z `datetime` nowymi typami danych należy jawnie <xref:System.Data.SqlDbType> ustawić właściwość parametru na typ danych wystąpienia. Używanie <xref:System.Data.SqlDbType.Variant> lub niejawnie dostarczanie wartości parametrów może powodować `datetime` problemy `smalldatetime` ze zgodnością z powrotem z typami danych i.  
  
 W poniższej `SqlDbTypes` tabeli przedstawiono, które są wywnioskowane, z których typy CLR:  
  
|Typ CLR|Wywnioskowany sqldbtype|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|przedział_czasu|SqlDbType.Time|  
|Datetimeoffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Pobieranie danych daty i godziny  
 W poniższej tabeli opisano metody, które są używane do pobierania wartości daty i godziny programu SQL Server 2008.  
  
|Metoda SqlClient|Opis|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Pobiera określoną wartość kolumny <xref:System.DateTime> jako strukturę.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Pobiera określoną wartość kolumny <xref:System.DateTimeOffset> jako strukturę.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Zwraca typ, który jest typem specyficznym dla dostawcy źródłowego dla tego pola. Zwraca te same `GetFieldType` typy, co w przypadku nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Pobiera wartość określonej kolumny. Zwraca te same `GetValue` typy, co dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Pobiera wartości w określonej tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Pobiera wartość kolumny jako <xref:System.Data.SqlTypes.SqlString>. Występuje, <xref:System.InvalidCastException> jeśli dane nie mogą `SqlString`być wyrażone jako .|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Pobiera dane kolumny jako `SqlDbType`domyślne . Zwraca te same `GetValue` typy, co dla nowych typów daty i godziny.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Pobiera wartości w określonej tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Pobiera wartość kolumny jako ciąg, jeśli wersja systemu typu jest ustawiona na SQL Server 2005. Występuje, <xref:System.InvalidCastException> jeśli dane nie mogą być wyrażone jako ciąg.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Pobiera określoną wartość kolumny <xref:System.TimeSpan> jako strukturę.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Pobiera określoną wartość kolumny jako podstawowy typ CLR.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Pobiera wartości kolumn w tablicy.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Zwraca, <xref:System.Data.DataTable> który opisuje metadane zestawu wyników.|  
  
> [!NOTE]
> Nowa data i `SqlDbTypes` godzina nie są obsługiwane dla kodu, który jest wykonywany w procesie w programie SQL Server. Wyjątek zostanie podniesiony, jeśli jeden z tych typów jest przekazywany do serwera.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Określanie wartości daty i godziny jako literałów  
 Można określić typy danych daty i godziny przy użyciu różnych formatów ciągów literału, które sql server następnie ocenia w czasie wykonywania, konwertując je do wewnętrznych struktur daty/godziny. SQL Server rozpoznaje dane daty i godziny, które są ujęte w pojedynczy cudzysłów ('). Poniższe przykłady pokazują niektóre formaty:  
  
- Alfabetyczne formaty daty, takie jak `'October 15, 2006'`.  
  
- Formaty daty numerycznej, takie jak `'10/15/2006'`.  
  
- Nierozdzielone formaty ciągów, `'20061015'`takie jak , które byłyby interpretowane jako 15 października 2006 r., jeśli używasz standardowego formatu daty ISO.  
  
> [!NOTE]
> Pełną dokumentację wszystkich formatów ciągów literału i innych funkcji typów danych daty i godziny można znaleźć w programie SQL Server Books Online.  
  
 Wartości czasu, które są mniejsze niż zero lub większe lub <xref:System.ArgumentException>równe 24 godzin, będą rzucać .  
  
## <a name="resources-in-sql-server-books-online"></a>Zasoby w programie SQL Server Books Online  
 Aby uzyskać więcej informacji na temat pracy z wartościami daty i godziny w programie SQL Server, zobacz następujące zasoby w programie SQL Server Books Online.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Typy i funkcje danych daty i godziny (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|Zawiera omówienie wszystkich typów i funkcji danych daty i godziny transakcji i sql.|  
|[Korzystanie z danych daty i godziny](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))|Zawiera informacje o typach i funkcjach danych daty i godziny oraz przykłady ich używania.|  
|[Typy danych (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)|Zawiera opis typów danych systemowych w programie SQL Server.|  
  
## <a name="see-also"></a>Zobacz też

- [Mapowanie typu danych serwera SQL](../sql-server-data-type-mappings.md)
- [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md)
- [Typy danych programu SQL Server i ADO.NET](sql-server-data-types.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
