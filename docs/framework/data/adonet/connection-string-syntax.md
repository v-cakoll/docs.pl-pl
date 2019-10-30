---
title: Składnia parametrów połączenia
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 9e9e330b7195e5c04b6e9e2d086a04209e1c0e13
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040155"
---
# <a name="connection-string-syntax"></a>Składnia parametrów połączenia
Każdy dostawca danych .NET Framework ma obiekt `Connection`, który dziedziczy po <xref:System.Data.Common.DbConnection> oraz Właściwość <xref:System.Data.Common.DbConnection.ConnectionString%2A> specyficzną dla dostawcy. Składnia określonych parametrów połączenia dla każdego dostawcy jest udokumentowana w `ConnectionString` właściwości. Poniższa tabela zawiera listę czterech dostawców danych uwzględnionych w .NET Framework.  
  
|Dostawca danych .NET Framework|Opis|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Zapewnia dostęp do danych Microsoft SQL Server. Aby uzyskać więcej informacji na temat składni parametrów połączenia, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|Zapewnia dostęp do danych dla źródeł danych narażonych na korzystanie z OLE DB. Aby uzyskać więcej informacji na temat składni parametrów połączenia, zobacz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|Zapewnia dostęp do danych dla źródeł danych narażonych na korzystanie z ODBC. Aby uzyskać więcej informacji na temat składni parametrów połączenia, zobacz <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Zapewnia dostęp do danych dla programu Oracle w wersji 8.1.7 lub nowszej. Aby uzyskać więcej informacji na temat składni parametrów połączenia, zobacz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Konstruktorzy parametrów połączeń  
 W ADO.NET 2,0 wprowadzono następujących konstruktorów parametrów połączenia dla dostawców danych .NET Framework.  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Konstruktory parametrów połączenia umożliwiają konstruowanie składniowo prawidłowych parametrów połączenia w czasie wykonywania, dzięki czemu nie trzeba ręcznie łączyć wartości parametrów połączenia w kodzie. Aby uzyskać więcej informacji, zobacz [konstruktory parametrów połączenia](connection-string-builders.md).  

## <a name="windows-authentication"></a>Uwierzytelnianie systemu Windows  
 Zalecamy używanie uwierzytelniania systemu Windows (nazywanego czasem *zabezpieczeniami zintegrowanymi*) do nawiązywania połączeń ze źródłami danych, które je obsługują. Składnia wykorzystywana w parametrach połączenia zależy od dostawcy. W poniższej tabeli przedstawiono składnię uwierzytelniania systemu Windows używaną z dostawcami danych .NET Framework.  
  
|Dostawcy|Składnia|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> `Integrated Security=true` zgłasza wyjątek, gdy jest używany z dostawcą `OleDb`.  
  
## <a name="sqlclient-connection-strings"></a>Parametry połączenia SqlClient  
Składnia <xref:System.Data.SqlClient.SqlConnection> parametrów połączenia jest udokumentowana we właściwości <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>. Za pomocą właściwości <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> można pobrać lub ustawić parametry połączenia dla bazy danych SQL Server. Jeśli musisz nawiązać połączenie z wcześniejszą wersją SQL Server, musisz użyć Dostawca danych .NET Framework dla OleDb (<xref:System.Data.OleDb>). Większość słów kluczowych parametrów połączenia jest również mapowanych na właściwości w <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  

> [!IMPORTANT]
> Ustawienie domyślne dla słowa kluczowego `Persist Security Info` jest `false`. Ustawienie go na `true` lub `yes` pozwala uzyskać informacje dotyczące zabezpieczeń, w tym identyfikator użytkownika i hasło, które zostaną uzyskane z połączenia po otwarciu połączenia. Zachowaj `Persist Security Info` ustaw na `false`, aby upewnić się, że niezaufane źródło nie ma dostępu do poufnych informacji o parametrach połączenia.  

### <a name="windows-authentication-with-sqlclient"></a>Uwierzytelnianie systemu Windows za pomocą programu SqlClient 
 Każda z poniższych form składni używa uwierzytelniania systemu Windows do łączenia się z bazą danych **AdventureWorks** na serwerze lokalnym.  
  
```csharp  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>Uwierzytelnianie SQL Server przy użyciu programu SqlClient   
 Uwierzytelnianie systemu Windows jest preferowane w przypadku łączenia się z SQL Server. Jeśli jednak wymagane jest uwierzytelnianie SQL Server, użyj następującej składni, aby określić nazwę użytkownika i hasło. W tym przykładzie gwiazdki są używane do reprezentowania prawidłowej nazwy użytkownika i hasła.  
  
```csharp  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Po nawiązaniu połączenia z usługą Azure SQL Database lub Azure SQL Data Warehouse i podania nazwy logowania w `user@servername`formacie upewnij się, że wartość `servername` identyfikatora logowania odpowiada wartości podanej dla `Server=`.

> [!NOTE]
> Uwierzytelnianie systemu Windows ma pierwszeństwo przed logowaniami SQL Server. Jeśli określisz zarówno zintegrowane zabezpieczenia = true jak i nazwę użytkownika i hasło, nazwa użytkownika i hasło zostaną zignorowane i zostanie użyte uwierzytelnianie systemu Windows.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Nawiązywanie połączenia z nazwanym wystąpieniem SQL Server
Aby nawiązać połączenie z nazwanym wystąpieniem SQL Server, użyj składni *nazwy Nazwa serwera* .  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

Podczas kompilowania parametrów połączenia można również ustawić właściwość <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> `SqlConnectionStringBuilder` na nazwę wystąpienia. Właściwość <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> obiektu <xref:System.Data.SqlClient.SqlConnection> jest tylko do odczytu.  
  
### <a name="type-system-version-changes"></a>Wpisz zmiany wersji systemu  
 Słowo kluczowe `Type System Version` w <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> określa reprezentacje po stronie klienta SQL Server typów. Aby uzyskać więcej informacji na temat słowa kluczowego `Type System Version`, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Łączenie i dołączanie do SQL Server Express wystąpień użytkownika  
 Wystąpienia użytkownika są funkcją w SQL Server Express. Umożliwiają one użytkownikowi uruchomionemu na najniższych uprawnieniach lokalnych konta systemu Windows dołączenie i uruchomienie SQL Server bazy danych bez konieczności posiadania uprawnień administracyjnych. Wystąpienie użytkownika jest wykonywane z poświadczeniami systemu Windows użytkownika, a nie jako usługa.  
  
 Aby uzyskać więcej informacji na temat pracy z wystąpieniami użytkowników, zobacz [SQL Server Express wystąpień użytkownika](./sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Korzystanie z TrustServerCertificate  
 Słowo kluczowe `TrustServerCertificate` jest prawidłowe tylko w przypadku nawiązywania połączenia z wystąpieniem SQL Server z prawidłowym certyfikatem. Gdy `TrustServerCertificate` jest ustawiona na `true`, warstwa transportu będzie używać protokołu SSL do szyfrowania kanału i pomijania pominięcia łańcucha certyfikatów w celu zweryfikowania zaufania.  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> Jeśli `TrustServerCertificate` jest ustawiona na `true`, a szyfrowanie jest włączone, poziom szyfrowania określony na serwerze będzie używany nawet wtedy, gdy `Encrypt` jest ustawiona na `false` w parametrach połączenia. W przeciwnym razie połączenie zakończy się niepowodzeniem.  
  
### <a name="enabling-encryption"></a>Włączanie szyfrowania  
 Aby włączyć szyfrowanie, gdy nie zainicjowano obsługi administracyjnej certyfikatu na serwerze, w SQL Server Configuration Manager należy ustawić opcje **szyfrowanie protokołu Force** i **certyfikat serwera zaufania** . W takim przypadku szyfrowanie będzie używać certyfikatu serwera z podpisem własnym bez sprawdzania poprawności, jeśli nie zainicjowano obsługi administracyjnej na serwerze żadnego certyfikatu zweryfikowanego.  
  
 Ustawienia aplikacji nie mogą zmniejszyć poziomu zabezpieczeń skonfigurowanych w SQL Server, ale można go opcjonalnie wzmocnić. Aplikacja może zażądać szyfrowania przez ustawienie słów kluczowych `TrustServerCertificate` i `Encrypt` na `true`, co gwarantuje, że szyfrowanie odbywa się nawet wtedy, gdy certyfikat serwera nie został zainicjowany i nie skonfigurowano **wymuszania szyfrowania protokołu** dla klienta. Jeśli jednak `TrustServerCertificate` nie jest włączona w konfiguracji klienta, jest nadal wymagany certyfikat serwera aprowizacji.  
  
 W poniższej tabeli opisano wszystkie przypadki.  
  
|Wymuś ustawienie klienta szyfrowania protokołu|Ustawienie klienta certyfikatu serwera zaufania|Szyfrowanie/używanie szyfrowania dla parametrów/atrybutu połączenia danych|Certyfikat serwera zaufania parametry/atrybut połączenia|Wynik|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Nie|Brak|Nie (domyślnie)|Ignorowane|Nie są wykonywane żadne szyfrowanie.|  
|Nie|Brak|Tak|Nie (domyślnie)|Szyfrowanie występuje tylko wtedy, gdy istnieje zweryfikowany certyfikat serwera, w przeciwnym razie próba połączenia nie powiedzie się.|  
|Nie|Brak|Tak|Tak|Szyfrowanie zawsze występuje, ale może korzystać z certyfikatu serwera z podpisem własnym.|  
|Tak|Nie|Ignorowane|Ignorowane|Szyfrowanie występuje tylko wtedy, gdy istnieje zweryfikowany certyfikat serwera; w przeciwnym razie próba połączenia nie powiedzie się.|  
|Tak|Tak|Nie (domyślnie)|Ignorowane|Szyfrowanie zawsze występuje, ale może korzystać z certyfikatu serwera z podpisem własnym.|  
|Tak|Tak|Tak|Nie (domyślnie)|Szyfrowanie występuje tylko wtedy, gdy istnieje zweryfikowany certyfikat serwera; w przeciwnym razie próba połączenia nie powiedzie się.|  
|Tak|Tak|Tak|Tak|Szyfrowanie zawsze występuje, ale może korzystać z certyfikatu serwera z podpisem własnym.|  
  
 Aby uzyskać więcej informacji, zobacz [używanie szyfrowania bez sprawdzania poprawności](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>Parametry połączenia OleDb  
 Właściwość <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> <xref:System.Data.OleDb.OleDbConnection> umożliwia pobieranie lub Ustawianie parametrów połączenia dla źródła danych OLE DB, takich jak Microsoft Access. Możesz również utworzyć `OleDb` parametry połączenia w czasie wykonywania przy użyciu klasy <xref:System.Data.OleDb.OleDbConnectionStringBuilder>.  
  
### <a name="oledb-connection-string-syntax"></a>Składnia parametrów połączenia OleDb  
 Należy określić nazwę dostawcy dla <xref:System.Data.OleDb.OleDbConnection> parametrów połączenia. Poniższe parametry połączenia nawiązują połączenie z bazą danych programu Microsoft Access za pomocą dostawcy Jet. Należy zauważyć, że `User ID` i `Password` słowa kluczowe są opcjonalne, jeśli baza danych jest niezabezpieczona (domyślnie).  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;
```  
  
 Jeśli baza danych programu Jet jest zabezpieczona przy użyciu zabezpieczeń na poziomie użytkownika, należy podać lokalizację pliku informacji o grupie roboczej (. mdw). Plik informacji o grupie roboczej służy do weryfikowania poświadczeń przedstawionych w parametrach połączenia.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> Możliwe jest podanie informacji o połączeniu dla **OleDbConnection** w pliku Universal Data Link (UDL); należy jednak unikać tego. Pliki UDL nie są szyfrowane i ujawniają informacje o parametrach połączenia w postaci zwykłego tekstu. Ponieważ plik UDL jest zewnętrznym zasobem opartym na plikach dla aplikacji, nie może być zabezpieczony przy użyciu .NET Framework. Pliki UDL nie są obsługiwane w przypadku usługi **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Używanie usługi DataDirectory do łączenia się z dostępem/aparatem Jet  
 `DataDirectory` nie `SqlClient`. Można go również używać z dostawcami danych <xref:System.Data.OleDb> i <xref:System.Data.Odbc> .NET. Następujący przykładowy ciąg <xref:System.Data.OleDb.OleDbConnection> ilustruje składnię wymaganą do nawiązania połączenia z Northwind. mdb znajdującą się w folderze App_Data aplikacji. Systemowa baza danych (System. mdw) jest również przechowywana w tej lokalizacji.  
  
```csharp  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> Określenie lokalizacji systemowej bazy danych w parametrach połączenia nie jest wymagane, jeśli baza danych dostępu/Jet jest niezabezpieczona. Zabezpieczenia są domyślnie wyłączone, gdy wszyscy użytkownicy nawiązują połączenie jako wbudowanego użytkownika administracyjnego z pustym hasłem. Nawet jeśli zabezpieczenia na poziomie użytkownika są poprawnie zaimplementowane, baza danych aparatu Jet pozostaje narażona na ataki. W związku z tym przechowywanie poufnych informacji w bazie danych dostępu/Jet nie jest zalecane ze względu na nieodłączną słabość schematu zabezpieczeń opartego na plikach.  
  
### <a name="connecting-to-excel"></a>Łączenie z programem Excel  
 Dostawca Microsoft Jet jest używany do nawiązywania połączenia ze skoroszytem programu Excel. W poniższych parametrach połączenia słowo kluczowe `Extended Properties` ustawia właściwości specyficzne dla programu Excel. "HDR = tak;" wskazuje, że pierwszy wiersz zawiera nazwy kolumn, a nie dane i "IMEX = 1;" informuje sterownik, aby zawsze czytał kolumny danych "międzymieszanych" jako tekst.  
  
```csharp 
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Należy zauważyć, że znak podwójnego cudzysłowu wymagany dla `Extended Properties` musi być również ujęty w znaki podwójnego cudzysłowu.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Składnia parametrów połączenia dostawcy kształtu danych  
 Użyj `Provider` i `Data Provider` słów kluczowych podczas korzystania z dostawcy kształtów danych firmy Microsoft. Poniższy przykład używa dostawcy kształtu do łączenia się z lokalnym wystąpieniem SQL Server.  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>Parametry połączenia ODBC  
 Właściwość <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> <xref:System.Data.Odbc.OdbcConnection> umożliwia pobieranie lub Ustawianie parametrów połączenia dla źródła danych OLE DB. Parametry połączenia ODBC są również obsługiwane przez <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.  
  
 Poniższe parametry połączenia używają sterownika tekstowego firmy Microsoft.  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Łączenie z programem Visual FoxPro przy użyciu usługi DataDirectory  
 Poniższy <xref:System.Data.Odbc.OdbcConnection> ciąg połączenia ilustruje używanie `DataDirectory` do nawiązywania połączenia z plikiem programu Microsoft Visual FoxPro.  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Parametry połączenia Oracle  
 Właściwość <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> <xref:System.Data.OracleClient.OracleConnection> umożliwia pobieranie lub Ustawianie parametrów połączenia dla źródła danych OLE DB. Parametry połączenia Oracle są również obsługiwane przez <xref:System.Data.OracleClient.OracleConnectionStringBuilder>.  
  
```csharp 
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Aby uzyskać więcej informacji na temat składni parametrów połączenia ODBC, zobacz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Parametry połączeń](connection-strings.md)
- [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)
- [Omówienie ADO.NET](ado-net-overview.md)
