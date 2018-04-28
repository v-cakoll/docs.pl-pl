---
title: Co to jest nowa w programie .NET Core 2.0
description: Więcej informacji na temat nowych funkcji .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: f99b053f69c4e06606cee5c78e3da7749c427e6c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="whats-new-in-net-core"></a>Co to jest nowa w programie .NET Core

.NET core 2.0 zawiera nowych funkcji i rozszerzeń w następujących obszarach:

- [Narzędzia](#tooling)
- [Obsługa języków](#language-support)
- [Ulepszenia platformy](#platform-improvements)
- [Zmiany interfejsu API](#api-changes-and-library-support)
- [Integracja z programem Visual Studio](#visual-studio-integration)
- [Ulepszenia dokumentacji](#documentation-improvements)

## <a name="tooling"></a>Narzędzia

### <a name="dotnet-restore-runs-implicitly"></a>Przywracanie DotNet uruchamia się domyślnie

W poprzednich wersjach programu .NET Core, trzeba było uruchomić [przywracania dotnet](../tools/dotnet-restore.md) polecenie, aby pobrać zależności natychmiast, po utworzeniu nowego projektu z [dotnet nowe](../tools/dotnet-new.md) polecenia, a także zawsze, gdy zostanie dodano nową zależność do projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Można także wyłączyć automatyczne wywoływanie `dotnet restore` przez przekazanie `--no-restore` przełączyć się do `new`, `run`, `build`, `publish`, `pack`, i `test` poleceń. 

### <a name="retargeting-to-net-core-20"></a>Przekierowania do platformy .NET Core 2.0

Po zainstalowaniu programu .NET Core 2.0 SDK projekty który docelowe .NET Core 1.x cel może zostać zmieniony na .NET Core 2.0.

Aby przekierować .NET Core 2.0, należy edytować plik projektu, zmieniając wartość `<TargetFramework>` elementu (lub `<TargetFrameworks>` elementu, jeśli masz więcej niż jeden element docelowy w pliku projektu) z 1.x 2.0:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Można również przekierować .NET standardowych bibliotek .NET 2.0 standardowe taki sam sposób:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Aby uzyskać więcej informacji na temat migracji projektu do .NET Core 2.0, zobacz [migracji z platformy ASP.NET Core 1.x do składnika ASP.NET 2.0 Core](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Obsługa języków

Oprócz obsługi języka C# i F #, .NET Core 2.0 obsługuje również Visual Basic.

### <a name="visual-basic"></a>Visual Basic

W wersji 2.0 .NET Core obsługuje teraz 2017 Visual Basic. Visual Basic umożliwia tworzenie następujących projektów:

- Aplikacje konsoli platformy .NET core
- Biblioteki klas .NET core
- Biblioteki klas .NET standard
- Projektów testów jednostkowych dla .NET core
- Projekty testowe xUnit .NET core

Na przykład do utworzenia aplikacji programu Visual Basic "Hello World", wykonaj następujące kroki w wierszu polecenia:

1. Otwórz okno konsoli, Utwórz katalog projektu i stał się bieżącego katalogu.

1. Wprowadź polecenie `dotnet new console -lang vb`.

   Polecenie tworzy plik projektu o `.vbproj` pliku rozszerzenie, wraz z pliku kodu źródłowego języka Visual Basic o nazwie *Program.vb*. Ten plik zawiera kod źródłowy, aby zapisać ciąg "Hello World!" w oknie konsoli.

1.  Wprowadź polecenie `dotnet run`. [Narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) automatycznie Kompiluj i wykonywanie aplikacji, która wyświetla komunikat "Hello World!" w oknie konsoli.

### <a name="support-for-c-71"></a>Obsługa języka C# 7.1

.NET core 2.0 obsługuje 7.1 C#, który dodaje szereg nowych funkcji, w tym:

- `Main` Metody punktu wejścia aplikacji, można oznaczyć z [async](../../csharp/language-reference/keywords/async.md) — słowo kluczowe.
- Wywnioskować nazwy spójnej kolekcji.
- Domyślne wyrażenia.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Ulepszenia platformy

.NET core 2.0 obejmuje kilka funkcji, które ułatwiają Zainstaluj oprogramowanie .NET Core i używać go na obsługiwanych systemów operacyjnych.

### <a name="net-core-for-linux-is-a-single-implementation"></a>Oprogramowanie .NET core dla systemu Linux jest pojedynczą implementacją

.NET core 2.0 oferuje pojedynczej implementacji systemu Linux, który działa na wielu dystrybucje systemu Linux. Oprogramowanie .NET core 1.x wymagane pobranie implementacji Linux specyficzne dla dystrybucji.

Można również tworzyć aplikacji przeznaczonych dla systemu Linux jako jeden system operacyjny. Oprogramowanie .NET core 1.x wymagane oddzielnie target każdej dystrybucji systemu Linux.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Obsługa bibliotek kryptograficznych firmy Apple

Oprogramowanie .NET core 1.x na macOS wymagane kryptograficznych biblioteki OpenSSL zestawu narzędzi. .NET core 2.0 korzysta z bibliotek kryptograficznych firmy Apple i nie wymaga biblioteki OpenSSL, więc nie trzeba go zainstalować.

## <a name="api-changes-and-library-support"></a>Zmiany interfejsu API i obsługa biblioteki

### <a name="support-for-net-standard-20"></a>Obsługa .NET 2.0 standardowe

.NET Standard definiuje wersjonowany zestaw interfejsów API, które muszą być dostępne na implementacje .NET, które są zgodne z tą wersją standardowego. .NET Standard jest przeznaczona dla deweloperów biblioteki. Ma on zagwarantowanie funkcje, które są dostępne w bibliotece, przeznaczonego dla wersji platformy .NET Standard w każdej implementacji .NET. Oprogramowanie .NET core 1.x obsługuje standardowe .NET w wersji 1.6, .NET Core 2.0 obsługuje najnowszą wersję platformy .NET Standard 2.0. Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).

.NET 2.0 standardowe zawiera ponad 20 000 API więcej niż były dostępne w wersji 1.6 standardowe .NET. Większość to rozwinięte powierzchni wyników zawierających interfejsów API, które są wspólne dla programu .NET Framework i platformy Xamarin w .NET Standard.

Biblioteki klas .NET 2.0 standardowych można także odwoływać bibliotek klas .NET Framework, pod warunkiem, że wywołują interfejsów API, które znajdują się w standardowe .NET 2.0. Nie ponowną kompilację biblioteki .NET Framework jest wymagana.

Aby uzyskać listę interfejsów API, które zostały dodane do .NET Standard od jej ostatniej wersji 1.6 standardowe .NET, zobacz [.NET 2.0 standardowe vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Rozszerzona powierzchni

Całkowita liczba interfejsami API dostępnymi w programie .NET Core 2.0 ma więcej niż podwójny porównaniu .NET Core 1.1.

I [pakiet zgodności systemu Windows](../porting/windows-compat-pack.md) eksportowanie z .NET Framework stała się znacznie prostsze.

### <a name="support-for-net-framework-libraries"></a>Obsługa bibliotek .NET Framework

Kodu platformy .NET core można odwoływać się do istniejących bibliotek .NET Framework, w tym istniejących pakietów NuGet. Należy pamiętać, że biblioteki muszą używać interfejsów API, które znajdują się w .NET Standard.

## <a name="visual-studio-integration"></a>integracja z programem Visual Studio

Visual Studio 2017 wersji 15.3 i w niektórych przypadkach program Visual Studio for Mac oferują szereg znaczące ulepszenia dla deweloperów platformy .NET Core.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>Przekierowania aplikacji .NET Core i bibliotek .NET Standard

Po zainstalowaniu programu .NET Core 2.0 SDK można przekierować projektów 1.x .NET Core .NET Core 2.0 i .NET Standard 1.x bibliotek .NET 2.0 standardowe.

Aby przekierować projektu w programie Visual Studio, możesz otworzyć **aplikacji** okna dialogowego właściwości projektu i Zmień na karcie **platformy docelowej** do wartości **.NET Core 2.0** lub **.NET 2.0 standardowe**. Można także zmienić go prawym przyciskiem myszy projekt i wybierając **Edytuj \*pliku .csproj** opcji. Aby uzyskać więcej informacji, zobacz [narzędzi](#tooling) wcześniej w tym temacie.

### <a name="live-unit-testing-support-for-net-core"></a>Obsługa funkcji Live Unit Testing dla platformy .NET Core

Przy każdej modyfikacji kodu na żywo testów jednostkowych automatycznie uruchamia wszystkie testy jednostkowe wykorzystywanych w tle i wyświetla wyniki i pokrycie kodu na żywo w środowisku Visual Studio. .NET core 2.0 obsługuje teraz Live testów jednostkowych. Wcześniej testów jednostkowych Live była dostępna tylko w przypadku aplikacji .NET Framework.

Aby uzyskać więcej informacji, zobacz [Live testów jednostkowych z programu Visual Studio 2017](/visualstudio/test/live-unit-testing) i [Live jednostki testowania — często zadawane pytania](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Lepszą obsługę wielu platform docelowych

Jeśli tworzysz projekt dla wielu struktur docelowych, można wybierać platformy docelowej z menu najwyższego poziomu. Na poniższej ilustracji projektu o nazwie SCD1 jest przeznaczony dla 64-bitowych Mac OS X 10.11 (`osx.10.11-x64`) i 64-bitowego systemu Windows 10/Windows Server 2016 (`win10-x64`). Przed wybraniem przycisku projektu, w tym przypadku do uruchomienia kompilacji debugowania, możesz wybrać platformy docelowej.

![Wybieranie platformy docelowej podczas kompilowania projektu](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>Obsługa Side-by-side .NET Core SDK

Teraz można zainstalować zestawu SDK .NET Core niezależnie od programu Visual Studio. Umożliwia jednej wersji programu Visual Studio do tworzenia projektów tego docelowego różne wersje programu .NET Core. Wcześniej Visual Studio i .NET Core SDK są ściśle powiązane; określonej wersji zestawu SDK wraz z określoną wersją programu Visual Studio.

## <a name="documentation-improvements"></a>Ulepszenia dokumentacji

### <a name="net-application-architecture"></a>Architektura aplikacji .NET

[Architektura aplikacji .NET](https://www.microsoft.com/net/learn/architecture) zapewnia dostęp do zestawu książek e, które zawierają wskazówki, najlepsze rozwiązania i przykładowe aplikacje, gdy przy użyciu platformy .NET do kompilacji:

- Kontenery Mikrousług i Docker.
- Aplikacje sieci Web ASP.NET.
- Aplikacje mobilne z platformą Xamarin.
- Aplikacje, które są wdrażane w chmurze platformy Azure.

## <a name="see-also"></a>Zobacz także
 [Co to jest nowe w programie ASP.NET 2.0 Core](/aspnet/core/aspnetcore-2.0)
