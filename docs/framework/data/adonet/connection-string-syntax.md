---
title: Składnia ciągu połączenia
ms.date: 03/30/2017
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: ac7053d1b1b0865f33ae1bcd955493b4c62c7be6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="connection-string-syntax"></a>Składnia ciągu połączenia
Każdy dostawca danych programu .NET Framework ma `Connection` obiekt dziedziczący z <xref:System.Data.Common.DbConnection> oraz specyficznych dla dostawcy <xref:System.Data.Common.DbConnection.ConnectionString%2A> właściwości. Składnia ciągu połączenia specyficzne dla każdego dostawcy jest udokumentowany w jego `ConnectionString` właściwości. W poniższej tabeli wymieniono dostawców cztery danych, które znajdują się w programie .NET Framework.  
  
|Dostawca danych programu .NET framework|Opis|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Zapewnia dostęp do danych programu Microsoft SQL Server. Aby uzyskać więcej informacji o składni ciągu połączenia, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|Zapewnia dostęp do danych dla źródeł danych ujawnianej za pomocą OLE DB. Aby uzyskać więcej informacji o składni ciągu połączenia, zobacz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|Zapewnia dostęp do danych dla źródeł danych, udostępnione za pośrednictwem sterownika ODBC. Aby uzyskać więcej informacji o składni ciągu połączenia, zobacz <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Zapewnia dostęp do danych programu Oracle w wersji version 8.1.7 lub nowszej. Aby uzyskać więcej informacji o składni ciągu połączenia, zobacz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Konstruktorzy ciągów połączenia  
 ADO.NET 2.0 wprowadzono następujące konstruktorów ciągu połączenia dla dostawcy danych .NET Framework.  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Konstruktorzy ciągów połączenia pozwalają utworzyć parametry połączenia nieprawidłową składnię w czasie wykonywania, dzięki czemu nie trzeba ręcznie połączyć wartości ciągu połączenia w kodzie. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md).  

## <a name="windows-authentication"></a>Uwierzytelnianie systemu Windows  
 Firma Microsoft zaleca używanie uwierzytelniania systemu Windows (czasami określane jako *zabezpieczenia zintegrowane*) nawiązywania połączenia ze źródłami danych, które ją obsługują. Składnia zatrudnionych w parametrach połączenia jest zależna od dostawcy. W poniższej tabeli przedstawiono składnię uwierzytelniania systemu Windows używana z dostawcy danych .NET Framework.  
  
|Dostawcy|Składnia|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  `Integrated Security=true` zgłasza wyjątek w przypadku użycia z `OleDb` dostawcy.  
  
## <a name="sqlclient-connection-strings"></a>Parametry połączenia SqlClient  
Składnia <xref:System.Data.SqlClient.SqlConnection> opisano parametry połączenia w <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> właściwości. Można użyć <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> właściwości do pobierania lub ustawiania ciągu połączenia dla bazy danych programu SQL Server. Jeśli musisz nawiązać połączenia z wcześniejszej wersji programu SQL Server, należy użyć dostawcy danych programu .NET Framework dla OleDb (<xref:System.Data.OleDb>). Słowa kluczowe parametrów połączenia większości również mapować do właściwości w <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  

> [!IMPORTANT]
>  Ustawieniem domyślnym dla `Persist Security Info` — słowo kluczowe jest `false`. Ustawieniem dla niego `true` lub `yes` umożliwia informacji istotnych dla zabezpieczeń, w tym identyfikator użytkownika i hasło, które mają zostać uzyskane z połączenia po otwarciu połączenia. Zachowaj `Persist Security Info` ustawioną `false` aby upewnić się, że niezaufanego źródła nie ma dostępu do poufnych ciągu połączenia.  

### <a name="windows-authentication-with-sqlclient"></a>Uwierzytelnianie systemu Windows z SqlClient 
 Każdy z następujących rodzajów składni używa uwierzytelniania systemu Windows do nawiązania połączenia **AdventureWorks** bazy danych na serwerze lokalnym.  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>Uwierzytelnianie programu SQL Server z SqlClient   
 Uwierzytelnianie systemu Windows jest preferowana przez łączenie z serwerem SQL. Jednak jeśli wymagane jest uwierzytelnienie serwera SQL, należy użyć następującej składni, aby określić nazwę użytkownika i hasło. W tym przykładzie gwiazdki są używane do reprezentowania prawidłowej nazwy użytkownika i hasła.  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Podczas łączenia z bazą danych SQL Azure lub usługi Azure SQL Data Warehouse i podaj identyfikator logowania w formacie `user@servername`, upewnij się, że `servername` wartość nazwy logowania jest zgodna z wartością przewidzianych `Server=`.

> [!NOTE]
>  Uwierzytelnianie systemu Windows mają pierwszeństwo przed logowania do programu SQL Server. Określenia obu Integrated Security = true również jako nazwy użytkownika i hasła, nazwę użytkownika i hasło zostaną zignorowane i będzie używane uwierzytelnianie systemu Windows.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Połącz się z nazwanym wystąpieniem programu SQL Server
Aby połączyć się z nazwanym wystąpieniem programu SQL Server, użyj *nazwa serwera azwa wystąpienia* składni.  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
Można również ustawić <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> właściwość `SqlConnectionStringBuilder` do nazwy obiektu podczas kompilowania parametrów połączenia. <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> Właściwość <xref:System.Data.SqlClient.SqlConnection> obiekt jest tylko do odczytu.  
  
### <a name="type-system-version-changes"></a>Zmiana wersji systemu typu  
 `Type System Version` — Słowo kluczowe w <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> określa po stronie klienta reprezentację typów programu SQL Server. Zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> uzyskać więcej informacji o `Type System Version` — słowo kluczowe.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Połączenie i dołączenie do programu SQL Server Express wystąpień użytkownika  
 Wystąpienia użytkownika są funkcją w programie SQL Server Express. One użytkownicy systemem najmniej uprzywilejowane konta lokalnego systemu Windows do dołączania i uruchomić bazy danych programu SQL Server bez wymogu posiadania uprawnień administracyjnych. Wystąpienia użytkownika jest wykonywana przy użyciu poświadczeń systemu Windows użytkownika, nie jako usługa.  
  
 Aby uzyskać więcej informacji na temat pracy z wystąpień użytkownika, zobacz [wystąpienia programu SQL Server Express użytkownika](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Przy użyciu TrustServerCertificate  
 `TrustServerCertificate` — Słowo kluczowe jest prawidłowy tylko w przypadku nawiązywania połączenia z wystąpieniem programu SQL Server przy użyciu prawidłowego certyfikatu. Gdy `TrustServerCertificate` ma ustawioną wartość `true`, warstwy transportowej będą używać protokołu SSL do szyfrowania kanału i obejście przejście łańcuch certyfikatów do sprawdzania poprawności zaufania.  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  Jeśli `TrustServerCertificate` ustawiono `true` i szyfrowanie jest włączone, poziom szyfrowania określonych na serwerze, który będzie używany nawet wtedy, gdy `Encrypt` ma ustawioną wartość `false` w parametrach połączenia. Połączenia zakończy się niepowodzeniem, w przeciwnym razie wartość.  
  
### <a name="enabling-encryption"></a>Włączenie szyfrowania  
 Aby włączyć szyfrowanie, gdy nie zainicjowano certyfikatu na serwerze, **wymuszania szyfrowania protokołu** i **zaufania certyfikatów serwera** opcje można ustawić w programie SQL Server Configuration Manager. W takim przypadku szyfrowania będzie używany certyfikat serwera z podpisem własnym bez sprawdzania poprawności, jeśli zainicjowano nie zweryfikowania certyfikatu na serwerze.  
  
 Ustawienia aplikacji nie można zmniejszyć poziom zabezpieczeń skonfigurowane w programie SQL Server, ale Opcjonalnie można wzmocnić. Aplikacja może zażądać szyfrowania przez ustawienie `TrustServerCertificate` i `Encrypt` słów kluczowych `true`, gwarantując, że szyfrowanie odbywa się nawet wtedy, gdy nie zainicjowano certyfikatu serwera i **wymuszania szyfrowania protokołu**  nie został skonfigurowany dla klienta. Jednak jeśli `TrustServerCertificate` nie jest włączone w konfiguracji klienta, certyfikat serwera inicjowana jest nadal wymagane.  
  
 W poniższej tabeli opisano wszystkie przypadki.  
  
|Wymusić ustawienie szyfrowania protokołu klienta|Zaufania ustawienie klienta, certyfikat serwera|Szyfrowanie szyfrowania używany atrybut parametrów połączenia danych|Zaufania atrybut parametrów połączenia certyfikatu serwera|Wynik|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Nie|Brak|(Domyślnie)|Ignorowane|Szyfrowanie nie występuje.|  
|Nie|Brak|Tak|(Domyślnie)|Szyfrowanie występuje tylko wtedy, gdy jest możliwe do zweryfikowania certyfikatu serwera, w przeciwnym razie próba połączenia nie powiedzie się.|  
|Nie|Brak|Tak|Tak|Szyfrowanie występuje tylko wtedy, gdy jest możliwe do zweryfikowania certyfikatu serwera, w przeciwnym razie próba połączenia nie powiedzie się.|  
|Tak|Nie|Ignorowane|Ignorowane|Szyfrowanie występuje tylko wtedy, gdy jest możliwe do zweryfikowania certyfikatu serwera, w przeciwnym razie próba połączenia nie powiedzie się.|  
|Tak|Tak|(Domyślnie)|Ignorowane|Szyfrowanie występuje tylko wtedy, gdy jest możliwe do zweryfikowania certyfikatu serwera, w przeciwnym razie próba połączenia nie powiedzie się.|  
|Tak|Tak|Tak|(Domyślnie)|Szyfrowanie występuje tylko wtedy, gdy jest możliwe do zweryfikowania certyfikatu serwera, w przeciwnym razie próba połączenia nie powiedzie się.|  
|Tak|Tak|Tak|Tak|Szyfrowanie występuje tylko wtedy, gdy jest możliwe do zweryfikowania certyfikatu serwera, w przeciwnym razie próba połączenia nie powiedzie się.|  
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu szyfrowania bez sprawdzania poprawności](http://go.microsoft.com/fwlink/?LinkId=120500) w dokumentacji SQL Server — książki Online.  
  
## <a name="oledb-connection-strings"></a>Parametry połączenia OLE DB  
 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> Właściwość <xref:System.Data.OleDb.OleDbConnection> służy do pobierania lub ustawiania ciągu połączenia dla źródła danych OLE DB, takich jak program Microsoft Access. Można również utworzyć `OleDb` parametry połączenia w czasie wykonywania za pomocą <xref:System.Data.OleDb.OleDbConnectionStringBuilder> klasy.  
  
### <a name="oledb-connection-string-syntax"></a>Składnia ciągu połączenia OLE DB  
 Należy określić nazwę dostawcy <xref:System.Data.OleDb.OleDbConnection> parametry połączenia. Następujący ciąg połączenia łączy się z bazą danych programu Microsoft Access za pomocą dostawcy Jet. Należy pamiętać, że `User ID` i `Password` słowa kluczowe są opcjonalne, jeśli baza danych jest niezabezpieczone (ustawienie domyślne).  
  
```   
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 Jeśli baza danych Jet jest zabezpieczone przy użyciu zabezpieczeń na poziomie użytkownika, należy podać lokalizację pliku (.mdw). Tego pliku jest używany do walidacji poświadczenia podane w parametrach połączenia.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  Można podać informacje o połączeniu **oledbconnection —** w plik Universal Data Link (UDL); jednak należy unikać w ten sposób. Pliki UDL nie są szyfrowane i ujawniać informacje o parametrach połączenia w postaci zwykłego tekstu. Ponieważ plik UDL zewnętrzny zasób opartych na plikach do aplikacji, nie może być chronione przy użyciu programu .NET Framework. Pliki UDL nie są obsługiwane dla **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Aby nawiązać połączenie dostępu/Jet przy użyciu DataDirectory  
 `DataDirectory` nie jest zarezerwowana `SqlClient`. Można go również używać razem <xref:System.Data.OleDb> i <xref:System.Data.Odbc> dostawcy danych .NET. Poniższy przykład <xref:System.Data.OleDb.OleDbConnection> ciąg przedstawia składnię wymagane do nawiązania Northwind.mdb znajduje się w folderze app_data aplikacji. Systemowej bazy danych (grupach) również są przechowywane w tej lokalizacji.  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  Określanie lokalizacji systemowej bazy danych w parametrach połączenia nie jest wymagane, jeśli baza danych programu Access/Jet jest niezabezpieczona. Zabezpieczenia jest domyślnie wyłączona, z wszystkich użytkowników łączących się wbudowanych użytkownika jako administratora przy użyciu pustego hasła. Nawet wtedy, gdy zabezpieczenia na poziomie użytkownika jest poprawnie zaimplementowana, bazy danych Jet pozostaje narażony na ataki. W związku z tym ważne informacje są przechowywane w bazie danych programu Access/Jet nie jest zalecane z powodu związanego z używaniem słabe jego schemat zabezpieczeń opartych na plikach.  
  
### <a name="connecting-to-excel"></a>Łączenie z programu Excel  
 Dostawca Microsoft Jet jest używany do nawiązania połączenia skoroszytu programu Excel. W następujące parametry połączenia `Extended Properties` — słowo kluczowe ustawia właściwości, które są specyficzne dla programu Excel. "HDR = Yes;" wskazuje, że pierwszy wiersz zawiera nazwy kolumn, nie danych i "IMEX = 1;" sterownik zawsze odczytać kolumny danych "mieszany —" jako tekst.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Należy pamiętać, że wymagane podwójnego cudzysłowu dla `Extended Properties` również musi być ujęta w znaki podwójnego cudzysłowu.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Składnia ciągu połączenia dostawcy kształtu danych  
 Korzystanie z obu `Provider` i `Data Provider` słów kluczowych w przypadku korzystania z dostawcy kształtu danych firmy Microsoft. W poniższym przykładzie użyto dostawcy kształtu nawiązać połączenia z lokalnego wystąpienia programu SQL Server.  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>Parametry połączenia ODBC  
 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> Właściwość <xref:System.Data.Odbc.OdbcConnection> służy do pobierania lub ustawiania ciągu połączenia dla źródła danych OLE DB. Parametry połączenia ODBC są również obsługiwane przez <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.  
  
 Następujący ciąg połączenia używa sterownika tekstowego firmy Microsoft.  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Przy użyciu DataDirectory nawiązać połączenia z programem Visual FoxPro  
 Następujące <xref:System.Data.Odbc.OdbcConnection> przedstawiono przykładowy ciąg połączenia przy użyciu `DataDirectory` do łączenia się z plikiem programu Microsoft Visual FoxPro.  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Parametry połączenia Oracle  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Właściwość <xref:System.Data.OracleClient.OracleConnection> służy do pobierania lub ustawiania ciągu połączenia dla źródła danych OLE DB. Parametry połączenia Oracle są również obsługiwane przez <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Aby uzyskać więcej informacji o składni ciągu połączenia ODBC, zobacz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
