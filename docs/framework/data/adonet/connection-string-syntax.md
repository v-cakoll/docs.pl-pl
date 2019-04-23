---
title: Składnia parametrów połączenia
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 4c5ed5000f075fb637915dc40e122a9337176e36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084971"
---
# <a name="connection-string-syntax"></a>Składnia parametrów połączenia
Każdy dostawca danych .NET Framework ma `Connection` obiektu, który dziedziczy z <xref:System.Data.Common.DbConnection> oraz specyficzne dla dostawcy <xref:System.Data.Common.DbConnection.ConnectionString%2A> właściwości. Składnia ciągu połączenia określone dla każdego dostawcy jest udokumentowany w jego `ConnectionString` właściwości. W poniższej tabeli wymieniono dostawców cztery danych, które są zawarte w .NET Framework.  
  
|Dostawca danych .NET framework|Opis|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Zapewnia dostęp do danych programu Microsoft SQL Server. Aby uzyskać więcej informacji na temat składnia ciągu połączenia, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|Zapewnia dostęp do danych dla źródeł danych uwidaczniane za pomocą OLE DB. Aby uzyskać więcej informacji na temat składnia ciągu połączenia, zobacz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|Zapewnia dostęp do danych dla źródła danych dostępne za pośrednictwem sterownika ODBC. Aby uzyskać więcej informacji na temat składnia ciągu połączenia, zobacz <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Zapewnia dostęp do danych na oprogramowanie Oracle w wersji 8.1.7 lub nowszej. Aby uzyskać więcej informacji na temat składnia ciągu połączenia, zobacz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Konstruktorzy parametrów połączeń  
 ADO.NET w wersji 2.0 wprowadzono następujące Konstruktorzy parametrów połączenia dla dostawcy danych .NET Framework.  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Konstruktorzy parametrów połączeń pozwalają utworzyć parametry połączenia nieprawidłową składnię w czasie wykonywania, dzięki czemu nie trzeba ręcznie połączyć wartości ciągu połączenia w kodzie. Aby uzyskać więcej informacji, zobacz [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md).  

## <a name="windows-authentication"></a>Uwierzytelnianie systemu Windows  
 Firma Microsoft zaleca używanie uwierzytelniania Windows (czasami określane jako *zintegrowane zabezpieczenia*) do łączenia ze źródłami danych, które go obsługują. Składnia zatrudnionych w parametrach połączenia jest zależna od dostawcy. W poniższej tabeli przedstawiono składnię uwierzytelniania Windows używana z dostawcy danych .NET Framework.  
  
|Dostawca|Składnia|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  `Integrated Security=true` zgłasza wyjątek, gdy jest używane z `OleDb` dostawcy.  
  
## <a name="sqlclient-connection-strings"></a>Parametry połączeń klient SQL  
Składnia <xref:System.Data.SqlClient.SqlConnection> ciąg połączenia jest udokumentowany w <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> właściwości. Możesz użyć <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> właściwość, aby pobrać lub ustawić parametry połączenia dla bazy danych programu SQL Server. Jeśli potrzebujesz nawiązać połączenia z wcześniejszej wersji programu SQL Server, należy użyć .NET Framework Data Provider for OLE DB (<xref:System.Data.OleDb>). Większość słów kluczowych ciągów połączenia również mapować do właściwości w <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  

> [!IMPORTANT]
>  Ustawieniem domyślnym dla `Persist Security Info` słowo kluczowe jest `false`. Ustawienie `true` lub `yes` umożliwia informacje związane z zabezpieczeniami, w tym identyfikator użytkownika i hasło, które mają zostać uzyskane z połączenia po otwarciu połączenia. Zachowaj `Persist Security Info` równa `false` aby upewnić się, że niezaufanego źródła nie ma dostępu do informacji o parametrach połączenia poufnych.  

### <a name="windows-authentication-with-sqlclient"></a>Uwierzytelnianie Windows za pomocą SqlClient 
 Każdy z poniższych form składni korzysta z uwierzytelniania Windows połączyć się z **AdventureWorks** bazy danych na serwerze lokalnym.  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>Uwierzytelnianie programu SQL Server przy użyciu SqlClient   
 Uwierzytelnianie Windows jest preferowane w przypadku łączenia się z serwerem SQL. Jednak jeśli wymagane jest uwierzytelnianie programu SQL Server, należy użyć następującej składni, aby określić nazwę użytkownika i hasło. W tym przykładzie gwiazdka są używane do reprezentowania prawidłową nazwę użytkownika i hasło.  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Podczas łączenia się z bazą danych SQL Azure lub usługi Azure SQL Data Warehouse i udostępniania funkcji logowania w formacie `user@servername`, upewnij się, że `servername` wartości Nazwa logowania jest zgodna wartość podana dla `Server=`.

> [!NOTE]
>  Uwierzytelnianie Windows mają pierwszeństwo przed logowania programu SQL Server. Jeśli określisz zarówno zabezpieczenia zintegrowane = true, oraz nazwę użytkownika i hasło, nazwę użytkownika i hasło zostaną zignorowane i zostanie użyte uwierzytelnianie Windows.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Łączenie się z nazwanym wystąpieniem programu SQL Server
Aby nawiązać połączenie nazwane wystąpienie programu SQL Server, należy użyć *nazwa komputera\nazwa wystąpienia serwera* składni.  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
Można również ustawić <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> właściwość `SqlConnectionStringBuilder` do nazwy obiektu podczas kompilowania parametrów połączenia. <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> Właściwość <xref:System.Data.SqlClient.SqlConnection> obiekt jest tylko do odczytu.  
  
### <a name="type-system-version-changes"></a>Zmiana wersji systemu typu  
 `Type System Version` — Słowo kluczowe w <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> określa reprezentację po stronie klienta typów programu SQL Server. Zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> Aby uzyskać więcej informacji na temat `Type System Version` — słowo kluczowe.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Łączenie i dołączanie do programu SQL Server Express wystąpień użytkownika  
 Wystąpienia użytkownika są funkcją programu SQL Server Express. Umożliwiają one użytkownika w systemie najmniej uprzywilejowane konto lokalne Windows do dołączenia i korzystać z bazy danych programu SQL Server bez wymogu posiadania uprawnień administracyjnych. Wystąpienia użytkownika wykonuje się przy użyciu poświadczeń Windows użytkownika, nie jako usługa.  
  
 Aby uzyskać więcej informacji na temat pracy z wystąpień użytkownika, zobacz [wystąpienia programu SQL Server Express użytkownika](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Za pomocą TrustServerCertificate  
 `TrustServerCertificate` — Słowo kluczowe jest prawidłowa tylko wtedy, gdy nawiązywania połączenia z wystąpieniem programu SQL Server z prawidłowym certyfikatem. Gdy `TrustServerCertificate` ustawiono `true`, warstwy transportowej będą używać protokołu SSL do szyfrowania kanału i pominąć zalet łańcucha certyfikatów w celu zweryfikowania relacji zaufania.  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  Jeśli `TrustServerCertificate` ustawiono `true` i szyfrowanie jest włączone, poziom szyfrowania określonych na serwerze, który będzie używany nawet wtedy, gdy `Encrypt` ustawiono `false` w parametrach połączenia. Połączenie zakończy się niepowodzeniem, w przeciwnym razie.  
  
### <a name="enabling-encryption"></a>Włączanie szyfrowania  
 Aby włączyć szyfrowanie, gdy nie zainicjowano certyfikat na serwerze **Wymuszaj szyfrowanie protokołu** i **certyfikat serwera zaufania** opcje muszą być ustawione w programie SQL Server Configuration Manager. W tym przypadku szyfrowania będzie używany certyfikat serwera z podpisem własnym bez sprawdzania poprawności, jeśli został aprowizowany ma możliwe do zweryfikowania certyfikatu na serwerze.  
  
 Ustawienia aplikacji nie można zmniejszyć poziom zabezpieczeń skonfigurowana w programie SQL Server, ale Opcjonalnie można zwiększanie. Aplikacja może zażądać szyfrowania, ustawiając `TrustServerCertificate` i `Encrypt` słów kluczowych `true`, gwarantując, że szyfrowanie odbywa się nawet wtedy, gdy nie zainicjowano certyfikat serwera i **Wymuszaj szyfrowanie protokołu**  nie został skonfigurowany dla klienta. Jednak jeśli `TrustServerCertificate` nie jest włączone w konfiguracji klienta jest nadal wymagany certyfikat serwera elastycznie.  
  
 W poniższej tabeli opisano wszystkie przypadki.  
  
|Wymusić ustawienie klienta protokołu szyfrowania|Ustawienie klienta, certyfikat serwera zaufania|Szyfrowanie/Szyfrowanie dla atrybut parametrów połączenia danych|Atrybut parametrów połączenia certyfikat serwera zaufania|Wynik|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Nie|Brak|Nie (ustawienie domyślne)|Ignorowane|Szyfrowanie nie występuje.|  
|Nie|Brak|Tak|Nie (ustawienie domyślne)|Szyfrowanie występuje tylko wtedy, gdy możliwe do zweryfikowania certyfikatu serwera, w przeciwnym razie próba połączenia nie powiedzie się.|  
|Nie|Brak|Tak|Tak|Szyfrowanie zawsze występuje, ale może być używany certyfikat serwera z podpisem własnym.|  
|Tak|Nie|Ignorowane|Ignorowane|Szyfrowanie występuje tylko wtedy, gdy znajduje się certyfikat serwera weryfikowalny; w przeciwnym razie próba połączenia kończy się niepowodzeniem.|  
|Yes|Tak|Nie (ustawienie domyślne)|Ignorowane|Szyfrowanie zawsze występuje, ale może być używany certyfikat serwera z podpisem własnym.|  
|Tak|Yes|Tak|Nie (ustawienie domyślne)|Szyfrowanie występuje tylko wtedy, gdy znajduje się certyfikat serwera weryfikowalny; w przeciwnym razie próba połączenia kończy się niepowodzeniem.|  
|Tak|Yes|Yes|Yes|Szyfrowanie zawsze występuje, ale może być używany certyfikat serwera z podpisem własnym.|  
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu szyfrowania bez sprawdzania poprawności](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>Parametry połączenia OleDb  
 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> Właściwość <xref:System.Data.OleDb.OleDbConnection> pozwala pobrać lub ustawić parametry połączenia dla źródła danych OLE DB, takie jak program Microsoft Access. Można również utworzyć `OleDb` parametry połączenia w czasie wykonywania za pomocą <xref:System.Data.OleDb.OleDbConnectionStringBuilder> klasy.  
  
### <a name="oledb-connection-string-syntax"></a>Składnia ciągu połączenia OleDb  
 Należy określić nazwę dostawcy <xref:System.Data.OleDb.OleDbConnection> parametry połączenia. Łączy następujące parametry połączenia bazy danych Microsoft Access za pomocą dostawcy Jet. Należy pamiętać, że `User ID` i `Password` słowa kluczowe są opcjonalne, jeśli baza danych jest niezabezpieczone (ustawienie domyślne).  
  
```   
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 Jeśli bazy danych Jet jest zabezpieczony za pomocą zabezpieczeń na poziomie użytkownika, należy podać lokalizację pliku (.mdw). Plik informacji o grupie roboczej jest używany do walidacji poświadczenia znajdujące się w ciągu połączenia.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  Jest to możliwe, aby podać informacje o połączeniu dla **oledbconnection —** w plik Universal Data Link (UDL); jednak należy unikać sposób. Pliki UDL nie są szyfrowane, a następnie udostępnić informacje o parametrach połączenia w postaci zwykłego tekstu. Ponieważ plik UDL zewnętrznego zasobu opartych na plikach do aplikacji, nie może być chronione przy użyciu programu .NET Framework. Pliki UDL nie są obsługiwane dla **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Aby nawiązać połączenie dostępu/Jet przy użyciu DataDirectory  
 `DataDirectory` nie jest dostępna wyłącznie dla `SqlClient`. Może również służyć za pomocą <xref:System.Data.OleDb> i <xref:System.Data.Odbc> dostawcy danych .NET. Poniższy przykład <xref:System.Data.OleDb.OleDbConnection> ciągu pokazuje składnię wymagane do nawiązania Northwind.mdb znajdujący się w folderze app_data aplikacji. Systemowej bazy danych (grupach) również są przechowywane w tej lokalizacji.  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  Określanie lokalizacji systemowej bazy danych w parametrach połączenia nie jest wymagane, jeśli baza danych programu Access/Jet jest niezabezpieczona. Zabezpieczenia jest domyślnie wyłączona, za pomocą wszystkich użytkowników łączących się wbudowane użytkownika jako administratora przy użyciu pustego hasła. Nawet wtedy, gdy zabezpieczenia na poziomie użytkownika jest implementowana prawidłowo, bazy danych Jet pozostają narażone na ataki. W związku z tym przechowywanie poufnych informacji w bazie danych programu Access/Jet nie jest zalecana ze względu na słabe nieprzerwaną pracę jego schemat zabezpieczeń opartych na plikach.  
  
### <a name="connecting-to-excel"></a>Nawiązywanie połączenia z programu Excel  
 Dostawca Microsoft Jet jest używany do łączenia się ze skoroszytem programu Excel. W poniższym ciągu połączenia `Extended Properties` — słowo kluczowe ustawia właściwości, które są specyficzne dla programu Excel. "HDR = Yes;" wskazuje, że pierwszy wiersz zawiera nazwy kolumn, nie dane, i "IMEX = 1;" sterownik zawsze przeczytać kolumn danych "mieszany —" jako tekst.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Należy zauważyć, że wymagany znak cudzysłowu dla `Extended Properties` również muszą być ujęte w podwójny cudzysłów.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Składnia ciągu połączenia dostawcy kształtu danych  
 Korzystanie z obu `Provider` i `Data Provider` słów kluczowych, gdy za pomocą dostawcy kształt danych firmy Microsoft. W poniższym przykładzie użyto dostawcy kształtu do łączenia z lokalnym wystąpieniem programu SQL Server.  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>Parametry połączenia ODBC  
 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> Właściwość <xref:System.Data.Odbc.OdbcConnection> pozwala pobrać lub ustawić parametry połączenia dla źródła danych OLE DB. Parametry połączenia ODBC są również obsługiwane przez <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.  
  
 Następujące parametry połączenia używa sterownika Microsoft tekstu.  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Za pomocą DataDirectory nawiązać połączenia z programem Visual FoxPro  
 Następujące <xref:System.Data.Odbc.OdbcConnection> przykładowy ciąg połączenia, który demonstruje sposób użycia `DataDirectory` do łączenia się z plikiem programu Microsoft Visual FoxPro.  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Parametry połączenia bazy danych Oracle  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Właściwość <xref:System.Data.OracleClient.OracleConnection> pozwala pobrać lub ustawić parametry połączenia dla źródła danych OLE DB. Parametry połączenia bazy danych Oracle, są również obsługiwane przez <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Aby uzyskać więcej informacji na temat składnia ciągu połączenia ODBC, zobacz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)
- [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
