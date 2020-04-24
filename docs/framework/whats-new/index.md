---
title: Co nowego w programie .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: f56ba7d68be107e697d3f732767f0a5f11c1a622
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644229"
---
# <a name="whats-new-in-net-framework"></a>Co nowego w platformie .NET Framework

W tym artykule podsumowano najważniejsze nowe funkcje i ulepszenia w następujących wersjach programu .NET Framework:

- [.NET Framework 4.8](#v48)
- [.NET Framework 4.7.2](#v472)
- [.NET Framework 4.7.1](#v471)
- [.NET Framework 4.7](#v47)
- [.NET Framework 4.6.2](#v462)
- [.NET Framework 4.6.1](#v461)
- [.NET 2015 i .NET Framework 4.6](#v46)
- [.NET Framework 4.5.2](#v452)
- [.NET Framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Ten artykuł nie zawiera wyczerpujących informacji o każdej nowej funkcji i może ulec zmianie. Aby uzyskać ogólne informacje na temat programu .NET Framework, zobacz [Wprowadzenie](../get-started/index.md). Aby zapoznać się z obsługiwanymi platformami, zobacz [Wymagania systemowe](../get-started/system-requirements.md). Aby uzyskać łącza do pobierania i instrukcje instalacji, zobacz [Podręcznik instalacji](../install/guide-for-developers.md).

> [!NOTE]
> Zespół .NET Framework również zwalnia funkcje poza pasmem z NuGet, aby rozwinąć obsługę platformy i wprowadzić nowe funkcje, takie jak niezmienne kolekcje i typy wektorów obsługujące kartę SIMD. Aby uzyskać więcej informacji, zobacz [Dodatkowe biblioteki klas i interfejsy API](../additional-apis/index.md) [oraz wersje .NET Framework i Out-of-Band](../get-started/the-net-framework-and-out-of-band-releases.md).
> Zobacz [pełną listę pakietów NuGet](https://www.nuget.org/profiles/dotnetframework) dla programu .NET Framework.

<a name="v48" />

## <a name="introducing-net-framework-48"></a>Przedstawiamy platformę .NET Framework 4.8

Program .NET Framework 4.8 opiera się na poprzednich wersjach programu .NET Framework 4.x, dodając wiele nowych poprawek i kilka nowych funkcji, pozostając jednocześnie bardzo stabilnym produktem.

### <a name="downloading-and-installing-net-framework-48"></a>Pobieranie i instalowanie programu .NET Framework 4.8

Program .NET Framework 4.8 można pobrać z następujących lokalizacji:

- [Instalator sieci Web programu .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [Instalator net framework 4.8 w trybie offline](https://dotnet.microsoft.com/download/dotnet-framework/net48)

Program .NET Framework 4.8 można zainstalować w systemach Windows 10, Windows 8.1, Windows 7 z zb1 i odpowiednich platformach serwerowych, począwszy od systemu Windows Server 2008 R2 z dodatku SP1. Program .NET Framework 4.8 można zainstalować za pomocą instalatora sieci Web lub instalatora w trybie offline. Zalecanym sposobem dla większości użytkowników jest użycie instalatora sieci web.

Program .NET Framework 4.8 można kierować na platformę .NET Framework 4.8 w programie Visual Studio 2012 lub nowszym, instalując [pakiet .NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).

### <a name="whats-new-in-net-framework-48"></a>Co nowego w .NET Framework 4.8

Program .NET Framework 4.8 wprowadza nowe funkcje w następujących obszarach:

- [Klasy podstawowe](#core48)
- [Windows Communication Foundation (WCF)](#wcf48)
- [Windows Presentation Foundation (WPF)](#wpf48)
- [Środowisko wykonawcze języka wspólnego](#clr48)

Ulepszona dostępność, która umożliwia aplikacji zapewnienie odpowiedniego środowiska dla użytkowników technologii ułatwień dostępu, nadal jest głównym celem programu .NET Framework 4.8. Aby uzyskać informacje na temat ulepszeń ułatwień dostępu w programie .NET Framework 4.8, zobacz [Co nowego w ułatwieniach dostępu w programie .NET Framework](whats-new-in-accessibility.md).

<a name="core48" />

#### <a name="base-classes"></a>Klas podstawowych

**Zmniejszony wpływ FIPS na kryptografię.** W poprzednich wersjach programu .NET Framework klasy <xref:System.Security.Cryptography.SHA256Managed> zarządzanych <xref:System.Security.Cryptography.CryptographicException> dostawców kryptograficznych, takie jak throw a, gdy biblioteki kryptograficzne systemu są skonfigurowane w trybie "FIPS". Wyjątki te są zgłaszane, ponieważ zarządzane wersje klas dostawcy kryptograficznego, w przeciwieństwie do bibliotek kryptograficznych systemu, nie zostały poddane certyfikacji FIPS (Federal Information Processing Standards) 140-2. Ponieważ niewielu deweloperów ma swoje maszyny programistyczne w trybie FIPS, wyjątki są często generowane w systemach produkcyjnych.

Domyślnie w aplikacjach docelowych .NET Framework 4.8 następujące klasy <xref:System.Security.Cryptography.CryptographicException> kryptografii zarządzanej nie są już w tym przypadku odrzucane:

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

Zamiast tego te klasy przekierowują operacje kryptograficzne do biblioteki kryptografii systemowej. Ta zmiana skutecznie usuwa potencjalnie mylące różnice między środowiskami deweloperskimi i środowiskami produkcyjnymi i sprawia, że składniki macierzyste i składniki zarządzane działają zgodnie z tymi samymi zasadami kryptograficznymi. Aplikacje, które zależą od tych wyjątków można przywrócić `Switch.System.Security.Cryptography.UseLegacyFipsThrow` poprzednie `true`zachowanie, ustawiając AppContext przełączyć się na . Aby uzyskać więcej informacji, zobacz [Zarządzane klasy kryptografii nie zgłaszają kryptografiiException w trybie FIPS](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).

**Korzystanie ze zaktualizowanej wersji ZLib**

Począwszy od .NET Framework 4.5, clrcompression.dll zestaw używa [ZLib](https://www.zlib.net), natywnej biblioteki zewnętrznej kompresji danych, w celu zapewnienia implementacji dla algorytmu deflate. .NET Framework 4.8, clrcompression.dll jest aktualizowany do korzystania z wersji ZLib 1.2.11, który zawiera kilka kluczowych ulepszeń i poprawek.

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

**Wprowadzenie ServiceHealthBehavior**

Punkty końcowe kondycji są szeroko używane przez narzędzia aranżacji do zarządzania usługami na podstawie ich stanu kondycji. Kontrole kondycji mogą być również używane przez narzędzia monitorowania do śledzenia i dostarczania powiadomień o dostępności i wydajności usługi.

**ServiceHealthBehavior** jest zachowanie usługi WCF, która rozszerza <xref:System.ServiceModel.Description.IServiceBehavior>.  Po dodaniu <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> do kolekcji zachowanie usługi wykonuje następujące czynności:

- Zwraca stan kondycji usługi z kodami odpowiedzi HTTP. Można określić w ciągu kwerendy kod stanu HTTP dla żądania sondy kondycji HTTP/GET.

- Publikuje informacje o kondycji usługi. Szczegóły specyficzne dla usługi, w tym stan usługi, liczba przepustnicy i pojemność `?health` mogą być wyświetlane przy użyciu żądania HTTP/GET z ciągiem zapytania. Łatwość dostępu do takich informacji jest ważne podczas rozwiązywania problemów z niewłaściwie usługi WCF.

Istnieją dwa sposoby, aby udostępnić punkt końcowy kondycji i opublikować informacje o kondycji usługi WCF:

- Za pomocą kodu. Przykład:

  ```csharp
  ServiceHost host = new ServiceHost(typeof(Service1),
                     new Uri("http://contoso:81/Service1"));
  ServiceHealthBehavior healthBehavior =
      host.Description.Behaviors.Find<ServiceHealthBehavior>();
  healthBehavior ??= new ServiceHealthBehavior();
  host.Description.Behaviors.Add(healthBehavior);
  ```

  ```vb
  Dim host As New ServiceHost(GetType(Service1),
              New Uri("http://contoso:81/Service1"))
  Dim healthBehavior As ServiceHealthBehavior =
     host.Description.Behaviors.Find(Of ServiceHealthBehavior)()
  If healthBehavior Is Nothing Then
     healthBehavior = New ServiceHealthBehavior()
  End If
  host.Description.Behaviors.Add(healthBehavior)
  ```

- Za pomocą pliku konfiguracyjnego. Przykład:

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

Stan kondycji usługi można wyszukiwać za pomocą parametrów `OnDispatcherFailure` `OnListenerFailure`kwerendy, takich jak `OnThrottlePercentExceeded` `OnServiceFailure`, , i kod odpowiedzi HTTP można określić dla każdego parametru kwerendy. Jeśli kod odpowiedzi HTTP zostanie pominięty dla parametru kwerendy, kod odpowiedzi HTTP 503 jest używany domyślnie. Przykład:

- OnServiceFailure:`https://contoso:81/Service1?health&OnServiceFailure=450`

  Kod stanu odpowiedzi HTTP 450 jest zwracany, gdy <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) jest większy niż .
Parametry kwerendy i przykłady:

- OnDispatcherFailure:`https://contoso:81/Service1?health&OnDispatcherFailure=455`

  Kod stanu odpowiedzi HTTP 455 jest zwracany, gdy stan któregokolwiek z dyspozytorów kanału jest większy niż <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.

- OnListenerFailure:`https://contoso:81/Service1?health&OnListenerFailure=465`

  Kod stanu odpowiedzi HTTP 465 jest zwracany, gdy stan któregokolwiek z odbiorników kanału jest większy niż <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.

- OnThrottlePercentExceeded:`https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`

  Określa wartość procentową {1 – 100}, która wyzwala odpowiedź i jej kod odpowiedzi HTTP {200 – 599}. W tym przykładzie:

  - Jeśli wartość procentowa jest większa niż 95, zwracany jest kod odpowiedzi HTTP 500.

  - Jeśli zwracana jest wartość procentowa lub między 70 a 95, zwracana jest wartość 350.

  - W przeciwnym razie zwraca się 200.

Stan kondycji usługi można wyświetlić w formacie HTML, określając `https://contoso:81/Service1?health` ciąg zapytania, taki jak lub `https://contoso:81/Service1?health&Xml`w formacie XML, określając ciąg zapytania, taki jak . Ciąg zapytania, `https://contoso:81/Service1?health&NoContent` taki jak zwraca pustą stronę HTML.

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Ulepszenia o wysokiej rozdzielczości DPI**

W programie .NET Framework 4.8 WPF WPF dodaje obsługę świadomości DPI na monitorze V2 i skalowania DPI w trybie mieszanym. Aby uzyskać dodatkowe informacje na temat rozwoju wysokiej rozdzielczości [DPI w systemie Windows, zobacz tworzenie aplikacji dla komputerów stacjonarnych](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) o wysokiej rozdzielczości DPI.

Program .NET Framework 4.8 poprawia obsługę hostowanych identyfikatorów HWND i windows forms w aplikacjach WPF o wysokiej rozdzielczości dpi na platformach obsługujących skalowanie dpi w trybie mieszanym (począwszy od aktualizacji systemu Windows 10 kwietnia 2018). Gdy hostowane identyfikatory HWND lub windows forms formanty są tworzone jako mieszane tryb dpi skalowane okna przez wywołanie [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) i [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), mogą być hostowane w aplikacji Per-Monitor V2 WPF i są odpowiednio do wielkości i skalowane. Taka hostowana zawartość nie jest renderowana w natywnej rozdzielczości DPI; Zamiast tego system operacyjny skaluje hostowane treści do odpowiedniego rozmiaru. Obsługa trybu świadomości DPI w monitorze dla monitora w wersji 2 umożliwia również hostowaniem formantów WPF (tj. nadrzędnych) w oknie macierzystym w aplikacji o wysokiej rozdzielczości DPI.

Aby włączyć obsługę skalowania o wysokiej rozdzielczości DPI w trybie mieszanym, można ustawić następujące przełączniki [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w pliku konfiguracji aplikacji:

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a>Środowisko wykonawcze języka wspólnego

Środowisko wykonawcze w programie .NET Framework 4.8 zawiera następujące zmiany i ulepszenia:

**Ulepszenia kompilatora JIT**. Kompilator Just-in-time (JIT) w programie .NET Framework 4.8 jest oparty na kompilatorze JIT w programie .NET Core 2.1. Wiele optymalizacji i wszystkie poprawki błędów wprowadzone do kompilatora JIT .NET Core 2.1 są zawarte w kompilatorze JIT .NET Framework 4.8.

**NGEN ulepszenia**. Środowisko wykonawcze poprawiło zarządzanie pamięcią dla obrazów [Generatora obrazów natywnych](../tools/ngen-exe-native-image-generator.md) (NGEN), dzięki czemu dane mapowane z obrazów NGEN nie są rezydentne w pamięci. Zmniejsza to powierzchnię dostępną dla ataków, które próbują wykonać dowolny kod, modyfikując pamięć, która zostanie wykonana.

**Skanowanie złośliwego oprogramowania dla wszystkich zestawów**. W poprzednich wersjach programu .NET Framework środowisko wykonawcze skanuje wszystkie zestawy załadowane z dysku przy użyciu usługi Windows Defender lub oprogramowania do ochrony przed złośliwym oprogramowaniem innych firm. Jednak zestawy ładowane z innych źródeł, <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> takich jak metoda, nie są skanowane i mogą potencjalnie zawierać niewykryte złośliwe oprogramowanie. Począwszy od programu .NET Framework 4.8 działającego w systemie Windows 10, środowisko wykonawcze uruchamia skanowanie za pomocą rozwiązań ochrony przed złośliwym oprogramowaniem, które implementują [interfejs skanowania przeciw złośliwemu oprogramowania (AMSI).](/windows/desktop/AMSI/antimalware-scan-interface-portal)

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a>Co nowego w .NET Framework 4.7.2

Program .NET Framework 4.7.2 zawiera nowe funkcje w następujących obszarach:

- [Klasy podstawowe](#core-472)
- [ASP.NET](#asp-net472)
- [Networking](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

Ciągła koncentracja w .NET Framework 4.7.2 jest lepsza dostępność, która umożliwia aplikacji zapewnienie odpowiedniego środowiska dla użytkowników technologii ułatwień dostępu. Aby uzyskać informacje na temat ulepszeń ułatwień dostępu w programie .NET Framework 4.7.2, zobacz [Co nowego w ułatwieniach dostępu w programie .NET Framework](whats-new-in-accessibility.md).

<a name="core-472" />

#### <a name="base-classes"></a>Klas podstawowych

Program .NET Framework 4.7.2 zawiera dużą liczbę ulepszeń kryptograficznych, lepszą obsługę dekompresji dla archiwów ZIP i dodatkowe interfejsy API kolekcji.

**Nowe przeciążenia RSA. Tworzenie i DSA. Utworzyć**

Metody <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> i umożliwiają podanie kluczowych parametrów podczas <xref:System.Security.Cryptography.DSA> <xref:System.Security.Cryptography.RSA> tworzenia wystąpienia nowego lub klucza. Pozwalają one zastąpić kod jak następujące:

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

z takim kodem:

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

Metody <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> i umożliwiają generowanie nowych <xref:System.Security.Cryptography.DSA> kluczy lub <xref:System.Security.Cryptography.RSA> kluczy o określonym rozmiarze klucza. Przykład:

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

**Konstruktory Rfc2898DeriveBytes akceptują nazwę algorytmu mieszania**

Klasa <xref:System.Security.Cryptography.Rfc2898DeriveBytes> ma trzy nowe konstruktory z parametrem, <xref:System.Security.Cryptography.HashAlgorithmName> który identyfikuje algorytm HMAC do użycia podczas wyprowadzania kluczy. Zamiast używać SHA-1, deweloperzy powinni używać HMAC opartego na sha-2, takiego jak SHA-256, jak pokazano w poniższym przykładzie:

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

**Obsługa klawiszy tymczasowych**

Import PFX może opcjonalnie załadować klucze prywatne bezpośrednio z pamięci, omijając dysk twardy.Gdy nowa <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flaga jest <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> określona w konstruktorze <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> lub jeden z przeciążeń metody, klucze prywatne zostaną załadowane jako klucze efemeryczne. Zapobiega to widoczne klucze na dysku. Jednak:

- Ponieważ klucze nie są zachowywane na dysku, certyfikaty ładowane z tą flagą nie są dobrymi kandydatami do dodania do sklepu X509Store.

- Klucze ładowane w ten sposób są prawie zawsze ładowane przez Windows CNG. W związku z tym wywołujący muszą uzyskać dostęp do klucza prywatnego, wywołując metody rozszerzenia, takie jak [cert. GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). Właściwość <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> nie działa.

- Ponieważ starsza <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> właściwość nie działa z certyfikatami, deweloperzy powinni przeprowadzić rygorystyczne testy przed przełączeniem na klucze efemeryczne.

**Programowe tworzenie żądań podpisywania certyfikatów PKCS#10 i certyfikatów kluczy publicznych X.509**

Począwszy od programu .NET Framework 4.7.2, obciążenia mogą generować żądania podpisywania certyfikatów (CRS), co umożliwia wystawianie generowania żądań certyfikatów do istniejących narzędzi. Jest to często przydatne w scenariuszach testowych.

Aby uzyskać więcej informacji i przykłady kodu, zobacz "Programowe tworzenie żądań podpisywania certyfikatów PKCS#10 i certyfikatów kluczy publicznych X.509" w [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Nowi członkowie SignerInfo**

Począwszy od .NET Framework <xref:System.Security.Cryptography.Pkcs.SignerInfo> 4.7.2, klasa udostępnia więcej informacji na temat podpisu. Można pobrać wartość właściwości, <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> aby określić algorytm podpisu używany przez sygnatariusza. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>można wywołać, aby uzyskać kopię podpisu kryptograficznego dla tego sygnatariusza.

**Pozostawienie zawiniętego strumienia otwartego po usunięciu CryptoStream**

Począwszy od .NET Framework 4.7.2, <xref:System.Security.Cryptography.CryptoStream> klasa ma <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> dodatkowy konstruktor, który pozwala nie zamykać opakowane strumienia.Aby pozostawić opakowany <xref:System.Security.Cryptography.CryptoStream> strumień otwarty po usunięciu <xref:System.Security.Cryptography.CryptoStream> wystąpienia, należy wywołać nowy konstruktor w następujący sposób:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**Zmiany dekompresyjne w DeflateStream**

Począwszy od programu .NET Framework 4.7.2, implementacja <xref:System.IO.Compression.DeflateStream> operacji dekompresyjnych w klasie została zmieniona na domyślne używanie natywnych interfejsów API systemu Windows. Zazwyczaj powoduje to znaczną poprawę wydajności.

Obsługa dekompresji przy użyciu interfejsów API systemu Windows jest domyślnie włączona dla aplikacji docelowych .NET Framework 4.7.2. Aplikacje przeznaczone dla wcześniejszych wersji programu .NET Framework, ale uruchomione w ramach programu .NET Framework 4.7.2, mogą zdecydować się na to zachowanie, dodając następujący [przełącznik AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do pliku konfiguracji aplikacji:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**Dodatkowe interfejsy API kolekcji**

.NET Framework 4.7.2 dodaje szereg nowych interfejsów API do <xref:System.Collections.Generic.SortedSet%601> i <xref:System.Collections.Generic.HashSet%601> typów. Należą do nich:

- `TryGetValue`metody, które rozszerzają wzorzec try używane w innych typach kolekcji do tych dwóch typów. Dostępne metody:

  - [publicznego bool\<HashSet T>. TryGetValue(T equalValue, out T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [publicznego bool\<SortedSet T>. TryGetValue(T equalValue, out T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- `Enumerable.To*`metody rozszerzenia, które konwertuje kolekcję na: <xref:System.Collections.Generic.HashSet%601>

  - [public static HashSet\<TSource> ToHashSet\<TSource>(to źródło\<> IEnumerable TSource)](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [\<public static HashSet TSource> ToHashSet\<TSource>(to źródło\<> IEnumerable TSource, IEqualityComparer\<TSource> comparer)](xref:System.Linq.Enumerable.ToHashSet%2A)

- Nowe <xref:System.Collections.Generic.HashSet%601> konstruktory, które umożliwiają ustawienie pojemności kolekcji, co daje korzyści <xref:System.Collections.Generic.HashSet%601> wydajności, gdy znasz rozmiar z wyprzedzeniem:

  - [publiczna pojemność hashset(int)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
  - [public HashSet(int capacity, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

Klasa <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zawiera nowe przeciążenia <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> i metody, aby pobrać wartość ze słownika lub dodać go, jeśli nie zostanie znaleziony, i dodać wartość do słownika lub zaktualizować go, jeśli już istnieje.

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

[Iniekcja zależności (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) oddziela obiekty i ich zależności, dzięki czemu kod obiektu nie musi być już zmieniany tylko dlatego, że zmieniono zależność. Podczas tworzenia aplikacji ASP.NET docelowych .NET Framework 4.7.2 można:

- Użyj wtrysku opartego na seterach, interfejsie i konstruktorze w [programach obsługi i modułach,](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)) [wystąpieniach strony](xref:System.Web.UI.Page)i [formancie użytkowników](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ASP.NET projektów aplikacji sieci web.

- Użyj wtrysku opartego na modułach ustawiający i opartego na interfejsie w [programach obsługi i modułach,](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)) [wystąpieniach strony](xref:System.Web.UI.Page)i [kontrolach użytkowników](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ASP.NET projektów witryn sieci Web.

- Podłącz różne struktury iniekcji zależności.

**Obsługa plików cookie tej samej witryny**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) uniemożliwia przeglądarce wysyłanie plików cookie wraz z żądaniem między witrynami. .NET Framework 4.7.2 <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> dodaje właściwość, której wartość jest elementem <xref:System.Web.SameSiteMode?displayProperty=nameWithType> członkowskim wyliczenia. Jeśli jego <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> wartość <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>jest lub , `SameSite` ASP.NET dodaje atrybut do nagłówka set-cookie. Obsługa sameSite dotyczy <xref:System.Web.HttpCookie> obiektów, a <xref:System.Web.Security.FormsAuthentication> także <xref:System.Web.SessionState> plików cookie i plików cookie.

Dla <xref:System.Web.HttpCookie> obiektu można ustawić ten sam obiekt w następujący sposób:

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

Możesz również skonfigurować pliki cookie SameSite na poziomie aplikacji, modyfikując plik web.config:

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

Możesz dodać SameSite <xref:System.Web.Security.FormsAuthentication> <xref:System.Web.SessionState> dla i pliki cookie, modyfikując plik konfiguracji internetowej:

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   </authentication>
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />

#### <a name="networking"></a>Networking

**Implementacja właściwości HttpClientHandler**

Program .NET Framework 4.7.1 dodał <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> osiem właściwości do klasy. Jednak dwa rzucił <xref:System.PlatformNotSupportedException>. .NET Framework 4.7.2 zapewnia teraz implementację dla tych właściwości. Właściwości są następujące:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a>SQLClient

**Obsługa uwierzytelniania uniwersalnego usługi Azure Active Directory i uwierzytelniania wieloskładnikowego**

Rosnąca zgodność i wymagania dotyczące zabezpieczeń wymagają, aby wielu klientów korzystało z uwierzytelniania wieloskładnikowego (MFA). Ponadto bieżące najlepsze rozwiązania zniechęcają do dołączania haseł użytkowników bezpośrednio w ciągach połączeń. Aby obsługiwać te zmiany, program .NET Framework 4.7.2 rozszerza [parametry połączenia SQLClient,](xref:System.Data.SqlClient.SqlConnection.ConnectionString) dodając nową wartość "Active Directory Interactive", dla istniejącego słowa kluczowego "Uwierzytelnianie" do obsługi usługi MFA i [uwierzytelniania usługi Azure AD.](/azure/sql-database/sql-database-aad-authentication-configure) Nowa metoda interaktywna obsługuje natywnych i federowanych użytkowników usługi Azure AD, a także użytkowników-gości usługi Azure AD. Gdy ta metoda jest używana, uwierzytelnianie usługi MFA nałożone przez usługę Azure AD jest obsługiwane dla baz danych SQL. Ponadto proces uwierzytelniania żąda hasła użytkownika do przestrzegania najlepszych rozwiązań w zakresie zabezpieczeń.

W poprzednich wersjach programu .NET Framework łączność <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> SQL obsługiwała tylko opcje i opcje. Oba te są częścią nieinterakcyjnego [protokołu ADAL,](/azure/active-directory/develop/active-directory-authentication-libraries)który nie obsługuje usługi MFA. Dzięki nowej <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> opcji łączność SQL obsługuje usługi MFA, a także istniejące metody uwierzytelniania (hasło i zintegrowane uwierzytelnianie), co umożliwia użytkownikom interaktywne wprowadzanie haseł użytkowników bez utrwalania haseł w ciągu połączenia.

Aby uzyskać więcej informacji i przykład, zobacz "SQL -- Azure AD Universal and Multi-factor Authentication Support" w [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Obsługa zawsze zaszyfrowanej wersji 2**

NET Framework 4.7.2 dodaje obsługuje oparte na enklawie zawsze szyfrowane. Oryginalna wersja Always Encrypted to technologia szyfrowania po stronie klienta, w której klucze szyfrowania nigdy nie opuszczają klienta. W enklawie zawsze szyfrowane, klient może opcjonalnie wysłać klucze szyfrowania do bezpiecznej enklawy, która jest bezpieczną jednostką obliczeniową, która może być uznana za część programu SQL Server, ale kod programu SQL Server nie może manipulować. Aby obsługiwać oparte na enklawie zawsze szyfrowane, .NET Framework 4.7.2 dodaje następujące typy i elementy członkowskie do obszaru <xref:System.Data.SqlClient> nazw:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, który określa identyfikator Uri dla enklawy oparte zawsze zaszyfrowane.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, która jest klasą abstrakcyjną, z której pochodzą wszyscy dostawcy enklaw.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, który hermetyzuje stan dla danej sesji enklawy.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, który udostępnia parametry zaświadczania używane przez program SQL Server w celu uzyskania informacji wymaganych do wykonania określonego protokołu zaświadczania.

Plik konfiguracji aplikacji następnie określa konkretnej <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> implementacji klasy abstrakcyjnej, która zapewnia funkcjonalność dla dostawcy enklawy. Przykład:

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

Podstawowy przepływ oparte na enklawie zawsze szyfrowane jest:

1. Użytkownik tworzy połączenie AlwaysEncrypted z programem SQL Server, które obsługuje oparte na enklawie zawsze szyfrowane. Kierowca kontaktuje się z usługą zaświadczania, aby upewnić się, że łączy się z właściwą enklawą.

1. Po zatwierdzeniu enklawy sterownik ustanawia bezpieczny kanał z bezpieczną enklawą hostowane na sql server.

1. Sterownik udostępnia klucze szyfrowania autoryzowane przez klienta z bezpieczną enklawą na czas trwania połączenia SQL.

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Znajdowanie resourcedictionaries według źródła**

Począwszy od programu .NET Framework 4.7.2, asystent diagnostyczny można <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> zlokalizować, które zostały utworzone z danego źródła Uri.(Ta funkcja jest używana przez asystentów diagnostycznych, a nie przez aplikacje produkcyjne). Asystent diagnostyczny, takich jak Visual Studio "Edit-and-Continue" obiekt umożliwia jego użytkownika edytować ResourceDictionary z zamiarem, że zmiany mają być stosowane do uruchomionej aplikacji. Jednym z kroków w osiągnięciu tego jest znalezienie wszystkich ResourceDictionaries, że uruchomiona aplikacja została utworzona ze słownika, który jest edytowany. Na przykład aplikacja może zadeklarować ResourceDictionary, którego zawartość jest kopiowana z danego źródła identyfikatora URI:

```xml
<ResourceDictionary Source="MyRD.xaml" />
```

Asystent diagnostyczny, który edytuje oryginalny znacznik w *myRD.xaml,* może użyć nowej funkcji, aby zlokalizować słownik.Funkcja jest implementowana przez nową metodę <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>statyczną, . Asystent diagnostyczny wywołuje nową metodę przy użyciu bezwzględnego identyfikatora Uri, który identyfikuje oryginalne znaczniki, jak pokazano w poniższym kodzie:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

Metoda zwraca puste wyliczalne, chyba <xref:System.Windows.Diagnostics.VisualDiagnostics> że [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  jest włączona i zmienna środowiskowa jest ustawiona.

**Znajdowanie właścicieli ResourceDictionary**

Począwszy od programu .NET Framework 4.7.2, asystent <xref:Windows.UI.Xaml.ResourceDictionary>diagnostyczny może zlokalizować właścicieli danego programu .(Funkcja jest używana przez asystentów diagnostycznych, a nie przez aplikacje produkcyjne). Za każdym razem, gdy <xref:Windows.UI.Xaml.ResourceDictionary>zmiana zostanie wniesiona do programu, WPF automatycznie znajdzie wszystkie odwołania [DynamicResource,](../wpf/advanced/dynamicresource-markup-extension.md) które mogą mieć wpływ na zmianę.

Asystent diagnostyczny, taki jak visual studio "Edit-and-Continue" funkcji może chcesz rozszerzyć to do obsługi [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odwołania. Pierwszym krokiem w tym procesie jest znalezienie właścicieli słownika; oznacza to, aby znaleźć `Resources` wszystkie obiekty, których właściwość odwołuje się do słownika <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> (bezpośrednio lub pośrednio za pośrednictwem właściwości). Trzy nowe metody statyczne <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> zaimplementowane w klasie, po `Resources` jednej dla każdego z typów podstawowych, który ma właściwość, obsługuje ten krok:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Metody te zwracają puste wyliczalne, chyba że <xref:System.Windows.Diagnostics.VisualDiagnostics> jest włączona i zmienna środowiskowa [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  jest ustawiona.

**Znajdowanie odwołań staticResource**

Asystent diagnostyczny może teraz otrzymywać powiadomienie za każdym razem, gdy odwołanie [StaticResource](../wpf/advanced/staticresource-markup-extension.md) zostanie rozpoznane.(Funkcja jest używana przez asystentów diagnostycznych, a nie przez aplikacje produkcyjne).) Asystent diagnostyczny, taki jak visual studio "Edit-and-Continue" funkcji może chcesz zaktualizować wszystkie <xref:Windows.UI.Xaml.ResourceDictionary> zastosowania zasobu, gdy jego wartość w zmianie. WPF WPF robi to automatycznie dla [odwołań DynamicResource,](../wpf/advanced/dynamicresource-markup-extension.md) ale celowo nie robi tego dla [odwołań StaticResource.](../wpf/advanced/staticresource-markup-extension.md) Począwszy od programu .NET Framework 4.7.2, asystent diagnostyczny może używać tych powiadomień do lokalizowania tych zastosowań zasobu statycznego.

Powiadomienie jest implementowane przez <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> nowe zdarzenie:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

To zdarzenie jest wywoływane za każdym razem, gdy środowisko wykonawcze rozpoznaje odwołanie [StaticResource.](../wpf/advanced/staticresource-markup-extension.md)Argumenty <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> opisują rozdzielczość i wskazują obiekt i właściwość, które hostują odwołanie [StaticResource](../wpf/advanced/staticresource-markup-extension.md) oraz <xref:Windows.UI.Xaml.ResourceDictionary> klucz i klucz używany do rozpoznawania:

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

```vb
Public Class StaticResourceResolvedEventArgs : Inherits EventArgs
   Public ReadOnly Property TargetObject As Object
   Public ReadOnly Property TargetProperty As Object
   Public ReadOnly Property ResourceDictionary As ResourceDictionary
   Public ReadOnly Property ResourceKey As Object
End Class
```

Zdarzenie nie jest wywoływane `add` (a jego akcesor jest ignorowany), chyba że <xref:System.Windows.Diagnostics.VisualDiagnostics> jest włączona i ustawiona [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  jest zmienna środowiskowa.

#### <a name="clickonce"></a>ClickOnce

Aplikacje obsługujące interfejs HDPI dla formularzy systemu Windows, Programu Windows Presentation Foundation (WPF) i Visual Studio Tools for Office (VSTO) można wdrożyć za pomocą clickonce. Jeśli w manifeście aplikacji zostanie znaleziony następujący wpis, wdrożenie zakończy się pomyślnie w ramach programu .NET Framework 4.7.2:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

W przypadku aplikacji Windows Forms poprzednie obejście ustawiania świadomości DPI w pliku konfiguracji aplikacji, a nie w manifeście aplikacji, nie jest już konieczne dla pomyślnego wdrożenia ClickOnce.

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a>Co nowego w .NET Framework 4.7.1

Program .NET Framework 4.7.1 zawiera nowe funkcje w następujących obszarach:

- [Klasy podstawowe](#core471)
- [Środowisko wykonawcze języka wspólnego (CLR)](#clr)
- [Networking](#net471)
- [ASP.NET](#asp-net471)

Ponadto głównym celem w .NET Framework 4.7.1 jest poprawa dostępności, co pozwala aplikacji, aby zapewnić odpowiednie środowisko dla użytkowników technologii ułatwień dostępu. Aby uzyskać informacje na temat ulepszeń ułatwień dostępu w programie .NET Framework 4.7.1, zobacz [Co nowego w ułatwieniach dostępu w programie .NET Framework](whats-new-in-accessibility.md).

<a name="core471" />

#### <a name="base-classes"></a>Klas podstawowych

**Obsługa platformy .NET Standard 2.0**

[Program .NET Standard](../../standard/net-standard.md) definiuje zestaw interfejsów API, które muszą być dostępne dla każdej implementacji platformy .NET obsługującej tę wersję standardu. Program .NET Framework 4.7.1 w pełni obsługuje program .NET Standard 2.0 i dodaje [około 200 interfejsów API zdefiniowanych](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) w standardzie .NET Standard 2.0 i których brakuje w programach .NET Framework 4.6.1, 4.6.2 i 4.7. (Należy zauważyć, że te wersje platformy .NET Framework obsługują .NET Standard 2.0 tylko wtedy, gdy dodatkowe pliki pomocy technicznej .NET Standard są również wdrażane w systemie docelowym). Aby uzyskać więcej informacji, zobacz "BCL - .NET Standard 2.0 Support" w poście w blogu [.NET Framework 4.7.1 Runtime and Compiler Features.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/)

**Obsługa konstruktorów konfiguracji**

Konstruktorzy konfiguracji umożliwiają deweloperom dynamiczne wstrzykiwanie i tworzenie ustawień konfiguracji aplikacji w czasie wykonywania. Konstruktory konfiguracji niestandardowej mogą służyć do modyfikowania istniejących danych w sekcji konfiguracji lub do tworzenia sekcji konfiguracji całkowicie od podstaw. Bez konstruktorów konfiguracji pliki .config są statyczne, a ich ustawienia są definiowane na jakiś czas przed uruchomieniem aplikacji.

Aby utworzyć niestandardowy konstruktor konfiguracji, należy wyprowadzić konstruktora z klasy abstrakcyjnej <xref:System.Configuration.ConfigurationBuilder> i zastąpić jej <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> i <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. Można również zdefiniować konstruktorów w pliku .config. Aby uzyskać więcej informacji, zobacz sekcję "Konstruktorzy konfiguracji" w poście blogu [.NET Framework 4.7.1 ASP.NET i funkcje konfiguracji.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/)

**Wykrywanie funkcji w czasie wykonywania**

Klasa <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> zapewnia mechanizm określania, czy wstępnie zdefiniowana funkcja jest obsługiwana w danej implementacji .NET w czasie kompilacji lub w czasie wykonywania. W czasie kompilacji kompilator może sprawdzić, czy określone pole istnieje, aby ustalić, czy funkcja jest obsługiwana; jeśli tak, może emitować kod, który korzysta z tej funkcji. W czasie wykonywania aplikacja może <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> wywołać metodę przed emisją kodu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Dodawanie metody pomocnika w celu opisania funkcji obsługiwanych przez środowisko wykonawcze](https://github.com/dotnet/corefx/issues/17116).

**Typy krotek wartości są serializable**

Począwszy od .NET Framework 4.7.1 <xref:System.ValueTuple?displayProperty=nameWithType> i skojarzonych z nim typów ogólnych są oznaczone jako [Serializable](xref:System.SerializableAttribute), co umożliwia serializacji binarnej. Powinno to ułatwić migrację typów <xref:System.Tuple%603> krotek, takich jak i <xref:System.Tuple%604>, aby wartość typów krotki łatwiejsze. Aby uzyskać więcej informacji, zobacz "Kompilator — ValueTuple jest serializowalny" w wpisie w blogu [.NET Framework 4.7.1 Runtime and Compiler Features.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/)

**Obsługa odwołań tylko do odczytu**

Program .NET Framework 4.7.1 dodaje plik <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>. Ten atrybut jest używany przez kompilatory języka do oznaczania elementów członkowskich, które mają tylko do odczytu ref zwraca typy lub parametry. Aby uzyskać więcej informacji, zobacz "Kompilator — obsługa readonlyReferences" w poście w blogu [.NET Framework 4.7.1 Runtime and Compiler Features.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) Aby uzyskać informacje na temat wartości zwracane ref, zobacz [Ref zwraca wartości i ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) i Ref return values [(Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />

#### <a name="common-language-runtime-clr"></a>Środowisko uruchomieniowe języka wspólnego (CLR)

**Ulepszenia wydajności wyrzucania elementów bezużytecznych**

Zmiany w wyrzucaniu elementów bezużytecznych (GC) w .NET Framework 4.7.1 zwiększają ogólną wydajność, szczególnie w przypadku alokacji sterty dużych obiektów (LOH). W .NET Framework 4.7.1 oddzielne blokady są używane dla małych sterty obiektów (SOH) i alokacji LOH, co umożliwia alokacje LOH występuje, gdy gc w tle jest zamiatanie SOH. W rezultacie aplikacje, które tworzą dużą liczbę alokacji LOH powinny zobaczyć zmniejszenie rywalizacji blokady alokacji i lepszą wydajność. Aby uzyskać więcej informacji, zobacz sekcję "Runtime -- GC Performance Improvements" w poście w blogu [.NET Framework 4.7.1 Runtime and Compiler Features.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/)

<a name="net471"/>

#### <a name="networking"></a>Networking

**Obsługa sha-2 dla Message.HashAlgorithm**

W .NET Framework 4.7 i <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> wcześniejszych wersjach <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> właściwości obsługiwane wartości i tylko. Począwszy od programu .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>i <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> są również obsługiwane. Czy ta wartość jest rzeczywiście używana zależy <xref:System.Messaging.Message> od usługi MSMQ, ponieważ samo wystąpienie nie mieszania, ale po prostu przekazuje wartości do usługi MSMQ. Aby uzyskać więcej informacji, zobacz sekcję "Obsługa SHA-2 dla message.HashAlgorithm" w poście w blogu [.NET Framework 4.7.1 ASP.NET i konfiguracji.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/)

<a name="asp-net471" />

#### <a name="aspnet"></a>ASP.NET

**Kroki wykonywania w ASP.NET aplikacji**

ASP.NET przetwarza żądania w wstępnie zdefiniowanym potoku, który zawiera 23 zdarzenia. ASP.NET wykonuje każdy program obsługi zdarzeń jako krok wykonania. W wersjach ASP.NET do platformy .NET Framework 4.7 ASP.NET nie może przepływać kontekstu wykonywania z powodu przełączania między wątkami macierzystymi i zarządzanymi. Zamiast tego ASP.NET selektywnie przepływa <xref:System.Web.HttpContext>tylko . Począwszy od .NET Framework 4.7.1, <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> metoda umożliwia również moduły do przywracania danych otoczenia. Ta funkcja jest przeznaczona dla bibliotek zajmujących się śledzeniem, profilowanie, diagnostyka lub transakcji, na przykład, które dbają o przepływ wykonywania aplikacji. Aby uzyskać więcej informacji, zobacz "ASP.NET funkcja kroku wykonywania" w [blogu .NET Framework 4.7.1 ASP.NET i funkcje konfiguracji.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/)

**ASP.NET HttpCookie parsing**

.NET Framework 4.7.1 zawiera <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>nową metodę, która zapewnia znormalizowany sposób tworzenia <xref:System.Web.HttpCookie> obiektu z ciągu i dokładnie przypisać wartości plików cookie, takie jak data wygaśnięcia i ścieżka. Aby uzyskać więcej informacji, zobacz "ASP.NET httpcookie analizowanie" w [.NET Framework 4.7.1 ASP.NET i funkcje konfiguracji](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blogu.

**Opcje mieszania SHA-2 dla poświadczeń uwierzytelniania formularzy ASP.NET**

W programie .NET Framework 4.7 i wcześniejszych wersjach ASP.NET umożliwiał deweloperom przechowywanie poświadczeń użytkownika z haszowanymi hasłami w plikach konfiguracyjnych przy użyciu modułu MD5 lub SHA1. Począwszy od programu .NET Framework 4.7.1, ASP.NET obsługuje również nowe bezpieczne opcje mieszania SHA-2, takie jak SHA256, SHA384 i SHA512. SHA1 pozostaje domyślny, a domyślny algorytm mieszania można zdefiniować w pliku konfiguracji sieci Web. Przykład:

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

## <a name="whats-new-in-net-framework-47"></a>Co nowego w programach .NET Framework 4.7

Program .NET Framework 4.7 zawiera nowe funkcje w następujących obszarach:

- [Klasy podstawowe](#Core47)
- [Networking](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Aby uzyskać listę nowych interfejsów API dodanych do platformy .NET Framework 4.7, zobacz [.NET Framework 4.7 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) on GitHub. Aby uzyskać listę ulepszeń funkcji i poprawek błędów w programie .NET Framework 4.7, zobacz [.NET Framework 4.7 Lista zmian](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) w usłudze GitHub. Aby uzyskać więcej informacji, zobacz [Ogłaszanie programu .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) w blogu platformy .NET.

<a name="Core47" />

#### <a name="base-classes"></a>Klas podstawowych

.NET Framework 4.7 poprawia serializację <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>przez:

**Ulepszona funkcjonalność dzięki kryptografii krzywej eliptycznej (ECC)***

W .NET Framework 4.7 metody <xref:System.Security.Cryptography.ECDsa> zostały <xref:System.Security.Cryptography.ECDiffieHellman> dodane do i klas, `ImportParameters(ECParameters)` aby umożliwić obiekt do reprezentowania już ustalonego klucza. Dodano `ExportParameters(Boolean)` również metodę eksportowania klucza przy użyciu jawnych parametrów krzywej.

Program .NET Framework 4.7 dodaje również obsługę dodatkowych krzywych (w tym pakietu krzywej buforu) i dodał <xref:System.Security.Cryptography.ECDsa.Create%2A> <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> wstępnie zdefiniowane definicje ułatwiające tworzenie za pomocą nowych i fabrycznych metod.

Można zobaczyć [przykład .NET Framework 4.7 ulepszenia kryptografii](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) na GitHub.

**Lepsza obsługa znaków sterujących przez DataContractJsonSerializer**

W .NET Framework 4.7 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> klasa serializuje znaki sterujące zgodnie ze standardem ECMAScript 6. To zachowanie jest domyślnie włączone dla aplikacji docelowych .NET Framework 4.7 i jest funkcją opt-in dla aplikacji, które są uruchomione w ramach programu .NET Framework 4.7, ale są przeznaczone dla poprzedniej wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz sekcję [zgodności aplikacji.](../migration-guide/application-compatibility.md)

<a name="net47" />

#### <a name="networking"></a>Networking

Program .NET Framework 4.7 dodaje następującą funkcję związaną z siecią:

**Domyślna obsługa systemu operacyjnego dla protokołów TLS***

Stos TLS, który jest <xref:System.Net.Security.SslStream?displayProperty=nameWithType> używany przez składniki i up-stack, takie jak HTTP, FTP i SMTP, umożliwia deweloperom korzystanie z domyślnych protokołów TLS obsługiwanych przez system operacyjny. Deweloperzy nie muszą już kodować na czas wersji TLS.

<a name="ASP-NET47" />

#### <a name="aspnet"></a>ASP.NET

W programie .NET Framework 4.7 ASP.NET zawiera następujące nowe funkcje:

**Rozszerzalność pamięci podręcznej obiektów**

Począwszy od programu .NET Framework 4.7, ASP.NET dodaje nowy zestaw interfejsów API, które umożliwiają deweloperom zastąpienie domyślnych implementacji ASP.NET do buforowania obiektów w pamięci i monitorowania pamięci. Deweloperzy mogą teraz zastąpić dowolny z następujących trzech składników, jeśli ASP.NET implementacja nie jest odpowiednia:

- **Magazyn pamięci podręcznej obiektów**. Korzystając z sekcji konfiguracji nowych dostawców pamięci podręcznej, deweloperzy mogą podłączyć nowe implementacje pamięci podręcznej obiektów dla aplikacji ASP.NET przy użyciu nowego interfejsu **ICacheStoreProvider.**

- **Monitorowanie pamięci**. Domyślny monitor pamięci w ASP.NET powiadamia aplikacje, gdy są one uruchomione w pobliżu skonfigurowanych limitów bajtów prywatnych dla procesu lub gdy na komputerze brakuje całkowitej dostępnej fizycznej pamięci RAM. Gdy te limity są w pobliżu, powiadomienia są uruchamiane. W przypadku niektórych aplikacji powiadomienia są uruchamiane zbyt blisko skonfigurowanych limitów, aby umożliwić przydatne reakcje. Deweloperzy mogą teraz pisać własne monitory pamięci, <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> aby zastąpić domyślne przy użyciu właściwości.

- **Reakcje graniczne pamięci**. Domyślnie ASP.NET próbuje przyciąć pamięć podręczną obiektów <xref:System.GC.Collect%2A?displayProperty=nameWithType> i okresowo wywoływać, gdy zbliża się limit procesu bajtów prywatnych. W przypadku niektórych aplikacji <xref:System.GC.Collect%2A?displayProperty=nameWithType> częstotliwość wywołań lub ilość przyciętej pamięci podręcznej są nieefektywne. Deweloperzy mogą teraz zastąpić lub uzupełnić domyślne zachowanie, subskrybując implementacje **IObserver** na monitorze pamięci aplikacji.

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) dodaje następujące funkcje i zmiany:

**Możliwość skonfigurowania domyślnych ustawień zabezpieczeń wiadomości na TLS 1.1 lub TLS 1.2**

Począwszy od .NET Framework 4.7, WCF umożliwia skonfigurowanie TSL 1.1 lub TLS 1.2 oprócz SSL 3.0 i TSL 1.0 jako domyślnego protokołu zabezpieczeń wiadomości. Jest to ustawienie opt-in; aby ją włączyć, należy dodać następujący wpis do pliku konfiguracji aplikacji:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**Większa niezawodność aplikacji WCF i serializacja WCF**

WCF zawiera szereg zmian kodu, które eliminują warunki wyścigu, poprawiając w ten sposób wydajność i niezawodność opcji serializacji. Należą do nich:

- Lepsza obsługa mieszania kodu asynchroniczną i synchroniczną w wywołaniach **SocketConnection.BeginRead** i **SocketConnection.Read**.
- Poprawiono niezawodność podczas przerywania połączenia z **SharedConnectionListener** i **DuplexChannelBinder**.
- Zwiększona niezawodność operacji serializacji <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> podczas wywoływania metody.
- Zwiększona niezawodność podczas usuwania kelnera przez wywołanie **ChannelSynchronizer.RemoveWaiter** metody.

<a name="wf47" />

#### <a name="windows-forms"></a>Windows Forms

W programie .NET Framework 4.7 formularze systemu Windows zwiększają obsługę monitorów o wysokiej rozdzielczości DPI.

**Obsługa wysokiej rozdzielczości DPI**

Począwszy od aplikacji docelowych .NET Framework 4.7, .NET Framework oferuje obsługę wysokiej rozdzielczości DPI i dynamicznej rozdzielczości DPI dla aplikacji Windows Forms. Obsługa wysokiej rozdzielczości DPI poprawia układ i wygląd formularzy i elementów sterujących na monitorach o wysokiej rozdzielczości DPI. Dynamiczna rozdzielczość DPI zmienia układ i wygląd formularzy i formantów, gdy użytkownik zmieni współczynnik skali DPI lub wyświetlania uruchomionej aplikacji.

Obsługa wysokiej rozdzielczości DPI to funkcja opt-in skonfigurowana przez zdefiniowanie [ \<sekcji System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) w pliku konfiguracji aplikacji. Aby uzyskać więcej informacji na temat dodawania wysokiej obsługi dpi i dynamicznej obsługi dpi do aplikacji Windows Forms, zobacz [Obsługa wysokiej rozdzielczości DPI w formularzach systemu Windows](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

W programie .NET Framework 4.7 WPF WPF zawiera następujące ulepszenia:

**Obsługa stosu dotykowego/rysika opartego na wiadomościach WM_POINTER systemu Windows**

Teraz masz możliwość korzystania z stosu dotykowego/rysika na podstawie [WM_POINTER wiadomości](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) zamiast platformy usług odużynych systemu Windows (WISP). Jest to funkcja opt-in w .NET Framework. Aby uzyskać więcej informacji, zobacz sekcję [zgodności aplikacji.](../migration-guide/application-compatibility.md)

**Nowa implementacja interfejsów API drukowania WPF**

WPF WPF drukowania interfejsów API w <xref:System.Printing.PrintQueue?displayProperty=nameWithType> klasie wywołać interfejsu API pakietu dokumentów [drukowania](/windows/desktop/printdocs/tailored-app-printing-api) systemu Windows zamiast przestarzałe [XPS Print API](/windows/desktop/printdocs/xps-printing). Aby uzyskać wpływ tej zmiany na zgodność aplikacji, zobacz sekcję [Zgodność aplikacji.](../migration-guide/application-compatibility.md)

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a>Co nowego w .NET Framework 4.6.2

Program .NET Framework 4.6.2 zawiera nowe funkcje w następujących obszarach:

- [ASP.NET](#ASPNET462)

- [Kategorie znaków](#Strings)

- [Kryptografia](#Crypto462)

- [Sqlclient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Program Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Konwertowanie aplikacji Formularze systemu Windows i WPF WPF na aplikacje platformy uniwersalnej systemu Windows](#UWPConvert)

- [Ulepszenia debugowania](#Debug462)

Aby uzyskać listę nowych interfejsów API dodanych do platformy .NET Framework 4.6.2, zobacz [.NET Framework 4.6.2 Zmiany interfejsu API](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) w usłudze GitHub. Aby uzyskać listę ulepszeń funkcji i poprawek błędów w programie .NET Framework 4.6.2, zobacz [.NET Framework 4.6.2 Lista zmian](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) w usłudze GitHub. Aby uzyskać więcej informacji, zobacz [Ogłaszanie programu .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) w blogu platformy .NET.

<a name="ASPNET462" />

### <a name="aspnet"></a>ASP.NET

W programie .NET Framework 4.6.2 ASP.NET zawiera następujące ulepszenia:

**Ulepszona obsługa zlokalizowanych komunikatów o błędach w walidatorach adnotacji danych**

Walidatory adnotacji danych umożliwiają wykonywanie sprawdzania poprawności przez dodanie jednego lub więcej atrybutów do właściwości klasy. Element atrybutu <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> definiuje tekst komunikatu o błędzie, jeśli sprawdzanie poprawności nie powiedzie się. Począwszy od programu .NET Framework 4.6.2, ASP.NET ułatwia lokalizowanie komunikatów o błędach. Komunikaty o błędach zostaną zlokalizowane, jeśli:

1. Jest <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> to zawarte w atrybucie sprawdzania poprawności.

2. Plik zasobu jest przechowywany w folderze App_LocalResources.

3. Nazwa zlokalizowanego pliku zasobów ma `DataAnnotation.Localization.{` *nazwę*`}.resx`formularza , gdzie *nazwa* jest nazwą kultury w *formacie languageCode*`-`*kraj/regionKoduj* lub *languageCode*.

4. Nazwa klucza zasobu jest ciągiem <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> przypisanym do atrybutu, a jego wartością jest zlokalizowany komunikat o błędzie.

Na przykład następujący atrybut adnotacji danych definiuje domyślny komunikat o błędzie kultury dla nieprawidłowej klasyfikacji.

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

Następnie można utworzyć plik zasobu DataAnnotation.Localization.fr.resx, którego kluczem jest ciąg komunikatu o błędzie i którego wartość jest zlokalizowanym komunikatem o błędzie. Plik musi znajdować się `App.LocalResources` w folderze. Na przykład poniżej znajduje się klucz i jego wartość w zlokalizowanym komunikacie o błędzie języka francuskiego (fr):

| Nazwa                                 | Wartość                                     |
| ------------------------------------ | ----------------------------------------- |
| Ocena musi wynosić od 1 do 10. | La note doit être obejmują entre 1 i 10. |

 Ponadto lokalizacja adnotacji danych jest rozszerzalna. Deweloperzy mogą podłączyć własnego dostawcę localizer ciąg implementując <xref:System.Web.Globalization.IStringLocalizerProvider> interfejs do przechowywania ciąg lokalizacji gdzieś inne niż w pliku zasobów.

 **Pomoc techniczna asynchroniczna u dostawców sklepu w stanie sesji**

 ASP.NET teraz umożliwia metody zwracania zadań, które mają być używane z dostawcami magazynu stanu sesji, umożliwiając w ten sposób aplikacjom ASP.NET uzyskanie korzyści skalowalności asynchronii. Aby obsługuje operacje asynchroniczne z dostawcami magazynu stanu sesji, ASP.NET zawiera nowy interfejs, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>który dziedziczy <xref:System.Web.IHttpModule> i umożliwia deweloperom implementowanie własnego modułu stanu sesji i dostawców magazynu sesji asynchronicznej. Interfejs jest zdefiniowany w następujący sposób:

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

```vb
Public Interface ISessionStateModule : Inherits IHttpModule
   Sub ReleaseSessionState(context As HttpContext)
   Function ReleaseSessionStateAsync(context As HttpContext) As Task
End Interface
```

 Ponadto <xref:System.Web.SessionState.SessionStateUtility> klasa zawiera dwie nowe <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> metody <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>i , które mogą być używane do obsługi operacji asynchronicznych.

 **Obsługa asynchronii dla dostawców pamięci podręcznej danych wyjściowych**

 Począwszy od programu .NET Framework 4.6.2, metody zwracania zadań mogą być używane z dostawcami pamięci podręcznej wyjściowej, aby zapewnić korzyści skalowalności asynchronii.  Dostawcy, którzy implementują te metody zmniejszyć blokowanie wątków na serwerze sieci web i zwiększyć skalowalność usługi ASP.NET.

 Następujące interfejsy API zostały dodane do obsługi asynchronicznych dostawców pamięci podręcznej danych wyjściowych:

- Klasa, <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> która dziedziczy <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> i umożliwia deweloperom zaimplementowanie asynchronimii dostawcy pamięci podręcznej danych wyjściowych.

- Klasa, <xref:System.Web.Caching.OutputCacheUtility> która udostępnia metody pomocnicze konfigurowania pamięci podręcznej danych wyjściowych.

- 18 nowych metod <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> w klasie. Należą <xref:System.Web.HttpCachePolicy.GetCacheability%2A>do <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A> <xref:System.Web.HttpCachePolicy.GetETag%2A>nich <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A> <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A> <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>, , , , , , , i .

- 2 nowe metody <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> w <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>klasie: i .

- 2 nowe metody <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> w <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>klasie: i .

- 2 nowe metody <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> w <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>klasie: i .

- W <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> klasie <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> metoda.

- W <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metoda.

<a name="Strings" />

### <a name="character-categories"></a>Kategorie znaków

Znaki w programie .NET Framework 4.6.2 są klasyfikowane na podstawie [standardu Unicode, wersja 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). W programie .NET Framework 4.6 i .NET Framework 4.6.1 znaki zostały sklasyfikowane na podstawie kategorii znaków Unicode 6.3.

Obsługa unicode 8.0 jest ograniczona do klasyfikacji <xref:System.Globalization.CharUnicodeInfo> znaków według klasy i typów i metod, które opierają się na nim. Należą do <xref:System.Globalization.StringInfo> nich klasa, <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> przeciążona metoda i [klasy znaków rozpoznawane](../../standard/base-types/character-classes-in-regular-expressions.md) przez aparat wyrażeń regularnych programu .NET Framework.  Porównanie i sortowanie znaków i ciągów nie ma wpływu na tę zmianę i nadal polega na podstawowym systemie operacyjnym lub, w systemach Windows 7, na danych znaków dostarczonych przez program .NET Framework.

Aby uzyskać informacje na zmiany w kategoriach znaków z Unicode 6.0 na Unicode 7.0, zobacz [Standard Unicode, wersja 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) w witrynie konsorcjum Unicode. Zmiany z Unicode 7.0 na Unicode 8.0 można znaleźć w [standardzie Unicode w wersji 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) na stronie internetowej Konsorcjum Unicode.

<a name="Crypto462" />

### <a name="cryptography"></a>Kryptografia

**Obsługa certyfikatów X509 zawierających FIPS 186-3 DSA**

Program .NET Framework 4.6.2 dodaje obsługę certyfikatów DSA (Digital Signature Algorithm) X509, których klucze przekraczają limit FIPS 186-2 1024-bitowy.

Oprócz obsługi większych rozmiarów kluczy FIPS 186-3, .NET Framework 4.6.2 umożliwia obliczanie podpisów z rodziny algorytmów mieszania SHA-2 (SHA256, SHA384 i SHA512). Obsługa FIPS 186-3 jest <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> świadczona przez nową klasę.

Zgodnie z ostatnich zmian <xref:System.Security.Cryptography.RSA> w klasie w .NET Framework <xref:System.Security.Cryptography.ECDsa> 4.6 i klasy w .NET <xref:System.Security.Cryptography.DSA> Framework 4.6.1, abstrakcyjna klasa podstawowa w .NET Framework 4.6.2 ma dodatkowe metody, aby umożliwić wywołującym korzystanie z tej funkcji bez rzutowania. Można wywołać <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> metodę rozszerzenia, aby podpisać dane, jak pokazano w poniższym przykładzie.

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

I można wywołać metodę rozszerzenia, <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> aby zweryfikować podpisane dane, jak pokazano w poniższym przykładzie.

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

**Zwiększona przejrzystość wprowadzania do procedur wyprowadzania klucza ECDiffieHellman**

.NET Framework 3.5 dodał obsługę umowy klucza Elliptic Curve Diffie-Hellman z trzema różnymi procedurami funkcji wyprowadzania klucza (KDF). Dane wejściowe do procedur i same procedury zostały skonfigurowane za <xref:System.Security.Cryptography.ECDiffieHellmanCng> pomocą właściwości obiektu. Ale ponieważ nie każda rutynowa czytać każdą właściwość wejściowej, było dużo miejsca na zamieszanie w przeszłości dewelopera.

Aby rozwiązać ten problem w .NET Framework 4.6.2, do <xref:System.Security.Cryptography.ECDiffieHellman> klasy podstawowej dodano następujące trzy metody, aby wyraźniej reprezentować te procedury KDF i ich dane wejściowe:

|Metoda ECDiffieHellman|Opis|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Wyprowadza materiał klucza przy użyciu formuły<br /><br /> HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HASH(secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> gdzie *x* jest obliczonym wynikiem algorytmu EC Diffie-Hellman.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Wyprowadza materiał klucza przy użyciu formuły<br /><br /> HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> gdzie *x* jest obliczonym wynikiem algorytmu EC Diffie-Hellman.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Wyprowadza materiał klucza przy użyciu algorytmu wyprowadzania funkcji pseudolosowych TLS (PRF).|

**Obsługa szyfrowania symetrycznego z funkcją utrwalonych kluczy**

Biblioteka kryptografii systemu Windows (CNG) dodała obsługę przechowywania utrwalonych kluczy symetrycznych i używania kluczy symetrycznych przechowywanych sprzętowo, a program .NET Framework 4.6.2 umożliwił deweloperom korzystanie z tej funkcji.  Ponieważ pojęcie kluczowych nazw i kluczowych dostawców jest specyficzne dla implementacji, korzystanie z tej funkcji wymaga wykorzystania konstruktora typów implementacji betonu zamiast preferowanego podejścia fabrycznego (takiego jak wywoływanie). `Aes.Create`

Obsługa szyfrowania symetrycznego z funkcją utrwalone klucze istnieje dla algorytmów AES (<xref:System.Security.Cryptography.AesCng>) i 3DES (<xref:System.Security.Cryptography.TripleDESCng>). Przykład:

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

**Obsługa protokołu SignedXml dla mieszania SHA-2**

.NET Framework 4.6.2 dodaje <xref:System.Security.Cryptography.Xml.SignedXml> obsługę do klasy dla RSA-SHA256, RSA-SHA384 i RSA-SHA512 PKCS # 1 metody podpisu i SHA256, SHA384 i SHA512 odwołania metody trawienia.

Stałe URI są widoczne <xref:System.Security.Cryptography.Xml.SignedXml>na:

|Pole SignedXml|Stały|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Wszystkie programy, które zarejestrowały <xref:System.Security.Cryptography.SignatureDescription> <xref:System.Security.Cryptography.CryptoConfig> niestandardowy program obsługi w celu dodania obsługi tych algorytmów będą nadal działać tak <xref:System.Security.Cryptography.CryptoConfig> jak w przeszłości, ale ponieważ są teraz domyślne platformy, rejestracja nie jest już konieczna.

<a name="SQLClient" />

### <a name="sqlclient"></a>Sqlclient

Dostawca danych programu .NET<xref:System.Data.SqlClient?displayProperty=nameWithType>Framework dla programu SQL Server ( ) zawiera następujące nowe funkcje w programie .NET Framework 4.6.2:

**Buforowanie połączeń i limity czasu z bazami danych SQL platformy Azure**

Gdy buforowanie połączenia jest włączone i występuje limit czasu lub inny błąd logowania, wyjątek jest buforowany, a buforowany wyjątek jest zgłaszany przy każdej kolejnej próbie połączenia przez następne 5 sekund do 1 minuty. Aby uzyskać więcej informacji, zobacz [Sql Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).

To zachowanie nie jest pożądane podczas łączenia się z bazy danych SQL azure, ponieważ próby połączenia może zakończyć się niepowodzeniem z błędami przejściowymi, które są zazwyczaj szybko odzyskane. Aby lepiej zoptymalizować proces ponawiania połączeń, zachowanie okresu blokowania puli połączeń jest usuwane, gdy połączenia z bazami danych SQL platformy Azure nie powiodą się.

Dodanie nowego `PoolBlockingPeriod` słowa kluczowego pozwala wybrać okres blokowania najlepiej dopasowany do twojej aplikacji. Wartości są następujące:

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

Okres blokowania puli połączeń dla aplikacji, która łączy się z usługą Azure SQL Database jest wyłączona, a okres blokowania puli połączeń dla aplikacji, która łączy się z innym wystąpieniem programu SQL Server jest włączony. Jest to wartość domyślna. Jeśli nazwa punktu końcowego serwera kończy się dowolną z następujących czynności, są one uważane za bazy danych SQL azure:

- database.windows.net .database.windows.net

- database.chinacloudapi.cn .

- database.usgovcloudapi.net .database.usgovcloudapi.net

- database.cloudapi.de .database.cloudapi.de

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

Okres blokowania puli połączeń jest zawsze włączony.

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

Okres blokowania puli połączeń jest zawsze wyłączony.

**Ulepszenia zawsze szyfrowane**

SQLClient wprowadza dwa ulepszenia dla zawsze zaszyfrowane:

- Aby zwiększyć wydajność sparametryzowanych zapytań względem zaszyfrowanych kolumn bazy danych, metadane szyfrowania parametrów kwerendy są teraz buforowane. Z <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> właściwością `true` ustawioną na (która jest wartością domyślną), jeśli ta sama kwerenda jest wywoływana wiele razy, klient pobiera metadane parametrów z serwera tylko raz.

- Wpisy klucza szyfrowania kolumn w pamięci podręcznej kluczy są <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> teraz eksmitowane po konfigurowalnym przedziale czasu, ustawionym przy użyciu właściwości.

<a name="WCF" />

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

W programie .NET Framework 4.6.2 program Windows Communication Foundation został rozszerzony w następujących obszarach:

**Obsługa zabezpieczeń transportu WCF dla certyfikatów przechowywanych przy użyciu CNG**

Zabezpieczenia transportu WCF obsługują certyfikaty przechowywane przy użyciu biblioteki kryptografii systemu Windows (CNG). W .NET Framework 4.6.2 ta obsługa jest ograniczona do korzystania z certyfikatów z kluczem publicznym, który ma wykładnik nie więcej niż 32 bitów długości. Gdy aplikacja jest przeznaczona dla programu .NET Framework 4.6.2, ta funkcja jest domyślnie włączona.

W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.6.1 i wcześniejszych, ale działających w programie .NET Framework 4.6.2 tę funkcję można włączyć, dodając następujący wiersz do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku app.config lub web.config.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

Można to również zrobić programowo z kodem, jak poniżej:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

**Lepsza obsługa wielu reguł regulacji czasu letniego przez klasę DataContractJsonSerializer**

Klienci mogą użyć ustawienia konfiguracji aplikacji, aby ustalić, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> czy klasa obsługuje wiele reguł dopasowania dla jednej strefy czasowej. Jest to funkcja opt-in. Aby ją włączyć, dodaj następujące ustawienie do pliku app.config:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Gdy ta funkcja jest <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> włączona, <xref:System.TimeZoneInfo> obiekt używa typu <xref:System.TimeZone> zamiast typu do deserializacji danych daty i godziny. <xref:System.TimeZoneInfo>obsługuje wiele reguł dostosowawczych, co umożliwia pracę z historycznymi danymi strefy czasowej;   <xref:System.TimeZone> nie.

Aby uzyskać więcej <xref:System.TimeZoneInfo> informacji na temat zmian struktury i strefy czasowej, zobacz [Omówienie strefy czasowej](../../standard/datetime/time-zone-overview.md).

**NetNamedPipeBinding najlepsze dopasowanie**

WCF ma nowe ustawienie aplikacji, które można ustawić w aplikacjach klienckich, aby upewnić się, że zawsze łączą się z usługą nasłuchiwania identyfikatora URI, która najlepiej pasuje do tego, który żądają. Z tego ustawienia `false` aplikacji ustawiona na (domyślnie), jest możliwe dla klientów korzystających <xref:System.ServiceModel.NetNamedPipeBinding> do próby połączenia się z usługą nasłuchiwania na identyfikatorze URI, który jest podciąg żądanego identyfikatora URI.

Na przykład klient próbuje połączyć się `net.pipe://localhost/Service1`z usługą nasłuchującą w programie , `net.pipe://localhost`ale inna usługa na tym komputerze z uprawnieniami administratora nasłuchuje w programie . Przy tym ustawieniu `false`aplikacji ustawiona na , klient będzie próbował połączyć się z niewłaściwą usługą. Po ustawieniu ustawienia `true`aplikacji klient zawsze połączy się z najlepiej dopasowaną usługą.

> [!NOTE]
> Klienci <xref:System.ServiceModel.NetNamedPipeBinding> korzystający z usług find na podstawie adresu podstawowego usługi (jeśli istnieje), a nie pełnego adresu punktu końcowego. Aby upewnić się, że to ustawienie zawsze działa, usługa powinna używać unikatowego adresu podstawowego.

Aby włączyć tę zmianę, dodaj następujące ustawienie aplikacji do pliku App.config lub Web.config aplikacji klienckiej:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

**Protokół SSL 3.0 nie jest protokołem domyślnym**

W przypadku korzystania z protokołu NetTcp z zabezpieczeniami transportu i certyfikatem typu poświadczeń protokół SSL 3.0 nie jest już domyślnym protokołem używanym do negocjowania bezpiecznego połączenia. W większości przypadków nie powinno mieć wpływu na istniejące aplikacje, ponieważ protokół TLS 1.0 znajduje się na liście protokołów dla protokołu NetTcp. Wszyscy istniejący klienci powinni mieć możliwość negocjowania połączenia przy użyciu co najmniej protokołu TLS 1.0. Jeśli wymagany jest protokół Ssl3, użyj jednego z następujących mechanizmów konfiguracji, aby dodać go do listy wynegocjowanych protokołów.

- Właściwość <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType>

- Właściwość <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType>

- Sekcja [ \<>transportu](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) sekcji [ \<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)

- Sekcja [ \<>sslStreamSecurity](../configure-apps/file-schema/wcf/sslstreamsecurity.md) sekcji [ \<customBinding>](../configure-apps/file-schema/wcf/custombinding.md)

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

W programie .NET Framework 4.6.2 program Windows Presentation Foundation został rozszerzony w następujących obszarach:

**Sortowanie grup**

Aplikacja, która używa <xref:System.Windows.Data.CollectionView> obiektu do grupowania danych można teraz jawnie zadeklarować sposób sortowania grup. Jawne sortowanie rozwiązuje problem nieutule dyskusyjnego zamawiania, który występuje, gdy aplikacja dynamicznie dodaje lub usuwa grupy lub gdy zmienia wartość właściwości elementu zaangażowanych w grupowanie. Może również poprawić wydajność procesu tworzenia grupy, przenosząc porównania właściwości grupowania z rodzaju pełnej kolekcji do rodzaju grup.

Aby obsługiwać sortowanie <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> grup, nowe i <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> właściwości opisują sposób <xref:System.ComponentModel.GroupDescription> sortowania kolekcji grup produkowanych przez obiekt. Jest to analogiczne do sposobu, <xref:System.Windows.Data.ListCollectionView> w jaki właściwości o identycznej nazwie opisują sposób sortowania elementów danych.

Dwie nowe właściwości statyczne <xref:System.Windows.Data.PropertyGroupDescription> klasy <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>i , mogą być używane dla najczęstszych przypadków.

Na przykład następujące grupy XAML grup danych według wieku, sortować grupy wiekowe w porządku rosnącym i grupować elementy w każdej grupie wiekowej według nazwiska.

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

**Obsługa klawiatury dotykowej**

Obsługa klawiatury dotykowej umożliwia śledzenie ostrości w aplikacjach WPF, automatycznie wywołując i odrzucając klawiaturę dotykową w systemie Windows 10 po odebraniu wprowadzania dotykowego przez formant, który może przyjmować wprowadzanie tekstu.

W poprzednich wersjach programu .NET Framework aplikacje WPF nie mogą zdecydować się na śledzenie fokusu bez wyłączania obsługi gestów pióra/dotyku WPF. W rezultacie aplikacje WPF musi wybrać między pełną obsługą dotykową WPF lub polegać na promocji myszy systemu Windows.

**Dpi na monitor**

Aby obsługiwać niedawne rozprzestrzenianie środowisk o wysokiej rozdzielczości i hybrydowej rozdzielczości DPI dla aplikacji WPF, WPF WPF w programie .NET Framework 4.6.2 umożliwia rozpoznawanie na monitorze. Zobacz [przykłady i przewodnik dla deweloperów](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) w usłudze GitHub, aby uzyskać więcej informacji na temat sposobu włączania aplikacji WPF, aby stać się na monitorze DPI.

W poprzednich wersjach programu .NET Framework aplikacje WPF są system-DPI aware. Innymi słowy interfejsu użytkownika aplikacji jest skalowany przez system operacyjny, w zależności od DPI monitora, na którym aplikacja jest renderowana.

W przypadku aplikacji działających w ramach programu .NET Framework 4.6.2 można wyłączyć zmiany dpi na monitorze w aplikacjach WPF, dodając instrukcję konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji w następujący sposób:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a>Program Windows Workflow Foundation (WF)

W programie .NET Framework 4.6.2 program Windows Workflow Foundation został rozszerzony w następującym obszarze:

**Obsługa wyrażeń języka C# i IntelliSense w rehosted WF Designer**

Począwszy od programu .NET Framework 4.5, WF obsługuje wyrażenia języka C# w programie Visual Studio Designer i w przepływach pracy kodu. Rehosted Workflow Designer jest kluczową funkcją WF, która pozwala na Projektant przepływu pracy, aby być w aplikacji poza Visual Studio (na przykład w WPF).  Windows Workflow Foundation zapewnia możliwość obsługi wyrażeń języka C# i IntelliSense w Rehosted Workflow Designer. Aby uzyskać więcej informacji, zobacz [blog programu Windows Workflow Foundation](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).

`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`W wersjach programu .NET Framework przed 4.6.2 Program WF Designer IntelliSense jest uszkodzony, gdy klient odbudowuje projekt przepływu pracy z programu Visual Studio. Gdy kompilacja projektu zakończy się pomyślnie, typy przepływu pracy nie znajdują się w projektancie, a ostrzeżenia intellisense dla brakujących typów przepływu pracy są wyświetlane w oknie **Lista błędów.** .NET Framework 4.6.2 rozwiązuje ten problem i udostępnia rozwiązanie IntelliSense.

**Aplikacje przepływu pracy V1 z śledzeniem przepływu pracy są teraz uruchamiane w trybie FIPS**

Maszyny z włączonym trybem zgodności FIPS mogą teraz pomyślnie uruchomić aplikację w stylu przepływu pracy w wersji 1 z włączonym śledzeniem przepływu pracy. Aby włączyć ten scenariusz, należy wprowadzić następujące zmiany w pliku app.config:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

Jeśli ten scenariusz nie jest włączony, uruchomienie aplikacji kontynuuje generowanie wyjątku z komunikatem "Ta implementacja nie jest częścią algorytmów kryptograficznych zweryfikowanych przez platformę Windows FIPS".

**Ulepszenia przepływu pracy podczas korzystania z aktualizacji dynamicznej w programie Visual Studio Workflow Designer**

Projektant przepływu pracy, Projektant działań schematu blokowego i inni projektanci działań przepływu pracy pomyślnie <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> ładują i wyświetlają przepływy pracy, które zostały zapisane po wywołaniu tej metody. W wersjach programu .NET Framework przed programem .NET Framework 4.6.2 ładowanie pliku XAML <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> w programie Visual Studio dla przepływu pracy, który został zapisany po wywołaniu, może spowodować następujące problemy:

- Projektant przepływu pracy nie może poprawnie załadować pliku <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> XAML (gdy znajduje się na końcu wiersza).

- Projektant działań schematu blokowego lub inni projektanci działań przepływu pracy mogą wyświetlać wszystkie obiekty w ich domyślnych lokalizacjach, w przeciwieństwie do dołączonych wartości właściwości.

<a name="clickonce-1" />

### <a name="clickonce"></a>ClickOnce

ClickOnce został zaktualizowany do obsługi TLS 1.1 i TLS 1.2 oprócz protokołu 1.0, który już obsługuje. ClickOnce automatycznie wykrywa, który protokół jest wymagany; nie dodatkowe kroki w aplikacji ClickOnce są wymagane, aby włączyć TLS 1.1 i 1.2 wsparcia.

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Konwertowanie aplikacji Formularze systemu Windows i WPF WPF na aplikacje platformy uniwersalnej systemu Windows

System Windows oferuje teraz możliwości przesuń istniejące aplikacje klasyczne systemu Windows, w tym aplikacje WPF i Windows Forms, na platformę uniwersalną systemu Windows (UWP). Ta technologia działa jako mostek, umożliwiając stopniową migrację istniejącej bazy kodu do platformy uniwersalnej systemu Windows, dzięki czemu aplikacja jest przewożona do wszystkich urządzeń z systemem Windows 10.

Przekonwertowane aplikacje klasyczne uzyskują tożsamość aplikacji podobną do tożsamości aplikacji platformy uniwersalnej systemu Windows, co sprawia, że interfejsy API platformy uniwersalnej systemu Windows są dostępne, aby włączyć funkcje, takie jak dynamiczne kafelki i powiadomienia. Aplikacja nadal zachowuje się jak wcześniej i działa jako aplikacja pełnego zaufania. Po przekonwertowaniu aplikacji proces kontenera aplikacji można dodać do istniejącego procesu pełnego zaufania, aby dodać adaptacyjny interfejs użytkownika. Po przeniesieniu wszystkich funkcji do procesu kontenera aplikacji można usunąć pełny proces zaufania, a nową aplikację platformy uniwersalnej systemu Windows można udostępnić wszystkim urządzeniom z systemem Windows 10.

<a name="Debug462" />

### <a name="debugging-improvements"></a>Ulepszenia debugowania

*Niezarządzanego interfejsu API debugowania* został rozszerzony w .NET Framework 4.6.2 do wykonywania dodatkowych analiz, gdy <xref:System.NullReferenceException> jest generowany tak, że jest możliwe określenie, która zmienna w jednym wierszu kodu źródłowego jest `null`.   Aby obsługiwać ten scenariusz, następujące interfejsy API zostały dodane do niezarządzanego interfejsu API debugowania.

- [Interfejsy ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)i [ICorDebugVariableHomeEnum,](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) które ujawniają macierzyste domy zmiennych zarządzanych. Dzięki temu debugery do niektórych <xref:System.NullReferenceException> analizy przepływu kodu, gdy występuje i do pracy wstecz, aby `null`określić zmienną zarządzaną, która odpowiada lokalizacji macierzystej, która była .

- [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metoda zapewnia mapowanie dla ICorDebugType [do COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), który umożliwia debugera, aby uzyskać [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) bez wystąpienia ICorDebugType. Istniejące interfejsy API na [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) mogą następnie służyć do określenia układu klasy typu.

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a>Co nowego w .NET Framework 4.6.1

Program .NET Framework 4.6.1 zawiera nowe funkcje w następujących obszarach:

- [Kryptografia](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profilowanie](#Profile461)

- [Ngen](#NGEN461)

Aby uzyskać więcej informacji na temat programu .NET Framework 4.6.1, zobacz następujące tematy:

- [.NET Framework 4.6.1 lista zmian](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [Zgodność aplikacji w 4.6.1](../migration-guide/application-compatibility.md)

- [Diff interfejsu API programu .NET Framework](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (w usłudze GitHub)

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Kryptografia: Obsługa certyfikatów X509 zawierających ECDSA

.NET Framework 4.6 dodał obsługę RSACng dla certyfikatów X509. Program .NET Framework 4.6.1 dodaje obsługę certyfikatów X509 ECDSA (Elliptic Curve Digital Signature Algorithm).

ECDSA oferuje lepszą wydajność i jest bezpieczniejszym algorytmem kryptograficznym niż RSA, zapewniając doskonały wybór, w którym wydajność i skalowalność zabezpieczeń warstwy transportowej (TLS) są problemem. Implementacja platformy .NET Framework zawija wywołania do istniejących funkcji systemu Windows.

Poniższy przykładowy kod pokazuje, jak łatwo jest wygenerować podpis dla strumienia bajtów przy użyciu nowej obsługi certyfikatów ECDSA X509 zawartych w .NET Framework 4.6.1.

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

Zapewnia to wyraźny kontrast do kodu potrzebnego do wygenerowania podpisu w .NET Framework 4.6.

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a>ADO.NET

Do ADO.NET dodano następujące elementy:

**Zawsze szyfrowana obsługa kluczy chronionych sprzętowo**

ADO.NET obsługuje teraz przechowywanie zawsze zaszyfrowanych kluczy głównych kolumn natywnie w sprzętowych modułach zabezpieczeń (HSM). Dzięki tej obsłudze klienci mogą korzystać z kluczy asymetrycznych przechowywanych w modułach HSM bez konieczności pisania dostawców magazynu kluczy głównych kolumn niestandardowych i rejestrowania ich w aplikacjach.

Klienci muszą zainstalować dostawcę CSP dostarczonego przez dostawcę usług kryptograficznych dostarczonego przez dostawcę usług HSM lub dostawców magazynu kluczy CNG na serwerach aplikacji lub komputerach klienckich, aby uzyskać dostęp do zawsze zaszyfrowanych danych chronionych kluczami głównymi kolumn przechowywanymi w pliku HSM.

**Ulepszone <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> zachowanie połączenia dla AlwaysOn**

SqlClient teraz automatycznie zapewnia szybsze połączenia z AlwaysOn Availability Group (AG). W sposób przejrzysty wykrywa, czy aplikacja łączy się z grupą dostępności AlwaysOn (AG) w innej podsieci i szybko odnajduje bieżący aktywny serwer i zapewnia połączenie z serwerem. Przed tą wersją aplikacja musiała ustawić parametry `"MultisubnetFailover=true"` połączenia, aby uwzględnić, aby wskazać, że łączy się z grupą dostępności AlwaysOn. Bez ustawiania słowa `true`kluczowego połączenia na , aplikacja może wystąpić limit czasu podczas łączenia się z grupą dostępności AlwaysOn. W tej wersji aplikacja *nie* musi <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> `true` już być ustawiona. Aby uzyskać więcej informacji na temat obsługi sqlclient dla grup dostępności zawsze włączone, zobacz [Obsługa SqlClient dla wysokiej dostępności, odzyskiwanie po awarii](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Program Windows Presentation Foundation zawiera szereg ulepszeń i zmian.

**Większa wydajność**

Opóźnienie w wypalaniu zdarzeń dotykowych zostało naprawione w .NET Framework 4.6.1. Ponadto wpisanie formantu <xref:System.Windows.Controls.RichTextBox> nie powoduje już powiązania wątku renderowania podczas szybkiego wprowadzania danych wejściowych.

**Ulepszenia sprawdzania pisowni**

Moduł sprawdzania pisowni w WPF został zaktualizowany w systemie Windows 8.1 i nowszych wersjach, aby wykorzystać obsługę systemu operacyjnego do sprawdzania pisowni dodatkowych języków.  Nie ma żadnych zmian w funkcjonalności w wersjach systemu Windows przed Windows 8.1.

Podobnie jak w poprzednich wersjach programu .NET Framework, język bloku <xref:System.Windows.Controls.TextBox> formantu ora <xref:System.Windows.Controls.RichTextBox> jest wykrywany przez wyszukując informacje w następującej kolejności:

- `xml:lang`, jeśli jest obecny.

- Bieżący język wprowadzania.

- Bieżąca kultura wątku.

Aby uzyskać więcej informacji na temat obsługi języka w WPF, zobacz [wpis w blogu WPF na temat funkcji .NET Framework 4.6.1](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/).

**Dodatkowa obsługa słowników niestandardowych dla użytkowników**

W .NET Framework 4.6.1 WPF WPF rozpoznaje słowniki niestandardowe, które są rejestrowane globalnie. Ta funkcja jest dostępna oprócz możliwości rejestrowania ich na kontrolę.

W poprzednich wersjach WPF słowniki niestandardowe nie rozpoznawały wykluczonych słów i list Autokorekty. Są one obsługiwane w systemach Windows 8.1 i Windows 10 `%AppData%\Microsoft\Spelling\<language tag>` za pomocą plików, które można umieścić pod katalogiem.  Do tych plików mają zastosowanie następujące reguły:

- Pliki powinny mieć rozszerzenia .dic (dla dodanych słów), .exc (dla wykluczonych słów) lub .acl (dla Autokorekty).

- Pliki powinny być UTF-16 LE zwykły tekst, który rozpoczyna się od znaku zamówienia bajtów (BOM).

- Każdy wiersz powinien składać się ze słowa (na dodanych i wykluczonych list wyrazów) lub pary autokorekty ze słowami oddzielonymi pionowym paskiem ("&#124;") (na liście słów Autokorekty).

- Pliki te są uważane za tylko do odczytu i nie są modyfikowane przez system.

> [!NOTE]
> Te nowe formaty plików nie są bezpośrednio obsługiwane przez WPF sprawdzanie pisowni interfejsów API i słowniki niestandardowe dostarczane do WPF WPF w aplikacjach powinny nadal używać plików .lex.

**Samples**

Istnieje wiele przykładów WPF w repozytorium GitHub [Microsoft/WPF-Samples.](https://github.com/Microsoft/WPF-Samples) Pomóż nam ulepszyć nasze próbki, wysyłając nam prośbę o pobranie lub otwierając [problem z gitHubem.](https://github.com/Microsoft/WPF-Samples/issues)

**Rozszerzenia DirectX**

WPF WPF zawiera [pakiet NuGet,](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) który zapewnia nowe <xref:System.Windows.Interop.D3DImage> implementacje, które ułatwiają współdziałanie z DX10 i Dx11 zawartości. Kod dla tego pakietu został otwarty i jest dostępny [na GitHub](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a>Fundacja przepływu pracy systemu Windows: transakcje

Metoda <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> może teraz używać menedżera transakcji rozproszonych innych niż MSDTC do promowania transakcji. Można to zrobić, określając identyfikator promotora transakcji <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> GUID do nowego przeciążenia . Jeśli ta operacja zakończy się pomyślnie, istnieją ograniczenia dotyczące możliwości transakcji. Po zarejestrowaniu promotora transakcji innych niż MSDTC <xref:System.Transactions.TransactionPromotionException> następujące metody zgłaszają, ponieważ te metody wymagają awansu do usługi MSDTC:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

Po zarejestrowaniu promotora transakcji innych niż MSDTC musi on być używany do przyszłych trwałych rejestracji przy użyciu protokołów, które definiuje. Organizator <xref:System.Guid> transakcji można uzyskać za pomocą <xref:System.Transactions.Transaction.PromoterType%2A> obiektu. Gdy transakcja promuje, promotor transakcji <xref:System.Byte> udostępnia tablicę, która reprezentuje token promowany. Aplikacja może uzyskać promowany token dla promowanej transakcji nie <xref:System.Transactions.Transaction.GetPromotedToken%2A> msdtc za pomocą metody.

Użytkownicy nowego <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> przeciążenia muszą przestrzegać określonej sekwencji wywołań, aby operacja promocji została pomyślnie ukończona. Reguły te są udokumentowane w dokumentacji metody.

<a name="Profile461" />

### <a name="profiling"></a>Profilowanie

Interfejs API profilowania bez mana został rozszerzony w następujący sposób:

- Lepsza obsługa dostępu do kontrolerów pdb w interfejsie [ICorProfilerInfo7.](../unmanaged-api/profiling/icorprofilerinfo7-interface.md)

  W ASP.NET Core, staje się coraz bardziej powszechne dla zestawów, które mają być kompilowane w pamięci przez Roslyn. Dla programistów tworzących narzędzia do profilowania oznacza to, że pdb, które historycznie były serializowane na dysku, mogą już nie być obecne. Narzędzia profilera często używają plików PDB do mapowania kodu z powrotem do wierszy źródłowych dla zadań, takich jak pokrycie kodu lub analiza wydajności wiersza po wierszu. Interfejs [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) zawiera teraz dwie nowe metody, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) i [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), aby zapewnić tym narzędziom profiler z dostępem do danych WDB w pamięci, Za pomocą nowych interfejsów API, profiler może uzyskać zawartość bazy danych WDB w pamięci jako tablicy bajtowej, a następnie przetwarzać go lub serializować na dysku.

- Lepsze oprzyrządowanie z interfejsem ICorProfiler.

  Profilerzy, które `ICorProfiler` korzystają z funkcji rejit interfejsów API dla instrumentacji dynamicznej można teraz zmodyfikować niektóre metadane. Wcześniej takie narzędzia mogły instrumentować IL w dowolnym momencie, ale metadane mogły być modyfikowane tylko w czasie ładowania modułu. Ponieważ IL odnosi się do metadanych, to ograniczone rodzaje instrumentacji, które można zrobić. Znieśliśmy niektóre z tych limitów, dodając metodę [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) do obsługi podzbioru edycji metadanych `TypeSpec` `MemberRef`po `MemberSpec`załadowaniu modułu, w szczególności przez dodanie nowych `UserString` `AssemblyRef`, `TypeRef`, , i rekordów. Ta zmiana sprawia, że znacznie szerszy zakres oprzyrządowania w locie jest możliwy.

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a>Natywne kontrolery PDB generatora obrazów (NGEN)

Śledzenie zdarzeń między komputerami umożliwia klientom profilowanie programu na komputerze A i przeglądanie danych profilowania z mapowaniem linii źródłowej na komputerze B. Przy użyciu poprzednich wersji programu .NET Framework użytkownik skopiowałby wszystkie moduły i obrazy natywne z profilowanego komputera do komputera analitycznego zawierającego bazę danych IL PDB w celu utworzenia mapowania źródłowego do natywnego. Chociaż ten proces może działać dobrze, gdy pliki są stosunkowo małe, na przykład dla aplikacji telefonicznych, pliki mogą być bardzo duże w systemach stacjonarnych i wymagają dużo czasu na kopiowanie.

Dzięki kontrolerom PDBs Ngen NGen można utworzyć bazę danych PDB zawierającą mapowanie IL-to-native bez zależności od bazy danych IL PDB. W naszym scenariuszu śledzenia zdarzeń między komputerami wszystko, co jest potrzebne, to skopiować natywnego obrazu PDB, który jest generowany przez komputer A do komputera B i użyć interfejsów API dostępu do [interfejsu debugowania](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) do odczytu mapowania źródła do IL PDB i mapowania IL-to-native obrazu PDB. Połączenie obu mapowań zapewnia mapowanie od źródła do natywnego. Ponieważ natywny obraz PDB jest znacznie mniejszy niż wszystkie moduły i obrazy natywne, proces kopiowania z maszyny A do maszyny B jest znacznie szybszy.

<a name="v46" />

## <a name="whats-new-in-net-2015"></a>Co nowego w .NET 2015

Program .NET 2015 wprowadza programy .NET Framework 4.6 i .NET Core. Niektóre nowe funkcje dotyczą obu i inne funkcje są specyficzne dla .NET Framework 4.6 lub .NET Core.

- **ASP.NET Core**

  Program .NET 2015 zawiera ASP.NET Core, która jest implementacją lean .NET do tworzenia nowoczesnych aplikacji opartych na chmurze. ASP.NET Core jest modułowy, dzięki czemu można uwzględnić tylko te funkcje, które są potrzebne w aplikacji. Może być hostowany w serwisach IIS lub hostowany samodzielnie w procesie niestandardowym i można uruchamiać aplikacje z różnymi wersjami programu .NET Framework na tym samym serwerze. Zawiera nowy system konfiguracji środowiska, który jest przeznaczony do wdrażania w chmurze.

  MVC, Web API i stron sieci Web są ujednolicone w jednej ramach o nazwie MVC 6. Tworzenie aplikacji ASP.NET Core za pomocą narzędzi w programie Visual Studio 2015 lub nowszym. Istniejące aplikacje będą działać na nowym programie .NET Framework; jednak do tworzenia aplikacji, która używa MVC 6 lub SignalR 3, należy użyć systemu projektu w programie Visual Studio 2015 lub nowszej.

  Aby uzyskać więcej informacji, zobacz [ASP.NET Core](/aspnet/core/).

- **Aktualizacje ASP.NET**

  - **Interfejs API oparty na zadaniach dla opróżniania odpowiedzi asynchronicznego**

    ASP.NET teraz zapewnia prosty interfejs API oparty na zadaniach dla opróżniania odpowiedzi asynchronicznego, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>który umożliwia asynchronicznie `async/await` opróżnianie odpowiedzi przy użyciu obsługi języka.

  - **Powiązanie modelu obsługuje metody zwracania zadań**

    W programie .NET Framework 4.5 ASP.NET dodał funkcję powiązanie modelu, która umożliwiła rozszerzalne podejście skoncentrowane na kodzie do operacji danych opartych na programie CRUD na stronach formularzy sieci Web i formantach użytkowników. System wiązania modelu <xref:System.Threading.Tasks.Task>obsługuje teraz metody wiązania modelu zwracającego. Ta funkcja umożliwia deweloperom formularzy sieci Web uzyskanie korzyści skalowalności asynchronii z łatwością systemu wiązania danych podczas korzystania z nowszych wersji ormów, w tym entity framework.

    Powiązanie modelu asynchronizowego jest kontrolowane przez ustawienie `aspnet:EnableAsyncModelBinding` konfiguracji.

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    W aplikacjach docelowych .NET Framework 4.6 `true`domyślnie . W aplikacjach działających w programie .NET Framework 4.6, które są `false` przeznaczone dla wcześniejszej wersji programu .NET Framework, jest to domyślnie. Można go włączyć, ustawiając ustawienie `true`konfiguracji na .

  - **Obsługa protokołu HTTP/2 (Windows 10)**

    [HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) to nowa wersja protokołu HTTP, która zapewnia znacznie lepsze wykorzystanie połączenia (mniej rund między klientem a serwerem), co powoduje mniejsze opóźnienie ładowania strony sieci web dla użytkowników.  Strony sieci Web (w przeciwieństwie do usług) najbardziej korzystają z protokołu HTTP/2, ponieważ protokół optymalizuje dla wielu artefaktów wymaganych w ramach jednego środowiska. Obsługa protokołu HTTP/2 została dodana do ASP.NET w .NET Framework 4.6. Ponieważ funkcje sieciowe istnieją w wielu warstwach, nowe funkcje były wymagane w systemie Windows, w iiS i w ASP.NET, aby włączyć protokół HTTP/2. Aby korzystać z protokołu HTTP/2 z ASP.NET, musisz być uruchomiony w systemie Windows 10.

    Protokół HTTP/2 jest również obsługiwany i domyślnie włączony dla aplikacji platformy uniwersalnej <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> systemu Windows (UWP) systemu Windows 10, które korzystają z interfejsu API.

    Aby zapewnić sposób korzystania z funkcji [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) w ASP.NET aplikacji, do <xref:System.Web.HttpResponse.PushPromise%28System.String%29> <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29> <xref:System.Web.HttpResponse> klasy dodano nową metodę z dwoma przeciążeniami i ,.

    > [!NOTE]
    > Chociaż ASP.NET Core obsługuje http/2, obsługa funkcji PUSH PROMISE nie została jeszcze dodana.

    Przeglądarka i serwer www (IIS w systemie Windows) wykonują całą pracę. Nie musisz robić żadnych ciężkich podnoszenia dla użytkowników.

    Większość [głównych przeglądarek obsługuje protokół HTTP/2,](https://www.wikipedia.org/wiki/HTTP/2)więc jest prawdopodobne, że użytkownicy będą korzystać z obsługi PROTOKOŁU HTTP/2, jeśli serwer ją obsługuje.

  - **Obsługa protokołu wiązania tokenu**

    Firmy Microsoft i Google współpracują nad nowym podejściem do uwierzytelniania, zwanym [protokołem powiązania tokenów.](https://github.com/TokenBinding/Internet-Drafts) Założenie jest takie, że tokeny uwierzytelniania (w pamięci podręcznej przeglądarki) mogą zostać skradzione i wykorzystane przez przestępców do uzyskiwania dostępu do innych bezpiecznych zasobów (na przykład konta bankowego) bez konieczności posiadania hasła lub innej uprzywilejowanej wiedzy. Nowy protokół ma na celu złagodzenie tego problemu.

    Protokół wiązania tokenu zostanie zaimplementowany w systemie Windows 10 jako funkcja przeglądarki. ASP.NET aplikacje będą uczestniczyć w protokole, dzięki czemu tokeny uwierzytelniania są sprawdzane jako prawidłowe. Implementacje klienta i serwera ustanawiają kompleksową ochronę określoną przez protokół.

  - **Randomizowane algorytmy mieszania ciągów**

    Program .NET Framework 4.5 wprowadził [randomizowanym algorytmem mieszania ciągów](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Jednak nie był obsługiwany przez ASP.NET z powodu niektórych funkcji ASP.NET zależało od stabilnego kodu mieszania. W .NET Framework 4.6 obsługiwane są teraz losowo algorytmy mieszania ciągów. Aby włączyć tę funkcję, użyj ustawienia `aspnet:UseRandomizedStringHashAlgorithm` konfiguracji.

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- **ADO.NET**

  ADO .NET obsługuje teraz funkcję Zawsze szyfrowana dostępną w programie SQL Server 2016 Community Technology Preview 2 (CTP2). Dzięki zawsze zaszyfrowanemu program SQL Server może wykonywać operacje na zaszyfrowanych danych, a najlepszy klucz szyfrowania znajduje się w aplikacji w zaufanym środowisku klienta, a nie na serwerze. Zawsze zaszyfrowane zabezpiecza dane klienta, więc administratorzy nie mają dostępu do danych zwykłego tekstu. Szyfrowanie i odszyfrowywanie danych odbywa się w sposób przejrzysty na poziomie sterownika, minimalizując zmiany, które należy wywężone w istniejących aplikacjach. Aby uzyskać szczegółowe informacje, zobacz [Zawsze szyfrowane (Aparat baz danych)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) i [Zawsze szyfrowane (tworzenie klienta)](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **64-bitowy kompilator JIT dla kodu zarządzanego**

  .NET Framework 4.6 zawiera nową wersję 64-bitowego kompilatora JIT (pierwotnie o nazwie kodowej RyuJIT). Nowy kompilator 64-bitowy zapewnia znaczną poprawę wydajności w stosunku do starszego 64-bitowego kompilatora JIT. Nowy kompilator 64-bitowy jest włączony dla procesów 64-bitowych uruchomionych na dodatek .NET Framework 4.6. Aplikacja będzie działać w procesie 64-bitowym, jeśli jest skompilowany jako 64-bitowy lub AnyCPU i jest uruchomiony w 64-bitowym systemie operacyjnym. Chociaż dołożono starań, aby przejście do nowego kompilatora było tak przejrzyste, jak to możliwe, możliwe są zmiany w zachowaniu.

  Nowy 64-bitowy kompilator JIT zawiera również sprzętowe funkcje przyspieszania SIMD w połączeniu z typami obsługującymi kartę SIMD w obszarze <xref:System.Numerics> nazw, co może przynieść dobrą poprawę wydajności.

- **Ulepszenia ładowarki montażowej**

  Moduł ładujący zestaw wykorzystuje teraz bardziej efektywnie używa pamięci, zwalniając zestawy IL po załadowaniu odpowiedniego obrazu NGEN. Ta zmiana zmniejsza pamięć wirtualną, co jest szczególnie korzystne dla dużych aplikacji 32-bitowych (takich jak Visual Studio), a także oszczędza pamięć fizyczną.

- **Zmiany w bibliotece klas podstawowych**

  Wiele nowych interfejsów API zostały dodane wokół do platformy .NET Framework 4.6, aby włączyć kluczowe scenariusze. Należą do nich następujące zmiany i uzupełnienia:

  - **Implementacje> IReadOnlyCollection\<T**

    Dodatkowe kolekcje <xref:System.Collections.Generic.IReadOnlyCollection%601> implementują takie jak <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601>.

  - **CultureInfo.CurrentKultura i KulturaInfo.CurrentUIKultura**

    Właściwości <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> i są teraz do odczytu i zapisu, a nie tylko do odczytu. Jeśli przypisać nowy <xref:System.Globalization.CultureInfo> obiekt do tych właściwości, bieżącej `Thread.CurrentThread.CurrentCulture` kultury wątku zdefiniowane przez właściwość i bieżącej kultury wątku interfejsu użytkownika zdefiniowane przez `Thread.CurrentThread.CurrentUICulture` właściwości również zmienić.

  - **Ulepszenia wyrzucania elementów bezużytecznych (GC)**

    Klasa <xref:System.GC> zawiera <xref:System.GC.TryStartNoGCRegion%2A> teraz <xref:System.GC.EndNoGCRegion%2A> i metody, które umożliwiają nie zezwalanie na wyrzucanie elementów bezużytecznych podczas wykonywania ścieżki krytycznej.

    Nowe przeciążenie <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metody pozwala kontrolować, czy sterty małych obiektów i sterty dużych obiektów są zamiatane i kompaktowane lub tylko zmieciony.

  - **Typy obsługujące kartę SIMD**

    Obszar <xref:System.Numerics> nazw zawiera teraz kilka typów obsługujących kartę <xref:System.Numerics.Matrix3x2> <xref:System.Numerics.Matrix4x4>SIMD, <xref:System.Numerics.Vector3>takich <xref:System.Numerics.Vector4>jak , , <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, , i .

    Ponieważ nowy 64-bitowy kompilator JIT zawiera również sprzętowe funkcje przyspieszania SIMD, istnieją szczególnie znaczące ulepszenia wydajności podczas korzystania z typów obsługujących kartę SIMD z nowym 64-bitowym kompilatorem JIT.

  - **Aktualizacje kryptograficzne**

    Interfejs <xref:System.Security.Cryptography?displayProperty=nameWithType> API jest aktualizowany w celu obsługi [interfejsów API kryptografii CNG systemu Windows](/windows/desktop/SecCNG/cng-reference). Poprzednie wersje programu .NET Framework opierały się w całości na [wcześniejszej wersji interfejsów API kryptografii systemu Windows](/windows/desktop/SecCrypto/cryptography-portal) jako podstawy <xref:System.Security.Cryptography?displayProperty=nameWithType> implementacji. Mieliśmy prośby o obsługę interfejsu API CNG, ponieważ obsługuje [on nowoczesne algorytmy kryptograficzne](/windows/desktop/SecCNG/cng-features#suite-b-support), które są ważne dla niektórych kategorii aplikacji.

    Program .NET Framework 4.6 zawiera następujące nowe ulepszenia do obsługi interfejsów API kryptografii CNG systemu Windows:

    - Zestaw metod rozszerzenia dla certyfikatów X509 i `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, które zwracają implementację opartą na CNG, a nie implementację opartą na capi, gdy jest to możliwe. (Niektóre karty inteligentne itp., nadal wymagają CAPI, a interfejsy API obsługują rezerwowe).

    - Klasa, <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> która zapewnia implementację CNG algorytmu RSA.

    - Ulepszenia interfejsu API RSA, dzięki czemu typowe akcje nie wymagają już rzutowania. Na przykład szyfrowanie danych <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> przy użyciu obiektu wymaga kodu, jak w poprzednich wersjach programu .NET Framework.

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      Kod, który używa nowych interfejsów API kryptografii w .NET Framework 4.6 można przepisać w następujący sposób, aby uniknąć rzutowania.

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - **Obsługa konwersji dat i godzin na lub z czasu Uniksa**

    Do <xref:System.DateTimeOffset> struktury dodano następujące nowe metody obsługi konwersji wartości daty i godziny na lub z czasu Uniksa:

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - **Przełączniki zgodności**

    Klasa <xref:System.AppContext> dodaje nową funkcję zgodności, która umożliwia modułowi zapisu biblioteki zapewnienie jednolitego mechanizmu rezygnacji dla nowych funkcji dla swoich użytkowników. Ustanawia ona luźno powiązane umowy między składnikami w celu przekazania wniosku o rezygnację. Ta funkcja jest zazwyczaj ważne, gdy wprowadza się zmianę do istniejących funkcji. Z drugiej strony istnieje już niejawna aplikacja opt-in dla nowych funkcji.

    Za <xref:System.AppContext>pomocą bibliotek definiuje i udostępnia przełączniki zgodności, podczas gdy kod, który od nich zależy, może ustawić te przełączniki, aby wpłynęli na zachowanie biblioteki. Domyślnie biblioteki zapewniają nowe funkcje i tylko ją zmieniają (oznacza to, że zapewniają poprzednie funkcje), jeśli przełącznik jest ustawiony.

    Aplikacja (lub biblioteka) może zadeklarować wartość przełącznika <xref:System.Boolean> (który jest zawsze wartością), którą definiuje biblioteka zależna. Przełącznik jest zawsze `false`niejawnie . Ustawienie przełącznika `true` na to włącza. Jawnie ustawienie przełącznika `false` na zapewnia nowe zachowanie.

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    Biblioteka musi sprawdzić, czy konsument zadeklarował wartość przełącznika, a następnie odpowiednio działać na nim.

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
    else
    {
        // new code
    }
    ```

    ```vb
    If Not AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", shouldThrow) Then
        ' This is the case where the switch value was not set by the application.
        ' The library can choose to get the value of shouldThrow by other means.
        ' If no overrides nor default values are specified, the value should be 'false'.
        ' A false value implies the latest behavior.
    End If

    ' The library can use the value of shouldThrow to throw exceptions or not.
    If shouldThrow Then
        ' old code
    Else
        ' new code
    End If
    ```

    Jest to korzystne, aby użyć spójnego formatu dla przełączników, ponieważ są one formalne umowy udostępniane przez bibliotekę. Poniżej przedstawiono dwa oczywiste formaty.

    - *Przełącznik*. *przestrzeni nazw*. *nazwa przełączania*

    - *Przełącznik*. *biblioteki*. *nazwa przełączania*

  - **Zmiany wzorca asynchronicznego opartego na zadaniach (TAP)**

    Dla aplikacji, które są przeznaczone dla programu <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .NET Framework 4.6 i obiekty dziedziczą kultury kultury i interfejsu użytkownika wątku wywołującego. Zachowanie aplikacji, które są przeznaczone dla poprzednich wersji programu .NET Framework lub które nie są przeznaczone dla określonej wersji programu .NET Framework, pozostaje bez zmian. Aby uzyskać więcej informacji, zobacz sekcję "Kultura i operacje asynchroniczne oparte na zadaniach" tematu <xref:System.Globalization.CultureInfo> klasy.

    Klasa <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> umożliwia reprezentowanie danych otoczenia, który jest lokalny dla danego przepływu `async` kontroli asynchroniczne, takich jak metoda. Może służyć do utrwalania danych między wątkami. Można również zdefiniować metodę wywołania zwrotnego, która jest powiadamiana <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> za każdym razem, gdy dane otoczenia zmienią się, ponieważ właściwość została jawnie zmieniona lub ponieważ wątek napotkał przejście kontekstu.

    Trzy metody <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>wygody , <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>i <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, zostały dodane do wzorca asynchronicznego opartego na zadaniach (TAP), aby przywrócić ukończone zadania w określonym stanie.

    Klasa <xref:System.IO.Pipes.NamedPipeClientStream> obsługuje teraz komunikację asynchronizacjową z nową <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>. Metoda.

  - **EventSource obsługuje teraz zapisywanie w dzienniku zdarzeń**

    Teraz można użyć <xref:System.Diagnostics.Tracing.EventSource> klasy do rejestrowania komunikatów administracyjnych lub operacyjnych do dziennika zdarzeń, oprócz istniejących sesji ETW utworzonych na komputerze. W przeszłości trzeba było użyć pakietu Microsoft.Diagnostics.Tracing.EventSource NuGet dla tej funkcji. Ta funkcja jest teraz wbudowana w .NET Framework 4.6.

    Pakiet NuGet i .NET Framework 4.6 zostały zaktualizowane o następujące funkcje:

    - **Zdarzenia dynamiczne**

      Zezwala na zdarzenia zdefiniowane "w locie" bez tworzenia metod zdarzeń.

    - **Ładunki bogate**

      Umożliwia przekazywanie specjalnie przypisanych klas i tablic, a także typów pierwotnych jako ładunku

    - **Śledzenie aktywności**

      Powoduje, że zdarzenia Start i Stop oznaczają zdarzenia między nimi identyfikatorem reprezentującym wszystkie aktualnie aktywne działania.

    Aby obsługiwać te funkcje, przeciążona metoda została dodana <xref:System.Diagnostics.Tracing.EventSource.Write%2A> do <xref:System.Diagnostics.Tracing.EventSource> klasy.

- **Windows Presentation Foundation (WPF)**

  - **Ulepszenia HDPI**

    Obsługa HDPI w WPF jest teraz lepsza w .NET Framework 4.6. Wprowadzono zmiany w zaokrąglaniu układu w celu zmniejszenia wystąpień przycinania w formantach z obramowaniami. Domyślnie ta funkcja jest włączona <xref:System.Runtime.Versioning.TargetFrameworkAttribute> tylko wtedy, gdy jest ustawiona na .NET 4.6.  Aplikacje przeznaczone dla wcześniejszych wersji struktury, ale są uruchomione w programie .NET Framework 4.6, mogą zdecydować się na nowe zachowanie, dodając następujący wiersz do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku app.config:

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    Okna WPF międzystrefowe wiele monitorów z różnymi ustawieniami DPI (konfiguracja Multi-DPI) są teraz całkowicie renderowane bez zaciemnionych regionów. Możesz zrezygnować z tego zachowania, dodając następujący `<appSettings>` wiersz do sekcji pliku app.config, aby wyłączyć to nowe zachowanie:

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    Obsługa automatycznego ładowania prawego kursora na podstawie ustawienia <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>DPI została dodana do .

  - **Dotyk jest lepszy**

    Raporty klientów na [Connect,](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) że dotyk powoduje nieprzewidywalne zachowanie zostały rozwiązane w programie .NET Framework 4.6. Próg podwójnego stuknięcia dla aplikacji ze Sklepu Windows i aplikacji WPF jest teraz taki sam w systemie Windows 8.1 i nowszym.

  - **Przezroczysta obsługa okna podrzędnego**

    WPF WPF WPF W.NET Framework 4.6 obsługuje przezroczyste okna podrzędne w systemie Windows 8.1 i powyżej. Umożliwia to tworzenie niesektularnych i przezroczystych okien podrzędnych w oknach najwyższego poziomu. Tę funkcję można włączyć, <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> ustawiając właściwość na `true`.

- **Windows Communication Foundation (WCF)**

  - **Obsługa SSL**

    WCF obsługuje teraz w wersji SSL TLS 1.1 i TLS 1.2, oprócz SSL 3.0 i TLS 1.0, podczas korzystania z NetTcp z zabezpieczeniami transportu i uwierzytelnianiem klienta. Teraz można wybrać protokół, którego użyć, lub wyłączyć stare mniej bezpieczne protokoły. Można to zrobić, ustawiając <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> właściwość lub dodając następujące do pliku konfiguracji.

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

    WCF teraz pozwala użytkownikom upewnić się, że niektóre wiadomości są wysyłane przy użyciu różnych podstawowych połączeń HTTP. Istnieją dwa sposoby wykonania tej czynności:

    - **Używanie prefiksu nazwy grupy połączeń**

      Użytkownicy mogą określić ciąg, który WCF będzie używany jako prefiks dla nazwy grupy połączeń. Dwie wiadomości z różnymi prefiksami są wysyłane przy użyciu różnych podstawowych połączeń HTTP. Prefiks można ustawić, dodając parę klucz/wartość <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> do właściwości wiadomości. Klucz jest "HttpTransportConnectionGroupNamePrefix"; wartość jest żądanym prefiksem.

    - **Korzystanie z różnych fabryk kanałów**

      Użytkownicy mogą również włączyć funkcję, która zapewnia, że wiadomości wysyłane przy użyciu kanałów utworzonych przez różne fabryki kanałów będą używać różnych podstawowych połączeń HTTP. Aby włączyć tę funkcję, użytkownicy `true`muszą ustawić następujące elementy: `appSetting`

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- **Fundacja przepływu pracy systemu Windows (WWF)**

  Teraz można określić liczbę sekund, przez które usługa przepływu pracy będzie trzymać żądanie operacji poza kolejnością, gdy istnieje nierozliczona zakładka "bez protokołu" przed rozliczeniem żądania. Zakładka "nie-protokół" to zakładka, która nie jest powiązana z zaległymi działaniami receive. Niektóre działania tworzą zakładki niebędące protokołami w ramach ich implementacji, więc może nie być oczywiste, że istnieje zakładka niebędąca protokołem. Należą do nich Stan i Wybierz. Więc jeśli masz usługę przepływu pracy zaimplementowane z komputera stanu lub zawierające działanie pobrania, najprawdopodobniej będzie miał zakładki bez protokołu. Możesz określić interwał, dodając wiersz `appSettings` podobny do sekcji pliku app.config:

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  Wartość domyślna to 60 sekund. Jeśli `value` jest ustawiona na 0, żądania poza kolejnością są natychmiast odrzucane z błędem z tekstem, który wygląda następująco:

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  Jest to ten sam komunikat, który zostanie wyświetlony, jeśli odebrano komunikat operacji poza kolejnością i nie ma żadnych zakładek innych niż protokół.

  Jeśli wartość `FilterResumeTimeoutInSeconds` elementu jest niezerowa, istnieją zakładki nierozerwalne i upływ czasu wygasa, operacja kończy się niepowodzeniem z komunikatem limitu czasu.

- **Transakcje**

  Teraz można dołączyć identyfikator transakcji rozproszonej dla transakcji, która spowodowała wyjątek pochodzący z <xref:System.Transactions.TransactionException> do thrown. Można to zrobić, dodając następujący `appSettings` klucz do sekcji pliku app.config:

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  Wartością domyślną jest `false`.

- **Networking**

  - **Ponowne użycie gniazda**

    System Windows 10 zawiera nowy algorytm sieci o wysokiej skalowalności, który lepiej wykorzystuje zasoby komputera, ponownie korzystając z portów lokalnych dla wychodzących połączeń TCP. Program .NET Framework 4.6 obsługuje nowy algorytm, umożliwiając aplikacjom platformy .NET korzystanie z nowego zachowania. W poprzednich wersjach systemu Windows istniał sztuczny limit równoczesnych połączeń (zazwyczaj 16 384, domyślny rozmiar zakresu portów dynamicznych), który może ograniczyć skalowalność usługi, powodując wyczerpanie portu pod obciążeniem.

    W programie .NET Framework 4.6 dodano dwa interfejsy API, aby umożliwić ponowne użycie portu, co skutecznie usuwa limit 64 KB dla równoczesnych połączeń:

    - Wartość <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> wyliczenia.

    - Właściwość. <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType>

    Domyślnie <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> właściwość `false` jest `HWRPortReuseOnSocketBind` chyba, `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` że wartość klucza rejestru jest ustawiona na 0x1. Aby włączyć ponowne użycie portu lokalnego <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> w `true`połączeniach HTTP, ustaw właściwość na . Powoduje to, że wszystkie wychodzące <xref:System.Net.HttpWebRequest> połączenia gniazda TCP z i do korzystania z <xref:System.Net.Http.HttpClient> nowej opcji gniazda systemu Windows 10, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), która umożliwia ponowne użycie portu lokalnego.

    Deweloperzy zapisujący aplikację tylko do <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> gniazd można określić <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> opcję podczas wywoływania metody, takie jak tak, aby gniazda wychodzące ponownie użyć portów lokalnych podczas wiązania.

  - **Obsługa międzynarodowych nazw domen i PunyCode**

    Nowa właściwość <xref:System.Uri.IdnHost%2A>, została dodana do klasy, <xref:System.Uri> aby lepiej obsługiwać międzynarodowe nazwy domen i PunyCode.

- **Zmiana rozmiaru w formantach formularzy systemu Windows.**

  Ta funkcja została <xref:System.Windows.Forms.DomainUpDown>rozwinięta w .NET Framework 4.6, aby uwzględnić , <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> <xref:System.Drawing.Design.UITypeEditor> <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> <xref:System.Windows.Forms.DataGridViewColumn> i typów i <xref:System.Windows.Forms.ToolStripSplitButton> prostokąta określonego przez właściwość używaną podczas rysowania .

  Jest to funkcja opt-in. Aby go włączyć, `EnableWindowsFormsHighDpiAutoResizing` ustaw `true` element na plik konfiguracji aplikacji (app.config):

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Obsługa kodowania stron kodowych**

  Program .NET Core obsługuje głównie kodowanie Unicode i domyślnie zapewnia ograniczoną obsługę kodowania stron kodowych. Można dodać obsługę kodowania stron kodowych dostępnych w programach .NET Framework, ale nieobsługiwanych <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> w .NET Core, rejestrując kodowanie stron kodowych za pomocą metody. Aby uzyskać więcej informacji, zobacz <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

  Aplikacje systemu Windows dla systemu Windows 10, które są przeznaczone dla platformy .NET Core i są zapisywane w języku C# lub Visual Basic, mogą korzystać z nowej technologii, która kompiluje aplikacje do kodu macierzystego, a nie IL. Tworzą aplikacje charakteryzujące się szybszym czasem uruchamiania i wykonywania. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji z platformą .NET Native](../net-native/index.md). Aby zapoznać się z omówieniem platformy .NET Native, który sprawdza, czym różni się zarówno kompilacja JIT, jak i NGEN oraz co to oznacza dla kodu, zobacz [.NET Native i Compilation](../net-native/net-native-and-compilation.md).

  Aplikacje są kompilowane do kodu macierzystego domyślnie podczas kompilowania ich z programem Visual Studio 2015 lub nowszym. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do platformy .NET Native](../net-native/getting-started-with-net-native.md).

  Aby obsługiwać debugowanie aplikacji natywnych platformy .NET, do niezarządzanego interfejsu API debugowania dodano szereg nowych interfejsów i wyliczeń. Aby uzyskać więcej informacji, zobacz [debugowanie (odwołanie interfejsu API niezarządzane).](../unmanaged-api/debugging/index.md)

- **Pakiety platformy .NET Framework typu open source**

  Pakiety .NET Core, takie jak niezmienne kolekcje, [interfejsy API SIMD](https://www.nuget.org/packages/Microsoft.Bcl.Simd)i interfejsy API sieci, takie jak te znalezione w obszarze <xref:System.Net.Http> nazw, są teraz dostępne jako pakiety open source w [usłudze GitHub.](https://github.com/) Aby uzyskać dostęp do kodu, zobacz [.NET w serwisie GitHub](https://github.com/dotnet/runtime). Aby uzyskać więcej informacji i jak przyczynić się do tych pakietów, zobacz [.NET Core i Open-Source](../get-started/net-core-and-open-source.md), [.NET Strona główna na GitHub](https://github.com/dotnet/home).

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a>Co nowego w .NET Framework 4.5.2

- **Nowe interfejsy API dla aplikacji ASP.NET.** Nowe <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> i <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody umożliwiają inspekcję i modyfikowanie nagłówków odpowiedzi i kodu stanu, gdy odpowiedź jest opróżniany do aplikacji klienckiej. Należy rozważyć użycie tych <xref:System.Web.HttpApplication.PreSendRequestHeaders> metod <xref:System.Web.HttpApplication.PreSendRequestContent> zamiast i zdarzeń; są bardziej wydajne i niezawodne.

  Metoda <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> umożliwia planowanie małych elementów pracy w tle. ASP.NET śledzi te elementy i zapobiega nagłym zakończeniu procesu roboczego przez usługi IIS do czasu ukończenia wszystkich elementów pracy w tle. Tej metody nie można wywołać poza domeną aplikacji zarządzanej ASP.NET.

  Nowe <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> i <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> właściwości zwracają wartości logiczne, które wskazują, czy nagłówki odpowiedzi zostały zapisane. Można użyć tych właściwości, aby upewnić się, <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> że wywołania interfejsów API, takich jak (które zgłaszają wyjątki, jeśli nagłówki zostały zapisane) zakończy się pomyślnie.

- **Zmiana rozmiaru w formantach formularzy systemu Windows.** Ta funkcja została rozszerzona. Teraz można użyć ustawienia DPI systemu, aby zmienić rozmiar składników następujących dodatkowych kontrolek (na przykład strzałki rozwijanej w polach kombi):

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  Jest to funkcja opt-in. Aby go włączyć, `EnableWindowsFormsHighDpiAutoResizing` ustaw `true` element na plik konfiguracji aplikacji (app.config):

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Nowa funkcja przepływu pracy.** Menedżer zasobów, który używa <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metody (i dlatego <xref:System.Transactions.IPromotableSinglePhaseNotification> implementuje interfejs) <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> można użyć nowej metody, aby zażądać następujących czynności:

  - Promuj transakcję do transakcji koordynatora transakcji rozproszonych firmy Microsoft (MSDTC).

  - <xref:System.Transactions.IPromotableSinglePhaseNotification> Zamień <xref:System.Transactions.ISinglePhaseNotification>na program , który jest trwałą rejestracją, która obsługuje zatwierdzanie jednofazowe.

  Można to zrobić w tej samej domenie aplikacji i nie wymaga żadnego dodatkowego kodu niezarządzanego do interakcji z msdtc do wykonywania promocji. Nowa metoda może być wywoływana tylko wtedy, <xref:System.Transactions?displayProperty=nameWithType> gdy <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` istnieje zaległe wywołanie z do metody, która jest implementowana przez promowanie rejestracji.

- **Usprawnienia profilowania.** Następujące nowe interfejsy API profilowania niezarządzanego zapewniają bardziej niezawodne profilowanie:

  - [COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [Wyliczenie COR_PRF_HIGH_MONITOR](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [GetAssemblyReferences, metoda](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [GetEventMask2, metoda](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [SetEventMask2, metoda](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [AddAssemblyReference, metoda](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  Poprzednie `ICorProfiler` implementacje obsługiwane z opóźnieniem ładowania zestawów zależnych. Nowe interfejsy API profilowania wymagają zestawów zależnych, które są wstrzykiwane przez profiler być ładowalne natychmiast, zamiast ładować po aplikacji jest w pełni zainicjowany. Ta zmiana nie ma wpływu `ICorProfiler` na użytkowników istniejących interfejsów API.

- **Ulepszenia debugowania.** Następujące nowe niezarządzane debugowanie interfejsów API zapewniają lepszą integrację z profilera. Teraz można uzyskać dostęp do metadanych wstawianych przez profiler, a także zmiennych lokalnych i kodu produkowanego przez żądania ReJIT kompilatora podczas debugowania zrzutu.

  - [SetWriteableMetadataUpdateMode, metoda](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [EnumerateLocalVariablesEx, metoda](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [GetLocalVariableEx, metoda](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [GetCodeEx, metoda](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [GetActiveReJitRequestILCode, metoda](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [GetInstrumentedILMap, metoda](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Zmiany śledzenia zdarzeń.** Program .NET Framework 4.5.2 umożliwia śledzenie aktywności poza procesem— śledzenie zdarzeń dla systemu Windows (ETW) dla większej powierzchni. Dzięki temu dostawcy zaawansowanego zarządzania energią (APM) zapewniają lekkie narzędzia, które dokładnie śledzą koszty poszczególnych żądań i działań, które przecinają wątki.  Te zdarzenia są wywoływane tylko wtedy, gdy kontrolery ETW je włączyć; w związku z tym zmiany nie mają wpływu na wcześniej napisany kod ETW lub kod, który działa z ETW wyłączone.

- **Promowanie transakcji i przekształcanie jej w trwałą rejestrację**

  <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>to nowy interfejs API dodany do programu .NET Framework 4.5.2 i 4.6:

  ```csharp
  [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
  public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                            IPromotableSinglePhaseNotification promotableNotification,
                                            ISinglePhaseNotification enlistmentNotification,
                                            EnlistmentOptions enlistmentOptions)
  ```

  ```vb
  <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")>
  public Function PromoteAndEnlistDurable(resourceManagerIdentifier As Guid,
                                          promotableNotification As IPromotableSinglePhaseNotification,
                                          enlistmentNotification As ISinglePhaseNotification,
                                          enlistmentOptions As EnlistmentOptions) As Enlistment
  ```

  Metoda może być używana przez rejestrację, która <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> została wcześniej <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> utworzona przez w odpowiedzi na metodę. Prosi `System.Transactions` o promowanie transakcji do transakcji MSDTC i "konwersji" promowanie rejestracji do trwałego rejestracji. Po pomyślnym zakończeniu tej <xref:System.Transactions.IPromotableSinglePhaseNotification> metody interfejs nie będzie `System.Transactions`już odwoływał się przez program <xref:System.Transactions.ISinglePhaseNotification> , a wszelkie przyszłe powiadomienia będą docierać do dostarczonego interfejsu. Rejestracja, o czym mowa, musi działać jako trwałego rejestracji, wspieranie rejestrowania transakcji i odzyskiwania. <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> Szczegółowe informacje można znaleźć w tym zakresie. Ponadto rekrutacja musi obsługiwać <xref:System.Transactions.ISinglePhaseNotification>.  Ta metoda może być wywoływana *tylko* podczas przetwarzania <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> wywołania. Jeśli tak nie jest, <xref:System.Transactions.TransactionException> wyjątek.

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a>Co nowego w .NET Framework 4.5.1

**Aktualizacje z kwietnia 2014 r.:**

- [Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) zawiera aktualizacje szablonów biblioteki klas przenośnych do obsługi tych scenariuszy:

  - Interfejsów API środowiska wykonawczego systemu Windows można używać w przenośnych bibliotekach docelowych dla systemów Windows 8.1, Windows Phone 8.1 i Windows Phone Silverlight 8.1.

  - Kod XAML (windows.ui.xaml) można uwzględnić w bibliotekach przenośnych, gdy jest skierowany na system Windows 8.1 lub Windows Phone 8.1. Obsługiwane są następujące szablony XAML: Pusta strona, Słownik zasobów, Formant szablonów i Kontrola użytkownika.

  - Można utworzyć przenośny składnik środowiska wykonawczego systemu Windows (plik winmd) do użytku w aplikacjach ze Sklepu przeznaczonych dla systemów Windows 8.1 i Windows Phone 8.1.

  - Możesz ponownie kierować bibliotekę klas ze Sklepu Windows lub Sklepu Windows Phone, taką jak przenośna biblioteka klas.

  Aby uzyskać więcej informacji na temat tych zmian, zobacz [Biblioteka klas przenośnych](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Zestaw zawartości programu .NET Framework zawiera teraz dokumentację dla platformy .NET Native, która jest technologią wstępnej kompilacji do tworzenia i wdrażania aplikacji systemu Windows. .NET Native kompiluje aplikacje bezpośrednio do kodu macierzystego, a nie do języka pośredniego (IL), aby uzyskać lepszą wydajność. Aby uzyskać szczegółowe informacje, zobacz [Kompilowanie aplikacji z platformą .NET Native](../net-native/index.md).

- [Źródło referencyjne programu .NET Framework](https://referencesource.microsoft.com/) zapewnia nowe środowisko przeglądania i ulepszone funkcje. Teraz można przeglądać kod źródłowy programu .NET Framework w trybie online, [pobrać odwołanie](https://referencesource.microsoft.com/download.html) do przeglądania w trybie offline i przejść przez źródła (w tym poprawki i aktualizacje) podczas debugowania. Aby uzyskać więcej informacji, zobacz wpis blogu [Nowy wygląd źródła odwołania .NET](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).

Nowe funkcje i ulepszenia w klasach podstawowych w .NET Framework 4.5.1 obejmują:

- Automatyczne przekierowywanie powiązania dla zestawów. Począwszy od programu Visual Studio 2013, podczas kompilowania aplikacji, która jest przeznaczona dla programu .NET Framework 4.5.1, przekierowania powiązania mogą zostać dodane do pliku konfiguracji aplikacji, jeśli aplikacja lub jej składniki odwołują się do wielu wersji tego samego zestawu. Tę funkcję można również włączyć dla projektów przeznaczonych dla starszych wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie i wyłączanie automatycznego przekierowania powiązania](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Możliwość zbierania informacji diagnostycznych, aby pomóc deweloperom poprawić wydajność aplikacji serwera i chmury. Aby uzyskać więcej <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> informacji, zobacz i <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> metody w <xref:System.Diagnostics.Tracing.EventSource> klasie.

- Możliwość jawnie kompaktowania sterty dużych obiektów (LOH) podczas wyrzucania elementów bezużytecznych. Aby uzyskać więcej <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> informacji, zobacz właściwość.

- Dodatkowe ulepszenia wydajności, takie jak zawieszenie aplikacji ASP.NET, wielordzeniowe ulepszenia JIT i szybsze uruchamianie aplikacji po aktualizacji programu .NET Framework. Aby uzyskać szczegółowe informacje, zobacz [.NET Framework 4.5.1 anons](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) i [ASP.NET aplikacji zawiesić](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blogu.

Ulepszenia formularzy systemu Windows obejmują:

- Zmiana rozmiaru w formantach formularzy systemu Windows. Za pomocą ustawienia dpi systemu można zmienić rozmiar składników formantów (na przykład ikon wyświetlanych w siatce właściwości), decydując się na wpis w pliku konfiguracji aplikacji (app.config) dla aplikacji. Ta funkcja jest obecnie obsługiwana w następujących formantach formularzy systemu Windows:

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - Niektóre aspekty <xref:System.Windows.Forms.DataGridView> (patrz [nowe funkcje w 4.5.2](#v452) dla dodatkowych kontroli obsługiwane)

  Aby włączyć tę funkcję, \<dodaj nowy element appSettings> do pliku konfiguracyjnego `EnableWindowsFormsHighDpiAutoResizing` (app.config) i ustaw element na: `true`

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

Ulepszenia podczas debugowania aplikacji .NET Framework w programie Visual Studio 2013 obejmują:

- Zwraca wartości w debugerze programu Visual Studio. Podczas debugowania zarządzanej aplikacji w programie Visual Studio 2013 w oknie Autos są wyświetlane zwracane typy i wartości metod. Te informacje są dostępne dla aplikacji klasycznych, Sklep Windows i Windows Phone. Aby uzyskać więcej informacji, zobacz [Badanie wartości zwracanych wywołań metod](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).

- Edytuj i kontynuuj dla aplikacji 64-bitowych. Program Visual Studio 2013 obsługuje funkcję Edycja i Kontynuuj dla 64-bitowych aplikacji zarządzanych na komputery, Sklep Windows i Windows Phone. Istniejące ograniczenia pozostają w mocy dla aplikacji 32-bitowych i 64-bitowych (zobacz ostatnią sekcję [artykułu Obsługiwane zmiany kodu (C#).](/visualstudio/debugger/supported-code-changes-csharp)

- Debugowanie z uwzględnieniem asynchronii. Aby ułatwić debugowanie aplikacji asynchronicznych w programie Visual Studio 2013, stos wywołań ukrywa kod infrastruktury dostarczony przez kompilatory do obsługi programowania asynchronialnego, a także łańcuchy w logicznych ramek nadrzędnych, dzięki czemu można wykonać logiczne wykonanie programu jaśniej. Okno Zadania zastępuje okno Zadania równoległe i wyświetla zadania związane z określonym punktem przerwania, a także wyświetla wszystkie inne zadania, które są aktualnie aktywne lub zaplanowane w aplikacji. O tej funkcji można przeczytać w sekcji "Debugowanie z uwzględnieniem asynchronii" [w ogłoszeniu .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

- Lepsza obsługa wyjątków dla składników środowiska wykonawczego systemu Windows. W systemie Windows 8.1 wyjątki wynikające z aplikacji ze Sklepu Windows zachowują informacje o błędzie, który spowodował wyjątek, nawet w granicach języka. O tej funkcji można przeczytać w sekcji "Tworzenie aplikacji ze Sklepu Windows" [w ogłoszeniu .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

Począwszy od programu Visual Studio 2013, można użyć [narzędzia do optymalizacji zarządzanych profilów (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) w celu optymalizacji aplikacji ze Sklepu Windows 8.x oraz aplikacji klasycznych.

Aby uzyskać nowe funkcje w ASP.NET 4.5.1, zobacz [ASP.NET i narzędzia sieci Web dla programu Visual Studio 2013 Release Notes](/aspnet/visual-studio/overview/2013/release-notes).

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a>Co nowego w .NET Framework 4.5

### <a name="base-classes"></a>Klas podstawowych

- Możliwość zmniejszenia ponownego uruchamiania systemu przez wykrywanie i zamykanie aplikacji .NET Framework 4 podczas wdrażania. Zobacz [Ograniczanie liczby ponownych uruchomień systemu podczas instalacji programu .NET Framework 4.5](../deployment/reducing-system-restarts.md).

- Obsługa macierzy większych niż 2 gigabajty (GB) na platformach 64-bitowych. Tę funkcję można włączyć w pliku konfiguracji aplikacji. Zobacz [ \<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), który zawiera również listę innych ograniczeń dotyczących rozmiaru obiektu i rozmiaru tablicy.

- Lepsza wydajność za pośrednictwem wyrzucania elementów bezużytecznych w tle dla serwerów. Korzystając z wyrzucania elementów bezużytecznych serwera w .NET Framework 4.5, tło wyrzucania elementów bezużytecznych jest automatycznie włączone. Zobacz sekcję Wyrzucanie elementów bezużytecznych serwera w tle [tematu Podstawy wyrzucania elementów bezużytecznych.](../../standard/garbage-collection/fundamentals.md)

- Kompilacja just-in-time (JIT), która jest opcjonalnie dostępna na procesorach wielordzeniowych w celu zwiększenia wydajności aplikacji. Zobacz: <xref:System.Runtime.ProfileOptimization>.

- Możliwość ograniczenia czasu trwania aparatu wyrażeń regularnych będzie próbował rozwiązać wyrażenie regularne, zanim limit czasu. Zobacz <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> właściwość.

- Możliwość definiowania kultury domyślnej dla domeny aplikacji. Zobacz <xref:System.Globalization.CultureInfo> klasę.

- Obsługa konsoli dla kodowania Unicode (UTF-16). Zobacz <xref:System.Console> klasę.

- Obsługa przechowywania wersji danych zamawiania ciągów kulturowych i porównywania. Zobacz <xref:System.Globalization.SortVersion> klasę.

- Lepsza wydajność podczas pobierania zasobów. Zobacz [Pakowanie i wdrażanie zasobów](../resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Ulepszenia kompresji zip, aby zmniejszyć rozmiar skompresowanego pliku. Zobacz <xref:System.IO.Compression?displayProperty=nameWithType> obszar nazw.

- Możliwość dostosowania kontekstu odbicia, aby zastąpić domyślne <xref:System.Reflection.Context.CustomReflectionContext> zachowanie odbicia za pośrednictwem klasy.

- Obsługa wersji 2008 umięlonych nazw domen w aplikacjach <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> (IDNA), gdy klasa jest używana w systemie Windows 8.

- Delegowanie porównania ciągów do systemu operacyjnego, który implementuje Unicode 6.0, gdy .NET Framework jest używany w systemie Windows 8. Podczas uruchamiania na innych platformach .NET Framework zawiera własne dane porównania ciągów, które implementuje Unicode 5.x. Zobacz <xref:System.String> klasy i uwagi sekcji <xref:System.Globalization.SortVersion> klasy.

- Możliwość obliczania kodów skrótów dla ciągów na podstawie domeny aplikacji. Zobacz [ \<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Wsparcie odbicia typu <xref:System.Type> <xref:System.Reflection.TypeInfo> podzielone między klasami. Zobacz [Odbicie w programie .NET Framework dla aplikacji ze Sklepu Windows](../reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

W .NET Framework 4.5 managed extensibility Framework (MEF) zawiera następujące nowe funkcje:

- Obsługa typów ogólnych.

- Model programowania oparty na konwencji, który umożliwia tworzenie części na podstawie konwencji nazewnictwa, a nie atrybutów.

- Wiele zakresów.

- Podzbiór MEF, którego można używać podczas tworzenia aplikacji ze Sklepu Windows 8.x. Ten podzbiór jest dostępny jako [pakiet do pobrania](https://www.nuget.org/packages/Microsoft.Composition) z Galerii NuGet. Aby zainstalować pakiet, otwórz projekt w programie Visual Studio, wybierz pozycję **Zarządzaj pakietami NuGet** z menu **Projektu** i wyszukaj w trybie `Microsoft.Composition` online pakiet.

Aby uzyskać więcej informacji, zobacz [Managed Extensibility Framework (MEF)](../mef/index.md).

### <a name="asynchronous-file-operations"></a>Operacje asynchroniczne plików

W programie .NET Framework 4.5 nowe funkcje asynchroniczne zostały dodane do języków C# i Visual Basic. Te funkcje dodają model oparty na zadaniach do wykonywania operacji asynchronicznych. Aby użyć tego nowego modelu, należy użyć metod asynchronicznych w klasach we/wy. Zobacz [Asynchroniczne we/wy pliku](../../standard/io/asynchronous-file-i-o.md).

<a name="tools" />

### <a name="tools"></a>narzędzia

W programie .NET Framework 4.5 generator plików zasobów (Resgen.exe) umożliwia utworzenie pliku resw do użytku w aplikacjach ze Sklepu Windows 8.x z pliku .resources osadzonego w zestawie programu .NET Framework. Aby uzyskać więcej informacji, zobacz [Resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md).

Optymalizacja z przewodnikiem profilu zarządzanego (Mpgo.exe) umożliwia skrócenie czasu uruchamiania aplikacji, wykorzystania pamięci (rozmiar zestawu roboczego) i przepływności poprzez optymalizację natywnych zestawów obrazów. Narzędzie wiersza polecenia generuje dane profilu dla natywnych zestawów aplikacji obrazu. Zobacz [Mpgo.exe (Managed Profile Guided Optimization Tool)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Począwszy od programu Visual Studio 2013, można użyć mpgo.exe do optymalizacji aplikacji ze Sklepu Windows 8.x, a także aplikacji klasycznych.

<a name="parallel" />

### <a name="parallel-computing"></a>Przetwarzanie równoległe

.NET Framework 4.5 zawiera kilka nowych funkcji i ulepszeń dla komputerów równoległych. Obejmują one lepszą wydajność, zwiększoną kontrolę, ulepszoną obsługę programowania asynchronicznej, nową bibliotekę przepływu danych oraz ulepszoną obsługę debugowania równoległego i analizy wydajności. Zobacz wpis [Co nowego dla równoległości w .NET 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) w programie programowania równoległego z blogiem .NET.

<a name="web" />

### <a name="web"></a>Sieć Web

ASP.NET 4.5 i 4.5.1 dodać powiązanie modelu dla formularzy sieci Web, obsługa WebSocket, programy obsługi asynchronii, ulepszenia wydajności i wiele innych funkcji. Więcej informacji zawierają następujące zasoby:

- [ASP.NET 4.5 i Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [Platforma ASP.NET i narzędzia Web Tools dla programu Visual Studio 2013 — informacje o wersji](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a>Sieci<a name="networking" />

.NET Framework 4.5 udostępnia nowy interfejs programowania dla aplikacji HTTP. Aby uzyskać więcej informacji, zobacz nowe <xref:System.Net.Http?displayProperty=nameWithType> i <xref:System.Net.Http.Headers?displayProperty=nameWithType> przestrzenie nazw.

Pomoc techniczna jest również dostępna dla nowego interfejsu programowania do akceptowania i <xref:System.Net.HttpListener> interakcji z połączeniem WebSocket przy użyciu istniejących i powiązanych klas. Aby uzyskać więcej informacji, zobacz <xref:System.Net.WebSockets> <xref:System.Net.HttpListener> nowy obszar nazw i klasy.

Ponadto program .NET Framework 4.5 zawiera następujące ulepszenia sieciowe:

- Obsługa identyfikatorów URI zgodnych ze specyfikacją RFC. Aby uzyskać więcej <xref:System.Uri> informacji, zobacz i powiązanych zajęć.

- Obsługa analizowania umięsionej nazwy domeny (IDN). Aby uzyskać więcej <xref:System.Uri> informacji, zobacz i powiązanych zajęć.

- Obsługa internacjonalizacji adresów e-mail (EAI). Aby uzyskać więcej <xref:System.Net.Mail> informacji, zobacz obszar nazw.

- Ulepszona obsługa IPv6. Aby uzyskać więcej <xref:System.Net.NetworkInformation> informacji, zobacz obszar nazw.

- Obsługa gniazd w dwóch trybach. Aby uzyskać więcej <xref:System.Net.Sockets.Socket> informacji, zobacz i <xref:System.Net.Sockets.TcpListener> klasy.

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

W programie .NET Framework 4.5, Windows Presentation Foundation (WPF) zawiera zmiany i ulepszenia w następujących obszarach:

- Nowy <xref:System.Windows.Controls.Ribbon.Ribbon> formant, który umożliwia zaimplementowanie interfejsu użytkownika wstążki, który obsługuje pasek narzędzi szybki dostęp, menu aplikacji i karty.

- Nowy <xref:System.ComponentModel.INotifyDataErrorInfo> interfejs, który obsługuje sprawdzanie poprawności danych synchronicznych i asynchronicznych.

- Nowe funkcje <xref:System.Windows.Controls.VirtualizingPanel> <xref:System.Windows.Threading.Dispatcher> dla i klas.

- Zwiększona wydajność podczas wyświetlania dużych zestawów zgrupowanych danych i uzyskiwania dostępu do kolekcji w wątkach innych niż interfejs użytkownika.

- Powiązanie danych z właściwościami statycznymi, powiązanie <xref:System.Reflection.ICustomTypeProvider> danych z typami niestandardowymi, które implementują interfejs, oraz pobieranie informacji wiązania danych z wyrażenia wiążącego.

- Zmiana położenia danych w miarę zmiany wartości (kształtowanie na żywo).

- Możliwość sprawdzenia, czy kontekst danych dla kontenera elementów jest rozłączony.

- Możliwość ustawiania czasu, jaki powinien ugiąć się między zmianami właściwości a aktualizacjami źródła danych.

- Ulepszona obsługa implementowania wzorców słabych zdarzeń. Ponadto zdarzenia mogą teraz akceptować rozszerzenia znaczników.

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

W programie .NET Framework 4.5 dodano następujące funkcje, aby ułatwić zapisywanie i utrzymywanie aplikacji Windows Communication Foundation (WCF):

- Uproszczenie wygenerowanych plików konfiguracyjnych.

- Wsparcie dla rozwoju pierwszego kontraktu.

- Możliwość łatwiejszego konfigurowania ASP.NET trybu zgodności.

- Zmiany domyślnych wartości właściwości transportu, aby zmniejszyć prawdopodobieństwo, że trzeba będzie je ustawić.

- Aktualizacje <xref:System.Xml.XmlDictionaryReaderQuotas> klasy, aby zmniejszyć prawdopodobieństwo, że trzeba będzie ręcznie skonfigurować przydziały dla czytników słowników XML.

- Sprawdzanie poprawności plików konfiguracyjnych WCF przez program Visual Studio w ramach procesu kompilacji, dzięki czemu można wykryć błędy konfiguracji przed uruchomieniem aplikacji.

- Nowa obsługa przesyłania strumieniowego asynchronii.

- Nowe mapowanie protokołu HTTPS ułatwiające udostępnianie punktu końcowego za pośrednictwem protokołu HTTPS za pomocą internetowych usług informacyjnych (IIS).

- Możliwość generowania metadanych w jednym dokumencie `?singleWSDL` WSDL przez dołączenie do adresu URL usługi.

- Websockets obsługuje, aby umożliwić prawdziwą komunikację dwukierunkową przez porty 80 i 443 o właściwościach wydajności podobnych do transportu TCP.

- Obsługa konfigurowania usług w kodzie.

- Etykietki narzędzi Edytora XML.

- <xref:System.ServiceModel.ChannelFactory>wsparcia buforowania.

- Obsługa kompresji kodera binarnego.

- Obsługa transportu UDP, który umożliwia deweloperom pisanie usług, które używają wiadomości "zwolnij i zapomnij". Klient wysyła wiadomość do usługi i oczekuje żadnej odpowiedzi od usługi.

- Możliwość obsługi wielu trybów uwierzytelniania w jednym punkcie końcowym WCF podczas korzystania z transportu HTTP i zabezpieczeń transportu.

- Obsługa usług WCF, które używają międzynarodowych nazw domen (IDN).

Aby uzyskać więcej informacji, zobacz [Co nowego w programie Windows Communication Foundation](../wcf/whats-new.md).

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a>Program Windows Workflow Foundation (WF)

W programie .NET Framework 4.5 do programu Windows Workflow Foundation (WF) dodano kilka nowych funkcji, w tym:

- Przepływy pracy maszyny stanu, które zostały po raz pierwszy wprowadzone w ramach programu .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)). Ta aktualizacja zawierała kilka nowych klas i działań, które umożliwiły deweloperom tworzenie przepływów pracy maszyny stanu. Te klasy i działania zostały zaktualizowane dla programu .NET Framework 4.5 w celu uwzględnienia:

  - Możliwość ustawiania punktów przerwania w stanach.

  - Możliwość kopiowania i wklejania przejść w projektancie przepływu pracy.

  - Obsługa projektanta dla tworzenia przejścia wyzwalacza udostępnionego.

  - Działania związane z tworzeniem przepływów pracy <xref:System.Activities.Statements.StateMachine> <xref:System.Activities.Statements.State>maszyny <xref:System.Activities.Statements.Transition>stanu, w tym: , i .

- Ulepszone funkcje projektanta przepływu pracy, takie jak:

  - Ulepszone funkcje wyszukiwania przepływu pracy w programie Visual Studio, w tym **szybkie znajdowanie** i **znajdowanie w plikach**.

  - Możliwość automatycznego tworzenia działania Sekwencja, gdy drugie działanie podrzędne jest dodawany do działania kontenera i uwzględnić oba działania w Sequence działania.

  - Obsługa przesuwania, która umożliwia zmianę widocznej części przepływu pracy bez użycia pasków przewijania.

  - Nowy widok **konspektu dokumentu,** który pokazuje składniki przepływu pracy w widoku konspektu w stylu drzewa i umożliwia wybranie składnika w widoku **Konspektu dokumentu.**

  - Możliwość dodawania adnotacji do działań.

  - Możliwość definiowania i używania delegatów działania przy użyciu projektanta przepływu pracy.

  - Automatyczne łączenie i automatyczne wstawianie dla działań i przejść w przepływach pracy maszyny stanu i schematu blokowego.

- Przechowywanie informacji o stanie widoku dla przepływu pracy w jednym elemencie w pliku XAML, dzięki czemu można łatwo zlokalizować i edytować informacje o stanie widoku.

- A NoPersistScope działania kontenera, aby zapobiec aktywności podrzędnych z utrwalania.

- Obsługa wyrażeń języka C#:

  - Projekty przepływu pracy, które używają języka Visual Basic użyje wyrażeń Visual Basic, a projekty przepływu pracy języka C# będą używać wyrażeń języka C#.

  - Projekty przepływu pracy języka C#, które zostały utworzone w programie Visual Studio 2010 i które mają wyrażenia Języka Visual Basic, są zgodne z projektami przepływu pracy języka C#, które używają wyrażeń języka C#.

- Ulepszenia przechowywania wersji:

  - Nowa <xref:System.Activities.WorkflowIdentity> klasa, która zapewnia mapowanie między wystąpieniem utrwalonego przepływu pracy a jego definicją przepływu pracy.

  - Wykonanie obok siebie wielu wersji przepływu pracy na tym <xref:System.ServiceModel.Activities.WorkflowServiceHost>samym hoście, w tym .

  - W aktualizacji dynamicznej możliwość modyfikowania definicji wystąpienia utrwalonego przepływu pracy.

- Programowanie usług przepływu pracy jako pierwszego kontraktu, które zapewnia obsługę automatycznego generowania działań w celu dopasowania do istniejącej umowy serwisowej.

Aby uzyskać więcej informacji, zobacz [Co nowego w programie Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).

<a name="tailored" />

### <a name="net-for-windows-8x-store-apps"></a>Platforma .NET dla aplikacji do Sklepu Windows 8.x

Aplikacje ze Sklepu Windows 8.x są przeznaczone do określonych rozmiarów i wykorzystują możliwości systemu operacyjnego Windows. Podzbiór programu .NET Framework 4.5 lub 4.5.1 jest dostępny do tworzenia aplikacji ze Sklepu Windows 8.x dla systemu Windows przy użyciu języka C# lub Visual Basic. Ten podzbiór jest nazywany .NET dla aplikacji ze Sklepu Windows 8.x i jest omówiony w [omówienie](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

### <a name="portable-class-libraries"></a>Przenośne biblioteki klas<a name="portable" />

Projekt biblioteki klas przenośnych w programie Visual Studio 2012 (i nowszych wersjach) umożliwia pisanie i tworzenie zarządzanych zestawów, które działają na wielu platformach platformy .NET Framework. Korzystając z projektu przenośnej biblioteki klas, można wybrać platformy (takie jak Windows Phone i .NET dla windows 8.x Store apps) do docelowej. Dostępne typy i elementy członkowskie w projekcie są automatycznie ograniczone do typowych typów i członków na tych platformach. Aby uzyskać więcej informacji, zobacz [Biblioteka klas przenośnych](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Zobacz też

- [Program .NET Framework i wydania poza harmonogramem (OOB)](../get-started/the-net-framework-and-out-of-band-releases.md)
- [Co nowego w ułatwieniach dostępu w platformie .NET Framework](whats-new-in-accessibility.md)
- [Co nowego w programie Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Co nowego w programie Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019)
- [ASP.NET](/aspnet)
- [Co nowego w języku C++ w programie Visual Studio](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
