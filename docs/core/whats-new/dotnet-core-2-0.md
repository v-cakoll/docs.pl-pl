---
title: What's new in .NET Core 2.0
description: Więcej informacji na temat nowych funkcji, które znajdują się w .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: 02aac2dab2b892927c0c98fae30bb287a6e24ad6
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778470"
---
# <a name="whats-new-in-net-core-20"></a>What's new in .NET Core 2.0

.NET core 2.0 zawiera ulepszenia i nowe funkcje w następujących obszarach:

- [Narzędzia](#tooling)
- [Obsługa języków](#language-support)
- [Ulepszenia platformy](#platform-improvements)
- [Zmiany interfejsu API](#api-changes-and-library-support)
- [Integracja z programem Visual Studio](#visual-studio-integration)
- [Udoskonalenia dokumentacji](#documentation-improvements)

## <a name="tooling"></a>Narzędzia

### <a name="dotnet-restore-runs-implicitly"></a>DotNet restore uruchamia się domyślnie

W poprzednich wersjach programu .NET Core, trzeba było uruchomić [dotnet restore](../tools/dotnet-restore.md) polecenie, aby pobrać zależności natychmiast, po utworzeniu nowego projektu za pomocą [dotnet nowe](../tools/dotnet-new.md) polecenia, a także zawsze, gdy użytkownik dodać nowe zależności do projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Można również wyłączyć automatyczne wywołanie `dotnet restore` , przekazując `--no-restore` przełączyć się do `new`, `run`, `build`, `publish`, `pack`, i `test` poleceń.

### <a name="retargeting-to-net-core-20"></a>Trwa przekierowywanie do programu .NET Core 2.0

Jeśli zainstalowano zestawu .NET Core 2.0 SDK, projekty przeznaczone na platformę .NET Core 1.x można ukierunkowany na .NET Core 2.0.

Aby przekierować do platformy .NET Core 2.0, należy edytować plik projektu, zmieniając wartość `<TargetFramework>` elementu (lub `<TargetFrameworks>` elementu, jeśli masz więcej niż jeden element docelowy w pliku projektu) z 1.x do 2.0:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Można również przekierować biblioteki .NET Standard, .NET Standard 2.0 tak samo:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Aby uzyskać więcej informacji na temat migracji projektu .NET Core 2.0, zobacz [migracji z programu ASP.NET Core 1.x do ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Obsługa języków

Oprócz obsługi języka C# i F #, .NET Core 2.0 obsługuje Visual Basic.

### <a name="visual-basic"></a>Visual Basic

W wersji 2.0 .NET Core obsługuje teraz 2017 Visual Basic. Visual Basic umożliwia tworzenie następujących typów projektu:

- Aplikacje konsoli .NET core
- Biblioteki klas platformy .NET core
- Biblioteki klas .NET standard
- Projekty testów jednostkowych .NET core
- Projekty testów xUnit platformy .NET core

Na przykład aby utworzyć aplikację Visual Basic "Hello World", wykonaj następujące czynności w wierszu polecenia:

1. Otwórz okno konsoli, a następnie utwórz katalog dla projektu i ułatwiają bieżącego katalogu.

1. Wprowadź polecenie `dotnet new console -lang vb`.

   Polecenie tworzy plik projektu o `.vbproj` pliku rozszerzenie, wraz z pliku kodu źródłowego języka Visual Basic o nazwie *Program.vb*. Ten plik zawiera kod źródłowy, aby zapisać ciąg "Hello World!" w oknie konsoli.

1. Wprowadź polecenie `dotnet run`. [Interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) automatycznie kompiluje i uruchamia aplikację, która wyświetla komunikat "Hello World!" w oknie konsoli.

### <a name="support-for-c-71"></a>Obsługa języka C# 7.1

.NET core 2.0 obsługuje C# 7.1, który dodaje wiele nowych funkcji, w tym:

- `Main` Metody punktu wejścia aplikacji, mogą być oznaczone [async](../../csharp/language-reference/keywords/async.md) — słowo kluczowe.
- Pochodnych nazw krotek.
- Wyrażenia domyślnego.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Ulepszenia platformy

.NET core 2.0 obejmuje pewną liczbę funkcji, które ułatwiają instalowanie programu .NET Core i z niej korzystać w obsługiwanych systemach operacyjnych.

### <a name="net-core-for-linux-is-a-single-implementation"></a>.NET core dla systemu Linux jest pojedynczą implementacją

.NET core 2.0 oferuje pojedynczą implementacją systemu Linux, która działa na wielu dystrybucji systemu Linux. .NET core 1.x wymagane pobierania implementacji programu specyficzne dla dystrybucji systemu Linux.

Możesz również tworzyć aplikacje przeznaczone dla systemu Linux jako jeden system operacyjny. .NET core 1.x wymagane oddzielnie docelowe każdej dystrybucji systemu Linux.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Obsługa bibliotek kryptograficznych firmy Apple

.NET core 1.x w systemie macOS wymagane kryptograficznych biblioteki OpenSSL zestawu narzędzi. .NET core 2.0 używa bibliotek kryptograficznych firmy Apple i nie wymaga biblioteki OpenSSL, dzięki czemu nie trzeba go zainstalować.

## <a name="api-changes-and-library-support"></a>Zmiany interfejsu API i obsługa bibliotek

### <a name="support-for-net-standard-20"></a>Obsługa .NET Standard 2.0

.NET Standard definiuje zestaw numerów wersji interfejsów API, które muszą być dostępne w implementacji .NET, które są zgodne z wersji standard. .NET Standard jest przeznaczona dla deweloperów bibliotek. Ma on funkcjonalność, która jest dostępna dla biblioteki, który jest przeznaczony dla wersji programu .NET Standard na każdej implementacji .NET. .NET core 1.x obsługuje .NET Standard w wersji 1.6; .NET Core 2.0 obsługuje najnowszej wersji .NET Standard 2.0. Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).

.NET standard 2.0 zawiera ponad 20 000 więcej interfejsów API nie były dostępne w wersji 1.6 standardowy .NET. Większość tego rozwinięte powierzchni wyników zawierających interfejsów API, które są wspólne dla środowiska .NET Framework i Xamarin do .NET Standard.

Biblioteki klas .NET standard 2.0 także odwoływać się do biblioteki klas .NET Framework, pod warunkiem, że będą wywoływać interfejsy API, które znajdują się w programie .NET Standard 2.0. Nie kompilację bibliotek programu .NET Framework jest wymagana.

Aby uzyskać listę interfejsów API, które zostały dodane do .NET Standard od jej ostatniej wersji platformy .NET Standard w wersji 1.6, zobacz [vs .NET Standard 2.0. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Rozwinięty obszar powierzchni

Całkowita liczba interfejsami API dostępnymi w programie .NET Core 2.0 podwoiła więcej niż w porównaniu z platformy .NET Core 1.1.

I [systemie Windows Compatibility Pack](../porting/windows-compat-pack.md) przenoszenie z .NET Framework również stał się dużo prostsze.

### <a name="support-for-net-framework-libraries"></a>Obsługa bibliotek .NET Framework

Kod platformy .NET core może odwoływać się do istniejących bibliotek .NET Framework, w tym istniejących pakietów NuGet. Należy pamiętać, że bibliotek należy użyć interfejsów API, które znajdują się w programie .NET Standard.

## <a name="visual-studio-integration"></a>integracja z programem Visual Studio

Visual Studio 2017 w wersji 15.3, a w niektórych przypadkach program Visual Studio for Mac oferuje szereg znaczące ulepszenia dla deweloperów platformy .NET Core.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>Trwa przekierowywanie aplikacje platformy .NET Core oraz biblioteki .NET Standard

Jeśli zainstalowano zestawu .NET Core 2.0 SDK, można przekierować projektów programu .NET Core 1.x do platformy .NET Core 2.0 i .NET Standard 1.x bibliotek .NET Standard 2.0.

Aby przekierować projektu w programie Visual Studio, możesz otworzyć **aplikacji** na karcie okna dialogowego właściwości projektu i zmień **platformę docelową** wartość **.NET Core 2.0** lub **.NET standard 2.0**. Możesz również zmienić, klikając prawym przyciskiem myszy na projekt i wybierając **Edytuj \*pliku .csproj** opcji. Aby uzyskać więcej informacji, zobacz [narzędzi](#tooling) wcześniej w tym temacie.

### <a name="live-unit-testing-support-for-net-core"></a>Obsługa funkcji Live Unit Testing dla platformy .NET Core

Przy każdej modyfikacji kodu Live Unit Testing automatycznie uruchamia wszystkie testy jednostkowe wykorzystywanych w tle i wyświetla wyniki i pokrycia kodu na żywo w środowisku Visual Studio. .NET core 2.0 obsługuje teraz funkcję Live Unit Testing. Wcześniej Live Unit Testing była dostępna tylko w przypadku aplikacji .NET Framework.

Aby uzyskać więcej informacji, zobacz [Live Unit Testing w programie Visual Studio 2017](/visualstudio/test/live-unit-testing) i [Live Unit Testing — często zadawane pytania](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Lepsza obsługa wielu platform docelowych

Jeśli tworzysz projekt dla wielu platform docelowych można teraz wybrać platformę docelową menu najwyższego poziomu. Na poniższej ilustracji, projekt o nazwie SCD1 cele 64-bitowym z systemem macOS X 10.11 (`osx.10.11-x64`) i 64-bitowego systemu Windows 10/Windows Server 2016 (`win10-x64`). Przed wybraniem przycisku projektu, w tym przypadku kompilację debugowania, możesz wybrać platformy docelowej.

![Wybieranie platformy docelowej podczas kompilowania projektu](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>Side-by-side obsługę zestawów .NET Core SDK

Można teraz zainstalować zestaw .NET Core SDK, niezależnie od programu Visual Studio. Umożliwia jednej wersji programu Visual Studio do tworzenia projektów tego kierują do różnych wersji programu .NET Core. Wcześniej Visual Studio i .NET Core SDK są ściśle powiązane; określoną wersję zestawu SDK wraz z określonej wersji programu Visual Studio.

## <a name="documentation-improvements"></a>Udoskonalenia dokumentacji

### <a name="net-application-architecture"></a>Architektura aplikacji .NET

[Architektura aplikacji .NET](https://www.microsoft.com/net/learn/architecture) zapewnia dostęp do zestawu książkami elektronicznymi, które zapewniają wskazówki, najlepsze rozwiązania i przykładowe aplikacje, korzystając z platformy .NET do tworzenia:

- [Mikrousług i kontenerów rozwiązania Docker](../../standard/microservices-architecture/index.md)
- [Aplikacje sieci Web wykorzystujące technologie ASP.NET](../../standard/modern-web-apps-azure-architecture/index.md)
- [Aplikacje mobilne za pomocą platformy Xamarin](/xamarin/xamarin-forms/enterprise-application-patterns/index.md)
- [Aplikacje, które są wdrażane w chmurze dzięki platformie Azure](/azure/architecture/reference-architectures/index.md)

## <a name="see-also"></a>Zobacz także

* [What's new in ASP.NET Core 2.0](/aspnet/core/aspnetcore-2.0)
