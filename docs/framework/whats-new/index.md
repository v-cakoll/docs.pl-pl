---
title: Co nowego w .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c15b2c27e51557494f10c2445d75a4bd56c47f91
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987242"
---
# <a name="whats-new-in-the-net-framework"></a>Co nowego w .NET Framework

Ten artykuł podsumowuje najważniejsze nowe funkcje i ulepszenia w następujących wersjach .NET Framework:

- [.NET Framework 4.8](#v48)
- [.NET Framework 4.7.2](#v472)
- [.NET Framework 4.7.1](#v471)
- [.NET Framework 4.7](#v47)
- [.NET Framework 4.6.2](#v462)
- [.NET Framework 4.6.1](#v461)
- [.NET 2015 i .NET Framework 4,6](#v46)
- [.NET Framework 4.5.2](#v452)
- [.NET Framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Ten artykuł nie zawiera wyczerpujących informacji o każdej nowej funkcji i może ulec zmianie. Aby uzyskać ogólne informacje na temat .NET Framework, zobacz [wprowadzenie](../get-started/index.md). W przypadku obsługiwanych platform zobacz [wymagania systemowe](../get-started/system-requirements.md). Aby uzyskać linki do pobrania i instrukcje instalacji, zobacz [Przewodnik instalacji](../install/guide-for-developers.md).

> [!NOTE]
> Zespół .NET Framework również zwalnia funkcje poza pasmem z pakietem NuGet, aby rozwinąć obsługę platformy i wprowadzić nowe funkcje, takie jak Niezmienne kolekcje i typy wektorów z włączonym SIMD. Aby uzyskać więcej informacji, zobacz [dodatkowe biblioteki klas i interfejsy API](../additional-apis/index.md) oraz [.NET Framework i wersje poza pasmem](../get-started/the-net-framework-and-out-of-band-releases.md).
> Zapoznaj się z [pełną listą pakietów NuGet](https://www.nuget.org/profiles/dotnetframework) dla .NET Framework.

<a name="v48" />

## <a name="introducing-net-framework-48"></a>Wprowadzenie .NET Framework 4,8

.NET Framework 4,8 kompiluje w poprzednich wersjach .NET Framework 4. x poprzez dodanie wielu nowych poprawek i kilku nowych funkcji, gdy jest to bardzo stabilny produkt.

### <a name="downloading-and-installing-net-framework-48"></a>Pobieranie i instalowanie .NET Framework 4,8

.NET Framework 4,8 można pobrać z następujących lokalizacji:

- [Instalator sieci Web .NET Framework 4,8](https://go.microsoft.com/fwlink/?LinkId=2085155)

- [Instalator offline systemu .NET Framework 4,8](https://go.microsoft.com/fwlink/?linkid=2088631)

.NET Framework 4,8 można zainstalować w systemie Windows 10, Windows 8.1, Windows 7 z dodatkiem SP1 i odpowiednich platformach serwera, począwszy od systemu Windows Server 2008 R2 z dodatkiem SP1. .NET Framework 4,8 można zainstalować przy użyciu Instalatora sieci Web lub Instalatora w trybie offline. Zalecanym sposobem większości użytkowników jest użycie Instalatora sieci Web.

Aby docelowo .NET Framework 4,8 w programie Visual Studio 2012 lub nowszym, należy zainstalować [pakiet deweloperski .NET Framework 4,8](https://go.microsoft.com/fwlink/?LinkId=2085167).

### <a name="whats-new-in-net-framework-48"></a>Co nowego w .NET Framework 4,8

.NET Framework 4,8 wprowadza nowe funkcje w następujących obszarach:

- [Klasy bazowe](#core48)
- [Windows Communication Foundation (WCF)](#wcf48)
- [Windows Presentation Foundation (WPF)](#wpf48)
- [Środowisko uruchomieniowe języka wspólnego](#clr48)

Ulepszony ułatwienia dostępu, dzięki czemu aplikacja zapewnia odpowiednie środowisko dla użytkowników technologii pomocniczej, w dalszym ciągu jest głównym fokusem .NET Framework 4,8. Aby uzyskać informacje na temat ulepszeń ułatwień dostępu w .NET Framework 4,8, zobacz [co nowego w ułatwieniach dostępu w .NET Framework](whats-new-in-accessibility.md).

<a name="core48" />

#### <a name="base-classes"></a>Klas podstawowych

**Zredukowany wpływ na Szyfrowanie FIPS**. W poprzednich wersjach .NET Framework zarządzane klasy dostawcy usług kryptograficznych, takie jak <xref:System.Security.Cryptography.SHA256Managed> <xref:System.Security.Cryptography.CryptographicException> throw, gdy systemowe biblioteki kryptograficzne są skonfigurowane w trybie FIPS. Te wyjątki są zgłaszane, ponieważ zarządzane wersje klas dostawcy usług kryptograficznych, w przeciwieństwie do bibliotek kryptograficznych systemu, nie zostały poddane FIPS (Federal Information Processing Standards) 140-2 certyfikacji. Ponieważ kilku deweloperów ma swoje komputery deweloperskie w trybie FIPS, wyjątki są często zgłaszane w systemach produkcyjnych.

Domyślnie w aplikacjach, które są przeznaczone .NET Framework 4,8, następujące zarządzane klasy kryptograficzne nie zgłaszają już <xref:System.Security.Cryptography.CryptographicException> w tym przypadku:

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

Zamiast tego te klasy przekierowują operacje kryptograficzne do biblioteki kryptografii systemu. Ta zmiana skutecznie usuwa potencjalne różnice między środowiskami deweloperskimi i środowiskami produkcyjnymi oraz sprawia, że składniki natywne i składniki zarządzane działają w ramach tych samych zasad kryptograficznych. Aplikacje, które są zależne od tych wyjątków, mogą przywrócić poprzednie zachowanie przez ustawienie `Switch.System.Security.Cryptography.UseLegacyFipsThrow` przełącznika `true`AppContext na. Aby uzyskać więcej informacji, zobacz [zarządzane klasy kryptografii nie zgłaszają wyjątku kryptografii w trybie FIPS](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).

**Korzystanie z zaktualizowanej wersji programu ZLib**

Począwszy od .NET Framework 4,5, zestaw clrcompression. dll używa [zlib](https://www.zlib.net), natywnej biblioteki zewnętrznej do kompresji danych, aby zapewnić implementację algorytmu Wklęśnięcie. .NET Framework 4,8, clrcompression. dll został zaktualizowany tak, aby korzystał z wersji ZLib 1.2.11, która obejmuje kilka kluczowych ulepszeń i poprawek.

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

**Wprowadzenie do ServiceHealthBehavior**

Punkty końcowe kondycji są szeroko używane przez narzędzia aranżacji do zarządzania usługami w oparciu o ich stan kondycji. Kontrola kondycji może być również używana przez narzędzia do monitorowania do śledzenia i dostarczania powiadomień dotyczących dostępności i wydajności usługi.

**ServiceHealthBehavior** to zachowanie usługi WCF, które rozszerza <xref:System.ServiceModel.Description.IServiceBehavior>.  Po dodaniu do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> kolekcji zachowanie usługi wykonuje następujące czynności:

- Zwraca stan kondycji usługi z kodami odpowiedzi HTTP. W ciągu zapytania można określić kod stanu HTTP dla żądania sondowania kondycji HTTP/GET.

- Publikuje informacje o kondycji usługi. Szczegóły dotyczące usługi, w tym stan usługi, liczniki ograniczenia i pojemność, można wyświetlić za pomocą żądania HTTP/GET z `?health` ciągiem zapytania. Łatwość dostępu do tych informacji jest ważna podczas rozwiązywania problemów z usługą błędna WCF.

Istnieją dwa sposoby uwidocznienia punktu końcowego kondycji i publikowania informacji o kondycji usługi WCF:

- Za poorednictwem kodu. Na przykład:

  ```csharp
  ServiceHost host = new ServiceHost(typeof(Service1),
                     new Uri("http://contoso:81/Service1"));
  ServiceHealthBehavior healthBehavior =
      host.Description.Behaviors.Find<ServiceHealthBehavior>();
  if (healthBehavior == null)
  {
     healthBehavior = new ServiceHealthBehavior();
  }
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

- Przy użyciu pliku konfiguracji. Na przykład:

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

Za pomocą parametrów zapytania, takich `OnServiceFailure`jak, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`) można zbadać stan kondycji usługi, a dla każdego parametru zapytania można określić kod odpowiedzi HTTP. Jeśli kod odpowiedzi HTTP zostanie pominięty dla parametru zapytania, domyślnie używany jest kod odpowiedzi HTTP 503. Na przykład:

- OnServiceFailure:`https://contoso:81/Service1?health&OnServiceFailure=450`

  Kod stanu odpowiedzi HTTP 450 jest zwracany, gdy element ServiceHost [. State](xref:System.ServiceModel.Channels.CommunicationObject.State) jest większy <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>niż.
Parametry zapytania i przykłady:

- OnDispatcherFailure:`https://contoso:81/Service1?health&OnDispatcherFailure=455`

  Kod stanu odpowiedzi HTTP 455 jest zwracany, gdy stan dowolnego z dyspozytorów kanałów jest większy niż <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.

- OnListenerFailure:`https://contoso:81/Service1?health&OnListenerFailure=465`

  Kod stanu odpowiedzi HTTP 465 jest zwracany, gdy stan dowolnego odbiornika kanałów jest większy niż <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.

- OnThrottlePercentExceeded:`https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`

  Określa wartość procentową {1 – 100}, która wyzwala odpowiedź i kod odpowiedzi HTTP {200 – 599}. W tym przykładzie:

  - Jeśli wartość procentowa jest większa niż 95, zwracany jest kod odpowiedzi HTTP 500.

  - Jeśli zostanie zwrócona wartość procentowa lub z przedziału od 70 do 95, 350.

  - W przeciwnym razie jest zwracana 200.

Stan kondycji usługi może być wyświetlany w formacie HTML przez określenie ciągu zapytania, takiego `https://contoso:81/Service1?health` jak lub w XML, przez określenie ciągu zapytania `https://contoso:81/Service1?health&Xml`, takiego jak. Ciąg zapytania, na `https://contoso:81/Service1?health&NoContent` przykład zwraca pustą stronę HTML.

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Ulepszenia o wysokiej rozdzielczości DPI**

W .NET Framework 4,8, WPF dodaje obsługę skalowania DPI na poziomie v2 i trybu mieszanego. Dodatkowe informacje na temat programowania wysokiej rozdzielczości DPI można znaleźć [w temacie Tworzenie aplikacji klasycznych o wysokiej rozdzielczości DPI w systemie Windows](/desktop/hidpi/high-dpi-desktop-application-development-on-windows) .

.NET Framework 4,8 usprawnia obsługę hostowanych funkcji HWND i Windows Forms współdziałania w aplikacjach WPF o wysokiej rozdzielczości DPI na platformach obsługujących skalowanie DPI w trybie mieszanym (począwszy od aktualizacji systemu Windows 10 kwietnia 2018). W przypadku, gdy w trybie mieszanym skalowanie wartościowe lub kontrolki Windows Forms są tworzone jako okna z funkcją rozdzielczości DPI, wywoływanie funkcji [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) i [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext)może być obsługiwane w aplikacji WPF w wersji 2 dla monitora i ma rozmiar i odpowiednio skalowane. Taka hostowana zawartość nie jest renderowana w natywnej rozdzielczości DPI; Zamiast tego system operacyjny skaluje hostowaną zawartość do odpowiedniego rozmiaru. Obsługa trybu sygnalizacji DPI na monitor v2 umożliwia również hostowanie formantów WPF (tj. nadrzędnych) w oknie macierzystym w aplikacji o wysokiej rozdzielczości DPI.

Aby włączyć obsługę skalowania wysokiej rozdzielczości DPI w trybie mieszanym, można ustawić następujące przełączniki [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w pliku konfiguracyjnym aplikacji:

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a>Środowisko uruchomieniowe języka wspólnego

Środowisko uruchomieniowe w .NET Framework 4,8 obejmuje następujące zmiany i usprawnienia:

**Ulepszenia kompilatora JIT**. Kompilator just-in-Time (JIT) w .NET Framework 4,8 jest oparty na kompilatorze JIT w programie .NET Core 2,1. Wiele optymalizacji i wszystkie poprawki błędów kompilatora JIT programu .NET Core 2,1 są zawarte w kompilatorze JIT .NET Framework 4,8.

**Ulepszenia programu Ngen**. Środowisko uruchomieniowe poprawiło zarządzanie pamięcią dla obrazów [natywnego generatora obrazów](../tools/ngen-exe-native-image-generator.md) (Ngen), dzięki czemu dane mapowane z obrazów NGen nie są rezydentem pamięci. Pozwala to zmniejszyć ilość miejsca dostępnego na ataki próbujące wykonać dowolny kod, modyfikując pamięć, która zostanie wykonana.

**Skanowanie w poszukiwaniu złośliwego oprogramowania dla wszystkich zestawów**. W poprzednich wersjach .NET Framework środowisko uruchomieniowe skanuje wszystkie zestawy ładowane z dysku przy użyciu programu Windows Defender lub oprogramowania chroniącego przed złośliwym kodem. Jednak zestawy załadowane z innych źródeł, na przykład przez <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> metodę, nie są skanowane i mogą potencjalnie zawierać niewykryte złośliwe oprogramowanie. Począwszy od .NET Framework 4,8 uruchomionego w systemie Windows 10 środowisko uruchomieniowe wyzwala skanowanie przez rozwiązania chroniące przed złośliwym kodem [(AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal).

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a>Co nowego w .NET Framework 4.7.2

.NET Framework 4.7.2 zawiera nowe funkcje w następujących obszarach:

- [Klasy bazowe](#core-472)
- [ASP.NET](#asp-net472)
- [Sieć](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

Dalszy nacisk na .NET Framework 4.7.2 jest ulepszony, co pozwala aplikacji zapewnić odpowiednie środowisko dla użytkowników technologii pomocniczej. Informacje o ulepszeniach ułatwień dostępu w programie .NET Framework 4.7.2 można znaleźć w temacie [co nowego w ułatwieniach dostępu w .NET Framework](whats-new-in-accessibility.md).

<a name="core-472" />

#### <a name="base-classes"></a>Klas podstawowych

.NET Framework 4.7.2 oferuje dużą liczbę ulepszeń kryptograficznych, lepszą obsługę dekompresji archiwów ZIP oraz dodatkowe interfejsy API kolekcji.

**Nowe przeciążenia RSA. Tworzenie i DSA. Create**

<xref:System.Security.Cryptography.DSA> <xref:System.Security.Cryptography.RSA> Metody i umożliwiają<xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> podawanie kluczowych parametrów podczas tworzenia wystąpienia nowego lub klucza. <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> Umożliwiają one zastępowanie kodu podobne do następujących:

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

z kodem podobnym do tego:

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

Metody <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSA> i <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> pozwalają generować nowe lub<xref:System.Security.Cryptography.RSA> klucze o określonym rozmiarze klucza. Na przykład:

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

**Konstruktory Rfc2898DeriveBytes akceptują nazwę algorytmu wyznaczania wartości skrótu**

Klasa ma trzy nowe konstruktory <xref:System.Security.Cryptography.HashAlgorithmName> z parametrem, który identyfikuje algorytm HMAC, który ma być używany podczas wyprowadzania kluczy. <xref:System.Security.Cryptography.Rfc2898DeriveBytes> Zamiast używać algorytmu SHA-1, deweloperzy powinni używać algorytmu HMAC opartego na algorytmie SHA-2, takiego jak SHA-256, jak pokazano w następującym przykładzie:

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

Import PFX może opcjonalnie załadować klucze prywatne bezpośrednio z pamięci, pomijając dysk twardy. Gdy nowa <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flaga jest określona <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> w konstruktorze lub jeden <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> z przeciążeń metody, klucze prywatne zostaną załadowane jako klucze tymczasowe. Zapobiega to widocznym kluczom na dysku. Ale

- Ponieważ klucze nie są utrwalane na dysku, certyfikaty załadowane z tą flagą nie są dobrym kandydatami do dodania do X509Store.

- Klucze ładowane w ten sposób są prawie zawsze ładowane za pośrednictwem systemu Windows CNG. W związku z tym obiekty wywołujące muszą uzyskać dostęp do klucza prywatnego przez wywoływanie metod rozszerzających, takich jak [certyfikat. GetRSAPrivateKey ()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> Właściwość nie działa.

- Ponieważ Starsza <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> właściwość nie działa z certyfikatami, deweloperzy powinni wykonać rygorystyczne testy przed przełączeniem do kluczy tymczasowych.

**Programowe tworzenie certyfikatów podpisywania certyfikatów PKCS # 10 oraz certyfikaty klucza publicznego X. 509**

Począwszy od .NET Framework 4.7.2, obciążenia mogą generować żądania podpisania certyfikatu (przedstawiciele klienta), co umożliwia przygotowanie generacji żądań certyfikatów do istniejących narzędzi. Jest to często przydatne w scenariuszach testowych.

Aby uzyskać więcej informacji i przykładów kodu, zobacz "programowe tworzenie żądań podpisywania certyfikatów PKCS # 10 oraz certyfikaty klucza publicznego X. 509" w [blogu platformy .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Nowi członkowie SignerInfo**

Począwszy od .NET Framework 4.7.2, <xref:System.Security.Cryptography.Pkcs.SignerInfo> Klasa ujawnia więcej informacji o sygnaturze. Możesz pobrać wartość <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> właściwości, aby określić algorytm podpisu używany przez program podpisujący. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>można wywołać, aby uzyskać kopię podpisu kryptograficznego dla tej osoby podpisującej.

**Pozostawienie opakowanego strumienia otwartego po usunięciu CryptoStream**

Począwszy od .NET Framework 4.7.2, <xref:System.Security.Cryptography.CryptoStream> Klasa ma dodatkowy Konstruktor, który pozwala <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> nie zamykać opakowanego strumienia. Aby pozostawić opakowany strumień otwarty po usunięciu <xref:System.Security.Cryptography.CryptoStream> wystąpienia, wywołaj nowego <xref:System.Security.Cryptography.CryptoStream> konstruktora w następujący sposób:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**Dekompresja zmian w DeflateStream**

Począwszy od .NET Framework 4.7.2, implementacja operacji dekompresji w <xref:System.IO.Compression.DeflateStream> klasie została zmieniona w taki sposób, aby domyślnie używała natywnych interfejsów API systemu Windows. Zwykle powoduje to znaczne zwiększenie wydajności.

Obsługa dekompresji przy użyciu interfejsów API systemu Windows jest włączona domyślnie dla aplikacji, które są przeznaczone .NET Framework 4.7.2. Aplikacje, które są przeznaczone dla wcześniejszych wersji .NET Framework ale działają w ramach .NET Framework 4.7.2, mogą przystąpić do tego zachowania, dodając następujący [przełącznik AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do pliku konfiguracji aplikacji:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**Dodatkowe interfejsy API kolekcji**

.NET Framework 4.7.2 dodaje wiele nowych interfejsów API do <xref:System.Collections.Generic.SortedSet%601> typów i. <xref:System.Collections.Generic.HashSet%601> Należą do nich następujące elementy:

- `TryGetValue`metody, które zwiększają wzorzec try użyty w innych typach kolekcji do tych dwóch typów. Metody są następujące:

  - [Public bool HashSet —\<T >. TryGetValue (T equalValue, out T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [Public bool SortedSet\<T >. TryGetValue (T equalValue, out T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- `Enumerable.To*`metody rozszerzające, które konwertują kolekcję na <xref:System.Collections.Generic.HashSet%601>:

  - [publiczne statyczne HashSet —\<TSource > ToHashSet\<TSource > (w tym\<interfejsie IEnumerable TSource > Source)](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [publiczne statyczne HashSet —\<TSource > ToHashSet\<TSource > (to IEnumerable\<TSource > source, IEqualityComparer\<TSource > porównując)](xref:System.Linq.Enumerable.ToHashSet%2A)

- Nowe <xref:System.Collections.Generic.HashSet%601> konstruktory, które umożliwiają ustawienie pojemności kolekcji, która daje korzyść wydajności, gdy wiesz, jaki jest rozmiar <xref:System.Collections.Generic.HashSet%601> z góry:

  - [Public HashSet — (int)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
  - [Public HashSet — (pojemność int, IEqualityComparer\<T > funkcja porównująca)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

Klasa zawiera nowe przeciążenia <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> metod i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> , aby pobrać wartość ze słownika lub dodać ją, jeśli nie zostanie znaleziona, i dodać wartość do słownika lub zaktualizować ją, jeśli już istnieje. <xref:System.Collections.Concurrent.ConcurrentDictionary%602>

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

[Iniekcja zależności (di)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) oddziela obiekty i ich zależności, tak aby kod obiektu nie był już zmieniany tylko z powodu zmiany zależności. Podczas tworzenia aplikacji ASP.NET, które są przeznaczone dla .NET Framework 4.7.2, można:

- Używaj opartych na metodach, opartych na interfejsach i iniekcji konstruktorów w programach [obsługi i modułach](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [wystąpieniach stron](xref:System.Web.UI.Page)i [kontrolach użytkownika](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) projektów aplikacji sieci Web ASP.NET.

- Używaj opartych na metodzie i iniekcji opartej na interfejsach w programach [obsługi i modułach](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [wystąpieniach stron](xref:System.Web.UI.Page)i [kontrolach użytkowników](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) w projektach witryn sieci Web ASP.NET.

- Podłącz różne struktury iniekcji zależności.

**Obsługa plików cookie tego samego miejsca**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) zapobiega wysyłaniu plików cookie przez przeglądarkę wraz z żądaniem między lokacjami. .NET Framework 4.7.2 dodaje właściwość <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> , której wartość <xref:System.Web.SameSiteMode?displayProperty=nameWithType> jest składową wyliczenia. Jeśli wartość to <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> lub <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET dodaje `SameSite` atrybut do nagłówka Set-cookie. Obsługa SameSite dotyczy <xref:System.Web.HttpCookie> obiektów, <xref:System.Web.Security.FormsAuthentication> a <xref:System.Web.SessionState> także plików cookie.

Można ustawić SameSite dla <xref:System.Web.HttpCookie> obiektu w następujący sposób:

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

Możesz również skonfigurować pliki cookie SameSite na poziomie aplikacji, modyfikując plik Web. config:

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

Możesz dodać SameSite dla <xref:System.Web.Security.FormsAuthentication> plików cookie i <xref:System.Web.SessionState> zmodyfikować plik Web config:

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

.NET Framework 4.7.1 dodać osiem właściwości do <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> klasy. Jednak dwie wywołały <xref:System.PlatformNotSupportedException>. .NET Framework 4.7.2 teraz udostępnia implementację tych właściwości. Właściwości są następujące:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a>SQLClient

**Obsługa Azure Active Directory uwierzytelniania uniwersalnego i uwierzytelniania wieloskładnikowego**

Rosnące wymagania dotyczące zgodności i zabezpieczeń wymagają, aby wielu klientów korzystało z uwierzytelniania wieloskładnikowego (MFA). Ponadto obecnie najlepsze rozwiązania uniemożliwiają uwzględnienie haseł użytkowników bezpośrednio w parametrach połączenia. Aby można było obsługiwać te zmiany, .NET Framework 4.7.2 rozszerza [Parametry połączenia SqlClient](xref:System.Data.SqlClient.SqlConnection.ConnectionString) przez dodanie nowej wartości "Active Directory Interactive" dla istniejącego słowa kluczowego "Authentication" do obsługi uwierzytelniania MFA i [usługi Azure AD](/azure/sql-database/sql-database-aad-authentication-configure). Nowa metoda interaktywna obsługuje natywnych i federacyjnych użytkowników usługi Azure AD, a także użytkowników-Gości usługi Azure AD. Gdy ta metoda jest używana, uwierzytelnianie MFA narzucone przez usługę Azure AD jest obsługiwane dla baz danych SQL. Ponadto proces uwierzytelniania żąda hasła użytkownika w celu przestrzegania najlepszych rozwiązań w zakresie zabezpieczeń.

W poprzednich wersjach .NET Framework łączności SQL obsługiwane są <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> tylko opcje i. <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> Oba te elementy są częścią nieinteraktywnego [protokołu ADAL](/azure/active-directory/develop/active-directory-authentication-libraries), który nie obsługuje usługi MFA. Dzięki nowej <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> opcji łączność SQL obsługuje uwierzytelnianie MFA, a także istniejące metody uwierzytelniania (hasło i uwierzytelnianie zintegrowane), które umożliwiają użytkownikom interaktywne wprowadzanie haseł użytkowników bez utrwalania haseł w połączeniu. parametry.

Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz "SQL--usługa Azure AD Universal and wieloskładnikowe Authentication Support" w [blogu platformy .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Obsługa Always Encrypted wersja 2**

Program NET Framework 4.7.2 dodaje obsługę dla Always Encrypted opartych na enklawy. Oryginalna wersja Always Encrypted jest technologią szyfrowania po stronie klienta, w której klucze szyfrowania nigdy nie opuszczają klienta. W Always Encrypted opartych na enklawy klient może opcjonalnie wysłać klucze szyfrowania do bezpiecznej enklawy, która jest bezpieczną jednostką obliczeniową, która może być traktowana jako część SQL Server, ale ten kod SQL Server nie może naruszać. Aby można było obsługiwać Always Encrypted opartych na enklawy, .NET Framework 4.7.2 dodaje następujące typy i elementy <xref:System.Data.SqlClient> członkowskie do przestrzeni nazw:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, który określa identyfikator URI Always Encrypted opartych na enklawy.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, która jest klasą abstrakcyjną, z której pochodzą wszyscy dostawcy enklawy.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, który hermetyzuje stan danej sesji enklawy.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, która zapewnia parametry zaświadczania używane przez SQL Server do uzyskiwania informacji wymaganych do wykonania określonego protokołu zaświadczania.

Następnie plik konfiguracji aplikacji określa konkretną implementację klasy abstrakcyjnej <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> , która udostępnia funkcje dostawcy enklawy. Przykład:

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

Podstawowy przepływ Always Encrypted opartych na enklawy to:

1. Użytkownik tworzy SQL Server połączenie AlwaysEncrypted, które obsługuje Always Encrypted oparte na enklawy. Sterownik kontaktuje się z usługą zaświadczania, aby upewnić się, że nawiązuje połączenie z właściwym enklawy.

1. Po zaświadczeniu enklawy sterownik ustanawia bezpieczny kanał z bezpiecznym enklawy hostowanym na SQL Server.

1. Sterownik udostępnia klucze szyfrowania autoryzowane przez klienta z bezpiecznym enklawy na czas trwania połączenia SQL.

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Znajdowanie ResourceDictionaries według źródła**

Począwszy od .NET Framework 4.7.2, asystent diagnostyczny może zlokalizować <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> , który został utworzony na podstawie danego źródłowego identyfikatora URI. (Ta funkcja jest używana przez asystentów diagnostycznych, a nie przez aplikacje produkcyjne). Asystent diagnostyczny, taki jak funkcja "Edytuj i Kontynuuj" programu Visual Studio, umożliwia użytkownikowi edytowanie ResourceDictionary z zamiarem, że zmiany zostaną zastosowane do uruchomionej aplikacji. Jednym z kroków osiągnięcia tego celu jest znalezienie wszystkich ResourceDictionaries, że uruchomiona aplikacja została utworzona na podstawie edytowanego słownika. Na przykład aplikacja może zadeklarować element ResourceDictionary, którego zawartość jest kopiowana z danego źródłowego identyfikatora URI:

```xml
<ResourceDictionary Source="MyRD.xaml">
```

Asystent diagnostyczny, który edytuje pierwotne znaczniki w *MyRD. XAML* , może użyć nowej funkcji do zlokalizowania słownika. Funkcja jest implementowana przez nową metodę <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>statyczną. Asystent diagnostyczny wywołuje nową metodę przy użyciu bezwzględnego identyfikatora URI, który identyfikuje oryginalne znaczniki, jak pokazano w poniższym kodzie:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

Metoda zwraca puste wartości wyliczalne <xref:System.Windows.Diagnostics.VisualDiagnostics> [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  , chyba że jest włączona, a zmienna środowiskowa jest ustawiona.

**Znajdowanie właścicieli ResourceDictionary**

Począwszy od .NET Framework 4.7.2, asystent diagnostyczny może zlokalizować właścicieli danego <xref:Windows.UI.Xaml.ResourceDictionary>elementu. (Funkcja jest używana przez asystentów diagnostycznych, a nie przez aplikacje produkcyjne). Za każdym razem <xref:Windows.UI.Xaml.ResourceDictionary>, gdy zostanie wprowadzona zmiana w programie, WPF automatycznie odnajdzie wszystkie odwołania [DynamicResource —](../wpf/advanced/dynamicresource-markup-extension.md) , które mogą mieć wpływ na zmianę.

Asystent diagnostyczny, taki jak obiekt "Edytuj i Kontynuuj" programu Visual Studio, może chcieć przedłużyć ten sposób, aby obsługiwał odwołania [StaticResource](../wpf/advanced/staticresource-markup-extension.md) . Pierwszym krokiem w tym procesie jest znalezienie właścicieli słownika; oznacza to, aby znaleźć wszystkie obiekty, których `Resources` Właściwość odwołuje się do słownika (bezpośrednio lub pośrednio <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> przez właściwość). Trzy nowe metody statyczne zaimplementowane dla <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> klasy, po jednej dla każdego z typów podstawowych, które `Resources` mają właściwość, obsługują ten krok:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Te metody zwracają pustą wartość wyliczalną <xref:System.Windows.Diagnostics.VisualDiagnostics> [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  , chyba że jest włączona, a zmienna środowiskowa jest ustawiona.

**Znajdowanie odwołań StaticResource**

Asystent diagnostyczny może teraz odbierać powiadomienie za każdym razem, gdy zostanie rozpoznane odwołanie [StaticResource](../wpf/advanced/staticresource-markup-extension.md) . (Funkcja jest używana przez asystentów diagnostycznych, a nie przez aplikacje produkcyjne). Asystent diagnostyczny, taki jak funkcja "Edytuj i Kontynuuj" programu Visual Studio, może chcieć zaktualizować wszystkie zastosowania zasobu, gdy jego wartość <xref:Windows.UI.Xaml.ResourceDictionary> zmienia się. WPF robi to automatycznie w odniesieniu do [DynamicResource —](../wpf/advanced/dynamicresource-markup-extension.md) , ale celowo nie robi to w odniesieniu do [StaticResource](../wpf/advanced/staticresource-markup-extension.md) . Począwszy od .NET Framework 4.7.2, asystent diagnostyczny może użyć tych powiadomień, aby zlokalizować te zastosowania zasobu statycznego.

Powiadomienie jest implementowane przez nowe <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> zdarzenie:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

To zdarzenie jest wywoływane za każdym razem, gdy środowisko uruchomieniowe rozwiązuje odwołanie [StaticResource](../wpf/advanced/staticresource-markup-extension.md) . Argumenty opisują rozdzielczość i wskazują obiekt i właściwość, które obsługują odwołanie [StaticResource](../wpf/advanced/staticresource-markup-extension.md) , oraz <xref:Windows.UI.Xaml.ResourceDictionary> klucz używany do rozwiązania: <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs>

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

Zdarzenie nie zostało zgłoszone (a jego `add` akcesor jest ignorowany) <xref:System.Windows.Diagnostics.VisualDiagnostics> , chyba że jest [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)włączona i  zmienna środowiskowa jest ustawiona.

#### <a name="clickonce"></a>ClickOnce

Aplikacje obsługujące HDPI dla Windows Forms, Windows Presentation Foundation (WPF) i Visual Studio Tools dla pakietu Office (VSTO) można wdrożyć przy użyciu technologii ClickOnce. Jeśli w manifeście aplikacji zostanie znaleziony następujący wpis, wdrożenie zakończy się pomyślnie w .NET Framework 4.7.2:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

W przypadku aplikacji Windows Forms poprzednie obejście ustawienia rozpoznawania DPI w pliku konfiguracyjnym aplikacji, a nie manifestu aplikacji, nie jest już konieczne do pomyślnego wdrożenia technologii ClickOnce.

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a>Co nowego w .NET Framework 4.7.1

.NET Framework 4.7.1 zawiera nowe funkcje w następujących obszarach:

- [Klasy bazowe](#core471)
- [Środowisko uruchomieniowe języka wspólnego (CLR)](#clr)
- [Sieć](#net471)
- [ASP.NET](#asp-net471)

Ponadto najważniejszym fokusem w .NET Framework 4.7.1 jest ulepszony ułatwienia dostępu, dzięki czemu aplikacja może zapewnić odpowiednie środowisko dla użytkowników technologii pomocniczej. Informacje o ulepszeniach ułatwień dostępu w programie .NET Framework 4.7.1 można znaleźć w temacie [co nowego w ułatwieniach dostępu w .NET Framework](whats-new-in-accessibility.md).

<a name="core471" />

#### <a name="base-classes"></a>Klas podstawowych

**Obsługa .NET Standard 2,0**

[.NET Standard](../../standard/net-standard.md) definiuje zestaw interfejsów API, które muszą być dostępne dla każdej implementacji platformy .NET, która obsługuje tę wersję Standard. .NET Framework 4.7.1 w pełni obsługuje .NET Standard 2,0 i dodaje [około 200 interfejsów API](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) , które są zdefiniowane w .NET Standard 2,0 i brakuje ich w .NET Framework 4.6.1, 4.6.2 i 4,7. (Należy zauważyć, że te wersje .NET Framework obsługują .NET Standard 2,0 tylko wtedy, gdy w systemie docelowym wdrożono również dodatkowe pliki obsługi .NET Standard). Aby uzyskać więcej informacji, zobacz "BCL-.NET Standard 2,0 Support" w blogu [.NET Framework środowiska uruchomieniowego 4.7.1 i kompilatora](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .

**Obsługa konstruktorów konfiguracji**

Konstruktory konfiguracji pozwalają deweloperom na dynamiczne Wstawianie i kompilowanie ustawień konfiguracji aplikacji w czasie wykonywania. Konstruktory konfiguracji niestandardowej mogą służyć do modyfikowania istniejących danych w sekcji konfiguracyjnej lub do tworzenia sekcji konfiguracyjnej w całości od podstaw. Bez konstruktorów konfiguracji, pliki. config są statyczne, a ich ustawienia są definiowane jakiś czas przed uruchomieniem aplikacji.

Aby utworzyć niestandardowy Konstruktor konfiguracji, należy uzyskać swój Konstruktor z klasy abstrakcyjnej <xref:System.Configuration.ConfigurationBuilder> i <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> zastąpić go i <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. Możesz również zdefiniować kompilacje w pliku. config. Aby uzyskać więcej informacji, zobacz sekcję "konstruktorzy konfiguracji" w blogu [.NET Framework 4.7.1 ASP.NET i Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) post.

**Wykrywanie funkcji w czasie wykonywania**

<xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> Klasa udostępnia mechanizm umożliwiający określenie, czy wstępnie zdefiniowana funkcja jest obsługiwana w danej implementacji platformy .NET w czasie kompilacji czy w czasie wykonywania. W czasie kompilacji kompilator może sprawdzić, czy określone pole istnieje, aby określić, czy funkcja jest obsługiwana; Jeśli tak, może to emitować kod, który korzysta z tej funkcji. W czasie wykonywania aplikacja może wywołać <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metodę przed emitowaniem kodu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Dodawanie metody pomocnika do opisywania funkcji obsługiwanych przez środowisko uruchomieniowe](https://github.com/dotnet/corefx/issues/17116).

**Typy krotek wartości można serializować**

Począwszy od .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> a skojarzone typy ogólne są oznaczone jako możliwe do [serializacji](xref:System.SerializableAttribute), co umożliwia serializacji binarnej. Powinno to ułatwić Migrowanie typów krotek, takich <xref:System.Tuple%603> jak <xref:System.Tuple%604>i, do typów krotek wartości. Aby uzyskać więcej informacji, zobacz "kompilator--ValueTuple jest możliwy do serializacji" w blogu [.NET Framework środowiska uruchomieniowego 4.7.1 i funkcje kompilatora](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .

**Obsługa odwołań tylko do odczytu**

.NET Framework 4.7.1 dodaje <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>. Ten atrybut jest używany przez kompilatory języka do oznaczania elementów członkowskich, które mają zwracane typy lub parametry odwołania tylko do odczytu. Aby uzyskać więcej informacji, zobacz "kompilator--support for ReadOnlyReferences" w wpisie .NET Framework w blogu [środowiska uruchomieniowego 4.7.1 i funkcji kompilatora](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) . Aby uzyskać informacje na temat zwracanych wartości, zobacz odwołania do zwracanych wartości [orazC# wartości lokalne ref (Przewodnik)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) i [ref Return (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />

#### <a name="common-language-runtime-clr"></a>Środowisko uruchomieniowe języka wspólnego (CLR)

**Udoskonalenia wydajności odzyskiwania pamięci**

Zmiany w wyrzucaniu elementów bezużytecznych (GC) w .NET Framework 4.7.1 poprawić ogólną wydajność, szczególnie w przypadku alokacji dużego obiektu sterty (LOH). W .NET Framework 4.7.1, osobne blokady są używane dla sterty małego obiektu i alokacji LOH, co umożliwia przydzielanie LOH, gdy w tle GC (BGC) jest czyszczony raport o kondycji. W związku z tym aplikacje, które tworzą dużą liczbę alokacji LOH, powinny mieć zmniejszenie rywalizacji o blokadę alokacji i lepszą wydajność. Aby uzyskać więcej informacji, zobacz sekcję "ulepszenia wydajności środowiska uruchomieniowego GC" w blogu [.NET Framework środowiska uruchomieniowego 4.7.1 i funkcji kompilatora](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .

<a name="net471"/>

#### <a name="networking"></a>Obsługa sieci

**Obsługa algorytmu SHA-2 dla komunikatu. algorytm**

W .NET Framework 4,7 i wcześniejszych wersjach <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> właściwość obsługuje tylko <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> wartości i <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> . Począwszy od .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, i <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> są również obsługiwane. Określa, czy ta wartość jest faktycznie używana, zależy od usługi MSMQ <xref:System.Messaging.Message> , ponieważ samo wystąpienie nie wykonuje mieszania, ale po prostu przekazuje wartości do usługi MSMQ. Aby uzyskać więcej informacji, zobacz sekcję "Obsługa protokołu SHA-2 dla komunikatu. algorytm" w wpisie w blogu [.NET Framework 4.7.1 ASP.NET i Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .

<a name="asp-net471" />

#### <a name="aspnet"></a>ASP.NET

**Kroki wykonywania w aplikacjach ASP.NET**

ASP.NET przetwarza żądania we wstępnie zdefiniowanym potoku zawierającym 23 zdarzenia. ASP.NET wykonuje każdy program obsługi zdarzeń jako krok wykonania. W wersjach programu ASP.NET do .NET Framework 4,7 ASP.NET nie można przepływać kontekstu wykonywania z powodu przełączenia między wątkami macierzystymi i zarządzanymi. Zamiast tego ASP.NET selektywnie przepływy <xref:System.Web.HttpContext>tylko. Począwszy od .NET Framework 4.7.1, <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> Metoda umożliwia również modułom przywracanie danych otoczenia. Ta funkcja jest przeznaczona dla bibliotek objętych śledzeniem, profilem, diagnostyką lub transakcjami, na przykład z myślą o przepływie wykonywania aplikacji. Aby uzyskać więcej informacji, zobacz "funkcja kroku wykonywania ASP.NET" w wpisie w blogu [.NET Framework 4.7.1 ASP.NET i Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .

**Analiza ASP.NET HttpCookie**

.NET Framework 4.7.1 zawiera nową metodę, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>która stanowi standardowy sposób <xref:System.Web.HttpCookie> tworzenia obiektu na podstawie ciągu i dokładnego przypisywania wartości cookie, takich jak data wygaśnięcia i ścieżka. Aby uzyskać więcej informacji, zobacz "Analiza ASP.NET HttpCookie" w blogu [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .

**Opcje wyznaczania wartości skrótu SHA-2 dla poświadczeń uwierzytelniania ASP.NET Forms**

W .NET Framework 4,7 i wcześniejszych wersjach ASP.NET zezwolenie deweloperom na przechowywanie poświadczeń użytkownika z użyciem skrótów haseł w plikach konfiguracji przy użyciu algorytmu MD5 lub SHA1. Począwszy od .NET Framework 4.7.1, ASP.NET obsługuje również nowe bezpieczne opcje skrótu SHA-2, takie jak SHA256, SHA384 i SHA512. Algorytm SHA1 pozostaje domyślny, a w pliku konfiguracyjnym sieci Web można zdefiniować niedomyślnego algorytmu wyznaczania wartości skrótu. Przykład:

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

## <a name="whats-new-in-net-framework-47"></a>Co nowego w .NET Framework 4,7

.NET Framework 4,7 zawiera nowe funkcje w następujących obszarach:

- [Klasy bazowe](#Core47)
- [Sieć](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Aby uzyskać listę nowych interfejsów API dodanych do .NET Framework 4,7, zobacz [.NET Framework 4,7 zmiany interfejsu API](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) w serwisie GitHub. Aby zapoznać się z listą ulepszeń funkcji i poprawek błędów w .NET Framework 4,7, zobacz [.NET Framework 4,7 Lista zmian](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) w serwisie GitHub.  Aby uzyskać dodatkowe informacje, zobacz temat [ogłaszanie .NET Framework 4,7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) w blogu platformy .NET.

<a name="Core47" />

#### <a name="base-classes"></a>Klas podstawowych

.NET Framework 4,7 usprawnia serializację przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:

**Rozszerzona funkcjonalność przy użyciu kryptografii krzywej eliptycznej (ECC)** *

W .NET Framework 4,7 `ImportParameters(ECParameters)` dodano metody <xref:System.Security.Cryptography.ECDsa> do klas i <xref:System.Security.Cryptography.ECDiffieHellman> , aby umożliwić obiektowi reprezentowania już ustanowionego klucza. Dodano `ExportParameters(Boolean)` również metodę eksportu klucza przy użyciu jawnych parametrów krzywej.

.NET Framework 4,7 również dodaje obsługę dodatkowych krzywych (w tym zestawu krzywej Brainpool) i dodał wstępnie zdefiniowane definicje w celu ułatwienia tworzenia przy użyciu nowych <xref:System.Security.Cryptography.ECDsa.Create%2A> i <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> fabrycznych metod.

[Przykład ulepszeń kryptografii .NET Framework 4,7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) w serwisie GitHub.

**Lepsza obsługa znaków kontrolnych przez Klasa DataContractJsonSerializer**

W .NET Framework 4,7, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializacji znaki kontrolne zgodne ze standardem ECMAScript 6. To zachowanie jest domyślnie włączone dla aplikacji, które są przeznaczone dla .NET Framework 4,7 i jest funkcją wyboru dla aplikacji, które działają w ramach .NET Framework 4,7, ale celem jest poprzednia wersja .NET Framework. Aby uzyskać więcej informacji, zobacz [przekierowywanie zmian w .NET Framework 4,7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />

#### <a name="networking"></a>Obsługa sieci

.NET Framework 4,7 dodaje następującą funkcję powiązaną z siecią:

**Domyślna obsługa systemu operacyjnego dla protokołów TLS***

Stos protokołu TLS, który jest używany przez <xref:System.Net.Security.SslStream?displayProperty=nameWithType> składniki stosujące i w górę, takie jak http, FTP i SMTP, umożliwia deweloperom korzystanie z domyślnych protokołów protokołu TLS obsługiwanych przez system operacyjny. Deweloperzy nie muszą już wykodować wersji TLS.

<a name="ASP-NET47" />

#### <a name="aspnet"></a>ASP.NET

W .NET Framework 4,7 ASP.NET zawiera następujące nowe funkcje:

**Rozszerzalność pamięci podręcznej obiektów**

Począwszy od .NET Framework 4,7, ASP.NET dodaje nowy zestaw interfejsów API, które umożliwiają deweloperom zastąpienie domyślnych implementacji ASP.NET dla pamięci podręcznej obiektów i pamięci. Deweloperzy mogą teraz zastąpić dowolne z następujących trzech składników, jeśli implementacja ASP.NET nie jest odpowiednia:

- **Magazyn pamięci podręcznej obiektów**. Za pomocą nowej sekcji Konfiguracja dostawców pamięci podręcznej deweloperzy mogą podłączyć nowe implementacje pamięci podręcznej obiektów dla aplikacji ASP.NET przy użyciu nowego interfejsu **ICacheStoreProvider** .

- **Monitorowanie pamięci**. Domyślny monitor pamięci w programie ASP.NET powiadamia aplikacje, gdy działają w pobliżu skonfigurowanego limitu bajtów prywatnych dla tego procesu lub gdy na komputerze jest mało dostępnej fizycznej pamięci RAM. Gdy te limity zbliżają się, powiadomienia są wywoływane. W przypadku niektórych aplikacji powiadomienia są wywoływane zbyt blisko skonfigurowanych limitów, aby umożliwić korzystanie z przydatnych reakcji. Deweloperzy mogą teraz pisać własne monitory pamięci, aby zamienić wartość domyślną przy użyciu <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> właściwości.

- **Reakcje z limitem pamięci**. Domyślnie ASP.NET próbuje przyciąć pamięć podręczną obiektów i okresowo wywoływać <xref:System.GC.Collect%2A?displayProperty=nameWithType> , gdy limit procesu prywatnego bajtów jest bliski. W przypadku niektórych aplikacji częstotliwość wywołań <xref:System.GC.Collect%2A?displayProperty=nameWithType> lub ilość pamięci podręcznej, która jest przycinana, jest nieskuteczna. Deweloperzy mogą teraz zastąpić lub uzupełnić zachowanie domyślne, subskrybując implementacje **IObserver** do monitora pamięci aplikacji.

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) dodaje następujące funkcje i zmiany:

**Możliwość skonfigurowania domyślnych ustawień zabezpieczeń komunikatów do protokołu TLS 1,1 lub TLS 1,2**

Począwszy od .NET Framework 4,7, usługa WCF umożliwia skonfigurowanie programu TSL 1,1 lub TLS 1,2 oprócz protokołu SSL 3,0 i TSL 1,0 jako domyślnego protokołu zabezpieczeń komunikatów. Jest to ustawienie zgody. Aby ją włączyć, należy dodać następujący wpis do pliku konfiguracji aplikacji:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**Zwiększona niezawodność aplikacji WCF i serializacji WCF**

Program WCF zawiera szereg zmian w kodzie, które eliminują sytuacje wyścigu, co poprawia wydajność i niezawodność opcji serializacji. Należą do nich następujące elementy:

- Lepsza obsługa mieszania kodu asynchronicznego i synchronicznego w wywołaniach **SocketConnection. BeginRead** i **SocketConnection. Read**.
- Zwiększona niezawodność podczas przerywania połączenia z **SharedConnectionListener** i **DuplexChannelBinder**.
- Ulepszona niezawodność operacji serializacji podczas wywoływania <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> metody.
- Zwiększona niezawodność podczas usuwania oczekiwania przez wywołanie metody **ChannelSynchronizer. RemoveWaiter** .

<a name="wf47" />

#### <a name="windows-forms"></a>Windows Forms

W .NET Framework 4,7 Windows Forms Ulepszona obsługa monitorów o wysokiej rozdzielczości DPI.

**Obsługa wysokiej rozdzielczości DPI**

Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4,7, .NET Framework funkcje o wysokiej rozdzielczości DPI i dynamicznej rozdzielczości DPI dla aplikacji Windows Forms. Obsługa wysokiej rozdzielczości DPI usprawnia układ i wygląd formularzy i kontrolek na monitorach o wysokiej rozdzielczości DPI. Dynamiczne DPI zmienia układ i wygląd formularzy i kontrolek, gdy użytkownik zmienia wartość DPI lub współczynnik skali wyświetlania uruchomionej aplikacji.

Obsługa wysokiej rozdzielczości DPI to funkcja, która została skonfigurowana przez zdefiniowanie [ \<sekcji System. Windows. Forms. ConfigurationSection >](../configure-apps/file-schema/winforms/index.md) w pliku konfiguracyjnym aplikacji. Aby uzyskać więcej informacji na temat dodawania obsługi wysokiej rozdzielczości DPI i dynamicznej rozdzielczości DPI do aplikacji Windows Forms, zobacz [Obsługa wysokiej rozdzielczości DPI w Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

W .NET Framework 4,7, WPF obejmuje następujące udoskonalenia:

**Obsługa stosu dotykowego/pióra opartego na komunikatach WM_POINTER systemu Windows**

Masz teraz możliwość używania stosu dotykowego/pióra na podstawie [komunikatów WM_POINTER](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) zamiast platformy Windows Ink Services (roamingu). Jest to funkcja opcjonalna w .NET Framework. Aby uzyskać więcej informacji, zobacz [przekierowywanie zmian w .NET Framework 4,7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

**Nowa Implementacja interfejsów API drukowania WPF**

Interfejsy API drukowania WPF w <xref:System.Printing.PrintQueue?displayProperty=nameWithType> klasie wywołują [interfejs API pakietu dokumentów](/windows/desktop/printdocs/tailored-app-printing-api) systemu Windows zamiast przestarzałego [interfejsu API drukowania XPS](/windows/desktop/printdocs/xps-printing). Aby uzyskać wpływ tej zmiany na zgodność aplikacji, zobacz Przekierowanie [zmian w .NET Framework 4,7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a>Co nowego w .NET Framework 4.6.2

.NET Framework 4.6.2 zawiera nowe funkcje w następujących obszarach:

- [ASP.NET](#ASPNET462)

- [Kategorie znaków](#Strings)

- [Cryptography](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Konwertowanie aplikacji Windows Forms i WPF na aplikacje platformy UWP](#UWPConvert)

- [Ulepszenia debugowania](#Debug462)

Aby uzyskać listę nowych interfejsów API dodanych do .NET Framework 4.6.2, zobacz [.NET Framework zmiany interfejsu API 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) w serwisie GitHub. Aby zapoznać się z listą ulepszeń funkcji i poprawek błędów w .NET Framework 4.6.2, zobacz [.NET Framework 4.6.2 list zmian](https://go.microsoft.com/fwlink/?LinkId=708778) w witrynie GitHub.  Aby uzyskać dodatkowe informacje, zobacz temat [ogłaszanie .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) w blogu platformy .NET.

<a name="ASPNET462" />

### <a name="aspnet"></a>ASP.NET

W .NET Framework 4.6.2 ASP.NET obejmuje następujące udoskonalenia:

**Ulepszona obsługa zlokalizowanych komunikatów o błędach w modułach sprawdzania poprawności adnotacji danych**

Moduły sprawdzania poprawności adnotacji danych umożliwiają wykonanie walidacji przez dodanie jednego lub większej liczby atrybutów do właściwości klasy. <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> Element atrybutu definiuje tekst komunikatu o błędzie, jeśli Walidacja nie powiedzie się. Począwszy od .NET Framework 4.6.2, ASP.NET ułatwia lokalizowanie komunikatów o błędach. Komunikaty o błędach będą lokalizowane, jeśli:

1. <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> Podano w atrybucie walidacji.

2. Plik zasobów jest przechowywany w folderze App_LocalResources.

3. `DataAnnotation.Localization.{`Nazwa zlokalizowanego pliku zasobów ma *nazwę*`}.resx`formularza, gdzie *name* jest nazwą kultury w formacie *languageCode*`-`*Country/regionCode* lub *languageCode*.

4. Nazwa klucza zasobu jest ciągiem przypisanym do <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atrybutu, a jego wartość jest zlokalizowanym komunikatem o błędzie.

Na przykład następujący atrybut adnotacji danych definiuje domyślną wartość domyślnej kultury dla nieprawidłowej klasyfikacji.

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

Następnie można utworzyć plik zasobów, DataAnnotation. lokalizacja. fr. resx, którego kluczem jest ciąg komunikatu o błędzie i którego wartość jest zlokalizowanym komunikatem o błędzie. Plik musi znajdować się w `App.LocalResources` folderze. Na przykład poniżej znajduje się klucz i jego wartość w zlokalizowanym komunikacie o błędzie języka francuskiego (fr):

| Nazwa                                 | Wartość                                     |
| ------------------------------------ | ----------------------------------------- |
| Klasyfikacja musi zawierać się w przedziale od 1 do 10. | La uwagi doit être obejmuje Entre 1 et 10. |

 Ponadto lokalizacja adnotacji danych jest rozszerzalna. Deweloperzy mogą podłączyć własnego dostawcę lokalizatora ciągów, implementując <xref:System.Web.Globalization.IStringLocalizerProvider> interfejs do przechowywania ciągu lokalizacji w innym miejscu niż w pliku zasobów.

 **Obsługa asynchroniczna z dostawcami magazynu stanów sesji**

 ASP.NET teraz zezwala na używanie metod zwracających zadania z dostawcami magazynu stanów sesji, co umożliwia aplikacjom ASP.NET uzyskanie korzyści z skalowalności asynchronicznej. Aby obsługiwał operacje asynchroniczne z dostawcami magazynu stanów sesji, ASP.NET obejmuje nowy interfejs <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, który dziedziczy z <xref:System.Web.IHttpModule> i umożliwia deweloperom wdrażanie własnych modułów stanu sesji i dostawców magazynu sesji asynchronicznych. Interfejs jest zdefiniowany w następujący sposób:

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

 Ponadto <xref:System.Web.SessionState.SessionStateUtility> Klasa obejmuje dwie nowe metody <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> które mogą służyć do obsługi operacji asynchronicznych.

 **Obsługa asynchronicznych dostawców pamięci podręcznej**

 Począwszy od .NET Framework 4.6.2, metody zwracające zadania mogą być używane z dostawcami pamięci podręcznej danych wyjściowych w celu zapewnienia skalowalności w systemie.  Dostawcy implementujący te metody redukują blokowanie wątków na serwerze sieci Web i zwiększają skalowalność usługi ASP.NET.

 Dodano następujące interfejsy API obsługujące asynchroniczne dostawcy pamięci podręcznej danych wyjściowych:

- Klasa, która dziedziczy po <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> i umożliwia deweloperom wdrożenie asynchronicznego dostawcy pamięci podręcznej wyjściowej. <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType>

- <xref:System.Web.Caching.OutputCacheUtility> Klasa, która zapewnia metody pomocnika do konfigurowania wyjściowej pamięci podręcznej.

- 18 nowych metod w <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> klasie. Należą <xref:System.Web.HttpCachePolicy.GetCacheability%2A>do nich <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A> ,<xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, ,,<xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, ,<xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>,,, ,<xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetNoStore%2A> <xref:System.Web.HttpCachePolicy.GetRevalidation%2A> <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A> ,<xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>i .<xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>

- 2 nowe metody w <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> klasie: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> i <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.

- 2 nowe metody w <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> klasie: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> i <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.

- 2 nowe metody w <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> klasie: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> i <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.

- <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> W klasie<xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> Metoda.

- <xref:System.Web.Caching.CacheDependency> W<xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metodzie.

<a name="Strings" />

### <a name="character-categories"></a>Kategorie znaków

Znaki w .NET Framework 4.6.2 są klasyfikowane na podstawie standardu [Unicode w wersji 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). W .NET Framework 4,6 i .NET Framework 4.6.1, znaki zostały sklasyfikowane w oparciu o kategorie znaków Unicode 6,3.

Obsługa standardu Unicode 8,0 jest ograniczona do klasyfikacji znaków przez <xref:System.Globalization.CharUnicodeInfo> klasę oraz do typów i metod, które są od niego zależne. Obejmują <xref:System.Globalization.StringInfo> one klasę, przeciążoną <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> metodę i [klasy znaków](../../standard/base-types/character-classes-in-regular-expressions.md) rozpoznawane przez aparat wyrażeń regularnych .NET Framework.  Ta zmiana nie ma wpływ na porównanie znaków i ciągów, a także w systemach Windows 7 — w przypadku danych znakowych dostarczonych przez .NET Framework.

Zmiany w kategoriach znakowych z Unicode 6,0 na Unicode 7,0 można znaleźć [w standardzie Unicode w wersji 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) w witrynie internetowej konsorcjum Unicode Consortium. Aby uzyskać zmiany z Unicode 7,0 na Unicode 8,0, zobacz [standard Unicode w wersji 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) w witrynie sieci Web programu Unicode Consortium.

<a name="Crypto462" />

### <a name="cryptography"></a>Cryptography

**Obsługa certyfikatów x509 zawierających FIPS 186-3 DSA**

.NET Framework 4.6.2 dodaje obsługę dla certyfikatów x509 (algorytm podpisu cyfrowego), których klucze przekraczają limit FIPS 186-2 1024-bitowy.

Oprócz obsługi większych rozmiarów standardu FIPS 186-3 .NET Framework 4.6.2 umożliwia obliczanie sygnatur przy użyciu rodziny SHA-2 algorytmów wyznaczania wartości skrótu (SHA256, SHA384 i SHA512). Obsługa standardu FIPS 186-3 jest udostępniana <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> przez nową klasę.

W przypadku niedawnych zmian <xref:System.Security.Cryptography.RSA> w klasie w .NET Framework 4,6 <xref:System.Security.Cryptography.ECDsa> i klasie <xref:System.Security.Cryptography.DSA> w .NET Framework 4.6.1, abstrakcyjna klasa bazowa w .NET Framework 4.6.2 ma dodatkowe metody zezwalające obiektom wywołującym na korzystanie z tej funkcji bez rzutowania. Możesz wywołać <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> metodę rozszerzenia, aby podpisać dane, jak pokazano w poniższym przykładzie.

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

Można też wywołać <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> metodę rozszerzenia, aby zweryfikować podpisane dane, jak pokazano w poniższym przykładzie.

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

**Zwiększono przejrzystość danych wejściowych procedur wyprowadzania klucza ECDiffieHellman**

.NET Framework 3,5 dodano obsługę dla uzgadniania klucza diff-Hellmana z trzema różnymi procedurami funkcji wyprowadzania klucza (KDF). Dane wejściowe procedur i same procedury, zostały skonfigurowane za pośrednictwem właściwości <xref:System.Security.Cryptography.ECDiffieHellmanCng> obiektu. Jednak ponieważ nie każda procedura odczytuje każdą właściwość wejściową, istniało bardzo dużo miejsca do mylenia w przeszłości deweloperów.

Aby rozwiązać ten wpływ na .NET Framework 4.6.2, do klasy <xref:System.Security.Cryptography.ECDiffieHellman> bazowej dodano następujące trzy metody, aby dokładniej przedstawić te procedury KDF i ich dane wejściowe:

|ECDiffieHellman, Metoda|Opis|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Dziedziczy materiał klucza przy użyciu formuły<br /><br /> Hash (secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> HASH (secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> gdzie *x* jest obliczanym wynikiem algorytmu Diffie-Hellmana.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Dziedziczy materiał klucza przy użyciu formuły<br /><br /> HMAC (hmacKey, secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> HMAC (hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> gdzie *x* jest obliczanym wynikiem algorytmu Diffie-Hellmana.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Jest to kluczowy materiał przy użyciu algorytmu wyznaczania wartościowo-Random protokołu TLS (PRF).|

**Obsługa szyfrowania symetrycznego klucza**

Biblioteka kryptografii systemu Windows (CNG) dodaliśmy obsługę przechowywania utrwalonych kluczy symetrycznych i używania kluczy symetrycznych przechowywanych sprzętowo, a .NET Framework 4.6.2, że deweloperzy mogą korzystać z tej funkcji.  Ponieważ pojęcie nazw kluczy i dostawców kluczy jest specyficzne dla implementacji, użycie tej funkcji wymaga użycia konstruktora konkretnych typów implementacji zamiast preferowanego podejścia do fabryki (na przykład wywoływanie `Aes.Create`).

Obsługa szyfrowania symetrycznego klucza istnieje dla algorytmów AES (<xref:System.Security.Cryptography.AesCng>) i 3DES (<xref:System.Security.Cryptography.TripleDESCng>). Na przykład:

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

**SignedXml obsługa tworzenia skrótów SHA-2**

.NET Framework 4.6.2 dodaje do <xref:System.Security.Cryptography.Xml.SignedXml> klasy obsługę kluczy RSA-SHA256, RSA-SHA384, i RSA-SHA512 PKCS # 1 oraz SHA256, SHA384 i SHA512 algorytmy szyfrowania.

Wszystkie stałe identyfikatorów URI są uwidocznione <xref:System.Security.Cryptography.Xml.SignedXml>na:

|Pole SignedXml|Stała|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Wszystkie programy, w których zarejestrowano <xref:System.Security.Cryptography.SignatureDescription> <xref:System.Security.Cryptography.CryptoConfig> procedurę obsługi niestandardowej do dodawania obsługi tych algorytmów, będą nadal działać tak samo jak w przeszłości, ale ponieważ <xref:System.Security.Cryptography.CryptoConfig> teraz istnieją wartości domyślne platformy, rejestracja nie jest już dostępna wymaga.

<a name="SQLClient" />

### <a name="sqlclient"></a>SqlClient

.NET Framework dostawca danych dla SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) zawiera następujące nowe funkcje w .NET Framework 4.6.2:

**Buforowanie i limity czasu połączeń z bazami danych Azure SQL**

Po włączeniu puli połączeń i przekroczeniu limitu czasu lub innego błędu logowania, wyjątek jest buforowany i zostanie zgłoszony wyjątek buforowany dla każdej kolejnej próby połączenia przez następne 5 sekund do 1 minuty.  Aby uzyskać więcej informacji, zobacz SQL Servering pooling [(ADO.NET)](../data/adonet/sql-server-connection-pooling.md).

To zachowanie nie jest pożądane podczas łączenia się z bazami danych Azure SQL, ponieważ próby połączenia mogą zakończyć się niepowodzeniem z błędami przejściowymi, które są zwykle przywracane szybko. Aby lepiej zoptymalizować środowisko ponownej próby połączenia, zachowanie w okresie blokowania puli połączeń zostanie usunięte w przypadku niepowodzenia połączeń z bazami danych SQL Azure.

Dodanie nowego `PoolBlockingPeriod` słowa kluczowego umożliwia wybranie okresu blokowania najlepiej dopasowanego do Twojej aplikacji. Dostępne są następujące wartości:

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

Okres blokowania puli połączeń dla aplikacji, która łączy się z Azure SQL Database, jest wyłączony, a okres blokowania puli połączeń dla aplikacji łączącej się z jakimkolwiek innym wystąpieniem SQL Server jest włączony. Jest to wartość domyślna. Jeśli nazwa punktu końcowego serwera zostanie zakończona z dowolnego z poniższych, są one uznawane za bazy danych SQL Azure:

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

Okres blokowania puli połączeń jest zawsze włączony.

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

Okres blokowania puli połączeń jest zawsze wyłączony.

**Ulepszenia dla Always Encrypted**

Klient SQL wprowadza dwa ulepszenia dla Always Encrypted:

- Aby poprawić wydajność zapytań parametrycznych względem kolumn zaszyfrowanych baz danych, metadane szyfrowania dla parametrów zapytania są teraz buforowane. Właściwość ustawiona na `true` (która jest wartością domyślną), jeśli to samo zapytanie jest wywoływane wiele razy, Klient pobiera metadane parametrów z serwera tylko raz. <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType>

- Wpisy kluczy szyfrowania kolumn w pamięci podręcznej kluczy są teraz wykluczone po konfigurowalnym przedziale czasu <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> , ustawiane za pomocą właściwości.

<a name="WCF" />

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

W .NET Framework 4.6.2 Windows Communication Foundation została ulepszona w następujących obszarach:

**Obsługa zabezpieczeń transportu WCF dla certyfikatów przechowywanych przy użyciu CNG**

Zabezpieczenia transportu WCF obsługują certyfikaty przechowywane przy użyciu biblioteki kryptografii systemu Windows (CNG). W .NET Framework 4.6.2 ta obsługa jest ograniczona do używania certyfikatów z kluczem publicznym, który ma wykładnik nie więcej niż 32 bitów. Gdy aplikacja jest przeznaczona dla .NET Framework 4.6.2, ta funkcja jest domyślnie włączona.

W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.6.1 i starszych, ale są uruchomione na .NET Framework 4.6.2, tę funkcję można włączyć, dodając następujący wiersz do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku App. config lub Web. config.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

Można to również zrobić programowo przy użyciu kodu, takiego jak następujące:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

**Lepsza obsługa wielu reguł korekty czasu letniego przez klasę Klasa DataContractJsonSerializer**

Klienci mogą używać ustawienia konfiguracji aplikacji, aby określić, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> czy Klasa obsługuje wiele reguł korekty dla jednej strefy czasowej. Jest to funkcja opcjonalna. Aby ją włączyć, Dodaj następujące ustawienie do pliku App. config:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Gdy ta funkcja jest włączona, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiekt <xref:System.TimeZoneInfo> używa typu zamiast <xref:System.TimeZone> typu do deserializacji danych daty i godziny. <xref:System.TimeZoneInfo>Program obsługuje wiele reguł dostosowawczych, co umożliwia współpracę z danymi strefy czasowej historycznej.   <xref:System.TimeZone> nie.

Aby uzyskać więcej informacji na <xref:System.TimeZoneInfo> temat struktury i dostosowań strefy czasowej, zobacz [Omówienie strefy czasowej](../../standard/datetime/time-zone-overview.md).

**NetNamedPipeBinding najlepsze dopasowanie**

Funkcja WCF ma nowe ustawienie aplikacji, które można ustawić w aplikacjach klienckich, aby upewnić się, że zawsze łączą się z usługą nasłuchiwanie na identyfikatorze URI, który najlepiej pasuje do tego, który z nich żąda. Gdy to ustawienie aplikacji ma ustawioną `false` wartość (domyślnie), klienci korzystający <xref:System.ServiceModel.NetNamedPipeBinding> z programu w celu nawiązania połączenia z usługą nasłuchuje na identyfikatorze URI, który jest podciągiem żądanego identyfikatora URI.

Na przykład klient próbuje nawiązać połączenie z usługą nasłuchującą pod `net.pipe://localhost/Service1`adresem, ale inna usługa na tym komputerze z uprawnieniami administratora nasłuchuje pod `net.pipe://localhost`adresem. Gdy to ustawienie aplikacji ma ustawioną wartość `false`, klient podejmie próbę nawiązania połączenia z niewłaściwą usługą. Po ustawieniu ustawienia aplikacji na `true`, klient zawsze będzie łączył się z najlepszą zgodną usługą.

> [!NOTE]
> Klienci korzystający <xref:System.ServiceModel.NetNamedPipeBinding> z usługi Find Services w oparciu o adres podstawowy usługi (jeśli istnieje), a nie pełny adres punktu końcowego. Aby zapewnić, że to ustawienie zawsze działa, usługa powinna używać unikatowego adresu podstawowego.

Aby włączyć tę zmianę, Dodaj następujące ustawienie aplikacji do pliku App. config lub Web. config aplikacji klienckiej:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

**SSL 3,0 nie jest protokołem domyślnym**

W przypadku korzystania z NetTcp z zabezpieczeniami transportu i typem poświadczeń certyfikatu protokół SSL 3,0 nie jest już domyślnym protokołem używanym do negocjowania bezpiecznego połączenia. W większości przypadków nie ma to wpływu na istniejące aplikacje, ponieważ protokół TLS 1,0 jest uwzględniony na liście protokołów dla NetTcp. Wszyscy istniejący klienci powinni mieć możliwość negocjowania połączenia przy użyciu co najmniej protokołu TLS 1,0. Jeśli Ssl3 jest wymagany, użyj jednego z poniższych mechanizmów konfiguracji, aby dodać go do listy protokołów negocjowanych.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> Właściwość

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> Właściwość

- Sekcja [ Transport>wsekcji>NetTcpBinding\<](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) [ \<](../configure-apps/file-schema/wcf/nettcpbinding.md)

- [ Sekcja\<](../configure-apps/file-schema/wcf/custombinding.md) sslStreamSecurity > sekcji CustomBinding > [ \<](../configure-apps/file-schema/wcf/sslstreamsecurity.md)

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

W .NET Framework 4.6.2 Windows Presentation Foundation została ulepszona w następujących obszarach:

**Sortowanie grup**

Aplikacja, która używa <xref:System.Windows.Data.CollectionView> obiektu do grupowania danych, może teraz jawnie zadeklarować sposób sortowania grup. Jawne sortowanie dotyczy problemu nieintuicyjnej kolejności, która występuje, gdy aplikacja dynamicznie dodaje lub usuwa grupy, lub gdy zmienia wartość właściwości elementu w grupowaniu. Może również zwiększyć wydajność procesu tworzenia grupy przez przeniesienie porównań właściwości grupowania z sortowania pełnej kolekcji do sortowania grup.

Aby można było obsłużyć sortowanie <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> grup <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> , nowe i właściwości opisują sposób sortowania kolekcji grup utworzonych przez <xref:System.ComponentModel.GroupDescription> obiekt. Jest to analogiczne do sposobu sortowania elementów danych o <xref:System.Windows.Data.ListCollectionView> identycznych nazwach.

Dwie nowe statyczne właściwości <xref:System.Windows.Data.PropertyGroupDescription> <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> klasy i <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, mogą być używane w przypadku najczęstszych przypadków.

Na przykład poniższe dane grup XAML są uporządkowane według wieku, sortowania grupy wiekowe w kolejności rosnącej oraz grupowania elementów w każdej grupie wiekowej według nazwiska.

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

**Obsługa klawiatury miękkiej**

Obsługa klawiatury miękkiej umożliwia śledzenie fokusu w aplikacjach WPF przez automatyczne wywoływanie i odrzucanie nowej miękkiej klawiatury w systemie Windows 10, gdy dane wejściowe dotyku są odbierane przez kontrolkę, która może przyjmować tekst.

W poprzednich wersjach .NET Framework aplikacje WPF nie mogą należeć do śledzenia fokusu bez wyłączania obsługi gestu pióra WPF/dotknięcia.  W efekcie aplikacje WPF muszą wybierać między pełną obsługą technologii WPF touch lub korzystać z promocji myszy systemu Windows.

**DPI na monitor**

Aby obsłużyć najnowsze rozprzestrzenianie środowisk o wysokiej rozdzielczości DPI i hybrydowych DPI dla aplikacji WPF, WPF w .NET Framework 4.6.2 umożliwia świadomość poszczególnych monitorów. Zapoznaj się z [przykładami i przewodnikiem dewelopera](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) w witrynie GitHub, aby uzyskać więcej informacji na temat sposobu włączania aplikacji platformy WPF do monitorowania według rozdzielczości DPI.

We wcześniejszych wersjach .NET Framework aplikacje WPF są oparte na systemie DPI. Innymi słowy, interfejs użytkownika aplikacji jest skalowany w odpowiednim systemie operacyjnym, w zależności od wartości DPI monitora, na którym jest renderowana aplikacja. ,

W przypadku aplikacji uruchamianych w ramach .NET Framework 4.6.2 można wyłączyć zmiany dpi dla poszczególnych monitorów w aplikacjach WPF przez dodanie instrukcji konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracyjnym aplikacji w następujący sposób:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a>Program Windows Workflow Foundation (WF)

W .NET Framework 4.6.2 Windows Workflow Foundation został ulepszony w następującym obszarze:

**Obsługa C# wyrażeń i technologii IntelliSense w rehostowanym projektancie WF**

Począwszy od .NET Framework 4,5, WF obsługuje C# wyrażenia zarówno w projektancie programu Visual Studio, jak i w przepływach pracy w kodzie. Rehostowana Projektant przepływu pracy to kluczowa funkcja WF, która umożliwia Projektant przepływu pracy do aplikacji poza programem Visual Studio (na przykład w WPF).  Windows Workflow Foundation oferuje możliwość obsługi C# wyrażeń i technologii IntelliSense w przypadku ponownego hostowanej Projektant przepływu pracy. Aby uzyskać więcej informacji, zapoznaj się z [blogiem Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).

`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`W wersjach .NET Framework przed .NET Framework 4.6.2 Funkcja IntelliSense projektanta WF jest uszkodzona, gdy klient odbudowuje projekt przepływu pracy z programu Visual Studio. Gdy kompilacja projektu zakończy się pomyślnie, typy przepływu pracy nie są dostępne w projektancie, a w oknie **Lista błędów** są wyświetlane ostrzeżenia z funkcji IntelliSense dotyczące brakujących typów przepływów pracy. .NET Framework 4.6.2 rozwiązuje ten problem i udostępnia funkcję IntelliSense.

**Aplikacje w wersji 1 z funkcją śledzenia przepływu pracy na teraz działaniu w trybie FIPS**

Maszyny z włączonym trybem zgodności ze standardem FIPS mogą teraz pomyślnie uruchomić aplikację w stylu w wersji 1 z funkcją śledzenia przepływu pracy. Aby włączyć ten scenariusz, należy wprowadzić następujące zmiany w pliku App. config:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

Jeśli ten scenariusz nie jest włączony, uruchomienie aplikacji w dalszym ciągu generuje wyjątek z komunikatem "Ta implementacja nie jest częścią zgodnych algorytmów kryptograficznych FIPS platformy Windows."

**Udoskonalenia przepływu pracy podczas korzystania z aktualizacji dynamicznej w programie Visual Studio Projektant przepływu pracy**

Projektant działań Projektant przepływu pracy, schemat blokowy i inne działania związane z przepływem pracy pomyślnie załadowały i wyświetlą przepływy pracy <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> , które zostały zapisane po wywołaniu metody. W wersjach .NET Framework przed .NET Framework 4.6.2, ładowanie pliku XAML w programie Visual Studio dla przepływu pracy, który został zapisany po wywołaniu <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> , może spowodować następujące problemy:

- Projektant przepływu pracy nie może poprawnie załadować pliku XAML (gdy <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> znajduje się na końcu wiersza).

- Projektant działań Flowchart lub inny przepływ pracy może wyświetlać wszystkie obiekty w ich domyślnych lokalizacjach, w przeciwieństwie do wartości właściwości dołączony.

<a name="clickonce-1" />

### <a name="clickonce"></a>ClickOnce

Program ClickOnce został zaktualizowany do obsługi protokołów TLS 1,1 i TLS 1,2 oprócz protokołu 1,0, który jest już obsługiwany. Technologia ClickOnce automatycznie wykrywa wymagany protokół; Aby włączyć obsługę protokołu TLS 1,1 i 1,2, nie są wymagane żadne dodatkowe kroki w aplikacji ClickOnce.

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Konwertowanie aplikacji Windows Forms i WPF na aplikacje platformy UWP

System Windows oferuje teraz możliwości przenoszenia istniejących aplikacji klasycznych systemu Windows, w tym aplikacji WPF i Windows Forms, do platforma uniwersalna systemu Windows (platformy UWP). Ta technologia działa jako most, dzięki czemu można stopniowo migrować istniejącą bazę kodu do platformy UWP, dzięki czemu aplikacja jest przenoszona na wszystkie urządzenia z systemem Windows 10.

Skonwertowane aplikacje klasyczne uzyskują tożsamość aplikacji podobną do tożsamości aplikacji platformy UWP, dzięki czemu interfejsy API platformy UWP dostępne do włączania funkcji, takich jak kafelki dynamiczne i powiadomienia. Aplikacja będzie nadal działać tak jak wcześniej i działała jako aplikacja pełnego zaufania. Po przekonwertowaniu aplikacji proces kontenera aplikacji można dodać do istniejącego procesu pełnego zaufania, aby dodać do niego interfejs użytkownika adaptacyjnego. Po przeniesieniu wszystkich funkcji do procesu kontenera aplikacji można usunąć pełny proces zaufania i udostępnić nową aplikację platformy UWP wszystkim urządzeniom z systemem Windows 10.

<a name="Debug462" />

### <a name="debugging-improvements"></a>Ulepszenia debugowania

Niezarządzany *interfejs API debugowania* został ulepszony w .NET Framework 4.6.2 do wykonania dodatkowej analizy, <xref:System.NullReferenceException> gdy zostanie zgłoszony, aby można było określić, która zmienna w jednym wierszu kodu źródłowego to. `null`   Aby obsłużyć ten scenariusz, dodano następujące interfejsy API do niezarządzanego interfejsu API debugowania.

- Interfejsy [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)i [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) , które uwidaczniają natywne domy zmiennych zarządzanych. Dzięki temu debugery mogą wykonywać pewne analizy przepływu kodu, gdy <xref:System.NullReferenceException> wystąpi, i aby przejść do tyłu, aby określić zmienną zarządzaną, która odnosi się do lokalizacji `null`natywnej.

- Metoda [ICorDebugType2:: GetTypeId](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) zapewnia mapowanie dla ICorDebugType do [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), dzięki czemu debuger może uzyskać [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) bez wystąpienia ICorDebugType. Istniejące interfejsy API w [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) można następnie użyć do określenia układu klasy typu.

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a>Co nowego w .NET Framework 4.6.1

.NET Framework 4.6.1 zawiera nowe funkcje w następujących obszarach:

- [Cryptography](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profilowanie](#Profile461)

- [NGen](#NGEN461)

Więcej informacji o .NET Framework 4.6.1 można znaleźć w następujących tematach:

- [.NET Framework 4.6.1 listę zmian](https://go.microsoft.com/fwlink/?LinkId=622964)

- [Zgodność aplikacji w 4.6.1](../migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

- [Różnica interfejsu API .NET Framework](https://go.microsoft.com/fwlink/?LinkId=622989) (w serwisie GitHub)

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Cryptography Obsługa certyfikatów x509 zawierających ECDSA

.NET Framework 4,6 dodano obsługę RSACng dla certyfikatów x509. .NET Framework 4.6.1 dodaje obsługę dla certyfikatów x509 (algorytm podpisu cyfrowego krzywej eliptyczna) ECDSA.

ECDSA zapewnia lepszą wydajność i stanowi bardziej bezpieczny algorytm kryptograficzny niż RSA, zapewniając doskonałe rozwiązanie w zakresie wydajności i skalowalności Transport Layer Security (TLS). Implementacja .NET Framework zawija wywołania do istniejących funkcji systemu Windows.

Poniższy przykładowy kod pokazuje, jak łatwo jest wygenerować sygnaturę strumienia bajtów przy użyciu nowej obsługi certyfikatów x509 ECDSA zawartych w .NET Framework 4.6.1.

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

Oferuje to wyróżniony kontrast w kodzie wymaganym do wygenerowania podpisu w .NET Framework 4,6.

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a>ADO.NET

Do ADO.NET zostały dodane następujące elementy:

**Obsługa Always Encrypted kluczy chronionych sprzętem**

ADO.NET obsługuje teraz przechowywanie kluczy głównych kolumn Always Encrypted w sprzętowych modułach zabezpieczeń (sprzętowych modułów zabezpieczeń). Dzięki temu klientom można korzystać z kluczy asymetrycznych przechowywanych w sprzętowych modułów zabezpieczeń bez konieczności pisania dostawców magazynu kluczy niestandardowych i rejestrowania ich w aplikacjach.

Klienci muszą zainstalować dostawcę usług kryptograficznych dostarczonych przez dostawcę modułu HSM lub dostawców magazynu kluczy CNG na serwerach aplikacji lub komputerach klienckich w celu uzyskania dostępu do danych Always Encrypted chronionych przy użyciu kluczy głównych kolumn przechowywanych w module HSM.

**Ulepszone <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> zachowanie połączenia dla funkcji AlwaysOn**

Klient SqlClient teraz automatycznie zapewnia szybsze połączenia z grupą dostępności AlwaysOn (AG). W sposób niewidoczny dla użytkownika wykryje, czy aplikacja nawiązuje połączenie z grupą dostępności AlwaysOn (AG) w innej podsieci, i szybko odnajduje bieżący aktywny serwer i zapewnia połączenie z serwerem. Przed tą wersją aplikacja wymagała ustawienia parametrów połączenia do uwzględnienia `"MultisubnetFailover=true"` , aby wskazać, że nastąpiło połączenie z grupą dostępności AlwaysOn. Bez ustawienia słowa kluczowego połączenia `true`do, aplikacja może napotkać limit czasu podczas nawiązywania połączenia z grupą dostępności AlwaysOn. W tej wersji aplikacja nie musi już być ustawiona na `true` wartość <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> . Aby uzyskać więcej informacji na temat obsługi klienta z zawsze włączonymi grupami dostępności, zobacz temat [Obsługa klienta w przypadku wysokiej dostępności i odzyskiwania po awarii](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Windows Presentation Foundation obejmuje wiele udoskonaleń i zmian.

**Zwiększona wydajność**

Opóźnienie w przypadku uruchamiania zdarzeń Touch zostało rozwiązane w .NET Framework 4.6.1. Ponadto wpisywanie <xref:System.Windows.Controls.RichTextBox> kontrolki nie powoduje już powiązania wątku renderowania podczas szybkiego wprowadzania danych.

**Ulepszenia sprawdzania pisowni**

Moduł sprawdzania pisowni w programie WPF został zaktualizowany w Windows 8.1 i nowszych wersjach, aby można było korzystać z obsługi systemu operacyjnego w przypadku dodatkowych języków sprawdzania pisowni.  Nie wprowadzono zmian w wersjach systemu Windows starszych niż Windows 8.1.

Tak jak w poprzednich wersjach .NET Framework, język dla <xref:System.Windows.Controls.TextBox> bloku ora <xref:System.Windows.Controls.RichTextBox> kontroli jest wykrywany przez wyszukiwanie informacji w następującej kolejności:

- `xml:lang`, jeśli jest obecny.

- Bieżący język wejściowy.

- Bieżąca kultura wątku.

Aby uzyskać dodatkowe informacje na temat obsługi języków w programie WPF, zobacz [wpis w blogu WPF w witrynie .NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkID=691819).

**Dodatkowa obsługa słowników niestandardowych dla poszczególnych użytkowników**

W .NET Framework 4.6.1, WPF rozpoznaje niestandardowe słowniki, które są rejestrowane globalnie. Ta funkcja jest dostępna oprócz możliwości zarejestrowania ich na kontrolę.

We wcześniejszych wersjach programu WPF Słowniki niestandardowe nie rozpoznają wykluczonych słów i list Autokorekty. Są one obsługiwane w systemach Windows 8.1 i Windows 10 za pomocą plików, które można umieścić w `%AppData%\Microsoft\Spelling\<language tag>` katalogu.  Do tych plików mają zastosowanie następujące reguły:

- Pliki powinny mieć rozszerzenia. dic (dla dodanych wyrazów),. wyłączne (dla wykluczonych słów) lub ACL (na potrzeby funkcji Autokorekta).

- Pliki powinny zawierać tekst w formacie UTF-16, zaczynający się od znaku kolejności bajtów (BOM).

- Każdy wiersz powinien zawierać słowo (na dodanych i wykluczonych listach wyrazów) lub parę Autokorekta z wyrazami rozdzielonymi pionowym paskiem ("&#124;") (na liście Autokorekta wyrazów).

- Te pliki są uznawane za tylko do odczytu i nie są modyfikowane przez system.

> [!NOTE]
> Te nowe formaty plików nie są bezpośrednio obsługiwane przez interfejsy API sprawdzania pisowni WPF, a Słowniki niestandardowe dostarczane do WPF w aplikacjach powinny nadal używać plików. lex.

**Przykłady**

Istnieje kilka przykładów WPF w repozytorium GitHub [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) . Pomóż nam ulepszyć nasze przykłady, wysyłając do nas żądanie ściągnięcia lub otwierając [problem usługi GitHub](https://github.com/Microsoft/WPF-Samples/issues).

**Rozszerzenia DirectX**

WPF zawiera [pakiet NuGet](https://go.microsoft.com/fwlink/?LinkID=691342) , który udostępnia nowe implementacje <xref:System.Windows.Interop.D3DImage> programu, które ułatwiają współdziałanie z zawartością DX10 i DX11. Kod dla tego pakietu został otwarty jako źródło i jest dostępny [w serwisie GitHub](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: Transakcje

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> Metoda może teraz korzystać z programu Distributed Transaction Manager innego niż MSDTC, aby podwyższyć poziom transakcji. W tym celu należy określić identyfikator GUID transakcji dla nowego <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> przeciążenia. W przypadku pomyślnego wykonania tej operacji istnieją ograniczenia dotyczące możliwości transakcji. Po zapisaniu podwyższania poziomu usługi MSDTC następujące metody <xref:System.Transactions.TransactionPromotionException> zgłaszają, ponieważ te metody wymagają podwyższania poziomu do usługi MSDTC:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

Po zapisaniu podwyższania poziomu usługi MSDTC należy go używać na potrzeby przyszłych trwałych rejestracji przy użyciu protokołów, które definiuje. Promotor transakcji można uzyskać przy <xref:System.Transactions.Transaction.PromoterType%2A> użyciu właściwości. <xref:System.Guid> Gdy transakcja promuje, podwyższanie poziomu transakcji zapewnia <xref:System.Byte> tablicę, która reprezentuje podwyższony token. Aplikacja może uzyskać podwyższony token dla transakcji, która nie jest podwyższana dla <xref:System.Transactions.Transaction.GetPromotedToken%2A> usługi MSDTC, za pomocą metody.

Użytkownicy nowego <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> przeciążenia muszą wykonać określoną sekwencję wywołań, aby operacja podwyższania została zakończona pomyślnie. Te reguły są udokumentowane w dokumentacji metody.

<a name="Profile461" />

### <a name="profiling"></a>Profilowanie

Niezarządzany interfejs API profilowania został ulepszony w następujący sposób:

- Lepsza obsługa dostępu do plików PDB w interfejsie [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) .

  W ASP.NET Core staje się znacznie bardziej powszechny dla zestawów do skompilowania w pamięci przez Roslyn. W przypadku deweloperów tworzących narzędzia profilowania oznacza to, że nie można już wyplików PDB, że na dysku mogły być serializowane historyczne. Narzędzia profilera często używają plików PDB do mapowania kodu z powrotem do wierszy źródłowych dla zadań, takich jak pokrycie kodu lub analiza wydajności linia po wierszu. Interfejs [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) zawiera teraz dwie nowe metody, [ICorProfilerInfo7:: GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) i [ICorProfilerInfo7:: ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), aby udostępnić te narzędzia profilera z dostępem do danych PDB znajdujących się w pamięci. Korzystając z nowych interfejsów API, profiler może uzyskać zawartość PDB w pamięci jako tablicę bajtową, a następnie przetworzyć ją lub serializować do dysku.

- Lepsza Instrumentacja przy użyciu interfejsu ICorProfiler.

  Program profilowający korzystający z `ICorProfiler` funkcji API ReJIT dla Instrumentacji dynamicznej może teraz modyfikować niektóre metadane. Wcześniej takie narzędzia mogły w dowolnej chwili instrumentować IL, ale metadane można modyfikować tylko w czasie ładowania modułu. Ponieważ IL odwołuje się do metadanych, ogranicza to typy instrumentacji, które mogą zostać wykonane. Niektóre z tych limitów zostały zniesione przez dodanie metody [ICorProfilerInfo7:: ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) w celu obsługi podzbioru zmian metadanych po załadowaniu modułu, w szczególności przez dodanie `AssemblyRef`nowych, `TypeRef`, `TypeSpec` `MemberRef`,, `MemberSpec` i`UserString` rekordy. Ta zmiana zapewnia znacznie szerszy zakres Instrumentacji na bieżąco.

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a>Generator obrazu natywnego (NGEN) plików PDB

Śledzenie zdarzeń między maszynami umożliwia klientom profilowanie programu na maszynie A i przyjrzyj się zdarzeniom profilowania z mapowaniem wierszy źródłowych na komputerze B. korzystając z poprzednich wersji .NET Framework, użytkownik skopiuje wszystkie moduły i obrazy natywne z PROFILOWANEGO maszynę z maszyną analizy, która zawiera plik PDB języka IL, aby utworzyć mapowanie źródła do kodu natywnego. Chociaż ten proces może działać prawidłowo, gdy pliki są stosunkowo małe, na przykład w przypadku aplikacji na telefon, pliki mogą być bardzo duże w systemach komputerowych i wymagają znaczącego czasu na skopiowanie.

Za pomocą narzędzia NGen plików PDB można utworzyć plik PDB zawierający mapowanie IL-to-native bez zależności w pliku PDB IL. W naszym scenariuszu śledzenia zdarzeń między maszynami konieczne jest skopiowanie pliku PDB obrazu natywnego, który jest generowany przez maszynę A na komputerze B i użycie [interfejsów API dostępu do interfejsu debugowania](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) w celu odczytania mapowania Source-to-IL języka IL i kodu Il-to-native obrazu natywnego zmianę. Połączenie obu mapowań zapewnia mapowanie między źródłami. Ponieważ plik PDB obrazu natywnego jest znacznie mniejszy niż wszystkie moduły i obrazy natywne, proces kopiowania z maszyny A na maszynę B jest znacznie szybszy.

<a name="v46" />

## <a name="whats-new-in-net-2015"></a>Co nowego w programie .NET 2015

W programie .NET 2015 wprowadzono .NET Framework 4,6 i .NET Core. Niektóre nowe funkcje mają zastosowanie do obu i innych funkcji, które są specyficzne dla .NET Framework 4,6 lub .NET Core.

- **ASP.NET Core**

  Platforma .NET 2015 zawiera ASP.NET Core, która jest implementacją środowiska .NET Lean do kompilowania nowoczesnych aplikacji opartych na chmurze. ASP.NET Core jest modułowy, dzięki czemu można uwzględnić tylko te funkcje, które są potrzebne w aplikacji. Mogą być hostowane w usługach IIS lub samodzielny w procesie niestandardowym i można uruchamiać aplikacje z różnymi wersjami .NET Framework na tym samym serwerze. Obejmuje nowy system konfiguracji środowiska, który jest przeznaczony do wdrożenia w chmurze.

  MVC, Web API i Web Pages są ujednolicone w pojedynczą strukturę o nazwie MVC 6. Tworzysz ASP.NET Core aplikacje za poorednictwem narzędzi w programie Visual Studio 2015 lub nowszym. Twoje istniejące aplikacje będą działały na nowym .NET Framework; Jednak w przypadku kompilowania aplikacji używającej MVC 6 lub sygnalizującego 3 należy użyć systemu projektu w programie Visual Studio 2015 lub nowszym.

  Aby uzyskać więcej informacji, zobacz [ASP.NET Core](/aspnet/core/).

- **ASP.NET Updates**

  - **Interfejs API oparty na zadaniach dla opróżniania odpowiedzi asynchronicznej**

    ASP.NET teraz udostępnia prosty interfejs API oparty na zadaniach do opróżniania <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>odpowiedzi asynchronicznych, który umożliwia asynchroniczne opróżnianie odpowiedzi przy użyciu `async/await` obsługi języka.

  - **Powiązanie modelu obsługuje metody zwracające zadania**

    W .NET Framework 4,5 ASP.NET dodano funkcję powiązania modelu, która umożliwiła rozszerzalne podejście ukierunkowane na CRUD operacji na danych na stronach formularzy sieci Web i w kontrolkach użytkownika. System powiązań modelu obsługuje <xref:System.Threading.Tasks.Task>teraz zwracające metody powiązań modelu. Ta funkcja umożliwia deweloperom formularzy sieci Web uzyskanie korzyści z skalowalności asynchronicznej przy użyciu systemu powiązań danych w przypadku używania nowszych wersji programu ORMs, w tym Entity Framework.

    Powiązanie modelu asynchronicznego jest kontrolowane przez `aspnet:EnableAsyncModelBinding` ustawienie konfiguracji.

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    W przypadku aplikacji docelowych .NET Framework 4,6 jest to wartość domyślna `true`. W przypadku aplikacji uruchomionych na .NET Framework 4,6, które są przeznaczone dla starszej wersji .NET Framework, `false` jest to domyślnie. Można ją włączyć, ustawiając ustawienie konfiguracja na `true`.

  - **Obsługa protokołu HTTP/2 (system Windows 10)**

    [Http/2](https://www.wikipedia.org/wiki/HTTP/2) to nowa wersja protokołu HTTP, która zapewnia znacznie lepsze wykorzystanie połączenia (mniejszą liczbę operacji rundy między klientem a serwerem), co powoduje załadowanie strony sieci Web o mniejszej opóźnieniu dla użytkowników.  Strony sieci Web (w przeciwieństwie do usług) korzystają z protokołu HTTP/2, ponieważ protokół optymalizuje dla wielu artefaktów, które są żądane w ramach jednego środowiska. Obsługa protokołu HTTP/2 została dodana do ASP.NET w .NET Framework 4,6. Ponieważ funkcjonalność sieci istnieje w wielu warstwach, w systemie Windows w usługach IIS i w programie ASP.NET są wymagane nowe funkcje, które umożliwiają włączenie protokołu HTTP/2. Aby używać protokołu HTTP/2 z usługą ASP.NET, musi być uruchomiony system Windows 10.

    Protokół HTTP/2 jest również obsługiwany i domyślnie włączony w przypadku aplikacji z systemem Windows 10 platforma uniwersalna systemu Windows (platformy UWP) <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> , które używają interfejsu API.

    Aby zapewnić możliwość korzystania z funkcji [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) w aplikacjach ASP.NET, Nowa metoda z dwoma przeciążeń <xref:System.Web.HttpResponse.PushPromise%28System.String%29> i <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>została dodana do <xref:System.Web.HttpResponse> klasy.

    > [!NOTE]
    > Mimo że ASP.NET Core obsługuje protokół HTTP/2, obsługa funkcji WYPYCHANia PROMISe nie została jeszcze dodana.

    Przeglądarka i serwer sieci Web (usługi IIS w systemie Windows) wykonują wszystkie prace. Nie trzeba wykonywać żadnych dużych ponoszenia zawartości dla użytkowników.

    Większość [głównych przeglądarek obsługuje protokół HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), dlatego prawdopodobnie użytkownicy będą korzystać z obsługi protokołu HTTP/2, jeśli serwer ten obsługuje.

  - **Obsługa protokołu powiązania tokenu**

    Firma Microsoft i Google współpracują nad nowym podejściem do uwierzytelniania, nazywanym [protokołem powiązania tokenu](https://github.com/TokenBinding/Internet-Drafts). Założeniem jest to, że tokeny uwierzytelniania (w pamięci podręcznej przeglądarki) mogą być skradzione i używane przez przestępców w celu uzyskania dostępu do bezpiecznych zasobów (np. konta bankowego) bez konieczności podawania hasła lub wszelkich innych uprzywilejowanych informacji. Nowy protokół ma na celu ograniczenie tego problemu.

    Protokół powiązania tokenu zostanie wdrożony w systemie Windows 10 jako funkcja przeglądarki. Aplikacje ASP.NET będą uczestniczyć w protokole, dzięki czemu tokeny uwierzytelniania są weryfikowane jako wiarygodne. Klient i implementacje serwera określają kompleksową ochronę określoną przez protokół.

  - **Losowe algorytmy wyznaczania wartości ciągów**

    .NET Framework 4,5 wprowadził [losowy algorytm wyznaczania wartości skrótu](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Nie jest to jednak obsługiwane przez ASP.NET z powodu niektórych funkcji ASP.NET zależnych od stabilnego kodu skrótu. W .NET Framework 4,6 są teraz obsługiwane losowe algorytmy wyznaczania wartości ciągów. Aby włączyć tę funkcję, użyj `aspnet:UseRandomizedStringHashAlgorithm` ustawienia konfiguracji.

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- **ADO.NET**

  Obiekt ADO .NET obsługuje teraz funkcję Always Encrypted dostępną w SQL Server 2016 Community Technology Preview 2 (CTP2). Za pomocą Always Encrypted SQL Server mogą wykonywać operacje na zaszyfrowanych danych, a wszystkie klucze szyfrowania znajdują się w aplikacji wewnątrz zaufanego środowiska klienta, a nie na serwerze. Always Encrypted zabezpiecza dane klientów, dzięki czemu przetwarzający nie mają dostępu do danych w postaci zwykłego tekstu. Szyfrowanie i odszyfrowywanie danych odbywa się w sposób przezroczysty na poziomie sterownika, minimalizując zmiany, które należy wprowadzić w istniejących aplikacjach. Aby uzyskać szczegółowe informacje, zobacz [Always Encrypted (aparat bazy danych)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) i [Always Encrypted (Programowanie klienta)](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **64-bitowy kompilator JIT dla kodu zarządzanego**

  .NET Framework 4,6 zawiera nową wersję 64-bitowego kompilatora JIT (pierwotnie kod o nazwie RyuJIT). Nowy kompilator 64-bitowy zapewnia znaczące ulepszenia wydajności w porównaniu do starszego, 64-bitowego kompilatora JIT. Nowy kompilator 64-bitowy jest włączony dla procesów 64-bitowych uruchomionych w oparciu o .NET Framework 4,6. Aplikacja będzie działać w procesie 64-bitowym, jeśli zostanie skompilowana jako 64-bit lub AnyCPU i uruchomiona w 64-bitowym systemie operacyjnym. Należy zachować ostrożność, aby przechodzenie do nowego kompilatora było możliwie przejrzyste. zmiany w zachowaniu są możliwe. Chcemy bezpośrednio poznać wszelkie problemy, które wystąpiły podczas korzystania z nowego kompilatora JIT. Skontaktuj się z nami za pomocą [programu Microsoft Connect](https://connect.microsoft.com/) , jeśli wystąpi problem, który może być związany z nowym kompilatorem 64-bitowym JIT.

  Nowy kompilator 64-bitowy JIT zawiera również funkcje SIMD przyspieszania sprzętowego w połączeniu z typami z obsługą SIMD w <xref:System.Numerics> przestrzeni nazw, co może przynieść dobre ulepszenia wydajności.

- **Udoskonalenia modułu ładującego zestawy**

  Program ładujący zestawy zużywa teraz pamięć bardziej wydajnie, zwalniając zestawy IL po załadowaniu odpowiedniego obrazu NGEN. Ta zmiana zmniejsza ilość pamięci wirtualnej, co jest szczególnie przydatne w przypadku dużych aplikacji 32-bitowych (takich jak Visual Studio), a także umożliwia zapisanie pamięci fizycznej.

- **Zmiany w bibliotece klas podstawowych**

  Dodano wiele nowych interfejsów API do .NET Framework 4,6, aby umożliwić korzystanie z kluczowych scenariuszy. Należą do nich następujące zmiany i Dodatki:

  - **IReadOnlyCollection\<T > implementacje**

    W przypadku dodatkowych <xref:System.Collections.Generic.IReadOnlyCollection%601> kolekcji zaimplementowane <xref:System.Collections.Generic.Queue%601> są <xref:System.Collections.Generic.Stack%601>takie jak i.

  - **CultureInfo. CurrentCulture i CultureInfo. CurrentUICulture**

    Właściwości <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> są teraz do odczytu i zapisu, a nie tylko do odczytu. W przypadku przypisywania <xref:System.Globalization.CultureInfo> nowego obiektu do tych właściwości, bieżąca kultura wątku zdefiniowana `Thread.CurrentThread.CurrentCulture` przez właściwość i kulturę `Thread.CurrentThread.CurrentUICulture` wątku interfejsu użytkownika, która jest definiowana przez właściwości, również zmienia się.

  - **Udoskonalenia do wyrzucania elementów bezużytecznych (GC)**

    Klasa zawiera <xref:System.GC.TryStartNoGCRegion%2A> teraz i<xref:System.GC.EndNoGCRegion%2A> metody, które umożliwiają niezezwalanie na wyrzucanie elementów bezużytecznych podczas wykonywania ścieżki krytycznej. <xref:System.GC>

    Nowe Przeciążenie <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metody pozwala kontrolować, czy zarówno sterta małego obiektu, jak i sterta dużego obiektu są wycierane i kompaktowe.

  - **Typy z obsługą SIMD**

    <xref:System.Numerics.Quaternion> <xref:System.Numerics.Vector3> <xref:System.Numerics.Plane> <xref:System.Numerics.Vector2> <xref:System.Numerics.Matrix3x2> <xref:System.Numerics.Vector4>Przestrzeń nazw zawiera teraz wiele typów z obsługą SIMD, takich jak, <xref:System.Numerics.Matrix4x4>,,,, i. <xref:System.Numerics>

    Ponieważ nowy kompilator 64-bitowy JIT obejmuje również funkcje sprzętowego przyspieszania SIMD, istnieją szczególnie znaczące ulepszenia wydajności w przypadku używania typów z obsługą SIMD z nowym, 64-bitowym kompilatorem JIT.

  - **Aktualizacje kryptografii**

    Interfejs API jest aktualizowany do obsługi [interfejsów API kryptografii CNG systemu Windows.](/windows/desktop/SecCNG/cng-reference) <xref:System.Security.Cryptography?displayProperty=nameWithType> Poprzednie wersje .NET Framework były używane całkowicie we [wcześniejszej wersji interfejsów API kryptografii systemu Windows](/windows/desktop/SecCrypto/cryptography-portal) jako podstawy <xref:System.Security.Cryptography?displayProperty=nameWithType> implementacji. Mamy żądania obsługi interfejsu API CNG, ponieważ obsługuje on [nowoczesne algorytmy kryptografii](/windows/desktop/SecCNG/cng-features#suite-b-support), które są ważne w przypadku niektórych kategorii aplikacji.

    .NET Framework 4,6 zawiera następujące nowe ulepszenia do obsługi interfejsów API kryptografii CNG systemu Windows:

    - Zestaw metod rozszerzających certyfikaty x509 i `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, które zwracają implementację opartą na protokole CNG, a nie implementację w trybie CAPI, gdy jest to możliwe. (Niektóre karty inteligentne itp.) nadal wymagają użycia programu CAPI, a interfejsy API obsługują rezerwę.

    - <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> Klasa, która zapewnia implementację algorytmu RSA w implementacji CNG.

    - Udoskonalenia interfejsu API RSA, dzięki czemu typowe akcje nie wymagają już rzutowania. Na przykład szyfrowanie danych przy użyciu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> obiektu wymaga kodu, takiego jak następujące w poprzednich wersjach .NET Framework.

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      Kod korzystający z nowych interfejsów API kryptografii w .NET Framework 4,6 może zostać zapisany w następujący sposób, aby uniknąć rzutowania.

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - **Obsługa konwersji dat i godzin do lub z czasu systemu UNIX**

    Do <xref:System.DateTimeOffset> struktury dodano następujące nowe metody obsługi konwersji wartości daty i godziny do lub z czasu systemu UNIX:

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - **Przełączniki zgodności**

    Nowa <xref:System.AppContext> Klasa dodaje nową funkcję zgodności, która umożliwia autorom biblioteki zapewnienie jednolitego mechanizmu rezygnacji dla nowych funkcji dla użytkowników. Tworzy luźno rozłączoną umowę między składnikami w celu przekazywania żądania rezygnacji. Ta funkcja jest zwykle ważna w przypadku zmiany istniejącej funkcji. Z drugiej strony istnieje już niejawny wybór dla nowych funkcji.

    W <xref:System.AppContext>programie biblioteki definiują i uwidaczniają przełączniki zgodności, podczas gdy kod, który zależy od nich, mogą ustawiać te przełączniki na wpływ na zachowanie biblioteki. Domyślnie biblioteki udostępniają nowe funkcje i zmieniają je (to oznacza, że zapewniają poprzednie funkcje), jeśli przełącznik jest ustawiony.

    Aplikacja (lub biblioteka) może zadeklarować wartość przełącznika (zawsze <xref:System.Boolean> wartość), który definiuje Biblioteka zależna. Przełącznik jest zawsze niejawnie `false`. Ustawienie przełącznika w taki `true` sposób, aby włączyć go. Jawne ustawienie przełącznika `false` zapewnia nowe zachowanie.

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    Biblioteka musi sprawdzić, czy konsument zadeklaruje wartość przełącznika, a następnie odpowiednio wykonać odpowiednie działania.

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

    Korzystne jest użycie spójnego formatu dla przełączników, ponieważ są one formalnym kontraktem udostępnianym przez bibliotekę. Poniżej przedstawiono dwa oczywiste formaty.

    - *Przełącznik*. *przestrzeń nazw*. *przełącznikname*

    - *Przełącznik*. *Biblioteka*. *przełącznikname*

  - **Zmiany wzorca asynchronicznego opartego na zadaniach (TAP)**

    W przypadku aplikacji, które są przeznaczone dla <xref:System.Threading.Tasks.Task> .NET Framework <xref:System.Threading.Tasks.Task%601> 4,6, a obiekty dziedziczą kulturę i kultury interfejsu użytkownika wywołującego wątku. Nie dotyczy to zachowania aplikacji przeznaczonych dla poprzednich wersji .NET Framework lub nie przeznaczonych dla określonej wersji .NET Framework. Aby uzyskać więcej informacji, zapoznaj się z sekcją "kultury i operacje asynchroniczne oparte na <xref:System.Globalization.CultureInfo> zadaniach" w temacie dotyczącym klas.

    Klasa pozwala reprezentować dane otoczenia, które są lokalne dla danego przepływu kontroli asynchronicznej, takie `async` jak metoda. <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> Może służyć do utrwalania danych w wątkach. Można również zdefiniować metodę wywołania zwrotnego, która jest przekazywana za każdym razem, gdy dane <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> otoczenia ulegną zmianie, ponieważ właściwość została jawnie zmieniona lub wątek napotkał przejście kontekstu.

    Trzy wygodne metody, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, zostały dodane do wzorca asynchronicznego opartego na zadaniach (TAP) w celu zwrócenia ukończonych zadań w określonym stanie.

    Klasa obsługuje teraz asynchroniczną komunikację z nowym <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>. <xref:System.IO.Pipes.NamedPipeClientStream> Method.

  - **Zdarzenie EventSource obsługuje teraz zapisywanie w dzienniku zdarzeń**

    Teraz można użyć <xref:System.Diagnostics.Tracing.EventSource> klasy do rejestrowania administracyjnych lub komunikatów operacyjnych w dzienniku zdarzeń, oprócz wszelkich istniejących sesji ETW utworzonych na komputerze. W przeszłości należało użyć pakietu NuGet Microsoft. Diagnostics. Tracing. EventSource dla tej funkcji. Ta funkcja jest teraz wbudowana .NET Framework 4,6.

    Pakiet NuGet i .NET Framework 4,6 zostały zaktualizowane przy użyciu następujących funkcji:

    - **Zdarzenia dynamiczne**

      Umożliwia zdefiniowanie zdarzeń "na bieżąco" bez tworzenia metod zdarzeń.

    - **Rozbudowane ładunki**

      Umożliwia użycie specjalnie przypisanych klas i tablic, a także typów pierwotnych, które mają być przesyłane jako ładunek

    - **Śledzenie działań**

      Powoduje, że zdarzenia uruchamiania i zatrzymywania do tagów zdarzeń między nimi mają identyfikator reprezentujący wszystkie aktualnie aktywne aktywności.

    Do obsługi tych funkcji przeciążona <xref:System.Diagnostics.Tracing.EventSource.Write%2A> Metoda została dodana <xref:System.Diagnostics.Tracing.EventSource> do klasy.

- **Windows Presentation Foundation (WPF)**

  - **Udoskonalenia HDPI**

    Obsługa HDPI w programie WPF jest teraz lepsza w .NET Framework 4,6. Wprowadzono zmiany układu zaokrąglania, aby zmniejszyć liczbę wystąpień wycinków w kontrolkach z obramowaniem. Domyślnie ta funkcja jest włączona tylko wtedy, gdy <xref:System.Runtime.Versioning.TargetFrameworkAttribute> jest ustawiony na platformę .NET 4,6.  Aplikacje, które są przeznaczone dla wcześniejszych wersji platformy, ale działają w .NET Framework 4,6, mogą zrezygnować z nowego zachowania, dodając następujący wiersz do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku App. config:

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    Środowiska WPF systemu Windows na rozgałęzieniu wielu monitorów z różnymi ustawieniami DPI (Konfiguracja z wieloma DPI) są teraz całkowicie renderowane bez czarnego regionu. Możesz zrezygnować z tego zachowania, dodając następujący wiersz do `<appSettings>` sekcji pliku App. config, aby wyłączyć to nowe zachowanie:

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    Dodano obsługę automatycznego ładowania prawego kursora na podstawie ustawienia DPI <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.

  - **Lepsza obsługa dotyku**

    Raporty klienta dotyczące [połączenia](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) , które dotykają nieprzewidywalnego zachowania, zostały rozwiązane w .NET Framework 4,6. Próg podwójnego nacisku dla aplikacji ze sklepu Windows i aplikacji WPF jest teraz taki sam jak w Windows 8.1 i nowszych.

  - **Obsługa okna przezroczystego elementu podrzędnego**

    WPF w .NET Framework 4,6 obsługuje przezroczyste okna podrzędne w Windows 8.1 i nowszych. Dzięki temu można tworzyć nieprostokątne i przezroczyste okna podrzędne w oknach najwyższego poziomu. Tę funkcję można włączyć przez ustawienie <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> właściwości na. `true`

- **Windows Communication Foundation (WCF)**

  - **Obsługa protokołu SSL**

    Usługa WCF obsługuje teraz protokół SSL w wersji 1,1 i TLS 1,2, oprócz protokołu SSL 3,0 i TLS 1,0, podczas korzystania z usługi NetTcp z zabezpieczeniami transportu i uwierzytelnianiem klientów. Teraz można wybrać protokół, który ma być używany, lub aby wyłączyć stare, bezpieczne protokoły. Można to zrobić, ustawiając <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> właściwość lub dodając następujący element do pliku konfiguracji.

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

  - **Wysyłanie komunikatów przy użyciu różnych połączeń HTTP**

    Usługa WCF umożliwia teraz użytkownikom zapewnienie, że niektóre komunikaty są wysyłane przy użyciu różnych podstawowych połączeń HTTP. Istnieją dwa sposoby wykonania tej czynności:

    - **Używanie prefiksu nazwy grupy połączeń**

      Użytkownicy mogą określić ciąg, który będzie używany przez program WCF jako prefiks nazwy grupy połączeń. Dwa komunikaty z różnymi prefiksami są wysyłane przy użyciu różnych podstawowych połączeń HTTP. Prefiks ustawia się przez dodanie pary klucz/wartość do <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> właściwości komunikatu. Klucz ma wartość "HttpTransportConnectionGroupNamePrefix"; wartość jest pożądanym prefiksem.

    - **Korzystanie z różnych fabryk kanałów**

      Użytkownicy mogą również włączyć funkcję, która zapewnia, że komunikaty wysyłane przy użyciu kanałów utworzonych przez różne fabryki kanałów będą używać różnych podstawowych połączeń HTTP. Aby włączyć tę funkcję, użytkownicy muszą ustawić następujące elementy `appSetting`: `true`

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- **Windows Workflow Foundation (WWF)**

  Teraz możesz określić liczbę sekund, przez jaką usługa przepływu pracy będzie przekroczyć żądanie operacji poza kolejnością, gdy istnieje oczekująca zakładka "bez protokołu" przed upływem limitu czasu żądania. Zakładka "non-Protocol" jest zakładką, która nie jest powiązana z oczekującymi działaniami Receive. Niektóre działania tworzą zakładki nieobsługujące protokołów w ramach ich implementacji, dlatego może nie być oczywiste, że istnieje zakładka niebędąca protokołem. Obejmują one stan i wybór. Dlatego jeśli masz zaimplementowaną usługę przepływu pracy z maszyną stanu lub z działaniami pobrania, najprawdopodobniej zaistnieją zakładki niebędące protokołami. Interwał można określić, dodając wiersz podobny do `appSettings` sekcji pliku App. config:

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  Wartość domyślna to 60 sekund. Jeśli `value` wartość jest równa 0, żądania poza kolejnością są natychmiast odrzucane z powodu błędu z tekstem, który wygląda następująco:

  ```
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  Jest to ten sam komunikat, który jest wyświetlany po odebraniu komunikatu o operacji poza kolejnością i braku zakładek innych niż protokoły.

  Jeśli wartość `FilterResumeTimeoutInSeconds` elementu jest różna od zera, istnieją zakładki bez protokołu, a interwał limitu czasu wygaśnie, operacja kończy się niepowodzeniem z komunikatem o limicie czasu.

- **Transakcje**

  Teraz można uwzględnić identyfikator transakcji rozproszonej dla transakcji, która spowodowała zgłoszenie wyjątku pochodzącego od <xref:System.Transactions.TransactionException> . W tym celu należy dodać następujący klucz do `appSettings` sekcji pliku App. config:

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  Wartość domyślna to `false`.

- **Sieć**

  - **Ponowne użycie gniazda**

    System Windows 10 zawiera nowy algorytm sieci o wysokiej skalowalności, który umożliwia lepsze wykorzystanie zasobów komputera przez ponowne użycie portów lokalnych dla wychodzących połączeń TCP. .NET Framework 4,6 obsługuje nowy algorytm, umożliwiając aplikacjom .NET korzystanie z nowych zachowań. W poprzednich wersjach systemu Windows istnieje sztuczny limit połączeń współbieżnych (zazwyczaj 16 384, domyślny rozmiar dynamicznego zakresu portów), który może ograniczyć skalowalność usługi, powodując wyczerpanie portów podczas ładowania.

    W .NET Framework 4,6 dodano dwa nowe interfejsy API umożliwiające ponowne użycie portów, co skutecznie eliminuje limit 64 KB dla połączeń współbieżnych:

    - Wartość <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> wyliczenia.

    - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> Właściwość.

    Domyślnie <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> właściwość jest `false` określana `HWRPortReuseOnSocketBind` ,`HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` chyba że wartość klucza rejestru jest ustawiona na 0x1. Aby włączyć ponowne używanie portów lokalnych dla połączeń HTTP, należy <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> ustawić właściwość `true`na. Powoduje to, że wszystkie wychodzące <xref:System.Net.Http.HttpClient> połączenia <xref:System.Net.HttpWebRequest> gniazda TCP z i do korzystania z nowej opcji gniazda systemu Windows 10 [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), która umożliwia ponowne użycie portów lokalnych.

    Deweloperzy piszący aplikację tylko do gniazd mogą określić <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> opcję podczas wywoływania metody, takiej jak <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , aby gniazda wychodzące ponownie używały portów lokalnych podczas wiązania.

  - **Obsługa międzynarodowych nazw domen i formacie Punycode**

    Do <xref:System.Uri> klasy dodano nową <xref:System.Uri.IdnHost%2A>właściwość, która zapewnia lepszą obsługę międzynarodowych nazw domen i formacie Punycode.

- **Zmienianie rozmiarów w kontrolkach Windows Forms.**

  Ta funkcja <xref:System.Windows.Forms.DomainUpDown>została rozwinięta w .NET Framework 4,6, aby uwzględnić typy, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.ToolStripSplitButton> i prostokąt określony przez <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> Właściwość używaną podczas rysowania <xref:System.Drawing.Design.UITypeEditor>.

  Jest to funkcja opcjonalna. Aby je włączyć, ustaw `EnableWindowsFormsHighDpiAutoResizing` element na `true` w pliku konfiguracji aplikacji (App. config):

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Obsługa kodowania stron kodowych**

  Program .NET Core obsługuje przede wszystkim kodowania Unicode i domyślnie udostępnia ograniczoną obsługę kodowania stron kodowych. Można dodać obsługę kodowania stron kodowych dostępnych w .NET Framework ale nieobsługiwane w programie .NET Core przez zarejestrowanie kodowania stron kodowych za <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> pomocą metody. Aby uzyskać więcej informacji, zobacz <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

  Aplikacje systemu Windows dla systemu Windows 10, które są przeznaczone dla platformy C# .NET Core i są zapisywana lub Visual Basic mogą korzystać z nowej technologii, która kompiluje aplikacje do kodu natywnego, a nie Il. Generują aplikacje charakteryzujące się krótszym czasem uruchamiania i wykonywania. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji za pomocą .NET Native](../net-native/index.md). Aby zapoznać się z omówieniem .NET Native, który bada, w jaki sposób różni się od kompilacji JIT i NGEN oraz czego dotyczy Twój kod, zapoznaj się z tematem [.NET Native i kompilacją](../net-native/net-native-and-compilation.md).

  Aplikacje są domyślnie kompilowane do kodu natywnego podczas kompilowania ich przy użyciu programu Visual Studio 2015 lub nowszego. Aby uzyskać więcej informacji, zobacz [wprowadzenie z .NET Native](../net-native/getting-started-with-net-native.md).

  Aby można było obsługiwać debugowanie .NET Native aplikacje, do niezarządzanego interfejsu API debugowania dodano wiele nowych interfejsów i wyliczeń. Aby uzyskać więcej informacji, zobacz temat [debugowanie (niezarządzany wykaz interfejsów API)](../unmanaged-api/debugging/index.md) .

- **Pakiety .NET Framework Open Source**

  Pakiety .NET Core, takie jak Niezmienne kolekcje, [interfejsy API SIMD](https://go.microsoft.com/fwlink/?LinkID=518639)i interfejsy API sieci, takie jak te <xref:System.Net.Http> , które znajdują się w przestrzeni nazw, są teraz dostępne jako pakiety Open Source w witrynie [GitHub](https://github.com/). Aby uzyskać dostęp do kodu, zobacz [CoreFx w witrynie GitHub](https://github.com/dotnet/corefx). Aby uzyskać więcej informacji i dowiedzieć się, jak współtworzyć te pakiety, zobacz stronę główną platformy .NET [Core i Open Source](../get-started/net-core-and-open-source.md) [w witrynie GitHub](https://github.com/dotnet/home).

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a>Co nowego w .NET Framework 4.5.2

- **Nowe interfejsy API dla aplikacji ASP.NET.** Nowe <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> i<xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody umożliwiają sprawdzanie i modyfikowanie nagłówków odpowiedzi oraz kodu stanu, gdy odpowiedź jest opróżniana do aplikacji klienckiej. Rozważ użycie tych metod zamiast <xref:System.Web.HttpApplication.PreSendRequestHeaders> zdarzeń i <xref:System.Web.HttpApplication.PreSendRequestContent> ; są one bardziej wydajne i niezawodne.

  <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> Metoda umożliwia zaplanowanie niewielkich elementów roboczych w tle. ASP.NET śledzi te elementy i uniemożliwia nieoczekiwane zakończenie procesu roboczego przez usługi IIS do momentu zakończenia wszystkich elementów roboczych w tle. Tej metody nie można wywołać poza domenę aplikacji zarządzanej przez ASP.NET.

  Nowe <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> i<xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> właściwości zwracają wartości logiczne, które wskazują, czy nagłówki odpowiedzi zostały zapisaniu. Możesz użyć tych właściwości, aby upewnić się, że wywołania interfejsów API <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> , takie jak (które generują wyjątki, jeśli nagłówki zostały zapisaniu) powiedzie się.

- **Zmienianie rozmiarów w kontrolkach Windows Forms.** Ta funkcja została rozszerzona. Teraz można użyć ustawienia DPI systemu, aby zmienić rozmiar składników następujących dodatkowych kontrolek (na przykład strzałkę rozwijaną w polach kombi):

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  Jest to funkcja opcjonalna. Aby je włączyć, ustaw `EnableWindowsFormsHighDpiAutoResizing` element na `true` w pliku konfiguracji aplikacji (App. config):

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Nowa funkcja przepływu pracy.** Menedżer zasobów korzystający z <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metody (i w związku z tym <xref:System.Transactions.IPromotableSinglePhaseNotification> implementującej interfejs) może użyć nowej <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> metody do żądania następujących czynności:

  - Podnieś poziom transakcji do transakcji usługi Microsoft Distributed Transaction Coordinator (MSDTC).

  - Zamień <xref:System.Transactions.IPromotableSinglePhaseNotification> na element <xref:System.Transactions.ISinglePhaseNotification>, który jest trwałą rejestracją, która obsługuje zatwierdzenia pojedynczej fazy.

  Można to zrobić w ramach tej samej domeny aplikacji i nie jest wymagany żaden dodatkowy kod niezarządzany do współpracy z usługą MSDTC w celu przeprowadzenia promocji. Nową metodę można wywołać tylko wtedy, <xref:System.Transactions?displayProperty=nameWithType> <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` gdy istnieje zaległe wywołanie z metody, która jest implementowana przez rejestrację promocji.

- **Udoskonalenia profilowania.** Następujące nowe niezarządzane interfejsy API profilowania zapewniają bardziej niezawodne profilowanie:

  - [COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [Wyliczenie COR_PRF_HIGH_MONITOR](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [GetAssemblyReferences, metoda](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [GetEventMask2, metoda](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [SetEventMask2, metoda](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [AddAssemblyReference, metoda](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  Poprzednie `ICorProfiler` implementacje obsługują ładowanie zestawów zależnych z opóźnieniem. Nowe interfejsy API profilowania wymagają zestawów zależnych, które są wstrzykiwane przez profiler, aby można je było załadować natychmiast, zamiast ładować po całkowitym zainicjowaniu aplikacji. Ta zmiana nie ma wpływu na użytkowników istniejących `ICorProfiler` interfejsów API.

- **Ulepszenia debugowania.** Poniższe nowe niezarządzane interfejsy API debugowania zapewniają lepszą integrację z profilerem. Teraz możesz uzyskiwać dostęp do metadanych wstawianych przez profiler, a także zmiennych lokalnych i kodu wytworzonych przez ReJIT kompilatora w przypadku debugowania zrzutów.

  - [SetWriteableMetadataUpdateMode, metoda](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [EnumerateLocalVariablesEx, metoda](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [GetLocalVariableEx, metoda](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [GetCodeEx, metoda](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [GetActiveReJitRequestILCode, metoda](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [GetInstrumentedILMap, metoda](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Zmiany śledzenia zdarzeń.** .NET Framework 4.5.2 pozwala na pozaprocesowe śledzenie aktywności na podstawie śledzenia zdarzeń systemu Windows (ETW) dla większego obszaru powierzchni. Dzięki temu dostawcy zaawansowanego zarządzania energią (APM) mogą zapewnić uproszczone narzędzia, które dokładnie śledzą koszty poszczególnych żądań i działań obejmujących wiele wątków.  Te zdarzenia są wywoływane tylko wtedy, gdy są włączone przez kontrolery ETW; w związku z tym zmiany nie mają wpływu na wcześniej zapisany kod ETW lub kod, który jest uruchamiany z funkcją ETW wyłączona.

- **Podwyższanie poziomu transakcji i konwertowanie jej na trwałe rejestracje**

  <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>jest nowym interfejsem API dodanym do .NET Framework 4.5.2 i 4,6:

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

  Metoda może być używana przez rejestrację, która została wcześniej utworzona przez <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> w odpowiedzi <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> na metodę. Prosi `System.Transactions` o podwyższenie poziomu transakcji do transakcji MSDTC i "Konwertuj" rejestrację promocji na trwałą rejestrację. Po pomyślnym <xref:System.Transactions.IPromotableSinglePhaseNotification> zakończeniu tej metody interfejs nie będzie już przywoływany `System.Transactions`przez program, a wszystkie przyszłe powiadomienia będą docierać do podanego <xref:System.Transactions.ISinglePhaseNotification> interfejsu. Dana Rejestracja musi pełnić rolę trwałej rejestracji, obsługującej rejestrowanie i odzyskiwanie transakcji. Aby uzyskać <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> szczegółowe informacje, zobacz. Ponadto Rejestracja musi obsługiwać <xref:System.Transactions.ISinglePhaseNotification>.  Tę metodę można wywołać *tylko* podczas przetwarzania <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> wywołania. Jeśli tak nie jest, <xref:System.Transactions.TransactionException> zgłaszany jest wyjątek.

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a>Co nowego w .NET Framework 4.5.1

**Aktualizacje 2014 kwietnia**:

- [Aktualizacja Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) obejmuje aktualizacje szablonów bibliotek klas przenośnych do obsługi następujących scenariuszy:

  - W bibliotekach przenośnych można używać środowisko wykonawcze systemu Windows interfejsów API przeznaczonych dla Windows 8.1, Windows Phone 8,1 i Windows Phone Silverlight 8,1.

  - W przenośnych bibliotekach można uwzględnić kod XAML (typy Windows. UI. XAML), gdy jest przeznaczony Windows 8.1 lub Windows Phone 8,1. Obsługiwane są następujące szablony XAML:  Pusta strona, słownik zasobów, kontrolka z szablonem i kontrolka użytkownika.

  - Można utworzyć przenośny składnik środowisko wykonawcze systemu Windows (plik. winmd) do użycia w aplikacjach ze sklepu przeznaczonym dla Windows 8.1 i Windows Phone 8,1.

  - Można przekierować magazyn Windows lub Windows Phone bibliotekę klas magazynu, jak Biblioteka klas przenośnych.

  Aby uzyskać więcej informacji o tych zmianach, zobacz [Przenośna biblioteka klas](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Zestaw zawartości .NET Framework zawiera teraz dokumentację .NET Native, która jest technologią prekompilacji do kompilowania i wdrażania aplikacji systemu Windows. .NET Native kompiluje aplikacje bezpośrednio do kodu natywnego, a nie do języka pośredniego (IL), aby uzyskać lepszą wydajność. Aby uzyskać szczegółowe informacje, zobacz [Kompilowanie aplikacji za pomocą .NET Native](../net-native/index.md).

- [Źródło referencyjne .NET Framework](https://referencesource.microsoft.com/) udostępnia nowe środowisko przeglądania i udoskonalone funkcje. Możesz teraz przeglądać kod źródłowy .NET Framework online, [pobrać odwołanie](https://referencesource.microsoft.com/download.html) do wyświetlania w trybie offline i przejść przez źródła (w tym poprawki i aktualizacje) podczas debugowania. Aby uzyskać więcej informacji, zobacz wpis w blogu [nowe wyszukiwanie źródła odwołania dla platformy .NET](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).

Nowe funkcje i ulepszenia w klasach bazowych w .NET Framework 4.5.1 obejmują:

- Automatyczne przekierowywanie powiązań dla zestawów. Począwszy od Visual Studio 2013, podczas kompilowania aplikacji przeznaczonej dla .NET Framework 4.5.1 można dodać przekierowania powiązań do pliku konfiguracyjnego aplikacji, jeśli aplikacja lub jej składniki odwołują się do wielu wersji tego samego zestawu. Tę funkcję można również włączyć dla projektów przeznaczonych dla starszych wersji .NET Framework. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznego przekierowywania](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)powiązań.

- Możliwość zbierania informacji diagnostycznych, aby pomóc deweloperom w ulepszaniu wydajności serwerów i aplikacji w chmurze. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> metody <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> i w <xref:System.Diagnostics.Tracing.EventSource> klasie.

- Możliwość jawnego kompaktowania sterty dużego obiektu (LOH) podczas wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwość.

- Dodatkowe ulepszenia wydajności, takie jak zawieszenie aplikacji ASP.NET, wielordzeniowe udoskonalenia JIT i szybsze uruchamianie aplikacji po aktualizacji .NET Framework. Aby uzyskać szczegółowe informacje, zapoznaj się z wpisem w blogu [.NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) i zawieszania [aplikacji ASP.NET](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) .

Ulepszenia Windows Forms obejmują:

- Zmienianie rozmiarów w kontrolkach Windows Forms. Ustawienia DPI systemu można użyć do zmiany rozmiaru składników formantów (na przykład ikon, które pojawiają się w siatce właściwości) przez zajęcie wpisu w pliku konfiguracyjnym aplikacji (App. config) aplikacji. Ta funkcja jest obecnie obsługiwana w następujących formantach Windows Forms:

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - Niektóre aspekty <xref:System.Windows.Forms.DataGridView> (zobacz [nowe funkcje w 4.5.2 w](#v452) przypadku dodatkowych formantów)

  Aby włączyć tę funkcję, Dodaj nowy \<plik AppSettings > do pliku konfiguracji (App. config) i `EnableWindowsFormsHighDpiAutoResizing` Ustaw element na `true`:

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

Ulepszenia podczas debugowania aplikacji .NET Framework w Visual Studio 2013 obejmują:

- Zwraca wartości w debugerze programu Visual Studio. Gdy debugujesz zarządzaną aplikację w Visual Studio 2013, w oknie samochody są wyświetlane typy zwracane i wartości dla metod. Te informacje są dostępne dla aplikacji klasycznych, sklepu Windows i Windows Phone. Aby uzyskać więcej informacji, zobacz [badanie wartości zwracanych wywołań metod](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).

- Edytuj i Kontynuuj dla aplikacji 64-bitowych. Visual Studio 2013 obsługuje funkcję Edytuj i Kontynuuj dla 64-bitowych aplikacji zarządzanych dla komputerów stacjonarnych, sklepu Windows i Windows Phone. Istniejące ograniczenia nadal obowiązują dla aplikacji 32-bitowych i 64-bitowych (zobacz ostatnią sekcję [obsługiwane zmiany koduC#()](/visualstudio/debugger/supported-code-changes-csharp) artykułu).

- Debugowanie z obsługą asynchroniczną. Aby ułatwić debugowanie asynchronicznych aplikacji w Visual Studio 2013, stos wywołań ukrywa kod infrastruktury dostarczony przez kompilatory do obsługi asynchronicznego programowania, a także łańcuchuje w logicznych klatkach nadrzędnych, dzięki czemu można wykonać więcej czynności po wykonaniu programu logicznego zrozumiał. Okno zadań zastępuje okno zadania równoległe i wyświetla zadania, które odnoszą się do określonego punktu przerwania, a także wyświetla wszystkie inne zadania, które są aktualnie aktywne lub zaplanowane w aplikacji. Informacje o tej funkcji można znaleźć w sekcji "debugowanie z obsługą asynchroniczną" [anonsu .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

- Lepsza obsługa wyjątków dla składników środowisko wykonawcze systemu Windows. W [!INCLUDE[win81](../../../includes/win81-md.md)]programie wyjątki, które powstają w aplikacjach ze sklepu Windows, zachowują informacje o błędzie, który spowodował wyjątek, nawet między granicami języka. Informacje o tej funkcji można znaleźć w sekcji "Programowanie aplikacji ze sklepu Windows" w [ogłoszeniu .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

Począwszy od Visual Studio 2013, można użyć narzędzia do [optymalizacji zarządzanej przez profil zarządzany (Mpgo. exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) w celu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] zoptymalizowania aplikacji oraz aplikacji klasycznych.

Nowe funkcje w programie ASP.NET 4.5.1 można znaleźć w temacie [ASP.NET and Web Tools for Visual Studio 2013 informacji o wersji](/aspnet/visual-studio/overview/2013/release-notes).

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a>Co nowego w .NET Framework 4,5

### <a name="base-classes"></a>Klas podstawowych

- Możliwość zmniejszenia liczby ponownych uruchomień systemu przez wykrywanie i zamykanie aplikacji .NET Framework 4 podczas wdrażania. Zobacz [zmniejszanie liczby ponownych uruchomień systemu podczas instalacji .NET Framework 4,5](../deployment/reducing-system-restarts.md).

- Obsługa tablic o rozmiarze większym niż 2 gigabajty (GB) na platformach 64-bitowych. Tę funkcję można włączyć w pliku konfiguracji aplikacji. Zobacz element gcAllowVeryLargeObjects >, który również zawiera inne ograniczenia dotyczące rozmiaru obiektu i rozmiaru tablicy. [ \<](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)

- Lepsza wydajność dzięki wyrzucaniu elementów bezużytecznych w tle dla serwerów. W przypadku używania wyrzucania elementów bezużytecznych serwera w .NET Framework 4,5, wyrzucanie elementów bezużytecznych w tle jest automatycznie włączone. Zobacz sekcję odzyskiwanie pamięci w tle w temacie Podstawowe informacje dotyczące wyrzucania [elementów](../../standard/garbage-collection/fundamentals.md) bezużytecznych.

- Kompilacja just-in-Time (JIT) w tle, która jest opcjonalnie dostępna na wielordzeniowych procesorach, aby zwiększyć wydajność aplikacji. Zobacz <xref:System.Runtime.ProfileOptimization>.

- Możliwość ograniczenia czasu, przez który aparat wyrażeń regularnych podejmie próbę rozpoznania wyrażenia regularnego przed przekroczeniem limitu czasu. <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> Zobacz właściwość.

- Możliwość zdefiniowania domyślnej kultury dla domeny aplikacji. Zapoznaj <xref:System.Globalization.CultureInfo> się z klasą.

- Obsługa kodowania Unicode (UTF-16) w konsoli. Zapoznaj <xref:System.Console> się z klasą.

- Obsługa wersji uporządkowania ciągów i danych porównawczych. Zapoznaj <xref:System.Globalization.SortVersion> się z klasą.

- Lepsza wydajność podczas pobierania zasobów. Zobacz [pakowanie i wdrażanie zasobów](../resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Udoskonalenia kompresji ZIP w celu zmniejszenia rozmiaru skompresowanego pliku. <xref:System.IO.Compression?displayProperty=nameWithType> Zobacz obszar nazw.

- Możliwość dostosowania kontekstu odbicia w celu przesłania domyślnego zachowania odbicia za <xref:System.Reflection.Context.CustomReflectionContext> pomocą klasy.

- Obsługa wersji 2008 międzynarodowych nazw domen w programie Applications (IDNA) standard, gdy <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> Klasa jest używana w systemie. [!INCLUDE[win8](../../../includes/win8-md.md)]

- Delegowanie porównania ciągów do systemu operacyjnego, który implementuje Unicode 6,0, gdy .NET Framework jest używany w systemie [!INCLUDE[win8](../../../includes/win8-md.md)]. W przypadku uruchamiania na innych platformach .NET Framework obejmuje własne dane porównania ciągów, które implementują standard Unicode 5. x. Zapoznaj <xref:System.String> się z klasą i sekcjami <xref:System.Globalization.SortVersion> uwagi klasy.

- Możliwość obliczania kodów skrótów dla ciągów na podstawie poszczególnych domen aplikacji. [ Zobacz\<UseRandomizedStringHashAlgorithm > elementu](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Obsługa odbicia typu jest <xref:System.Type> dzielona <xref:System.Reflection.TypeInfo> między klasy i. Zobacz [odbicie w .NET Framework dla aplikacji ze sklepu Windows](../reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

W .NET Framework 4,5 Managed Extensibility Framework (MEF) udostępnia następujące nowe funkcje:

- Obsługa typów ogólnych.

- Model programowania oparty na Konwencji, który umożliwia tworzenie części na podstawie konwencji nazewnictwa, a nie atrybutów.

- Wiele zakresów.

- Podzbiór MEF, którego można używać podczas tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Ten podzestaw jest dostępny jako [pakiet do pobrania](https://go.microsoft.com/fwlink/?LinkId=256238) z galerii NuGet. Aby zainstalować pakiet, Otwórz projekt w programie Visual Studio, wybierz polecenie **Zarządzaj pakietami NuGet** z menu **projekt** i Wyszukaj w `Microsoft.Composition` trybie online pakiet.

Aby uzyskać więcej informacji, zobacz [Managed Extensibility Framework (MEF)](../mef/index.md).

### <a name="asynchronous-file-operations"></a>Asynchroniczne operacje na plikach

W .NET Framework 4,5 nowe funkcje asynchroniczne zostały dodane do języków C# i Visual Basic. Te funkcje dodają model oparty na zadaniach służący do wykonywania operacji asynchronicznych. Aby użyć tego nowego modelu, należy użyć metod asynchronicznych w klasach we/wy. Zobacz [asynchroniczne operacje we/wy pliku](../../standard/io/asynchronous-file-i-o.md).

<a name="tools" />

### <a name="tools"></a>Narzędzia

W .NET Framework 4,5, Generator plików zasobów (Resgen. exe) umożliwia utworzenie pliku. resw do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacjach z pliku. resources osadzonego w .NET Framework zestawie. Aby uzyskać więcej informacji, zobacz [Resgen. exe (Generator plików zasobów)](../tools/resgen-exe-resource-file-generator.md).

Optymalizacja z przewodnikiem zarządzanym profilem (Mpgo. exe) umożliwia skrócenie czasu uruchamiania aplikacji, wykorzystanie pamięci (rozmiar zestawu roboczego) i przepływność przez optymalizację zestawów obrazów natywnych. Narzędzie wiersza polecenia generuje dane profilowe dla zestawów aplikacji obrazu natywnego. Zobacz [Mpgo. exe (Narzędzie optymalizacji zarządzanego profilu)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Począwszy od Visual Studio 2013, można użyć programu Mpgo. exe do optymalizowania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji oraz aplikacji klasycznych.

<a name="parallel" />

### <a name="parallel-computing"></a>Przetwarzanie równoległe

.NET Framework 4,5 zawiera kilka nowych funkcji i ulepszeń obliczeń równoległych. Obejmują one ulepszoną wydajność, zwiększoną kontrolę, ulepszoną obsługę programowania asynchronicznego, nową bibliotekę przepływu danych oraz ulepszoną obsługę debugowania równoległego i wydajności. Zapoznaj się z wpisem nowości [w programie .net 4,5](https://go.microsoft.com/fwlink/?LinkId=235061) na blogu programowanie równoległe przy użyciu platformy .NET.

<a name="web" />

### <a name="web"></a>sieć Web

ASP.NET 4,5 i 4.5.1 Dodawanie powiązania modelu dla formularzy sieci Web, obsługi protokołu WebSocket, obsługi asynchronicznych, ulepszeń wydajności i wielu innych funkcji. Aby uzyskać więcej informacji, zobacz następujące zasoby:

- [ASP.NET 4,5 i Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [Platforma ASP.NET i narzędzia Web Tools dla programu Visual Studio 2013 — informacje o wersji](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking-a-namenetworking-"></a>Sieci<a name="networking" />

.NET Framework 4,5 udostępnia nowy interfejs programowania dla aplikacji HTTP. Aby uzyskać więcej informacji, zobacz nowe <xref:System.Net.Http?displayProperty=nameWithType> i <xref:System.Net.Http.Headers?displayProperty=nameWithType> przestrzenie nazw.

Pomoc techniczna jest również dostępna dla nowego interfejsu programowania do akceptowania i korzystania z połączenia WebSocket przy użyciu istniejących <xref:System.Net.HttpListener> i powiązanych klas. Aby uzyskać więcej informacji, zobacz nową <xref:System.Net.WebSockets> przestrzeń nazw <xref:System.Net.HttpListener> i klasy.

Ponadto .NET Framework 4,5 obejmuje następujące udoskonalenia sieci:

- Obsługa identyfikatorów URI zgodnych ze standardem RFC. Aby uzyskać więcej informacji, <xref:System.Uri> Zobacz i powiązane klasy.

- Obsługa analizy międzynarodowej nazwy domeny (IDN). Aby uzyskać więcej informacji, <xref:System.Uri> Zobacz i powiązane klasy.

- Obsługa funkcji wielojęzycznych dla adresów E-mail (EAI). Aby uzyskać więcej informacji, zobacz <xref:System.Net.Mail> przestrzeń nazw.

- Ulepszona obsługa protokołu IPv6. Aby uzyskać więcej informacji, zobacz <xref:System.Net.NetworkInformation> przestrzeń nazw.

- Obsługa gniazd Dual-Mode. Aby uzyskać więcej informacji, zobacz <xref:System.Net.Sockets.Socket> klasy <xref:System.Net.Sockets.TcpListener> i.

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

W .NET Framework 4,5 Windows Presentation Foundation (WPF) zawiera zmiany i usprawnienia w następujących obszarach:

- Nowa <xref:System.Windows.Controls.Ribbon.Ribbon> kontrolka, która umożliwia implementację interfejsu użytkownika wstążki, który obsługuje pasek narzędzi Szybki dostęp, menu aplikacji i karty.

- Nowy <xref:System.ComponentModel.INotifyDataErrorInfo> interfejs obsługujący synchroniczną i asynchroniczną weryfikację danych.

- Nowe funkcje dla <xref:System.Windows.Controls.VirtualizingPanel> klas i <xref:System.Windows.Threading.Dispatcher> .

- Zwiększona wydajność podczas wyświetlania dużych zestawów pogrupowanych danych i uzyskiwania dostępu do kolekcji w wątkach innych niż interfejs użytkownika.

- Powiązanie danych z właściwościami statycznymi, powiązanie danych z typami niestandardowymi, które implementują <xref:System.Reflection.ICustomTypeProvider> interfejs i pobierają informacje o powiązaniu danych z wyrażenia powiązania.

- Zmiana położenia danych jako zmiany wartości (kształtowanie na żywo).

- Możliwość sprawdzenia, czy kontekst danych kontenera elementów jest odłączony.

- Możliwość ustawienia czasu, który powinien upłynąć między zmianami właściwości i aktualizacjami źródła danych.

- Ulepszona obsługa implementowania słabych wzorców zdarzeń. Ponadto zdarzenia mogą teraz akceptować rozszerzenia znaczników.

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

W .NET Framework 4,5 dodano następujące funkcje, które ułatwiają zapisywanie i konserwowanie aplikacji Windows Communication Foundation (WCF):

- Uproszczenie wygenerowanych plików konfiguracji.

- Obsługa pierwszego rozwoju kontraktu.

- Możliwość łatwiejszego konfigurowania trybu zgodności ASP.NET.

- Zmiany wartości właściwości domyślnych transportu w celu zmniejszenia prawdopodobieństwa, że będzie konieczne ich ustawienie.

- <xref:System.Xml.XmlDictionaryReaderQuotas> Aktualizuje klasę, aby zmniejszyć prawdopodobieństwo, że konieczne będzie ręczne skonfigurowanie przydziałów dla czytników słownika XML.

- Sprawdzanie poprawności plików konfiguracji WCF przez program Visual Studio w ramach procesu kompilacji, dzięki czemu można wykryć błędy konfiguracji przed uruchomieniem aplikacji.

- Nowe asynchroniczne obsłudze przesyłania strumieniowego.

- Nowe mapowanie protokołu HTTPS, aby ułatwić udostępnianie punktu końcowego za pośrednictwem protokołu HTTPS za pomocą Internet Information Services (IIS).

- Możliwość generowania metadanych w jednym dokumencie WSDL przez dołączenie `?singleWSDL` do adresu URL usługi.

- Obsługa obiektów WebSockets w celu umożliwienia prawdziwej komunikacji dwukierunkowej za pośrednictwem portów 80 i 443 z charakterystykami wydajności podobnymi do transportu TCP.

- Obsługa konfigurowania usług w kodzie.

- Etykietki narzędzi edytora XML.

- <xref:System.ServiceModel.ChannelFactory>Obsługa buforowania.

- Obsługa kompresji koderów binarnych.

- Obsługa transportu UDP, który umożliwia deweloperom pisanie usług korzystających z komunikatów "Fire i zapomnij". Klient wysyła komunikat do usługi i oczekuje braku odpowiedzi z usługi.

- Możliwość obsługi wielu trybów uwierzytelniania w jednym punkcie końcowym WCF podczas korzystania z transportu HTTP i zabezpieczeń transportu.

- Obsługa usług WCF korzystających z międzynarodowych nazw domen (IDN).

Aby uzyskać więcej informacji, zobacz [co nowego w Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=228173).

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a>Program Windows Workflow Foundation (WF)

W .NET Framework 4,5 dodano kilka nowych funkcji do Windows Workflow Foundation (WF), w tym:

- Przepływy pracy automatu Stanów, które zostały po raz pierwszy wprowadzone w ramach .NET Framework 4.0.1 ([aktualizacja .NET Framework 4 platformy 1](https://go.microsoft.com/fwlink/?LinkID=215092)). Ta aktualizacja zawiera kilka nowych klas i działań, które umożliwiają deweloperom tworzenie przepływów pracy automatu Stanów. Te klasy i działania zostały zaktualizowane dla .NET Framework 4,5, aby uwzględnić:

  - Możliwość ustawiania punktów przerwania w Stanach.

  - Możliwość kopiowania i wklejania przejść w Projektancie przepływu pracy.

  - Obsługa tworzenia przejść między udostępnionymi wyzwalaczami przez projektanta.

  - Działania tworzenia przepływów pracy automatu Stanów <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>w tym <xref:System.Activities.Statements.Transition>:,, i.

- Ulepszone Projektant przepływu pracy funkcje, takie jak następujące:

  - Ulepszone możliwości wyszukiwania przepływu pracy w programie Visual Studio, w tym **szybkie znajdowanie** i **Znajdowanie plików**.

  - Możliwość automatycznego tworzenia działania sekwencji po dodaniu drugiego działania podrzędnego do działania kontenera oraz w celu uwzględnienia obu działań w działaniu sekwencji.

  - Obsługa panoramowania, która umożliwia zmianę widocznej części przepływu pracy bez używania pasków przewijania.

  - Nowy widok **konspektu dokumentu** , który pokazuje składniki przepływu pracy w widoku konspektu w stylu drzewa i umożliwia wybranie składnika w widoku **konspektu dokumentu** .

  - Możliwość dodawania adnotacji do działań.

  - Możliwość definiowania delegatów działań i korzystania z nich przy użyciu projektanta przepływu pracy.

  - Funkcja AutoConnect i funkcja autoinsert dla działań i przejść w przepływie pracy automatu stanów i schematu blokowego.

- Przechowywanie informacji o stanie widoku dla przepływu pracy w pojedynczym elemencie w pliku XAML, dzięki czemu można łatwo lokalizować i edytować informacje o stanie widoku.

- Działanie kontenera NoPersistScope zapobiegające utrwalaniu działań podrzędnych.

- Obsługa C# wyrażeń:

  - Projekty przepływu pracy używające Visual Basic będą używać wyrażeń Visual Basic, C# a projekty przepływu pracy C# będą używać wyrażeń.

  - C#projekty przepływu pracy utworzone w programie Visual Studio 2010 i zawierające wyrażenia Visual Basic są zgodne z C# projektami przepływu pracy, które C# używają wyrażeń.

- Udoskonalenia wersji:

  - Nowa <xref:System.Activities.WorkflowIdentity> Klasa, która zapewnia mapowanie między utrwalonym wystąpieniem przepływu pracy i jego definicją przepływu pracy.

  - Wykonywanie równoczesne wielu wersji przepływu pracy na tym samym hoście, włącznie <xref:System.ServiceModel.Activities.WorkflowServiceHost>z.

  - W obszarze aktualizacja dynamiczna można modyfikować definicję utrwalonego wystąpienia przepływu pracy.

- Opracowywanie usługi przepływu pracy w pierwszej kolejności, która zapewnia obsługę automatycznego generowania działań w celu dopasowania do istniejącego kontraktu usługi.

Aby uzyskać więcej informacji, zobacz [co nowego w Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=228176).

<a name="tailored" />

### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]

[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikacje są przeznaczone do określonych celów formularzy i wykorzystują możliwości systemu operacyjnego Windows. Podzestaw .NET Framework 4,5 lub 4.5.1 jest dostępny do kompilowania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji dla systemu Windows za pomocą C# lub Visual Basic. Ten podzbiór jest [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] wywoływany i został omówiony w [przeglądzie](https://go.microsoft.com/fwlink/?LinkId=228491) w centrum deweloperów systemu Windows.

### <a name="portable-class-libraries-a-nameportable-"></a>Przenośne biblioteki klas<a name="portable" />

Przenośna biblioteka klas w programie Visual Studio 2012 (i nowszych wersjach) umożliwia pisanie i kompilowanie zestawów zarządzanych, które działają na wielu platformach .NET Framework. Korzystając z projektu biblioteki klas przenośnych, należy wybrać platformy (takie jak Windows Phone i [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) do obiektów docelowych. Dostępne typy i elementy członkowskie w projekcie są automatycznie ograniczone do wspólnych typów i elementów członkowskich na tych platformach. Aby uzyskać więcej informacji, zobacz [Przenośna biblioteka klas](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Zobacz także

- [Program .NET Framework i wydania poza harmonogramem (OOB)](../get-started/the-net-framework-and-out-of-band-releases.md)
- [Co nowego w ułatwieniach dostępu w .NET Framework](whats-new-in-accessibility.md)
- [Co nowego w programie Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio)
- [ASP.NET](/aspnet)
- [Co nowego w wizualizacjiC++](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
