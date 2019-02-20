---
title: What's new in .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
  - csharp
  - vb
helpviewer_keywords:
  - 'what''s new [.NET Framework]'
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
author: rpetrusha
ms.author: ronpet
---
# What's new in .NET Framework <a name="introduction"></a>

Ten artykuł zawiera podsumowanie kluczowych nowych funkcji i ulepszeń w następujących wersjach systemu .NET Framework:

- [.NET Framework 4.7.2](#v472)
- [.NET Framework 4.7.1](#v471)
- [.NET Framework 4.7](#v47)
- [.NET Framework 4.6.2](#v462)
- [.NET Framework 4.6.1](#v461)
- [.NET 2015 i .NET Framework 4.6](#v46)
- [.NET Framework 4.5.2](#v452)
- [.NET Framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Ten artykuł nie zawiera wyczerpujących informacji odnośnie każdej nowej funkcji i może ulec zmianie. Aby uzyskać ogólne informacje dotyczące programu .NET Framework, zobacz [wprowadzenie](../../../docs/framework/get-started/index.md). Dla obsługiwanych platform, zobacz [wymagania systemowe](~/docs/framework/get-started/system-requirements.md). Łącza pobierania oraz instrukcje dotyczące instalacji, zobacz [Przewodnik instalacji](../../../docs/framework/install/guide-for-developers.md).

> [!NOTE]
> Zespół .NET Framework udostępnia również funkcje poza pasmem z NuGet, aby rozwijać obsługę platform i wprowadzać nowe funkcje, takie jak niezmienne kolekcje i typy wektorowe obsługujące na SIMD. Aby uzyskać więcej informacji, zobacz [dodatkowe biblioteki klas i interfejsów API](../additional-apis/index.md) i [.NET Framework i wersji Out-of-Band](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md). Zobacz [pełną listę pakietów NuGet](https://blogs.msdn.microsoft.com/dotnet/p/nugetpackages/) dla programu .NET Framework lub subskrybować [nasz Kanał informacyjny](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).

<a name="v472" />

## <a name="introducing-the-net-framework-472"></a>Wprowadzenie do programu .NET Framework 4.7.2

.NET Framework 4.7.2 opiera się na poprzednie wersje programu .NET Framework 4.x, dodając wiele nowych usprawnień i kilka nowych funkcji, pozostając bardzo stabilnego produktu.

### <a name="downloading-and-installing-the-net-framework-472"></a>Pobieranie i instalowanie programu .NET Framework 4.7.2

.NET Framework 4.7.2 można pobrać z następujących lokalizacji:

- [Instalator programu .NET framework 4.7.2 sieci Web](https://go.microsoft.com/fwlink/?LinkId=863262)

- [NET Framework 4.7.2 Instalator w trybie Offline](https://go.microsoft.com/fwlink/?LinkId=863265)

.NET Framework 4.7.2 można zainstalować w systemie Windows 10, Windows 8.1, Windows 7 z dodatkiem SP1 i odpowiednich platform serwerowych, począwszy od systemu Windows Server 2008 R2 SP1. .NET Framework 4.7.2 można zainstalować za pomocą Instalatora sieci web lub Instalatora w trybie offline. Zalecaną metodą dla większości użytkowników jest użycie Instalatora sieci web.

Możesz wybrać docelową programu .NET Framework 4.7.2 w programie Visual Studio 2012 lub nowszym, instalując [pakiet dla deweloperów .NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=874338).

### <a name="whats-new-in-the-net-framework-472"></a>What's new in .NET Framework 4.7.2

.NET Framework 4.7.2 zawiera nowe funkcje w następujących obszarach:

- [Funkcje podstawowe](#core-472)
- [ASP.NET](#asp-net472)
- [Sieć](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

Kontynuowanie skoncentrować się na platformie .NET Framework 4.7.2 jest ulepszone ułatwień dostępu, który umożliwia aplikacji zapewnić odpowiednie środowisko dla użytkowników technologii pomocniczej. Aby uzyskać informacji na temat ulepszenia ułatwień dostępu w programie .NET Framework 4.7.2, zobacz [What's new in ułatwień dostępu w programie .NET Framework](whats-new-in-accessibility.md).

<a name="core-472" />

#### <a name="core"></a>Core

.NET Framework 4.7.2 zawiera dużą liczbę rozszerzeń kryptograficznych, lepszą obsługę dekompresji archiwa ZIP i dodatkową kolekcję interfejsów API.

**Nowe przeciążenia RSA. Tworzenie i DSA. Utwórz**

<xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> i <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> metody umożliwiają określanie parametrów klucza podczas tworzenia wystąpienia nowego <xref:System.Security.Cryptography.DSA> lub <xref:System.Security.Cryptography.RSA> klucza. Umożliwiają one Zastąp kod, jak pokazano poniżej:

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

<xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> i <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> metody umożliwiają generowanie nowych <xref:System.Security.Cryptography.DSA> lub <xref:System.Security.Cryptography.RSA> kluczy z określonym kluczem o rozmiarze. Na przykład:

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

<xref:System.Security.Cryptography.Rfc2898DeriveBytes> Klasa ma trzy konstruktory nowe z <xref:System.Security.Cryptography.HashAlgorithmName> parametr, który identyfikuje algorytmem HMAC do użycia podczas wyprowadzania kluczy. Zamiast przy użyciu algorytmu SHA-1, deweloperzy powinny używać HMAC oparte na SHA-2, takie jak algorytm SHA-256, jak pokazano w poniższym przykładzie:

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

Importuj plik PFX Opcjonalnie można załadować kluczy prywatnych bezpośrednio z pamięci, z pominięciem dysku twardego. Po nowe <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flaga jest określona w <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> konstruktora lub jednego z przeciążeń <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> metody, kluczy prywatnych, które będą ładowane jako klucze tymczasowe. Zapobiega to kluczy jest widoczny na dysku. Jednak:

- Ponieważ klucze nie są zachowywane na dysku, certyfikaty ładowane za pomocą tej flagi nie są dobrymi kandydatami do dodania do X509Store.

- Klucze załadowane w ten sposób prawie zawsze są ładowane za pomocą Windows CNG. W związku z tym, obiekty wywołujące muszą dostępu do klucza prywatnego przez wywołanie metody rozszerzenia, takie jak [certyfikatu. GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> Właściwości nie działa.

- Od starszego <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> właściwości nie działa z certyfikatami, deweloperzy należy wykonywać rygorystyczne testy przed przełączeniem do kluczy tymczasowych.

**Programowe tworzenie żądania podpisywania PKCS #10 certyfikacji i certyfikatów kluczy publicznych X.509**

Począwszy od programu .NET Framework 4.7.2 obciążeń można wygenerować certyfikatu podpisywania żądania (CSR), który umożliwia generowanie żądania certyfikatu, zostaną umieszczone w istniejących narzędzi. Jest to często przydatne w scenariuszach testowych.

Aby uzyskać więcej informacji i przykłady kodu, zobacz "programowe tworzenie PKCS #10 żądań podpisywania certyfikacji i certyfikatów kluczy publicznych X.509" w [bloga platformy .NET](https://blogs.msdn.microsoft.com/dotnet/2018/03/08/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Nowi członkowie SignerInfo**

Począwszy od programu .NET Framework 4.7.2, <xref:System.Security.Cryptography.Pkcs.SignerInfo> klasa udostępnia więcej informacji o podpisie. Można pobrać wartość <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> własność, aby określić algorytm podpisu używane przez osoby podpisującej. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> można wywołać można uzyskać kopię podpisu kryptograficznego tej osoby podpisującej.

**Mając otwarte strumieniem opakowanej po usunięciu CryptoStream**

Począwszy od programu .NET Framework 4.7.2, <xref:System.Security.Cryptography.CryptoStream> klasa ma dodatkowym konstruktorze umożliwiającą <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> nie zamknąć opakowana strumienia. Pozostanie opakowana strumienia otwarte po <xref:System.Security.Cryptography.CryptoStream> wystąpienia zostanie usunięty, wywoływał nową <xref:System.Security.Cryptography.CryptoStream> konstruktora w następujący sposób:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```
```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**Dekompresja zmiany DeflateStream**

Począwszy od programu .NET Framework 4.7.2, wykonywania działań dekompresji w <xref:System.IO.Compression.DeflateStream> klasy zmienił się na domyślnie używają natywnych interfejsów API Windows. Zazwyczaj powoduje to zwiększenie wydajności istotne.

Obsługa dekompresji przy użyciu interfejsów API Windows jest domyślnie włączone dla aplikacji przeznaczonych dla środowiska .NET Framework 4.7.2. Aplikacje docelowe wcześniejszych wersji programu .NET Framework, które są uruchomione na platformie .NET Framework 4.7.2 zdecydować się na to zachowanie przez dodanie poniższego [przełącznika AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do pliku konfiguracji aplikacji:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**Dodatkową kolekcję interfejsów API**

.NET Framework 4.7.2 dodaje wiele nowych interfejsów API do <xref:System.Collections.Generic.SortedSet%601> i <xref:System.Collections.Generic.HashSet%601> typów. Należą do nich następujące elementy:

- `TryGetValue` metody, które rozszerzyć wzorzec spróbuj używany w inne typy kolekcji do tych dwóch typów. Dostępne są następujące metody:

   - [bool publiczny zestaw HashSet<T>. TryGetValue (out T actualValue T equalValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
   - [publiczne bool SortedSet<T>. TryGetValue (out T actualValue T equalValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- `Enumerable.To*` metody rozszerzenia, które kolekcję, aby przekonwertować <xref:System.Collections.Generic.HashSet%601>:

   - [publiczne statyczne hashset —<TSource> ToHashSet<TSource>(to interfejs IEnumerable<TSource> źródła)](xref:System.Linq.Enumerable.ToHashSet%2A)
   - [publiczne statyczne hashset —<TSource> ToHashSet<TSource>(to interfejs IEnumerable<TSource> źródła IEqualityComparer<TSource> modułu porównującego)](xref:System.Linq.Enumerable.ToHashSet%2A)

- Nowe <xref:System.Collections.Generic.HashSet%601> konstruktorów, które pozwalają ustawić pojemności kolekcji stopa wydajności, gdy wiesz rozmiar <xref:System.Collections.Generic.HashSet%601> wcześniej:

   - [publiczny zestaw HashSet (pojemność int)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
   - [hashset — publiczny (int pojemności, IEqualityComparer<T> modułu porównującego)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

<xref:System.Collections.Concurrent.ConcurrentDictionary%602> Klasa zawiera nowe przeciążenia <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody do pobierania wartości ze słownika lub dodać go, jeśli nie zostanie znaleziony, a także dodać wartość do słownika lub zaktualizować go, jeśli już istnieje.

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

**Obsługa wstrzykiwanie zależności w formularzach sieci Web**

[Wstrzykiwanie zależności (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) oddziela obiektów i ich zależności, aby kod obiektu nie jest już musi zostać zmienione tylko w przypadku, ponieważ zależność została zmieniona. Podczas tworzenia aplikacji ASP.NET, które obsługują program .NET Framework 4.7.2, możesz wykonywać następujące czynności:

- Użyj iniekcji na podstawie metody ustawiającej, oparte na interfejsie i na podstawie konstruktora w [programów obsługi i modułów](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [stronie wystąpień](xref:System.Web.UI.Page), i [kontrolki użytkownika](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) aplikacji internetowej platformy ASP.NET projekty.

- Użyj metody ustawiającej, jak i oparty na iniekcji w [programów obsługi i modułów](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [stronie wystąpień](xref:System.Web.UI.Page), i [kontrolki użytkownika](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) projektów witryny sieci web platformy ASP.NET.

- Podłącz struktur iniekcji zależności różne.

**Obsługa plików cookie w tej samej lokacji**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) zapobiega wysyłaniu pliku cookie wraz z żądaniem między lokacjami w przeglądarce. .NET Framework 4.7.2 dodaje <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> właściwości, których wartość jest <xref:System.Web.SameSiteMode?displayProperty=nameWithType> element członkowski wyliczenia. Jeśli wartość to <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> lub <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET dodaje `SameSite` atrybutu do nagłówka set-cookie. Obsługa SameSite dotyczy <xref:System.Web.HttpCookie> obiekty, jak również jako do <xref:System.Web.Security.FormsAuthentication> i <xref:System.Web.SessionState> plików cookie.

Możesz ustawić SameSite dla <xref:System.Web.HttpCookie> obiektu w następujący sposób:

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```
```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```
SameSite plików cookie można również skonfigurować na poziomie aplikacji, modyfikując plik web.config:

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

.NET Framework 4.7.1 dodano osiem właściwości <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> klasy. Jednak dwa zgłosił <xref:System.PlatformNotSupportedException>. .NET Framework 4.7.2 udostępnia teraz implementację tych właściwości. Dostępne są następujące właściwości:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a>SQLClient

**Obsługa usługi Azure Active Directory Universal Authentication oraz uwierzytelnianie wieloskładnikowe**

Rosnących wymagań zgodności i zabezpieczeń wymagają, że wielu klientów używa usługi uwierzytelnianie wieloskładnikowe (MFA). Ponadto bieżące najlepszych rozwiązań zniechęcić tym haseł użytkowników bezpośrednio w parametrach połączenia. Aby obsługiwać te zmiany, rozszerza .NET Framework 4.7.2 [ciągi połączeń klient SQL](xref:System.Data.SqlClient.SqlConnection.ConnectionString) , dodając nową wartość "Active Directory interaktywnych" dla istniejących — słowo kluczowe "Uwierzytelnianie" do obsługi uwierzytelniania Wieloskładnikowego i [usługi Azure AD Uwierzytelnianie](/azure/sql-database/sql-database-aad-authentication-configure). Nowy przypadku metody interakcyjnej obsługuje natywne i Federacyjna użytkowników usługi Azure AD, a także użytkowników-gości usługi Azure AD. W przypadku tej metody uwierzytelniania MFA nałożone przez usługę Azure AD jest obsługiwana dla baz danych SQL. Ponadto proces uwierzytelniania żąda hasła użytkownika, aby stosować najlepsze rozwiązania dotyczące zabezpieczeń.

W poprzednich wersjach programu .NET Framework, łączność z serwerem SQL obsługuje tylko <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> i <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> opcje. Oba te są częścią nieinterakcyjnej [ADAL protokołu](/azure/active-directory/develop/active-directory-authentication-libraries), który nie obsługuje uwierzytelniania Wieloskładnikowego. Przy użyciu nowego <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> opcja, łączność z serwerem SQL obsługuje uwierzytelnianie wieloskładnikowe, a także istniejących metod uwierzytelniania (hasła i zintegrowane uwierzytelnianie), który umożliwia użytkownikom wprowadzanie haseł użytkowników interaktywnie bez przechowywanie haseł w połączeniu ciąg.

Aby uzyskać więcej informacji i obejrzeć przykład, zobacz "SQL — AD uniwersalnych i Multi-Factor Authentication pomocy technicznej systemu Azure" w [bloga platformy .NET](https://blogs.msdn.microsoft.com/dotnet/2018/03/08/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Obsługa zawsze szyfrowane w wersji 2**

NET Framework 4.7.2 dodaje obsługuje na podstawie enklawy Always Encrypted. Oryginalna wersja są zawsze szyfrowane jest technologii szyfrowania po stronie klienta, w których szyfrowania kluczy nigdy nie opuszczają klienta. W podstawie enklawy Always Encrypted klient może wysłać opcjonalnie kluczy szyfrowania do bezpiecznego enklawy, który jest jednostką obliczeniową bezpiecznego można je traktować jako część programu SQL Server, ale, że nie można modyfikować kodu programu SQL Server. Aby zapewnić obsługę na podstawie enklawy Always Encrypted, .NET Framework 4.7.2 dodaje następujące typy i elementy członkowskie do <xref:System.Data.SqlClient> przestrzeni nazw:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, który określa identyfikator Uri na podstawie enklawy Always Encrypted.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, która jest klasą abstrakcyjną, z których wszystkie enklawy wywodzą się dostawców.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, która hermetyzuje stan enklawy danej sesji.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, zapewniającą parametry zaświadczania używany przez program SQL Server można pobrać informacji wymaganych do wykonania konkretnego protokołu zaświadczania.

Plik konfiguracji aplikacji Określa konkretną implementację abstrakcyjnej <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> klasy, który udostępnia funkcjonalność dla dostawcy enklawy. Na przykład:

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

Podstawowy przepływ na podstawie enklawy Always Encrypted to:

1. Użytkownik tworzy połączenie AlwaysEncrypted do programu SQL Server obsługiwane na podstawie enklawy Always Encrypted. Sterownik kontaktuje się z usługą zaświadczania, aby upewnić się, nawiązuje połączenie z do prawego enklawy.

1. Po enklawy została potwierdzona, sterownik nawiązuje bezpiecznego kanału z bezpiecznego enklawy hostowanych w programie SQL Server.

1. Sterownik udostępnia klucze szyfrowania autoryzowane przez klienta z bezpiecznego enklawy na czas trwania połączenia SQL.

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Znajdowanie ResourceDictionaries według źródła**

Począwszy od programu .NET Framework 4.7.2 diagnostycznych Asystent mogą zlokalizować <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> które zostały utworzone z danego źródła identyfikatora Uri. (Ta funkcja jest do użytku asystentów diagnostyczne, a nie aplikacji produkcyjnych). Diagnostyczne Asystenta ustawień, takich jak Visual Studio "Edit-and-Continue" funkcji umożliwia jej użytkownika Edytuj ResourceDictionary z zamiarem, że zmiany zastosowane do uruchomionej aplikacji. Jeden krok w osiągnięciu tego celu jest znalezienie wszystkich ResourceDictionaries utworzonych ze słownika, która jest edytowany uruchomionej aplikacji. Na przykład aplikacja może zadeklarować ResourceDictionary, którego zawartość zostanie skopiowana ze źródłem danego identyfikatora URI:

```xml
<ResourceDictionary Source="MyRD.xaml">
```

Asystent diagnostycznych, który umożliwia edycję w oryginale *MyRD.xaml* można użyć nowej funkcji do zlokalizowania w słowniku. Ta funkcja jest implementowany przez nowej metody statyczne, <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>. Asystent diagnostycznych wywołuje nowej metody przy użyciu bezwzględny identyfikator Uri identyfikujący oryginalny kod znaczników, jak pokazano w poniższym kodzie:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```
```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

Metoda zwraca pustą wyliczalny chyba że <xref:System.Windows.Diagnostics.VisualDiagnostics> jest włączona i [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  zmienna środowiskowa jest ustawiona.

**Znajdowanie ResourceDictionary właścicieli**

Począwszy od programu .NET Framework 4.7.2 diagnostycznych Asystent mogą zlokalizować właściciele danego <xref:Windows.UI.Xaml.ResourceDictionary>. (Ta funkcja jest do użytku przez diagnostycznych asystentów a nie przez aplikacje produkcyjne). Zawsze, gdy zostanie zmienione <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automatycznie znajdzie wszystkie [dynamicresource —](../wpf/advanced/dynamicresource-markup-extension.md) odwołań, które mogą mieć wpływ zmiany.

Diagnostyczne Asystenta ustawień, takich jak Visual Studio "Edit-and-Continue" funkcji postanowić, aby rozszerzyć takie rozwiązanie pozwoli obsługiwać [staticresource —](../wpf/advanced/staticresource-markup-extension.md) odwołania. Pierwszym krokiem w ramach tego procesu jest znalezienie właściciele słownika; oznacza to aby znaleźć wszystkie obiekty którego `Resources` właściwość odwołuje się do słownika (albo bezpośrednio lub pośrednio za pośrednictwem <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> właściwości). Trzy nowe metody statyczne implementowane w <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> klasy, jednej dla każdego z typów podstawowych, które ma `Resources` właściwości, obsługują ten krok:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Te metody zwracają pustą wyliczalny chyba że <xref:System.Windows.Diagnostics.VisualDiagnostics> jest włączona i [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  zmienna środowiskowa jest ustawiona.

**Trwa znajdowanie odwołań staticresource —**

Asystent diagnostyczne mogą teraz otrzymać powiadomienie po każdym [staticresource —](../wpf/advanced/staticresource-markup-extension.md) odwołanie nie zostanie rozwiązany. (Ta funkcja jest do użytku asystentów diagnostyczne, a nie aplikacji produkcyjnych). Diagnostyczne Asystenta ustawień, takich jak Visual Studio "Edit-and-Continue" funkcji może być zaktualizowanie wszystkie przypadki użycia zasobu po jego wartości w <xref:Windows.UI.Xaml.ResourceDictionary> zmiany. WPF dzieje automatyczne [dynamicresource —](../wpf/advanced/dynamicresource-markup-extension.md) odwołania, ale celowo nie jest to [staticresource —](../wpf/advanced/staticresource-markup-extension.md) odwołania. Począwszy od programu .NET Framework 4.7.2 diagnostycznych Asystenta ustawień, można użyć tych powiadomień do zlokalizowania tych zastosowań zasób statyczny.

Powiadomienie jest implementowany przez nowy <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> zdarzeń:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

To zdarzenie jest wywoływane zawsze wtedy, gdy środowisko uruchomieniowe rozpoznaje [staticresource —](../wpf/advanced/staticresource-markup-extension.md) odwołania. <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> Argumenty opisano rozwiązania i wskazać obiektów i właściwości hostujących [staticresource —](../wpf/advanced/staticresource-markup-extension.md) odwołania i <xref:Windows.UI.Xaml.ResourceDictionary> i klucz użyty do rozwiązania:

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

Zdarzenie nie zostanie wywołane (i jego `add` metody dostępu jest ignorowana) chyba że <xref:System.Windows.Diagnostics.VisualDiagnostics> jest włączona i [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  zmienna środowiskowa jest ustawiona.

#### <a name="clickonce"></a>ClickOnce

HDPI aplikacje z obsługą formularzy Windows, Windows Presentation Foundation (WPF) i Visual Studio Tools dla pakietu Office (VSTO) można wdrożyć przy użyciu technologii ClickOnce. Jeśli następujący wpis zostanie znaleziony w manifeście aplikacji, wdrożenie powiedzie się na platformie .NET Framework 4.7.2:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

Dla aplikacji Windows Forms obejście poprzednie ustawienia świadomości DPI w pliku konfiguracyjnym aplikacji, a nie w manifeście aplikacji nie jest już niezbędne do pomyślnego wdrożenia ClickOnce.

<a name="v471" />

## <a name="whats-new-in-the-net-framework-471"></a>What's new in .NET Framework 4.7.1

.NET Framework 4.7.1 zawiera nowe funkcje w następujących obszarach:

- [Funkcje podstawowe](#core471)
- [Środowisko uruchomieniowe języka wspólnego (CLR)](#clr)
- [Sieć](#net471)
- [ASP.NET](#asp-net471)

Ponadto główne skoncentrować się na platformie .NET Framework 4.7.1 jest ulepszone ułatwień dostępu, który umożliwia aplikacji zapewnić odpowiednie środowisko dla użytkowników technologii pomocniczej. Aby uzyskać informacji na temat ulepszenia ułatwień dostępu w programie .NET Framework 4.7.1, zobacz [What's new in ułatwień dostępu w programie .NET Framework](whats-new-in-accessibility.md).

<a name="core471" />

#### <a name="core"></a>Core

**Obsługa .NET Standard 2.0**

[.NET standard](~/docs/standard/net-standard.md) definiuje zestaw interfejsów API, które muszą być dostępne w każdej implementacji .NET, która obsługuje daną wersję standard. .NET Framework 4.7.1 w pełni obsługuje .NET Standard 2.0 i dodaje [około 200 interfejsów API](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) które są zdefiniowane w programie .NET Standard 2.0 i brakuje w .NET Framework 4.7, 4.6.1 i 4.6.2. (Zwróć uwagę, że te wersje programu .NET Framework obsługuje .NET Standard 2.0, tylko wtedy, gdy dodatkowe pliki obsługi .NET Standard są wdrożone w systemie docelowym). Aby uzyskać więcej informacji, zobacz "BCL — .NET Standard 2.0 Support" w [środowiska uruchomieniowego .NET Framework 4.7.1 i funkcje kompilatora](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) wpis w blogu.

**Obsługa konfiguracji konstruktorów**

Konstruktorzy konfiguracji umożliwiają deweloperom wstrzyknąć i ustawienia konfiguracji dla aplikacji mają być dynamicznie kompilacji w czasie wykonywania. Konfiguracja niestandardowa Konstruktorzy może służyć do modyfikowania istniejących danych w sekcji konfiguracji lub Tworzenie sekcji konfiguracji całkowicie od podstaw. Bez Konstruktorzy konfiguracji pliki .config są statyczne i ich ustawienia są definiowane trochę czasu, zanim aplikacja zostanie uruchomiona.

Aby utworzyć Konstruktor konfiguracji niestandardowej, możesz dziedziczyć z konstruktora abstrakcyjnej <xref:System.Configuration.ConfigurationBuilder> klasy i zastąp jego <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> i <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. W pliku .config są również definiować swoje konstruktorów. Aby uzyskać więcej informacji, zobacz sekcję "Konfiguracja Konstruktorzy" w [platformy .NET Framework 4.7.1 ASP.NET i funkcje konfiguracji](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) wpis w blogu.

**Wykrywanie funkcji wykonawczej**

<xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> Klasa udostępnia mechanizm dla należy określić, czy wstępnie zdefiniowane funkcji jest obsługiwane w danej implementacji .NET w czasie kompilacji lub w czasie wykonywania. W czasie kompilacji kompilator można sprawdzić, czy określone pole istnieje w celu ustalenia, czy ta funkcja jest obsługiwana; Jeśli tak, jego może emitować Kod, który korzysta z zalet tej funkcji. W czasie wykonywania aplikacja może wywołać <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metody przed emitowanie kodu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Dodaj metodę pomocnika do opisania funkcje obsługiwane przez środowisko uruchomieniowe](https://github.com/dotnet/corefx/issues/17116).

**Typy krotki wartości są możliwe do serializacji**

Począwszy od programu .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> i ich skojarzone typy ogólne są oznaczone jako [Serializable](xref:System.SerializableAttribute), co pozwala serializacji binarnej. Powinna stanowić Migrowanie typy krotek, takich jak <xref:System.Tuple%603> i <xref:System.Tuple%604>, aby łatwiej typy krotki wartości. Aby uzyskać więcej informacji, zobacz "Kompilatora — ValueTuple jest możliwy do serializacji" w [środowiska uruchomieniowego .NET Framework 4.7.1 i funkcje kompilatora](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) wpis w blogu.

**Obsługa odwołań tylko do odczytu**

Dodaje platformy .NET Framework 4.7.1 <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>. Ten atrybut jest używany przez Kompilatory języka aby oznaczyć elementy członkowskie, których typy zwracane ref tylko do odczytu lub parametrów. Aby uzyskać więcej informacji, zobacz "Kompilatora — obsługa dla ReadOnlyReferences" w [środowiska uruchomieniowego .NET Framework 4.7.1 i funkcje kompilatora](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) wpis w blogu. Aby uzyskać informacje na wartości zwracane ref, zobacz [Ref zwracać wartości i ref, zmienne lokalne (Przewodnik C#)](~/docs/csharp/programming-guide/classes-and-structs/ref-returns.md) i [Ref zwracane wartości (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />

#### <a name="common-language-runtime-clr"></a>Środowisko uruchomieniowe języka wspólnego (CLR)

**Ulepszenia wydajności kolekcji wyrzucania elementów**

Zmiany do wyrzucania elementów bezużytecznych (GC) w programie .NET Framework 4.7.1 zwiększyć ogólną wydajność, szczególnie w przypadku dużych sterty obiektów (LOH) alokacji. W .NET Framework 4.7.1 oddzielne blokady są używane do alokacje małych obiektów sterty raportu i LOH, co pozwala alokacje LOH występuje wówczas, gdy tło GC (BGC) jest sprawdzaniu raport o kondycji. W rezultacie aplikacje wchodzące w dużej liczby alokacji LOH powinien zostać wyświetlony zmniejszenia rywalizacji o blokadę alokację i wydajności. Aby uzyskać więcej informacji, zobacz sekcję "Środowiska uruchomieniowego — GC wydajności Improvements" w [środowiska uruchomieniowego .NET Framework 4.7.1 i funkcje kompilatora](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features/) wpis w blogu.

<a name="net471"/>

#### <a name="networking"></a>Obsługa sieci

**Obsługa Message.HashAlgorithm SHA-2**

W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> wartości właściwości obsługiwane <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> i <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> tylko. Począwszy od programu .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, i <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> są również obsługiwane. Czy ta wartość będzie faktycznie używana jest zależna od usługi MSMQ, ponieważ <xref:System.Messaging.Message> samego wystąpienia jest nie wyznaczania wartości skrótu, ale po prostu przekazuje wartości do usługi MSMQ. Aby uzyskać więcej informacji, zobacz sekcję "Obsługa SHA-2 Message.HashAlgorithm" w [funkcje platformy .NET Framework 4.7.1 ASP.NET i konfiguracji](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features/) wpis w blogu.

<a name="asp-net471" />

#### <a name="aspnet"></a>ASP.NET

**Wykonanie kroków w aplikacjach ASP.NET**

ASP.NET przetwarza żądania w wstępnie zdefiniowanych potok, który zawiera zdarzenia 23. ASP.NET wykonuje każdy program obsługi zdarzeń jako etap wykonywania. W wersjach programu ASP.NET do programu .NET Framework 4.7 ASP.NET, nie można wykonać przepływu kontekstu wykonywania, ze względu na przełączanie między natywnych i zarządzanych wątków. Zamiast tego ASP.NET selektywnie przepływa tylko <xref:System.Web.HttpContext>. Począwszy od programu .NET Framework 4.7.1, <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> metoda umożliwia również modułów, aby przywrócić dane otoczenia. Ta funkcja jest przeznaczona dla danych ze śledzenia, profilowanie, diagnostyki lub transakcji, na przykład bibliotek, które interesują przepływ wykonania aplikacji. Aby uzyskać więcej informacji, zobacz "Wykonywanie kroku funkcję ASP.NET" w [platformy .NET Framework 4.7.1 ASP.NET i funkcje konfiguracji](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) wpis w blogu.

**HttpCookie ASP.NET analizy**

Program .NET Framework 4.7.1 zawiera nową metodę <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, która udostępnia standardowy sposób tworzenia <xref:System.Web.HttpCookie> obiekt z ciągu i precyzyjne przypisywanie wartości pliku cookie, takie jak Data wygaśnięcia i ścieżkę. Aby uzyskać więcej informacji, zobacz "Podczas analizowania HttpCookie ASP.NET" w [platformy .NET Framework 4.7.1 ASP.NET i funkcje konfiguracji](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) wpis w blogu.

**Opcje wyznaczania wartości skrótu SHA-2 dla poświadczenia uwierzytelniania formularzy programu ASP.NET**

W .NET Framework 4.7 i wersjach starszych program ASP.NET dozwolone deweloperom przechowywać poświadczenia użytkownika przy użyciu haseł w formie skrótu w plikach konfiguracji przy użyciu algorytmu MD5 lub SHA1. Począwszy od programu .NET Framework 4.7.1 ASP.NET obsługuje również nowe opcje wyznaczania wartości skrótu SHA-2 bezpieczny SHA256, SHA384 i SHA512. Algorytm SHA1 pozostanie domyślnie i algorytm wyznaczania wartości skrótu innych niż domyślne można zdefiniować w pliku konfiguracji sieci web. Na przykład:

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

<a name="v47" />

## <a name="whats-new-in-the-net-framework-47"></a>Co nowego w programie .NET Framework 4.7

.NET Framework 4.7 zawiera nowe funkcje w następujących obszarach:

- [Funkcje podstawowe](#Core47)
- [Sieć](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Aby uzyskać listę nowych interfejsów API jest dodawany do programu .NET Framework 4.7, zobacz [zmiany interfejsu API programu .NET Framework 4.7](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) w witrynie GitHub. Aby uzyskać listę ulepszeń funkcji i poprawek błędów w programie .NET Framework 4.7, zobacz [.NET Framework 4.7 Lista zmian](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) w witrynie GitHub.  Aby uzyskać więcej informacji, zobacz [ogłoszenie .NET Framework 4.7](https://blogs.msdn.microsoft.com/dotnet/2017/04/05/announcing-the-net-framework-4-7/) w blogu .NET.

<a name="Core47" />

#### <a name="core"></a>Core

.NET Framework 4.7 zwiększa serializacji przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:

**Ulepszone funkcje za pomocą kryptografii krzywej eliptycznej (ECC)***

W programie .NET Framework 4.7 `ImportParameters(ECParameters)` metody zostały dodane do <xref:System.Security.Cryptography.ECDsa> i <xref:System.Security.Cryptography.ECDiffieHellman> klasę, aby umożliwić dla obiektu do reprezentowania klawiszem już ustanowione. `ExportParameters(Boolean)` Metoda został również dodany eksportu klucza przy użyciu parametrów jawne krzywej.

.NET Framework 4.7 również dodaje obsługę dodatkowych krzywych (w tym pakiet krzywej Brainpool) oraz dodano wstępnie zdefiniowanych definicje łatwość z tworzenia za pomocą nowego <xref:System.Security.Cryptography.ECDsa.Create%2A> i <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> metodach fabryki.

Możesz zobaczyć [przykład ulepszenia kryptografii programu .NET Framework 4.7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) w witrynie GitHub.

**Lepsza obsługa kontroli znaków, w ramach elementu DataContractJsonSerializer**

W programie .NET Framework 4.7 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializuje znaków kontrolnych, zgodnie z standard ECMAScript 6. To zachowanie jest domyślnie włączone dla aplikacji przeznaczonych dla środowiska .NET Framework 4.7, a to funkcja opcjonalna w przypadku aplikacji, które są uruchomione w .NET Framework 4.7, ale odwoływać się do poprzedniej wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [zmiany Retargetingu w programie .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />

#### <a name="networking"></a>Obsługa sieci

.NET Framework 4.7 dodanie następującej funkcji związanych z siecią:

**Domyślnie system operacyjny obsługuje protokoły TLS***

Stos protokołu TLS, który jest używany przez <xref:System.Net.Security.SslStream?displayProperty=nameWithType> i składników w górę stosu, takich jak HTTP, FTP i SMTP, umożliwia deweloperom korzystanie z domyślnych protokołów TLS obsługiwana przez system operacyjny. Deweloperzy muszą nie dłużej trwale kodować wersję protokołu TLS.

<a name="ASP-NET47" />

#### <a name="aspnet"></a>ASP.NET

W programie .NET Framework 4.7 program ASP.NET zawiera następujące nowe funkcje:

**Rozszerzalność pamięci podręcznej obiektu**

Począwszy od programu .NET Framework 4.7 ASP.NET dodaje nowy zestaw interfejsów API, które umożliwiają deweloperom w celu zastąpienia domyślnej implementacji platformy ASP.NET do monitorowania pamięci i buforowania obiektów w pamięci. Deweloperzy teraz zastąpić żadnego z następujących trzech składników, jeśli implementacja programu ASP.NET nie jest odpowiednia:

- **Object Cache Store**. Za pomocą nowej sekcji konfiguracji dostawcy pamięci podręcznej, deweloperzy można dodać nowego implementacjach pamięci podręcznej obiektów dla aplikacji ASP.NET za pomocą nowego **ICacheStoreProvider** interfejsu.

- **Monitorowanie pamięci**. Domyślny monitor pamięci w programie ASP.NET: powiadamia aplikacje uruchamianego bliski limitu skonfigurowanego prywatne bajty dla procesu, lub gdy komputer ma za mało całkowitej dostępnej pamięci fizycznej RAM. Gdy zbliża się te limity, powiadomienia są uruchamiane. W przypadku niektórych aplikacji Powiadomienia są uruchamiane zbyt Zamknij skonfigurowanego limitami, umożliwiające reakcje przydatne. Deweloperzy mogą zapisywać swoje własne monitorów pamięci, aby zastąpić domyślny za pomocą <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> właściwości.

- **Reakcje "Limit pamięci:**. Domyślnie program ASP.NET próbuje trim obiektu pamięci podręcznej i okresowo wywoływać <xref:System.GC.Collect%2A?displayProperty=nameWithType> gdy zbliża się limit prywatnych bajtów procesu. W niektórych aplikacjach częstotliwość wywołań <xref:System.GC.Collect%2A?displayProperty=nameWithType> lub ilości pamięci podręcznej, które są spacje są nieefektywne. Deweloperzy mogą teraz Zastąp lub uzupełniają domyślne zachowanie, subskrybując ten biuletyn **IObserver** implementacji w celu monitorowania pamięci aplikacji.

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) dodaje następujące funkcje i zmiany:

**Można skonfigurować domyślne ustawienia zabezpieczeń wiadomości protokołu TLS 1.1 lub protokołu TLS 1.2**

Począwszy od programu .NET Framework 4.7 WCF umożliwia skonfigurowanie TSL 1.1 lub protokołu TLS 1.2, oprócz protokołu SSL 3.0 i TSL 1.0 jako domyślnego protokołu zabezpieczeń wiadomości. To jest ustawienie zgłoszenie zgody na uczestnictwo w; Aby ją włączyć, należy dodać następujący wpis do pliku konfiguracyjnego aplikacji:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**Poprawiono niezawodność aplikacji WCF i serializacji WCF**

Usługi WCF zawiera szereg zmian w kodzie, które wyeliminować sytuację wyścigu, a więc poprawa wydajności i niezawodności opcje serializacji. Należą do nich następujące elementy:

- Lepsza obsługa kodu synchronicznego i asynchronicznego w wywołaniach mieszanie **SocketConnection.BeginRead** i **SocketConnection.Read**.
- Większa niezawodność podczas przerywania połączenia z **SharedConnectionListener** i **DuplexChannelBinder**.
- Większa niezawodność operacji serializacji, podczas wywoływania <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> metody.
- Większa niezawodność podczas usuwania kelner przez wywołanie metody **ChannelSynchronizer.RemoveWaiter** metody.

<a name="wf47" />

#### <a name="windows-forms"></a>Windows Forms

W programie .NET Framework 4.7 Windows Forms usprawnia obsługę wysokiej rozdzielczości DPI monitorów.

**Obsługa wysokiej rozdzielczości DPI**

Począwszy od aplikacji, których platformą docelową .NET Framework 4.7, .NET Framework funkcje wysokiej rozdzielczości DPI i dynamiczne DPI pomocy technicznej dla aplikacji Windows Forms. Obsługa wysokiej rozdzielczości DPI zwiększa układ i wygląd formularzy i kontrolek w wysokiej rozdzielczości DPI monitorów. Dynamiczne DPI zmienia układ i wygląd formularzy i kontrolki, gdy użytkownik zmieni współczynnik skalowania DPI lub wyświetlanie uruchomionej aplikacji.

Obsługa wysokiej rozdzielczości DPI to funkcja opcjonalna skonfigurowanego przez zdefiniowanie [ \<System.Windows.Forms.ConfigurationSection >](../configure-apps/file-schema/winforms/index.md) sekcji w pliku konfiguracyjnym aplikacji. Aby uzyskać więcej informacji na temat dodawania obsługa wysokiej rozdzielczości DPI i dynamiczna obsługa rozdzielczości DPI do aplikacji Windows Forms, zobacz [wysokiej rozdzielczości DPI pomocy technicznej w formularzach Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

W programie .NET Framework 4.7 WPF obejmuje następujące ulepszenia:

**Obsługa stosu dotyk/pióra, oparte na Windows WM_POINTER wiadomości**

Masz teraz możliwość korzystania z stosu dotyk/pióra, na podstawie [wiadomości WM_POINTER](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) zamiast Windows Ink usług platformy (WISP). Jest to funkcja opcjonalna w .NET Framework. Aby uzyskać więcej informacji, zobacz [zmiany Retargetingu w programie .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

**Nową metodę implementacji dla WPF, drukowanie interfejsów API**

WPF użytkownika drukowanie interfejsów API w <xref:System.Printing.PrintQueue?displayProperty=nameWithType> klasa wywołać Windows [interfejsu API pakietu dokument Drukuj](/windows/desktop/printdocs/tailored-app-printing-api) zamiast przestarzałego [API drukowanie plików XPS](/windows/desktop/printdocs/xps-printing). Wpływ tej zmiany na zgodność aplikacji w temacie [zmiany Retargetingu w programie .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="v462" />

## <a name="whats-new-in-the-net-framework-462"></a>What's new in .NET Framework 4.6.2

[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Zawiera nowe funkcje w następujących obszarach:

- [ASP.NET](#ASPNET462)

- [Kategorii znaków](#Strings)

- [Kryptografia](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Konwertowanie Windows Forms i WPF aplikacji do aplikacji platformy uniwersalnej systemu Windows](#UWPConvert)

- [Ulepszenia debugowania](#Debug462)

Aby uzyskać listę nowych interfejsów API jest dodawany do programu .NET Framework 4.6.2, zobacz [zmiany interfejsu API platformy .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) w witrynie GitHub. Aby uzyskać listę ulepszeń funkcji i poprawek błędów w programie .NET Framework 4.6.2, zobacz [platformy .NET Framework 4.6.2 Lista zmian](https://go.microsoft.com/fwlink/?LinkId=708778) w witrynie GitHub.  Aby uzyskać więcej informacji, zobacz [ogłoszenie .NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/) w blogu .NET.

<a name="ASPNET462" />

### <a name="aspnet"></a>ASP.NET

W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], program ASP.NET zawiera następujące ulepszenia:

**Ulepszona obsługa lokalizowane komunikaty o błędzie w modułów weryfikacji adnotacji danych**

Modułów weryfikacji adnotacji danych umożliwiają wykonywanie sprawdzania poprawności, dodając jeden lub więcej atrybutów do właściwości klasy. Ten atrybut <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element definiuje tekst komunikatu o błędzie, jeśli weryfikacja zakończy się niepowodzeniem. Począwszy od [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET ułatwia lokalizowanie komunikatów o błędach. Komunikaty o błędach będą zlokalizowane, jeśli:

1.  <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> Jest podawany jako atrybut weryfikacji.

2.  Plik zasobów jest przechowywany w folderze globalnego.

3.  Nazwa pliku zlokalizowanych zasobów ma postać `DataAnnotation.Localization.{` *nazwa*`}.resx`, gdzie *nazwa* jest nazwa kultury w formacie *languageCode* `-` *kod kraju/regionu* lub *languageCode*.

4.  Nazwa klucza zasobu jest ciąg znaków, przypisany do <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atrybutu i jego wartość jest komunikat o błędzie zlokalizowane.

Na przykład następujący atrybut adnotacji danych definiuje komunikat o błędzie domyślną kulturę używaną do oceny nieprawidłowy.

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

Następnie można utworzyć pliku zasobów, DataAnnotation.Localization.fr.resx, którego klucz jest ciąg komunikatu o błędzie, którego wartość jest komunikat o błędzie zlokalizowane. Plik musi zostać znaleziony w `App.LocalResources` folderu. Na przykład Oto klucz i jego wartość w zlokalizowanych francuski (fr) języka komunikat o błędzie:

| Nazwa                                 | Wartość                                     |
| ------------------------------------ | ----------------------------------------- |
| Klasyfikacja musi mieć od 1 do 10. | Uwaga la ętre doit obejmują entre 1 et 10. |

 Ponadto lokalizacja adnotacji danych jest rozszerzalny. Deweloperzy można dodać własne dostawcy lokalizatorowi ciąg przez zaimplementowanie <xref:System.Web.Globalization.IStringLocalizerProvider> interfejs do przechowywania ciągu lokalizacji gdzieś innych niż w pliku zasobów.

 **Obsługa Async z dostawcami magazynu stanu sesji**

 ASP.NET umożliwia teraz metody zwracającą zadanie ma być używany z dostawcami magazynu stanu sesji, co pozwoli na aplikacje programu ASP.NET, aby w pełni skalowalność zalety asynchronicznych. Aby obsługuje operacje asynchroniczne przy użyciu stanu sesji należy przechowywać dostawców, program ASP.NET zawiera nowy interfejs <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, który dziedziczy z <xref:System.Web.IHttpModule> i pozwalają deweloperom na wdrażanie własnych stanu sesji modułu i async magazynu dostawcy sesji. Interfejs jest zdefiniowana w następujący sposób:

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

 Ponadto <xref:System.Web.SessionState.SessionStateUtility> klasa zawiera dwie nowe metody, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> i <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, który może służyć do obsługi operacji asynchronicznych.

 **Asynchroniczna pomoc techniczna dla dostawców pamięci podręcznej danych wyjściowych**

 Począwszy od [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zwracającą zadanie metody może służyć za pomocą dostawcy pamięci podręcznej danych wyjściowych do zapewnienia skalowalności zalety asynchronicznych.  Dostawcy, które implementują te metody zmniejszyć blokuje wątku na serwerze sieci web i poprawić skalowalność usługi ASP.NET.

 Następujące interfejsy API zostały dodane do obsługi asynchronicznego dostawcy pamięci podręcznej danych wyjściowych:

- <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> Klasy, która dziedziczy po elemencie <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> i pozwalają deweloperom na wdrażanie asynchronicznej dostawca wyjściowej pamięci podręcznej.

- <xref:System.Web.Caching.OutputCacheUtility> Klasy, która zapewnia metody pomocnika do konfigurowania pamięci podręcznej danych wyjściowych.

- 18 nowych metod w <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> klasy. Obejmują one <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, i <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.

- 2 nowych metod w <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> klasy: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> i <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.

- 2 nowych metod w <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> klasy: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> i <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.

- 2 nowych metod w <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> klasy: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> i <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.

- W <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> klasy <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> metody.

- W <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metody.

<a name="Strings" />

### <a name="character-categories"></a>Kategorii znaków
 Znaki w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] są klasyfikowane na podstawie [standardu Unicode, wersja 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] i [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], znaki były klasyfikowane na podstawie kategorii znaków Unicode 6.3.

 Obsługa Unicode 8.0 jest ograniczona do klasyfikacji znaków, w ramach <xref:System.Globalization.CharUnicodeInfo> klas i typów i metod, które polegać na niej. Obejmują one <xref:System.Globalization.StringInfo> klasy przeciążone <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> metody i [klasy znaku](../../../docs/standard/base-types/character-classes-in-regular-expressions.md) rozpoznawane przez aparat wyrażeń regularnych systemu .NET Framework.  Znakowe i porównywanie i sortowanie nie mają wpływu tej zmiany i nadal korzysta ze w podstawowym systemie operacyjnym lub w systemach Windows 7 na znak danych dostarczane przez program .NET Framework.

 Zmiany w kategorii znaków Unicode 6.0, 7.0 Unicode, zobacz [Unicode Standard, wersja 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) w witrynie sieci Web konsorcjum Unicode. Aby zmiany z Unicode 7.0 Unicode 8.0, zobacz [Unicode Standard, wersja 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) w witrynie sieci Web konsorcjum Unicode.

<a name="Crypto462" />

### <a name="cryptography"></a>Kryptografia

 **Obsługa X509 certyfikatów zawierających DSA FIPS 186 3**

 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Alokowanej dla DSA (algorytmu Digital Signature Algorithm) X509 certyfikatów, których klucze FIPS może przekraczać limitu 1024-bitowy 186-2.

 Oprócz obsługi większych rozmiarów klucza standardu FIPS 186-3, [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] pozwala na korzystanie z sygnaturami z rodziny SHA-2 algorytmów wyznaczania wartości skrótu (SHA256, SHA384 i SHA512). FIPS 186 3 w pomoc techniczna jest świadczona przez nowy <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> klasy.

 Zgodnie z najnowszych zmian w <xref:System.Security.Cryptography.RSA> klasy w .NET Framework 4.6 i <xref:System.Security.Cryptography.ECDsa> klasy w .NET Framework 4.6.1 <xref:System.Security.Cryptography.DSA> abstrakcyjna klasa bazowa w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ma dodatkowe metody, aby umożliwić wywołującym użyć tej funkcji funkcje bez rzutowania. Możesz wywołać <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> metodę rozszerzenia, aby zarejestrować dane, co ilustruje poniższy przykład.

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

Można też wywołać <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> metodę rozszerzenia, aby sprawdzić podpisanych danych, co ilustruje poniższy przykład.

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

 .NET Framework 3.5 dodano obsługę Ellipic krzywej Diffie'ego-Hellmana klucz Umowy z trzech różnych procedur funkcja wyprowadzania klucza (KDF). Dane wejściowe procedury i procedur, zostały skonfigurowane za pomocą właściwości na <xref:System.Security.Cryptography.ECDiffieHellmanCng> obiektu. Ale ponieważ nie każda procedura Odczyt wszystkich właściwości danych wejściowych, wystarczającą ilość miejsca na pomyłek w przeszłości dewelopera.

 Aby rozwiązać ten w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zostały dodane do następujących trzech metod <xref:System.Security.Cryptography.ECDiffieHellman> klasy bazowej na wyraźniej reprezentują tych procedur KDF i ich dane wejściowe:

|Metoda ECDiffieHellman|Opis|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Pochodzi materiału klucza przy użyciu formuły<br /><br /> SKRÓT (secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> SKRÓT (secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> gdzie *x* jest obliczana wynikiem algorytmu Diffie-Hellman WE.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Pochodzi materiału klucza przy użyciu formuły<br /><br /> HMAC (hmacKey, secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> HMAC (hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> gdzie *x* jest obliczana wynikiem algorytmu Diffie-Hellman WE.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Pochodzi materiału klucza przy użyciu Algorytm wyprowadzania pseudolosową — funkcja (PRF) protokołu TLS.|

 **Obsługa szyfrowania symetrycznego klucza trwały**

 Biblioteka kryptografii Windows (CNG) dodano obsługę do przechowywania kluczy symetrycznych utrwalonych i przy użyciu kluczy symetrycznych przechowywane sprzętu i [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] mades możliwe dla deweloperów skorzystać z tej funkcji.  Ponieważ pojęcie nazw kluczy i kluczy dostawcy jest specyficzne dla implementacji, za pomocą tej funkcji wymaga przy użyciu konstruktora typy konkretną implementację zamiast podejście preferowanych fabryki (np. wywołanie `Aes.Create`).

 Obsługa szyfrowania symetrycznego klucza utrwalone istnieje AES (<xref:System.Security.Cryptography.AesCng>) i algorytmu 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algorytmów. Na przykład:

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

 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Dodaje obsługę <xref:System.Security.Cryptography.Xml.SignedXml> klasy dla metody podpis algorytm RSA-SHA256, RSA SHA384 i RSA SHA512 PKCS #1 SHA256, SHA384 i SHA512 odwołania i algorytmami skrótu.

 Stałe identyfikatora URI są narażone na <xref:System.Security.Cryptography.Xml.SignedXml>:

|Pole SignedXml|Stała|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Wszystkie programy, które zostały zarejestrowane niestandardowe <xref:System.Security.Cryptography.SignatureDescription> obsługi do <xref:System.Security.Cryptography.CryptoConfig> Aby dodać obsługę algorytmy te będą nadal działać jak w przeszłości, ale ponieważ istnieją teraz domyślnie platformy, <xref:System.Security.Cryptography.CryptoConfig> rejestracji nie jest już wymagane.

<a name="SQLClient" />

### <a name="sqlclient"></a>SqlClient

 .NET framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) obejmuje następujące nowe funkcje w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:

 **Pula połączeń i limitów czasu z bazami danych Azure SQL**

 Po buforowanie połączeń jest włączona i limit czasu lub inny błąd logowania wystąpi, wyjątek jest buforowana i pamięci podręcznej wyjątek jest generowany na kolejne próba kolejnych 5 sekund do 1 minuty.  Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia puli (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).

 To zachowanie nie jest pożądane, podczas nawiązywania połączenia z baz danych SQL Azure, ponieważ próby nawiązania połączenia może zakończyć się niepowodzeniem z błędami przejściowymi, które zwykle są szybkiego odzyskania. Aby lepiej zoptymalizować proces ponawiania prób połączenia połączenia puli blokowania okres, w którym zachowanie jest usuwany, gdy błąd połączenia z bazami danych SQL Azure.

 Dodawanie nowej `PoolBlockingPeriod` — słowo kluczowe pozwala wybrać okres blokowania najodpowiedniejsza dla twojej aplikacji. Wartości:

`Auto`

Puli połączeń blokuje okres dla aplikacji, który nawiązuje połączenie z bazą danych Azure SQL Database jest wyłączona, a puli połączeń blokuje okres dla aplikacji, która łączy do innego wystąpienia programu SQL Server jest włączona. Jest to wartość domyślna. Jeśli nazwa punktu końcowego serwera zakończy się z dowolnymi z następujących czynności, są one traktowane jako bazy danych SQL Azure:

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

`AlwaysBlock`

Połączenia czasu blokowania puli jest zawsze włączona.

`NeverBlock`

Połączenia czasu blokowania puli jest zawsze wyłączona.

 **Ulepszenia dla Always Encrypted**

 Klient SQL wprowadzono dwa ulepszenia dla funkcji Always Encrypted:

- Aby poprawić wydajność sparametryzowanych zapytań dotyczących kolumny szyfrowanej bazy danych, teraz są buforowane metadane szyfrowania parametrów zapytania. Za pomocą <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> właściwością `true` (czyli wartość domyślna), jeśli tego samego zapytania jest wywoływana wiele razy, klient pobiera parametr metadane z serwera tylko raz.

- Teraz obrazuje wpisy klucza szyfrowania kolumny klucza pamięci podręcznej po upływie czasu możliwość konfigurowania czasu, można ustawić przy użyciu <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> właściwości.

<a name="WCF" />

### <a name="windows-communication-foundation"></a>Windows Communication Foundation
 W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Communication Foundation została rozszerzona w następujących obszarach:

 **Obsługa zabezpieczeń transportu WCF certyfikaty przechowywane przy użyciu CNG**

 Zabezpieczenia transportu usługi WCF obsługuje certyfikaty przechowywane przy użyciu biblioteki kryptografii Windows (CNG). W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ta obsługa jest ograniczona do korzystania z certyfikatów z kluczem publicznym, zawierającej wykładnika nie więcej niż 32 bity długości. Gdy odpowiedniej aplikacji [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ta funkcja jest domyślnie włączone.

 W przypadku aplikacji, których platformą docelową [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i starszych, ale są uruchomione na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], można włączyć tę funkcję, dodając następujący wiersz do [ \<środowiska uruchomieniowego >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części pliku app.config lub web.config plik.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

Ponadto można to zrobić programowo przy użyciu kodu, jak pokazano poniżej:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

 **Lepsza obsługa wielu reguł dopasowania czasu letniego przez klasę klasa DataContractJsonSerializer**

 Klienci mogą użyć ustawienia konfiguracji aplikacji, aby określić, czy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> klasy obsługuje wiele reguł dopasowania dla jednej strefie czasowej. Jest to funkcja opcjonalna. Aby ją włączyć, należy dodać następujące ustawienie do pliku app.config:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Gdy ta funkcja jest włączona, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiektu używa <xref:System.TimeZoneInfo> wpisz zamiast <xref:System.TimeZone> typu do deserializacji danych daty i godziny. <xref:System.TimeZoneInfo> obsługuje wiele reguł dopasowania, dzięki czemu można pracować z danymi historycznymi strefy czasowej;   <xref:System.TimeZone> nie.

Aby uzyskać więcej informacji na temat <xref:System.TimeZoneInfo> struktury i strefy czasowej z ułatwieniami, zobacz [strefy czasowe — omówienie](../../../docs/standard/datetime/time-zone-overview.md).

**Najlepsze dopasowanie NetNamedPipeBinding**

 Usługi WCF zawiera nowe ustawienie aplikacji, które można ustawić na aplikacje klienckie, aby upewnić się, że zawsze łączą się z service nasłuchiwania na identyfikator URI, który najlepiej pasuje do jednej, ich żądanie. To ustawienie aplikacji jest równa `false` (ustawienie domyślne), jest możliwe dla klientów używających <xref:System.ServiceModel.NetNamedPipeBinding> próbuje nawiązać połączenie z usługą nasłuchuje na identyfikator URI, który jest podciągiem żądanego identyfikatora URI.

 Na przykład klient próbuje nawiązać połączenie z usługa nasłuchuje na `net.pipe://localhost/Service1`, lecz nasłuchuje innej usługi na tym komputerze, na którym działa z uprawnieniami administratora na `net.pipe://localhost`. To ustawienie aplikacji jest równa `false`, klient podejmował próbę połączenia z usługą problem. Po ustawieniu ustawienia aplikacji na `true`, klient będzie zawsze łączyć z najlepiej dopasowaną usługi.

> [!NOTE]
> Klienci korzystający z <xref:System.ServiceModel.NetNamedPipeBinding> znaleźć usług w oparciu o adres podstawowy usługi (jeśli istnieje) zamiast adresu pełną punktu końcowego. Aby upewnić się, to ustawienie zawsze działa usługa należy używać unikatowy adres podstawowy.

 Aby włączyć tę zmianę, Dodaj następujące ustawienie aplikacji do pliku App.config lub Web.config aplikacji klienta:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

 **Protokół SSL 3.0 nie jest domyślnym protokołem**

 Korzystając z zabezpieczeń transportu i poświadczeń typu certyfikatu NetTcp, SSL 3.0 nie jest już domyślny protokół używany do negocjowania bezpiecznego połączenia. W większości przypadków należy bez wpływu na istniejące aplikacje, ponieważ protokół TLS 1.0 znajduje się na liście protokół NetTcp. Wszyscy istniejący klienci powinno być możliwe negocjowania połączenia przy użyciu w co najmniej protokół TLS 1.0. Jeśli Ssl3 jest wymagane, użyj jednej z następujących mechanizmów konfiguracji Aby dodać go do listy wynegocjowanym protokołów.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> Właściwości

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> Właściwości

- [ \<Transportu >](../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) części [ \<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) sekcji

- [ \<SslStreamSecurity >](../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) części [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) sekcji

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Presentation Foundation została rozszerzona w następujących obszarach:

 **Sortowanie grup**

 Aplikacja, która używa <xref:System.Windows.Data.CollectionView> obiektu do grupowania danych teraz można jawnie zadeklarować sposób sortowania grupy. Jawne sortowania adresów problem nieintuicyjnych kolejności pojawia się po aplikacji dynamicznie dodaje lub usuwa grupy lub zmianie wartości właściwości elementu zaangażowanych w grupowaniu. Może również zwiększyć wydajność procesu tworzenia grup, przenosząc porównania właściwości grupowania sortowania pełnym zbiorem do sortowania grup.

 Do obsługi sortowania grupy, nowe <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> i <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> właściwości opisują sposób sortowania kolekcji grupy utworzone przez <xref:System.ComponentModel.GroupDescription> obiektu. To jest odpowiednikiem sposób o identycznej nazwie <xref:System.Windows.Data.ListCollectionView> właściwości opisują sposób sortowania elementów danych.

 Dwie nowe właściwości statycznej z <xref:System.Windows.Data.PropertyGroupDescription> klasy <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> i <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, może służyć do najbardziej typowe przypadki.

 Na przykład następujące dane grupy XAML od wieku, sortować grupy wiekowe, w kolejności rosnącej i grupowanie elementów w każdej grupie wiekowej według nazwiska.

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

 **Klawiatura programowa obsługa**

 Elastyczne Obsługa klawiatury umożliwia fokus śledzenie w aplikacjach WPF przez automatyczne wywołanie i odrzucanie nowe klawiatura programowa w systemie Windows 10, po odebraniu wprowadzanie dotykowe przez kontrolkę, która może przyjąć tekstowych danych wejściowych.

 W poprzednich wersjach programu .NET Framework aplikacje WPF nie mogą skorzystać fokus śledzenia bez konieczności wyłączania WPF pióra/obsługi wprowadzania dotykowego gestu.  W wyniku aplikacji WPF, należy wybrać pełnej obsługi wprowadzania dotykowego WPF lub zależą od podwyższenia poziomu myszy Windows.

 **Rozpoznawanie wartości DPI monitora**

 Do obsługi najnowszych rozprzestrzenianie wysokiej rozdzielczości DPI i rozdzielczości DPI hybrydowego środowiska w przypadku aplikacji WPF, platformy WPF w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] umożliwia rozpoznawanie monitora. Zobacz [przewodnik dla deweloperów i przykłady](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) w serwisie GitHub, aby uzyskać więcej informacji na temat włączania aplikacji WPF stać się świadome DPI monitora.

 W poprzednich wersjach programu .NET Framework aplikacje WPF to system-DPI. Innymi słowy interfejs użytkownika aplikacji jest skalowana przez system operacyjny, zgodnie z potrzebami, w zależności od wartości DPI monitora, na którym aplikacja jest renderowany. ,

 Dla aplikacji działających w ramach [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], rozpoznawanie wartości DPI monitora zmian w aplikacjach WPF można wyłączyć przez dodanie instrukcji konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji konfiguracji aplikacji, plików w następujący sposób:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a>Program Windows Workflow Foundation (WF)
 W [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Workflow Foundation została rozszerzona w następującym obszarze:

 **Obsługa wyrażeń języka C# i technologii IntelliSense w Projektancie WF Re-hosted**

 Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], WF obsługuje wyrażeń języka C# w obu projektanta programu Visual Studio i przepływy pracy kodu. Re-hosted projektanta przepływu pracy jest kluczowym elementem WF umożliwiający projektanta przepływów pracy w aplikacji poza programem Visual Studio (na przykład w WPF).  Windows Workflow Foundation udostępnia możliwość obsługi wyrażeń języka C# i technologii IntelliSense w Projektancie przepływu pracy Re-hosted. Aby uzyskać więcej informacji, zobacz [blogu Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).

 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` W wersjach programu .NET Framework w wersjach wcześniejszych niż [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], funkcja IntelliSense programu WF projektanta został przerwany, gdy klient ponownie kompiluje projekt przepływu pracy w programie Visual Studio. Gdy kompilacja projektu zakończy się pomyślnie, typy przepływów pracy nie znajdują się w Projektancie i ostrzeżenia z technologii IntelliSense dla brakujących typy przepływów pracy są wyświetlane w **lista błędów** okna. [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Rozwiązuje ten problem i sprawia, że funkcja IntelliSense niedostępne.

 **Aplikacje V1 przepływu pracy śledzenia przepływu pracy na teraz być uruchamiane w trybie FIPS**

 Maszyny z włączonym trybem zgodności ze standardem FIPS można teraz pomyślnie uruchomić przepływ pracy w wersji 1 stylu aplikacji za pomocą przepływu pracy śledzenia na. Aby realizacji tego scenariusza, należy wprowadzić następującą zmianę do pliku app.config:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

 Jeśli w tym scenariuszu nie jest włączona, uruchamianie aplikacji w dalszym ciągu wygeneruje wyjątek z komunikatem "Ta implementacja nie jest częścią systemu Windows Platform FIPS zatwierdzone algorytmy kryptograficzne."

 **Ulepszenia przepływu pracy podczas używania aktualizacji dynamicznej z projektanta przepływów pracy w usłudze Visual Studio**

 Projektant przepływu pracy, FlowChart, Projektant działań i innych projektantów działań przepływu pracy teraz pomyślnie ładowanie i wyświetlanie przepływów pracy, które zostały zapisane po wywołaniu <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metody. W wersjach programu .NET Framework przed [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], podczas ładowania pliku XAML w programie Visual Studio dla przepływu pracy, który został zapisany po wywołaniu <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> może spowodować następujące problemy:

- Projektant przepływu pracy nie można poprawnie załadować plik XAML (gdy <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> znajduje się na końcu wiersza).

- Flowchart, Projektant działań lub innych Projektanci działań przepływu pracy mogą być wyświetlane wszystkie obiekty w ich domyślne lokalizacje, w przeciwieństwie do wartości właściwości dołączone.


### <a name="clickonce"></a>ClickOnce

ClickOnce został zaktualizowany do obsługi protokołu TLS 1.1 i TLS 1.2, oprócz protokołu 1.0, która już obsługuje. ClickOnce automatycznie wykrywa, który protokół jest wymagana. żadne dodatkowe czynności w ramach aplikacji ClickOnce są wymagane do włączenia protokołu TLS 1.1 i 1.2 pomocy technicznej.

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Konwertowanie Windows Forms i WPF aplikacji do aplikacji platformy uniwersalnej systemu Windows
 Windows oferuje teraz możliwości, aby przenieść istniejące aplikacje pulpitu Windows, w tym aplikacje WPF i Windows Forms do uniwersalnej platformy Windows (UWP). Ta technologia działa jak most, umożliwiając stopniowo migracji istniejącej bazie kodu do platformy uniwersalnej systemu Windows, a tym samym dostosowanie aplikacji do wszystkich urządzeń z systemem Windows 10.

 Przekonwertowane aplikacje komputerowe uzyskać podobny do aplikacji tożsamości aplikacji platformy uniwersalnej systemu Windows, co sprawia, że interfejsy API platformy uniwersalnej systemu Windows jest dostępny, aby włączyć funkcje, takie jak żywych kafelków i powiadomienia tożsamość aplikacji. Aplikacja będzie nadal działać tak jak poprzednio i działa jako aplikacja pełnego zaufania. Po przekonwertowaniu aplikacji, można dodać do istniejącego procesu pełnego zaufania, aby dodać interfejs użytkownika adaptacyjne procesu kontenera aplikacji. Gdy wszystkie funkcje są przenoszone do procesu kontenera aplikacji, proces pełnego zaufania, można je usunąć i w nowej aplikacji platformy uniwersalnej systemu Windows mogą być udostępniane do wszystkich urządzeń z systemem Windows 10.

<a name="Debug462" />

### <a name="debugging-improvements"></a>Ulepszenia debugowania
 *Niezarządzane debugowanie API* została rozszerzona w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] celu przeprowadzenia dodatkowej analizy po <xref:System.NullReferenceException> jest generowany, aby była możliwość określenia, które zmienna w jednym wierszu kodu źródłowego jest `null`.   Aby zapewnić obsługę tego scenariusza, następujące interfejsy API zostały dodane do niezarządzanego interfejsu API debugowania.

- [ICorDebugCode4](../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md), i [ICorDebugVariableHomeEnum](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interfejsów, które ujawniają natywnych domach zarządzane zmienne. Dzięki temu debugery wykonasz jakieś analizy przepływu kodu podczas <xref:System.NullReferenceException> występuje i przeanalizuj informacje wstecz pochodzące ustalenie zarządzanych zmiennej, która odnosi się do natywnych lokalizacji, który był `null`.

- [ICorDebugType2::GetTypeID](../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metoda zapewnia mapowanie ICorDebugType do [cor_typeid —](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), co pozwala debugera w celu uzyskania [cor_typeid —](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) wystąpienia z ICorDebugType. Istniejących interfejsów API na [cor_typeid —](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) następnie może służyć do określania układu klasy tego typu.

<a name="v461" />

## <a name="whats-new-in-the-net-framework-461"></a>What's new in .NET Framework 4.6.1

[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Zawiera nowe funkcje w następujących obszarach:

- [Kryptografia](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profilowanie](#Profile461)

- [NGen](#NGEN461)

Aby uzyskać więcej informacji na temat [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], zobacz następujące tematy:

- [Platformy .NET Framework 4.6.1 listy zmian](https://go.microsoft.com/fwlink/?LinkId=622964)

- [Zgodność aplikacji w wersji 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

- [.NET Framework API diff](https://go.microsoft.com/fwlink/?LinkId=622989) (w serwisie GitHub)

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Kryptografia: Obsługa X509 certyfikatów zawierających ECDSA
 .NET Framework 4.6 dodanie obsługi RSACng X509 certyfikatów. [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Dodaje obsługę ECDSA (Elliptic krzywej algorytmu Digital Signature Algorithm) X509 certyfikatów.

 ECDSA oferuje lepszą wydajność i jest bardziej bezpieczne algorytmu kryptograficznego, niż RSA, zapewniając doskonałym wyborem, gdzie zabezpieczeń TLS (Transport Layer), wydajności i skalowalności jest istotna. Wdrożenia programu .NET Framework opakowuje wywołania do istniejących funkcji Windows.

 Poniższy przykład kodu pokazuje, jak łatwo jest do generowania podpisu dla strumienia bajtów przy użyciu certyfikatów X 509 uwzględnione w nowej funkcji obsługi ECDSA [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].

 [!code-csharp[whatsnew.461.crypto#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
 [!code-vb[whatsnew.461.crypto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

 Zapewnia to oznaczone kontrastu w kodzie, potrzebne do generowania podpisu w .NET Framework 4.6.

 [!code-csharp[whatsnew.461.crypto#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
 [!code-vb[whatsnew.461.crypto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a>ADO.NET
 Poniżej zostały dodane do zestawu ADO.NET:

**Zawsze zaszyfrowane obsługę sprzętu chronione klucze**

 Platforma ADO.NET teraz obsługuje przechowywania kluczy głównych kolumny Always Encrypted natywnie w sprzętowych modułach zabezpieczeń (HSM). Dzięki temu klienci mogą korzystać z kluczy asymetrycznych przechowywanych w sprzętowych modułach zabezpieczeń bez konieczności pisania dostawców magazynu klucz główny kolumny niestandardowej i rejestrowania ich w aplikacjach.

 Klienci muszą zainstalować dostawcę usług Kryptograficznych udostępnionych przez dostawcę modułu HSM lub dostawcy magazynu kluczy CNG na serwery aplikacji lub komputerów klienckich, aby uzyskiwać dostęp do danych są zawsze szyfrowane, chronione przy użyciu kluczy głównych kolumny przechowywane w module HSM.

 **Ulepszone <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> zachowanie połączenia dla funkcji AlwaysOn**

Klient SQL teraz automatycznie zapewnia szybsze połączenia do grupy dostępności AlwaysOn (AG). Przezroczysty wykryje, czy aplikacja nawiązuje połączenie z zawsze włączonej grupy dostępności (grupy dostępności) w innej podsieci, szybko odnajduje bieżącego aktywnego serwera i zapewnia połączenie z serwerem. We wcześniejszych wersjach, aplikacja nie miała można ustawić parametrów połączenia do uwzględnienia `"MultisubnetFailover=true"` do wskazania, że połączenia do grupy dostępności (AlwaysOn). Bez ustawienia połączenia — słowo kluczowe na `true`, aplikacja może wystąpić limit czasu podczas nawiązywania połączenia zawsze włączonej grupy dostępności. W tej wersji aplikacja wykonuje *nie* należy ustawić <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> do `true` dłużej. Aby uzyskać więcej informacji na temat Obsługa SqlClient dla zawsze włączonych grup dostępności, zobacz [Obsługa SqlClient dla wysokiej dostępności, odzyskiwania po awarii](../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 Windows Presentation Foundation zawiera szereg udoskonaleń i zmian.

 **Lepsza wydajność**

 Opóźnienie w wyzwalanie zdarzeń touch został rozwiązany w [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Ponadto, wpisując <xref:System.Windows.Controls.RichTextBox> kontroli nie blokuje wątku renderowania podczas wprowadzania szybkie.

 **Ulepszenia sprawdzanie pisowni**

 Moduł sprawdzania pisowni w WPF została zaktualizowana na Windows 8.1 i nowsze wersje, aby korzystać z systemu operacyjnego obsługują sprawdzanie pisowni dodatkowych języków.  Nie ma zmian w funkcji z systemem Windows wersjach wcześniejszych niż Windows 8.1.

 Tak jak w poprzednich wersjach programu .NET Framework, w tym języku <xref:System.Windows.Controls.TextBox> kontrolować ora <xref:System.Windows.Controls.RichTextBox> blok zostanie wykryty przez wyszukiwanie informacji w następującej kolejności:

- `xml:lang`, jeśli jest obecny.

- Bieżący język danych wejściowych.

- Bieżąca kultura wątku.

 Aby uzyskać dodatkowe informacje na temat obsługi języków w programie WPF, zobacz [WPF wpis w blogu na temat funkcji programu .NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkID=691819).

 **Dodatkowa obsługa słowników niestandardowych na użytkownika**

 W [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], WPF rozpoznaje słowników niestandardowych, które są zarejestrowane w globalnie. Ta możliwość jest dostępnych dodatkowo oprócz możliwość rejestrowania, je-control.

 W poprzednich wersjach programu WPF słowników niestandardowych nie rozpoznał wykluczone słowa i listy Autokorekty. Są one obsługiwane w Windows 8.1 i Windows 10 przy użyciu plików, które można umieścić w obszarze `%AppData%\Microsoft\Spelling\<language tag>` katalogu.  Następujące reguły stosuje się do tych plików:

- Pliki powinny mają rozszerzenia .dic (w przypadku słowa dodane), .exc (w przypadku wykluczonych słowa) lub .acl (w przypadku Autokorekty).

- Pliki powinny być UTF-16 LE zwykłego tekstu, który rozpoczyna się za pomocą znacznika kolejności bajtów (BOM).

- Każdy wiersz powinien składać się programu word (na listach dodanych i wykluczonych programu word) lub pary Autokorekty słowami oddzielonych pionowy pasek ("&#124;") (na liście Autokorekty programu word).

- Pliki te są traktowane jako tylko do odczytu i nie są modyfikowane przez system.

> [!NOTE]
> Te nowe formaty plików nie są bezpośrednio obsługiwane przez interfejsy API sprawdzania pisowni WPF i słowników niestandardowych dostarczonych w aplikacjach WPF powinna w dalszym ciągu używać .lex plików.

**Przykłady**

 Istnieje kilka przykładów WPF w [WPF-Microsoft-Samples](https://github.com/Microsoft/WPF-Samples) repozytorium GitHub. Pomóż nam udoskonalać nasze przykłady, wysyłając żądania ściągnięcia lub otwierania [problem w usłudze GitHub](https://github.com/Microsoft/WPF-Samples/issues).

 **Rozszerzenia programu DirectX**

 Obejmuje WPF [pakietu NuGet](https://go.microsoft.com/fwlink/?LinkID=691342) zapewniający nowych wdrożeń <xref:System.Windows.Interop.D3DImage> ułatwia dla Ciebie na potrzeby współdziałania z DX10 i Dx11 zawartości. Kod ten pakiet był otwarty źródło i jest dostępny [w serwisie GitHub](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: Transakcje
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> Metoda teraz umożliwia korzystanie z Menedżera transakcji rozproszonych, innym niż MSDTC mógł wypromować transakcji. Można to zrobić, określając identyfikator GUID transakcji promoter do nowego <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> przeciążenia. Jeśli operacja się powiedzie, istnieją ograniczenia nakładane na możliwości transakcji. Gdy promoter transakcji MSDTC nie jest zarejestrowana, następujące metody throw <xref:System.Transactions.TransactionPromotionException> ponieważ te metody wymagają promocji do usługi MSDTC:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

 Gdy promoter transakcji MSDTC nie jest zarejestrowana, należy użyć dla przyszłych trwałych rejestracji przy użyciu protokołów, które definiuje. <xref:System.Guid> Promoter transakcji można uzyskać za pomocą <xref:System.Transactions.Transaction.PromoterType%2A> właściwości. Gdy transakcja promuje, zapewnia promoter transakcji <xref:System.Byte> tablica reprezentująca token o podwyższonym poziomie. Aplikację można uzyskać Podwyższono poziom token dla transakcji innym niż MSDTC promowane z <xref:System.Transactions.Transaction.GetPromotedToken%2A> metody.

 Użytkownicy o nowym <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> przeciążenia wykonaj sekwencję wywołań w kolejności dla operacji podwyższenia poziomu, która powinna zakończyć się powodzeniem. Te reguły są opisane w dokumentacji metody.

<a name="Profile461" />

### <a name="profiling"></a>Profilowanie

Niezarządzany API profilowania zostało ulepszone w następujący sposób:

- Lepsza obsługa uzyskiwania dostępu do baz danych PDB w [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) interfejsu.

   W programie ASP.NET Core on staje się znacznie bardziej powszechny dla kompilacji został skompilowany w pamięci przez Roslyn. Dla deweloperów, dzięki czemu narzędzi do profilowania oznacza to, że pliki PDB, które wcześniej zostały zaszeregowane na dysku może nie być już obecne. Narzędzia Profiler często używają plików PDB do mapowania kodu wierszy źródłowych dla zadań, takich jak analiza wydajności pokrycie lub wiersz po wierszu kodu. [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) interfejs zawiera teraz dwie nowe metody, [ICorProfilerInfo7::GetInMemorySymbolsLength](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) i [ICorProfilerInfo7::ReadInMemorySymbols](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md) , aby zapewnić te narzędzia profiler dostępu do danych PDB w pamięci, przy użyciu nowych interfejsów API, program profilujący może uzyskać zawartość pliku PDB w pamięci w postaci tablicy bajtów a następnie go przetworzyć lub serializować go na dysku.

- Lepsze Instrumentacji z interfejsem ICorProfiler.

   Profilerzy, którzy korzystają z `ICorProfiler` interfejsów API funkcji ReJit Instrumentation dynamicznego można również zmodyfikować niektóre metadane. Wcześniej tych narzędzi można instrumentować IL w dowolnym momencie, ale metadane mogą być modyfikowane tylko w czasie ładowania modułu. IL odwołuje się do metadanych, to ograniczone, ponieważ rodzaje instrumentacji, który może zostać wykonana. Firma Microsoft ma zniesione niektóre z tych ograniczeń, dodając [ICorProfilerInfo7::ApplyMetaData](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) metody w celu obsługi podzbiór zmiany metadanych po moduł ładuje się, w szczególności, dodając nowe `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, i `UserString` rekordów. Ta zmiana umożliwia o wiele szerszy zakres podpowiadania instrumentacji.

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a>Pliki PDB (NGEN) Generator obrazu natywnego
 Śledzenie zdarzeń między komputerami umożliwia klientom profilu programu na komputerze A i przyjrzeć danych profilowania za pomocą mapowania wiersz źródła na maszynę B. przy użyciu poprzednich wersji programu .NET Framework, użytkownik może spowodować skopiowanie wszystkich modułów i obrazy natywne z profilowanych Maszyna do maszyny analizy, która zawiera PDB IL można utworzyć mapowania źródła native. Podczas tego procesu może działać dobrze w przypadku, gdy pliki są stosunkowo mały, takie jak w przypadku aplikacji telefonicznej, pliki mogą bardzo dużych systemach pulpitu i będzie wymagać dużo czasu, aby skopiować.

 Przy użyciu plików PDB Ngen NGen można utworzyć pliku PDB, który zawiera mapowania IL do natywnego bez zależności w pliku PDB IL. W naszym scenariuszu śledzenia zdarzeń między komputerami wszystko, co jest potrzebne jest kopiowanie obrazu natywnego pliku PDB, który jest generowany przez maszyny od A do B maszyny i użyj [debugowanie interfejsów dostępu do interfejsu API](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) odczytać mapowania źródła IL IL PDB i natywnych obraz w pliku PDB IL do macierzystego mapowania. Połączenie obu mapowania zapewnia mapowanie źródła native. Ponieważ obraz natywny plik PDB jest znacznie mniejszy niż wszystkie moduły, a obrazy natywne, proces kopiowania od maszyny, A do B maszyny jest znacznie wyższa.

<a name="v46" />

## <a name="whats-new-in-net-2015"></a>What's new in .NET 2015
 Wprowadza .NET 2015 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] i .NET Core. Niektóre nowe funkcje dotyczą zarówno i inne funkcje są specyficzne dla [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] lub [!INCLUDE[net_core](../../../includes/net-core-md.md)].

- **ASP.NET Core**

     .NET 2015 obejmuje platformy ASP.NET Core, czyli zwarte implementacji .NET do tworzenia nowoczesnych aplikacji w chmurze. ASP.NET Core to moduły, więc może zawierać tylko te funkcje, które są potrzebne w Twojej aplikacji. Mogą być hostowane w usługach IIS lub może być samodzielnie hostowane w procesie niestandardowym. Ponadto możesz uruchamiać aplikacje z użyciem różnych wersji programu .NET Framework, na tym samym serwerze. Zawiera nowy system konfiguracji środowiska, które jest przeznaczone do wdrożenia w chmurze.

     MVC, interfejs API sieci Web i stron sieci Web są jednolite, tworząc jedną strukturę o nazwie technologii MVC 6. Platforma ASP.NET Core możesz tworzyć aplikacje za pomocą narzędzi w programie Visual Studio 2015 lub nowszego. Istniejące aplikacje będą działać na nowe .NET Framework; jednak do tworzenia aplikacji, który używa technologii MVC 6 lub SignalR 3, należy użyć systemu projektu programu Visual Studio 2015 lub nowszego.

     Aby uzyskać informacje, zobacz [platformy ASP.NET Core](/aspnet/core/).

- **ASP.NET Updates**

    - **Odpowiedź asynchroniczna opróżnienie opartego na zadaniach interfejsu API**

         ASP.NET teraz udostępnia prosty interfejs API opartego na zadaniach dla opróżnianie odpowiedź asynchroniczna, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, umożliwiająca odpowiedzi, aby było opróżnić asynchronicznie przy użyciu usługi w języka `async/await` pomocy technicznej.

    - **Wiązanie modelu obsługuje zwracania zadania metody**

         W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ASP.NET dodano funkcję powiązań modelu włączone rozszerzalne, skoncentrowane na kodzie sposobem operacje na danych opartych na podejściu CRUD w stron formularzy sieci Web i kontrolki użytkownika. Obsługuje teraz system wiązania modelu <xref:System.Threading.Tasks.Task>-zwracania metody wiązania modelu. Ta funkcja umożliwia deweloperom formularzy sieci Web przy użyciu nowszych wersji ORMs, łącznie z programu Entity Framework korzystać ze skalowalności zalet async z łatwością systemu powiązanie danych.

         Asynchroniczne wiązanie modelu jest kontrolowana przez `aspnet:EnableAsyncModelBinding` ustawienia konfiguracji.

        ```xml
        <appSettings>
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
        </appSettings>
        ```

         W aplikacji docelowej [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], jego wartość domyślna to `true`. W aplikacje działające na [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] przeznaczone na platformę wcześniejszej wersji programu .NET Framework, jest `false` domyślnie. Można ją włączyć, konfigurując dla ustawienia konfiguracji `true`.

    - **Obsługa protokołu HTTP/2 (system Windows 10)**

         [Protokołu HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) nową wersję protokołu HTTP, która zapewnia znacznie lepsze wykorzystanie połączenia (mniej rund między klientem i serwerem), wynikiem jest niższe opóźnienia strony sieci web podczas ładowania użytkowników.  Stron sieci Web (w przeciwieństwie do usługi) korzystają najbardziej z protokołu HTTP/2, ponieważ protokół optymalizuje wiele artefaktów, które są żądane w ramach jednego środowiska. Dodano obsługę protokołu HTTP/2 platformy ASP.NET w programie .NET Framework 4.6. Ponieważ istnieje funkcji sieciowych w wielu warstwach, nowe funkcje były wymagane, Windows, usługi IIS i platformę ASP.NET w celu włączenia protokołu HTTP/2. Musi działać w systemie Windows 10 za pomocą protokołu HTTP/2 platformy ASP.NET.

         Protokołu HTTP/2 jest również obsługiwana i domyślnie włączone dla systemu Windows 10 Universal Windows Platform systemu Windows (UWP) aplikacje, które używają <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> interfejsu API.

         Aby zapewnić sposób używania [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) funkcji w aplikacjach ASP.NET, nową metodę o dwa przeciążenia <xref:System.Web.HttpResponse.PushPromise%28System.String%29> i <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, została dodana do <xref:System.Web.HttpResponse> klasy.

        > [!NOTE]
        > Platforma ASP.NET Core obsługuje protokołu HTTP/2, pomoc techniczna dla funkcji WYPYCHANIA PROMISE nie został jeszcze dodany.

         Przeglądarki i serwera sieci web (IIS na Windows) wykonanie całąj pracy. Nie trzeba wykonać żadnych przenosząc obciążenie dla użytkowników.

         Większość [główne przeglądarki obsługują protokołu HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), więc istnieje prawdopodobieństwo, że użytkownicy będą mogli korzystać z obsługi protokołu HTTP/2, jeśli serwer obsługuje tę funkcję.

    - **Obsługa protokołu tworzenia powiązań tokenu**

         Firmy Microsoft i firmą Google zostały współpracę w na nowe podejście do uwierzytelniania, o nazwie [Token powiązania protokołu](https://github.com/TokenBinding/Internet-Drafts). Założeniu jest tokeny uwierzytelniania (w pamięci podręcznej przeglądarki) może być kradzieży i używane przez przestępców uzyskują dostęp do bezpiecznego zasobów (np. konta bankowego) bez konieczności hasła lub innych uprzywilejowanych wiedzy. Nowy protokół ma na celu rozwiązania problemu.

         Token powiązania protokołu zostaną zaimplementowane w systemie Windows 10 jako funkcji przeglądarki. Aplikacje platformy ASP.NET będzie uczestniczyć w protokole tak, aby tokeny uwierzytelniania są weryfikowane jako uprawnionych. Klient i implementacji serwera należy ustanowić ochrony end-to-end, określona przez protokół.

    - **Algorytmy wyznaczania wartości skrótu losowego ciągu**

         .NET Framework 4.5, wprowadzono [algorytmu wyznaczania wartości skrótu losowego ciągu](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Jednak go nie jest obsługiwana przez platformę ASP.NET z powodu niektóre platformy ASP.NET funkcje zależne od stabilna wartość skrótu. W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], losowy ciąg algorytmy wyznaczania wartości skrótu są teraz obsługiwane. Aby włączyć tę funkcję, należy użyć `aspnet:UseRandomizedStringHashAlgorithm` ustawienia konfiguracji.

        ```xml
        <appSettings>
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
        </appSettings>
        ```

- **ADO.NET**

     ADO .NET obsługuje teraz funkcję Always Encrypted dostępną w SQL Server 2016 Community Technology Preview 2 (CTP2). Z funkcją Always Encrypted programu SQL Server mogą wykonywać operacje na zaszyfrowane dane, a najlepiej klucza szyfrowania, który znajduje się z aplikacją w zaufanym środowisku klienta, a nie na serwerze. Zawsze zaszyfrowane zabezpiecza dane klienta, więc przetwarzający nie mają dostępu do danych w postaci zwykłego tekstu. Szyfrowanie i odszyfrowywanie danych działa w sposób niewidoczny dla użytkownika na poziomie sterownika, minimalizowanie zmian, które mają do istniejących aplikacji. Aby uzyskać więcej informacji, zobacz [Always Encrypted (aparat bazy danych)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) i [Always Encrypted (Programowanie klienta)](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **64-bitowy kompilator JIT kodu zarządzanego**

     .NET Framework 4.6 obejmuje nową wersję 64-bitowy kompilator JIT (pierwotnie kodu w elementach RyuJIT). Nowy, 64-bitowy kompilator zapewnia znaczne ulepszenia wydajności przez starsze 64-bitowego kompilatora JIT. Nowy, 64-bitowego kompilatora jest włączona dla procesów 64-bitowych, działających na szczycie .NET Framework 4.6. Aplikacja zostanie uruchomiona w procesie 64-bitowym, jeśli jest ona kompilowana jako 64-bitowa lub AnyCPU i jest uruchomiony w 64-bitowym systemie operacyjnym. Gdy starań w celu dokonania przejścia do kompilatora nowe jako przezroczysty, jak to możliwe, możliwe są zmiany w zachowaniu. Chcielibyśmy poznać bezpośrednio o wszelkich problemach, występujące podczas korzystania z nowego kompilatora JIT. Skontaktuj się z nami za pośrednictwem [witryny Microsoft Connect](https://connect.microsoft.com/) Jeśli wystąpi problem, który może być związany z nowego 64-bitowego kompilatora JIT.

     Nowe 64-bitowy kompilator JIT obejmuje również funkcje przyspieszania SIMD sprzętu w połączeniu z włączoną SIMD typów w <xref:System.Numerics> przestrzeni nazw, która umożliwia uzyskanie dobrej wydajności.

- **Ulepszenia programu ładującego zestawy**

     Program ładujący korzysta z pamięci efektywniej dzięki usuwaniu z niej zestawów IL po załadowaniu odpowiadających im obrazów NGEN. Ta zmiana zmniejsza użycie pamięci wirtualnej, co jest szczególnie korzystne w przypadku dużych aplikacji 32-bitowych (takich jak Visual Studio) oraz powoduje mniejsze zużycie pamięci fizycznej.

- **Zmiany w bibliotece klas podstawowych**

     Wiele nowych interfejsów API dodano wokół [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] do obsługi kluczowych scenariuszy. Te obejmują następujące zmienione lub dodane elementy:

    - **IReadOnlyCollection\<T > implementacji**

         Dodatkowe kolekcje implementują <xref:System.Collections.Generic.IReadOnlyCollection%601> takich jak <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601>.

    - **Wartość CultureInfo.CurrentCulture i CultureInfo.CurrentUICulture**

         <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości są teraz odczytu i zapisu, a nie tylko do odczytu. Jeśli przypiszesz nowe <xref:System.Globalization.CultureInfo> obiekt do tych właściwości zdefiniowane przez bieżącą kulturę wątku `Thread.CurrentThread.CurrentCulture` właściwość i Interfejsie użytkownika bieżącego wątku kultury zdefiniowane przez `Thread.CurrentThread.CurrentUICulture` również zmienić właściwości.

    - **Ulepszenia wyrzucania elementów bezużytecznych (GC)**

         <xref:System.GC> Klasy zawiera teraz <xref:System.GC.TryStartNoGCRegion%2A> i <xref:System.GC.EndNoGCRegion%2A> metody, które umożliwiają nie zezwalaj na odzyskiwanie pamięci podczas wykonywania ścieżkę krytyczną.

         Też nowym przeciążeniem <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metoda umożliwia kontrolowanie czy stosu małych obiektów i stos dużych obiektów są wycierana i kompaktowana tylko wycierana.

    - **Typy z obsługą SIMD**

         <xref:System.Numerics> Przestrzeni nazw teraz obejmuje wiele typów włączone SIMD, takie jak <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, i <xref:System.Numerics.Vector4>.

         Nowe 64-bitowy kompilator JIT zawiera również funkcje przyspieszania SIMD sprzętu, dlatego są szczególnie znaczne ulepszenia wydajności w przypadku korzystania z obsługą SIMD typów z nowe 64-bitowego kompilatora JIT.

    - **Aktualizacje kryptografii**

         <xref:System.Security.Cryptography?displayProperty=nameWithType> Interfejsu API jest aktualizowana w celu obsługi [interfejsu API kryptografii Windows CNG](/windows/desktop/SecCNG/cng-reference). Poprzednie wersje programu .NET Framework mają opiera się wyłącznie na [starszą wersję Windows API kryptografii](/windows/desktop/SecCrypto/cryptography-portal) jako podstawa <xref:System.Security.Cryptography?displayProperty=nameWithType> implementacji. Mieliśmy żądania w celu obsługi interfejsu API CNG, ponieważ obsługuje on [algorytmy kryptograficzne nowoczesnych](/windows/desktop/SecCNG/cng-features#suite-b-support), które są ważne w przypadku niektórych rodzajów aplikacji.

         .NET Framework 4.6 obejmuje następujące nowe ulepszenia do obsługi interfejsu API kryptografii Windows CNG:

        - Zestaw metod rozszerzenia X509 certyfikaty, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` i `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, które zwracają implementacji opartej na CNG, a nie na podstawie CAPI wykonania, gdy jest to możliwe. (Niektóre kart inteligentnych itp., nadal wymaga CAPI i interfejsy API obsługi plan awaryjny).

        - <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> Klasy, która dostarcza implementację CNG algorytmu RSA.

        - Ulepszenia interfejsu API RSA tak, aby typowe akcje nie wymagają już rzutowania. Na przykład szyfrowania danych przy użyciu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> obiektu wymaga kodu, podobnie do poniższego w poprzednich wersjach programu .NET Framework.

             [!code-csharp[WhatsNew.Casting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
             [!code-vb[WhatsNew.Casting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

             Kod, który używa nowego interfejsu API kryptografii w programie .NET Framework 4.6 zostać przepisane w następujący sposób, aby uniknąć rzutowania.

             [!code-csharp[WhatsNew.Casting#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
             [!code-vb[WhatsNew.Casting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

    - **Obsługa dla konwertowania daty i godziny do lub z typu time systemu Unix**

         Dodano następujące nowe metody <xref:System.DateTimeOffset> struktury obsługi konwersji wartości daty i godziny do lub z typu time systemu Unix:

        - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - **Przełączników zgodności**

         Nowy <xref:System.AppContext> klasa dodaje nową funkcję zgodności, która umożliwia autorów biblioteki, aby zapewnić jednolity mechanizm rezygnacji nowe funkcje dla swoich użytkowników. Definiuje on kontrakt luźno powiązane między składnikami w celu komunikowania się z rezygnacji z żądaniem. Ta możliwość jest zwykle ważne w przypadku zmian istniejących funkcji. Z drugiej strony już istnieje niejawna uczestnictwa w nowych funkcji.

         Za pomocą <xref:System.AppContext>, zdefiniuj bibliotek i przełączników zgodności udostępniają, podczas kod, który zależy od nich można ustawić te przełączniki mają wpływ na zachowanie biblioteki. Domyślnie biblioteki udostępnia nowe funkcje i zmieniają tylko (czyli zapewniają poprzednie funkcjonalności) Jeśli przełącznik jest ustawiony.

         Aplikacja (lub biblioteki), można zadeklarować wartość przełącznika (który jest zawsze <xref:System.Boolean> wartość) definiujący zależne biblioteki. Przełącznik jest zawsze niejawnie `false`. Ustawienie przełącznika `true` włączy ją. Jawne ustawianie przełącznika `false` udostępnia nowe zachowanie.

        ```csharp
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
        ```

         Biblioteka musisz sprawdzić, jeśli użytkownik został zadeklarowany wartość przełącznika i odpowiednio działają na niej.

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

         Korzystne jest, na użytek jednolitym formacie przełączników, ponieważ są one formalnego kontraktu udostępnianych przez bibliotekę. Poniżej przedstawiono dwa formaty oczywiste.

        - *Przełącznik*. *przestrzeń nazw*. *switchName*

        - *Przełącznik*. *Biblioteka*. *switchName*

    - **Zmiany opartego na zadaniach asynchronicznej wzorzec zadaniach (TAP)**

         W przypadku aplikacji, których platformą docelową [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiekty dziedziczą kultury i kultury interfejsu użytkownika wywołującego wątku. Działanie aplikacji, przeznaczone na platformę poprzednie wersje programu .NET Framework lub których nie docelowe określoną wersję programu .NET Framework jest nienaruszona. Aby uzyskać więcej informacji, zobacz sekcję "Kultury i opartego na zadaniach asynchronicznej operacji" <xref:System.Globalization.CultureInfo> temat poświęcony klasie.

         <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> Klasa służy do reprezentowania danych otoczenia, które jest lokalne przepływu daną kontrolkę asynchronicznych, takich jak `async` metody. Może służyć do utrwalenia danych w wątkach. Można również definiować metody wywołania zwrotnego, która jest powiadamiany o zmianie otoczenia danych albo ponieważ <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> jawnie można zmienić właściwości, lub ponieważ przejście kontekst wątku.

         Jako udogodnienie do trzech <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, zostały dodane do opartego na zadaniach asynchronicznej wzorca (TAP) do zwrócenia zadań wykonanych w określonym stanie.

         <xref:System.IO.Pipes.NamedPipeClientStream> Klasy obsługuje teraz komunikacji asynchronicznej za pomocą swojego nowego <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>. Metoda.

    - **EventSource obsługuje teraz zapisu w dzienniku zdarzeń**

         Możesz teraz użyć <xref:System.Diagnostics.Tracing.EventSource> klasy operacyjnych lub administracyjnych w dzienniku komunikaty w dzienniku zdarzeń, oprócz innych istniejących sesji ETW utworzonych na komputerze. W przeszłości trzeba było używać pakietu Microsoft.Diagnostics.Tracing.EventSource NuGet dla tej funkcji. Ta funkcja jest teraz wbudowana w program .NET Framework 4.6.

         Pakiet NuGet i .NET Framework 4.6 zostały zaktualizowane dzięki następującym funkcjom:

        - **Zdarzenia dynamiczne**

             Umożliwia zdefiniowane "w locie" bez metody zdarzeń tworzenia zdarzenia.

        - **Rozbudowane ładunków**

             Umożliwia specjalnie opartego na atrybutach klas i tablic, a także typy pierwotne, które zostaną przekazane jako ładunek

        - **Śledzenie działań**

             Powoduje, że rozpoczęcie i zakończenie zdarzenia tagu między nimi identyfikatorem, który reprezentuje wszystkie aktualnie aktywne działania.

         Do obsługi tych funkcji, przeciążone <xref:System.Diagnostics.Tracing.EventSource.Write%2A> metoda została dodana do <xref:System.Diagnostics.Tracing.EventSource> klasy.

- **Windows Presentation Foundation (WPF)**

    - **Ulepszenia HDPI**

         HDPI na platformie WPF jest teraz lepsza w [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Wprowadzono zmiany do układu zaokrąglania do zmniejszenia wystąpienia wycinka w kontrolkach z obramowaniem. Domyślnie ta funkcja jest włączona tylko wtedy, gdy Twoje <xref:System.Runtime.Versioning.TargetFrameworkAttribute> jest ustawiona na .NET 4.6.  Aplikacje, których docelową platformą są wcześniejsze wersje Framework, ale są uruchomione na [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] zgodzić się na nowe zachowanie, dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku app.config:

        ```xml
        <AppContextSwitchOverrides
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
        />
        ```

         Bez regionów poza blacked teraz renderowanych całkowicie windows WPF międzystrefowymi wielu monitorów z różnymi ustawieniami DPI (rozdzielczości, obsługa wielu konfiguracji). Można zrezygnować z tego zachowania, dodając następujący wiersz do `<appSettings>` sekcji w pliku app.config, aby wyłączyć to nowe zachowanie:

        ```xml
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>
        ```

         Obsługa automatycznego ładowania na podstawie ustawienia DPI kursor w prawo została dodana do <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.

    - **Touch jest lepsza**

         Odbiorcy raportów o [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) touch, tworzy nieprzewidywalne zachowanie zostały rozwiązane w [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Naciśnij dwukrotnie próg dla aplikacji Windows Store i aplikacji WPF teraz jest taka sama w Windows 8.1 lub nowszym.

    - **Przezroczysty podrzędne okna obsługi**

         Platformy WPF w [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] obsługuje okien podrzędnych przezroczyste w Windows 8.1 i nowszych. Pozwala na tworzenie okien podrzędnych-prostokątny i przejrzystości w najwyższego poziomu z systemem windows. Możesz włączyć tę funkcję, ustawiając <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> właściwość `true`.

- **Windows Communication Foundation (WCF)**

    - **Obsługa protokołu SSL**

         Usługi WCF teraz obsługuje protokół SSL w wersjach TLS 1.1 i TLS 1.2, oprócz protokołu SSL 3.0 i TLS 1.0, gdy NetTcp przy użyciu transportu zabezpieczeń i uwierzytelniania klientów. Jest teraz można wybrać protokół do użycia lub wyłącz stary mniejsze bezpieczne protokoły. Można to zrobić przez ustawienie <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> właściwości lub przez dodanie poniższego pliku konfiguracji.

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

    - **Wysyłanie wiadomości przy użyciu różnych połączeń HTTP**

         WCF umożliwia teraz użytkownikom upewnij się, że niektóre komunikaty są wysyłane przy użyciu różnych podstawowych połączeń HTTP. Istnieją dwa sposoby wykonania tej czynności:

        - **Przy użyciu prefiksu nazwy grupy połączenia**

             Użytkownicy mogą określić ciąg, który WCF będzie używany jako prefiksu nazwy grupy połączeń. Dwa komunikaty z różnymi prefiksami są wysyłane przy użyciu różnych podstawowych połączeń HTTP. Ustaw prefiks poprzez dodanie pary klucz/wartość na komunikat <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> właściwości. The key is "HttpTransportConnectionGroupNamePrefix"; the value is the desired prefix.

        - **Przy użyciu fabryk różnych kanałów**

             Użytkowników można również włączyć funkcję, która gwarantuje, że komunikaty wysyłane za pomocą kanałów utworzonych za pomocą różnych kanałów fabryk będzie używał innego podstawowego połączenia HTTP. Aby włączyć tę funkcję, użytkownicy muszą ustawić następujące `appSetting` do `true`:

            ```xml
            <appSettings>
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
            </appSettings>
            ```

- **Windows Workflow Foundation (WWF)**

     Można teraz określić liczbę sekund, przez które usługi przepływu pracy będą przechowywane na żądanie operacji poza kolejnością, gdy istnieje oczekujące zakładki "bez protokołu" limit żądania. Zakładka "bez protokołu" jest zakładki, która nie jest powiązana z oczekujących działań Receive. Niektóre działania Utwórz-protocol zakładki w ramach ich implementacji, dlatego nie może być oczywiste, że istnieje zakładki-protocol. Obejmują one stan i pobrania. Więc jeśli masz implementowane za pomocą automatu stanów przepływu pracy usługi lub zawierające działania Pick, dowiesz się, najprawdopodobniej z zakładki-protocol. Określ interwał, dodając wiersz, takie jak następujące polecenie, aby `appSettings` sekcji w pliku app.config:

    ```xml
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
    ```

     Wartość domyślna to 60 sekund. Jeśli `value` jest ustawiona na 0, poza kolejnością żądania są natychmiast odrzucane z błędów z tekstem, który wygląda w następujący sposób:

    ```
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
    ```

     Jest to ten sam komunikat, który pojawi się odebranie komunikatów poza kolejnością operacji i nie ma żadnych zakładek-protocol.

     Jeśli wartość `FilterResumeTimeoutInSeconds` element jest różna od zera, istnieją-protocol zakładek i interwał limitu czasu wygaśnięcia, kończy się niepowodzeniem z komunikatem limitu czasu.

- **Transakcje**

     Obecnie możesz uwzględniać identyfikator transakcji rozproszonej dla transakcji, która spowodowała wystąpienie wyjątku pochodną <xref:System.Transactions.TransactionException> zostanie wygenerowany. Możesz to zrobić, dodając następujący klucz do `appSettings` sekcji w pliku app.config:

    ```xml
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
    ```

     Wartość domyślna to `false`.

- **Sieć**

    - **Ponowne używanie gniazd**

         Windows 10 zawiera nowy algorytm sieci o wysokiej skalowalności, który ułatwia lepsze wykorzystanie zasobów maszyny poprzez ponowne użycie portów lokalnych dla połączenia wychodzące TCP. .NET Framework 4.6 obsługuje nowy algorytm, umożliwiając aplikacji .NET wykorzystać nowe zachowanie. W poprzednich wersjach systemu Windows było limit sztuczne liczby jednoczesnych połączeń (zazwyczaj 16 384, domyślny rozmiar dynamicznego zakresu portów), które może ograniczać skalowalność usługi, powodując wyczerpanie portów w warunkach obciążenia.

         W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], dodano dwa nowe interfejsy API umożliwiające ponowne użycie portu, który skutecznie usuwa limit 64 KB na temat jednoczesnych połączeń:

        - <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> Wartość wyliczenia.

        - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> Właściwości.

         Domyślnie <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> właściwość `false` chyba że `HWRPortReuseOnSocketBind` wartość `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` klucza rejestru jest ustawiona na 0x1. Aby włączyć port lokalny ponownemu użyciu starych w przypadku połączeń HTTP, ustaw <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> właściwość `true`. Powoduje to, że wszystkie wychodzące połączenia gniazda TCP z <xref:System.Net.Http.HttpClient> i <xref:System.Net.HttpWebRequest> używanie nowych opcji gniazda systemu Windows 10, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), która umożliwia ponowne użycie portu lokalnego.

         Deweloperom pisanie aplikacji tylko do gniazda można określić <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> opcji podczas wywoływania metody takie jak <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> wychodzącego sockets ponowne użycie portów lokalnych podczas tworzenia powiązania.

    - **Obsługa międzynarodowych nazw domen i PunyCode**

         Nowa właściwość <xref:System.Uri.IdnHost%2A>, została dodana do <xref:System.Uri> klasy w celu lepszej obsługi międzynarodowych nazw domen i PunyCode.

- **Zmiany rozmiaru kontrolek Windows Forms.**

     Ta funkcja została rozwinięta w [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] obejmujący <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.ToolStripSplitButton> typów i prostokąt określony przez <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> właściwość używana podczas rysowania <xref:System.Drawing.Design.UITypeEditor> .

     Jest to funkcja opcjonalna. Aby ją włączyć, ustaw `EnableWindowsFormsHighDpiAutoResizing` elementu `true` w pliku konfiguracyjnym (app.config) aplikacji:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Obsługa stron kodowych**

     [!INCLUDE[net_core](../../../includes/net-core-md.md)] przede wszystkim obsługuje kodowania Unicode i domyślnie udostępnia ograniczoną obsługę stron kodowych. Można dodać obsługę stron kodowych dostępnych w programie .NET Framework, ale niedostępną w [!INCLUDE[net_core](../../../includes/net-core-md.md)] , rejestrując stron kodowych za pomocą <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji, zobacz <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

     Aplikacje Windows dla systemu Windows 10, których platformą docelową [!INCLUDE[net_core](../../../includes/net-core-md.md)] i są zapisywane w języku C# lub Visual Basic można korzystać z nowej technologii, która kompiluje aplikacje do kodu natywnego, a nie IL. Wygenerowanie aplikacji jest określony przez szybsze uruchamianie i czasu wykonania. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji z architekturą .NET Native](../../../docs/framework/net-native/index.md). Omówienie programu .NET Native badający jak różni się od NGEN i kompilacja JIT i przebieg oznacza, że w kodzie, zobacz [.NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).

     Twoje aplikacje są kompilowane do kodu macierzystego domyślnie podczas kompilowania ich przy użyciu programu Visual Studio 2015 lub nowszego. Aby uzyskać więcej informacji, zobacz [wprowadzenie do platformy .NET Native](../../../docs/framework/net-native/getting-started-with-net-native.md).

     Aby zapewnić obsługę debugowania aplikacji .NET Native, liczba nowe interfejsy i wyliczenia zostały dodane do niezarządzanego interfejsu API debugowania. Aby uzyskać więcej informacji, zobacz [debugowanie (niezarządzany wykaz interfejsów API)](../../../docs/framework/unmanaged-api/debugging/index.md) tematu.

- **Pakiety .NET Framework typu open-source**

     Pakietów .NET core, takich jak kolekcje niezmienialne [interfejsów API SIMD](https://go.microsoft.com/fwlink/?LinkID=518639), a sieć interfejsów API, takich jak te znajdujące się w <xref:System.Net.Http> przestrzeni nazw są teraz dostępne jako pakiety "open source" na [GitHub](https://github.com/). Aby uzyskać dostęp do kodu, zobacz [CoreFx w serwisie GitHub](https://github.com/dotnet/corefx). Aby uzyskać więcej informacji i sposobu współtworzenia te pakiety, zobacz [platformy .NET Core i Open-Source](../../../docs/framework/get-started/net-core-and-open-source.md), [strony głównej platformy .NET w witrynie GitHub](https://github.com/dotnet/home).

 [Powrót do początku](#introduction)

<a name="v452" />

## <a name="whats-new-in-the-net-framework-452"></a>What's new in .NET Framework 4.5.2

- **Nowe interfejsy API dla aplikacji ASP.NET.** Nowy <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> i <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody pozwalają na sprawdzanie i modyfikowanie nagłówków odpowiedzi i kod stanu, ponieważ odpowiedź jest opróżnianych do aplikacji klienckich. Należy wziąć pod uwagę przy użyciu tych metod zamiast <xref:System.Web.HttpApplication.PreSendRequestHeaders> i <xref:System.Web.HttpApplication.PreSendRequestContent> zdarzeń; są one bardziej wydajny i niezawodny.

     <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> Metoda umożliwia zaplanowanie tła małych elementów roboczych. Program ASP.NET śledzi te elementy i zapobiega nagle przerywa proces roboczy, dopóki nie zostały wykonane wszystkie elementy robocze w tle usług IIS. Nie można wywołać tę metodę poza domeną zarządzaną aplikację ASP.NET.

     Nowy <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> i <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> właściwości zwracają wartości logiczne, które wskazują, czy nagłówki odpowiedzi została zapisana. Umożliwia te właściwości upewnij się, wywołania interfejsów API, takich jak <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (które zgłaszają wyjątki, jeśli napisano nagłówki) zakończy się powodzeniem.

- **Zmiany rozmiaru kontrolek Windows Forms.** Ta funkcja została rozwinięta. Ustawienie DPI systemu umożliwia teraz zmienić rozmiar składniki następujące dodatkowe kontrole (na przykład strzałkę listy rozwijanej w polu kombi):

    - <xref:System.Windows.Forms.ComboBox>
    - <xref:System.Windows.Forms.ToolStripComboBox>
    - <xref:System.Windows.Forms.ToolStripMenuItem>
    - <xref:System.Windows.Forms.Cursor>
    - <xref:System.Windows.Forms.DataGridView>
    - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

     Jest to funkcja opcjonalna. Aby ją włączyć, ustaw `EnableWindowsFormsHighDpiAutoResizing` elementu `true` w pliku konfiguracyjnym (app.config) aplikacji:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Nowa funkcja przepływ pracy.** Usługi resource manager, która używa <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> — metoda (i w związku z tym wdrażanie <xref:System.Transactions.IPromotableSinglePhaseNotification> interfejsu) można użyć nowej <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> metodę, aby zażądać następujące czynności:

    - Wypromować transakcji do transakcji transakcji Koordynator MSDTC (Microsoft Distributed).

    - Zastąp <xref:System.Transactions.IPromotableSinglePhaseNotification> z <xref:System.Transactions.ISinglePhaseNotification>, czyli trwałej rejestracji, który obsługuje zatwierdzania jedna faza.

     Możesz to zrobić w tej samej domenie aplikacji i nie wymaga żadnych dodatkowych niezarządzanego kodu do interakcji z MSDTC przeprowadzić podwyższenia poziomu. Nową metodę można wywołać tylko wtedy, gdy wywołanie oczekujące z <xref:System.Transactions?displayProperty=nameWithType> do <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` metodę, która jest implementowany przez awansowanie rejestracji.

- **Ulepszenia profilowania.** Nowe niezarządzanych profilowania API zapewniają bardziej niezawodne profilowania:

    - [COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura](../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
    - [Wyliczenie COR_PRF_HIGH_MONITOR](../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
    - [GetAssemblyReferences, metoda](../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
    - [GetEventMask2, metoda](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
    - [SetEventMask2, metoda](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
    - [AddAssemblyReference, metoda](../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

     Poprzednie `ICorProfiler` implementacje obsługiwane powolne ładowanie zestawów zależnych. Nowe interfejsy API profilowania wymagają zależnych zestawów, które są wprowadzane przez profiler za obciążana od razu, zamiast ładowany po aplikacji jest w pełni zainicjowany. Ta zmiana nie ma wpływu na istniejących użytkowników `ICorProfiler` interfejsów API.

- **Ulepszenia debugowania.** Następujących nowych niezarządzane debugowanie interfejsów API zapewniają lepszą integrację z profilera. Możesz teraz dostęp do metadanych wstawione przez profiler, a także zmienne lokalne i kod utworzony przez kompilatora ReJIT żądania podczas zrzutu debugowania.

    - [SetWriteableMetadataUpdateMode, metoda](../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
    - [EnumerateLocalVariablesEx, metoda](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
    - [GetLocalVariableEx, metoda](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
    - [GetCodeEx, metoda](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
    - [GetActiveReJitRequestILCode, metoda](../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
    - [GetInstrumentedILMap, metoda](../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Zdarzenia śledzenia zmian.** .NET Framework 4.5.2 umożliwia śledzenie aktywności poza procesem, oparte na śledzenie zdarzeń dla Windows ETW większy obszar powierzchni. Umożliwia to dostawcom zaawansowanego zarządzania energią (APM) udostępniają uproszczone narzędzia, które dokładnie śledzić koszty poszczególnych żądań i działań, które przecinają wątków.  Te zdarzenia są wywoływane tylko wtedy, gdy kontrolery ETW umożliwiały; w związku z tym zmiany nie wpływają na poprzednio wpisaną ETW kod lub kod, który jest uruchamiany za pomocą funkcji ETW jest wyłączona.

- **Podwyższanie poziomu transakcji i konwertowanie go na trwałej rejestracji**

     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> Nowy interfejs API dodaje się do programu .NET Framework 4.5.2 i 4.6:

    ```csharp
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                              IPromotableSinglePhaseNotification promotableNotification,
                                              ISinglePhaseNotification enlistmentNotification,
                                              EnlistmentOptions enlistmentOptions)
    ```

     Metoda może być używany przez rejestracji, który został wcześniej utworzony przez <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> w odpowiedzi na <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> metody. Sprawdza, czy `System.Transactions` mógł wypromować transakcji do transakcji MSDTC i na "konwersję" awansowanie rejestracji trwałej rejestracji. Po pomyślnym ukończeniu działania tej metody <xref:System.Transactions.IPromotableSinglePhaseNotification> interfejsu nie jest już się odwołuje `System.Transactions`, oraz wszelkich kolejnych powiadomień zostanie wyświetlony na podany <xref:System.Transactions.ISinglePhaseNotification> interfejsu. Funkcja rejestracji danego musi działać jako trwałej rejestracji, obsługując rejestrowanie transakcji i odzyskiwania. Zapoznaj się <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> Aby uzyskać szczegółowe informacje. Ponadto rejestracji musi obsługiwać <xref:System.Transactions.ISinglePhaseNotification>.  Ta metoda może *tylko* można wywołać podczas przetwarzania <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> wywołania. Jeśli tak nie jest <xref:System.Transactions.TransactionException> wyjątku.

 [Powrót do początku](#introduction)

<a name="v451" />

## <a name="whats-new-in-the-net-framework-451"></a>What's new in .NET Framework 4.5.1
 **Aktualizuje kwietnia 2014**:

- [Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) obejmuje aktualizacje szablony Portable Class Library do obsługi tych scenariuszy:

    - Za pomocą interfejsów API środowiska wykonawczego Windows w przenośnych bibliotek, których platformą docelową, Windows 8.1, Windows Phone 8.1 i Windows Phone Silverlight 8.1.

    - XAML (typy Windows.UI.XAML) można uwzględnić w przenośnych bibliotek, gdy miejscem docelowym, Windows 8.1 lub Windows Phone 8.1. Obsługiwane są następujące szablony XAML:  Pusta strona, słownika zasobów, formant z szablonem i kontrolki użytkownika.

    - Przenośne składnika wykonawczego Windows (plik winmd) można utworzyć do użycia w aplikacjach Store, przeznaczonych dla Windows 8.1 i Windows Phone 8.1.

    - Można przekierować bibliotekę klas Windows Store lub Windows Phone Store, takich jak biblioteki klas przenośnych.

     Aby uzyskać więcej informacji o tych zmianach, zobacz [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Teraz zestawu zawartości w programie .NET Framework zawiera dokumentację dotyczącą [!INCLUDE[net_native](../../../includes/net-native-md.md)], który jest technologia kompilacji wstępnej do kompilowania i wdrażania aplikacji Windows. [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompiluje swoich aplikacji bezpośrednio do kodu natywnego, a nie do języka pośredniego (IL), aby uzyskać lepszą wydajność. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji z architekturą .NET Native](../../../docs/framework/net-native/index.md).

- [Źródła programu .NET Framework odwołanie](https://referencesource.microsoft.com/) udostępnia nowe funkcje przeglądania i ulepszone funkcje. Teraz możesz przejść do kodu źródłowego .NET Framework do trybu online, [Pobierz odwołania](https://referencesource.microsoft.com/download.html) przeglądania w trybie offline i krok po kroku źródła (w tym poprawki i aktualizacje) podczas debugowania. Aby uzyskać więcej informacji, zobacz wpis na blogu [nowy wygląd na potrzeby źródło odwołania .NET](https://blogs.msdn.microsoft.com/dotnet/2014/02/24/a-new-look-for-net-reference-source/).

 Najważniejsze nowe funkcje i ulepszenia w programie .NET Framework 4.5.1 obejmują:

- Automatyczne przekierowywanie powiązań zestawów. Począwszy od programu Visual Studio 2013, gdy kompilujesz aplikację, który jest przeznaczony dla [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], przekierowania powiązań mogą być dodawane do pliku konfiguracji aplikacji Jeśli Twoja aplikacja lub jej składniki odwołują się do wielu wersji tego samego zestawu. Można również włączyć tę funkcję dla projektów przeznaczonych dla starszych wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznego przekierowywania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Możliwość zbierania informacji diagnostycznych, aby pomóc deweloperom ulepszyć wydajność aplikacji serwera i chmury. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> i <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> metody <xref:System.Diagnostics.Tracing.EventSource> klasy.

- Zdolność do jawnego kompaktowania sterty dużych obiektów (LOH) podczas wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwości.

- Dodatkowe ulepszenia wydajności, takie jak zawieszenie aplikacji ASP.NET, wielordzeniowe ulepszenia JIT i szybsze uruchamiani aplikacji po .NET Framework aktualizacji. Aby uzyskać więcej informacji, zobacz [ogłoszenie .NET Framework 4.5.1](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/) i [ASP.NET app suspend usprawnia](https://blogs.msdn.microsoft.com/dotnet/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting/) wpis w blogu.

 Ulepszenia do formularzy Windows Forms obejmują:

- Zmiany rozmiaru kontrolek Windows Forms. Umożliwia ustawienie rozdzielczości DPI systemu rozmiar składniki formanty (na przykład, ikony, które są wyświetlane w siatce właściwości), rezygnując się przy użyciu wpisu w pliku konfiguracyjnym aplikacji (app.config) dla aplikacji. Ta funkcja jest obecnie obsługiwane w następujących kontrolkach formularzy Windows:

    - <xref:System.Windows.Forms.PropertyGrid>
    - <xref:System.Windows.Forms.TreeView>
    - Niektóre aspekty <xref:System.Windows.Forms.DataGridView> (zobacz [nowe funkcje w wersji 4.5.2](#v452) dodatkowych formantów obsługiwane)

     Aby włączyć tę funkcję, Dodaj nowy \<appSettings > element pliku konfiguracji (app.config) i ustaw `EnableWindowsFormsHighDpiAutoResizing` elementu `true`:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

 Ulepszenia podczas debugowania aplikacji .NET Framework w programie Visual Studio 2013 obejmują:

- Wartości zwracane w debugerze programu Visual Studio. Podczas debugowania zarządzanej aplikacji w programie Visual Studio 2013, okno Autos Wyświetla typy zwracane i wartości dla metod. Te informacje są dostępne dla pulpitu, Windows Store i aplikacji Windows Phone. Aby uzyskać więcej informacji, zobacz [Sprawdź wartości zwracanych z wywołań metod](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn32325728%v=vs.120%29).

- Edytuj i Kontynuuj dla 64-bitowych aplikacji. Visual Studio 2013 obsługuje funkcje Edytuj i Kontynuuj dla 64-bitowej zarządzanej aplikacji pulpitu, Windows Store i Windows Phone. Istniejące ograniczenia pozostają w mocy zarówno 32-bitowych i 64-bitowych aplikacji (zobacz ostatnią sekcję [obsługiwane zmiany kodu (C#)](/visualstudio/debugger/supported-code-changes-csharp) artykułu).

- Debugowanie Async-aware. Aby ułatwić debugowanie aplikacji asynchronicznych w programie Visual Studio 2013, stos wywołań ukrywa kod infrastruktury dostarczany przez kompilatory do obsługi asynchronicznego programowania, a także tworzy powiązanie logiczne ramek nadrzędnych, dzięki czemu możesz wykonać więcej wykonywania logicznych program wyraźnie. Okno zadań zastępuje okno zadań równoległych i wyświetla zadania, które odnoszą się do określonego punktu przerwania i wyświetla również inne zadania, które są aktualnie aktywne lub zaplanowane w aplikacji. Informacje o tej funkcji w sekcji "debugowanie Async-aware" [ogłoszenie .NET Framework 4.5.1](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/).

- Lepsza obsługa wyjątków dla składników środowiska wykonawczego Windows. W [!INCLUDE[win81](../../../includes/win81-md.md)], wyjątki z aplikacji Windows Store zapisują informacje o błędzie, który spowodował wyjątek, nawet w granicach języka. Informacje o tej funkcji w sekcji "Tworzenie aplikacji Windows Store" [ogłoszenie .NET Framework 4.5.1](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/).

 Począwszy od programu Visual Studio 2013, można użyć [z przewodnikiem narzędzia optymalizacji zarządzanym profilem (Mpgo.exe)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md) zoptymalizować [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, jak również aplikacje klasycznych.

 Aby uzyskać nowe funkcje w programie ASP.NET 4.5.1, zobacz [ASP.NET and Web Tools dla programu Visual Studio 2013 Release Notes](/aspnet/visual-studio/overview/2013/release-notes).

 [Powrót do początku](#introduction)

<a name="v45" />

## <a name="whats-new-in-the-net-framework-45"></a>What's new in .NET Framework 4.5

### <a name="core-new-features-and-improvements"></a>Najważniejsze nowe funkcje i ulepszenia

- Możliwość ograniczenia system zostanie uruchomiony ponownie przez wykrywanie i zamykanie aplikacji .NET Framework 4 podczas wdrażania. Zobacz [zmniejszenie liczby System ponownych uruchomień podczas instalowania programu .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md).

- Wsparcie dla tablic, które są większe niż 2 gigabajty (GB) na platformach 64-bitowych. Tę funkcję można włączyć w pliku konfiguracyjnym aplikacji. Zobacz [ \<gcAllowVeryLargeObjects > element](../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), która zawiera również inne ograniczenia dotyczące obiektu i rozmiaru tablicy.

- Lepszą wydajność dzięki bezużytecznych w tle dla serwerów. Kiedy używasz wyrzucanie elementów bezużytecznych serwera w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wyrzucanie elementów bezużytecznych w tle jest włączane automatycznie. W sekcji tła serwer wyrzucania elementów bezużytecznych [podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/fundamentals.md) tematu.

- Kompilacja just-in-time (JIT) tła, która jest opcjonalnie dostępna na wielordzeniowych procesorach, aby zwiększyć wydajność aplikacji. Zobacz <xref:System.Runtime.ProfileOptimization>.

- Możliwość ograniczenia, jak długo silnik wyrażeń regularnych będzie próbował rozpoznać wyrażenie regularne, zanim upłynie limit czasu. Zobacz <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> właściwości.

- Możliwość definiowania domyślnej kultury domeny aplikacji. Zobacz <xref:System.Globalization.CultureInfo> klasy.

- Obsługa konsoli kodowania Unicode (UTF-16). Zobacz <xref:System.Console> klasy.

- Obsługa wersjonowania kolejności ciągów kultury i porównania danych. Zobacz <xref:System.Globalization.SortVersion> klasy.

- Lepsza wydajność podczas pobierania zasobów. Zobacz [opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Ulepszenia kompresji ZIP mające zmniejszenie rozmiaru skompresowanego pliku. Zobacz <xref:System.IO.Compression?displayProperty=nameWithType> przestrzeni nazw.

- Możliwość dostosowywania kontekstu odbicia, aby zastąpić domyślne zachowanie odbicia poprzez <xref:System.Reflection.Context.CustomReflectionContext> klasy.

- Obsługa międzynarodowych nazw domen aplikacji (IDNA) w wersji 2008 standard gdy <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> klasa jest używana na [!INCLUDE[win8](../../../includes/win8-md.md)].

- Delegowanie porównywania ciągów do systemu operacyjnego, który implementuje zestaw znaków Unicode 6.0, stosowania programu .NET Framework na [!INCLUDE[win8](../../../includes/win8-md.md)]. Podczas uruchamiania na innych platformach, program .NET Framework zawiera swoje własne dane porównania ciągu, która implementuje Unicode 5.x. Zobacz <xref:System.String> klasy oraz sekcję Uwagi <xref:System.Globalization.SortVersion> klasy.

- Możliwość obliczenia kodów skrótów dla ciągów na podstawie domeny aplikacji. Zobacz [ \<userandomizedstringhashalgorithm — > Element](../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Wsparcie typu reflection podzielone między <xref:System.Type> i <xref:System.Reflection.TypeInfo> klasy. Zobacz [odbicia w .NET Framework dla aplikacji Windows Store](../../../docs/framework/reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Managed Extensibility Framework (MEF) udostępnia następujące nowe funkcje:

- Obsługa typów ogólnych.

- Oparty na Konwencji model programowania, która umożliwia tworzenie części opartych na konwencji nazewnictwa zamiast atrybutów.

- Wiele zakresów.

- Podzbiór środowiska MEF, którego można używać podczas tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Ten podzbiór jest dostępny jako [pakiet do pobrania](https://go.microsoft.com/fwlink/?LinkId=256238) w galerii NuGet. Aby zainstalować pakiet, otwórz projekt w programie Visual Studio, wybierz polecenie **Zarządzaj pakietami NuGet** z **projektu** menu, a następnie wyszukaj w trybie online `Microsoft.Composition` pakietu.

 Aby uzyskać więcej informacji, zobacz [Managed Extensibility Framework (MEF)](../../../docs/framework/mef/index.md).

### <a name="asynchronous-file-operations"></a>Asynchroniczne operacje na plikach
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], nowe funkcje asynchroniczne zostały dodane do języków C# i Visual Basic. Te funkcje Dodawanie modelu opartego na zadaniach do wykonywania operacji asynchronicznych. Aby użyć tego nowego modelu, należy użyć metody asynchronicznej klas we/wy. Zobacz [asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md).

<a name="tools" />

### <a name="tools"></a>Narzędzia
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Generator plików zasobów (Resgen.exe) umożliwia utworzenie pliku .resw do użytku w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji z pliku Resources osadzonego w zestawie programu .NET Framework. Aby uzyskać więcej informacji, zobacz [Resgen.exe (Generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

 Zarządzane profilowana Optymalizacja (Mpgo.exe) pozwala na poprawę czas uruchamiania aplikacji, wykorzystanie pamięci (rozmiar zestawu roboczego) i przepustowości poprzez optymalizację zestawów obrazu natywnego. Narzędzie wiersza polecenia generuje dane profilów dla zestawów natywnych obrazów aplikacji. Zobacz [Mpgo.exe (narzędzie optymalizacji sterowanej zarządzanym profilem)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Począwszy od programu Visual Studio 2013, możesz użyć Mpgo.exe do optymalizacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, jak również aplikacje klasycznych.

<a name="parallel" />

### <a name="parallel-computing"></a>Obliczenia równoległe
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Zawiera kilka nowych funkcji i udoskonaleń do obliczeń równoległych. Obejmują one lepszą wydajność, zwiększoną kontrolę, Ulepszona obsługa programowania asynchronicznego, nową bibliotekę przepływu danych i lepszą obsługę równoległych analiz debugowania i wydajności. Zobacz wpis [nowości w równoległości obliczeń w .NET 4.5](https://go.microsoft.com/fwlink/?LinkId=235061) w Programowanie równoległe z bloga platformy .NET.

<a name="web" />

### <a name="web"></a>sieć Web

Program ASP.NET 4.5 i 4.5.1 dodaje powiązanie modelu dla formularzy sieci Web, obsługa protokołu WebSocket, obsługę asynchroniczną, ulepszenia wydajności i wiele innych funkcji. Aby uzyskać więcej informacji, zobacz następujące zasoby:

- [ASP.NET 4.5 and Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [Platforma ASP.NET i narzędzia Web Tools dla programu Visual Studio 2013 — informacje o wersji](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking-a-namenetworking-"></a>Sieć <a name="networking" />

[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Oferuje nowy interfejs programowania aplikacji protokołu HTTP. Aby uzyskać więcej informacji, zobacz nową <xref:System.Net.Http?displayProperty=nameWithType> i <xref:System.Net.Http.Headers?displayProperty=nameWithType> przestrzeni nazw.

Obsługa jest również nowy interfejs programowania dla akceptowania i interakcji z połączeniem WebSocket przy użyciu istniejących <xref:System.Net.HttpListener> i pokrewne klasy. Aby uzyskać więcej informacji, zobacz nową <xref:System.Net.WebSockets> przestrzeni nazw i <xref:System.Net.HttpListener> klasy.

Ponadto [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] obejmuje następujące ulepszenia sieciowe:

- Obsługa URI zgodna ze specyfikacją RFC. Aby uzyskać więcej informacji, zobacz <xref:System.Uri> i pokrewne klasy.

- Obsługa analizy Zinternacjonalizowanych nazw domen (IDN). Aby uzyskać więcej informacji, zobacz <xref:System.Uri> i pokrewne klasy.

- Obsługa internacjonalizacji adresów E-mail (EAI). Aby uzyskać więcej informacji, zobacz <xref:System.Net.Mail> przestrzeni nazw.

- Ulepszona obsługa protokołu IPv6. Aby uzyskać więcej informacji, zobacz <xref:System.Net.NetworkInformation> przestrzeni nazw.

- Obsługa podwójnych gniazd. Aby uzyskać więcej informacji, zobacz <xref:System.Net.Sockets.Socket> i <xref:System.Net.Sockets.TcpListener> klasy.

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Windows Presentation Foundation (WPF) zawiera zmiany i udoskonalenia w następujących obszarach:

- Nowy <xref:System.Windows.Controls.Ribbon.Ribbon> formant, który umożliwia implementację interfejsu użytkownika wstążki, który jest hostem kart, Menu aplikacji i paska narzędzi Szybki dostęp.

- Nowy <xref:System.ComponentModel.INotifyDataErrorInfo> interfejs, który obsługuje sprawdzanie poprawności danych synchroniczne i asynchroniczne.

- Nowe funkcje <xref:System.Windows.Controls.VirtualizingPanel> i <xref:System.Windows.Threading.Dispatcher> klasy.

- Zwiększona wydajność podczas wyświetlania dużych ustawia zgrupowanych danych i uzyskując dostęp do kolekcji w wątkach bez interfejsu użytkownika.

- Dane powiązanie z właściwościami statycznymi, wiązanie danych z niestandardowymi typami, które implementują <xref:System.Reflection.ICustomTypeProvider> interfejsu i pobieranie informacji o wiązaniach danych z wyrażenia wiązania.

- Zmiana położenia danych podczas zmiany wartości (kształtowanie na bieżąco).

- Możliwość, sprawdź, czy kontekst danych dla kontenera elementu jest odłączony.

- Możliwość ustawiania ilości czasu, który powinien upłynąć między zmianami właściwość i aktualizacji źródła danych.

- Ulepszona obsługa implementowania wzorców zdarzeń słabych. Ponadto zdarzenia mogą teraz akceptować rozszerzenia znaczników.

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], następujące funkcje zostały dodane do ułatwi zapis i konserwację aplikacji Windows Communication Foundation (WCF):

- Uproszczenie wygenerowanych plików konfiguracyjnych.

- Obsługa programowania z wymogiem wcześniejszego zawarcia kontraktu.

- Możliwość skonfigurowania łatwiej tryb zgodności ASP.NET.

- Zmiany w domyślnych wartości właściwości, aby zmniejszyć prawdopodobieństwo, że trzeba będzie je ustawić transportu.

- Aktualizacje <xref:System.Xml.XmlDictionaryReaderQuotas> klasy, aby zmniejszyć prawdopodobieństwo, że trzeba będzie ręcznie skonfigurować przydziały dla czytelników słownika XML.

- Sprawdzanie poprawności plików konfiguracyjnych WCF przez program Visual Studio jako część procesu kompilacji, dzięki czemu można wykrywać błędy konfiguracji przed uruchomieniem aplikacji.

- Nowe Obsługa asynchronicznego przesyłania strumieniowego.

- Nowe mapowanie protokołu HTTPS, aby ułatwić udostępnianie punktu końcowego za pośrednictwem protokołu HTTPS za pomocą programu Internet Information Services (IIS).

- Możliwość generowania metadanych w pojedynczym dokumencie WSDL przez dołączenie `?singleWSDL` na adres URL usługi.

- Obsługa protokółu Websocket włącza komunikację dwukierunkową przez porty 80 i 443, o charakterystyki wydajności jest podobna do warstwy transportowej TCP.

- Obsługa konfigurowania usług w kodzie.

- Etykietki narzędzi edytora XML.

- <xref:System.ServiceModel.ChannelFactory> Obsługa buforowania.

- Obsługa kompresji kodera binarnego.

- Wsparcie dla transportu UDP, który umożliwia programistom pisanie usług korzystających z "fire and forget" wiadomości. Klient wysyła komunikat do usługi i oczekuje odpowiedzi z usługi.

- Możliwość obsługi wielu trybów uwierzytelniania w jednym punkcie końcowym WCF, gdy za pomocą transportu HTTP i zabezpieczeń transportu.

- Obsługa usług WCF, które używają zinternacjonalizowanych nazw domen (IDN).

 Aby uzyskać więcej informacji, zobacz [What's New in Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=228173).

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a>Program Windows Workflow Foundation (WF)
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kilka nowych funkcji dodanych do Windows Workflow Foundation (WF), w tym:

- Stan przepływów pracy maszyny, które zostały najpierw wprowadzone w ramach programu .NET Framework 4.0.1 ([platformy aktualizacji 1 dla programu .NET Framework 4](https://go.microsoft.com/fwlink/?LinkID=215092)). Ta aktualizacja zawierała kilka nowych klas i działań, które umożliwiły deweloperom tworzenie przepływów pracy automatu stanów. Te klasy i działania zostały zaktualizowane dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do uwzględnienia:

    - Możliwość ustawienia punktów przerwania na stanach.

    - Możliwość kopiowania i wklejania przejść w Projektancie przepływu pracy.

    - Wsparcie tworzenia udostępnionych przejść wyzwalaczy.

    - Działania tworzenia przepływów pracy automatu stanów, w tym: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, i <xref:System.Activities.Statements.Transition>.

- Ulepszone funkcje projektanta przepływów pracy, takich jak następujące:

    - Rozszerzone możliwości wyszukiwania przepływu pracy w programie Visual Studio, w tym **szybkie znajdowanie** i **Znajdź w plikach**.

    - Zdolność do automatycznego tworzenia działania Sequence po dodaniu drugiego działania podrzędnego do działania kontenera oraz umieszczenia obu działań w działaniu Sequence.

    - Wsparcie panoramowania, które umożliwia widocznej części przepływu pracy można zmieniać bez używania pasków przewijania.

    - Nowy **konspekt dokumentu** widok, który pokazuje składniki przepływu pracy w widoku konspektu stylu drzewa i umożliwia wybierz składnik **konspekt dokumentu** widoku.

    - Możliwość dodawania adnotacji do działań.

    - Możliwość definiowania i stosowanie delegowania działania za pomocą projektanta przepływów pracy.

    - Automatyczne łączenie i wstawianie dla działań i przejść w stan maszyny i schematach blokowych przepływów pracy.

- Przechowywanie informacji o stanie widoku dla przepływu pracy w pojedynczym elemencie w pliku XAML, dzięki czemu można łatwo zlokalizować i edytować informacje o stanie widoku.

- Na kontenerze nopersistscope zapobiegające utrwalaniu działania podrzędne.

- Obsługa wyrażeń języka C#:

    - Projekty przepływu pracy, które używają języka Visual Basic będą używać wyrażeń języka Visual Basic, a projekty przepływu pracy w języku C# będzie używać wyrażeń języka C#.

    - Projekty języka C# przepływu pracy utworzone w programie Visual Studio 2010 i mające wyrażenia języka Visual Basic są zgodne z projektów C# przepływu pracy korzystających z wyrażeń języka C#.

- Ulepszenia przechowywania wersji:

    - Nowy <xref:System.Activities.WorkflowIdentity> klasy, która zapewnia mapowanie między istniejącym wystąpieniem przepływu pracy i jej definicją przepływu pracy.

    - Side-by-side wykonywanie wielu wersji przepływu pracy, w tym samym hoście, w tym <xref:System.ServiceModel.Activities.WorkflowServiceHost>.

    - Aktualizacji dynamicznej oferuje możliwość modyfikowania definicji utrwalonego wystąpienia przepływu pracy.

- Wymogiem wcześniejszego zawarcia kontraktu programowanie usługi przepływu pracy, co zapewnia obsługę automatycznego generowania działań pasujących do istniejącej umowy serwisowej.

 Aby uzyskać więcej informacji, zobacz [What's New in Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=228176).

<a name="tailored" />

### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]

[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje są przeznaczone dla określonych czynników formularzy i zwiększają możliwości systemu operacyjnego Windows. Podzbiór [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub 4.5.1 jest dostępny do kompilowania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje dla Windows przy użyciu języka C# lub Visual Basic. Podzbiór ten jest nazywany [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] i został omówiony w [Przegląd](https://go.microsoft.com/fwlink/?LinkId=228491) w Centrum deweloperów Windows.

### <a name="portable-class-libraries-a-nameportable-"></a>Biblioteki klas przenośnych <a name="portable" />

Projekt przenośnej biblioteki klas w programie Visual Studio 2012 (i nowszych wersjach) umożliwia pisanie i kompilowanie zestawów zarządzanych działające na wielu platformach .NET Framework. Korzystając z projektu Portable Class Library, wybierz platformy (np. Windows Phone i [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) do obiektu docelowego. Grupa dostępnych typów i członków projektu jest automatycznie ograniczana do typowych typów i członków na tych platformach. Aby uzyskać więcej informacji, zobacz [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Zobacz także

- [Program .NET Framework i wydania poza harmonogramem (OOB)](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
- [What's new in ułatwień dostępu w programie .NET Framework](whats-new-in-accessibility.md)
- [Co nowego w programie Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio)
- [ASP.NET](/aspnet)
- [Co nowego w programie Visual C++](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
