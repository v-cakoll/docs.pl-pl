---
title: Co nowego w programie .NET Core 2.1
description: Dowiedz się więcej o nowych funkcjach, które można znaleźć w .NET Core 2.1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 54ace52fc6a8f4614c1f762b65453979bcb92c7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398868"
---
# <a name="whats-new-in-net-core-21"></a>Co nowego w programie .NET Core 2.1

.NET Core 2.1 zawiera ulepszenia i nowe funkcje w następujących obszarach:

- [Narzędzia](#tooling)
- [Przewiń do przodu](#roll-forward)
- [Wdrożenie](#deployment)
- [Pakiet zgodności systemu Windows](#windows-compatibility-pack)
- [Ulepszenia kompilacji JIT](#jit-compiler-improvements)
- [Zmiany interfejsu API](#api-changes)

## <a name="tooling"></a>Narzędzia

Zestaw SDK .NET Core 2.1 (v 2.1.300), oprzyrządowanie dołączone do .NET Core 2.1, zawiera następujące zmiany i ulepszenia:

### <a name="build-performance-improvements"></a>Tworzenie ulepszeń wydajności

Głównym celem .NET Core 2.1 jest poprawa wydajności w czasie kompilacji, szczególnie w przypadku kompilacji przyrostowych. Te ulepszenia wydajności dotyczą zarówno kompilacji `dotnet build` wiersza polecenia przy użyciu i do kompilacji w programie Visual Studio. Niektóre poszczególne obszary poprawy obejmują:

- W przypadku rozpoznawania zasobów pakietu rozpoznawanie tylko zasobów używanych przez kompilację, a nie wszystkie zasoby.

- Buforowanie odwołań do zestawu.

- Korzystanie z długotrwałych serwerów kompilacji SDK, które `dotnet build` są procesami, które obejmują poszczególne wywołania. Eliminują one konieczność JIT-kompilacji `dotnet build` dużych bloków kodu za każdym razem jest uruchamiany. Procesy serwera kompilacji można automatycznie zakończyć za pomocą następującego polecenia:

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Nowe polecenia wiersza polecenia

Wiele narzędzi, które były dostępne tylko na `DotnetCliToolReference` podstawie projektu przy użyciu są teraz dostępne jako część .NET Core SDK. Do tych narzędzi należą:

- `dotnet watch`udostępnia obserwatora systemu plików, który czeka na zmianę pliku przed wykonaniem wyznaczonego zestawu poleceń. Na przykład następujące polecenie automatycznie odbudowuje bieżący projekt i generuje pełne dane wyjściowe, gdy zmienia się plik:

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   Zwróć `--` uwagę na `--verbose` opcję poprzedzanącą tę opcję. To rozgranicza opcje przekazywane `dotnet watch` bezpośrednio do polecenia z argumentów, które są przekazywane do procesu podrzędne. `dotnet` Bez niego `--verbose` opcja ma zastosowanie `dotnet watch` do polecenia, a `dotnet build` nie polecenia.
  
   Aby uzyskać więcej informacji, zobacz [Opracowywanie aplikacji ASP.NET Core przy użyciu zegarka dotnet](/aspnet/core/tutorials/dotnet-watch).

- `dotnet dev-certs`generuje certyfikaty używane podczas opracowywania w ASP.NET podstawowych aplikacji i zarządza nimi.

- `dotnet user-secrets`zarządza kluczami tajnymi w tajnym magazynie użytkownika w ASP.NET aplikacji Core.

- `dotnet sql-cache`tworzy tabelę i indeksy w bazie danych programu Microsoft SQL Server, która ma być używana do buforowania rozproszonego.

- `dotnet ef`jest narzędziem do zarządzania <xref:Microsoft.EntityFrameworkCore.DbContext> bazami danych, obiektami i migracjami w podstawowych aplikacjach entity framework. Aby uzyskać więcej informacji, zobacz [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Narzędzia globalne

.NET Core 2.1 obsługuje *narzędzia globalne* — czyli niestandardowe narzędzia, które są dostępne globalnie z wiersza polecenia. Model rozszerzalności w poprzednich wersjach programu .NET Core udostępnił niestandardowe narzędzia `DotnetCliToolReference`na podstawie poprzecznych projektów tylko przy użyciu .

Aby zainstalować narzędzie globalne, należy użyć polecenia [instalowania narzędzia dotnet.](../tools/dotnet-tool-install.md) Przykład:

```dotnetcli
dotnet tool install -g dotnetsay
```

Po zainstalowaniu narzędzie można uruchomić z wiersza polecenia, określając nazwę narzędzia. Aby uzyskać więcej informacji, zobacz [omówienie .NET Core Global Tools](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Zarządzanie narzędziami `dotnet tool` za pomocą polecenia

W sdk .NET Core 2.1 wszystkie `dotnet tool` operacje narzędzi używają polecenia. Dostępne są następujące opcje:

- [`dotnet tool install`](../tools/dotnet-tool-install.md), aby zainstalować narzędzie.

- [`dotnet tool update`](../tools/dotnet-tool-update.md), aby odinstalować i ponownie zainstalować narzędzie, które skutecznie je aktualizuje.

- [`dotnet tool list`](../tools/dotnet-tool-list.md), aby wyświetlić listę aktualnie zainstalowanych narzędzi.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md), aby odinstalować aktualnie zainstalowane narzędzia.

## <a name="roll-forward"></a>Przewiń do przodu

Wszystkie aplikacje .NET Core, począwszy od .NET Core 2.0, są automatycznie przerzucane do najnowszej *wersji pomocniczej* zainstalowanej w systemie.

Począwszy od .NET Core 2.0, jeśli wersja programu .NET Core, w której została zbudowana aplikacja, nie jest obecna w czasie wykonywania, aplikacja jest automatycznie uruchamiana względem najnowszej zainstalowanej *wersji pomocniczej* programu .NET Core. Innymi słowy, jeśli aplikacja jest zbudowana z .NET Core 2.0, a .NET Core 2.0 nie jest obecny w systemie hosta, ale .NET Core 2.1 jest, aplikacja jest uruchamiana z .NET Core 2.1.

> [!IMPORTANT]
> To zachowanie roll-forward nie ma zastosowania do wersji zapoznawczych. Domyślnie nie ma zastosowania do głównych wersji, ale można to zmienić za pomocą poniższych ustawień.

To zachowanie można zmodyfikować, zmieniając ustawienie roll-forward na nie kandydata udostępnionej struktury. Dostępne ustawienia to:

- `0`- wyłącz zachowanie wersji pomocniczej. Dzięki temu ustawieniu aplikacja stworzona dla .NET Core 2.0.0 zostanie przewiona do pliku .NET Core 2.0.1, ale nie do .NET Core 2.2.0 lub .NET Core 3.0.0.
- `1`- włączyć zachowanie wersji pomocniczej roll-forward. Jest to wartość domyślna dla ustawienia. Dzięki temu ustawieniu aplikacja stworzona dla .NET Core 2.0.0 będzie przerzucać dalej do .NET Core 2.0.1 lub .NET Core 2.2.0, w zależności od tego, który z nich jest zainstalowany, ale nie będzie przerzucać dalej do .NET Core 3.0.0.
- `2`- włączyć zachowanie roll-forward wersji pomocniczej i głównej. Jeśli zestaw, nawet różne wersje główne są brane pod uwagę, więc aplikacja zbudowana dla .NET Core 2.0.0 będzie przewijać do przodu do .NET Core 3.0.0.

To ustawienie można zmodyfikować na trzy sposoby:

- Ustaw `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` zmienną środowiskową na żądaną wartość.

- Dodaj następujący wiersz z żądaną wartością do pliku *.runtimeconfig.json:*

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- W przypadku korzystania z [polecenia CLI .NET Core](../tools/index.md)dodaj następującą opcję `run`z żądaną wartością do polecenia .NET Core, takiego jak:

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

Patch version roll forward jest niezależna od tego ustawienia i odbywa się po zastosowaniu potencjalnego zastosowania rzutu do przodu wersji pomocniczej lub głównej.

## <a name="deployment"></a>Wdrożenie

### <a name="self-contained-application-servicing"></a>Samodzielna obsługa aplikacji

`dotnet publish`teraz publikuje niezależne aplikacje z wersją usługi runtime. Podczas publikowania niezależnej aplikacji z .NET Core 2.1 SDK (v 2.1.300), aplikacja zawiera najnowszą wersję usługi uruchomieniowej znany przez ten zestaw SDK. Po uaktualnieniu do najnowszego sdk, zostanie opublikowany z najnowszą wersją programu .NET Core. Dotyczy to .NET Core 1.0 w czasie i nowszych.

Niezależne publikowanie opiera się na wersjach czasu wykonywania na NuGet.org. Nie trzeba mieć serviced runtime na komputerze.

Przy użyciu .NET Core 2.0 SDK, niezależne aplikacje są publikowane w czasie wykonywania .NET Core 2.0.0, chyba że inna wersja jest określona za pośrednictwem `RuntimeFrameworkVersion` właściwości. Dzięki temu nowemu zachowaniu nie trzeba już ustawiać tej właściwości, aby wybrać wyższą wersję czasu wykonywania dla niezależnej aplikacji. Najprostszym podejściem w przyszłości jest zawsze publikowanie za pomocą .NET Core 2.1 SDK (v 2.1.300).

Aby uzyskać więcej informacji, zobacz Samodzielne wdrażanie [runtime roll forward](../deploying/runtime-patch-selection.md).
## <a name="windows-compatibility-pack"></a>Pakiet zgodności systemu Windows

Podczas przenoszenia istniejącego kodu z platformy .NET Framework do programu .NET Core można użyć [pakietu zgodności systemu Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Zapewnia dostęp do 20 000 więcej interfejsów API niż są dostępne w .NET Core. Te interfejsy API <xref:System.Drawing?displayProperty=nameWithType> obejmują typy <xref:System.Diagnostics.EventLog> w obszarze nazw, klasie, WMI, licznikach wydajności, usługach systemu Windows oraz typach i członkach rejestru systemu Windows.

## <a name="jit-compiler-improvements"></a>Ulepszenia kompilatora JIT

.NET Core zawiera nową technologię kompilatora JIT o nazwie *kompilacja warstwowa* (znana również jako *optymalizacja adaptacyjna),* która może znacznie zwiększyć wydajność. Kompilacja warstwowa jest ustawieniem opt-in.

Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonania kodu. W przypadku mało używanych ścieżek kodu kompilator może poświęcić więcej czasu na optymalizację kodu niż czas wykonywania spędza uruchomiony niezoptymalizowany kod. Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:

- **Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.

- **Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są często wykonywane. Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.

Możesz zdecydować się na kompilację warstwową na dwa sposoby.

- Aby użyć kompilacji warstwowej we wszystkich projektach korzystających z zestawu SDK .NET Core 2.1, ustaw następującą zmienną środowiskową:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Aby użyć kompilacji warstwowej dla połów dla pojęć projektu, dodaj `<TieredCompilation>` właściwość do `<PropertyGroup>` sekcji pliku projektu MSBuild, jak pokazano w poniższym przykładzie:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>Zmiany interfejsu API

### <a name="spant-and-memoryt"></a>`Span<T>` i `Memory<T>`

.NET Core 2.1 zawiera kilka nowych typów, które sprawiają, że praca z tablicami i innymi typami pamięci jest znacznie bardziej wydajna. Nowe typy obejmują:

- <xref:System.Span%601?displayProperty=nameWithType>i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType>i <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bez tych typów podczas przekazywania takich elementów jako część tablicy lub sekcji buforu pamięci, należy wykonać kopię niektórych części danych przed przekazaniem go do metody. Te typy zapewniają wirtualny widok tych danych, który eliminuje potrzebę dodatkowych operacji alokacji i kopiowania pamięci.

W poniższym <xref:System.Span%601> przykładzie <xref:System.Memory%601> użyto wystąpienia i wystąpienie, aby zapewnić widok wirtualny 10 elementów tablicy.

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a>Kompresja Brotli

.NET Core 2.1 dodaje obsługę kompresji i dekompresji Brotli. Brotli jest uniwersalnym algorytmem kompresji bezstratnej, który jest zdefiniowany w [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) i jest obsługiwany przez większość przeglądarek internetowych i głównych serwerów internetowych. Można użyć klasy opartej <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> na strumieniu lub wysokiej <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> wydajności <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> span oparte i klas. W poniższym przykładzie przedstawiono <xref:System.IO.Compression.BrotliStream> kompresji z klasą:

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

Zachowanie <xref:System.IO.Compression.BrotliStream> jest takie <xref:System.IO.Compression.DeflateStream> samo <xref:System.IO.Compression.GZipStream>jak i , co ułatwia konwertowanie <xref:System.IO.Compression.BrotliStream>kodu, który wywołuje te interfejsy API do .

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Nowe interfejsy API kryptografii i ulepszenia kryptografii

.NET Core 2.1 zawiera wiele ulepszeń interfejsów API kryptografii:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>jest dostępny w pakiecie System.Security.Cryptography.Pkcs. Implementacja jest taka <xref:System.Security.Cryptography.Pkcs.SignedCms> sama jak klasy w .NET Framework.

- Nowe przeciążenia <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> i metody akceptują identyfikator algorytmu mieszania, aby umożliwić wywołującym uzyskanie wartości odcisku palca certyfikatu przy użyciu algorytmów innych niż SHA-1.

- Nowe <xref:System.Span%601>interfejsy API kryptografii są dostępne do mieszania, HMAC, kryptograficznego generowania liczb losowych, asymetrycznego generowania podpisów, asymetrycznego przetwarzania podpisów i szyfrowania RSA.

- Wydajność <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> poprawiła się o około 15% <xref:System.Span%601>przy użyciu implementacji opartej na.

- Nowa <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> klasa zawiera dwie nowe metody:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>zajmuje stałą ilość czasu, aby powrócić do dwóch wejść o tej samej długości, co sprawia, że nadaje się do wykorzystania w weryfikacji kryptograficznej, aby uniknąć przyczyniania się do informacji o czasie kanału bocznego.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>jest procedurą oczyszczania pamięci, która nie może być zoptymalizowana.

- Metoda <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> statyczna wypełnia <xref:System.Span%601> wartość losową.

- Jest <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> teraz obsługiwany na Linuksie i macOS.

- Elliptic-Curve Diffie-Hellman (ECDH) jest <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> teraz dostępny w rodzinie klas. Powierzchnia jest taka sama jak w .NET Framework.

- Wystąpienie zwracane <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> przez można zaszyfrować lub odszyfrować za pomocą OAEP przy użyciu sha-2 digest, a także generować lub weryfikować podpisy przy użyciu RSA-PSS.

### <a name="sockets-improvements"></a>Ulepszenia gniazd

.NET Core zawiera nowy <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>typ i <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>przepisane , które stanowią podstawę interfejsów API sieci owego wyższego poziomu.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, na przykład, jest <xref:System.Net.Http.HttpClient> podstawą realizacji. W poprzednich wersjach programu .NET Core interfejsy API wyższego poziomu były oparte na implementacjach sieci natywnych.

Implementacja gniazd wprowadzona w .NET Core 2.1 ma wiele zalet:

- Znaczna poprawa wydajności w porównaniu z poprzednią implementacją.

- Eliminacja zależności platformy, co upraszcza wdrażanie i obsługę.

- Spójne zachowanie na wszystkich platformach .NET Core.

<xref:System.Net.Http.SocketsHttpHandler>jest domyślną implementacją w .NET Core 2.1. Można jednak skonfigurować aplikację do używania <xref:System.Net.Http.HttpClientHandler> starszej <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> klasy, wywołując metodę:

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

Można również użyć zmiennej środowiskowej, aby zrezygnować <xref:System.Net.Http.SocketsHttpHandler>z używania implementacji gniazd na podstawie . Aby to zrobić, `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ustaw `false` jeden lub 0.

W systemie Windows można również <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>użyć , który opiera się <xref:System.Net.Http.SocketsHttpHandler> na implementacji macierzystej lub <xref:System.Net.Http.HttpClient> klasy, przekazując wystąpienie klasy do konstruktora.

W systemach Linux i macOS można konfigurować <xref:System.Net.Http.HttpClient> tylko na podstawie procesu. W systemie Linux musisz wdrożyć [libcurl,](https://curl.haxx.se/libcurl/) jeśli <xref:System.Net.Http.HttpClient> chcesz użyć starej implementacji. (Jest on zainstalowany z .NET Core 2.0.)

### <a name="breaking-changes"></a>Zmiany powodujące niezgodność

Aby uzyskać informacje o zmianach dotyczących łamania, zobacz [Łamanie zmian migracji z wersji 2.0 do 2.1](../compatibility/2.0-2.1.md).

## <a name="see-also"></a>Zobacz też

- [Co nowego w programie .NET Core](index.md)
- [Nowe funkcje ef core 2.1](/ef/core/what-is-new/ef-core-2.1)
- [Co nowego w ASP.NET Core 2.1](/aspnet/core/aspnetcore-2.1)
