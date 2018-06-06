---
title: Co to jest nowa w programie .NET Core 2.1
description: Więcej informacji na temat nowych funkcji .NET Core 2.1.
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2018
ms.openlocfilehash: a7e0ae3c65a18376a7648198a43f1272a2bddafd
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696458"
---
# <a name="whats-new-in-net-core-21"></a>Co to jest nowa w programie .NET Core 2.1

.NET core 2.1 zawiera nowych funkcji i rozszerzeń w następujących obszarach:

- [Narzędzia](#tooling)
- [Przenoszenia do przodu](#roll-forward)
- [Wdrażanie](#deployment)
- [Pakiet zgodności systemu Windows](#windows-compatibility-pack)
- [Ulepszenia kompilatora JIT](#jit-compiler-improvements)
- [Zmiany interfejsu API](#api-changes)

## <a name="tooling"></a>Narzędzia

Oprogramowanie .NET Core 2.1.300 SDK i narzędzia dołączonego .NET Core 2.1, obejmuje następujące zmiany i udoskonalenia:

### <a name="build-performance-improvements"></a>Ulepszenia wydajności kompilacji

Głównym celem .NET Core 2.1 jest poprawy wydajności w czasie kompilacji, szczególnie dla kompilacji przyrostowej. Te ulepszenia wydajności dotyczą zarówno kompilacji z wiersza polecenia przy użyciu `dotnet build` i kompilacji w programie Visual Studio. Niektóre poszczególnych obszarach poprawy obejmują:

- Rozpoznanie zasobów pakietu rozpoznawanie tylko zasoby używane przez kompilację, a nie wszystkie zasoby.

- Buforowanie odwołania do zestawów.

- Użyj zestawu SDK długotrwałe kompilacji z serwerów, które są procesów obejmujących przez poszczególne `dotnet build` wywołań. One wyeliminować potrzebę kompilacji JIT duże bloki kodu zawsze `dotnet build` jest uruchamiany. Tworzenie serwera, które mogą być automatycznie zakończone procesy przy użyciu następującego polecenia:

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Nowe polecenia interfejsu wiersza polecenia

Liczba narzędzia, które były dostępne tylko na projekt na podstawie przy użyciu [ `DotnetCliToolReference` ](../tools/extensibility.md) są teraz dostępne jako część zestawu SDK .NET Core. Narzędzia te obejmują:

- `dotnet watch` Zawiera obserwatora systemu plików, który oczekuje na plik, aby zmienić przed wykonaniem wyznaczonych zestaw poleceń. Na przykład następujące polecenie automatycznie odtwarza bieżącego projektu i generuje pełne dane wyjściowe przy każdej zmianie plik w tym:

   ```console
   dotnet watch -- --verbose build
   ```

   Aby uzyskać więcej informacji, zobacz [opracowanie platformy ASP.NET Core aplikacji przy użyciu czujki dotnet](/aspnet/core/tutorials/dotnet-watch)

- `dotnet dev-certs` generuje i zarządza certyfikaty używane podczas tworzenia aplikacji platformy ASP.NET Core.

- `dotnet user-secrets` zarządza kluczy tajnych w magazynie tajny użytkownika w aplikacjach ASP.NET Core.

- `dotnet sql-cache` tworzy tabelę i indeksy w bazie danych programu Microsoft SQL Server używanego do buforowania rozproszonego.

- `dotnet ef` to narzędzie do zarządzania bazami danych, <xref:Microsoft.EntityFrameworkCore.DbContext> obiektów i migracje w aplikacjach Entity Framework Core. Aby uzyskać więcej informacji, zobacz [narzędzia wiersza polecenia platformy .NET Core EF](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Narzędzia globalne

.NET core 2.1 obsługuje *globalne narzędzia* — to znaczy niestandardowe narzędzia dostępne globalnie z wiersza polecenia. Modelu rozszerzalności w poprzednich wersjach programu .NET Core udostępnione niestandardowego narzędzia na podstawie projektu na tylko przy użyciu [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).

Aby zainstalować narzędzie globalne, należy użyć [instalacji narzędzi dotnet](..\tools\dotnet-tool-install.md) polecenia. Na przykład:

```console
dotnet tool install -g dotnetsay
```

Po zakończeniu instalacji można uruchomić narzędzie z wiersza polecenia, określając nazwę narzędzia. Aby uzyskać więcej informacji, zobacz [Omówienie narzędzia globalne .NET Core](../tools/global-tools.md).

### <a name="single-source-tool-management-with-the-dotnet-tool-command"></a>Zarządzanie za pomocą narzędzia pojedynczego źródła `dotnet tool` polecenia

W .NET Core 2.1, użyj wszystkich operacji narzędzia `dotnet tool` polecenia. Dostępne są następujące opcje:

- `dotnet tool install` Aby zainstalować narzędzie.

- `dotnet tool update` Aby odinstalować i ponownie zainstalować narzędzie, które skutecznie aktualizacji.

- `dotnet tool list` Aby wyświetlić listę aktualnie zainstalowane narzędzia.

## <a name="roll-forward"></a>Przenoszenia do przodu

Wszystkie aplikacje .NET Core automatycznemu .NET 2.0 Core przekazywane dalej do najnowszej wersji *wersja pomocnicza* zainstalowanego w systemie. Oznacza to, że jeśli aplikacja została skompilowana przy wersja platformy .NET Core nie jest obecny, aplikacja jest uruchamiana dla najnowszej zainstalowanej wersji pomocniczej. Innymi słowy Jeśli aplikacja jest wbudowana .NET Core 2.0 i .NET Core 2.0 sam nie jest dostępny w systemie hosta, ale jest .NET Core 2.1, aplikacja zostanie uruchomiona przy użyciu zestawu .NET Core 2.1.

> [!IMPORTANT]
> To zachowanie przewijaniem do nie ma zastosowania do podglądu wersjach. Nie ma zastosowania główne wersje. Na przykład aplikacji .NET Core 1.0 nie są przekazywane dalej do .NET Core w wersji 2.0 lub .NET Core 2.1.

Można również wyłączyć zbiorczego wersja pomocnicza w jednym z trzech sposobów:

- Ustaw `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` równa 0, zmienna środowiskowa

- Dodaj następujący wiersz do pliku runtimeconfig.json:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- Korzystając z [narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md), obejmują takie jak następująca opcja za pomocą polecenia .NET Core `run`:

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a>wdrażania

### <a name="self-contained-application-servicing"></a>Obsługa aplikację autonomiczną

`dotnet publish` teraz publikuje niezależne aplikacji za pomocą wersji środowiska uruchomieniowego obsługiwane. Gdy opublikujesz aplikację autonomiczną przy użyciu zestawu SDK programu .NET Core 2.1, aplikacja zawiera najnowszą wersję środowiska uruchomieniowego obsługiwanych znane przez ten zestaw SDK. Podczas uaktualniania do najnowszej wersji zestawu SDK, będzie publikować przy użyciu najnowszej wersji środowiska uruchomieniowego .NET Core. Dotyczy to dla środowisk uruchomieniowych .NET Core 1.0 i nowszych.

Publikowanie niezależne zależy od wersji środowiska uruchomieniowego na NuGet.org. Nie trzeba mieć serwisowanego środowiska uruchomieniowego na tym komputerze.

Przy użyciu zestawu .NET Core 2.0 SDK, niezależne aplikacje są publikowane ze środowiskiem uruchomieniowym platformy .NET Core 2.0.0, chyba że określono inną wersję za pomocą `RuntimeFrameworkVersion` właściwości. Z to nowe zachowanie już nie musisz ustawić tę właściwość, aby wybrać wyższą wersję środowiska uruchomieniowego dla swojej aplikacji. Najłatwiejszy idąc dalej jest zawsze publikowanie za pomocą .NET Core 2.1 SDK.

## <a name="windows-compatibility-pack"></a>Pakiet zgodności systemu Windows

Jeśli port istniejącego kodu z programu .NET Framework do platformy .NET Core, możesz użyć [pakiet zgodności systemu Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Zapewnia dostęp do 20 000 API więcej niż jest dostępne w .NET Core. Te interfejsy API obejmują typy w <xref:System.Drawing?displayProperty="nameWithType"> przestrzeni nazw, <xref:System.Diagnostics.EventLog> klasy, usługi WMI, liczniki wydajności, usług systemu Windows i typy rejestru systemu Windows i elementów członkowskich.

## <a name="jit-compiler-improvements"></a>Ulepszenia kompilatora JIT

Oprogramowanie .NET core zawiera nową technologią kompilatora JIT o nazwie *kompilacji do warstwy* (znanej także jako *adaptacyjną optymalizacji*) która może znacznie poprawić wydajność.

Co ważne zadania wykonywane przez kompilator JIT optymalizuje wykonanie kodu. Jednak w przypadku ścieżek kodu rzadko używanych kompilator może poświęcić więcej czasu na Optymalizacja kodu niż środowiska uruchomieniowego spędza uruchamiania zoptymalizowanego kodu. Kompilacja warstwowych wprowadza dwóch etapach w kompilacji JIT:

- A **najpierw warstwy**, które generuje kod tak szybko jak to możliwe.

- A **Druga warstwa**, który generuje zoptymalizowanego kodu dla tych metod, które są często wykonywane. Druga warstwa kompilacji jest wykonywane równolegle na potrzeby zwiększenia wydajności.

Możesz przetestować warstwowych kompilacji z aplikacji .NET Core 2.1, ustawiając zmienną środowiskową następujące:

```console
COMPlus_TieredCompilation="1"
```

## <a name="api-changes"></a>Zmiany interfejsu API

### <a name="spant-and-memoryt"></a>`Span<T>` I `Memory<T>`

.NET core 2.1 zawiera niektóre nowe typy, które sprawiają, że praca z tablicami i innych rodzajów wydajniejsza pamięci. Nowe typy:

- <xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> i <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bez tych typów przy przekazywaniu tych elementów jako część tablicy lub sekcji bufora pamięci należy utworzyć kopię część danych przed przekazaniem go do metody. Te typy zapewniają wirtualny widok tych danych, która eliminuje potrzebę alokacji dodatkowej pamięci i operacje kopiowania.

W poniższym przykładzie użyto <xref:System.Span%601> wystąpienia w celu zapewnienia przeglądu wirtualny 10 elementów tablicy.

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a>Kompresja Brotli

.NET core 2.1 dodaje obsługę Brotli kompresji i dekompresji. Brotli to algorytm kompresji bezstratny ogólnego przeznaczenia, który jest zdefiniowany w [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) i są obsługiwane w większości przeglądarek sieci web i serwerów głównych sieci web. Można użyć podstawie strumienia <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> klasy lub wysokiej wydajności na podstawie zakresu <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> i <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> klasy. Poniższy przykład przedstawia kompresji z <xref:System.IO.Compression.BrotliStream> klasy:

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<xref:System.IO.Compression.BrotliStream> Zachowanie jest takie samo, jak <xref:System.IO.Compression.DeflateStream> i <xref:System.IO.Compression.GZipStream>, która ułatwia przekonwertować kod, który wywołuje te interfejsy API do <xref:System.IO.Compression.BrotliStream>.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Kryptografia nowych interfejsów API i ulepszenia kryptografii

.NET core 2.1 zawiera wiele ulepszeń usługi cryptography API:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> jest niedostępny w pakiecie System.Security.Cryptography.Pkcs. Implementacja jest taka sama jak <xref:System.Security.Cryptography.Pkcs.SignedCms> klasa w programie .NET Framework.

- Nowe przeciążeń <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody akceptuje identyfikator algorytmu wyznaczania wartości skrótu, aby umożliwić wywołującym można pobrać wartości odcisku palca certyfikatu przy użyciu algorytmy innych niż SHA-1.

- Nowe <xref:System.Span%601>— oparte na kryptografii interfejsy API są dostępne do tworzenia skrótu HMAC, kryptograficzne Generowanie liczby losowej podpisu asymetrycznego generowania, przetwarzania podpisu asymetrycznego i szyfrowania RSA.

- Wydajność <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> ulepszono o około 15% przy użyciu <xref:System.Span%601>— na podstawie implementacji.

- Nowe <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> klasa zawiera dwa nowe metody:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> Trwa stałej ilości czasu zwracanego przez dowolnego dwóch parametrów wejściowych taką samą długość, dzięki czemu nadaje się do użytku w kryptograficznych weryfikacji, aby uniknąć Współtworzenie chronometrażu informacji kanału po stronie.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> to nie może zostać zoptymalizowana procedura czyszczenia pamięci.

- Statycznych <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> wypełnienia metody <xref:System.Span%601> losowych wartości.

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Jest teraz obsługiwana w systemie Linux i maxOS.

- Diffie-Hellman krzywej eliptycznej (ECDH) jest teraz dostępna w <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> klasy rodziny. Powierzchnia jest taka sama, jak w programie .NET Framework.

- Zwrócone przez wystąpienie <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> można zaszyfrować lub odszyfrować z OAEP przy użyciu skrótu SHA-2, oraz generowanie lub sprawdzają poprawność podpisów przy użyciu RSA-PSS.

### <a name="sockets-improvements"></a>Ulepszenia gniazda

Oprogramowanie .NET core zawiera nowy typ, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>i ponownie zapisane <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, które stanowią podstawę sieci wyższego poziomu interfejsów API.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, na przykład jest podstawą <xref:System.Net.Http.HttpClient> implementacji. W poprzednich wersjach programu .NET Core API wyższego poziomu były oparte na natywnych implementacji sieci.

Implementacja sockets wprowadzone w programie .NET Core 2.1 zawiera następujące korzyści:

- Poprawa wydajności znaczących w porównaniu z poprzedniej implementacji.

- Eliminacja zależności platformy, które upraszcza wdrażania i obsługi.

- Zachowanie spójności na wszystkich platformach .NET Core.

Na podstawie Sockets <xref:System.Net.Http.SocketsHttpHandler> jest domyślna implementacja .NET Core 2.1. Jednak należy skonfigurować aplikację do używania starszej <xref:System.Net.Http.HttpClientHandler> klasy przez wywołanie metody <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> metody:

```csharp
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", false);
```

Można również użyć środowiska zmiennej, aby zrezygnować z używania gniazda implementacje na podstawie <xref:System.Net.Http.SocketsHttpHandler>. Aby to zrobić, ustaw `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` albo `false` lub równa 0.

W systemie Windows, można używać <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, która zależy od implementacji native lub <xref:System.Net.Http.SocketsHttpHandler> klasy przez przekazanie wystąpienia klasy do <xref:System.Net.Http.HttpClient> konstruktora.

W systemie Linux i macOS, można skonfigurować tylko <xref:System.Net.Http.HttpClient> na podstawie każdego procesu. W systemie Linux należy wdrożyć [libcurl](https://curl.haxx.se/libcurl/) Jeśli chcesz używać starego <xref:System.Net.Http.HttpClient> implementacji. (Jest instalowana z programem .NET Core 2.0.)

## <a name="see-also"></a>Zobacz także

[Co nowego w programie .NET Core](index.md)  
[Nowe funkcje w programie EF Core 2.1](/ef/core/what-is-new/ef-core-2.1)  
[What's new in ASP.NET Core 2.1](/aspnet/core/aspnetcore-2.1)
