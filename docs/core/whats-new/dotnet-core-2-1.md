---
title: Co nowego w programie .NET Core 2.1
description: Dowiedz się więcej o nowych funkcjach znalezionych w .NET Core 2.1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 78d9a6490c0479d9c21e01d0bcba41294d674a5c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644381"
---
# <a name="whats-new-in-net-core-21"></a>Co nowego w programie .NET Core 2.1

Program .NET Core 2.1 zawiera ulepszenia i nowe funkcje w następujących obszarach:

- [Narzędzia](#tooling)
- [Przewiń do przodu](#roll-forward)
- [Wdrożenie](#deployment)
- [Pakiet zgodności systemu Windows](#windows-compatibility-pack)
- [Ulepszenia kompilacji JIT](#jit-compiler-improvements)
- [Zmiany api](#api-changes)

## <a name="tooling"></a>Narzędzia

Zestaw .NET Core 2.1 SDK (v 2.1.300), oprzyrządowanie dołączone do programu .NET Core 2.1, zawiera następujące zmiany i ulepszenia:

### <a name="build-performance-improvements"></a>Twórz ulepszenia wydajności

Głównym celem platformy .NET Core 2.1 jest poprawa wydajności w czasie kompilacji, szczególnie w przypadku kompilacji przyrostowych. Te ulepszenia wydajności dotyczą zarówno kompilacji `dotnet build` wiersza polecenia przy użyciu i kompilacji w programie Visual Studio. Niektóre poszczególne obszary poprawy obejmują:

- W przypadku rozpoznawania zasobów pakietu rozpoznawanie tylko zasobów używanych przez kompilację, a nie wszystkie zasoby.

- Buforowanie odniesień do złożenia.

- Korzystanie z długotrwałych serwerów kompilacji SDK, `dotnet build` które są procesami, które obejmują poszczególne wywołania. Eliminują one konieczność JIT-kompilować duże `dotnet build` bloki kodu za każdym razem jest uruchamiany. Procesy serwera kompilacji można automatycznie zakończyć za pomocą następującego polecenia:

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Nowe polecenia interfejsu wiersza polecenia

Wiele narzędzi, które były dostępne tylko na `DotnetCliToolReference` podstawie projektu przy użyciu są teraz dostępne jako część .NET Core SDK. Do tych narzędzi należą:

- `dotnet watch`udostępnia obserwatora systemu plików, który czeka na zmianę pliku przed wykonaniem wyznaczonego zestawu poleceń. Na przykład następujące polecenie automatycznie odbudowuje bieżący projekt i generuje pełne dane wyjściowe za każdym razem, gdy zmienia się w nim plik:

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   Zwróć `--` uwagę na opcję `--verbose` poprzedzającą tę opcję. Rozgranicza opcje przekazywane bezpośrednio `dotnet watch` do polecenia z argumentów, `dotnet` które są przekazywane do procesu podrzędnego. Bez niego `--verbose` opcja ma zastosowanie `dotnet watch` do polecenia, a nie do `dotnet build` polecenia.
  
   Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji ASP.NET Core przy użyciu zegarka dotnet](/aspnet/core/tutorials/dotnet-watch).

- `dotnet dev-certs`generuje certyfikaty używane podczas tworzenia w aplikacjach ASP.NET Core i zarządza nimi.

- `dotnet user-secrets`zarządza wpisami tajnymi w tajnym magazynie użytkownika w aplikacjach ASP.NET Core.

- `dotnet sql-cache`tworzy tabelę i indeksy w bazie danych programu Microsoft SQL Server, które mają być używane do buforowania rozproszonego.

- `dotnet ef`jest narzędziem do zarządzania bazami danych, <xref:Microsoft.EntityFrameworkCore.DbContext> obiektami i migracjami w aplikacjach Entity Framework Core. Aby uzyskać więcej informacji, zobacz [Narzędzia wiersza polecenia EF Core .NET](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Narzędzia globalne

Program .NET Core 2.1 obsługuje *narzędzia globalne* — czyli narzędzia niestandardowe, które są dostępne globalnie z wiersza polecenia. Model rozszerzalności w poprzednich wersjach programu .NET Core udostępnił narzędzia niestandardowe dostępne dla projektu tylko za pomocą programu `DotnetCliToolReference`.

Aby zainstalować narzędzie globalne, należy użyć polecenia [instalacji narzędzia dotnet.](../tools/dotnet-tool-install.md) Przykład:

```dotnetcli
dotnet tool install -g dotnetsay
```

Po zainstalowaniu narzędzie można uruchomić z wiersza polecenia, określając nazwę narzędzia. Aby uzyskać więcej informacji, zobacz [omówienie .NET Core Global Tools](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Zarządzanie narzędziami `dotnet tool` za pomocą polecenia

W pliku .NET Core 2.1 SDK `dotnet tool` wszystkie operacje narzędzi używają tego polecenia. Dostępne są następujące opcje:

- [`dotnet tool install`](../tools/dotnet-tool-install.md), aby zainstalować narzędzie.

- [`dotnet tool update`](../tools/dotnet-tool-update.md), aby odinstalować i ponownie zainstalować narzędzie, które skutecznie je aktualizuje.

- [`dotnet tool list`](../tools/dotnet-tool-list.md), aby wyświetlić listę aktualnie zainstalowanych narzędzi.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md), aby odinstalować aktualnie zainstalowane narzędzia.

## <a name="roll-forward"></a>Przewiń do przodu

Wszystkie aplikacje .NET Core, począwszy od platformy .NET Core 2.0, automatycznie przewijają się do *najnowszej wersji pomocniczej zainstalowanej* w systemie.

Począwszy od .NET Core 2.0, jeśli wersja .NET Core, z którą została zbudowana aplikacja, nie jest obecna w czasie wykonywania, aplikacja automatycznie uruchamia się z *najnowszą zainstalowaną wersją pomocniczą* programu .NET Core. Innymi słowy, jeśli aplikacja jest zbudowana z .NET Core 2.0, a .NET Core 2.0 nie jest obecny w systemie hosta, ale .NET Core 2.1 jest, aplikacja działa z .NET Core 2.1.

> [!IMPORTANT]
> To zachowanie do przodu nie ma zastosowania do wersji zapoznawczych. Domyślnie nie dotyczy również głównych wersji, ale można to zmienić za pomocą poniższych ustawień.

Można zmodyfikować to zachowanie, zmieniając ustawienie roll-forward na żadnej udostępnionej struktury kandydata. Dostępne ustawienia to:

- `0`- wyłączyć zachowanie przewijania do przodu wersji pomocniczej. Przy tym ustawieniu aplikacja zbudowana dla platformy .NET Core 2.0.0 zostanie przesuń do przodu do .NET Core 2.0.1, ale nie do .NET Core 2.2.0 lub .NET Core 3.0.0.
- `1`- włączyć zachowanie przewijania wersji pomocniczej do przodu. Jest to wartość domyślna dla tego ustawienia. Przy tym ustawieniu aplikacja zbudowana dla platformy .NET Core 2.0.0 zostanie przesuń do przodu do .NET Core 2.0.1 lub .NET Core 2.2.0, w zależności od tego, który z nich jest zainstalowany, ale nie będzie przekierowywać do przodu do .NET Core 3.0.0.
- `2`- włączyć drobne i główne zachowanie roll-forward wersji. Jeśli zestaw, nawet różne wersje główne są brane pod uwagę, więc aplikacja zbudowana dla .NET Core 2.0.0 zostanie przewijana do przodu do .NET Core 3.0.0.

To ustawienie można zmodyfikować na dowolny z trzech sposobów:

- Ustaw `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` zmienną środowiskową na żądaną wartość.

- Dodaj następujący wiersz o żądanej wartości do pliku *.runtimeconfig.json:*

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- W przypadku korzystania z interfejsu [wiersza polecenia .NET Core](../tools/index.md)należy dodać `run`następującą opcję z żądaną wartością do polecenia .NET Core, taką jak:

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

Roll do przodu wersji poprawki jest niezależna od tego ustawienia i odbywa się po zastosowaniu dowolnego potencjalnego rzutu wersji pomocniczej lub głównej do przodu.

## <a name="deployment"></a>Wdrożenie

### <a name="self-contained-application-servicing"></a>Samodzielne serwisowanie aplikacji

`dotnet publish`teraz publikuje samodzielne aplikacje z wersją serviced runtime. Podczas publikowania aplikacji niezależnej z .NET Core 2.1 SDK (v 2.1.300), aplikacja zawiera najnowszą wersję środowiska uruchomieniowego usługi znane przez ten zestaw SDK. Po uaktualnieniu do najnowszego sdk, można opublikować z najnowszą wersją środowiska uruchomieniowego .NET Core. Dotyczy to środowiska uruchomień .NET Core 1.0 i nowszych.

Samodzielne publikowanie opiera się na wersjach środowiska wykonawczego na NuGet.org. Nie trzeba mieć serviced runtime na komputerze.

Za pomocą .NET Core 2.0 SDK, samodzielne aplikacje są publikowane w czasie wykonywania .NET Core 2.0.0, chyba że inna wersja jest określona za pośrednictwem `RuntimeFrameworkVersion` właściwości. Dzięki temu nowemu zachowaniu nie trzeba już ustawiać tej właściwości, aby wybrać wyższą wersję środowiska uruchomieniowego dla aplikacji niezależnej. Najprostszym podejściem w przyszłości jest zawsze publikować za pomocą .NET Core 2.1 SDK (v 2.1.300).

Aby uzyskać więcej informacji, zobacz [Samodzielne wdrożenie uruchomieniowe rolki do przodu](../deploying/runtime-patch-selection.md).
## <a name="windows-compatibility-pack"></a>Pakiet zgodności systemu Windows

Po przekadaniu istniejącego kodu z programu .NET Framework do programu .NET Core można użyć [pakietu zgodności systemu Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Zapewnia dostęp do 20 000 więcej interfejsów API niż są dostępne w programie .NET Core. Te interfejsy API obejmują <xref:System.Drawing?displayProperty=nameWithType> typy <xref:System.Diagnostics.EventLog> w obszarze nazw, klasy, WMI, liczniki wydajności, usługi systemu Windows i typy rejestru systemu Windows i członków.

## <a name="jit-compiler-improvements"></a>Ulepszenia kompilatora JIT

.NET Core zawiera nową technologię kompilatora JIT o nazwie *kompilacji warstwowej* (znany również jako *optymalizacji adaptacyjnej),* które mogą znacznie zwiększyć wydajność. Kompilacja warstwowa jest ustawieniem opt-in.

Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonywania kodu. W przypadku mało używanych ścieżek kodu kompilator może jednak poświęcić więcej czasu na optymalizację kodu niż środowisko wykonawcze spędza uruchamianie nieoptymalizowanego kodu. Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:

- **Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.

- **Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są wykonywane często. Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.

Możesz zdecydować się na kompilację warstwową na jeden z dwóch sposobów.

- Aby użyć kompilacji warstwowej we wszystkich projektach korzystających z zestawu .NET Core 2.1 SDK, należy ustawić następującą zmienną środowiskową:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Aby użyć kompilacji warstwowej na podstawie projektu, `<TieredCompilation>` dodaj `<PropertyGroup>` właściwość do sekcji pliku projektu MSBuild, zgodnie z poniższym przykładem:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>Zmiany api

### <a name="spant-and-memoryt"></a>`Span<T>` i `Memory<T>`

.NET Core 2.1 zawiera kilka nowych typów, które sprawiają, że praca z macierzami i innymi typami pamięci jest znacznie bardziej wydajna. Nowe typy obejmują:

- <xref:System.Span%601?displayProperty=nameWithType>i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType>i <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bez tych typów podczas przekazywania takich elementów, jak część tablicy lub sekcji buforu pamięci, należy wykonać kopię niektórych części danych przed przekazaniem go do metody. Te typy zapewniają wirtualny widok tych danych, który eliminuje potrzebę dodatkowej alokacji pamięci i operacji kopiowania.

W poniższym <xref:System.Span%601> przykładzie <xref:System.Memory%601> użyto i wystąpienie, aby zapewnić widok wirtualny 10 elementów tablicy.

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a>Kompresja Brotli

.NET Core 2.1 dodaje obsługę kompresji i dekompresji Brotli. Brotli to uniwersalny algorytm kompresji bezstratnych, który jest zdefiniowany w [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) i jest obsługiwany przez większość przeglądarek internetowych i głównych serwerów internetowych. Można użyć klasy opartej na <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> strumieniu lub <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> klasy <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> oparte na rozpiętości o wysokiej wydajności. Poniższy przykład ilustruje <xref:System.IO.Compression.BrotliStream> kompresję z klasą:

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

Zachowanie <xref:System.IO.Compression.BrotliStream> jest takie <xref:System.IO.Compression.DeflateStream> samo <xref:System.IO.Compression.GZipStream>jak i , co ułatwia konwersję kodu, który wywołuje te interfejsy API do <xref:System.IO.Compression.BrotliStream>.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Nowe interfejsy API kryptografii i ulepszenia kryptografii

Program .NET Core 2.1 zawiera liczne ulepszenia interfejsów API kryptografii:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>jest dostępny w pakiecie System.Security.Cryptography.Pkcs. Implementacja jest taka <xref:System.Security.Cryptography.Pkcs.SignedCms> sama jak klasa w .NET Framework.

- Nowe przeciążenia <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody akceptują identyfikator algorytmu mieszania, aby umożliwić wywołującym uzyskanie wartości odcisku palca certyfikatu przy użyciu algorytmów innych niż SHA-1.

- Nowe <xref:System.Span%601>interfejsy API kryptografii opartej na kryptografii są dostępne do mieszania, HMAC, generowania liczb losowych kryptograficznych, generowania asymetrycznego podpisu, asymetrycznego przetwarzania podpisu i szyfrowania RSA.

- Wydajność poprawiła <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> się o około 15% przy użyciu implementacji opartej <xref:System.Span%601>na

- Nowa <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> klasa zawiera dwie nowe metody:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>zajmuje ustaloną ilość czasu, aby powrócić do dwóch wejść o tej samej długości, co sprawia, że nadaje się do wykorzystania w weryfikacji kryptograficznej, aby uniknąć przyczyniania się do czasu informacji kanału bocznego.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>jest procedurą czyszczenia pamięci, których nie można zoptymalizować.

- Metoda statyczna <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> wypełnia <xref:System.Span%601> wartości losowe.

- Jest <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> teraz obsługiwany w systemach Linux i macOS.

- Elliptic-Curve Diffie-Hellman (ECDH) jest <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> teraz dostępny w rodzinie klas. Powierzchnia jest taka sama jak w .NET Framework.

- Wystąpienie zwracane przez <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> można szyfrować lub odszyfrowywać za pomocą OAEP przy użyciu skrótu SHA-2, a także generować lub weryfikować podpisy przy użyciu RSA-PSS.

### <a name="sockets-improvements"></a>Ulepszenia gniazd

Program .NET Core zawiera <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>nowy typ <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>i przepisany plik, który stanowi podstawę interfejsów API sieciowego wyższego poziomu.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, na przykład, jest <xref:System.Net.Http.HttpClient> podstawą realizacji. W poprzednich wersjach programu .NET Core interfejsy API wyższego poziomu były oparte na implementacjach sieci natywnych.

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

Można również użyć zmiennej środowiskowej, aby zrezygnować z <xref:System.Net.Http.SocketsHttpHandler>używania implementacji gniazd opartych na . Aby to zrobić, `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ustaw `false` na jedną lub 0.

W systemie Windows można również <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>wybrać użycie , który opiera <xref:System.Net.Http.SocketsHttpHandler> się na implementacji macierzystej <xref:System.Net.Http.HttpClient> lub klasy, przekazując wystąpienie klasy do konstruktora.

W systemach Linux i macOS <xref:System.Net.Http.HttpClient> można konfigurować tylko na podstawie procesu. W systemie Linux należy wdrożyć [libcurl,](https://curl.haxx.se/libcurl/) jeśli <xref:System.Net.Http.HttpClient> chcesz użyć starej implementacji. (Jest zainstalowany z .NET Core 2.0.)

### <a name="breaking-changes"></a>Fundamentalne zmiany

Aby uzyskać informacje na temat zmiany podziału, zobacz [Przerywanie zmian migracji z wersji 2.0 do 2.1](../compatibility/2.0-2.1.md).

## <a name="see-also"></a>Zobacz też

- [Co nowego w programie .NET Core 3.1](dotnet-core-3-1.md)
- [Nowe funkcje w EF Core 2.1](/ef/core/what-is-new/ef-core-2.1)
- [Co nowego w ASP.NET Core 2.1](/aspnet/core/aspnetcore-2.1)
