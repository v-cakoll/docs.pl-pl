---
title: Co nowego w programie .NET Core 2.0
description: Dowiedz się więcej o nowych funkcjach znalezionych w .NET Core.
ms.date: 08/13/2017
ms.openlocfilehash: 115b3adc72b6798c6a7bac9cc18044a8822808a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398833"
---
# <a name="whats-new-in-net-core-20"></a>Co nowego w programie .NET Core 2.0

.NET Core 2.0 zawiera ulepszenia i nowe funkcje w następujących obszarach:

- [Narzędzia](#tooling)
- [Obsługa języków](#language-support)
- [Ulepszenia platformy](#platform-improvements)
- [Zmiany interfejsu API](#api-changes-and-library-support)
- [Integracja z programem Visual Studio](#visual-studio-integration)
- [Ulepszenia dokumentacji](#documentation-improvements)

## <a name="tooling"></a>Narzędzia

### <a name="dotnet-restore-runs-implicitly"></a>przywracanie dotnet działa niejawnie

W poprzednich wersjach programu .NET Core trzeba było uruchomić polecenie [przywracania dotnet,](../tools/dotnet-restore.md) aby pobrać zależności natychmiast po utworzeniu nowego projektu za pomocą nowego polecenia [dotnet,](../tools/dotnet-new.md) a także za każdym razem, gdy dodano nową zależność do projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Można `dotnet restore` również wyłączyć automatyczne wywołanie, `--no-restore` przekazując `new`przełącznik `run` `build`do `publish` `pack`, `test` , , , i poleceń.

### <a name="retargeting-to-net-core-20"></a>Retargeting do .NET Core 2.0

Jeśli jest zainstalowany zestaw SDK .NET Core 2.0, projekty docelowe .NET Core 1.x można przekierować do .NET Core 2.0.

Aby ponownie kierować reklamy na .NET Core 2.0, należy `<TargetFramework>` edytować plik `<TargetFrameworks>` projektu, zmieniając wartość elementu (lub elementu, jeśli w pliku projektu znajduje się więcej niż jeden obiekt docelowy) z 1.x do 2.0:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

W ten sam sposób można również ponownie kierować biblioteki standardów .NET do .NET Standard 2.0:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Aby uzyskać więcej informacji na temat migracji projektu do programu .NET Core 2.0, zobacz [Migrowanie z ASP.NET Core 1.x do ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Obsługa języków

Oprócz obsługi języka C# i F#, .NET Core 2.0 obsługuje również visual basic.

### <a name="visual-basic"></a>Visual Basic

W wersji 2.0 program .NET Core obsługuje teraz program Visual Basic 2017. Za pomocą języka Visual Basic można utworzyć następujące typy projektów:

- Aplikacje konsoli .NET Core
- Biblioteki klas .NET Core
- Biblioteki klas .NET Standard
- Projekty testowe jednostkowe .NET Core
- .NET Core xUnit projekty testowe

Na przykład, aby utworzyć aplikację Visual Basic "Hello World", wykonaj następujące kroki z wiersza polecenia:

1. Otwórz okno konsoli, utwórz katalog dla projektu i uczyń go bieżącym katalogiem.

1. Wprowadź polecenie `dotnet new console -lang vb`.

   Polecenie tworzy plik projektu `.vbproj` z rozszerzeniem pliku wraz z plikiem kodu źródłowego języka Visual Basic o nazwie *Program.vb*. Ten plik zawiera kod źródłowy do napisania ciągu "Hello World!" do okna konsoli.

1. Wprowadź polecenie `dotnet run`. Interfejs [cli programu .NET Core](../tools/index.md) automatycznie kompiluje i wykonuje aplikację, która wyświetla komunikat "Hello World!" w oknie konsoli.

### <a name="support-for-c-71"></a>Obsługa języka C# 7.1

.NET Core 2.0 obsługuje c# 7.1, który dodaje szereg nowych funkcji, w tym:

- Metoda, `Main` punkt wejścia aplikacji, może być oznaczona słowem kluczowym [asynchronicznego.](../../csharp/language-reference/keywords/async.md)
- Wywnioskowane nazwy krotki.
- Wyrażenia domyślne.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Ulepszenia platformy

.NET Core 2.0 zawiera szereg funkcji ułatwiających instalację programu .NET Core i używanie go w obsługiwanych systemach operacyjnych.

### <a name="net-core-for-linux-is-a-single-implementation"></a>.NET Core dla systemu Linux to pojedyncza implementacja

.NET Core 2.0 oferuje jedną implementację systemu Linux, która działa na wielu dystrybucjach Linuksa. .NET Core 1.x wymagane jest pobranie implementacji systemu Linux specyficznedla dystrybucji.

Można również tworzyć aplikacje, które są przeznaczone dla systemu Linux jako jeden system operacyjny. .NET Core 1.x wymagane, aby kierować każdej dystrybucji systemu Linux oddzielnie.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Obsługa bibliotek kryptograficznych Firmy Apple

.NET Core 1.x w systemie macOS wymagał biblioteki kryptograficznej zestawu narzędzi OpenSSL. .NET Core 2.0 używa bibliotek kryptograficznych Firmy Apple i nie wymaga OpenSSL, więc nie trzeba go już instalować.

## <a name="api-changes-and-library-support"></a>Zmiany interfejsu API i obsługa bibliotek

### <a name="support-for-net-standard-20"></a>Obsługa standardu .NET 2.0

Standard .NET definiuje wersjonowany zestaw interfejsów API, które muszą być dostępne w implementacjach .NET, które są zgodne z tą wersją standardu. Standard .NET jest przeznaczony dla deweloperów biblioteki. Ma na celu zagwarantowanie funkcji, która jest dostępna dla biblioteki, która jest przeznaczona dla wersji standardu .NET na każdej implementacji .NET. .NET Core 1.x obsługuje wersję .NET Standard w wersji 1.6; .NET Core 2.0 obsługuje najnowszą wersję .NET Standard 2.0. Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).

.NET Standard 2.0 zawiera ponad 20 000 więcej interfejsów API niż były dostępne w standardzie .NET 1.6. Wiele z tego rozwiniętego obszaru powierzchni wynika z włączenia interfejsów API, które są wspólne dla .NET Framework i Xamarin do .NET Standard.

Biblioteki klas .NET Standard 2.0 mogą również odwoływać się do bibliotek klas .NET Framework, pod warunkiem, że wywołają interfejsy API obecne w standardzie .NET 2.0. Nie jest wymagana ponowna kompilacja bibliotek .NET Framework.

Aby uzyskać listę interfejsów API, które zostały dodane do standardu .NET od jego ostatniej wersji, .NET Standard 1.6, zobacz [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Rozszerzona powierzchnia

Całkowita liczba interfejsów API dostępnych w .NET Core 2.0 wzrosła ponad dwukrotnie w porównaniu z .NET Core 1.1.

A dzięki pakietowi [zgodności systemu Windows](../porting/windows-compat-pack.md) przenoszenie z platformy .NET Framework również stało się znacznie prostsze.

### <a name="support-for-net-framework-libraries"></a>Obsługa bibliotek programu .NET Framework

Kod .NET Core może odwoływać się do istniejących bibliotek .NET Framework, w tym istniejących pakietów NuGet. Należy zauważyć, że biblioteki muszą używać interfejsów API, które znajdują się w .NET Standard.

## <a name="visual-studio-integration"></a>Integracja z programem Visual Studio

Program Visual Studio 2017 w wersji 15.3, a w niektórych przypadkach program Visual Studio dla komputerów Mac oferuje szereg istotnych ulepszeń dla deweloperów .NET Core.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>Ponowne kierowanie aplikacji .NET Core i bibliotek standardów .NET

Jeśli jest zainstalowany zestaw SDK .NET Core 2.0, można ponownie skierować projekty .NET Core 1.x do bibliotek .NET Core 2.0 i .NET Standard 1.x do .NET Standard 2.0.

Aby ponownie kierować projekt w programie Visual Studio, otwórz kartę **Aplikacja** w oknie dialogowym właściwości projektu i zmień wartość **platformy docelowej** na **.NET Core 2.0** lub **.NET Standard 2.0**. Można go również zmienić, klikając prawym przyciskiem myszy projekt i wybierając opcję **Edycja \*pliku csproj.** Aby uzyskać więcej informacji, zobacz [sekcji Narzędzia](#tooling) wcześniej w tym temacie.

### <a name="live-unit-testing-support-for-net-core"></a>Obsługa funkcji Live Unit Testing dla platformy .NET Core

Za każdym razem, gdy modyfikujesz kod, aktywne testowanie jednostek automatycznie uruchamia wszystkie testy jednostkowe, których dotyczy problem w tle i wyświetla wyniki i pokrycie kodu na żywo w środowisku programu Visual Studio. .NET Core 2.0 obsługuje teraz testowanie jednostek na żywo. Wcześniej testowanie jednostek na żywo było dostępne tylko dla aplikacji .NET Framework.

Aby uzyskać więcej informacji, zobacz [Testowanie jednostek na żywo za pomocą programu Visual Studio](/visualstudio/test/live-unit-testing) i często [zadawane często zadawane pytania](/visualstudio/test/live-unit-testing-faq)dotyczące testowania jednostek na żywo .

### <a name="better-support-for-multiple-target-frameworks"></a>Lepsze wsparcie dla wielu ram docelowych

Jeśli budujesz projekt dla wielu platform docelowych, możesz teraz wybrać platformę docelową z menu najwyższego poziomu. Na poniższej rysunku projekt o nazwie SCD1 jest przeznaczony dla 64-bitowego systemu macOS X 10.11`osx.10.11-x64``win10-x64`( ) i 64-bitowego systemu Windows 10/Windows Server 2016 ( ). Można wybrać platformę docelową przed wybraniem przycisku projektu, w tym przypadku do uruchomienia kompilacji debugowania.

![Zrzut ekranu przedstawiający wybór struktury docelowej podczas tworzenia projektu.](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>Obsługa zestawów SDK sdk .NET Core side-by side

Zestaw SDK .NET Core można teraz zainstalować niezależnie od programu Visual Studio. Dzięki temu można dla pojedynczej wersji programu Visual Studio do tworzenia projektów, które są przeznaczone dla różnych wersji programu .NET Core. Wcześniej visual studio i .NET Core SDK były ściśle powiązane; określonej wersji sdk towarzyszy określonej wersji programu Visual Studio.

## <a name="documentation-improvements"></a>Ulepszenia dokumentacji

### <a name="net-application-architecture"></a>Architektura aplikacji .NET

[Architektura aplikacji .NET](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) zapewnia dostęp do zestawu e-booków, które zawierają wskazówki, najlepsze rozwiązania i przykładowe aplikacje podczas tworzenia aplikacji .NET przy użyciu platformy .NET:

- [Kontenery mikrousług i platformy Docker](../../architecture/microservices/index.md)
- [Aplikacje internetowe z ASP.NET](../../architecture/modern-web-apps-azure/index.md)
- [Aplikacje mobilne z systemem Xamarin](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [Aplikacje wdrożone w chmurze za pomocą platformy Azure](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a>Zobacz też

- [Co nowego w ASP.NET Core 2.0](/aspnet/core/aspnetcore-2.0)
