---
title: What's new in .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 3ca833031eb8bb0f43a334f833f2e0075842d57d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155481"
---
# <a name="whats-new-in-net-core-30-preview-1"></a>What's new in .NET Core 3.0 (wersja zapoznawcza 1)

W tym artykule opisano nowości w programie .NET Core 3.0 (wersja zapoznawcza 1). Jedną z największych ulepszenia to obsługa aplikacji klasycznych Windows (tylko Windows). Przy użyciu platformy .NET Core 3.0 to składnik o nazwie Windows Desktop, można przenosić aplikacje Windows Forms Windows Presentation Foundation (WPF). Aby być niejasne, składnik Windows Desktop jest obsługiwana tylko na Windows. Aby uzyskać więcej informacji, zobacz sekcję [pulpitu Windows](#windows-desktop) poniżej.

.NET core 3.0 dodaje obsługę C# 8.0.

[Pobierz i rozpoczynanie pracy z usługą .NET Core 3 (wersja zapoznawcza) 1](https://aka.ms/netcore3download) teraz na Windows, Mac i Linux. Można wyświetlić szczegółowe informacje o wersji w [informacje o wersji platformy .NET Core 3 (wersja zapoznawcza) 1](https://aka.ms/netcore3releasenotes).

Aby uzyskać więcej informacji, zobacz [ogłoszenie .NET Core 3.0 w wersji zapoznawczej 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).

## <a name="net-standard-21"></a>.NET standard 2.1

.NET core 3.0 implementuje platformy .NET Standard 2.1.

## <a name="default-executables"></a>Domyślne pliki wykonywalne

.NET core będzie teraz tworzyć pliki wykonywalne domyślnie. Jest to nowość w aplikacji, które używają globalnie zainstalowaną wersję platformy .NET Core. Do tej pory tylko [niezależna wdrożeń](../deploying/index.md#self-contained-deployments-scd) miał plików wykonywalnych.

Podczas `dotnet build` lub `dotnet publish`, plik wykonywalny jest tworzony, pod warunkiem, które odpowiadają środowisko i platforma używasz zestawu SDK. Mogą spodziewać się tego samego rzeczy, korzystając z tych plików wykonywalnych, tak jak w innych natywnych plików wykonywalnych, takich jak:

* Możesz kliknąć dwukrotnie plik wykonywalny.
* Można uruchomić aplikacji z poziomu wiersza polecenia, takie jak `myapp.exe` na Windows, i `./myapp` w systemie Linux i macOS.

> [!NOTE]
> Określanie określonego środowiska uruchomieniowego za pomocą `dotnet publish -r` lub `dotnet build -r` argumentów w innych środowiskach środowisko uruchomieniowe nie jest obsługiwane.

## <a name="build-copies-dependencies"></a>Kopiuje zależności kompilacji

`dotnet build` teraz kopiuje zależności NuGet dla aplikacji z pamięcią podręczną programu NuGet do folderu wyjściowego kompilacji. Wcześniej zależności zostały skopiowane tylko jako część `dotnet publish`. 

Istnieją pewne operacje takie jak łączenie i razor strony publikowania, który nadal będzie wymagać publikowania.


## <a name="local-dotnet-tools"></a>Narzędzia do lokalnego dotnet

.NET Core 2.1 obsługiwana globalnego narzędzia, .NET Core 3.0 to ma teraz lokalne narzędzia. Lokalne narzędzia są podobne do narzędzia globalnych, ale są skojarzone z określonej lokalizacji na dysku. Dzięki temu projektów i narzędzi na repozytorium. Wszystkie zainstalowane lokalnie narzędzie nie jest globalnie dostępna.

Lokalne narzędzia opierają się na nazwę pliku manifestu `dotnet-tools.json` w bieżącym katalogu. Ten plik manifestu definiuje narzędzia, które mają być dostępne. Ten plik manifestu są tworzone w katalogu głównym repozytorium, możesz upewnij się, każdy klonowania kodu można przywrócić i korzystania z narzędzi, które są niezbędne do pomyślnie pracę z kodem.

Po udostępnieniu pliku manifestu lokalne narzędzia, użyj następującego polecenia do automatycznego pobierania i instalowania tych narzędzi lokalnie:

```console
dotnet tool restore
```

Uruchom narzędzie lokalnych za pomocą następującego polecenia:

```console
dotnet tool run <tool-command-name>
```

Po wywołaniu lokalne narzędzie dotnet wyszukuje manifest się struktury katalogów. W przypadku odnalezienia pliku manifestu narzędzie przeszukiwany jest dla żądanego narzędzia. Jeśli narzędzie zostanie znaleziony, zawiera informacje dotyczące znajdowania narzędzia w lokalizacji globalnymi pakietami NuGet. 

Jeśli narzędzie zostanie znaleziony w manifeście, ale nie pamięci podręcznej, zostanie wyświetlony błąd. Zostanie on ulepszony komunikat po 1 (wersja zapoznawcza), aby poprosić użytkownika Uruchom `dotnet tool restore`.

Dodawanie lokalnych narzędzi do katalogu, należy najpierw utworzyć plik manifestu narzędzia. Po 1 (wersja zapoznawcza) oferujemy mechanizm służący do tworzenia plików manifestu, takie jak nowy szablon dotnet narzędzia. W przypadku 1 (wersja zapoznawcza), musisz utworzyć plik o nazwie `dotnet-tools.json` z następującą zawartością:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Po utworzeniu manifestu, lokalnego narzędzia można dodać do niego przy użyciu:

```console
dotnet tool install <toolPackageId>
```

To polecenie instaluje najnowszą wersję narzędzia, chyba że określono inną wersję.  Nawet jeśli automatycznie wybrano najnowszą wersję, wersję narzędzia są zapisywane w pliku manifestu narzędzia, aby umożliwić poprawną wersję narzędzia go przywrócić lub uruchom.

Plik manifestu narzędzia zaprojektowano w celu Zezwól na edytowanie strony — co może zrobić, aby zaktualizować wersję wymagane do pracy z repozytorium.

Oto przykład `dotnet-tools.json` pliku:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

Aby usunąć narzędzie z pliku manifestu narzędzia, uruchom następujące polecenie:

```console
dotnet tool uninstall <toolPackageId>
```

Globalne i lokalne narzędzi zgodna wersja środowiska uruchomieniowego jest wymagana. Wiele narzędzi, obecnie w witrynie NuGet.org docelowej platformy .NET Core środowiska uruchomieniowego 2.1. Aby zainstalować te globalnie lub lokalnie, czy nadal należy zainstalować [środowisko uruchomieniowe programu NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

Aby uzyskać więcej informacji, zobacz [lokalne narzędzia wczesne dokumentacja w wersji zapoznawczej](https://github.com/dotnet/cli/issues/10288).

## <a name="windows-desktop"></a>Pulpit systemu Windows

Począwszy od programu .NET Core 3.0 w wersji zapoznawczej 1, możesz tworzyć aplikacje pulpitu Windows przy użyciu WPF i Windows Forms. Następujące struktury obsługi, za pomocą nowoczesnych kontrolek i Fluent stylów z biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [Wyspy XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Składnik Windows Desktop jest częścią Windows zestaw SDK programu .NET Core 3.0.

Można utworzyć nowej aplikacji WPF i Windows Forms z następującymi `dotnet` poleceń:

```console
dotnet new wpf
dotnet new winforms
```

Można również otworzyć, uruchomić i debugowania projektów .NET Core 3.0 WPF i Windows Forms w programie Visual Studio 2019 r w wersji zapoznawczej 1. Obecnie można otwierać te projekty w programie Visual Studio 2017 15.9, jednak nie jest obsługiwanym scenariuszem (i należy [Włącz podglądy](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).

Nowe projekty są takie same jak istniejących projektów .NET Core z dodatkami kilka. Oto porównanie podstawowy projekt konsoli .NET Core i podstawowy projekt Windows Forms i WPF.

W projekcie konsoli .NET Core, projekt korzysta z `Microsoft.NET.Sdk` zestawu SDK ale deklaruje zależności na .NET Core 3.0 to za pośrednictwem `netcoreapp3.0` platformy docelowej. Aby utworzyć aplikację pulpitu Windows, należy użyć `Microsoft.NET.Sdk.WindowsDesktop` zestawu SDK i wybierz polecenie struktury interfejsu użytkownika, których można użyć:

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

Aby wybrać Windows Forms w WPF, należy ustawić `UseWindowsForms` zamiast `UseWPF`:

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

Zarówno `UseWPF` i `UseWindowsForms` można ustawić `true` Jeśli aplikacja korzysta z obu platform, na przykład gdy okno dialogowe Windows Forms jest hosting kontrolki WPF.

Podziel się swoją opinię na [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) i [dotnet/core](https://github.com/dotnet/core/issues) repozytoriów.

## <a name="fast-built-in-json-support"></a>Szybkie wbudowanej obsługi formatu JSON

`System.Text.Json.Utf8JsonReader` jest o wysokiej wydajności, niski alokacji, tylko do przodu czytnik UTF-8 kodowany w formacie JSON tekst odczytywane `ReadOnlySpan<byte>`. `Utf8JsonReader` Jest typem podstawowe, niskiego poziomu, który można wykorzystać do tworzenia niestandardowych analizatory i deserializers. Odczytywanie za pośrednictwem ładunek w formacie JSON za pomocą nowego `Utf8JsonReader` wynosi 2 x szybciej niż przy użyciu czytnika, z [Json.NET](https://www.newtonsoft.com/json). Nie przydziela do czasu konieczne actualize tokenów JSON jako ciągi (UTF-16).

Ten nowy interfejs API obejmuje następujące składniki:

* W wersji zapoznawczej 1: Czytnik JSON (dostępu sekwencyjnego)
* Dodana w następnej kolejności: Moduł zapisujący JSON, modelu DOM (dostępu swobodnego) obiektów poco elementu serializującego obiektów poco Deserializator

Oto pętli czytnika podstawowego `Utf8JsonReader` mogą służyć jako punkt początkowy:

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

Ekosystemu .NET opierało się na [Json.NET](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal dobrych wyborów. Program JSON.NET używa ciągów .NET jako jego podstawowy datatype kulisy używanej na UTF-16. 

W programie .NET Core 2.1 i 3.0, dodaliśmy nowe interfejsy API, który sprawia, że można pisać interfejsy API w formacie JSON (takich jak `Utf8JsonReader`) wymagających znacznie mniej pamięci, oparte na użyciu `Span<T>` i ciągi znaków UTF-8 i lepsze potrzebami aplikacji o wysokiej przepływności, takich jak Kestrel, ASP. Serwer sieci web .NET Core.

## <a name="ranges-and-indices"></a>Zakresy i indeksy

Nowy `Index` typ może być używany do indeksowania. Można utworzyć jeden z `int` , jest liczona od początku lub z prefiksem `^` — operator (C#), jest liczona od końca:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Istnieje również `Range` typ, który składa się z dwóch `Index` wartości, jeden dla początkowego i jeden dla elementu end i mogą być zapisywane z `x..y` zakres wyrażenia (C#). Następnie można zaindeksować z `Range` w celu tworzenia wycinka:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> Tylko [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) obsługuje składnię `Range` i `Index`.

## <a name="async-streams"></a>Asynchroniczne strumienie

`IAsyncEnumerable<T>` Typu jest nowa wersja asynchroniczne `IEnumerable<T>`. Język umożliwia `await foreach` za pośrednictwem tych zasobów w celu korzystania z ich elementów i `yield return` do ich do produkcji elementów.

Poniższy przykład ilustruje środowiska produkcyjnego i zużycia strumieni asynchronicznych. `foreach` Instrukcja jest asynchroniczne, a sam używa `yield return` do produkcji strumienia asynchronicznego dla obiektów wywołujących. Ten wzorzec (przy użyciu `yield return`) to zalecany model do produkcji strumieni asynchronicznych.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> .NET core 3.0 w wersji zapoznawczej 1 ma obecnie usterki, przy użyciu `await foreach`. Zamiast tego należy użyć `GetEnumerator` i `MoveNext` elementy procesu. Aby uzyskać więcej informacji, zobacz [roslyn / #31268](https://github.com/dotnet/roslyn/issues/31268).

Oprócz możliwości `await foreach`, można również utworzyć async Iteratory, na przykład iterator, który zwraca `IAsyncEnumerable/IAsyncEnumerator` można zarówno `await` i `yield` w. W przypadku obiektów, które muszą zostać zlikwidowany, można użyć `IAsyncDisposable`, który implementuje różnych typów BCL, takich jak `Stream` i `Timer`.

> [!NOTE]
> Tylko [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) obsługuje `await foreach` składni.

## <a name="type-sequencereader"></a>Wpisz: SequenceReader

W programie .NET Core 3.0 `System.Buffers.SequenceReader` dodano, który może służyć jako czytnik `ReadOnlySequence<T>`. Umożliwia to łatwe w użyciu o wysokiej wydajności, niski alokacji analizowanie `System.IO.Pipelines` dane, które mogą przechodzić przez kilka buforów zapasowy. 

Poniższy przykład dzieli dane wejściowe `Sequence` na prawidłowe `CR/LF` rozdzielonych wiersze:

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>Wpisz: MetadataLoadContext

`MetadataLoadContext` Typ został dodany, który umożliwia odczytywanie zestawu metadanych, bez wywierania wpływu na domeny aplikacji obiektu wywołującego. Zestawy są odczytywane jako dane, w tym zestawy stworzona z myślą o różnych architektur oraz platformach niż bieżącego środowiska. `MetadataLoadContext` nakłada się na <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, która jest dostępna tylko w programie .NET Framework.

`MetdataLoadContext` jest dostępna w [pakietu System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext). To pakiet .NET Standard 2.0.

`MetadataLoadContext` Udostępnia interfejsy API, podobnie jak <xref:System.Runtime.Loader.AssemblyLoadContext> typu, ale nie zależy od tego typu. Podobnie jak <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` umożliwia ładowanie zestawów w zestawie izolowane ładowania wszechświat. `MetdataLoadContext` Interfejsy API zwracają <xref:System.Reflection.Assembly> obiektów, umożliwiające użycie odbicia dobrze znanych interfejsów API. Wykonanie zorientowane na interfejsy API, takich jak [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), nie są dozwolone i będzie zgłaszać wyjątek InvalidOperationException.

W poniższym przykładzie pokazano, jak znaleźć konkretne typy w zestawie, który implementuje danego interfejsu:

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

Scenariusze dotyczące `MetadataLoadContext` obejmują funkcje czasu projektowania, narzędzi, czas kompilacji i środowiska uruchomieniowego światła w górę funkcje wymagające sprawdzanie zbiór zestawów danych i ma blokady wszystkich plików i pamięć zwolniona po kontroli jest wykonywane.

`MetadataLoadContext` Przeszła klasy programu rozpoznawania nazw dla jego konstruktora. Zadanie programu rozpoznawania nazw ma ładować `Assembly` biorąc pod uwagę jej `AssemblyName`. Klasa rozpoznawania pochodzi z abstrakcyjnej `MetadataAssemblyResolver` klasy. Implementacja programu rozpoznawania nazw dla scenariuszy opartych na ścieżkach jest dostarczana z `PathAssemblyResolver`.

[Testy MetadataLoadContext](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) pokazują wielu przypadków użycia. [Zestawu testów](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) są dobrym miejscem do rozpoczęcia.

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & OpenSSL 1.1.1 w systemie Linux

.NET core będą teraz korzystać z [Obsługa protokołu TLS 1.3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy będzie ona dostępna w danym środowisku. Istnieją różne korzyści 1.3 protokołu TLS na [zespołu OpenSSL](https://www.openssl.org/blog/blog/2018/09/11/release111/):

* Czas połączenia ulepszona z powodu ograniczenia liczby rund między klientem a serwerem.

* Ulepszone zabezpieczenia z powodu usunięcia rozmaite algorytmy kryptograficzne przestarzały i niezabezpieczone i szyfrowania większej uzgadniania połączenia.

.NET core 3.0 w wersji zapoznawczej 1 jest w stanie wykorzystujących **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, lub **OpenSSL 1.0.2** (niezależnie od znaleziono wersji najlepiej jest, w systemie Linux).  Podczas **OpenSSL 1.1.1** jest dostępna będzie używać typów SslStream i HttpClient **TLS 1.3** korzystając z `SslProtocols.None` (protokołów domyślne systemu), zakładając, że klient i serwer obsługi **TLS 1.3**.

W poniższym przykładzie pokazano .NET Core 3.0 w wersji zapoznawczej 1 na 18.10 Ubuntu nawiązywania połączenia z <https://www.cloudflare.com>:

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows i macOS nie jest jeszcze obsługiwany **TLS 1.3**. .NET core 3.0 to będzie obsługiwać **TLS 1.3** w tych systemach operacyjnych po udostępnieniu Pomocy technicznej.

## <a name="cryptography"></a>Kryptografia

Dodano obsługę dla **AES-GCM** i **AES-CCM** szyfrów, wdrożone za pośrednictwem `System.Security.Cryptography.AesGcm` i `System.Security.Cryptography.AesCcm`. Te algorytmy są [uwierzytelnione szyfrowanie za pomocą algorytmów skojarzenia danych (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption)i pierwszy algorytmów szyfrowania uwierzytelniony (AE) dodane do platformy .NET Core.

Poniższy kod demonstruje użycie **AesGcm** szyfrowania do szyfrowania i odszyfrowywania danych losowych.

Kod **AesCcm** będzie wyglądała niemal identyczne (tylko nazwy zmiennych klasy może się różnić).

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>Kryptograficznych kluczy importu/eksportu

.NET core 3.0 w wersji zapoznawczej 1 obsługuje importowanie i eksportowanie kluczy asymetrycznych publicznych i prywatnych z standardowych formatów, bez konieczności korzystania z certyfikatu X.509.

Wszystkie klucza Obsługa typów (RSA, DSA, ECDsa, ECDiffieHellman) **X.509 SubjectPublicKeyInfo** format kluczy publicznych i **PKCS #8 PrivateKeyInfo** i **PKCS #8 EncryptedPrivateKeyInfo**  formatów dla kluczy prywatnych. Dodatkowo obsługuje RSA **PKCS #1 RSAPublicKey** i **PKCS #1 RSAPrivateKey**. Wszystkie metody eksportowania generuje dane binarne zakodowane w formacie DER i metod import oczekiwać takie same. Jeśli klucz jest przechowywany w formacie PEM przyjaznego tekstu, obiekt wywołujący, będą musieli base64 — dekodowanie zawartości przed wywołaniem metody importu.

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

Pliki PKCS #8 mogą być kontrolowane za pomocą `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` klasy.

Pliki PFX/PKCS #12, które mogą być kontrolowane i modyfikować za pomocą `System.Security.Cryptography.Pkcs.Pkcs12Info` i `System.Security.Cryptography.Pkcs.Pkcs12Builder`, odpowiednio.

## <a name="serialport-for-linux"></a>Portu SerialPort dla systemu Linux

.NET core 3.0 obsługuje teraz <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> w systemie Linux.

Wcześniej, .NET Core obsługiwana tylko przy użyciu `SerialPort` typu na Windows.

## <a name="more-bcl-improvements"></a>Więcej udoskonaleń BCL

`Span<T>`, `Memory<T>`, I w środowisku .NET Core 3.0 zostały zoptymalizowane powiązanych typów, które zostały wprowadzone w programie .NET Core 2.1. Typowe operacje takie jak span konstrukcji, dzielenie, analizowania i formatowanie teraz działać lepiej. 

Ponadto takie jak typy `String` przejrzane czyni je bardziej efektywnymi, gdy jest używana jako klucze o ulepszenia w obszarze cover `Dictionary<TKey, TValue>` i innych kolekcji. Bez zmian w kodzie są wymagane do korzystania z tych ulepszeń.

Następujące ulepszenia również są nowe w .NET Core 3 (wersja zapoznawcza) 1:

* Obsługa Brotli wbudowanej w HttpClient
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* Złożone operatory arytmetyczne
* Podtrzymywania API gniazda TCP
* StringBuilder.GetChunks
* IPEndPoint analizy
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>Warstwowe kompilacji

[Warstwowe kompilacji](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) jest domyślnie przy użyciu platformy .NET Core 3.0. Jest funkcją, która umożliwia bardziej adaptacyjnie Użyj kompilator just in Time (JIT), aby uzyskać lepszą wydajność, zarówno podczas uruchamiania i w celu zmaksymalizowania wydajności.

Ta funkcja została dodana jako funkcja opcjonalna w [platformy .NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) i następnie została włączona domyślnie w [.NET Core 2.2 w wersji zapoznawczej 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/). Następnie został on przywrócony do zoptymalizowany pod kątem się przy użyciu wersji platformy .NET Core 2.2.

## <a name="arm64-linux-support"></a>Obsługa systemu Linux ARM64

Dodajemy obsługę tej wersji systemu Linux dla architektury ARM64. Kontekst Dodaliśmy obsługę ARM32 dla systemu Linux przy użyciu platformy .NET Core 2.1 i Windows przy użyciu platformy .NET Core 2.2. Głównym zastosowaniem dla architektury ARM64 jest obecnie używany w scenariuszach IoT.

Firma Alpine, Debian i Ubuntu [obrazów platformy Docker są dostępne dla platformy .NET Core dla architektury ARM64](https://hub.docker.com/r/microsoft/dotnet/).

Sprawdź, czy [stanu programu .NET Core ARM64](https://github.com/dotnet/announcements/issues/82) Aby uzyskać więcej informacji.

>[!NOTE]
> **ARM64** pomocy technicznej Windows nie jest jeszcze dostępna.
