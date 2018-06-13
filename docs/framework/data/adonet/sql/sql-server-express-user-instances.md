---
title: Wystąpienia programu SQL Server Express użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: 0af929de17a29d497ce6cf6c8cb055d416ab8761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365413"
---
# <a name="sql-server-express-user-instances"></a>Wystąpienia programu SQL Server Express użytkownika
Microsoft SQL Server Express Edition, (SQL Server Express) obsługuje funkcję wystąpienia użytkownika, który jest dostępny tylko w przypadku używania dostawcy danych programu .NET Framework dla programu SQL Server (`SqlClient`). Wystąpienia użytkownika jest osobnego wystąpienia programu SQL Server Express aparat bazy danych jest generowany przez wystąpienie nadrzędne. Zezwalaj na użytkowników, którzy nie są administratorami na swoich komputerach lokalnych, aby podłączyć się do programu SQL Server Express baz danych, a wystąpienia użytkownika. Każde wystąpienie jest uruchamiany w kontekście zabezpieczeń użytkownika na podstawie jednego wystąpienia na użytkownika.  
  
## <a name="user-instance-capabilities"></a>Możliwości wystąpienia użytkownika  
 Wystąpienia użytkownika są przydatne w przypadku użytkowników, którzy są systemem Windows przy użyciu konta użytkownika o najniższych uprawnieniach (LUA), ponieważ każdy użytkownik ma administrator programu SQL Server (`sysadmin`) uprawnienia w wystąpieniu uruchomiony na komputerze bez konieczności uruchamiania jako systemu Windows Administrator, a także. Oprogramowanie wykonywania w wystąpieniu użytkownika z ograniczonymi uprawnieniami nie można wprowadzić zmiany w całym systemie, ponieważ wystąpienie programu SQL Server Express jest uruchomiona na koncie systemu Windows bez uprawnień administratora, użytkownika, nie jako usługa. Każde wystąpienie użytkownika jest izolowane od jego wystąpienie nadrzędne i z innych wystąpień użytkownika, uruchomionych na tym samym komputerze. Baz danych uruchomionych w wystąpieniu użytkownika są otwierane tylko w trybie jednego użytkownika, a nie jest możliwe w dla wielu użytkowników do nawiązania połączenia baz danych uruchomionych w wystąpieniu użytkownika. Replikacja i zapytań rozproszonych również są wyłączone dla wystąpienia użytkownika.  
  
 Aby uzyskać więcej informacji zobacz "Wystąpień użytkownika" w dokumentacji SQL Server — książki Online.  
  
> [!NOTE]
>  Wystąpienia użytkownika nie są wymagane dla użytkowników, którzy są już administratorami na swoich komputerach lub w scenariuszach obejmujących wiele użytkowników bazy danych.  
  
## <a name="enabling-user-instances"></a>Włączanie wystąpień użytkownika  
 Aby wygenerować wystąpienia użytkownika, musi być uruchomiona nadrzędne wystąpienie programu SQL Server Express. Wystąpienia użytkownika jest włączone domyślnie, gdy SQL Server Express został zainstalowany i może być jawnie włączona lub wyłączona przez administratora systemu wykonywania **sp_configure** procedury składowanej systemu w wystąpieniu nadrzędnej.  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Protokół dla wystąpień użytkownika musi być lokalny potoków nazwanych. Wystąpienia użytkownika nie może zostać uruchomiona na zdalnym wystąpieniu programu SQL Server i logowania do programu SQL Server nie są dozwolone.  
  
## <a name="connecting-to-a-user-instance"></a>Nawiązywanie połączenia z wystąpieniem użytkownika  
 `User Instance` i `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Zezwalaj słowa kluczowe <xref:System.Data.SqlClient.SqlConnection> nawiązywania połączenia z wystąpieniem użytkownika. Wystąpienia użytkownika również są obsługiwane przez <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` i `AttachDBFilename` właściwości.  
  
 Należy pamiętać, że o parametrach połączenia przykładowych pokazano poniżej:  
  
-   `Data Source` — Słowo kluczowe odwołuje się do wystąpienie programu SQL Server Express, który generuje wystąpienia użytkownika. To wystąpienie domyślne. \sqlexpress.  
  
-   `Integrated Security` ustawiono `true`. Aby połączyć się wystąpienia użytkownika, uwierzytelnianie systemu Windows jest wymagana; Logowania do programu SQL Server nie są obsługiwane.  
  
-   `User Instance` Ma ustawioną wartość `true`, który wywołuje wystąpienia użytkownika. (Wartość domyślna to `false`.)  
  
-   `AttachDbFileName` Słowo kluczowe parametrów połączenia jest używany do dołączania plików podstawowej bazy danych (mdf), które musi zawierać pełną nazwę ścieżki. `AttachDbFileName` odpowiada także "rozszerzonych właściwości" i "początkowa nazwa pliku" kluczy w <xref:System.Data.SqlClient.SqlConnection> parametry połączenia.  
  
-   `|DataDirectory|` Ujęta w potoku symbole ciąg podstawienia odwołuje się do katalogu danych aplikacji Otwieranie połączenia i zapewnia ścieżką względną wskazującą lokalizację .mdf i .ldf plików dziennika i bazy danych. Jeśli chcesz zlokalizować tych plików w innym miejscu, należy podać pełną ścieżkę do plików.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> i <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> właściwości, aby utworzyć parametry połączenia w czasie wykonywania.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Przy użyciu &#124;DataDirectory&#124; ciąg podstawienia  
 `AttachDbFileName` został rozszerzony w ADO.NET 2.0 wraz z wprowadzeniem `|DataDirectory|` (ujęta w potoku symbole) ciąg podstawienia. `DataDirectory` jest używany w połączeniu z `AttachDbFileName` wskaż ścieżkę względną do pliku danych, umożliwiające deweloperom tworzenie parametrów połączenia, które są oparte na ścieżkę względną do źródła danych, zamiast trzeba określić pełną ścieżkę.  
  
 Lokalizacji fizycznej który `DataDirectory` wskazuje zależy od typu aplikacji. W tym przykładzie można dołączyć plik Northwind.mdf znajduje się w folderze \app_data aplikacji.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Gdy `DataDirectory` jest używane, ścieżka pliku nie może przekraczać w strukturze katalogów katalog wskazywany przez ciąg podstawienia. Na przykład jeśli pełni rozwinięte `DataDirectory` jest C:\AppDirectory\app_data, a następnie parametry połączenia przykładowych pokazano powyżej działa, ponieważ jest on poniżej c:\AppDirectory. Jednak próby określ `DataDirectory` jako `|DataDirectory|\..\data` spowoduje błąd, ponieważ \data nie jest podkatalogiem katalogu \AppDirectory.  
  
 Jeśli parametry połączenia zawiera ciąg podstawienia niewłaściwie sformatowany <xref:System.ArgumentException> zostanie wygenerowany.  
  
> [!NOTE]
>  <xref:System.Data.SqlClient> rozpoznaje ciągów podstawienia do pełnej ścieżki dla komputera lokalnego systemu plików. W związku z tym serwerem, HTTP i UNC nazw ścieżek nie są obsługiwane. Po otwarciu połączenia, jeśli serwer nie znajduje się na komputerze lokalnym, jest zgłaszany wyjątek.  
  
 Gdy <xref:System.Data.SqlClient.SqlConnection> jest otwarty, nastąpi przekierowanie z domyślnego wystąpienia programu SQL Server Express do działającego wystąpienia inicjowane czasu wykonywania w ramach konta obiektu wywołującego.  
  
> [!NOTE]
>  Może być konieczne w celu zwiększenia <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> wartości, ponieważ wystąpienia użytkownika może trwać dłużej załadować regularne wystąpień.  
  
 Poniższy fragment kodu zostanie otwarty nowy `SqlConnection`, wyświetla parametry połączenia w oknie konsoli, a następnie zamyka połączenie, podczas zamykania `using` blok kodu.  
  
```vb  
Private Sub OpenSqlConnection()  
    ' Retrieve the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Using connection As New SqlConnection(connectionString)  
        connection.Open()  
        Console.WriteLine("ConnectionString: {0}", _  
           connection.ConnectionString)  
    End Using  
End Sub  
```  
  
```csharp  
private static void OpenSqlConnection()  
{  
    // Retrieve the connection string.  
    string connectionString = GetConnectionString();  
  
    using (SqlConnection connection =   
        new SqlConnection(connectionString))  
    {  
        connection.Open();  
        Console.WriteLine("ConnectionString: {0}",   
             connection.ConnectionString);  
    }  
}  
```  
  
> [!NOTE]
>  Wystąpienia użytkownika nie są obsługiwane w typowych kod języka wspólnego (CLR), który jest działają w ramach programu SQL Server. <xref:System.InvalidOperationException> Jest generowany, jeśli `Open` jest wywoływana na <xref:System.Data.SqlClient.SqlConnection> mający `User Instance=true` w parametrach połączenia.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Okres istnienia połączenia wystąpienia użytkownika  
 W przeciwieństwie do wersji programu SQL Server, że uruchomiony jako usługa, wystąpienia programu SQL Server Express nie trzeba ją ręcznie uruchamiania i zatrzymywania. Zawsze użytkownik zaloguje się i łączy się z wystąpieniem użytkownika, wystąpienia użytkownika jest uruchomiony, jeśli nie jest już uruchomiony. Bazy danych wystąpienia użytkownika mają `AutoClose` opcji set, aby bazy danych jest automatycznie zamknięta po okresie braku aktywności. Proces sqlservr.exe, który jest uruchamiany jest przechowywana uruchomiona ograniczone limit czasu po zamknięciu ostatniego połączenia z wystąpieniem, więc nie trzeba ponownie uruchomić komputer w przypadku otwarcia inne połączenie przed upłynął limit czasu. Wystąpienia użytkownika automatycznie zamykany, jeśli nie nowe połączenie zostanie otwarty, zanim ten limit czasu upłynął. Administrator systemu w wystąpieniu nadrzędny można ustawić okres limitu czasu dla wystąpienia użytkownika przy użyciu **sp_configure** zmienić **limitu czasu wystąpienia użytkownika** opcji. Wartość domyślna to 60 minut.  
  
> [!NOTE]
>  Jeśli `Min Pool Size` jest używany w parametrach połączenia o wartości większej od zera, pulę połączeń zawsze będzie utrzymywać otwarte połączenia kilku i wystąpienia użytkownika nie zostanie automatycznie zamknięty.  
  
## <a name="how-user-instances-work"></a>Jak użytkownika wystąpienia pracy  
 Podczas pierwszego wystąpienia użytkownika jest generowany dla każdego użytkownika **wzorca** i **msdb** systemowych baz danych są kopiowane z folderu danych szablon do ścieżki w repozytorium danych lokalnych aplikacji użytkownika katalog do wyłącznego użytku przez wystąpienie użytkownika. Ta ścieżka jest zwykle `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Podczas uruchamiania wystąpienia użytkownika, **tempdb**dziennika i śledzenia pliki są także zapisywane do tego katalogu. Nazwa jest generowany dla tego wystąpienia jest musi być unikatowy dla każdego użytkownika.  
  
 Domyślnie wszyscy członkowie grupy BUILTIN\Użytkownicy systemu Windows są przyznawane uprawnienia do połączenia w lokalnym wystąpieniu, a także uprawnienia Odczyt i wykonywanie na pliki binarne programu SQL Server. Po zweryfikowaniu poświadczeń użytkownika wywołującego hosting wystąpienia użytkownika staje się `sysadmin` w tym wystąpieniu. Tylko pamięci współużytkowanej jest włączone dla wystąpień użytkownika, co oznacza, że tylko operacje na komputerze lokalnym są możliwe.  
  
 Użytkownicy muszą mieć uprawnienie odczytu i zapisu uprawnienia do plików .mdf i .ldf określone w parametrach połączenia.  
  
> [!NOTE]
>  Pliki .mdf i .ldf odpowiednio reprezentują pliki dziennika i bazy danych. Te dwa pliki są zestaw dopasowane tak szczególną uwagę należy podjąć podczas tworzenia kopii zapasowej i przywracanie operacji. Plik bazy danych zawiera informacje o dokładnej wersji pliku dziennika i bazy danych nie zostanie otwarty, jeśli jest sprzężona z niewłaściwego pliku dziennika.  
  
 Aby uniknąć uszkodzenia danych, bazy danych w wystąpieniu użytkownika jest otwarty z wyłącznego dostępu. Jeśli dwa wystąpienia inny użytkownik korzystać z tej samej bazy danych na tym samym komputerze, użytkownik w pierwszym wystąpieniu zamknąć bazy danych, aby można go otworzyć w drugie wystąpienie.  
  
## <a name="user-instance-scenarios"></a>Scenariusze wystąpienia użytkownika  
 Wystąpienia użytkownika dostarczyć deweloperom aplikacji baz danych z magazynem danych programu SQL Server, które nie są zależne od deweloperów o kontach z uprawnieniami administracyjnymi na swoich komputerach programowanie. Wystąpienia użytkownika są oparte na modelu dostępu/Jet, gdzie aplikacji bazy danych po prostu łączy do pliku, a użytkownik automatycznie ma pełne uprawnienia do wszystkich obiektów bazy danych bez konieczności interwencji administratora systemu, aby udzielić uprawnienia. Jest on przeznaczony do pracy w sytuacji, gdy użytkownik działa w ramach konta użytkownika o najniższych uprawnieniach (LUA) i nie ma uprawnienia administracyjne na serwerze lub komputerze lokalnym, ale musi utworzyć obiekty bazy danych i aplikacji. Wystąpienia użytkownika Zezwalaj użytkownikom na tworzenie wystąpień w czasie wykonywania, które są uruchamiane w kontekście zabezpieczeń przez użytkownika, a nie w kontekście zabezpieczeń bardziej uprzywilejowanego usługi system.  
  
> [!IMPORTANT]
>  Wystąpienia użytkownika należy używać tylko w scenariuszach, w których wszystkie aplikacje przy użyciu jego są całkowicie zaufanych.  
  
 Scenariusze wystąpienia użytkownika:  
  
-   Dowolnej aplikacji pojedynczego użytkownika, których udostępnianie danych nie jest wymagane.  
  
-   Wdrożenie ClickOnce. .NET Framework 2.0 (lub nowszej) i programu SQL Server Express są już zainstalowane na komputerze docelowym, pakiet instalacyjny pobrane wyniku akcji ClickOnce można instalować i używane przez użytkowników niebędących administratorami. Należy pamiętać, że dla administrator musi zainstalować programu SQL Server Express, jeżeli jest to część instalacji. Aby uzyskać więcej informacji, zobacz [ClickOnce wdrożenia dla aplikacji systemu Windows Forms](http://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df).  
  
-   W dedykowanym hostingu ASP.NET przy użyciu uwierzytelniania systemu Windows. Pojedyncze wystąpienie programu SQL Server Express może być hostowana w sieci intranet. Aplikacja nawiązuje połączenie przy użyciu konta systemu Windows ASPNET nie przy użyciu personifikacji. Wystąpienia użytkownika nie można używać dla innych firm lub udostępnionego hosting scenariuszy, w którym wszystkie aplikacje czy współużytkują to samo wystąpienie użytkownika nie jest już pozostać odizolowane od siebie.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Parametry połączeń](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [Nawiązywanie połączenia ze źródłem danych](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
