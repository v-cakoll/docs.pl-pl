---
title: Składnia parametrów połączenia
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 3df97419391fe17ef77a3b8f24c4f0689a04602f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151653"
---
# <a name="connection-string-syntax"></a>Składnia parametrów połączenia
Każdy dostawca danych platformy `Connection` .NET Framework <xref:System.Data.Common.DbConnection> ma obiekt, który <xref:System.Data.Common.DbConnection.ConnectionString%2A> dziedziczy z, a także właściwość specyficzne dla dostawcy. Składnia określonego ciągu połączenia dla każdego dostawcy `ConnectionString` jest udokumentowana w jego właściwości. W poniższej tabeli wymieniono czterech dostawców danych, które są zawarte w .NET Framework.  
  
|Dostawca danych programu .NET Framework|Opis|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Zapewnia dostęp do danych dla programu Microsoft SQL Server. Aby uzyskać więcej informacji na temat <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>składni ciągu połączenia, zobacz .|  
|<xref:System.Data.OleDb>|Zapewnia dostęp do danych dla źródeł danych narażonych przy użyciu ole DB. Aby uzyskać więcej informacji na temat <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>składni ciągu połączenia, zobacz .|  
|<xref:System.Data.Odbc>|Zapewnia dostęp do danych dla źródeł danych narażonych przy użyciu ODBC. Aby uzyskać więcej informacji na temat <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>składni ciągu połączenia, zobacz .|  
|<xref:System.Data.OracleClient>|Zapewnia dostęp do danych dla oracle w wersji 8.1.7 lub nowszej. Aby uzyskać więcej informacji na temat <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>składni ciągu połączenia, zobacz .|  
  
## <a name="connection-string-builders"></a>Konstruktorzy parametrów połączeń  
 ADO.NET 2.0 wprowadzono następujące konstruktorów ciągów połączeń dla dostawców danych .NET Framework.  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Konstruktorzy ciągów połączeń umożliwiają konstruowanie syntaktycznie prawidłowych ciągów połączeń w czasie wykonywania, więc nie trzeba ręcznie łączyć wartości ciągu połączenia w kodzie. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączeń](connection-string-builders.md).  

## <a name="windows-authentication"></a>Uwierzytelnianie systemu Windows  
 Zalecamy łączenie się ze źródłami danych, które go obsługują, zaleca się używanie uwierzytelniania systemu Windows (czasami nazywanego *jako zintegrowane zabezpieczenia).* Składnia zastosowana w ciągu połączenia różni się w zależności od dostawcy. W poniższej tabeli przedstawiono składnię uwierzytelniania systemu Windows używaną z dostawcami danych programu .NET Framework.  
  
|Dostawca|Składnia|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> `Integrated Security=true`zgłasza wyjątek, gdy `OleDb` jest używany z dostawcą.  
  
## <a name="sqlclient-connection-strings"></a>Parametry połączenia SqlClient  
Składnia ciągu <xref:System.Data.SqlClient.SqlConnection> połączenia jest udokumentowana we <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> właściwości. Właściwości można <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> użyć, aby uzyskać lub ustawić parametry połączenia dla bazy danych programu SQL Server. Jeśli chcesz połączyć się z wcześniejszą wersją programu SQL Server, należy<xref:System.Data.OleDb>użyć dostawcy danych programu .NET Framework dla oledb ( ). Większość słów kluczowych ciągu połączenia również <xref:System.Data.SqlClient.SqlConnectionStringBuilder>mapować do właściwości w .  

> [!IMPORTANT]
> Domyślnym ustawieniem `Persist Security Info` słowa `false`kluczowego jest . Ustawienie `true` lub `yes` umożliwia uzyskanie informacji wrażliwych na zabezpieczenia, w tym identyfikatora użytkownika i hasła, z połączenia po otwarciu połączenia. Ustaw, `Persist Security Info` `false` aby upewnić się, że niezaufane źródło nie ma dostępu do poufnych informacji o ciągu połączenia.  

### <a name="windows-authentication-with-sqlclient"></a>Uwierzytelnianie systemu Windows za pomocą aplikacji SqlClient
 Każda z poniższych form składni używa uwierzytelniania systemu Windows do łączenia się z bazą danych **AdventureWorks** na serwerze lokalnym.  
  
```csharp  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>Uwierzytelnianie programu SQL Server za pomocą aplikacji SqlClient
 Uwierzytelnianie systemu Windows jest preferowane do łączenia się z programem SQL Server. Jeśli jednak wymagane jest uwierzytelnianie programu SQL Server, należy użyć następującej składni, aby określić nazwę użytkownika i hasło. W tym przykładzie gwiazdki są używane do reprezentowania prawidłowej nazwy użytkownika i hasła.  
  
```csharp  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Po nawiązaniu połączenia z usługą Azure SQL Database lub `user@servername`usługi Azure `servername` SQL Data Warehouse i podaniu loginu w formacie upewnij się, że wartość w logowaniu jest zgodna z wartością podana dla `Server=`.

> [!NOTE]
> Uwierzytelnianie systemu Windows ma pierwszeństwo przed logowaniami programu SQL Server. Jeśli określisz zarówno Integrated Security=true, jak również nazwę użytkownika i hasło, nazwa użytkownika i hasło zostaną zignorowane i zostanie użyte uwierzytelnienie systemu Windows.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Łączenie się z nazwanym wystąpieniem programu SQL Server
Aby połączyć się z nazwanym wystąpieniem programu SQL Server, użyj składni *nazwa serwera\nazwa wystąpienia.*  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

Można również ustawić <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> właściwość `SqlConnectionStringBuilder` nazwy wystąpienia podczas tworzenia ciągu połączenia. Właściwość <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> <xref:System.Data.SqlClient.SqlConnection> obiektu jest tylko do odczytu.  
  
### <a name="type-system-version-changes"></a>Wpisz zmiany wersji systemu  
 Słowo `Type System Version` kluczowe <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> w a określa reprezentację po stronie klienta typów programu SQL Server. Zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> więcej informacji `Type System Version` na temat słowa kluczowego.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Łączenie i dołączanie do wystąpień użytkowników programu SQL Server Express  
 Wystąpienia użytkowników są funkcją w programie SQL Server Express. Umożliwiają one użytkownikowi działającemu na najmniej uprzywilejowanym lokalnym koncie systemu Windows dołączanie i uruchamianie bazy danych programu SQL Server bez konieczności posiadania uprawnień administracyjnych. Wystąpienie użytkownika jest wykonywane przy użyciu poświadczeń systemu Windows użytkownika, a nie jako usługa.  
  
 Aby uzyskać więcej informacji na temat pracy z wystąpieniami użytkowników, zobacz [Wystąpienia użytkowników programu SQL Server Express](./sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Korzystanie z certyfikatu TrustServerCertificate  
 Słowo `TrustServerCertificate` kluczowe jest prawidłowe tylko podczas łączenia się z wystąpieniem programu SQL Server z prawidłowym certyfikatem. Gdy `TrustServerCertificate` jest `true`ustawiona na , warstwa transportu użyje SSL do szyfrowania kanału i pomijania przechodzenia łańcucha certyfikatów w celu sprawdzenia poprawności zaufania.  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> Jeśli `TrustServerCertificate` jest `true` ustawiona i szyfrowanie jest włączone, poziom szyfrowania `Encrypt` określony na `false` serwerze będzie używany, nawet jeśli jest ustawiony na w ciągu połączenia. Połączenie zakończy się niepowodzeniem w przeciwnym razie.  
  
### <a name="enabling-encryption"></a>Włączanie szyfrowania  
 Aby włączyć szyfrowanie, gdy certyfikat nie został aprowizny na serwerze, w programie SQL Server Configuration Manager należy ustawić opcje **Szyfrowanie protokołu wymuszania** i **certyfikat serwera zaufania.** W takim przypadku szyfrowanie będzie używać certyfikatu serwera z podpisem własnym bez sprawdzania poprawności, jeśli na serwerze nie został aprowizny żaden zweryfikowany certyfikat.  
  
 Ustawienia aplikacji nie mogą zmniejszyć poziomu zabezpieczeń skonfigurowanego w programie SQL Server, ale mogą opcjonalnie je wzmocnić. Aplikacja może zażądać `TrustServerCertificate` szyfrowania, ustawiając słowa kluczowe i `Encrypt` na `true`, gwarantując, że szyfrowanie odbywa się nawet wtedy, gdy certyfikat serwera nie został aprowizny i **szyfrowanie wymuszania protokołu** nie zostało skonfigurowane dla klienta. Jeśli jednak `TrustServerCertificate` nie jest włączona w konfiguracji klienta, certyfikat aprowizowanego serwera jest nadal wymagany.  
  
 W poniższej tabeli opisano wszystkie przypadki.  
  
|Wymuszanie ustawienia klienta szyfrowania protokołu|Ustawienie klienta certyfikatu serwera zaufania|Szyfruj/używaj szyfrowania dla ciągu/atrybutu połączenia danych|Parametry/atrybut połączenia certyfikatu serwera zaufania|Wynik|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Nie|Nie dotyczy|Nie (domyślnie)|Ignorowane|Nie występuje szyfrowanie.|  
|Nie|Nie dotyczy|Tak|Nie (domyślnie)|Szyfrowanie odbywa się tylko wtedy, gdy istnieje sprawdzalny certyfikat serwera, w przeciwnym razie próba połączenia nie powiedzie się.|  
|Nie|Nie dotyczy|Tak|Tak|Szyfrowanie zawsze występuje, ale może używać certyfikatu serwera z podpisem własnym.|  
|Tak|Nie|Ignorowane|Ignorowane|Szyfrowanie odbywa się tylko wtedy, gdy istnieje sprawdzalny certyfikat serwera; w przeciwnym razie próba połączenia zakończy się niepowodzeniem.|  
|Tak|Tak|Nie (domyślnie)|Ignorowane|Szyfrowanie zawsze występuje, ale może używać certyfikatu serwera z podpisem własnym.|  
|Tak|Tak|Tak|Nie (domyślnie)|Szyfrowanie odbywa się tylko wtedy, gdy istnieje sprawdzalny certyfikat serwera; w przeciwnym razie próba połączenia zakończy się niepowodzeniem.|  
|Tak|Tak|Tak|Tak|Szyfrowanie zawsze występuje, ale może używać certyfikatu serwera z podpisem własnym.|  
  
 Aby uzyskać więcej informacji, zobacz [Używanie szyfrowania bez sprawdzania poprawności](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>Parametry połączenia OleDb  
 Właściwość <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> a <xref:System.Data.OleDb.OleDbConnection> umożliwia uzyskanie lub ustawienie ciągu połączenia dla źródła danych OLE DB, takiego jak Microsoft Access. Można również utworzyć `OleDb` parametry połączenia w czasie <xref:System.Data.OleDb.OleDbConnectionStringBuilder> wykonywania przy użyciu klasy.  
  
### <a name="oledb-connection-string-syntax"></a>Składnia ciągu połączenia OleDb  
 Należy określić nazwę dostawcy <xref:System.Data.OleDb.OleDbConnection> dla ciągu połączenia. Poniższy parametry połączenia łączą się z bazą danych programu Microsoft Access przy użyciu dostawcy jet. Należy zauważyć, że `User ID` i `Password` słowa kluczowe są opcjonalne, jeśli baza danych jest niezabezpieczona (domyślnie).  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;
```  
  
 Jeśli baza danych Jet jest zabezpieczona przy użyciu zabezpieczeń na poziomie użytkownika, należy podać lokalizację pliku informacyjnego grupy roboczej (mdw). Plik informacji grupy roboczej służy do sprawdzania poprawności poświadczeń przedstawionych w ciągu połączenia.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> Możliwe jest podanie informacji o połączeniu dla **OleDbConnection** w pliku Uniwersalnego łącza danych (UDL); jednak należy tego unikać. Pliki UDL nie są szyfrowane i ujawniają informacje o ciągu połączenia w postaci zwykłego tekstu. Ponieważ plik UDL jest zewnętrznym zasobem opartym na plikach dla aplikacji, nie można go zabezpieczyć za pomocą programu .NET Framework. Pliki UDL nie są obsługiwane dla **sqlclient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Łączenie się z programem Access/Jet za pomocą programu DataDirectory  
 `DataDirectory`nie jest `SqlClient`wyłączną tylko dla . Może być również używany <xref:System.Data.OleDb> <xref:System.Data.Odbc> z dostawcami danych i .NET. Poniższy <xref:System.Data.OleDb.OleDbConnection> przykładowy ciąg pokazuje składnię wymaganą do połączenia z northwind.mdb znajdującą się w folderze app_data aplikacji. Baza danych systemu (System.mdw) jest również przechowywana w tej lokalizacji.  
  
```csharp  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> Określenie lokalizacji bazy danych systemu w ciągu połączenia nie jest wymagane, jeśli baza danych programu Access/Jet jest niezabezpieczona. Zabezpieczenia są domyślnie wyłączone, a wszyscy użytkownicy łączą się jako wbudowany użytkownik administratora z pustym hasłem. Nawet wtedy, gdy zabezpieczenia na poziomie użytkownika jest poprawnie zaimplementowane, baza danych Jet pozostaje narażony na ataki. W związku z tym przechowywanie poufnych informacji w bazie danych programu Access/Jet nie jest zalecane ze względu na nieodłączną słabość jego schemat zabezpieczeń oparty na plikach.  
  
### <a name="connecting-to-excel"></a>Łączenie się z programem Excel  
 Dostawca microsoft jet służy do łączenia się ze skoroszytem programu Excel. W poniższym ciągu `Extended Properties` połączenia słowo kluczowe ustawia właściwości, które są specyficzne dla programu Excel. "HDR=Tak;" wskazuje, że pierwszy wiersz zawiera nazwy kolumn, a nie dane, a "IMEX=1;" informuje kierowcę, aby zawsze odczytywał kolumny danych "intermixed" jako tekst.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Należy zauważyć, że znak cudzysłowu wymaganego dla znaku `Extended Properties` ofertowego musi być również ujęty w znaki cudzysłowu.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Składnia ciągu połączenia dostawcy kształtu danych  
 Podczas korzystania `Provider` z `Data Provider` dostawcy kształtu danych firmy Microsoft należy używać zarówno słów kluczowych, jak i słów kluczowych. W poniższym przykładzie użyto dostawcy kształtu do łączenia się z lokalnym wystąpieniem programu SQL Server.  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"
```  
  
## <a name="odbc-connection-strings"></a>Parametry połączenia Odbc  
 Właściwość <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> a <xref:System.Data.Odbc.OdbcConnection> umożliwia uzyskanie lub ustawienie ciągu połączenia dla źródła danych OLE DB. Parametry połączenia Odbc są również <xref:System.Data.Odbc.OdbcConnectionStringBuilder>obsługiwane przez plik .  
  
 Poniższy parametry połączenia używają sterownika tekstu firmy Microsoft.  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Łączenie się z programem Visual FoxPro za pomocą programu DataDirectory  
 Poniższy <xref:System.Data.Odbc.OdbcConnection> przykład ciągu połączenia `DataDirectory` pokazuje, za pomocą do łączenia się z plikiem Programu Microsoft Visual FoxPro.  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Parametry połączenia Oracle  
 Właściwość <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> a <xref:System.Data.OracleClient.OracleConnection> umożliwia uzyskanie lub ustawienie ciągu połączenia dla źródła danych OLE DB. Parametry połączenia Oracle są również <xref:System.Data.OracleClient.OracleConnectionStringBuilder> obsługiwane przez plik .  
  
```csharp
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Aby uzyskać więcej informacji na temat składni ciągu połączenia ODBC, zobacz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Zobacz też

- [Parametry połączenia](connection-strings.md)
- [Łączenie się ze źródłem danych](connecting-to-a-data-source.md)
- [Omówienie ADO.NET](ado-net-overview.md)
