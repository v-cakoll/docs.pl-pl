---
title: What's new in .NET Core 2.1
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 2.1.
author: rpetrusha
ms.author: ronpet
ms.date: 06/06/2018
ms.openlocfilehash: 850df87666c5beb0594f0672d8f558c11653f973
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079724"
---
# <a name="whats-new-in-net-core-21"></a>What's new in .NET Core 2.1

.NET core 2.1 zawiera ulepszenia i nowe funkcje w następujących obszarach:

- [Narzędzia](#tooling)
- [Przenoszenia do przodu](#roll-forward)
- [Wdrażanie](#deployment)
- [Windows Compatibility Pack](#windows-compatibility-pack)
- [Ulepszenia kompilacji JIT](#jit-compiler-improvements)
- [Zmiany interfejsu API](#api-changes)

## <a name="tooling"></a>Narzędzia

.NET Core 2.1 SDK (v 2.1.300), narzędzia dostępne przy użyciu platformy .NET Core 2.1, obejmuje następujące zmiany i udoskonalenia:

### <a name="build-performance-improvements"></a>Ulepszenia wydajności kompilacji

W centrum uwagi platformy .NET Core 2.1 jest poprawę wydajności w czasie kompilacji, szczególnie w przypadku kompilacji przyrostowych. Te ulepszenia wydajności dotyczą zarówno kompilacji z wiersza polecenia przy użyciu `dotnet build` i kompilacji w programie Visual Studio. Niektóre poszczególne obszary ulepszeń należą:

- Rozpoznawanie zawartości pakietu rozpoznawanie tylko zasoby używane przez kompilację, a nie wszystkie zasoby.

- Buforowanie odwołania do zestawu.

- Użyj zestawu SDK długotrwałych kompilacji serwerów, które są procesy, które rozciągają się na poszczególnych `dotnet build` wywołania. One wyeliminować potrzebę dużych bloków kodu, skompilować wg JIT zawsze `dotnet build` jest uruchamiany. Tworzenie serwera, które mogą być automatycznie zakończone procesy za pomocą następującego polecenia:

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Nowe polecenia interfejsu wiersza polecenia

Wiele narzędzi, które były dostępne tylko na podstawę projektu przy użyciu [ `DotnetCliToolReference` ](../tools/extensibility.md) są teraz dostępne jako część zestawu .NET Core SDK. Do tych narzędzi należą:

- `dotnet watch` Zawiera obserwatora systemu plików, który oczekuje na plik, aby zmienić przed wykonaniem wyznaczonym zestaw poleceń. Na przykład następujące polecenie automatycznie odtwarza bieżącego projektu i generuje pełne dane wyjściowe przy każdym zmian w plikach w nim:

   ```console
   dotnet watch -- --verbose build
   ```

   Uwaga `--` opcję poprzedzającą `--verbose` opcji. Jego rozgranicza opcje przekazane bezpośrednio do `dotnet watch` polecenia na podstawie argumentów, które są przekazywane do elementu podrzędnego `dotnet` procesu. Bez tego `--verbose` opcja ma zastosowanie do `dotnet watch` nie polecenia `dotnet build` polecenia.
  
   Aby uzyskać więcej informacji, zobacz [aplikacji opracowywanie platformy ASP.NET Core przy użyciu Obejrzyj dotnet](/aspnet/core/tutorials/dotnet-watch)

- `dotnet dev-certs` generuje klucze i zarządza certyfikatami używanymi podczas tworzenia aplikacji platformy ASP.NET Core.

- `dotnet user-secrets` zarządza wpisów tajnych w magazynie wpisu tajnego użytkownika w aplikacji platformy ASP.NET Core.

- `dotnet sql-cache` tworzy tabelę i indeksy w bazie danych programu Microsoft SQL Server do użytku z rozproszonego buforowania.

- `dotnet ef` to narzędzie do zarządzania bazami danych, <xref:Microsoft.EntityFrameworkCore.DbContext> obiektów i migracje platformy Entity Framework Core aplikacji. Aby uzyskać więcej informacji, zobacz [narzędzia wiersza polecenia platformy .NET Core EF](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Narzędzia globalne

Obsługuje platformy .NET core 2.1 *globalnego narzędzia* — czyli narzędzia niestandardowe, które są dostępne globalnie w wierszu polecenia. Model rozszerzalności w poprzednich wersjach programu .NET Core udostępnione narzędzia niestandardowe na podstawie projektu tylko przy użyciu [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).

Aby zainstalować narzędzie globalne, należy użyć [instalacji narzędzi dotnet](..\tools\dotnet-tool-install.md) polecenia. Na przykład:

```console
dotnet tool install -g dotnetsay
```

Po zakończeniu instalacji można uruchomić narzędzie z wiersza polecenia, określając nazwę narzędzia. Aby uzyskać więcej informacji, zobacz [Omówienie narzędzia globalnej platformy .NET Core](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Narzędzie do zarządzania za pomocą `dotnet tool` polecenia

W .NET Core SDK 2.1 (v 2.1.300), wszystkie operacje narzędzia za pomocą `dotnet tool` polecenia. Dostępne są następujące opcje:

- [`dotnet tool install`](../tools/dotnet-tool-install.md) Aby zainstalować narzędzie.

- [`dotnet tool update`](../tools/dotnet-tool-update.md) Aby odinstalować i ponownie zainstaluj narzędzie, które skutecznie aktualizuje.

- [`dotnet tool list`](../tools/dotnet-tool-list.md) Aby wyświetlić listę aktualnie zainstalowanych narzędzi.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) Aby odinstalować aktualnie zainstalowanego narzędzia.

## <a name="roll-forward"></a>Przenoszenia do przodu

Wszystkie aplikacje platformy .NET Core, począwszy od programu .NET Core 2.0 automatycznie uaktualniane do najnowszej wersji *wersja pomocnicza* zainstalowanego w systemie.

Uruchamianie przy użyciu platformy .NET Core 2.0, jeśli wersja programu .NET Core, która została zbudowana aplikacja nie jest obecny w czasie wykonywania, aplikacja automatycznie uruchamiana najnowszej zainstalowanej *wersja pomocnicza* programu .NET Core. Innymi słowy Jeśli aplikacja jest oparte na platformie .NET Core 2.0 i .NET Core 2.0 nie jest dostępny w systemie hosta, ale jest platformy .NET Core 2.1, aplikacja zostanie uruchomiona przy użyciu platformy .NET Core 2.1.

> [!IMPORTANT]
> To zachowanie przodu nie ma zastosowania do wersji w wersji zapoznawczej. Nie ma zastosowania do wersji głównej. Na przykład aplikacji platformy .NET Core 1.0 w takich sytuacjach przydałaby uaktualniane do platformy .NET Core 2.0 lub platformy .NET Core 2.1.

Można również wyłączyć roll wersję pomocniczą na jeden z trzech sposobów:

- Ustaw `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` zmiennej środowiskowej na wartość 0.

- Dodaj następujący wiersz do pliku runtimeconfig.json:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- Korzystając z [narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md), obejmują będzie następująca opcja za pomocą polecenia .NET Core, takie jak `run`:

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a>wdrażania

### <a name="self-contained-application-servicing"></a>Aplikacja samodzielna obsługi

`dotnet publish` teraz publikowanie niezależna aplikacji przy użyciu wersji środowiska uruchomieniowego obsługiwanych. Podczas publikowania niezależna aplikacji przy użyciu zestawu .NET Core 2.1 SDK (v 2.1.300), aplikacja zawiera najnowszą wersję środowiska uruchomieniowego obsługiwanych znane przez ten zestaw SDK. Podczas uaktualniania na najnowszy zestaw SDK będzie publikowania za pomocą najnowszej wersji środowiska uruchomieniowego .NET Core. Dotyczy to dla środowisk uruchomieniowych platformy .NET Core 1.0 lub nowszy.

Publikowanie niezależne opiera się na wersje środowiska uruchomieniowego w witrynie NuGet.org. Nie trzeba mieć obsługiwane środowiska uruchomieniowego na komputerze.

Przy użyciu zestawu .NET Core 2.0 SDK, samodzielne aplikacje są publikowane w środowisku uruchomieniowym .NET Core 2.0.0 chyba że inna wersja jest określona za pomocą `RuntimeFrameworkVersion` właściwości. Za pomocą to nowe zachowanie nie jest już należy ustawić tę właściwość, aby wybrać wyższą wersję środowiska uruchomieniowego niezależna aplikacji. To najłatwiejsza metoda przechodzenia do przodu jest zawsze publikowanie przy użyciu zestawu SDK platformy .NET Core 2.1 (v 2.1.300).

Aby uzyskać więcej informacji, zobacz [niezależna deploymnet środowiska uruchomieniowego przenoszenia do przodu](../deploying/runtime-patch-selection.md).
## <a name="windows-compatibility-pack"></a>Windows Compatibility Pack

Jeśli przeniesiesz istniejący kod z programu .NET Framework i .NET Core, możesz użyć [systemie Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Zapewnia dostęp do 20 000 więcej interfejsów API, niż jest dostępnych w programie .NET Core. Te interfejsy API i obejmuje dodatkowe typy w <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw, <xref:System.Diagnostics.EventLog> klasy, usługi WMI, liczniki wydajności, usług Windows i Windows rejestru typów i członków.

## <a name="jit-compiler-improvements"></a>Ulepszenia kompilatora JIT

.NET core zawiera nową technologię kompilatora JIT, o nazwie *warstwowego kompilacji* (znany także jako *adaptacyjne optymalizacji*), może znacznie poprawić wydajność. Warstwowe kompilacja jest ustawienie zgłoszenie zgody na uczestnictwo.

Jedną z ważnych zadania wykonywane przez kompilator JIT jest zoptymalizowanie wykonywania kodu. Jednak dla ścieżek kodu rzadko używanych kompilator może poświęcić więcej czasu na optymalizację kodu niż środowisko uruchomieniowe spędzony przez uruchamianie kodu w sposób niezoptymalizowany. Kompilacja warstwowego wprowadzono dwa etapów w ramach kompilacji JIT:

- A **najpierw warstwy**, która generuje kod tak szybko, jak to możliwe.

- A **Druga warstwa**, która generuje zoptymalizowanego kodu dla tych metod, które są często wykonywane. Druga warstwa kompilacji odbywa się w sposób równoległy, aby uzyskać lepszą wydajność.

Możesz zdecydować się na warstwowy kompilacji na dwa sposoby.

- Aby używać warstwowego kompilacji w projektach korzystających z zestawu SDK programu .NET Core 2.1, Ustaw następującą zmienną środowiskową:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Aby użyć kompilacji warstwowego na poszczególnych projektów, należy dodać `<TieredCompilation>` właściwość `<PropertyGroup>` części pliku projektu MSBuild, co ilustruje poniższy przykład:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>Zmiany interfejsu API

### <a name="spant-and-memoryt"></a>`Span<T>` i `Memory<T>`

.NET core 2.1 zawiera kilka nowych typów, które sprawiają, że praca z tablicami i inne rodzaje pamięci znacznie bardziej efektywne. Nowe typy obejmują:

- <xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> i <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bez tych typów przy przekazywaniu takie elementy jako część tablicy lub sekcji bufora pamięci należy utworzyć kopię część danych przed przekazaniem go do metody. Te typy zapewniają wirtualny widok tych danych, która eliminuje potrzebę stosowania alokacji więcej pamięci i operacji kopiowania.

W poniższym przykładzie użyto <xref:System.Span%601> wystąpienia, aby przedstawić widok wirtualny 10 elementów tablicy.

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a>Kompresja Brotli

.NET core 2.1 dodaje obsługę Brotli kompresji i dekompresji. Brotli to algorytm kompresji bezstratne ogólnego przeznaczenia, który jest zdefiniowany w [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) i są obsługiwane w większości przeglądarek sieci web i serwery główne sieci web. Można użyć, na podstawie strumienia <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> klasy lub o wysokiej wydajności na podstawie zakresu <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> i <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> klasy. W poniższym przykładzie pokazano metody kompresji <xref:System.IO.Compression.BrotliStream> klasy:

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<xref:System.IO.Compression.BrotliStream> Zachowanie jest taka sama jak <xref:System.IO.Compression.DeflateStream> i <xref:System.IO.Compression.GZipStream>, który można łatwo przekonwertować kodu, który wywołuje te interfejsy API do <xref:System.IO.Compression.BrotliStream>.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Nowe elementy interfejsu API kryptografii i ulepszenia kryptografii

.NET core 2.1 zawiera wiele udoskonaleń cryptography API:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> jest dostępna w pakiecie System.Security.Cryptography.Pkcs. Implementacja jest taka sama jak <xref:System.Security.Cryptography.Pkcs.SignedCms> klasy w .NET Framework.

- Nowe przeciążenia <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody akceptuje identyfikator algorytmu wyznaczania wartości skrótu, umożliwiając metodom wywołującym można pobrać wartości odcisku palca certyfikatu, przy użyciu algorytmów niż SHA-1.

- Nowe <xref:System.Span%601>— oparte na kryptografii interfejsy API są dostępne do tworzenia skrótu HMAC, kryptograficzne Generowanie liczby losowej, asymetryczne generowania, przetwarzania asymetrycznego podpisu i szyfrowania RSA.

- Wydajność <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> ulepszono o około 15%, za pomocą <xref:System.Span%601>— na podstawie implementacji.

- Nowy <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> klasa zawiera dwie nowe metody:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> ma ustaloną ilość czasu, aby powrócić do dowolnego dwóch danych wejściowych o takiej samej długości, która sprawia, że nadaje się do użytku w kryptograficznych weryfikacji, aby uniknąć, przyczyniając się do czasu informacji kanału po stronie.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> to nie można zoptymalizować procedura czyszczenia pamięci.

- Statyczne <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> wypełnienia metoda <xref:System.Span%601> przy użyciu wartości losowych.

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Jest teraz obsługiwana w systemie Linux i maxOS.

- Grupa Diffie'ego-Hellmana krzywej eliptycznej (ECDH) jest teraz dostępna w <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> klasy rodziny. Obszar powierzchni jest taka sama, jak w programie .NET Framework.

- Wystąpienie zwrócone przez <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> zaszyfrować lub odszyfrować za pomocą OAEP przy użyciu skrótu SHA-2, a także Generowanie lub zweryfikować podpisu RSA-PSS przy użyciu usługi.

### <a name="sockets-improvements"></a>Ulepszenia gniazda

.NET core zawiera nowy typ <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>oraz nowych <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, które stanowią podstawę sieci wyższego poziomu interfejsów API.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, na przykład, będącą podstawą <xref:System.Net.Http.HttpClient> implementacji. W poprzednich wersjach programu .NET Core API wyższego poziomu znajdowały się na implementacji sieci.

Implementacja gniazda, wprowadzone w programie .NET Core 2.1 ma szereg zalet:

- Poprawa istotnie poprawiającą wydajność w porównaniu z poprzednim wdrożenia.

- Eliminacja zależności platformy, która upraszcza wdrażanie i obsługę.

- Spójne zachowanie na wszystkich platformach .NET Core.

<xref:System.Net.Http.SocketsHttpHandler> jest implementacją domyślną w programie .NET Core 2.1. Jednak należy skonfigurować aplikację do starszej wersji <xref:System.Net.Http.HttpClientHandler> klasy przez wywołanie metody <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody:

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

Możesz również użyć środowiska zmiennej, aby zrezygnować z przy użyciu gniazd implementacji na podstawie <xref:System.Net.Http.SocketsHttpHandler>. Aby to zrobić, należy ustawić `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` do jednej `false` lub równa 0.

W Windows, możesz również używać <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, która opiera się na natywnych implementacji lub <xref:System.Net.Http.SocketsHttpHandler> klasy przez przekazanie wystąpienia klasy do <xref:System.Net.Http.HttpClient> konstruktora.

W systemie Linux i macOS, można skonfigurować tylko <xref:System.Net.Http.HttpClient> na zasadzie na proces. W systemie Linux, należy wdrożyć [libcurl](https://curl.haxx.se/libcurl/) Jeśli chcesz używać starego <xref:System.Net.Http.HttpClient> implementacji. (Jest instalowany przy użyciu platformy .NET Core 2.0.)

## <a name="see-also"></a>Zobacz także

* [Co nowego w programie .NET Core](index.md)  
* [Nowe funkcje programu EF Core 2.1](/ef/core/what-is-new/ef-core-2.1)  
* [What's new in platformy ASP.NET Core 2.1](/aspnet/core/aspnetcore-2.1)
