---
title: Co to jest nowe w programie .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1e54aa8a9751a01e8856a3e9e71d63b55772f2c
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="whats-new-in-the-net-framework"></a>Co to jest nowe w programie .NET Framework
<a name="introduction"></a>Ten artykuł zawiera podsumowanie klucza nowe funkcje i ulepszenia w następujących wersjach programu .NET Framework:  
 
[.NET framework 4.7.2](#v472)   
[.NET Framework 4.7.1](#v471)    
[.NET framework 4.7](#v47)   
[.NET framework 4.6.2](#v462)   
[.NET framework 4.6.1](#v461)   
[.NET 2015 i .NET Framework 4.6](#v46)   
[.NET Framework 4.5.2](#v452)   
[.NET Framework 4.5.1](#v451)   
[Program .NET framework 4.5](#v45)   

Ten artykuł zawiera szczegółowe informacje na temat każdej nowej funkcji i mogą ulec zmianie. Aby uzyskać ogólne informacje o .NET Framework, zobacz [wprowadzenie](../../../docs/framework/get-started/index.md). Dla obsługiwanych platform, zobacz [wymagania systemowe](~/docs/framework/get-started/system-requirements.md). Łącza pobierania oraz instrukcje dotyczące instalacji, zobacz [Przewodnik instalacji](../../../docs/framework/install/guide-for-developers.md).

> [!NOTE]
> Zespół .NET Framework zwalnia również funkcje poza pasmem z NuGet, rozwiń węzeł Obsługa platform i wprowadzenie nowych funkcji, takich jak niezmienne kolekcje i typy wektorów SIMD — włączone. Aby uzyskać więcej informacji, zobacz [dodatkowych bibliotek klasy i interfejsy API](../additional-apis/index.md) i [.NET Framework i poza harmonogramem](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md). Zobacz [pełną listę pakietów NuGet](https://blogs.msdn.microsoft.com/dotnet/p/nugetpackages/) dla programu .NET Framework lub subskrybować [naszych kanału informacyjnego](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).

<a name="v472"></a> 
## <a name="introducing-the-net-framework-472"></a>Wprowadzenie do programu .NET Framework 4.7.2

.NET Framework 4.7.2 kompilacje w poprzednich wersjach programu .NET Framework 4.x, dodając wiele nowe poprawki oraz kilka nowych funkcji zachowując bardzo stabilne produktu.

### <a name="downloading-and-installing-the-net-framework-472"></a>Trwa pobieranie i instalowanie programu .NET Framework 4.7.2
 
.NET Framework 4.7.2 można pobrać z następujących lokalizacji:

- [Instalator programu .NET framework 4.7.2 sieci Web](http://go.microsoft.com/fwlink/?LinkId=863262)

- [NET Framework 4.7.2 Instalatora w trybie Offline](http://go.microsoft.com/fwlink/?LinkId=863265)

.NET Framework 4.7.2 można zainstalować na systemu Windows 10, Windows 8.1, Windows 7 z dodatkiem SP1 i odpowiednie platformy serwera, począwszy od systemu Windows Server 2008 R2 z dodatkiem SP1. .NET Framework 4.7.2 można zainstalować za pomocą Instalatora sieci web lub Instalatora w trybie offline. Zalecaną metodą dla większości użytkowników jest użycie Instalatora sieci web.

Możesz wybrać docelową programu .NET Framework 4.7.2 w programie Visual Studio 2012 lub nowszym, instalując [.NET Framework 4.7.2 Developer Pack](http://go.microsoft.com/fwlink/?LinkId=874338). 

### <a name="whats-new-in-the-net-framework-472"></a>Co to jest nowe w programie .NET Framework 4.7.2

.NET Framework 4.7.2 zawiera nowe funkcje w następujących obszarach:

- [Funkcje podstawowe](#core472)
- [ASP.NET](#asp-net472)
- [Sieci](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#ClickOnce472)

Kontynuowanie fokusu w programie .NET Framework 4.7.2 jest lepsze ułatwień dostępu, dzięki czemu aplikacji zapewnić odpowiednie funkcje użytkowników korzystających z technologii pomocniczej. Aby uzyskać informacje na Ulepszanie ułatwień dostępu w programie .NET Framework 4.7.2, zobacz [What's new in ułatwień dostępu w programie .NET Framework](whats-new-in-accessibility.md). 

<a name="core-472" />
#### <a name="core"></a>Core

.NET Framework 4.7.2 funkcjami wiele rozszerzeń kryptograficznych, lepsze Obsługa dekompresowania pliku archiwum ZIP i dodatkową kolekcję interfejsów API.

**Nowe przeciążenia RSA. Tworzenie i DSA. Utwórz**

<xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> i <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> metody umożliwiają Podaj parametry klucza przy uruchamianiu nową <xref:System.Security.Cryptography.DSA> lub <xref:System.Security.Cryptography.RSA> klucza. Umożliwiają one Zastąp kod podobne do poniższych:

```csharp
// Before .NET Framework 4.7.2
using (RSA rsa = RSA.Create())
{
   rsa.ImportParameters(rsaParameters);
   // Other code to execute using the RSA instance.
}
``` 

```vb
' Before .NET Framework 4.7.2
Using rsa = RSA.Create()
   rsa.ImportParameters(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
``` 
z kodem następująco:
```csharp
// Starting with .NET Framework 4.7.2
using (RSA rsa = RSA.Create(rsaParameters))
{
   // Other code to execute using the rsa instance.
}
``` 
```vb
' Starting with .NET Framework 4.7.2
Using rsa = RSA.Create(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
``` 

<xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> i <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> metody umożliwiają generowanie nowych <xref:System.Security.Cryptography.DSA> lub <xref:System.Security.Cryptography.RSA> klucze z określonego rozmiaru klucza. Na przykład:

```csharp
using (DSA dsa = DSA.Create(2048))
{
   // Other code to execute using the dsa instance.
}
``` 
```vb
Using dsa = DSA.Create(2048)
   ' Other code to execute using the dsa instance.
End Using
``` 

**Konstruktory Rfc2898DeriveBytes zaakceptuj nazwę algorytmu wyznaczania wartości skrótu**

<xref:System.Security.Cryptography.Rfc2898DeriveBytes> Klasa ma trzy nowe konstruktorów z <xref:System.Security.Cryptography.HashAlgorithmName> parametr, który identyfikuje Algorytm HMAC do użycia podczas tworzenia klasy pochodnej kluczy. Zamiast używać algorytmu SHA-1, deweloperzy powinny używać HMAC opartych na protokole algorytmu SHA-2, takie jak algorytm SHA-256, jak pokazano w poniższym przykładzie:

```csharp
private static byte[] DeriveKey(string password, out int iterations, out byte[] salt, 
                                out HashAlgorithmName algorithm)
{
   iterations = 100000;
   algorithm = HashAlgorithmName.SHA256;

   const int SaltSize = 32;
   const int DerivedValueSize = 32;

   using (Rfc2898DeriveBytes pbkdf2 = new Rfc2898DeriveBytes(password, SaltSize, 
                                                             iterations, algorithm))
   {
      salt = pbkdf2.Salt;
      return pbkdf2.GetBytes(DerivedValueSize);
   }
} 
```
```vb
Private Shared Function DeriveKey(password As String, ByRef iterations As Integer, 
                                  ByRef salt AS Byte(), ByRef algorithm As HashAlgorithmName) As Byte()
   iterations = 100000
   algorithm = HashAlgorithmName.SHA256

   Const SaltSize As Integer = 32
   Const  DerivedValueSize As Integer = 32

   Using pbkdf2 = New Rfc2898DeriveBytes(password, SaltSize, iterations, algorithm)
      salt = pbkdf2.Salt
      Return pbkdf2.GetBytes(DerivedValueSize)
   End Using
End Function 
```

**Obsługa kluczy tymczasowych**

Importuj PFX Opcjonalnie można załadować kluczy prywatnych bezpośrednio z pamięci, pomijanie dysku twardego. Gdy nowy <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flaga jest określona w <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> konstruktora lub jednej z przeciążeń <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> metody, kluczy prywatnych zostanie załadowany jako klucze tymczasowych. Zapobiega to kluczy jest widoczny na dysku. Jednak:

- Ponieważ kluczy nie są zachowywane na dysku, certyfikaty z tej flagi nie są odpowiednimi obiektami do dodania do X509Store.

- Załadowane w ten sposób klucze są prawie zawsze załadowanego za pomocą CNG systemu Windows. W związku z tym obiekty wywołujące muszą uzyskać dostęp do klucza prywatnego przez wywołanie metody rozszerzenia, takie jak [certyfikatu. GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> Właściwości nie działa.

- Ponieważ starszego <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> właściwości nie działa z certyfikatami, deweloperzy należy wykonać rygorystyczne testy przed przełączeniem do kluczy tymczasowych.

**Programowe tworzenie żądania podpisywania PKCS #10 certyfikacji i certyfikatów kluczy publicznych X.509**

Począwszy od programu .NET Framework 4.7.2 obciążeń można wygenerować certyfikatu podpisywania żądań (CSR), co umożliwia generowanie żądania certyfikatu do przemieszczony w istniejących narzędzi. Jest to często przydatne w scenariuszach testów.

Aby uzyskać więcej informacji oraz przykłady kodu, zobacz "programowe tworzenie PKCS #10 żądania podpisywania certyfikacji i certyfikatów kluczy publicznych X.509" w [blogu .NET](https://blogs.msdn.microsoft.com/dotnet/2018/03/08/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Nowe elementy członkowskie SignerInfo**

Począwszy od programu .NET Framework 4.7.2, <xref:System.Security.Cryptography.Pkcs.SignerInfo> klasa przedstawia więcej informacji na temat podpisu. Można pobrać wartość <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> właściwość, aby określić algorytm podpisu, używany przez osoby podpisującej. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> można wywołać w celu uzyskania kopii podpis kryptograficzny dla tej osoby podpisującej.

**Mając otwarte opakowana strumień po usunięciu CryptoStream**

Począwszy od programu .NET Framework 4.7.2, <xref:System.Security.Cryptography.CryptoStream> klasa ma dodatkowe konstruktora, który umożliwia <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> nie zamknąć opakowana strumienia. Aby pozostaw otwarte po opakowana strumienia <xref:System.Security.Cryptography.CryptoStream> usuwania, należy wywołać nowe <xref:System.Security.Cryptography.CryptoStream> konstruktora w następujący sposób:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```
```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**Dekompresja zmiany DeflateStream**

Począwszy od programu .NET Framework 4.7.2, wykonywania działań dekompresji w <xref:System.IO.Compression.DeflateStream> klasy zmienił się na domyślnie używają natywnych interfejsów API systemu Windows. Zazwyczaj powoduje to poprawy wydajności istotne. 

Domyślnie dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.2 włączona jest obsługa dekompresowania pliku przy użyciu interfejsów API systemu Windows. Aplikacje docelowe wcześniejszych wersji programu .NET Framework, które są uruchomione na platformie .NET Framework 4.7.2 włączyć do tego zachowania, dodając następujące [przełącznika AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do pliku konfiguracji aplikacji:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" /> 
```

**Dodatkową kolekcję interfejsów API**

.NET Framework 4.7.2 dodaje szereg nowych interfejsów API do <xref:System.Collections.Generic.SortedSet%601> i <xref:System.Collections.Generic.HashSet%601> typów. Należą do nich następujące elementy:

- `TryGetValue` metody, które wzorzec spróbuj użyć w innych typów kolekcji do tych dwóch typów. Dostępne są następujące metody:
   - [' publicznego bool zestaw HashSet<T>. TryGetValue (equalValue T, limit T actualValue;)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
   - [' publicznego bool SortedSet<T>. TryGetValue (equalValue T, limit T actualValue;)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
- `Enumerable.To*` metody rozszerzenia, które przekonwertowanie kolekcji do <xref:System.Collections.Generic.HashSet%601>:
   - [publiczne statyczne zestaw HashSet<TSource> ToHashSet<TSource>(ten atrybut IEnumerable<TSource> źródła);](xref:System.Linq.Enumerable.ToHashSet%2A)
   - [publiczne statyczne zestaw HashSet<TSource> ToHashSet<TSource>(ten atrybut IEnumerable<TSource> źródła IEqualityComparer<TSource> porównania);](xref:System.Linq.Enumerable.ToHashSet%2A)
- Nowy <xref:System.Collections.Generic.HashSet%601> konstruktorów, które pozwalają ustawić pojemność kolekcji, która daje w wyniku poprawiać wydajność, gdy wiesz rozmiar <xref:System.Collections.Generic.HashSet%601> wcześniej:
   - [zestaw HashSet publiczny (pojemność int)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
   - [zestaw HashSet publiczny (int pojemności, IEqualityComparer<T> porównania)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))  

<xref:System.Collections.Concurrent.ConcurrentDictionary%602> Klasa zawiera nowe przeciążeń <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody do pobierania wartości ze słownika lub dodać ją, jeśli nie zostanie znaleziony, a także Dodaj wartość do słownika lub do zaktualizowania go, jeśli już istnieje.

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472" />
#### <a name="aspnet"></a>ASP.NET

**Obsługa iniekcji zależności w formularzach sieci Web**

[Iniekcji zależności (Podpisane)](/aspnet/core/fundamentals/dependency-injection#what-is-dependency-injection) oddziela obiektów i ich zależności, dzięki czemu kod obiektu nie jest już musi zostać zmienione wyłącznie z powodu zależności została zmieniona. Podczas tworzenia aplikacji ASP.NET, które odnoszą się do programu .NET Framework 4.7.2, można:

- Użyj iniekcji na podstawie metody ustawiającej, na podstawie interfejsu i na podstawie konstruktora w [programów obsługi i modułów](https://msdn.microsoft.com/en-us/library/bb398986.aspx), [strony wystąpień](xref:System.Web.UI.Page), i [kontrolek użytkownika](https://msdn.microsoft.com/en-us/library/y6wb1a0e.aspx) aplikacji ASP.NET aplikację sieci web projekty.

- Użyj metody ustawiającej — interfejs procesorami i iniekcji w [programów obsługi i modułów](https://msdn.microsoft.com/en-us/library/bb398986.aspx), [strony wystąpień](xref:System.Web.UI.Page), i [kontrolek użytkownika](https://msdn.microsoft.com/en-us/library/y6wb1a0e.aspx) projektów witryny sieci web ASP.NET.

- Dołącz struktur iniekcji zależności inny. 

**Obsługa plików cookie w tej samej lokacji**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) zapobiega wysyłaniu wraz z żądania międzywitrynowego pliku cookie przeglądarki. .NET Framework 4.7.2 dodaje <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> o wartości <xref:System.Web.SameSiteMode?displayProperty=nameWithType> element członkowski wyliczenia. Jeśli jego wartość wynosi <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> lub <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET dodaje `SameSite` atrybutu nagłówka set-cookie. Obsługa SameSite dotyczy <xref:System.Web.HttpCookie> obiekty, jak również do <xref:System.Web.Security.FormsAuthentication> i <xref:System.Web.SessionState> plików cookie.
 
Można ustawić SameSite dla <xref:System.Web.HttpCookie> obiektów w następujący sposób:

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```
```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```
Pliki cookie SameSite można również skonfigurować na poziomie aplikacji przez zmodyfikowanie pliku web.config:

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```
Możesz dodać SameSite dla <xref:System.Web.Security.FormsAuthentication> i <xref:System.Web.SessionState> plików cookie przez zmodyfikowanie pliku konfiguracji sieci web:

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   <authentication />
   <sessionSate cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />
#### <a name="networking"></a>Obsługa sieci

**Implementacja właściwości HttpClientHandler**

.NET Framework 4.7.1 dodane osiem właściwości <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> klasy. Jednak dwóch zwrócił <xref:System.PlatformNotSupportedException>. .NET Framework 4.7.2 udostępnia teraz implementację tych właściwości. Dostępne są następujące właściwości:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />
#### <a name="sqlclient"></a>SQLClient

**Obsługa Azure uniwersalnych uwierzytelnianie usługi Active Directory i usługi Multi-Factor authentication**

Rosnących wymagań dotyczących zgodności i zabezpieczeń wymagają, że wielu klientów używa uwierzytelniania wieloskładnikowego (MFA). Ponadto bieżącego najlepszych rozwiązań zniechęcić tym haseł użytkowników bezpośrednio w parametrach połączenia. Aby obsługiwać te zmiany, .NET Framework 4.7.2 rozszerza [parametry połączenia SQLClient](xref:System.Data.SqlClient.SqlConnection.ConnectionString) , dodając nową wartość "Active Directory Interactive", istniejący słowa kluczowego "Uwierzytelnianie" do obsługi uwierzytelniania Wieloskładnikowego i [usługi Azure AD Uwierzytelnianie](/azure/sql-database/sql-database-aad-authentication-configure). Nowa metoda interakcyjne obsługuje macierzystego i federacyjnych użytkowników usługi Azure AD, a także gości usługi Azure AD. W przypadku tej metody uwierzytelniania MFA narzucone przez usługę Azure AD jest obsługiwana dla baz danych SQL. Ponadto proces uwierzytelniania żądania hasło użytkownika, aby stosować się do najlepszych rozwiązań dotyczących zabezpieczeń.

W poprzednich wersjach programu .NET Framework, łączność z serwerem SQL obsługuje tylko <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> i <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> opcje. Oba te są częścią metody nieinterakcyjnej [ADAL protokołu](/azure/active-directory/develop/active-directory-authentication-libraries), który nie obsługuje uwierzytelnianie wieloskładnikowe. Z nowym <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> opcji łączności z serwerem SQL obsługuje uwierzytelnianie wieloskładnikowe, a także istniejących metod uwierzytelniania (hasła i zintegrowane uwierzytelnianie), co pozwala użytkownikom na wprowadzanie hasła użytkowników interaktywnie bez utrwalanie haseł w połączeniu ciąg.

Więcej informacji oraz przykład sekcja "SQL — usługi Azure AD uniwersalnych i Multi-Factor uwierzytelniania Obsługa w" [blogu .NET](https://blogs.msdn.microsoft.com/dotnet/2018/03/08/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Obsługa zawsze zaszyfrowane w wersji 2**

NET Framework 4.7.2 dodaje obsługuje na podstawie enklawę zawsze szyfrowane. Z oryginalną wersją zawsze zaszyfrowane jest technologii szyfrowania po stronie klienta, w których szyfrowania kluczy nigdy nie opuszczają klienta. W podstawie enklawę zawsze zaszyfrowane klient może opcjonalnie wysyłać kluczy szyfrowania do bezpiecznego enklawę, czyli bezpiecznego jednostki obliczeniowych, który można określić jako część programu SQL Server, ale ten kod programu SQL Server nie może manipulować. Do obsługi na podstawie enklawę zawsze zaszyfrowane, .NET Framework 4.7.2 dodaje następujące typy i składniki do <xref:System.Data.SqlClient> przestrzeni nazw:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, która określa identyfikator Uri na podstawie enklawę zawsze szyfrowane.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, które jest klasą abstrakcyjną, z których wszystkie enklawę są uzyskiwane dostawców. 

- <xref:System.Data.SqlClient.SqlEnclaveSession>, który hermetyzuje stan enklawę danej sesji.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, zapewniające parametry zaświadczania używany przez program SQL Server do pobierania informacji niezbędnych do wykonania konkretnego protokołu zaświadczania.

Plik konfiguracji aplikacji następnie określa konkretną implementację klasy abstrakcyjnej <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> klasy, który udostępnia funkcjonalność enklawę dostawcy. Na przykład:

```xml
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/> 
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="Azure" type="Microsoft.SqlServer.Management.AlwaysEncrypted.AzureEnclaveProvider,MyApp"/>
      <add name="HGS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.HGSEnclaveProvider,MyApp" />
    </providers>
  </SqlColumnEncryptionEnclaveProviders >
</configuration>
```

Podstawowe przepływem na podstawie enklawę zawsze zaszyfrowane jest:

1. Użytkownik tworzy AlwaysEncrypted połączenia z programem SQL Server, który obsługiwany na podstawie enklawę zawsze szyfrowane. Sterownik kontaktuje się z usługą zaświadczania zapewnienie łączy się z prawej enklawę.

1. Po enklawę zostało potwierdzone, sterownik ustanawia bezpiecznego kanału z daną enklawę bezpiecznego hostowanych na serwerze SQL.

1. Sterownik udostępnia klucze szyfrowania autoryzowana przez klienta z bezpiecznego enklawę na czas trwania połączenia SQL.

<a name="wpf472" />
#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Znajdowanie elementów ResourceDictionaries przez źródło**

Począwszy od programu .NET Framework 4.7.2 diagnostycznych Asystent mogą zlokalizować <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> zostały utworzone z danego źródła identyfikatora Uri. (Ta funkcja jest używana przez Asystenci diagnostycznych, a nie przez aplikacje produkcyjne.) Diagnostycznych Asystenta, takich jak funkcje "Edit-and-Continue" programu Visual Studio umożliwia jego użytkownika edytować ResourceDictionary przy użyciu zamiaru, że zmiany można zastosować do uruchomionej aplikacji. Jednym z etapów realizacji tego jest znajdowanie wszystkich elementów ResourceDictionaries utworzone ze słownika, który jest edytowany działającej aplikacji. Na przykład aplikacji mogą zadeklarować ResourceDictionary, którego zawartość zostanie skopiowana ze źródła danego identyfikatora URI:


```xml
<ResourceDictionary Source="MyRD.xaml">
```

Asystent diagnostycznych, który umożliwia edycję oryginalnego kodu znaczników w *MyRD.xaml* można użyć nowej funkcji do zlokalizowania w słowniku. Funkcja jest implementowany przez nowe metody statycznej <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>. Asystent diagnostycznych wywołuje metodę nowe przy użyciu bezwzględny identyfikator Uri identyfikujący oryginalny kod znaczników, jak pokazano w poniższym kodzie:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```
```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

Metoda zwraca pustą wyliczalny chyba że <xref:System.Windows.Diagnostics.VisualDiagnostics> jest włączona i [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) ustawiono zmiennej środowiskowej.

**Znajdowanie właścicieli ResourceDictionary**

Począwszy od programu .NET Framework 4.7.2 diagnostycznych Asystent mogą zlokalizować właściciele danego <xref:Windows.UI.Xaml.ResourceDictionary>. (Funkcja używa się asystentów diagnostycznych, a nie przez aplikacje produkcyjne.) Przy każdej zmianie <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automatycznie odnajduje wszystkie [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) odwołania, które mogą wpłynąć na zmianę. 

Diagnostycznych Asystenta, takich jak funkcje programu Visual Studio "Edit-and-Continue" może być tak, aby obsłużyć rozszerzyć [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odwołania. Pierwszym krokiem w procesie jest znalezienie właściciele słownika. oznacza to aby znaleźć wszystkie obiekty których `Resources` właściwość odwołuje się do słownika (albo bezpośrednio lub pośrednio przez <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> właściwości). Trzech nowych metod statycznych na <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> klasy, po jednej dla każdego z typów podstawowych, które ma `Resources` właściwości, obsługują ten krok:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Te metody zwracają pustą wyliczalny chyba że <xref:System.Windows.Diagnostics.VisualDiagnostics> jest włączona i [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) ustawiono zmiennej środowiskowej.

**Trwa znajdowanie odwołań StaticResource**

Diagnostycznych Asystenta teraz odbierać powiadomienia przy każdym [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odwołania został rozwiązany. (Funkcja używa się asystentów diagnostycznych, a nie przez aplikacje produkcyjne.) Diagnostycznych Asystenta, takich jak funkcje programu Visual Studio "Edit-and-Continue" może być zaktualizowanie używa wszystkich zasobów podczas jego wartość w <xref:Windows.UI.Xaml.ResourceDictionary> zmiany. WPF robi to automatycznie dla [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) odwołania, ale celowo nie jest to [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odwołania. Począwszy od programu .NET Framework 4.7.2 diagnostycznych Asystenta można użyć te powiadomienia do odnalezienia tych zastosowań statycznych zasobów. 

Powiadomienie jest implementowany przez nowe <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> zdarzeń:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```
```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

To zdarzenie jest wywoływane zawsze, gdy środowisko uruchomieniowe rozpoznaje [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odwołania. <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> Argumentów opisano rozdzielczość i wskazywać obiektu, a właściwość hostujących [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odwołania i <xref:Windows.UI.Xaml.ResourceDictionary> i klucz używany do rozpoznawania:

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

Zdarzenie nie jest wywoływane (i jego `add` metody dostępu jest ignorowane) chyba że <xref:System.Windows.Diagnostics.VisualDiagnostics> jest włączona i [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) ustawiono zmiennej środowiskowej.

<a name="clickonce472" />
#### <a name="clickonce"></a>ClickOnce

HDPI aplikacje z obsługą formularzy systemu Windows, Windows Presentation Foundation (WPF) i Visual Studio Tools dla pakietu Office (środowisko VSTO) można wdrożyć przy użyciu technologii ClickOnce. Jeśli następujący wpis zostanie znaleziony w manifeście aplikacji, wdrożenie powiedzie się na platformie .NET Framework 4.7.2:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

Dla aplikacji Windows Forms obejście poprzednie ustawienia świadomości DPI w pliku konfiguracji aplikacji, a nie w manifeście aplikacji nie jest już niezbędne do pomyślnego wdrożenia ClickOnce.

<a name="v471"></a> 
## <a name="whats-new-in-the-net-framework-471"></a>Co to jest nowe w programie .NET Framework 4.7.1

.NET Framework 4.7.1 zawiera nowe funkcje w następujących obszarach:
 
- [Funkcje podstawowe](#core471)
- [Środowisko uruchomieniowe języka wspólnego (CLR)](#clr)
- [Sieci](#net471)
- [ASP.NET](#asp-net471) 

Ponadto najważniejszy w programie .NET Framework 4.7.1 jest lepsze ułatwień dostępu, dzięki czemu aplikacji zapewnić odpowiednie funkcje użytkowników korzystających z technologii pomocniczej. Aby uzyskać informacje na ulepszenia ułatwień dostępu w programie .NET Framework 4.7.1, zobacz [What's new in ułatwień dostępu w programie .NET Framework](whats-new-in-accessibility.md). 

<a name="core471" />
#### <a name="core"></a>Core

**Obsługa .NET 2.0 standardowe**

[.NET standard](~/docs/standard/net-standard.md) definiuje zestaw interfejsów API, które muszą być dostępne na każdym implementacja .NET obsługuje tej wersji standard. .NET Framework 4.7.1 w pełni obsługuje .NET 2.0 standardowe i dodaje [około 200 interfejsów API](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) są definiowane w .NET 2.0 standardowe i brakuje programu .NET Framework 4.6.1, 4.6.2 i 4.7. (Pamiętaj, że te wersje programu .NET Framework obsługują .NET 2.0 standardowe tylko wtedy, gdy dodatkowe pliki obsługi .NET Standard również są wdrażane w systemie docelowym). Aby uzyskać więcej informacji, zobacz "BCL — .NET 2.0 Pomoc techniczna Standard" w [środowiska uruchomieniowego .NET Framework 4.7.1 i funkcje kompilatora](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) wpis w blogu.

**Obsługa konfiguracji konstruktorów**

Konstruktorzy konfiguracji umożliwiają deweloperom wstrzyknąć i dynamicznie utworzyć ustawienia konfiguracji dla aplikacji w czasie wykonywania. Konfiguracja niestandardowa konstruktorów może służyć do modyfikowania istniejących danych w sekcji konfiguracji lub tworzenia sekcji konfiguracji całkowicie od nowa. Bez konstruktorów konfiguracji plikach .config są statyczne i ich ustawienia są definiowane na pewien czas, zanim aplikacja zostanie uruchomiona.

Aby utworzyć builder Konfiguracja niestandardowa, Twoje konstruktora pochodzi z klasy abstrakcyjnej <xref:System.Configuration.ConfigurationBuilder> klasy i zastąp jego <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> i <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. Możesz również definiować z konstruktorów w pliku Config. Aby uzyskać więcej informacji, zobacz sekcję "Konstruktorów konfiguracji" w [programu .NET Framework 4.7.1 ASP.NET i konfiguracji funkcji](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) wpis w blogu. 

**Wykrywanie funkcji środowiska wykonawczego**

<xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> Klasa udostępnia mechanizm Określ, czy wstępnie zdefiniowane funkcja jest obsługiwana w danej implementacji .NET w czasie kompilacji lub w czasie wykonywania. W czasie kompilacji kompilatora można sprawdzić, czy określone pole istnieje do ustalenia, czy funkcja jest obsługiwana; Jeśli tak, jego Emituj kod, który korzysta z tej funkcji. W czasie wykonywania, aplikacja może wywołać <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metody przed emitowanie kodu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Dodaj metodę pomocnika do opisywania funkcje obsługiwane przez środowisko uruchomieniowe](https://github.com/dotnet/corefx/issues/17116).

**Wartość krotki typy możliwy do serializacji**

Począwszy od programu .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> i jego skojarzone typy ogólne są oznaczone jako [Serializable](xref:System.SerializableAttribute), dzięki czemu serializacji binarnej. Powinna stanowić Migrowanie typów spójnej kolekcji, takie jak <xref:System.Tuple%603> i <xref:System.Tuple%604>, wartość krotki typów łatwiejsze. Aby uzyskać więcej informacji, zobacz "Kompilatora — ValueTuple jest możliwy do serializacji" w [środowiska uruchomieniowego .NET Framework 4.7.1 i funkcje kompilatora](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) wpis w blogu.

**Obsługa odwołań tylko do odczytu**

.NET Framework 4.7.1 dodaje <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>. Ten atrybut jest używany przez Kompilatory języka aby oznaczyć elementów członkowskich, które mają parametrów lub zwracanych typów ref tylko do odczytu. Aby uzyskać więcej informacji, zobacz "Kompilatora — obsługa dla ReadOnlyReferences" w [środowiska uruchomieniowego .NET Framework 4.7.1 i funkcje kompilatora](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) wpis w blogu. Informacje o wartościach zwracany ref, zobacz [Ref zwracać wartości i ref, zmienne lokalne (C# przewodnik)](~/docs/csharp/programming-guide/classes-and-structs/ref-returns.md) i [Ref zwracane wartości (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />
#### <a name="common-language-runtime-clr"></a>Środowisko uruchomieniowe języka wspólnego (CLR)

**Ulepszenia wydajności pamięci kolekcji**

Zmiany wyrzucanie elementów bezużytecznych (GC) w programie .NET Framework 4.7.1 zwiększyć ogólną wydajność, szczególnie w przypadku alokacji sterty obiektu duże (LOH). W programie .NET Framework 4.7.1 oddzielne blokady są używane dla małych obiektu sterty (raport) i LOH alokacji, dzięki czemu alokacji LOH nastąpić, gdy tło GC (BGC) jest profilach raport o kondycji. W związku z tym aplikacje wykonujące duża liczba przydziałów LOH powinna zostać wyświetlona zmniejszenia rywalizacji blokad alokacji i wydajności. Aby uzyskać więcej informacji, zobacz sekcję "Ulepszenia wydajności GC — środowisko uruchomieniowe" w [środowiska uruchomieniowego .NET Framework 4.7.1 i funkcje kompilatora](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features/) wpis w blogu. 

<a name="net471"/>
#### <a name="networking"></a>Obsługa sieci

**Obsługa Message.HashAlgorithm SHA-2**

.NET Framework 4.7 i wcześniejszych wersjach <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> wartości właściwości obsługiwane <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> i <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> tylko. Począwszy od programu .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, i <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> są również obsługiwane. Określa, czy ta wartość będzie faktycznie używana jest zależna od usługi MSMQ, ponieważ <xref:System.Messaging.Message> wystąpienie jest nie wyznaczania wartości skrótu, ale po prostu przekazuje wartości do usługi MSMQ. Aby uzyskać więcej informacji, zobacz sekcję "Obsługa SHA-2 Message.HashAlgorithm" w [funkcje .NET Framework 4.7.1 ASP.NET i konfiguracji](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features/) wpis w blogu.

<a name="asp-net471" />
#### <a name="aspnet"></a>ASP.NET

**Wykonanie kroków w aplikacjach ASP.NET**

ASP.NET przetwarza żądania w wstępnie zdefiniowanych potok, który obejmuje 23 zdarzenia. ASP.NET wykonuje każdy program obsługi zdarzeń jako etap wykonywania. W wersjach programu ASP.NET do .NET Framework 4.7 program ASP.NET nie można wykonać przepływu kontekstu wykonywania z powodu przełączanie między natywnych i zarządzanych wątków. Zamiast tego ASP.NET selektywnie przepływa tylko <xref:System.Web.HttpContext>. Począwszy od programu .NET Framework 4.7.1, <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> metoda umożliwia również modułów otoczenia dane mają zostać przywrócone. Ta funkcja jest przeznaczona dla danych śledzenia, profilowanie, diagnostyki lub transakcji, na przykład bibliotek, które interesujących przepływu wykonywania aplikacji. Aby uzyskać więcej informacji, zobacz "Funkcja platformy ASP.NET wykonywania kroku" w [programu .NET Framework 4.7.1 ASP.NET i konfiguracji funkcji](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) wpis w blogu. 

**Podczas analizowania HttpCookie ASP.NET**

.NET Framework 4.7.1 zawiera nową metodę <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, która udostępnia standardowy sposób tworzenia <xref:System.Web.HttpCookie> obiekt z ciągu i dokładnie Przypisz wartości pliku cookie, takie jak Data wygaśnięcia i ścieżkę. Aby uzyskać więcej informacji, zobacz "Podczas analizowania HttpCookie ASP.NET" w [programu .NET Framework 4.7.1 ASP.NET i konfiguracji funkcji](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) wpis w blogu. 

**Opcje wyznaczania wartości skrótu SHA-2 poświadczenia uwierzytelniania formularzy ASP.NET**

W .NET Framework 4.7 i starszych wersji platformy ASP.NET mogą deweloperów do przechowywania poświadczeń użytkownika z haseł mieszanych w plikach konfiguracji przy użyciu algorytmu MD5 lub SHA1. Począwszy od programu .NET Framework 4.7.1 ASP.NET obsługuje również nowe opcje wyznaczania wartości skrótu SHA-2 bezpiecznego takich jak SHA256, SHA384 i SHA512. SHA1 pozostaje domyślne, a algorytm skrótu innych niż domyślne można zdefiniować w pliku konfiguracji sieci web. Na przykład:

```xml
<system.web>
    <authentication mode="Forms">
        <forms loginUrl="~/login.aspx">
          <credentials passwordFormat="SHA512">
            <user name="jdoe" password="6D003E98EA1C7F04ABF8FCB375388907B7F3EE06F278DB966BE960E7CBBD103DF30CA6D61F7E7FD981B2E4E3A64D43C836A4BEDCA165C33B163E6BCDC538A664" />
          </credentials>
        </forms>
    </authentication>
</system.web>
```

<a name="v47"></a> 
## <a name="whats-new-in-the-net-framework-47"></a>Co to jest nowa w programie .NET Framework 4.7

.NET Framework 4.7 zawiera nowe funkcje w następujących obszarach:

- [Funkcje podstawowe](#Core47)
- [Sieci](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Aby uzyskać listę nowych interfejsów API dodane do .NET Framework 4.7, zobacz [zmiany interfejsu API programu .NET Framework 4.7](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) w witrynie GitHub. Aby uzyskać listę ulepszenia funkcji i poprawek w .NET Framework 4.7, zobacz [.NET Framework 4.7 Lista zmian](http://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) w witrynie GitHub.  Aby uzyskać dodatkowe informacje, zobacz [Announcing .NET Framework 4.7](https://blogs.msdn.microsoft.com/dotnet/2017/04/05/announcing-the-net-framework-4-7/) w blogu .NET.

<a name="Core47" />
#### <a name="core"></a>Core

.NET Framework 4.7 zwiększa serializacji przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:

**Ulepszone funkcje z kryptografii krzywej eliptycznej (ECC)***

W 4.7 Framework .NET `ImportParameters(ECParameters)` metody zostały dodane do <xref:System.Security.Cryptography.ECDsa> i <xref:System.Security.Cryptography.ECDiffieHellman> klasę, aby umożliwić dla obiekt do reprezentowania kluczem już nawiązane. `ExportParameters(Boolean)` Metody również została dodana do eksportowania klucza przy użyciu parametrów jawnych krzywą.

.NET Framework 4.7 również dodaje obsługę dodatkowych krzywych (w tym zestawie krzywej Brainpool) i został dodany wstępnie zdefiniowanych definicje łatwość z tworzenia za pomocą nowej <xref:System.Security.Cryptography.ECDsa.Create%2A> i <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> metody fabryki.

Widać [przykład ulepszenia kryptografii programu .NET Framework 4.7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) w witrynie GitHub.

**Lepszą obsługę znaki kontrolne przez elementu DataContractJsonSerializer**

W 4.7 Framework .NET <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializuje znaki kontrolne zgodnie z standard używany język ECMAScript 6. To zachowanie jest domyślnie włączone dla aplikacji, które odnoszą się do .NET Framework 4.7 i jest funkcji opcjonalnych dla aplikacji, które działają w ramach .NET Framework 4.7, ale docelowy poprzedniej wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [zmiany Retargetingu w .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />
#### <a name="networking"></a>Obsługa sieci

.NET Framework 4.7 powoduje dodanie następujących funkcji związanych z siecią:

**Domyślny system operacyjny obsługuje protokoły TLS***

Stosu protokołu TLS, która jest używana przez <xref:System.Net.Security.SslStream?displayProperty=nameWithType> i składniki w górę stosu, takich jak HTTP, FTP i SMTP, umożliwia deweloperom są używane protokoły TLS domyślne obsługiwane przez system operacyjny. Deweloperzy muszą nie dłużej kodowane wersji protokołu TLS.

<a name="ASP-NET47" />
#### <a name="aspnet"></a>ASP.NET

W 4.7 Framework .NET program ASP.NET zawiera następujące nowe funkcje:

**Obiekt rozszerzalności pamięci podręcznej**

Począwszy od .NET Framework 4.7, ASP.NET dodaje nowy zestaw interfejsów API, które umożliwiają deweloperom zastąpienia domyślnej implementacji ASP.NET do monitorowania pamięci i buforowania obiektów w pamięci. Deweloperzy teraz można zastąpić żadnego z następujących trzech składników opcji, jeśli implementacja ASP.NET nie jest odpowiedni:

- **Magazynu pamięci podręcznej obiektu**. Za pomocą nowej sekcji konfiguracji dostawcy pamięci podręcznej, deweloperzy można podłączyć w implementacjach nowej pamięci podręcznej obiektów dla aplikacji ASP.NET przy użyciu nowej **ICacheStoreProvider** interfejsu.
 
- **Monitorowanie pamięci**. Domyślny monitor pamięci w programie ASP.NET powiadamia aplikacji uruchomionej zbliża się limit skonfigurowany bajtów prywatnych procesu lub gdy komputer ma za mało całkowitej dostępnej fizycznej pamięci RAM. Gdy zbliża się tymi limitami, powiadomienia są uruchamiane. Dla pewnych aplikacji Powiadomienia są uruchamiane zbyt Zamknij skonfigurowanych limitami umożliwiające przydatne reakcji. Programiści mogą pisać teraz własne monitorów pamięci, aby zastąpić domyślną przy użyciu <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> właściwości.

- **Reakcje Limit pamięci**. Domyślnie program ASP.NET próbuje trim obiektu pamięci podręcznej i okresowo wywoływać <xref:System.GC.Collect%2A?displayProperty=nameWithType> gdy zbliża się limit bajtów prywatnych procesu. Dla pewnych aplikacji, częstotliwość wywołań <xref:System.GC.Collect%2A?displayProperty=nameWithType> lub ilość pamięci podręcznej, który jest usuwane są mało wydajne. Deweloperzy mogą teraz zastępujące lub uzupełniające domyślne zachowanie Subskrybuj **IObserver** implementacje do monitorowania pamięci aplikacji.

<a name="wcf47" />
#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) dodaje następujące funkcje i zmiany:

**Możliwość konfigurowania domyślnych ustawień zabezpieczeń wiadomości do protokołu TLS 1.1 i TLS 1.2**

Począwszy od .NET Framework 4.7 WCF umożliwia konfigurowanie TSL 1.1 lub protokołu TLS 1.2, oprócz protokołu SSL 3.0 i TSL 1.0 jako domyślny protokół zabezpieczeń wiadomości. To jest ustawienie opcjonalnych; Aby ją włączyć, należy dodać następujący wpis do pliku konfiguracji aplikacji:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" /> 
</runtime>
```

**Większą niezawodność aplikacji WCF i serializacji WCF**

Usługi WCF zawiera szereg zmiany kodu, które wyeliminować wyścigu, zwiększając wydajność i niezawodność opcji serializacji. Należą do nich następujące elementy:

- Lepszą obsługę mieszanie synchronicznego i asynchronicznego kodu w wywołaniach **SocketConnection.BeginRead** i **SocketConnection.Read**.
- Poprawia niezawodność podczas przerywania połączenia z **SharedConnectionListener** i **DuplexChannelBinder**.
- Poprawia niezawodność operacji serializacji podczas wywoływania metody <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> metody.
- Poprawia niezawodność podczas usuwania kelner wywołując **ChannelSynchronizer.RemoveWaiter** metody.

<a name="wf47" />
#### <a name="windows-forms"></a>Windows Forms

W 4.7 Framework .NET formularze systemu Windows, ulepsza obsługę wysokiej rozdzielczości monitorów.

**Wysokie DPI pomocy technicznej.**

Począwszy od aplikacji przeznaczonych .NET Framework 4.7, .NET Framework funkcje wysokiej rozdzielczości DPI dynamiczne obsługę aplikacji formularzy systemu Windows. Wysoka Obsługa DPI zwiększa układu i wyglądu formularzy i kontrolek na wysokiej rozdzielczości monitorów. DPI dynamicznej zmiany układu i wyglądu formularzy i kontrolki, gdy użytkownik zmieni współczynnik skali DPI lub wyświetlania aplikacji uruchomionych.

Wysokie DPI pomocy technicznej jest funkcji opcjonalnych, które można skonfigurować, definiując [ \<System.Windows.Forms.ConfigurationSection >](../configure-apps/file-schema/winforms/index.md) sekcji w pliku konfiguracyjnym aplikacji. Aby uzyskać więcej informacji o dodawaniu wysokiej rozdzielczości DPI pomocy technicznej i obsługa dynamicznego DPI w aplikacji formularzy systemu Windows, zobacz [obsługuje wysokiej rozdzielczości DPI w formularzach systemu Windows](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47"></a> 
#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

W 4.7 Framework .NET WPF zawiera następujące udoskonalenia:

**Obsługa stosu touch/pióro oparte na wiadomości WM_POINTER systemu Windows**

Masz teraz opcję użycia stosu touch/pióra, na podstawie [wiadomości WM_POINTER](https://msdn.microsoft.com/library/windows/desktop/hh454903.aspx) zamiast platformy usług odręczne (WISP) systemu Windows. Jest to funkcja zgłoszenie zgody na uczestnictwo w programie .NET Framework. Aby uzyskać więcej informacji, zobacz [zmiany Retargetingu w .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

**Nowej implementacji dla WPF drukowanie interfejsów API**

WPF do drukowania interfejsów API w <xref:System.Printing.PrintQueue?displayProperty=nameWithType> klasy wywołanie systemu Windows [drukowania dokumentu pakietu API](https://msdn.microsoft.com/library/windows/desktop/hh448418(v=vs.85).aspx) zamiast przestarzałych [API drukowania XPS](https://msdn.microsoft.com/library/windows/desktop/ff686814(v=vs.85).aspx). Aby wpływ tej zmiany na zgodność aplikacji, zobacz [zmiany Retargetingu w .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md). 

<a name="v462"></a> 
## <a name="whats-new-in-the-net-framework-462"></a>Co to jest nowe w programie .NET Framework 4.6.2

[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Zawiera nowe funkcje w następujących obszarach:

- [ASP.NET](#ASPNET462)

- [Kategorie znaków](#Strings)

- [Kryptografia](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#ClickOnce)

- [Konwertowanie formularzy systemu Windows i aplikacji WPF do aplikacji platformy uniwersalnej systemu Windows](#UWPConvert)

- [Ulepszenia debugowania](#Debug462)

Aby dodać listę nowych interfejsów API programu .NET Framework 4.6.2, zobacz [zmiany interfejsu API platformy .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) w witrynie GitHub. Aby uzyskać listę ulepszenia funkcji i poprawek w programie .NET Framework 4.6.2, zobacz [.NET Framework 4.6.2 Lista zmian](http://go.microsoft.com/fwlink/?LinkId=708778) w witrynie GitHub.  Aby uzyskać dodatkowe informacje, zobacz [o .NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/) w blogu .NET.

<a name="ASPNET462"></a> 
### <a name="aspnet"></a>ASP.NET
 W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], program ASP.NET zawiera następujące udoskonalenia:

 **Ulepszona obsługa zlokalizowanego komunikatów o błędach w modułów sprawdzania poprawności danych adnotacji**

 Moduły weryfikacji adnotacji danych służą do sprawdzania poprawności, dodając co najmniej jeden atrybut do właściwości klasy. Ten atrybut <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element definiuje tekst komunikatu o błędzie, jeśli weryfikacja zakończy się niepowodzeniem. Począwszy od [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET ułatwia lokalizowanie komunikaty o błędach. Komunikaty o błędach zostaną zlokalizowane, jeśli:

1.  <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> Podano w atrybucie sprawdzania poprawności.

2.  Plik zasobu jest przechowywany w folderze App_LocalResources.

3.  Nazwa pliku zlokalizowanych zasobów ma postać `DataAnnotation.Localization.{` *nazwa*`}.resx`, gdzie *nazwa* jest w formacie nazwy kultury *atrybutu languageCode* `-` *kod kraju/regionu* lub *atrybutu languageCode*.

4.  Nazwa klucza zasobu jest przypisany do ciągu <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atrybutu i jego wartość jest zlokalizowana komunikat.

 Na przykład następującego atrybutu adnotacji danych określa domyślną kulturę komunikat o błędzie dla nieprawidłowy klasyfikacji.

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

 Następnie możesz utworzyć plik zasobów DataAnnotation.Localization.fr.resx, którego klucz jest ciąg komunikat błędu, którego wartość jest zlokalizowany komunikat. Plik musi znajdować się w `App.LocalResources` folderu. Na przykład Oto klucz i wartość w komunikat o błędzie zlokalizowanych język francuski (fr):

| Nazwa                                 | Wartość                                     |
| ------------------------------------ | ----------------------------------------- |
| Klasyfikacja musi wynosić od 1 do 10. | Uwaga la ętre doit obejmują entre 1 et 10. |

 Ponadto lokalizacja adnotacji danych jest otwarty. Deweloperzy można dodać własne dostawcy lokalizatora ciąg zaimplementowanie <xref:System.Web.Globalization.IStringLocalizerProvider> interfejs do przechowywania lokalizacja ciągu w innym innych niż w pliku zasobu.

 **Obsługa Async z dostawcami magazynu stanu sesji**

 ASP.NET umożliwia teraz umożliwiające zwracanie zadań metody mają być używane z dostawcami magazynu stanu sesji, umożliwiając aplikacji ASP.NET można pobrać skalowalność zalet asynchronicznej. To jest obsługiwane operacje asynchroniczne ze stanem sesji przechowuje dostawców, program ASP.NET zawiera nowy interfejs <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, który dziedziczy z <xref:System.Web.IHttpModule> i umożliwia deweloperom wdrażanie własnych stanu sesji modułu i async sesji dostawców magazynu. Interfejs jest zdefiniowane w następujący sposób:

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

 Ponadto <xref:System.Web.SessionState.SessionStateUtility> klasa zawiera dwie nowe metody <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> i <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, który może służyć do obsługi operacji asynchronicznych.

 **Obsługa Async dostawców pamięci podręcznej danych wyjściowych**

 Począwszy od [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], umożliwiające zwracanie zadań metody może służyć z dostawcami pamięci podręcznej danych wyjściowych do zapewnienia skalowalności zalet asynchronicznego.  Dostawców, które implementują tych metod redukcję blokady wątku na serwerze sieci web i poprawić skalowalność usługi ASP.NET.

 Zostały dodane następujące interfejsy API do obsługi asynchroniczne dostawców pamięci podręcznej danych wyjściowych:

- <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> Klasy, która dziedziczy po klasie <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> i umożliwia deweloperom wdrażanie asynchronicznej dostawcy pamięci podręcznej danych wyjściowych.

- <xref:System.Web.Caching.OutputCacheUtility> Klasy, która udostępnia metody pomocnicze do konfigurowania wyjściowej pamięci podręcznej.

- 18 nowych metod w <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> klasy. Obejmują one <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, i <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.

- 2 nowych metod w <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> klasy: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> i <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.

- 2 nowych metod w <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> klasy: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> i <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.

- 2 nowych metod w <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> klasy: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> i <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.

- W <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> klasy <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> metody.

- W <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metody.

<a name="Strings"></a> 
### <a name="character-categories"></a>Kategorie znaków
 Znaki w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] są klasyfikowane na podstawie [Unicode Standard, wersja 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/). W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] i [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], znaków zostały sklasyfikowane na podstawie kategorii znaków Unicode 6.3.

 Obsługa Unicode 8.0 jest ograniczona do klasyfikacji znaków przez <xref:System.Globalization.CharUnicodeInfo> klas i typów i metod, które polegać na nich. Obejmują one <xref:System.Globalization.StringInfo> klasy przeciążone <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> metody i [klasy znaku](../../../docs/standard/base-types/character-classes-in-regular-expressions.md) rozpoznawane przez aparat wyrażeń regularnych .NET Framework.  Porównanie znaków i ciąg sortowania ta zmiana nie ma wpływu i są nadal korzysta na podstawowym systemie operacyjnym lub w systemach Windows 7, w danych znakowych dostarczane przez program .NET Framework.

 Zmiany w kategorie znaków z Unicode 6.0, 7.0 Unicode, zobacz [Unicode Standard, wersja 7.0.0](http://www.unicode.org/versions/Unicode7.0.0/) w witrynie sieci Web konsorcjum Unicode. Aby zmiany z Unicode 7.0 Unicode 8.0, zobacz [Unicode Standard, wersja 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) w witrynie sieci Web konsorcjum Unicode.

<a name="Crypto462"></a> 
### <a name="cryptography"></a>Kryptografia

 **Obsługa X509 certyfikaty zawierające DSA FIPS 186 3**

 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Dodaje obsługę DSA (cyfrowego algorytm podpisu) X509 certyfikatów, której klucze przekracza FIPS limit 1024-bitowe 186-2.

 Oprócz obsługi większych rozmiarów klucza FIPS 186-3 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] pozwala na korzystanie z podpisów z rodziny SHA-2 algorytmów wyznaczania wartości skrótu (SHA256, SHA384 i SHA512). FIPS 186 3 pomoc techniczna jest świadczona przez nowy <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> klasy.

 Zgodnie z najnowszych zmian w <xref:System.Security.Cryptography.RSA> klasy w .NET Framework 4.6 i <xref:System.Security.Cryptography.ECDsa> klasa w programie .NET Framework 4.6.1, <xref:System.Security.Cryptography.DSA> abstrakcyjnej klasy podstawowej w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ma dodatkowe metody, aby umożliwić wywołującym użyć tej funkcji funkcje bez rzutowania. Możesz wywołać <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> — metoda rozszerzenia do podpisywania danych, jak przedstawiono na poniższym przykładzie.

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb 
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

 Pozwala wywoływać <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> — metoda rozszerzenia, aby sprawdzić podpisane dane, jak przedstawiono na poniższym przykładzie.

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

 **Zwiększenia przejrzystości dla danych wejściowych do procedury wyprowadzania klucza ECDiffieHellman**

 .NET Framework 3.5 dodano obsługę Ellipic krzywej Diffie-Hellman klucza umowy z trzech różnych procedury funkcja wyprowadzania klucza (KDF). Dane wejściowe procedury i procedury, zostały skonfigurowane za pomocą właściwości na <xref:System.Security.Cryptography.ECDiffieHellmanCng> obiektu. Ale ponieważ nie wszystkie procedury odczytać co właściwości wejściowej, wystarczającą ilość miejsca na pomyłek w przeszłości dewelopera.

 Aby rozwiązać ten w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], dodano następujące trzy metody <xref:System.Security.Cryptography.ECDiffieHellman> klasy podstawowej na bardziej precyzyjnie reprezentują te procedury KDF i ich dane wejściowe:

|ECDiffieHellman — metoda|Opis|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Pochodzi materiału klucza przy użyciu formuły<br /><br /> SKRÓT (secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> SKRÓT (secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> gdzie *x* jest obliczana wynik algorytmu Diffie-Hellman WE.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Pochodzi materiału klucza przy użyciu formuły<br /><br /> Metoda HMAC (hmacKey, secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> Metoda HMAC (hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> gdzie *x* jest obliczana wynik algorytmu Diffie-Hellman WE.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Pochodzi materiału klucza przy użyciu algorytmu wyliczającego TLS pseudolosowego — funkcja (PRF).|

 **Obsługa szyfrowania symetrycznego klucza utrwalone**

 Biblioteka Kryptografia systemu Windows (CNG) dodano obsługę przechowywania kluczy symetrycznych utrwalonego i przy użyciu kluczy symetrycznych przechowywane sprzętu i [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] mades możliwe dla deweloperów skorzystać z tej funkcji.  Ponieważ pojęcie nazwy kluczy i kluczy dostawców jest konkretnej implementacji, za pomocą tej funkcji wymaga przy użyciu konstruktora typów konkretną implementację zamiast fabryki preferowane podejście (takie jak wywołania `Aes.Create`).

 Istnieje Obsługa utrwalone klucza szyfrowania symetrycznego AES (<xref:System.Security.Cryptography.AesCng>) i algorytmu 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algorytmów. Na przykład:

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb 
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

 **Obsługa SignedXml wyznaczania wartości skrótu SHA-2**

 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Dodaje obsługę do <xref:System.Security.Cryptography.Xml.SignedXml> klasy dla metod podpisu RSA SHA256, RSA SHA384 i RSA SHA512 PKCS #1 i odwołanie SHA256, SHA384 i SHA512 algorytmy skrótu.

 Stałe identyfikatora URI są narażone na <xref:System.Security.Cryptography.Xml.SignedXml>:

|Pole SignedXml|Stała|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Wszystkie programy, które zostały zarejestrowane niestandardowego <xref:System.Security.Cryptography.SignatureDescription> obsługi do <xref:System.Security.Cryptography.CryptoConfig> Aby dodać obsługę algorytmy te będą nadal działać jak w przeszłości, ale ponieważ ma teraz domyślne platformy, <xref:System.Security.Cryptography.CryptoConfig> rejestracji nie jest już niezbędne.

<a name="SQLClient"></a> 
### <a name="sqlclient"></a>SqlClient
 .NET framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) obejmuje następujące nowe funkcje w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:

 **Pula połączeń i limity czasu z bazy danych Azure SQL**

 Po włączeniu puli połączeń i przekroczenie limitu czasu lub inny błąd logowania, wyjątek jest buforowana, i pamięci podręcznej wyjątku w kolejnych próba dalej 5 sekund na 1 minutę.  Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia buforowanie (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).

 To zachowanie nie jest pożądane, łącząc się z bazy danych SQL Azure, ponieważ próby nawiązania połączenia może zakończyć się niepowodzeniem z błędami przejściowymi, które zwykle są szybko odzyskane. Aby lepiej Optymalizuj środowisko ponów próbę połączenia, połączenie puli blokowania okres, w którym działanie zostanie usunięta po awarii połączeń z bazami danych SQL Azure.

 Dodawanie nowej `PoolBlockingPeriod` — słowo kluczowe umożliwia wybranie okresu blokowania najlepiej nadaje się do aplikacji. Wartości:

 `Auto` Puli połączeń blokuje okresu dla aplikacji, która łączy się z bazą danych SQL Azure jest wyłączona, a puli połączeń blokuje okresu dla aplikacji, która łączy do dowolnego wystąpienia programu SQL Server jest włączona. Jest to wartość domyślna. Jeśli nazwa punktu końcowego serwera kończy się na następujących, są one uznawane za baz danych SQL Azure:

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

 `AlwaysBlock` Połączenia czasu blokowania puli jest zawsze włączone.

 `NeverBlock` Połączenia czasu blokowania puli jest zawsze wyłączona.

 **Rozszerzenia dla zawsze zaszyfrowane**

 SQLClient wprowadzono dwie ulepszenia zawsze szyfrowane:

- Aby zwiększyć wydajność sparametryzowanych zapytań dotyczących bazy danych zaszyfrowanych kolumn, teraz są buforowane metadane szyfrowania parametrów zapytania. Z <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> ustawioną właściwość `true` (która jest wartością domyślną), gdy tego samego zapytania została wywołana wiele razy, klient pobiera metadane parametrów z serwera tylko raz.

- Wpisy klucza szyfrowania kolumny w pamięci podręcznej klucza są teraz usunięty po przedział czasu można skonfigurować, ustawić za pomocą <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> właściwości.

<a name="WCF"></a> 
### <a name="windows-communication-foundation"></a>Windows Communication Foundation
 W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Communication Foundation została rozszerzona w następujących obszarach:

 **Obsługa zabezpieczeń transportu WCF certyfikaty przechowywane przy użyciu CNG**

 Zabezpieczenia transportu WCF obsługuje certyfikaty przechowywane przy użyciu biblioteki Kryptografia systemu Windows (CNG). W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ta obsługa jest ograniczona do korzystania z certyfikatów za pomocą klucza publicznego, który ma długość wykładnika nie więcej niż 32-bitowy. Gdy odpowiedniej aplikacji [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ta funkcja jest domyślnie włączona.

 Dla aplikacji, które odnoszą się do [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i wcześniejszych, ale są uruchomione na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], można włączyć tę funkcję, dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części app.config lub web.config plik.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

Ponadto można to zrobić programowo z kodem podobne do poniższych:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

 **Klasa klasa DataContractJsonSerializer lepszą obsługę wielu reguł korygowania czasu letniego**

 Klienci mogą użyć ustawienia konfiguracji aplikacji, aby określić, czy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> klasa obsługuje wiele reguł dopasowania dla jednej strefie czasowej. Jest to funkcji opcjonalnych. Aby go włączyć, Dodaj następujące ustawienie do pliku app.config:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Gdy ta funkcja jest włączona, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiekt używa <xref:System.TimeZoneInfo> wpisz zamiast <xref:System.TimeZone> typu do deserializacji danych daty i godziny. <xref:System.TimeZoneInfo> obsługuje wiele reguł korygowania, dzięki czemu możliwe do pracy z danych historycznych strefy czasowej.   <xref:System.TimeZone> nie.

Aby uzyskać więcej informacji na temat <xref:System.TimeZoneInfo> struktury i zmiany strefy czasowej, zobacz [Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md).

**NetNamedPipeBinding najlepszego dopasowania**

 Usługi WCF jest nowe ustawienie aplikacji, które można ustawić dla aplikacji klienckich, aby upewnić się, że zawsze działają z usługą nasłuchiwania URI, który najlepiej pasuje do jednej, ich żądanie. To ustawienie aplikacji ustawioną `false` (ustawienie domyślne), jest możliwe w przypadku klientów z <xref:System.ServiceModel.NetNamedPipeBinding> próbuje połączyć się z usługą nasłuchiwanie na identyfikatorze URI, który jest podciągiem żądanego identyfikatora URI.

 Na przykład klient próbuje nawiązać nasłuchuje usługa w `net.pipe://localhost/Service1`, ale inną usługę na tym komputerze, na którym działa z uprawnieniami administratora prowadzi nasłuchiwanie na `net.pipe://localhost`. To ustawienie aplikacji ustawioną `false`, klient będzie podjął próbę nawiązania niewłaściwej usługi. Po ustawieniu ustawienia aplikacji na `true`, klient będzie zawsze łączyć się najlepiej dopasowaną usługi.

> [!NOTE]
>  Klienci używający <xref:System.ServiceModel.NetNamedPipeBinding> znaleźć usługi na podstawie adres podstawowy usługi (jeśli istnieje) zamiast adres punktu końcowego pełna. Aby upewnić się, to ustawienie zawsze działa usługa należy używać unikatowy adres podstawowy.

 Aby włączyć tę zmianę, Dodaj następujące ustawienie aplikacji w pliku App.config lub Web.config aplikacji klienta:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

 **Protokół SSL 3.0 nie jest domyślnym protokołem**

 Używając NetTcp z zabezpieczeń transportu i typu poświadczeń certyfikatu protokołu SSL 3.0 nie jest już domyślnym protokołem używane do negocjowania bezpiecznego połączenia. W większości przypadków należy bez wpływu na istniejące aplikacje, ponieważ protokołu TLS 1.0 znajduje się na liście protokół NetTcp. Wszyscy istniejący klienci powinno być możliwe do negocjowania połączenia przy użyciu na co najmniej protokołu TLS 1.0. Jeśli wymagana jest Ssl3, użyj jednej z następujących mechanizmów konfiguracji można dodać go do listy wynegocjowanym protokołów.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> Właściwości

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> Właściwości

- [ \<Transportu >](../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) sekcji [ \<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) sekcji

- [ \<SslStreamSecurity >](../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) sekcji [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) sekcji

<a name="WPF462"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Presentation Foundation została rozszerzona w następujących obszarach:

 **Sortowanie grupy**

 Aplikacja, która używa <xref:System.Windows.Data.CollectionView> obiektu do grupowania danych teraz można jawnie deklarować sposób sortowania w grupach. Jawne sortowania adresów występuje problem z systemem innym niż intuicyjne kolejności, gdy aplikacji dynamicznie dodaje lub usuwa grup lub zmianie wartości właściwości elementu objętego grupowania. On również zwiększyć wydajność procesu tworzenia grupy przez przeniesienie porównania właściwości grupowania z sortowania pełnej kolekcji do sortowania grup.

 Do obsługi grupy sortowania, nowe <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> i <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> właściwości opisują sposób sortowania kolekcji grupy utworzonej przez <xref:System.ComponentModel.GroupDescription> obiektu. To jest odpowiednikiem sposób o identycznej nazwie <xref:System.Windows.Data.ListCollectionView> właściwości opisują sposób sortowania elementów danych.

 Dwa nowe statycznej właściwości <xref:System.Windows.Data.PropertyGroupDescription> klasy <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> i <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, może służyć do najbardziej typowych przypadkach.

 Na przykład następujące dane grupy XAML przez okres ważności, grup wiek w kolejności rosnącej sortowania i grupowania elementów w każdej grupie wieku przez nazwisko.

```xaml
<GroupDescriptions>
     <PropertyGroupDescription 
         PropertyName="Age" 
         CustomSort= 
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

 **Obsługa klawiatura programowa**

 Elastyczne Obsługa klawiatury umożliwia śledzenie w aplikacjach WPF przez automatyczne wywoływanie i odrzucanie nowego klawiatura programowa w systemie Windows 10, po odebraniu przez formant, który może zająć tekstową wprowadzania dotykowego fokus.

 W poprzednich wersjach programu .NET Framework aplikacje WPF nie mogą zrezygnować do śledzenia bez wyłączenie obsługi gestów pióra/touch WPF fokus.  W związku z tym aplikacje WPF musisz wybrać między pełną obsługę touch WPF lub zależą od podwyższenia poziomu myszy systemu Windows.

 **Rozdzielczości monitora**

 Do obsługi ostatnie mnożenie środowiska wysokiej rozdzielczości i hybrydowych DPI dla aplikacji WPF, WPF w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] umożliwia świadomości-monitor. Zobacz [przykłady i przewodnik dewelopera po](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) w witrynie GitHub, aby uzyskać więcej informacji o sposobie włączania aplikacji WPF stają się pamiętać DPI dla monitora.

 W poprzednich wersjach programu .NET Framework aplikacje WPF to system-DPI. Innymi słowy interfejs użytkownika aplikacji jest skalowana przez system operacyjny, zgodnie z potrzebami, w zależności od rozdzielczości monitora, na którym aplikacja jest renderowany. ,

 Dla aplikacji do uruchamiania [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], można wyłączyć rozdzielczości monitora zmian w aplikacji WPF przez dodanie instrukcji konfiguracji do [ \<środowiska uruchomieniowego >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji konfiguracji aplikacji, plików w następujący sposób:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462"></a> 
### <a name="windows-workflow-foundation-wf"></a>Program Windows Workflow Foundation (WF)
 W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], programu Windows Workflow Foundation została rozszerzona w następującym obszarze:

 **Obsługa wyrażeń C# i IntelliSense w Projektancie WF Re-hosted**

 Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], WF obsługuje wyrażeń C#, zarówno w projektancie programu Visual Studio i w przepływach pracy kodu. Re-hosted projektanta przepływów pracy jest kluczowym elementem WF umożliwiający projektanta przepływów pracy w aplikacji poza programem Visual Studio (na przykład na platformie WPF).  Windows Workflow Foundation udostępnia możliwość obsługi wyrażeń C# i IntelliSense w Projektancie przepływów pracy Re-hosted. Aby uzyskać więcej informacji, zobacz [blogu Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).

 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` W wersjach programu .NET Framework starszych niż [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], IntelliSense projektanta WF został przerwany, gdy klient odtwarza projektu przepływu pracy w programie Visual Studio. Kompilacja projektu zakończy się pomyślnie, gdy typy przepływu pracy nie zostały znalezione w Projektancie i ostrzeżeń z IntelliSense dla Brak typów przepływu pracy są wyświetlane w **listy błędów** okna. [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Rozwiązuje ten problem i udostępnia IntelliSense.

 **Aplikacje V1 przepływu pracy z przepływu pracy śledzenia na teraz być uruchamiane w trybie FIPS**

 Maszyny włączono obsługę trybu zgodności ze standardem FIPS można teraz pomyślnie uruchomić przepływ pracy w wersji 1 stylu aplikacji z przepływem pracy śledzenia na. Aby włączyć ten scenariusz, musisz wprowadzić następujące zmiany do pliku app.config:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

 Jeśli w tym scenariuszu nie jest włączona, działania aplikacji w dalszym ciągu wygeneruje wyjątek z komunikatem "Ta implementacja nie jest częścią systemu Windows Platform FIPS zatwierdzone algorytmy kryptograficzne."

 **Ulepszenia przepływu pracy podczas używania aktualizacji dynamicznej z projektanta przepływów pracy w usłudze Visual Studio**

 Projektanta przepływów pracy, Projektant działań schemat blokowy i innych projektantów działań przepływu pracy teraz pomyślnie załadować i wyświetlić przepływy pracy, które zostały zapisane po wywołaniu <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metody. W wersjach programu .NET Framework, przed [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], podczas ładowania pliku XAML w programie Visual Studio dla przepływu pracy, który został zapisany po wywołaniu <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> może spowodować następujące problemy:

- Projektant przepływu pracy nie można poprawnie załadować pliku XAML (gdy <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> znajduje się na końcu wiersza).

- Schemat blokowy działania Designer lub innych projektantów działań przepływu pracy mogą być wyświetlane wszystkie obiekty w ich lokalizacje domyślne, w przeciwieństwie do wartości właściwości dołączone.

<a name="ClickOnce"></a> 
### <a name="clickonce"></a>ClickOnce
 ClickOnce została zaktualizowana do obsługi protokołu TLS 1.1 i TLS 1.2, oprócz protokołu 1.0, który już obsługuje. ClickOnce automatycznie wykrywa, który protokół jest wymagana. żadne dodatkowe czynności w aplikacji ClickOnce są wymagane do włączenia protokołu TLS 1.1 i 1.2 pomocy technicznej.

<a name="UWPConvert"></a> 
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Konwertowanie formularzy systemu Windows i aplikacji WPF do aplikacji platformy uniwersalnej systemu Windows
 System Windows oferuje możliwości do istniejącej aplikacji klasycznych systemu Windows, w tym również aplikacje WPF i formularze systemu Windows do systemu Windows platformy Uniwersalnej. Ta technologia działa jako mostka, umożliwiając stopniowo migrację podstawowej istniejący kod do platformy uniwersalnej systemu Windows, a tym samym Przywracanie aplikacji do wszystkich urządzeń z systemem Windows 10.

 Przekonwertowane aplikacje komputerowe uzyskać podobne do tożsamości aplikacji w aplikacji platformy uniwersalnej systemu Windows, co sprawia, że interfejsów API platformy uniwersalnej systemu Windows jest dostępny, aby włączyć funkcje, takie jak kafelki na żywo i powiadomienia tożsamości aplikacji. Aplikacja nadal zachowywać się jak poprzednio i działa jako aplikacja pełnego zaufania. Po przekonwertowaniu aplikacji, proces kontenera aplikacji można dodać do istniejącej proces pełnego zaufania, aby dodać interfejs użytkownika adaptacyjną. Gdy wszystkie funkcje są przenoszone do procesu kontenera aplikacji, można usunąć procesu pełnego zaufania i nowej aplikacji platformy uniwersalnej systemu Windows mogą być udostępniane do wszystkich urządzeń z systemem Windows 10.

<a name="Debug462"></a> 
### <a name="debugging-improvements"></a>Ulepszenia debugowania
 *Niezarządzanych API — debugowanie* została rozszerzona w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] do analizowania dodatkowe podczas <xref:System.NullReferenceException> jest zgłaszany, dzięki czemu można określić, które zmiennej w jednym wierszu kodu źródłowego jest `null`.   Aby obsługiwać ten scenariusz, następujące interfejsy API zostały dodane do niezarządzanego API debugowania.

- [ICorDebugCode4](../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md), i [ICorDebugVariableHomeEnum](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interfejsów, które ujawnia natywnego domach zarządzanych zmiennych. Dzięki temu debugery na wykonanie analizy przepływu kodu podczas <xref:System.NullReferenceException> występuje oraz pracy wstecz do określenia zarządzanych zmiennej, która odpowiada natywnego lokalizacji, która została `null`.

- [ICorDebugType2::GetTypeID](../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metody przewiduje ICorDebugType do mapowania [COR_TYPEID](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), dzięki czemu debuger w celu uzyskania [COR_TYPEID](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bez wystąpienia z ICorDebugType. Istniejących interfejsów API [COR_TYPEID](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) następnie może służyć do określania układu klasy tego typu.

<a name="v461"></a> 
## <a name="whats-new-in-the-net-framework-461"></a>Co to jest nowe w programie .NET Framework 4.6.1
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Zawiera nowe funkcje w następujących obszarach:

- [Kryptografia](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profilowanie](#Profile461)

- [Narzędzie NGen](#NGEN461)

 Aby uzyskać więcej informacji na temat [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], zobacz następujące tematy:

- [.NET Framework 4.6.1 listy zmian](http://go.microsoft.com/fwlink/?LinkId=622964)

- [Zgodność aplikacji w wersji 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

- [Diff interfejsu API programu .NET Framework](http://go.microsoft.com/fwlink/?LinkId=622989) (w serwisie GitHub)

<a name="Crypto"></a> 
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Kryptografia: Obsługa X509 certyfikaty zawierające ECDSA
 .NET Framework 4.6 dodano RSACng obsługę X509 certyfikatów. [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Dodaje obsługę ECDSA (Elliptic cyfrowego podpisu algorytm krzywej) X509 certyfikatów.

 ECDSA oferuje lepszą wydajność i jest bardziej bezpieczne algorytmu kryptograficznego, niż RSA, zapewniając doskonałym wyborem zabezpieczeń TLS (Transport Layer), wydajność i skalowalność w przypadku wątpliwości dotyczących. Wdrożenia programu .NET Framework jest zawijana wywołuje istniejące funkcje systemu Windows.

 Poniższy przykład kodu pokazuje, jak łatwo jest generowanie podpis strumień bajtów przy użyciu ECDSA Obsługa nowych certyfikatów X 509 zawarte w [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].

 [!code-csharp[whatsnew.461.crypto#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
 [!code-vb[whatsnew.461.crypto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

 Zapewnia to oznaczone kontrastu kod potrzebny do generowania podpisu w .NET Framework 4.6.

 [!code-csharp[whatsnew.461.crypto#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
 [!code-vb[whatsnew.461.crypto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461"></a> 
### <a name="adonet"></a>ADO.NET
 Poniżej zostały dodane do ADO.NET:

**Zawsze zaszyfrowane obsługę sprzętu kluczy chronionych**

 ADO.NET obsługuje teraz przechowywania kluczy głównych kolumn zawsze zaszyfrowane natywnie w sprzętowych modułach zabezpieczeń (HSM). Z tej obsługi klienci mogą korzystać z kluczy asymetrycznych przechowywany w sprzętowych modułów zabezpieczeń bez konieczności pisania dostawców magazynu kluczy głównych kolumn niestandardowych i rejestrowania ich w aplikacji.

 Klienci muszą zainstalować HSM dostarczonym dostawcy usług Kryptograficznych lub dostawców magazynu kluczy CNG na komputery klienckie lub serwery aplikacji, aby uzyskać dostęp do danych zawsze zaszyfrowane chronione przy użyciu kluczy głównych kolumn przechowywane w module HSM.

 **Ulepszone <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> zachowanie połączenia dla funkcji AlwaysOn**
 
SqlClient automatycznie udostępnia teraz szybsze połączenia do grupy dostępności AlwaysOn (AG). Przezroczysty wykryje, czy aplikacja nawiązuje połączenie z grupy dostępności funkcji AlwaysOn (grupy dostępności) w innej podsieci i szybko odnajduje bieżącego aktywnego serwera i zapewnia połączenie z serwerem. Przed tą wersją aplikacji było ustawić parametry połączenia, aby uwzględnić `"MultisubnetFailover=true"` aby wskazać, że połączenia do grupy dostępności funkcji AlwaysOn. Bez ustawienia połączenia — słowo kluczowe na `true`, aplikacja może wystąpić limit czasu podczas nawiązywania połączenia z grupy dostępności funkcji AlwaysOn. W tej wersji aplikacji jest *nie* należy ustawić <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> do `true` już. Aby uzyskać więcej informacji o obsłudze SqlClient dla zawsze włączonych grup dostępności, zobacz [SqlClient obsługę wysokiej dostępności, odzyskiwania po awarii](../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 Windows Presentation Foundation zawiera wiele ulepszeń oraz zmiany.

 **Większa wydajność**

 Opóźnienie w wyzwalania zdarzenia touch został rozwiązany w [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Ponadto, wpisując w <xref:System.Windows.Controls.RichTextBox> formantu nie blokuje wątku renderowania podczas szybkiego danych wejściowych.

 **Ulepszenia sprawdzania pisowni**

 Moduł sprawdzania pisowni na platformie WPF została zaktualizowana na Windows 8.1 i nowszych wersjach systemu operacyjnego wykorzystać obsługuje sprawdzanie pisowni dodatkowych języków.  Nie została zmieniona w funkcji w wersjach systemu Windows przed Windows 8.1.

 Jak w poprzednich wersjach programu .NET Framework, w tym języku <xref:System.Windows.Controls.TextBox> kontrolować ora <xref:System.Windows.Controls.RichTextBox> bloku są wykrywane przez wyszukiwanie informacji w następującej kolejności:

- `xml:lang`, jeśli jest obecny.

- Bieżący język.

- Bieżącej kultury wątku.

 Aby uzyskać dodatkowe informacje na temat obsługi języków w programie WPF, zobacz [WPF wpis w blogu na temat funkcji platformy .NET Framework 4.6.1](http://go.microsoft.com/fwlink/?LinkID=691819).

 **Dodatkowa obsługa słowniki na użytkownika**

 W [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], WPF rozpoznaje słowniki, które są zarejestrowane globalnie. Ta funkcja jest dostępna, oprócz możliwości rejestrowania ich-control.

 W poprzednich wersjach programu WPF słowniki nie rozpoznał słowa wykluczenia i listy Autokorekty. Są one obsługiwane na Windows 8.1 i Windows 10 przy użyciu plików, które można umieścić w obszarze `%AppData%\Microsoft\Spelling\<language tag>` katalogu.  Te pliki mają zastosowanie następujące reguły:

- Pliki powinien mieć rozszerzenia .dic (dla słowa dodane), .exc (dla słów wykluczonych) lub .acl (dla Autokorekty).

- Pliki powinny być UTF-16 LE zwykłego tekstu, która rozpoczyna się z znacznik kolejności bajtów (BOM).

- Każdy wiersz powinien zawierać word (na listach word dodano i wykluczonych) lub parę Autokorekty z wyrazy oddzielone pionowy pasek ("&#124;") (na liście Autokorekty programu word).

- Pliki te są traktowane jako tylko do odczytu i nie są modyfikowane przez system.

> [!NOTE]
>  Te nowe formaty plików nie są bezpośrednio obsługiwane przez interfejsu API sprawdzania pisowni WPF i słowniki dostarczonych w aplikacjach WPF powinno być kontynuowane do korzystania z plików .lex.

**Przykłady**

 Istnieje szereg [przykłady WPF](https://msdn.microsoft.com/library/ms771633.aspx) w witrynie MSDN. Więcej niż 200 najpopularniejszych próbek (na podstawie ich użycia) zostanie przeniesiony do [repozytorium GitHub źródłowym Otwórz](https://github.com/Microsoft/WPF-Samples). Pomóż nam udoskonalić nasze przykłady, wysyłając żądania pobierania lub otwierania [problem GitHub](https://github.com/Microsoft/WPF-Samples/issues).

 **Rozszerzenia programu DirectX**

 Obejmuje WPF [pakietu NuGet](http://go.microsoft.com/fwlink/?LinkID=691342) zapewnia nowy implementacje <xref:System.Windows.Interop.D3DImage> ułatwia dla Ciebie na potrzeby współdziałania z DX10 i Dx11 zawartości. Kod dla tego pakietu był otwarty powierzając jej ich konserwację i jest dostępny [w serwisie GitHub](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461"></a> 
### <a name="windows-workflow-foundation-transactions"></a>Program Windows Workflow Foundation: transakcji
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> — Metoda za pomocą Menedżera transakcji rozproszonych, innego niż usługi MSDTC można podwyższyć poziomu transakcji. Możesz to zrobić przez określenie identyfikatora GUID transakcji promotor do nowego <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> przeciążenia. Jeśli ta operacja zakończy się pomyślnie, obowiązują ograniczenia nakładane na możliwości transakcji. Po promotor transakcji MSDTC nie jest zarejestrowany, throw następujących metod <xref:System.Transactions.TransactionPromotionException> ponieważ te metody wymagają promocji do usługi MSDTC:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

 Po promotor transakcji MSDTC nie jest zarejestrowany, należy użyć dla przyszłych trwałych rejestracji przy użyciu protokołów, które definiuje. <xref:System.Guid> Transakcji promotor można uzyskać za pomocą <xref:System.Transactions.Transaction.PromoterType%2A> właściwości. Jeśli transakcja wspiera, promotor transakcji zawiera <xref:System.Byte> tablica, która reprezentuje awansowana tokenu. Aplikację można uzyskać tokenu awansowana dla transakcji z systemem innym niż MSDTC awansowane z <xref:System.Transactions.Transaction.GetPromotedToken%2A> metody.

 Użytkownicy nowej <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> przeciążenia należy wykonać sekwencję wywołań w kolejności dla operacji podwyższenia poziomu pomyślnie. Te reguły są opisane w dokumentacji metody.

<a name="Profile461"></a> 
### <a name="profiling"></a>Profilowanie
 Niezarządzanego API profilowania został rozszerzony w następujący sposób:

 Lepszą obsługę dostępu do baz danych PDB w [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) interfejsu w ASP.Net 5, staje się coraz bardziej powszechne zestawy być skompilowany w pamięci przez Roslyn. Dla deweloperów, tworzenie narzędzi profilowania oznacza to, że pliki PDB, które kiedyś przeprowadzono serializacji na dysku może nie być już istnieje. Profiler narzędzi często używane pliki PDB do mapowania kodu wierszy źródłowych zadań, takich jak analiza wydajności pokrycia lub wiersz po wierszu kodu. [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) interfejs zawiera teraz dwa nowe metody, [ICorProfilerInfo7::GetInMemorySymbolsLength](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) i [ICorProfilerInfo7::ReadInMemorySymbols](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md) , aby zapewnić te narzędzia profilera z dostępu do danych PDB w pamięci, przy użyciu nowych interfejsów API, profiler może uzyskać zawartość pliku PDB w pamięci w postaci tablicy bajtów i go przetworzyć lub serializować go na dysku.

 Lepsze Instrumentacji z interfejsem ICorProfiler profilowania, którzy korzystają z `ICorProfiler` funkcji ReJit interfejsu API dla Instrumentacji dynamiczne można również zmodyfikować niektóre metadane. Wcześniej tych narzędzi można Instrumentacja IL w dowolnym momencie, ale metadanych można modyfikować tylko w czasie ładowania modułu. Ponieważ IL odwołuje się do metadanych, to ograniczona rodzaje instrumentacji, że może być wykonana. Firma Microsoft ma unosiło niektóre z tych ograniczeń, dodając [ICorProfilerInfo7::ApplyMetaData](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) metody do obsługi podzbiór zmiany metadanych po moduł ładowania, w szczególności przez dodanie nowych `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, i `UserString` rekordów. Ta zmiana umożliwia o wiele szerszy zakres o bieżąco instrumentacji.

<a name="NGEN461"></a> 
### <a name="native-image-generator-ngen-pdbs"></a>Pliki PDB (NGEN) Generator obrazu natywnego
 Śledzenie zdarzeń między komputerami umożliwia klientom profilu programu na komputerze A i wygląd profilowania danych z mapowaniem wiersz źródła na maszynie B. przy użyciu poprzednich wersji programu .NET Framework, użytkownik może skopiować wszystkie moduły i obrazów macierzystych z PROFILOWANEGO Maszyna do maszyny analizy, która zawiera PDB IL można utworzyć mapowania źródła do macierzystego. Podczas tego procesu może działać również w przypadku, gdy pliki są stosunkowo mały, takie jak w przypadku aplikacji telefonicznej, pliki mogą być bardzo duże w systemach komputerów i wymaga długiego czasu, aby skopiować.

 PDB Ngen NGen umożliwia tworzenie pliku PDB, który zawiera mapowania IL-native bez zależności pliku IL PDB. W naszym scenariuszu śledzenie zdarzeń między komputerami są wystarczające jest kopiowanie obrazu macierzystego PDB, wygenerowanego przez komputer A do B maszyny i użyj [debugowania interfejsu API dostępu](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) odczytać mapowania źródła do IL IL PDB i natywnego obraz w pliku PDB IL do macierzystego mapowania. Łączenie oba mapowania udostępnia mapowanie źródła do macierzystego. Ponieważ obraz macierzysty PDB jest znacznie mniejszy niż wszystkie moduły i obrazów natywnych, proces kopiowania z komputera, A na komputerze B przebiega szybciej.

<a name="v46"></a> 
## <a name="whats-new-in-net-2015"></a>Co to jest nowa w programie .NET 2015
 Wprowadza .NET 2015 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] i .NET Core. Niektóre nowe funkcje dotyczą zarówno i inne funkcje są specyficzne dla [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] lub [!INCLUDE[net_core](../../../includes/net-core-md.md)].

- **ASP.NET 5**

     .NET 2015 obejmuje ASP.NET 5, która jest gotowa implementacji .NET do tworzenia nowoczesnych aplikacji opartej na chmurze. ASP.NET 5 jest moduły, więc może zawierać tylko funkcje, które są wymagane w aplikacji. Można hostowanych w usługach IIS lub hosta samodzielnego w procesie niestandardowej, a na tym samym serwerze można uruchomić aplikacji z różnych wersji programu .NET Framework. Obejmuje on nowy system konfiguracji środowiska przeznaczonego do chmury wdrażania.

     MVC, Web API i stron sieci Web są ujednolicone w jedną o nazwie MVC 6 strukturę. Można tworzyć aplikacje ASP.NET 5 za pomocą nowych narzędzi programu Visual Studio 2015. Istniejące aplikacje będą działać w programie .NET Framework nowe; Jednak aby utworzyć aplikację, która używa MVC 6 lub SignalR 3, musi używać systemu projektu programu Visual Studio 2015.

     Aby uzyskać informacje, zobacz [ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238).

- **ASP.NET Updates**

    - **Opróżnianie odpowiedzi asynchronicznego opartego na zadaniach interfejsu API**

         Teraz program ASP.NET udostępnia prosty interfejs API oparty na zadaniach dla odpowiedzi asynchronicznych opróżnianie, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, umożliwiająca odpowiedzi do opróżnienia asynchronicznie przy użyciu danego języka `async/await` obsługuje.

    - `Model binding supports task-returning methods`

         W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ASP.NET dodaje funkcję wiązania modelu włączone to rozszerzalny, fokus kodu metoda operacje CRUD na podstawie danych w formularzach sieci Web stron i kontrolek użytkownika. Obsługuje teraz system wiązania modelu <xref:System.Threading.Tasks.Task>-zwracanie metody wiązania modelu. Ta funkcja umożliwia deweloperom formularzy sieci Web korzystać skalowalność zalet async z łatwością systemu powiązanie danych w przypadku nowszych wersji ORMs, łącznie z programu Entity Framework.

         Wiązanie modelu Async jest kontrolowane przez `aspnet:EnableAsyncModelBinding` ustawienia konfiguracji.

        ```xml
        <appSettings>
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
        </appSettings>
        ```

         W aplikacji docelowej [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], domyślne `true`. Na aplikacje działające na [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] który kątem starszej wersji programu .NET Framework, jest `false` domyślnie. Można ją włączyć przez ustawienie konfiguracji `true`.

    - **Obsługa protokołu HTTP/2 (z systemem Windows 10)**

         [HTTP/2](http://www.wikipedia.org/wiki/HTTP/2) nowej wersji protokołu HTTP, który zapewnia dużo lepsze wykorzystanie połączenia (mniej przechodzenia między klientem i serwerem), wynikiem jest niższe strony sieci web opóźnienia ładowania dla użytkowników.  Stron sieci Web (w przeciwieństwie do usługi) korzystają najbardziej z protokołu HTTP/2, ponieważ protokół optymalizuje wielu artefaktów żądanej w ramach jednej czynności. Dodano obsługę protokołu HTTP/2 do ASP.NET i .NET Framework 4.6. Ponieważ funkcji sieciowych w wielu warstw, nowe funkcje były wymagane w systemie Windows, usługi IIS i platformy ASP.NET, aby włączyć HTTP/2. Musi działać w systemie Windows 10 do używania protokołu HTTP/2 z platformy ASP.NET.

         HTTP/2 jest również obsługiwany i domyślnie włączone w systemie Windows 10 Windows uniwersalnych aplikacji platformy Uniwersalnej, które używają <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> interfejsu API.

         Aby zapewnić sposób użycia [PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE) funkcji w aplikacjach ASP.NET, nowej metody z dwa przeciążenia <xref:System.Web.HttpResponse.PushPromise%28System.String%29> i <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, został dodany do <xref:System.Web.HttpResponse> klasy.

        > [!NOTE]
        >  Natomiast ASP.NET 5 obsługuje HTTP/2, obsługę funkcji PUSH PROMISE nie została jeszcze dodane.

         Przeglądarki i serwer sieci web (IIS w systemie Windows) nie całą pracę. Nie trzeba wykonać wszelkie podnoszenia ciężki dla użytkowników.

         Większość [główne przeglądarki obsługują HTTP/2](http://www.wikipedia.org/wiki/HTTP/2), więc istnieje duże prawdopodobieństwo, że użytkownicy będą korzystać z obsługi protokołu HTTP/2, jeśli serwer obsługuje tę funkcję.

    - **Obsługa protokołu Token wiązania**

         Firma Microsoft i Google ma zostały współpracy nad nowe podejście do uwierzytelniania o nazwie [tokenu powiązania protokołu](https://github.com/TokenBinding/Internet-Drafts). Lokalna usługa jest tokeny uwierzytelniania (w pamięci podręcznej przeglądarki) może być kradzieży i używane przez mógłby uzyskać dostęp do zasobów w przeciwnym razie bezpieczne (np. konta bankowego) bez konieczności wprowadzania hasła lub innych uprzywilejowanych wiedzy. Nowy protokół ma na celu rozwiązania problemu.

         Token powiązania protokołu są realizowane w systemie Windows 10 jako funkcji przeglądarki. Aplikacje ASP.NET będzie uczestniczyć w protokole tak, że tokeny uwierzytelniania są weryfikowane się. Implementacji serwera i klienta ustanowić ochronę end-to-end określony przez protokół.

    - **Ciąg losowego algorytmów wyznaczania wartości skrótu**

         .NET Framework 4.5 wprowadzone [algorytmu wyznaczania wartości skrótu ciągu losowego](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Jednak go nie jest obsługiwana przez platformy ASP.NET z powodu ASP.NET niektóre funkcje zależne od stabilna wartość skrótu. W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], losowego algorytmów wyznaczania wartości skrótu ciągu są teraz obsługiwane. Aby włączyć tę funkcję, użyj `aspnet:UseRandomizedStringHashAlgorithm` ustawienia konfiguracji.

        ```xml
        <appSettings>
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
        </appSettings>
        ```

- **ADO.NET**

     ADO .NET obsługuje teraz funkcję zawsze zaszyfrowane dostępne w programu SQL Server 2016 Community Technology Preview 2 (CTP2). Zawsze zaszyfrowane programu SQL Server mogą wykonywać operacje na zaszyfrowanych danych i z aplikacją w zaufanym środowisku klienta, a nie na serwerze znajduje się najlepiej klucza szyfrowania. Zawsze zaszyfrowane zabezpiecza dane klienta, więc DBAs nie mają dostępu do danych w postaci zwykłego tekstu. Szyfrowania i odszyfrowywania danych działa w sposób niewidoczny dla użytkownika na poziomie sterownika, minimalizując zmiany, które nie zostały wprowadzone do istniejących aplikacji. Aby uzyskać więcej informacji, zobacz [zawsze zaszyfrowane (aparat bazy danych)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) i [zawsze zaszyfrowane (Programowanie klienta)](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **Kompilator JIT 64-bitowego do kodu zarządzanego**

     .NET Framework 4.6 funkcji nowej wersji przy użyciu kompilatora JIT 64-bitowych (pierwotnie nazwę kodową RyuJIT). Nowy kompilator 64-bitowy zapewnia znaczną poprawę wydajności przez starszego kompilatora JIT 64-bitowych. Nowy kompilator 64-bitowy jest włączone dla procesów 64-bitowym systemem na .NET Framework 4.6. Aplikacja zostanie uruchomiona w procesu 64-bitowego, jeśli jest on skompilowany jako 64-bitowa lub AnyCPU i działa na 64-bitowym systemie operacyjnym. Uwzględniono na przejście do nowego kompilatora jako przezroczysty, jak to możliwe, zmiany w zachowaniu są możliwe. Chcielibyśmy usłyszeć bezpośrednio o wszelkich problemach ze podczas używania nowego kompilatora JIT. Skontaktuj się z nami za pośrednictwem [Microsoft Connect](http://connect.microsoft.com/) Jeśli napotkasz problem, który może być związane z kompilator JIT 64-bitowych.

     Kompilator JIT 64-bitowych zawiera również funkcji przyspieszenia SIMD sprzętu w połączeniu z włączoną SIMD typów w <xref:System.Numerics> przestrzeni nazw, która umożliwia uzyskanie ulepszenia dobrą wydajność.

- **Ulepszenia modułu ładującego zestawu**

     Moduł ładujący zestawu teraz korzysta z pamięci wydajniej przez zwalnianie zestawów IL po załadowaniu odpowiedniego obrazu NGEN. Ta zmiana zmniejsza pamięci wirtualnej, co jest szczególnie przydatne w przypadku dużych aplikacji 32-bitowych (takiego jak Visual Studio) i pozwalają również zmniejszyć ilość pamięci fizycznej.

- **Klasa podstawowa Biblioteka zmiany**

     Dodano wiele nowych interfejsów API wokół do [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] na potrzeby scenariuszy z klucza. Należą do nich następujące zmiany i uzupełnienia:

    - **IReadOnlyCollection\<T > implementacji**

         Dodatkowe kolekcje implementować <xref:System.Collections.Generic.IReadOnlyCollection%601> takich jak <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601>.

    - **Wartość CultureInfo.CurrentCulture i CultureInfo.CurrentUICulture**

         <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości są teraz odczytu i zapisu, a nie tylko do odczytu. Po przypisaniu nowy <xref:System.Globalization.CultureInfo> obiektu tych właściwości bieżącej kultury wątku zdefiniowane przez `Thread.CurrentThread.CurrentCulture` właściwości i Interfejsie użytkownika bieżącego wątku kultury zdefiniowane przez `Thread.CurrentThread.CurrentUICulture` również zmienić właściwości.

    - **Ulepszenia dotyczące wyrzucania elementów bezużytecznych**

         <xref:System.GC> Zawiera teraz klasy <xref:System.GC.TryStartNoGCRegion%2A> i <xref:System.GC.EndNoGCRegion%2A> metod, które umożliwiają nie zezwalaj na odzyskiwanie pamięci podczas wykonywania ścieżkę krytyczną.

         Nowe przeciążenia <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metody umożliwia kontrolowanie czy zarówno sterty małego obiektu i sterty dużego obiektu są wycierana i kompaktowanie lub wycierana tylko.

    - **Typy włączone SIMD**

         <xref:System.Numerics> Przestrzeni nazw teraz obejmuje kilka włączone SIMD typów, takie jak <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, i <xref:System.Numerics.Vector4>.

         Ponieważ kompilator JIT 64-bitowych zawiera również funkcji przyspieszenia sprzętowego SIMD, są szczególnie istotne ulepszenia wydajności podczas korzystania z obsługą SIMD typów przez kompilator JIT 64-bitowych.

    - **Aktualizacje kryptografii**

         <xref:System.Security.Cryptography?displayProperty=nameWithType> Interfejsu API jest aktualizowana w celu obsługi [Windows CNG cryptography API](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx). Poprzednie wersje programu .NET Framework ma polegać wyłącznie na [wcześniejszej wersji systemu Windows API kryptografii](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx) jako podstawę <xref:System.Security.Cryptography?displayProperty=nameWithType> implementacji. Mamy żądań do obsługi interfejsu API CNG, ponieważ obsługuje on [algorytmów kryptograficznych nowoczesnych](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support), które są ważne w przypadku niektórych kategorii aplikacji.

         .NET Framework 4.6 obejmuje następujące nowe ulepszenia obsługi kryptografii Windows CNG API:

        - Zestaw metody rozszerzenia dla X509 certyfikatów, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` i `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, które zwracają wdrożenia usługi na podstawie CNG, a nie na podstawie CAPI wykonania, gdy jest to możliwe. (Niektóre kart inteligentnych itp., nadal wymaga CAPI i interfejsów API obsługi rezerwowego).

        - <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> Klasy, która udostępnia implementację CNG algorytmu RSA.

        - Rozszerzenia interfejsu API RSA, dzięki czemu typowych akcji nie wymagają już rzutowania. Na przykład szyfrowania danych przy użyciu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> obiekt wymaga kod podobnie do następującej w poprzednich wersjach programu .NET Framework.

             [!code-csharp[WhatsNew.Casting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
             [!code-vb[WhatsNew.Casting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

             Kod, który używa kryptografii nowych interfejsów API w .NET Framework 4.6 można ulegną w następujący sposób, aby uniknąć rzutowania.

             [!code-csharp[WhatsNew.Casting#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
             [!code-vb[WhatsNew.Casting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

    - **Obsługa konwersji daty i godziny do lub z czasu systemu Unix**

         Dodano następujące nowe metody <xref:System.DateTimeOffset> obsługuje konwertowania wartości daty i godziny z czasu systemu Unix lub struktury:

        - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - **Przełączniki zgodności**

         Nowe <xref:System.AppContext> klasa dodaje nową funkcją zgodności, która umożliwia autorom biblioteki na mechanizm uniform Wypisz dla nowych funkcji dla użytkowników. Definiuje on kontrakt luźno powiązane między składnikami, aby komunikować się rezygnacji z żądania. Ta możliwość jest zwykle ważny w przypadku zmian do istniejących funkcji. Z drugiej strony już istnieje niejawna zgody na nowych funkcji.

         Z <xref:System.AppContext>, zdefiniuj bibliotek i przełączniki zgodności Uwidacznianie podczas kod, który jest zależny od nich można ustawić tych przełączników wpłynąć na zachowanie biblioteki. Domyślnie udostępnia nowych funkcji w bibliotekach i zmieniają tylko (to znaczy zapewniają funkcje poprzednich) Jeśli jest ustawiona przełącznik.

         Aplikacja (lub biblioteki) mogą zadeklarować wartość przełącznika (która jest zawsze <xref:System.Boolean> wartość) definiujący zależnej biblioteki. Przełącznik jest zawsze niejawnie `false`. Ustawienia przełącznika `true` włączy ją. Jawne ustawienie przełącznika `false` udostępnia nowe zachowanie.

        ```csharp
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
        ```

         Biblioteka musi Sprawdź, czy klienta została zadeklarowana wartość przełącznika i odpowiednio działają na nim.

        ```csharp
        if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow)) 
        {
           // This is the case where the switch value was not set by the application. 
           // The library can choose to get the value of shouldThrow by other means. 
           // If no overrides nor default values are specified, the value should be 'false'. 
           // A false value implies the latest behavior.
        }

           // The library can use the value of shouldThrow to throw exceptions or not.
           if (shouldThrow) 
           {
              // old code
           }
           else {
              // new code
           }
        }
        ```

         Jest na użytek formacie spójnej przełączników, ponieważ są one formalnego kontraktu udostępnianych przez bibliotekę. Poniżej przedstawiono dwa formaty oczywiste.

        - *Przełącznik*. *przestrzeń nazw*. *switchName*

        - *Przełącznik*. *Biblioteka*. *switchName*

    - **Zmiany opartego na zadaniach wzorca asynchronicznego (TAP)**

         W przypadku aplikacji, które odnoszą się do [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiekty dziedziczą kultury i kultury interfejsu użytkownika wątku. Działanie aplikacji, która stosowane do poprzednich wersji programu .NET Framework lub które nie są kierowane określonej wersji programu .NET Framework, nie mają wpływu. Aby uzyskać więcej informacji, zobacz sekcję "Kultury i oparty na zadaniach asynchronicznej operacji" <xref:System.Globalization.CultureInfo> klasy tematu.

         <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> Klasa umożliwia reprezentują otoczenia dane, które jest lokalny dla przepływu daną kontrolkę asynchronicznego, takie jak `async` metody. Może służyć do utrwalenia danych pomiędzy wątkami. Istnieje także możliwość zdefiniowania metody wywołania zwrotnego, która jest powiadamiany o zmianie otoczenia danych albo ponieważ <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> właściwości jawnie została zmieniona, lub ponieważ wątek napotkała przejściowe kontekstu.

         Trzy metody wygody, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, zostały dodane do opartego na zadaniach asynchronicznej wzorcu (TAP) do zwrócenia zadań wykonanych w określonym stanie.

         <xref:System.IO.Pipes.NamedPipeClientStream> Klasa obsługuje teraz asynchroniczną komunikację ze swojego nowego <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>. Metoda.

    - **Element EventSource obsługuje teraz zapisu do dziennika zdarzeń**

         Teraz można używać <xref:System.Diagnostics.Tracing.EventSource> klasy do dziennika administracyjnych lub operacyjnych komunikaty w dzienniku zdarzeń Ponadto wszelkie istniejące sesje ETW utworzona na komputerze. W przeszłości konieczne było użycie pakietu Microsoft.Diagnostics.Tracing.EventSource NuGet dla tej funkcji. Ta funkcja jest obecnie wbudowane w program .NET Framework 4.6.

         Zarówno pakiet NuGet i .NET Framework 4.6 zostały zaktualizowane przy użyciu następujących funkcji:

        - **Zdarzenia dynamiczne**

             Umożliwia zdarzeń zdefiniowanych "na bieżąco" bez tworzenia metody zdarzeń.

        - **Ładunki RTF**

             Umożliwia specjalnie oparte na atrybutach klas i tablic, a także typy pierwotne, które mają być przekazywane jako ładunku

        - **Monitorowanie aktywności**

             Powoduje, że rozpoczęcie i zakończenie zdarzenia tagu między nimi o identyfikatorze, który reprezentuje wszystkie aktywne działania.

         Aby obsługiwać te funkcje, przeciążone <xref:System.Diagnostics.Tracing.EventSource.Write%2A> metody został dodany do <xref:System.Diagnostics.Tracing.EventSource> klasy.

- **Windows Presentation Foundation (WPF)**

    - **Ulepszenia HDPI**

         Obsługa HDPI na platformie WPF teraz jest ona odpowiedniejsza w [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Wprowadzono zmiany do układu zaokrąglania w celu ograniczenia wystąpień wycinka w formantach obramowaniami. Domyślnie ta funkcja jest włączona tylko wtedy, gdy Twoje <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ustawiono .NET 4.6.  Aplikacje docelowe wcześniejszych wersji platformy, które są uruchomione na [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] zgodzić się na nowe zachowanie, dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku app.config:

        ```xml
        <AppContextSwitchOverrides
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
        />
        ```

         Bez regionów blacked poza teraz renderowanych całkowicie windows WPF międzystrefowymi wiele monitorów o różnych ustawieniach DPI (DPI wielu konfiguracji). Można zrezygnować z tego zachowania, dodając następujący wiersz do `<appSettings>` sekcji pliku app.config, aby wyłączyć to nowe zachowanie:

        ```xml
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>
        ```

         Obsługa automatycznie ładowania prawo kursor na podstawie ustawienia DPI został dodany do <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.

    - **Touch jest lepszym rozwiązaniem**

         Klient zgłasza na [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) który touch tworzy nieprzewidywalne zachowanie zostały rozwiązane w [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Próg naciśnij dwa razy dla aplikacji ze Sklepu Windows i aplikacje WPF teraz jest taka sama w Windows 8.1 lub nowszym.

    - **Obsługa okna podrzędnego przezroczyste**

         WPF w [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] obsługuje okien podrzędnych przezroczyste w Windows 8.1 i nowszych. Dzięki temu można utworzyć okno podrzędne nieregularnych i przejrzysty w okien najwyższego poziomu. Można włączyć tę funkcję, ustawiając <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> właściwości `true`.

- **Windows Communication Foundation (WCF)**

    - **Obsługa protokołu SSL**

         Usługi WCF teraz obsługuje SSL, wersja protokołu TLS 1.1 i TLS 1.2, oprócz protokołu SSL 3.0 i TLS 1.0, używając NetTcp transportu zabezpieczeń i uwierzytelniania klientów. Jest teraz można wybrać, który protokół do użycia lub wyłącz stary mniejszym bezpiecznych protokołów. Można to zrobić przez ustawienie <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> właściwości lub przez dodanie poniższego do pliku konfiguracji.

        ```xml
        <netTcpBinding>
           <binding>
              <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                 <transport clientCredentialType="None|Windows|Certificate"
                            protectionLevel="None|Sign|EncryptAndSign"
                            sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                    </transport>
              </security>
           </binding>
        </netTcpBinding>
        ```

    - **Wysyłanie wiadomości przy użyciu innego połączenia HTTP**

         Usługi WCF umożliwia teraz użytkownikom upewnij się, że niektórych komunikatów są wysyłane przy użyciu różnych podstawowej połączeń HTTP. Istnieją dwa sposoby wykonania tej czynności:

        - **Przy użyciu prefiksu nazwy grupy połączenia**

             Użytkownicy mogą określić ciąg, który WCF będzie używać jako prefiksu nazwy grupy połączeń. Dwa komunikaty z różnymi prefiksami są wysyłane przy użyciu różnych podstawowej połączeń HTTP. Ustaw prefiks, dodając pary klucza/wartości do komunikatu <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> właściwości. Klucz jest "HttpTransportConnectionGroupNamePrefix"; wartość jest żądany prefiks.

        - **Za pomocą fabryk kanałów różnych**

             Użytkownicy mogą również włączyć funkcji, które powodują, że komunikatów wysyłanych za pomocą kanałów utworzonych za pomocą fabryk inny kanał będzie używał innego podstawowego połączenia HTTP. Aby włączyć tę funkcję, użytkownicy muszą określić następujące ustawienia `appSetting` do `true`:

            ```xml
            <appSettings>
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
            </appSettings>
            ```

- **Program Windows Workflow Foundation (WWF)**

     Można teraz określić liczbę sekund, przez które usługi przepływu pracy będą przechowywane żądanie operacji poza kolejnością, gdy istnieje oczekujące zakładki "z systemem innym niż protokół" limit żądania. Zakładka "z systemem innym niż protokół" jest zakładki, która nie jest powiązana z oczekujących działań Receive. Niektóre działania utworzyć-protocol zakładki w ich implementacji, nie może być oczywista, czy zakładki protokołu nie istnieje. Obejmują one stanu i pobrania. Więc jeśli masz zaimplementowany przy użyciu komputera stanu usługi przepływu pracy lub zawierające działania pobranie, będzie prawdopodobnie z zakładek-protocol. Określ interwał przez dodanie wiersza, takie jak następujące polecenie, aby `appSettings` sekcji w pliku app.config:

    ```xml
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
    ```

     Wartość domyślna to 60 sekund. Jeśli `value` jest ustawiony na wartość 0, poza kolejnością są natychmiast odrzucenia żądania z błędu na tekst, który wygląda następująco:

    ```
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees. 
    ```

     Jest to ten sam komunikat otrzymanej w przypadku operacji poza kolejnością komunikat jest odbierany i nie ma żadnych zakładek-protocol.

     Jeśli wartość `FilterResumeTimeoutInSeconds` element jest różna od zera, istnieją zakładki-protocol i interwał limitu czasu wygaśnięcia, kończy się niepowodzeniem z komunikatem limitu czasu.

- **Transakcje**

     Teraz można podać identyfikator transakcji rozproszonej dla transakcji, która spowodowała wystąpienie wyjątku pochodzących z <xref:System.Transactions.TransactionException> zostanie wygenerowany. Można to zrobić, dodając następujący klucz `appSettings` sekcji w pliku app.config:

    ```xml
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/> 
    ```

     Wartość domyślna to `false`.

- **Sieci**

    - **Ponowne użycie gniazda**

         Windows 10 obejmuje nowy algorytm sieci wysokiej skalowalności, który powoduje, że lepsze wykorzystanie zasobów komputera przez ponowne użycie portów lokalnych dla wychodzących połączeń TCP. .NET Framework 4.6 obsługuje nowego algorytmu, umożliwiając aplikacji .NET wykorzystać nowe zachowanie. W poprzednich wersjach systemu Windows wystąpił limit sztucznego równoczesnych połączeń (zazwyczaj 16384, domyślny rozmiar dynamicznego zakresu portów), które może ograniczać skalowalność usługi powodując wyczerpania portu w obszarze obciążenia.

         W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], dodano dwa nowe interfejsy API umożliwiające ponowne użycie portu, którego usunięcie limit 64 K równoczesnych połączeń:

        - <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> Wartość wyliczenia.

        - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> Właściwości.

         Domyślnie <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> właściwość jest `false` chyba że `HWRPortReuseOnSocketBind` wartość `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` klucz rejestru jest ustawiona na 0x1. Aby włączyć port lokalny ponownemu w przypadku połączeń HTTP, ustaw <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> właściwości `true`. Powoduje to, że wszystkie połączenia gniazda TCP wychodzące z <xref:System.Net.Http.HttpClient> i <xref:System.Net.HttpWebRequest> do używania nowej opcji gniazda systemu Windows 10, [SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx), umożliwiającej ponowne użycie portu lokalnego.

         Można określić deweloperom pisanie aplikacji tylko do gniazda <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> podczas wywoływania metody, takie jak <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> tak, aby wychodzącego sockets ponownego użycia portów lokalnych podczas tworzenia powiązania.

    - **Obsługa międzynarodowych nazw domen i PunyCode**

         Nową właściwość <xref:System.Uri.IdnHost%2A>, został dodany do <xref:System.Uri> klasę, aby lepiej obsługuje międzynarodowych nazw domen i PunyCode.

- **Zmiana rozmiaru formantów formularzy systemu Windows.**

     Ta funkcja została rozszerzona w [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] uwzględnienie <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.ToolStripSplitButton> typy i prostokąt określony przez <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> właściwość używana podczas rysowania <xref:System.Drawing.Design.UITypeEditor> .

     Jest to funkcji opcjonalnych. Aby go włączyć, ustaw `EnableWindowsFormsHighDpiAutoResizing` elementu `true` w pliku konfiguracyjnym (app.config) aplikacji:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Obsługa kodu strony kodowania**

     [!INCLUDE[net_core](../../../includes/net-core-md.md)] przede wszystkim obsługuje kodowania Unicode i domyślnie zapewnia ograniczoną obsługę kodu strony kodowania. Można dodać obsługę dla kodu strony kodowań dostępnych w programie .NET Framework, ale jest nieobsługiwany w [!INCLUDE[net_core](../../../includes/net-core-md.md)] rejestrując kodowania strony kodu z <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji, zobacz <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

     Aplikacje systemu Windows dla systemu Windows 10 kierowanych [!INCLUDE[net_core](../../../includes/net-core-md.md)] i są napisane w języku C# lub Visual Basic można korzystać z nowej technologii, która kompiluje aplikacji do kodu macierzystego zamiast IL. Wygenerowanie charakteryzujących się szybsze uruchamianie i czasy wykonania aplikacji. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji za pomocą platformy .NET Native](../../../docs/framework/net-native/index.md). Omówienie platformy .NET Native badający jak różni się od zarówno kompilacji JIT i NGEN i jakie środki do kodu, zobacz [platformy .NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).

     Aplikacje są kompilowane do kodu natywnego domyślnie podczas kompilowania z programem Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy z platformą .NET Native](../../../docs/framework/net-native/getting-started-with-net-native.md).

     Aby obsługiwać aplikacje platformy .NET Native debugowania, liczba nowe interfejsy i wyliczenia zostały dodane do niezarządzanego API debugowania. Aby uzyskać więcej informacji, zobacz [debugowanie (niezarządzany wykaz interfejsów API)](../../../docs/framework/unmanaged-api/debugging/index.md) tematu.

- **Open source pakietów .NET Framework**

     Pakiety .NET core, takie jak kolekcje niezmienialne [SIMD interfejsów API](http://go.microsoft.com/fwlink/?LinkID=518639), a sieć interfejsów API, takich jak zasoby znajdujące się w <xref:System.Net.Http> przestrzeni nazw są teraz dostępne jako typu open source pakietów na [GitHub](https://github.com/). Aby uzyskać dostęp do kodu, zobacz [CoreFx w serwisie GitHub](https://github.com/dotnet/corefx). Aby uzyskać więcej informacji i sposobu współtworzenia te pakiety, zobacz [.NET Core i Open-Source](../../../docs/framework/get-started/net-core-and-open-source.md), [strona główna platformy .NET w witrynie GitHub](https://github.com/dotnet/home).

 [Powrót do początku](#introduction)

<a name="v452"></a> 
## <a name="whats-new-in-the-net-framework-452"></a>Co to jest nowe w programie .NET Framework 4.5.2

- **Nowe interfejsy API dla aplikacji ASP.NET.** Nowy <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> i <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody pozwalają sprawdzić i modyfikować nagłówki odpowiedzi i kod stanu, ponieważ odpowiedź jest opróżniany do aplikacji klienckiej. Należy rozważyć użycie tych metod, zamiast <xref:System.Web.HttpApplication.PreSendRequestHeaders> i <xref:System.Web.HttpApplication.PreSendRequestContent> zdarzenia; są one bardziej wydajny i niezawodny.

     <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> Metody umożliwia zaplanowanie tła małych elementów roboczych. Program ASP.NET śledzi te elementy i uniemożliwia usług IIS nagle zakończenie procesu roboczego, dopóki wszystkie elementy robocze w tle została ukończona. Nie można wywołać tej metody poza domeną zarządzaną aplikację ASP.NET.

     Nowy <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> i <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> właściwości zwracają wartości logiczne, które wskazują, czy nagłówki odpowiedzi zostały zapisane. Umożliwia te właściwości upewnij się, że wywołującą do interfejsów API, takich jak <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> powiedzie się (które zgłaszają wyjątki, jeśli został napisany nagłówki).

- **Zmiana rozmiaru formantów formularzy systemu Windows.** Ta funkcja została rozszerzona. Ustawienie DPI systemu umożliwia teraz zmienić rozmiar składniki następujące dodatkowe kontrole (na przykład strzałkę listy rozwijanej w polu kombi):

     <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStripComboBox> <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.Cursor> <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

     Jest to funkcji opcjonalnych. Aby go włączyć, ustaw `EnableWindowsFormsHighDpiAutoResizing` elementu `true` w pliku konfiguracyjnym (app.config) aplikacji:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Nowa funkcja przepływ pracy.** Menedżer zasobów, który używa <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> — metoda (i w związku z tym wdrażanie <xref:System.Transactions.IPromotableSinglePhaseNotification> interfejsu) można użyć nowej <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> metodę, aby zażądać następujące:

    - Podwyższenia poziomu transakcji do transakcji koordynatora transakcji rozproszonych (MSDTC).

    - Zastąp <xref:System.Transactions.IPromotableSinglePhaseNotification> z <xref:System.Transactions.ISinglePhaseNotification>, który jest trwałe rejestracji, obsługujący jednej fazie zatwierdzeń.

     To może odbywać się w tej samej domenie aplikacji i nie wymaga żadnych dodatkowych niezarządzany kod do interakcji z usługą MSDTC przeprowadzić podwyższenia poziomu. Nowe metodę można wywołać tylko wtedy, gdy istnieje oczekujące wywołanie z <xref:System.Transactions?displayProperty=nameWithType> do <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` metodę, która jest zaimplementowana przez awansowanie rejestracji.

- **Ulepszenia profilowania.** Nowe niezarządzane profilowania API zapewniają bardziej niezawodne profilowania:

     [Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) [wyliczenie COR_PRF_HIGH_MONITOR](../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) [metoda GetAssemblyReferences](../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) [metoda GetEventMask2](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) [Metoda SetEventMask2](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) [metoda AddAssemblyReference](../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

     Poprzednie `ICorProfiler` implementacje obsługiwane opóźnionego ładowania zestawów zależnych. Nowe interfejsy API profilowania wymagają zależne zestawy, które są wstrzykiwane przez profiler być obciążane natychmiast, zamiast ładowany po aplikacji jest w pełni zainicjowany. Ta zmiana nie wpływa na użytkowników w istniejącej `ICorProfiler` interfejsów API.

- **Ulepszenia debugowania.** Następujące nowe niezarządzanych API debugowania zapewniają lepszą integrację z profilera. Możesz teraz metadanych dostępu wstawiane przez profiler, a także zmiennych lokalnych i kodu utworzonego przez żądania ReJIT kompilatora podczas zrzutu debugowania.

     [Metoda SetWriteableMetadataUpdateMode](../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) [metoda EnumerateLocalVariablesEx](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) [metoda GetLocalVariableEx](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) [metoda GetCodeEx](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) [Metoda GetActiveReJitRequestILCode](../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md) [metoda GetInstrumentedILMap](../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Zdarzenia śledzenia zmian.** .NET Framework 4.5.2 umożliwia śledzenie działania poza procesem, opartych na śledzenie zdarzeń systemu Windows ETW dla większych powierzchni. Umożliwia to dostawcom Zaawansowane zarządzanie energią (APM) oferują lekkie narzędzia precyzyjnie monitorować koszty poszczególnych żądań i działań, które wielu wątków.  Te zdarzenia są generowane tylko wtedy, gdy kontrolery ETW umożliwiały; Dlatego zmiany nie wpływają na uprzednio zapisany ETW kodu lub kod uruchamiany za pomocą funkcji ETW wyłączone.

- **Podwyższenie poziomu transakcji i konwertowana na trwałe rejestracji**

     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> Nowy interfejs API dodaje programu .NET Framework 4.5.2 i 4.6

    ```csharp
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                              IPromotableSinglePhaseNotification promotableNotification,
                                              ISinglePhaseNotification enlistmentNotification,
                                              EnlistmentOptions enlistmentOptions)
    ```

     Metoda może być używany przez rejestracji, która wcześniej została utworzona przez <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> w odpowiedzi na <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> metody. Sprawdza, czy `System.Transactions` do podwyższenia poziomu transakcji do transakcji usługi MSDTC i "konwertowania" rejestracja z możliwością awansowania do trwałych rejestracji. Po tej metody zakończy się pomyślnie, <xref:System.Transactions.IPromotableSinglePhaseNotification> interfejsu nie będzie odwoływać się `System.Transactions`, a wszystkie przyszłe powiadomienia pojawią się na udostępnionych <xref:System.Transactions.ISinglePhaseNotification> interfejsu. Dana rejestracja musi działać jako trwałe rejestracji, Obsługa rejestrowania transakcji i odzyskiwania. Zapoznaj się <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> szczegółowe informacje. Ponadto rejestracji musi obsługiwać <xref:System.Transactions.ISinglePhaseNotification>.  Ta metoda może *tylko* można wywołać podczas przetwarzania <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> wywołania. Jeśli to nie jest w tym przypadku <xref:System.Transactions.TransactionException> wyjątku.

 [Powrót do początku](#introduction)

<a name="v451"></a> 
## <a name="whats-new-in-the-net-framework-451"></a>Co to jest nowe w programie .NET Framework 4.5.1
 **Aktualizuje kwietnia 2014**:

- [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) obejmuje aktualizacje szablonów przenośnej biblioteki klas do obsługi tych scenariuszy:

    - Interfejsy API środowiska wykonawczego systemu Windows można użyć w przenośnych bibliotek, które odnoszą się do Windows 8.1, Windows Phone 8.1 i Windows Phone Silverlight 8.1.

    - XAML (Windows.UI.XAML typy) można uwzględnić w przenośnych bibliotek podczas target Windows 8.1 lub Windows Phone 8.1. Obsługiwane są następujące szablony XAML: pustej strony, słownik zasobów kontrolki z szablonem i kontrolki użytkownika.

    - Możesz utworzyć przenośne składnika środowiska wykonawczego systemu Windows (plik winmd) do użycia w aplikacjach w sklepie przeznaczonych dla Windows 8.1 i Windows Phone 8.1.

    - Można przekierować Sklepu Windows lub Sklepu Windows Phone biblioteki klas takich jak przenośnej biblioteki klas.

     Aby uzyskać więcej informacji na temat tych zmian, zobacz [przenośnej biblioteki klas](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Zawartość .NET Framework teraz ustawić obejmuje dokumentacji [!INCLUDE[net_native](../../../includes/net-native-md.md)], która jest wstępnej kompilacji technologie umożliwiające tworzenie i wdrażanie aplikacji systemu Windows. [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompiluje aplikacji bezpośrednio do kodu natywnego, a nie na języku pośrednim (IL), aby zapewnić lepszą wydajność. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji za pomocą platformy .NET Native](../../../docs/framework/net-native/index.md).

- [Źródła .NET Framework odwołanie](http://referencesource.microsoft.com/) udostępnia nowe funkcje przeglądania i ulepszone funkcje. Teraz można przeglądać w trybie online, kod źródłowy .NET Framework [Pobierz odwołanie](http://referencesource.microsoft.com/download.html) przeglądania w trybie offline i kroków źródeł (w tym poprawek i aktualizacji) podczas debugowania. Aby uzyskać więcej informacji, zobacz wpis w blogu [wygląda źródła odwołania .NET](https://blogs.msdn.microsoft.com/dotnet/2014/02/24/a-new-look-for-net-reference-source/).

 Podstawowe nowych funkcjach i rozszerzeniach w programie .NET Framework 4.5.1 obejmują:

- Automatycznego przekierowania powiązań dla zestawów. Począwszy od [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], podczas kompilowania aplikacji, którego celem jest [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], przekierowania powiązań mogą być dodawane do pliku konfiguracji aplikacji Jeśli aplikacji lub jego składniki odwoływać się wiele wersji tego samego zestawu. Można również włączyć tę funkcję dla projektów przeznaczonych dla starszych wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie automatycznego przekierowania powiązania](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Możliwość zbieraj informacje diagnostyczne, aby pomóc deweloperom poprawić wydajność aplikacji serwera i w chmurze. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> i <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> metod w <xref:System.Diagnostics.Tracing.EventSource> klasy.

- Możliwość jawnie compact sterty dużego obiektu (LOH) podczas wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwości.

- Ulepszenia wydajności dodatkowe np. zawieszenie aplikacji ASP.NET, ulepszenia JIT wielordzeniowych i szybsze uruchamianie aplikacji po .NET Framework aktualizacji. Aby uzyskać więcej informacji, zobacz [anonsu .NET Framework 4.5.1](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/) i [wstrzymać aplikacja ASP.NET](https://blogs.msdn.microsoft.com/dotnet/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting/) wpis w blogu.

 Ulepszenia do formularzy systemu Windows obejmują:

- Zmiana rozmiaru formantów formularzy systemu Windows. Ustawienie DPI systemu można zmienić rozmiaru elementów formantów (na przykład ikony, które są widoczne w siatce właściwości) służy przez Rezygnacja się przy użyciu wpisu w pliku konfiguracji aplikacji (app.config) dla aplikacji. Ta funkcja jest obecnie obsługiwane w następujących formantów formularzy systemu Windows:

     <xref:System.Windows.Forms.PropertyGrid> <xref:System.Windows.Forms.TreeView> Niektóre aspekty <xref:System.Windows.Forms.DataGridView> (zobacz [nowe funkcje w wersji 4.5.2](#v452) dodatkowych formantów obsługiwane)

     Aby włączyć tę funkcję, Dodaj nową \<appSettings > elementu do pliku konfiguracyjnego (app.config) i zestaw `EnableWindowsFormsHighDpiAutoResizing` elementu `true`:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

 Ulepszenia podczas debugowania aplikacji .NET Framework w [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] obejmują:

- Wartości zwracane w debugerze programu Visual Studio. Podczas debugowania aplikacji zarządzanej przez [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], wyświetla okno zmiennych automatycznych zwracać typów i wartości dla metod. Te informacje są dostępne dla pulpitu, Sklep Windows i aplikacje Windows Phone. Aby uzyskać więcej informacji, zobacz [Sprawdź wartości zwracanych z wywołań metody](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx) w bibliotece MSDN.

- Edytuj i Kontynuuj dla aplikacji 64-bitowych. [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] obsługuje funkcję Edytuj i Kontynuuj dla 64-bitowych zarządzane aplikacje dla pulpitu, Sklep Windows i Windows Phone. Istniejące ograniczenia pozostają w mocy zarówno 32-bitowe i 64-bitowych aplikacji (zobacz w ostatniej sekcji [obsługiwane zmiany kodu (C#)](/visualstudio/debugger/supported-code-changes-csharp) artykułu).

- Debugowanie Async-aware. Aby ułatwić debugowania w aplikacjach asynchronicznych w [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], stos wywołań ukrywa dostarczony przez kompilatory do obsługi programowania asynchronicznego kod infrastruktury i również łańcuchów w ramkach logiczny obiekt nadrzędny, aby można było wykonywać logicznych program wykonywania więcej wyraźnie. Okno zadań zastępuje okno zadań równoległych i przedstawia zadania, które odnoszą się do określonego punktu przerwania i wyświetla również inne zadania, które są aktualnie aktywne lub zaplanowane w aplikacji. Informacje o tej funkcji w sekcji "debugowanie obsługujący Async" [anonsu .NET Framework 4.5.1](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/).

- Lepszą obsługę wyjątków składników środowiska wykonawczego systemu Windows. W [!INCLUDE[win81](../../../includes/win81-md.md)], wyjątki, które wynikają z aplikacji ze Sklepu Windows zachować informacje o błędzie, który spowodował wyjątek, nawet w granicach języka. Informacje o tej funkcji w sekcji "Tworzenie aplikacji dla Sklepu Windows" [anonsu .NET Framework 4.5.1](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/). 

 Począwszy od [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], można użyć [zarządzane profil z przewodnikiem narzędzie optymalizacji (Mpgo.exe)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md) w celu zoptymalizowania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, a także aplikacji klasycznych.

 Na temat nowych funkcji w programie ASP.NET 4.5.1 [ASP.NET 4.5.1 i Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) w witrynie platformy ASP.NET.

 [Powrót do początku](#introduction)

<a name="v45"></a> 
## <a name="whats-new-in-the-net-framework-45"></a>Co to jest nowa w programie .NET Framework 4.5

### <a name="core-new-features-and-improvements"></a>Podstawowe nowe funkcje i ulepszenia

- Możliwość ograniczenia system zostanie uruchomiony ponownie przez wykrywanie i zamykaniu aplikacji .NET Framework 4 podczas wdrażania. Zobacz [zmniejszenie liczby systemu ponownych uruchomień podczas .NET Framework 4.5 instalacji](../../../docs/framework/deployment/reducing-system-restarts.md).

- Obsługa dla tablic, które są większe niż 2 gigabajty (GB) na platformach 64-bitowych. Tę funkcję można włączyć w pliku konfiguracyjnym aplikacji. Zobacz [ \<gcallowverylargeobjects — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), który zawiera również inne ograniczenia dotyczące rozmiaru obiektu i rozmiar tablicy.

- Lepsza wydajność przez odzyskiwanie pamięci w tle dla serwerów. Jeśli używasz serwera wyrzucanie elementów bezużytecznych w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], odzyskiwanie pamięci w tle jest automatycznie włączone. Zobacz sekcję odzyskiwanie pamięci w tle serwera [podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/fundamentals.md) tematu.

- Kompilacja just-in-time (JIT) tła opcjonalnie dostępnej w wielordzeniowych procesorów, aby zwiększyć wydajność aplikacji. Zobacz <xref:System.Runtime.ProfileOptimization>.

- Możliwość ograniczania jak długo aparat wyrażeń regularnych podejmie próbę rozpoznania wyrażenia regularnego, zanim upłynie limit czasu. Zobacz <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> właściwości.

- Możliwość definiowania kulturę domyślną na potrzeby domeny aplikacji. Zobacz <xref:System.Globalization.CultureInfo> klasy.

- Obsługa konsoli kodowanie Unicode (UTF-16). Zobacz <xref:System.Console> klasy.

- Obsługa wersji ciąg kultury porządkowania i porównania danych. Zobacz <xref:System.Globalization.SortVersion> klasy.

- Lepszą wydajność podczas pobierania zasobów. Zobacz [opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Ulepszenia kompresji ZIP Zmniejsz rozmiar pliku skompresowanego. Zobacz <xref:System.IO.Compression?displayProperty=nameWithType> przestrzeni nazw.

- Możliwość dostosowania kontekście odbicia, aby zastąpić domyślne zachowanie odbicia za pośrednictwem <xref:System.Reflection.Context.CustomReflectionContext> klasy.

- Obsługa międzynarodowych nazw domen aplikacji (IDNA) w wersji 2008 standard w przypadku <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> klasa jest używana na [!INCLUDE[win8](../../../includes/win8-md.md)].

- Delegowanie porównania ciągów do systemu operacyjnego, który implementuje Unicode 6.0, gdy programu .NET Framework jest używana na [!INCLUDE[win8](../../../includes/win8-md.md)]. Podczas uruchamiania na innych platformach, .NET Framework obejmuje własnych danych porównanie ciągu, która implementuje Unicode 5.x. Zobacz <xref:System.String> klasy i uwagi części <xref:System.Globalization.SortVersion> klasy.

- Możliwość obliczeniowe skrótu dla ciągów na poszczególnych domen aplikacji. Zobacz [ \<userandomizedstringhashalgorithm — > elementu](../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Typ obsługi odbicia podzielony między <xref:System.Type> i <xref:System.Reflection.TypeInfo> klasy. Zobacz [odbicia w .NET Framework dla aplikacji ze Sklepu Windows](../../../docs/framework/reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Framework Managed Extensibility (MEF) zapewnia następujące nowe funkcje:

- Obsługa typów ogólnych.

- Opartych na konwencjach model programowania, który umożliwia tworzenie części oparte na konwencji nazewnictwa, a nie atrybutów.

- Wiele zakresów.

- Podzbiór MEF używanego podczas tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Ten podzestaw jest dostępna jako [do pobrania pakietu](http://go.microsoft.com/fwlink/?LinkId=256238) z galerii NuGet. Aby zainstalować pakiet, otwórz projekt w programie Visual Studio, wybierz polecenie **Zarządzaj pakietami NuGet** z **projektu** menu, a następnie wyszukaj w trybie online `Microsoft.Composition` pakietu.

 Aby uzyskać więcej informacji, zobacz [Managed Extensibility Framework (MEF)](../../../docs/framework/mef/index.md).

### <a name="asynchronous-file-operations"></a>Operacje asynchroniczne plików
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], nowe funkcje asynchroniczne zostały dodane do języków C# i Visual Basic. Te funkcje dodać modelu opartego na zadaniach do wykonania operacji asynchronicznych. Aby użyć tego nowego modelu, użyj metod asynchronicznych w klasach we/wy. Zobacz [asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md).

<a name="tools"></a> 
### <a name="tools"></a>Narzędzia
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Generator pliku zasobów (Resgen.exe) umożliwia utworzenie pliku .resw do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji z pliku .resources osadzone w zestawie .NET Framework. Aby uzyskać więcej informacji, zobacz [Resgen.exe (Generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

 Zarządzane profilowana Optymalizacja (Mpgo.exe) pozwala zwiększyć czas uruchomienia aplikacji, wykorzystanie pamięci (rozmiar zestawu roboczego) i przepływności optymalizując zestawy obrazu macierzystego. Narzędzie wiersza polecenia generuje dane profilu dla zestawów aplikacji obrazu macierzystego. Zobacz [Mpgo.exe (narzędzie optymalizacji sterowania zarządzanym profilem)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Począwszy od [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], można zoptymalizować Mpgo.exe [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, a także aplikacji klasycznych.

<a name="parallel"></a> 
### <a name="parallel-computing"></a>Przetwarzanie równoległe
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Udostępnia kilka nowych funkcji i ulepszeń przetwarzania równoległego. Obejmują one lepszą wydajność, większą kontrolę ulepszoną obsługę programowania asynchronicznego, Nowa biblioteka przepływu danych i lepszą obsługę równoległych debugowania i analiza wydajności. Zobacz wpis [poświęconym nowościom dotyczącym równoległości w programie .NET 4.5](http://go.microsoft.com/fwlink/?LinkId=235061) w programowania równoległego z blogu .NET.

<a name="web"></a> 
### <a name="web"></a>sieć Web
 Program ASP.NET 4.5 i 4.5.1 dodać powiązanie modelu formularzy sieci Web, obsługa protokołu WebSocket, asynchroniczne procedury obsługi, ulepszenia wydajności i wiele innych funkcji. Aby uzyskać więcej informacji, zobacz następujące zasoby:

- [Program ASP.NET 4.5 i programu Visual Studio 2012](http://msdn.microsoft.com/library/ac9bb7f6-f094-4af7-bad0-acf49a5dbc55) w bibliotece MSDN.

- [ASP.NET 4.5.1 i Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) w witrynie platformy ASP.NET.

<a name="networking"></a> 
### <a name="networking"></a>Obsługa sieci
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Zapewnia nowy interfejs programowania aplikacji HTTP. Aby uzyskać więcej informacji, zobacz nowe <xref:System.Net.Http?displayProperty=nameWithType> i <xref:System.Net.Http.Headers?displayProperty=nameWithType> przestrzeni nazw.

 Obsługiwane są także nowego interfejsu programowania akceptowania i interakcji z połączeń protokołu WebSocket przy użyciu istniejącego <xref:System.Net.HttpListener> i powiązanych klas. Aby uzyskać więcej informacji, zobacz nowe <xref:System.Net.WebSockets> przestrzeni nazw i <xref:System.Net.HttpListener> klasy.

 Ponadto [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zawiera następujące ulepszenia sieci:

- Obsługa zgodne ze standardem RFC identyfikatora URI. Aby uzyskać więcej informacji, zobacz <xref:System.Uri> i powiązanych klas.

- Obsługa międzynarodowych nazw domen (IDN) podczas analizowania. Aby uzyskać więcej informacji, zobacz <xref:System.Uri> i powiązanych klas.

- Obsługa internacjonalizacji adres E-mail (EAI). Aby uzyskać więcej informacji, zobacz <xref:System.Net.Mail> przestrzeni nazw.

- Ulepszona obsługa protokołu IPv6. Aby uzyskać więcej informacji, zobacz <xref:System.Net.NetworkInformation> przestrzeni nazw.

- Obsługa podwójne gniazda. Aby uzyskać więcej informacji, zobacz <xref:System.Net.Sockets.Socket> i <xref:System.Net.Sockets.TcpListener> klasy.

<a name="client"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Windows Presentation Foundation (WPF) zawiera zmiany i udoskonalenia w następujących obszarach:

- Nowe <xref:System.Windows.Controls.Ribbon.Ribbon> kontroli, dzięki czemu można zaimplementować interfejs użytkownika wstążki obsługującego kart, aplikacji Menu i paska narzędzi Szybki dostęp.

- Nowe <xref:System.ComponentModel.INotifyDataErrorInfo> interfejs, który obsługuje sprawdzanie poprawności danych synchroniczne i asynchroniczne.

- Nowe funkcje <xref:System.Windows.Controls.VirtualizingPanel> i <xref:System.Windows.Threading.Dispatcher> klasy.

- Zwiększona wydajność w przypadku wyświetlania dużej ustawia grupowanych danych oraz uzyskiwania dostępu do kolekcji w wątkach bez interfejsu użytkownika.

- Powiązanie właściwości statycznych danych, do niestandardowego powiązania danych typów, które implementują <xref:System.Reflection.ICustomTypeProvider> interfejsu i pobieranie informacje o powiązaniu danych z wyrażenia powiązania.

- Zmienianie położenia danych po zmianie wartości (kształtowania na żywo).

- Możliwość sprawdzenia, czy kontekst danych dla elementu kontenera jest odłączony.

- Możliwość ustawić czas, który powinien upłynąć między zmian właściwości i aktualizacji źródła danych.

- Ulepszona obsługa stosowania wzorców słabe zdarzeń. Ponadto zdarzenia teraz akceptować rozszerzenia znaczników.

<a name="windows_communication_foundation"></a> 
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], następujące funkcje zostały dodane do prostszy sposób zapisania i obsługa aplikacji Windows Communication Foundation (WCF):

- Uproszczenie konfiguracji wygenerowanych plików.

- Obsługa tworzenia pierwszej kontraktu.

- Możliwość łatwiej skonfigurować tryb zgodności ASP.NET.

- Zmiany w domyślnym transportu wartości właściwości, aby zmniejszyć prawdopodobieństwo, że trzeba będzie je ustawić.

- Aktualizacje <xref:System.Xml.XmlDictionaryReaderQuotas> klasę, aby zmniejszyć prawdopodobieństwo, że trzeba będzie ręcznie skonfigurować przydziały dla czytników słownika XML.

- Sprawdzanie poprawności pliki konfiguracji usługi WCF w programie Visual Studio jako część procesu kompilacji, aby uruchomić aplikację, można wykrywać błędy konfiguracji.

- Nowy asynchroniczny obsługę przesyłania strumieniowego.

- Nowe mapowanie protokołu HTTPS, aby ułatwić ujawniać punkt końcowy za pośrednictwem protokołu HTTPS z programu Internet Information Services (IIS).

- Możliwość generowania metadanych w pojedynczego dokumentu WSDL, dodając `?singleWSDL` do adresu URL usługi.

- Obsługuje protokół Websockets do włączenia komunikacji dwukierunkowej true przez porty 80 i 443 z charakterystyki wydajności są podobne do transportu TCP.

- Obsługa Konfigurowanie usług w kodzie.

- Etykietki narzędzi edytora XML.

- <xref:System.ServiceModel.ChannelFactory> Obsługa buforowania.

- Obsługa kompresji kodera binarnego.

- Obsługa transportu UDP, który umożliwia deweloperom pisanie usług korzystających z "wyzwalać i zapomnij" wiadomości. Klient wysyła komunikat do usługi i oczekuje na brak odpowiedzi z usługi.

- Zdolność do obsługi wielu tryby uwierzytelniania na jeden punkt końcowy usługi WCF, korzystając z transportu HTTP i zabezpieczeń transportu.

- Obsługa usługi WCF, które używają międzynarodowych nazw domen (IDN).

 Aby uzyskać więcej informacji, zobacz [What's New in Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=228173).

<a name="windows_workflow_foundation"></a> 
### <a name="windows-workflow-foundation-wf"></a>Program Windows Workflow Foundation (WF)
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kilka nowych funkcji zostały dodane do systemu Windows Workflow Foundation (WF), w tym:

- Stan maszyny przepływów pracy, które zostały najpierw wprowadzone w ramach programu .NET Framework 4.0.1 ([platformy aktualizacji 1 dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=215092)). Ta aktualizacja jest uwzględniona kilka nowych klas i działań, które włączone deweloperom tworzenie przepływów pracy komputera stanu. Te klasy i działań, które zostały zaktualizowane dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do uwzględnienia:

    - Możliwość określenia punktów przerwania stanów.

    - Możliwość kopiowania i wklejania przejścia w Projektancie przepływów pracy.

    - Projektanta obsługę tworzenia przejścia wyzwalaczem udostępnionym.

    - Działania do tworzenia przepływów pracy maszyny stanu, w tym: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, i <xref:System.Activities.Statements.Transition>.

- Ulepszone funkcje projektanta przepływów pracy, takie jak następujące:

    - Rozszerzone możliwości wyszukiwania przepływu pracy w programie Visual Studio, w tym **szybkiego wyszukiwania** i **Znajdź w plikach**.

    - Zdolność do automatycznego tworzenia działania Sequence, gdy drugi działanie podrzędne zostanie dodany do działania kontenera i obejmować zarówno działania w działaniu sekwencji.

    - Przesuwanie pomocy technicznej, co pozwala widoczną część przepływu pracy można zmienić bez użycia pasków przewijania.

    - Nowy **konspekt dokumentu** widok, w którym przedstawiono składniki przepływu pracy w widoku drzewa stylu konspektu i umożliwia wybierz składnik **konspekt dokumentu** widoku.

    - Możliwość dodawania adnotacji do działań.

    - Możliwość Definiowanie oraz stosowanie delegatów działania za pomocą projektanta przepływów pracy.

    - Połącz automatycznie i auto wstawienie działań i przejść w stan komputera i schemat blokowy przepływów pracy.

- Magazyn informacji o stanie widoku dla przepływu pracy w jeden element w pliku XAML, aby można było łatwo zlokalizować i Edytuj informacje o stanie widoku.

- Działanie kontenera NoPersistScope aby zapobiec utrwalanie działań podrzędnych.

- Pomoc techniczna dla wyrażeń C#:

    - Projektów przepływu pracy, korzystających z języka Visual Basic użyje wyrażeń języka Visual Basic i C# projektów przepływu pracy będzie używać wyrażeń języka C#.

    - C# przepływu pracy projektów utworzonych w programie Visual Studio 2010 i Visual Basic wyrażenia, która ma są zgodne z C# przepływu pracy projektów, które używają wyrażeń C#.

- Przechowywanie wersji rozszerzenia:

    - Nowe <xref:System.Activities.WorkflowIdentity> klasy, która zapewnia mapowanie między wystąpienia utrwalonego przepływu pracy i jego definicji przepływu pracy.

    - Side-by-side wykonywanie wielu wersji przepływu pracy, w tym samym hoście, w tym <xref:System.ServiceModel.Activities.WorkflowServiceHost>.

    - W usłudze aktualizacji dynamicznej, uprawnienia do modyfikowania definicji wystąpienia utrwalonego przepływu pracy.

- Kontrakt pierwszy rozwoju usługi przepływu pracy, który zapewnia obsługę automatycznego generowania działań, aby dopasować istniejący kontrakt usługi.

 Aby uzyskać więcej informacji, zobacz [What's New in Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=228176).

<a name="tailored"></a> 
### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje są przeznaczone dla określonych typów urządzeń i korzystać z możliwości systemu operacyjnego Windows. Podzbiór [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub 4.5.1 jest dostępny do budowy [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji dla systemu Windows przy użyciu języka C# lub Visual Basic. Ten podzestaw jest nazywany [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] co opisano w [omówienie](http://go.microsoft.com/fwlink/?LinkId=228491) w Centrum deweloperów systemu Windows.

<a name="portable"></a> 
### <a name="portable-class-libraries"></a>Biblioteki klas przenośnych
 Projekt przenośnej biblioteki klas w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] (i nowszych wersjach) pozwala na zapisu i tworzenia zarządzanych zestawów działające na wielu platformach .NET Framework. Przy użyciu projektu biblioteki klas przenośnych, możesz wybrać platformy (np. Windows Phone i [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) do obiektu docelowego. Dostępne typy i elementy członkowskie w projekcie jest automatycznie ograniczany do często używanych typów i członków na tych platformach. Aby uzyskać więcej informacji, zobacz [przenośnej biblioteki klas](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Zobacz też
 [.NET Framework i zwalnia poza pasmem](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [What's new in ułatwień dostępu w programie .NET Framework](whats-new-in-accessibility.md)   
 [Co to jest nowa w programie Visual Studio 2017 r.](/visualstudio/ide/whats-new-in-visual-studio)   
 [ASP.NET](/aspnet)   
 [Co to jest nowe w programie Visual C++](/cpp/what-s-new-for-visual-cpp-in-visual-studio) 
