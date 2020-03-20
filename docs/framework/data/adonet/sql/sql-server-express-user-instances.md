---
title: Wystąpienia użytkownika programu SQL Server Express
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: 2bd67a9315eda4161d4b76e1638f5c08f9598a52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174488"
---
# <a name="sql-server-express-user-instances"></a>Wystąpienia użytkownika programu SQL Server Express
Program Microsoft SQL Server Express Edition (SQL Server Express) obsługuje funkcję wystąpienia użytkownika, która jest`SqlClient`dostępna tylko w przypadku korzystania z dostawcy danych programu .NET Framework dla programu SQL Server ( ). Wystąpienie użytkownika jest osobnym wystąpieniem aparatu bazy danych programu SQL Server Express, które jest generowane przez wystąpienie nadrzędne. Wystąpienia użytkowników umożliwiają użytkownikom, którzy nie są administratorami na komputerach lokalnych, dołączanie baz danych programu SQL Server Express i łączenie się z nim. Każde wystąpienie jest uruchamiane w kontekście zabezpieczeń poszczególnych użytkowników na zasadzie jednego wystąpienia na użytkownika.  
  
## <a name="user-instance-capabilities"></a>Możliwości wystąpienia użytkownika  
 Wystąpienia użytkowników są przydatne dla użytkowników, którzy korzystają z systemu Windows przy koncie użytkownika o najniższych uprawnieniach (LUA). Każdy użytkownik ma uprawnienia`sysadmin`administratora systemu programu SQL Server ( ) nad wystąpieniem uruchomionym na komputerze bez konieczności uruchamiania jako administrator systemu Windows. Oprogramowanie wykonujące w wystąpieniu użytkownika z ograniczonymi uprawnieniami nie może wprowadzać zmian w całym systemie, ponieważ wystąpienie programu SQL Server Express jest uruchomione na nie-administratorowym koncie systemu Windows użytkownika, a nie jako usługa. Każde wystąpienie użytkownika jest izolowane od jego wystąpienia nadrzędnego i od innych wystąpień użytkownika uruchomionych na tym samym komputerze. Bazy danych uruchomione w wystąpieniu użytkownika są otwierane tylko w trybie pojedynczego użytkownika i nie jest możliwe dla wielu użytkowników, aby połączyć się z bazami danych uruchomionymi w wystąpieniu użytkownika. Replikacja i zapytania rozproszone są również wyłączone dla wystąpień użytkowników.
  
> [!NOTE]
> Wystąpienia użytkowników nie są potrzebne użytkownikom, którzy są już administratorami na własnych komputerach lub w scenariuszach obejmujących wielu użytkowników bazy danych.  
  
## <a name="enabling-user-instances"></a>Włączanie wystąpień użytkowników  
 Aby wygenerować wystąpienia użytkowników, musi być uruchomione wystąpienie nadrzędne programu SQL Server Express. Wystąpienia użytkowników są domyślnie włączone po zainstalowaniu programu SQL Server Express i mogą być jawnie włączone lub wyłączone przez administratora systemu wykonującego procedurę składowaną systemu **sp_configure** w wystąpieniu nadrzędnym.  
  
```sql  
-- Enable user instances.  
sp_configure 'user instances enabled','1'
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Protokół sieciowy dla wystąpień użytkowników musi być lokalnymi nazwanymi potokami. Nie można uruchomić wystąpienia użytkownika na zdalnym wystąpieniu programu SQL Server, a logowania programu SQL Server nie są dozwolone.  
  
## <a name="connecting-to-a-user-instance"></a>Łączenie się z wystąpieniem użytkownika  
 I `User Instance` `AttachDBFilename` słowa kluczowe <xref:System.Data.SqlClient.SqlConnection> umożliwiają łączenie się z wystąpieniem użytkownika. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Wystąpienia użytkownika są również obsługiwane <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` `AttachDBFilename` przez i właściwości.  
  
 Zwróć uwagę na następujące informacje na temat przykładowego ciągu połączenia pokazanego poniżej:  
  
- Słowo `Data Source` kluczowe odnosi się do nadrzędnego wystąpienia programu SQL Server Express, które generuje wystąpienie użytkownika. Domyślnym wystąpieniem jest .\sqlexpress.  
  
- `Integrated Security`jest ustawiona na `true`. Aby połączyć się z wystąpieniem użytkownika, wymagane jest uwierzytelnianie systemu Windows; Logowania programu SQL Server nie są obsługiwane.  
  
- Jest `User Instance` ustawiona `true`na , która wywołuje wystąpienie użytkownika. (Wartość domyślna to `false`.)  
  
- Słowo `AttachDbFileName` kluczowe parametry połączenia jest używane do dołączania pliku podstawowej bazy danych (.mdf), który musi zawierać pełną nazwę ścieżki. `AttachDbFileName`odpowiada również kluczom "właściwości rozszerzone" i "nazwa pliku <xref:System.Data.SqlClient.SqlConnection> początkowego" w ciągu połączenia.  
  
- Ciąg `|DataDirectory|` podstawiania ujęty w symbolach potoku odnosi się do katalogu danych aplikacji otwierającej połączenie i zapewnia względną ścieżkę wskazującą lokalizację plików bazy danych i dziennika .mdf i .ldf. Jeśli chcesz zlokalizować te pliki w innym miejscu, musisz podać pełną ścieżkę do plików.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
> Można również użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> i właściwości do tworzenia ciągu połączenia w czasie wykonywania.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Używanie ciągu&#124;&#124; &#124;DataDirectory  
 `AttachDbFileName`został rozszerzony w ADO.NET 2.0 z wprowadzeniem `|DataDirectory|` (zamkniętego w symbolach rur) ciągu podstawienia. `DataDirectory`jest używany w `AttachDbFileName` połączeniu z wskazać względną ścieżkę do pliku danych, umożliwiając deweloperom tworzenie ciągów połączeń, które są oparte na względnej ścieżce do źródła danych, zamiast być wymagane do określenia pełnej ścieżki.  
  
 Lokalizacja fizyczna, która `DataDirectory` wskazuje zależy od typu aplikacji. W tym przykładzie plik Northwind.mdf, który ma zostać dołączony, znajduje się w folderze \app_data aplikacji.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Gdy `DataDirectory` jest używana, wynikowa ścieżka pliku nie może być wyższa w strukturze katalogów niż katalog wskazany przez ciąg podstawiania. Na przykład jeśli w `DataDirectory` pełni rozwinięty jest C:\AppDirectory\app_data, a następnie przykładowy ciąg połączenia pokazano powyżej działa, ponieważ jest poniżej c:\AppDirectory. Jednak próba określenia, `DataDirectory` `|DataDirectory|\..\data` jak spowoduje błąd, ponieważ \data nie jest podkatalogiem \AppDirectory.  
  
 Jeśli ciąg połączenia ma nieprawidłowo sformatowany <xref:System.ArgumentException> ciąg podstawiania, zostanie ono odrzucone.  
  
> [!NOTE]
> <xref:System.Data.SqlClient>rozwiązuje ciągi podstawiania na pełne ścieżki względem lokalnego systemu plików komputerowych. W związku z tym nazwy ścieżek serwera zdalnego, HTTP i UNC nie są obsługiwane. Wyjątek jest zgłaszany po otwarciu połączenia, jeśli serwer nie znajduje się na komputerze lokalnym.  
  
 Po <xref:System.Data.SqlClient.SqlConnection> otwarciu jest przekierowywane z domyślnego wystąpienia programu SQL Server Express do inicjowanego wystąpienia w czasie wykonywania uruchomionego na koncie wywołującego.  
  
> [!NOTE]
> Może być konieczne zwiększenie <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> wartości, ponieważ wystąpienia użytkownika może trwać dłużej niż regularne wystąpienia.  
  
 Poniższy fragment kodu `SqlConnection`otwiera nowy , wyświetla parametry połączenia w oknie konsoli, a `using` następnie zamyka połączenie po zamknięciu bloku kodu.  
  
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
> Wystąpienia użytkowników nie są obsługiwane w kodzie środowiska wykonawczego języka wspólnego (CLR), który jest uruchomiony wewnątrz programu SQL Server. Jest <xref:System.InvalidOperationException> generowany, `Open` jeśli jest <xref:System.Data.SqlClient.SqlConnection> wywoływana na który ma `User Instance=true` w ciągu połączenia.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Okres istnienia połączenia wystąpienia użytkownika  
 W przeciwieństwie do wersji programu SQL Server, które są uruchamiane jako usługa, wystąpienia programu SQL Server Express nie muszą być uruchamiane ręcznie i zatrzymywane. Za każdym razem, gdy użytkownik loguje się i łączy się z wystąpieniem użytkownika, wystąpienie użytkownika jest uruchamiane, jeśli nie jest jeszcze uruchomione. Bazy danych wystąpień `AutoClose` użytkowników mają ustawioną opcję, dzięki czemu baza danych jest automatycznie zamykana po okresie braku aktywności. Proces sqlservr.exe, który jest uruchamiany jest utrzymywany przez ograniczony okres czasu po zamknięciu ostatniego połączenia z wystąpieniem, więc nie trzeba go ponownie uruchamiać, jeśli inne połączenie zostanie otwarte przed upływem czasu. Wystąpienie użytkownika zostanie automatycznie zamknięte, jeśli żadne nowe połączenie nie zostanie otwarte przed upływem tego okresu. Administrator systemu w wystąpieniu nadrzędnym może ustawić czas trwania limitu czasu dla wystąpienia użytkownika za pomocą **sp_configure,** aby zmienić opcję **limitu czasu wystąpienia użytkownika.** Wartość domyślna to 60 minut.  
  
> [!NOTE]
> Jeśli `Min Pool Size` jest używany w ciągu połączenia o wartości większej niż zero, pooler połączenia zawsze będzie obsługiwać kilka otwartych połączeń, a wystąpienie użytkownika nie zostanie automatycznie zamknięty.  
  
## <a name="how-user-instances-work"></a>Jak działają wystąpienia użytkowników  
 Przy pierwszym generowaniu wystąpienia użytkownika dla każdego użytkownika, **główne** i **msdb** system baz danych są kopiowane z folderu Dane szablonu do ścieżki w katalogu repozytorium danych aplikacji lokalnej użytkownika do wyłącznego użytku przez wystąpienie użytkownika. Ta ścieżka jest `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`zazwyczaj . Po uruchomieniu wystąpienia użytkownika, **tempdb**, dziennik i pliki śledzenia są również zapisywane w tym katalogu. Nazwa jest generowana dla wystąpienia, które jest gwarantowane jako unikatowe dla każdego użytkownika.  
  
 Domyślnie wszyscy członkowie grupy Wbudowane\Użytkownicy systemu Windows mają uprawnienia do łączenia się w wystąpieniu lokalnym, a także do odczytu i wykonywania uprawnień w plikach binarnych programu SQL Server. Po zweryfikowaniu poświadczeń użytkownika wywołującego hostowania wystąpienia `sysadmin` użytkownika, ten użytkownik staje się w tym wystąpieniu. Tylko pamięć współużytkowana jest włączona dla wystąpień użytkownika, co oznacza, że możliwe są tylko operacje na komputerze lokalnym.  
  
 Użytkownikom należy przyznać uprawnienia do odczytu i zapisu w plikach .mdf i .ldf określonych w ciągu połączenia.  
  
> [!NOTE]
> Pliki .mdf i .ldf reprezentują odpowiednio pliki bazy danych i dziennika. Te dwa pliki są dopasowane zestaw, więc należy uważać podczas wykonywania kopii zapasowych i przywracania operacji. Plik bazy danych zawiera informacje o dokładnej wersji pliku dziennika, a baza danych nie zostanie otwarta, jeśli jest połączona z niewłaściwym plikiem dziennika.  
  
 Aby uniknąć uszkodzenia danych, baza danych w wystąpieniu użytkownika jest otwierana z wyłącznym dostępem. Jeśli dwa różne wystąpienia użytkownika współużytkuje tę samą bazę danych na tym samym komputerze, użytkownik w pierwszym wystąpieniu musi zamknąć bazę danych, zanim będzie można otworzyć w drugim wystąpieniu.  
  
## <a name="user-instance-scenarios"></a>Scenariusze wystąpienia użytkownika  
 Wystąpienia użytkowników zapewniają deweloperom aplikacji bazy danych magazyn danych programu SQL Server, który nie zależy od deweloperów posiadających konta administracyjne na swoich komputerach deweloperskich. Wystąpienia użytkowników są oparte na modelu programu Access/Jet, w którym aplikacja bazy danych po prostu łączy się z plikiem, a użytkownik automatycznie ma pełne uprawnienia do wszystkich obiektów bazy danych bez konieczności interwencji administratora systemu w celu przyznania uprawnień. Jest przeznaczony do pracy w sytuacjach, gdy użytkownik jest uruchomiony przy koncie użytkownika o najniższych uprawnieniach (LUA) i nie ma uprawnień administracyjnych na serwerze lub komputerze lokalnym, ale musi utworzyć obiekty i aplikacje bazy danych. Wystąpienia użytkowników umożliwiają użytkownikom tworzenie wystąpień w czasie wykonywania, które są uruchamiane w kontekście zabezpieczeń użytkownika, a nie w kontekście zabezpieczeń bardziej uprzywilejowanej usługi systemowej.  
  
> [!IMPORTANT]
> Wystąpienia użytkownika powinny być używane tylko w scenariuszach, w których wszystkie aplikacje korzystające z niego są w pełni zaufane.  
  
 Scenariusze wystąpienia użytkownika obejmują:  
  
- Każda aplikacja dla jednego użytkownika, w której udostępnianie danych nie jest wymagane.  
  
- Kliknij pozycjęWładne wdrożenie. Jeśli program .NET Framework 2.0 (lub nowszy) i SQL Server Express są już zainstalowane na komputerze docelowym, pakiet instalacyjny pobrany w wyniku akcji ClickOnce może być zainstalowany i używany przez użytkowników niebędących administratorami. Należy zauważyć, że administrator musi zainstalować program SQL Server Express, jeśli jest to część instalacji. Aby uzyskać więcej informacji, zobacz [ClickOnce Deployment for Windows Forms](../../../winforms/clickonce-deployment-for-windows-forms.md).
  
- Dedykowany hosting ASP.NET przy użyciu uwierzytelniania systemu Windows. Pojedyncze wystąpienie programu SQL Server Express może być hostowane w intranecie. Aplikacja łączy się przy użyciu konta ASPNET Systemu Windows, a nie przy użyciu personifikacji. Wystąpienia użytkowników nie powinny być używane w scenariuszach hostingu innych firm lub udostępniania, w których wszystkie aplikacje współużytkują to samo wystąpienie użytkownika i nie będą już odizolowane od siebie.  
  
## <a name="see-also"></a>Zobacz też

- [SQL Server i ADO.NET](index.md)
- [Parametry połączenia](../connection-strings.md)
- [Łączenie się ze źródłem danych](../connecting-to-a-data-source.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
