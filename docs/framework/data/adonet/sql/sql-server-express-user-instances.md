---
title: Wystąpienia użytkownika programu SQL Server Express
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: b456549daefa0fdf67524b0b039a091652cf41ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876281"
---
# <a name="sql-server-express-user-instances"></a>Wystąpienia użytkownika programu SQL Server Express
Microsoft SQL Server Express Edition, (SQL Server Express) obsługuje funkcję wystąpienia użytkownika, który jest dostępny tylko w przypadku używania dostawcy danych .NET Framework dla programu SQL Server (`SqlClient`). Wystąpienia użytkownika jest osobnego wystąpienia programu SQL Server Express aparatu bazy danych generowanych przez wystąpienie nadrzędne. Wystąpienia użytkownika umożliwiają użytkownikom niebędącym administratorami na swoich komputerach lokalnych do dołączenia i nawiązać połączenie z SQL Server Express bazy danych. Każde wystąpienie jest uruchamiany w kontekście zabezpieczeń użytkownika, na podstawie jednego wystąpienia na użytkownika.  
  
## <a name="user-instance-capabilities"></a>Możliwości wystąpienia użytkownika  
 Wystąpienia użytkownika są przydatne w przypadku użytkowników, którzy są systemem Windows przy użyciu konta użytkownika o najniższych uprawnieniach (LUA), ponieważ każdy użytkownik ma administrator systemu SQL Server (`sysadmin`) uprawnienia wystąpienia uruchomiony na komputerze bez konieczności uruchamiania jako Windows Administrator, a także. Oprogramowanie wykonywania wystąpieniu użytkownika z ograniczonymi uprawnieniami nie może wprowadzać zmian całego systemu, ponieważ wystąpienie programu SQL Server Express jest uruchomiona w ramach konta użytkowników niebędących administratorami Windows użytkownika, a nie jako usługa. Każde wystąpienie użytkownika jest izolowana, z jego wystąpienie nadrzędne i inne wystąpienia użytkownika, działające na tym samym komputerze. Bazy danych uruchomione w wystąpieniu użytkownika są otwierane tylko w trybie jednego użytkownika i nie jest możliwe dla wielu użytkowników nawiązać połączenie bazy danych uruchomione w wystąpieniu użytkownika. Replikacja i zapytań rozproszonych również są wyłączone dla wystąpienia użytkownika.  
  
 Aby uzyskać więcej informacji zobacz "Wystąpień użytkownika" w podręcznikach Online programu SQL Server.  
  
> [!NOTE]
>  Wystąpienia użytkownika nie są wymagane dla użytkowników, którzy są administratorami na swoich komputerach lub w scenariuszach obejmujących wiele użytkowników bazy danych.  
  
## <a name="enabling-user-instances"></a>Włączanie wystąpień użytkownika  
 Aby wygenerować wystąpienia użytkownika, musi działać nadrzędne wystąpienie programu SQL Server Express. Wystąpienia użytkownika są domyślnie włączone w przypadku programu SQL Server Express jest zainstalowany i może być jawnie włączone lub wyłączone przez administratora systemu, wykonywanie **procedury składowanej sp_configure** systemowej procedury składowanej wystąpienie nadrzędne.  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Protokół sieciowy do wystąpień użytkownika musi być lokalny nazwanych potoków. Nie można uruchomić wystąpienia użytkownika na zdalnym wystąpieniu programu SQL Server i logowania do programu SQL Server nie są dozwolone.  
  
## <a name="connecting-to-a-user-instance"></a>Nawiązywanie połączenia z wystąpieniem użytkownika  
 `User Instance` i `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Zezwalaj słowa kluczowe <xref:System.Data.SqlClient.SqlConnection> do połączenia z wystąpieniem użytkownika. Wystąpienia użytkownika są również obsługiwane przez <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` i `AttachDBFilename` właściwości.  
  
 Należy pamiętać o następujących dotyczących przykładowe parametry połączenia, pokazano poniżej:  
  
- `Data Source` — Słowo kluczowe odwołuje się do wystąpienie programu SQL Server Express, który generuje wystąpienia użytkownika. Wystąpienie domyślne to. \sqlexpress.  
  
- `Integrated Security` ustawiono `true`. Aby połączyć się z wystąpieniem użytkownika, jest wymagane; uwierzytelnianie Windows Logowania do programu SQL Server nie są obsługiwane.  
  
- `User Instance` Ustawiono `true`, która wywołuje wystąpienia użytkownika. (Wartość domyślna to `false`.)  
  
- `AttachDbFileName` Słowo kluczowe parametrów połączenia jest używany do dołączania plików podstawowej bazy danych (.mdf), który musi zawierać pełną nazwę ścieżki. `AttachDbFileName` również odpowiada "rozszerzonych właściwości" i "początkowa nazwa pliku" klucze w ramach <xref:System.Data.SqlClient.SqlConnection> parametry połączenia.  
  
- `|DataDirectory|` Ciąg podstawienia ujęty w symbole potoku odwołuje się do katalogu danych aplikacji, Otwieranie połączenia i udostępnia ścieżkę względną wskazującą lokalizację pliki mdf i ldf bazy danych i dziennika. Jeśli chcesz zlokalizować te pliki w innym miejscu, należy podać pełną ścieżkę do plików.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> i <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> właściwości do tworzenia parametrów połączenia w czasie wykonywania.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Za pomocą &#124;DataDirectory&#124; ciąg podstawienia  
 `AttachDbFileName` został rozszerzony ADO.NET w wersji 2.0 wraz z wprowadzeniem `|DataDirectory|` (ujęty w symbole potoku) ciąg podstawienia. `DataDirectory` jest używana w połączeniu z `AttachDbFileName` wskaż ścieżkę względną do pliku danych, co pozwoli deweloperom na tworzenie parametrów połączenia, które są oparte na ścieżkę względną do źródła danych, zamiast trzeba określić pełną ścieżkę.  
  
 Lokalizacji fizycznej, `DataDirectory` wskazuje zależy od typu aplikacji. W tym przykładzie można dołączyć pliku Northwind.mdf znajduje się w folderze \app_data aplikacji.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Gdy `DataDirectory` jest używane, ścieżka pliku nie może być wyższe w strukturze katalogu niż katalog wskazywany przez ciąg podstawienia. Na przykład jeśli pełni rozwinięte `DataDirectory` jest C:\AppDirectory\app_data, a następnie przykładowy ciąg połączenia powyżej działa, ponieważ jest on poniżej c:\AppDirectory. Jednak próba określenia `DataDirectory` jako `|DataDirectory|\..\data` spowoduje wystąpienie błędu, ponieważ \data nie jest to podkatalog \AppDirectory.  
  
 Jeśli parametry połączenia zawiera ciąg sformatowany podstawienia <xref:System.ArgumentException> zostanie zgłoszony.  
  
> [!NOTE]
>  <xref:System.Data.SqlClient> rozpoznaje ciągów podstawienia do pełnych ścieżek względem komputera lokalnego systemu plików. W związku z tym serwera zdalnego, HTTP i UNC nazwy ścieżek nie są obsługiwane. Wyjątek jest zgłaszany, gdy połączenie jest otwarte, jeśli serwer nie znajduje się na komputerze lokalnym.  
  
 Gdy <xref:System.Data.SqlClient.SqlConnection> jest otwarty, nastąpi przekierowanie z domyślnego wystąpienia programu SQL Server Express do działającego środowiska wykonawczego zainicjowane wystąpienie w ramach konta obiektu wywołującego.  
  
> [!NOTE]
>  Może być konieczne w celu zwiększenia <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> wartości, ponieważ wystąpienia użytkownika może potrwać dłużej obciążenia regularnych wystąpień.  
  
 Poniższy fragment kodu zostanie otwarty nowy `SqlConnection`, wyświetla parametry połączenia w oknie konsoli, a następnie zamyka połączenia, podczas zamykania `using` bloku kodu.  
  
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
>  Wystąpienia użytkownika nie są obsługiwane w typowych kod języka środowiska uruchomieniowego (języka wspólnego CLR), który działa wewnątrz programu SQL Server. <xref:System.InvalidOperationException> Jest generowany, jeśli `Open` jest wywoływana w <xref:System.Data.SqlClient.SqlConnection> zawierający `User Instance=true` w parametrach połączenia.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Okres istnienia połączenia wystąpienia użytkownika  
 W przeciwieństwie do wersji programu SQL Server czy uruchomić jako usługę, wystąpienia programu SQL Server Express nie trzeba ją ręcznie uruchomione i zatrzymane. Każdorazowo użytkownik loguje się i łączy się z wystąpieniem użytkownika wystąpienia użytkownika jest uruchomiona, gdy nie jest jeszcze uruchomiona. Wystąpienie bazy danych, użytkownika mają `AutoClose` zestaw opcji, aby baza danych jest automatycznie zamknięte po okresie braku aktywności. Proces sqlservr.exe, który jest uruchamiany jest przechowywana uruchomione przez ograniczony limit czasu po zamknięciu ostatniego połączenia z wystąpieniem, więc nie musi być uruchomiony ponownie, jeśli inne połączenie jest otwarte przed upływem limitu czasu. Wystąpienia użytkownika automatycznie zamykany, jeśli nie nowe połączenie, zostanie otwarty przed wygaśnięciem tego limitu czasu. Administrator systemu w wystąpieniu nadrzędny można ustawić okres limitu czasu dla wystąpienia użytkownika przy użyciu **procedury składowanej sp_configure** zmienić **limitu czasu wystąpienia użytkownika** opcji. Wartość domyślna to 60 minut.  
  
> [!NOTE]
>  Jeśli `Min Pool Size` jest używany w parametrach połączenia z wartością większą niż zero, pulę połączeń zawsze będzie utrzymywać kilka otwarte połączenia i wystąpienia użytkownika nie zostanie automatycznie zamknięta.  
  
## <a name="how-user-instances-work"></a>Jak użytkownika wystąpienia pracy  
 Wystąpienia użytkownika jest generowany dla każdego użytkownika, po raz pierwszy **wzorca** i **msdb** systemowych baz danych są kopiowane z folderu danych szablonu do ścieżki w repozytorium danych lokalnych aplikacji użytkownika katalog do wyłącznego użytku przez wystąpienia użytkownika. Ścieżka ta jest zazwyczaj `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Podczas uruchamiania wystąpienia użytkownika, **bazy danych tempdb**, zaloguj się i śledzenia plików, są również zapisywane do tego katalogu. Nazwa jest generowana dla tego wystąpienia może być unikatowy dla każdego użytkownika.  
  
 Domyślnie wszyscy członkowie grupy BUILTIN\Użytkownicy Windows są przyznawane uprawnienia do łączenia w lokalnym wystąpieniu, a także uprawnienia Odczyt i wykonywanie na pliki binarne programu SQL Server. Po zweryfikowaniu poświadczeń użytkownika wywołującego hostingu wystąpienia użytkownika staje się `sysadmin` w tym wystąpieniu. Tylko Pamięć współużytkowana jest włączony dla wystąpienia użytkownika, co oznacza, że tylko operacji na komputerze lokalnym jest możliwe.  
  
 Użytkownicy muszą mieć uprawnienie zarówno uprawnienia odczytu i zapisu na pliki mdf i ldf określone w parametrach połączenia.  
  
> [!NOTE]
>  Pliki mdf i ldf reprezentują pliki dziennika i bazy danych, odpowiednio. Te dwa pliki są dopasowane zestawu, więc opieki należy podjąć podczas tworzenia kopii zapasowej i przywracanie operacji. Plik bazy danych zawiera informacje na temat dokładnego wersji pliku dziennika i bazy danych nie będą otwierane, jeśli jest sprzężona z niewłaściwego pliku dziennika.  
  
 Aby uniknąć uszkodzenia danych, bazę danych w wystąpieniu użytkownika jest otwierany przy użyciu wyłącznego dostępu. Dwa wystąpienia inny użytkownik, któremu udostępniono tej samej bazy danych na tym samym komputerze, użytkownik, który w pierwszym wystąpieniu należy zamknąć bazy danych, aby można go otworzyć w drugim wystąpieniu.  
  
## <a name="user-instance-scenarios"></a>Scenariusze dotyczące użytkowników wystąpienia  
 Wystąpienia użytkownika zapewniają deweloperom aplikacji baz danych z magazynem danych programu SQL Server, które nie są zależne od deweloperów konta z uprawnieniami administracyjnymi na swoich komputerach roboczych. Wystąpienia użytkownika są oparte na modelu dostępu/Jet, gdzie aplikacji bazy danych, po prostu łączy do pliku, a użytkownik automatycznie ma pełne uprawnienia do wszystkich obiektów bazy danych bez konieczności interwencji administratora systemu, aby udzielić uprawnienia. Jest ona przeznaczona do pracy w sytuacjach, w którym użytkownik jest uruchomiona w ramach konta użytkownika o najniższych uprawnieniach (LUA) i nie ma uprawnienia administracyjne na serwerze lub komputerze lokalnym, ale musi utworzyć obiekty bazy danych i aplikacji. Wystąpienia użytkownika Zezwalaj użytkownikom na tworzenie wystąpień w czasie wykonywania, które są uruchamiane w kontekście zabezpieczeń przez użytkownika, a nie w kontekście zabezpieczeń bardziej uprzywilejowanego usługi system.  
  
> [!IMPORTANT]
>  Wystąpienia użytkownika można stosować tylko w scenariuszach gdzie wszystkie aplikacje używające jej są w pełni zaufane.  
  
 Scenariusze wystąpienia użytkownika:  
  
- Dowolnej aplikacji pojedynczego użytkownika, których udostępnianie danych nie jest wymagane.  
  
- Wdrożenie ClickOnce. .NET Framework 2.0 (lub nowszą) i SQL Server Express są już zainstalowane na komputerze docelowym, pakiet instalacyjny pobrane w wyniku akcji ClickOnce można instalować i posługują się użytkownicy inni niż administrator. Należy pamiętać, że dla administrator musi zainstalować programu SQL Server Express, jeżeli jest to część instalacji. Aby uzyskać więcej informacji, zobacz [wdrażania ClickOnce Windows Forms](../../../winforms/clickonce-deployment-for-windows-forms.md).
  
- W wersji dedykowanej przy użyciu uwierzytelniania Windows hostingu platformy ASP.NET. Pojedyncze wystąpienie programu SQL Server Express, mogą być hostowane w sieci intranet. Aplikacja nawiązuje połączenie, za pomocą konta Windows ASPNET, nie za pomocą personifikacji. Wystąpienia użytkownika nie powinien służyć do innych firm lub udostępnione hostingu scenariuszach, gdzie wszystkie aplikacje będą współużytkują to samo wystąpienie użytkownika i nie jest już pozostać odizolowane od siebie nawzajem.  
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [Parametry połączeń](../../../../../docs/framework/data/adonet/connection-strings.md)
- [Nawiązywanie połączenia ze źródłem danych](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
