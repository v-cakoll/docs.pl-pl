---
title: Wdrażanie aplikacji .NET core za pomocą narzędzi interfejsu wiersza polecenia
description: Dowiedz się, wdrażanie aplikacji .NET Core za pomocą narzędzia interfejsu wiersza polecenia (CLI)
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: a7e810372d831699eae777186385e45fe65cdf45
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266596"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>Wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia (CLI)

Możesz wdrożyć aplikację platformy .NET Core albo jako *wdrożenia zależny od struktury*, który zawiera pliki binarne aplikacji, ale zależy od obecności platformy .NET Core w systemie docelowym lub jako *niezależna wdrożenie*, który zawiera pliki binarne .NET Core i aplikacji. Aby uzyskać przegląd, zobacz [wdrożenie aplikacji programu .NET Core](index.md).

W poniższych sekcjach opisano sposób użycia [narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) do tworzenia następujących rodzajów wdrożenia:

- Wdrożenie zależny od struktury
- Wdrażanie zależny od struktury za pomocą zależności innych firm
- Niezależne wdrożenia
- Niezależne wdrożenia przy użyciu zależności innych firm

Podczas pracy z poziomu wiersza polecenia, można użyć dowolnego edytora w programie. Jeśli Edytor programu [programu Visual Studio Code](https://code.visualstudio.com), można otworzyć konsoli poleceń w środowisku Visual Studio Code, wybierając **widoku** > **zintegrowany Terminal**.

## <a name="framework-dependent-deployment"></a>Wdrożenie zależny od struktury

Wdrożenie zależny od struktury bez zależności innych firm po prostu polega na tworzenia, testowania i publikowania aplikacji. Prosty przykład napisany w języku C# przedstawiono proces.

1. Utwórz katalog projektu.

   Utwórz katalog dla projektu, co bieżący katalog.

1. Utwórz projekt.

   W wierszu polecenia wpisz polecenie [dotnet nową konsolę](../tools/dotnet-new.md) Aby utworzyć nowy projekt konsoli języka C# lub [dotnet nowej konsoli — lang vb](../tools/dotnet-new.md) Aby utworzyć nowy projekt konsoli języka Visual Basic, w tym katalogu.

1. Dodawanie kodu źródłowego aplikacji.

   Otwórz *Program.cs* lub *Program.vb* w edytorze i Zastęp automatycznie wygenerowany kod następującym kodem. On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Zależności projektu i narzędzia do aktualizacji.

   Uruchom [dotnet restore](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenie, aby przywrócić zależności określony w projekcie.

1. Utworzenie kompilacja do debugowania aplikacji.

   Użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenie, aby skompilować aplikację lub [dotnet, uruchom](../tools/dotnet-run.md) polecenie, aby skompilować i uruchomić ją.

1. Wdrażanie aplikacji.

   Po utworzeniu debugowania i przetestować program, należy utworzyć wdrożenie za pomocą następującego polecenia:

      ```console
      dotnet publish -f netcoreapp2.1 -c Release
      ```
   Spowoduje to utworzenie wydania (zamiast debugowania) wersję aplikacji. Pliki wynikowe są umieszczane w katalogu o nazwie *publikowania* znajdujący się w podkatalogu projektu *bin* katalogu.

   Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji. Plik jest przydatne głównie do debugowania wyjątków. Można nie rozprowadzić go z plikami aplikacji. Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.

   Kompletny zestaw plików aplikacji w jakikolwiek sposób, który można wdrożyć. Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

1. Uruchamianie aplikacji

   Po zainstalowaniu, użytkownicy mogą wykonać aplikacji przy użyciu `dotnet` polecenia i podając nazwę pliku aplikacji, takich jak `dotnet fdd.dll`.

   Oprócz plików binarnych aplikacji Instalatora należy również pakietu Instalatora udostępnionego framework albo Wyszukaj jako warunek wstępny jako część instalacji aplikacji.  Instalacja udostępnionego framework wymaga dostępu administratora/root.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Wdrażanie zależny od struktury za pomocą zależności innych firm

Wdrożenie zależny od struktury z co najmniej jeden zależności innych firm wymaga tych zależności dostępne dla projektu. Wymagane są dwa dodatkowe kroki, aby można było uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:

1. Dodaj odwołania do wymaganych bibliotek innych firm, aby `<ItemGroup>` części Twojej *csproj* pliku. Następujące `<ItemGroup>` sekcja zawiera zależność na [Json.NET](http://www.newtonsoft.com/json) jako biblioteki innej firmy:

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. Jeśli jeszcze nie, Pobierz pakiet NuGet zawierający zależności innych firm. Aby pobrać pakiet, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności. Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej narzędzia NuGet w czasu publikacji, musi on być dostępny w Twoim systemie.

Należy pamiętać, że wdrożenie zależny od struktury z zależności innych firm tylko jako przenośne jako jego zależności innych firm. Na przykład jeśli biblioteki innych firm obsługuje tylko z systemem macOS, aplikacja nie jest przenośny z systemami Windows. Dzieje się tak, jeśli zależności innych firm, sama jest zależna od kodu natywnego. Dobrym przykładem jest [serwera Kestrel](/aspnet/core/fundamentals/servers/kestrel), co wymaga zależności natywnych na [libuv](https://github.com/libuv/libuv). Podczas tworzenia Dyskietki dla aplikacji za pomocą tego rodzaju zależności innych firm opublikowane dane wyjściowe zawiera folder dla każdego [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) obsługującego natywnych zależności (i znajdujące się w pakiecie NuGet).

## <a name="simpleSelf"></a> Niezależne wdrożenia bez zależności innych firm

Wdrożenie niezależna bez zależności innych firm obejmuje tworzenie projektu i modyfikując *csproj* pliku, tworzenia, testowania i publikowania aplikacji. Prosty przykład napisany w języku C# przedstawiono proces. W przykładzie pokazano, jak utworzyć niezależna wdrożenia przy użyciu [narzędzia dotnet](../tools/dotnet.md) z wiersza polecenia.

1. Utwórz katalog dla projektu.

   Utwórz katalog dla projektu i ułatwiają bieżącego katalogu.

1. Utwórz projekt.

   W wierszu polecenia wpisz polecenie [dotnet nową konsolę](../tools/dotnet-new.md) Aby utworzyć nowy projekt konsoli języka C#, w tym katalogu.

1. Dodawanie kodu źródłowego aplikacji.

   Otwórz *Program.cs* w edytorze i Zastęp automatycznie wygenerowany kod następującym kodem. On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]
1. Zdefiniuj platformy, dla których będzie dotyczyć aplikacji.

   Tworzenie `<RuntimeIdentifiers>` tagów w `<PropertyGroup>` części Twojej *csproj* pliku, który definiuje platform aplikacji jest przeznaczony dla i określ identyfikator środowiska uruchomieniowego (RID) dla każdej z platform docelowych. Należy zauważyć, że trzeba będzie również dodać średnika do rozdzielenia identyfikatorów RID. Zobacz [katalog identyfikatora środowiska uruchomieniowego](../rid-catalog.md) Lista identyfikatorów środowisk uruchomieniowych.

   Na przykład następująca `<PropertyGroup>` sekcja wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   Należy pamiętać, że `<RuntimeIdentifiers>` element może znajdować się w dowolnym `<PropertyGroup>` w swojej *csproj* pliku. Pełny przykład *csproj* plik pojawia się w dalszej części w tej sekcji.

1. Zależności projektu i narzędzia do aktualizacji.

   Uruchom [dotnet restore](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenie, aby przywrócić zależności określony w projekcie.

1. Określ, czy używać globalizacji niezmiennej trybu.

   Szczególnie w przypadku, gdy aplikacja jest przeznaczona na systemie Linux, można zmniejszyć całkowity rozmiar wdrożenia, wykorzystując [globalizacji niezmiennej tryb](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md). Globalizacji niezmiennej tryb jest przydatne w przypadku aplikacji, które nie są wspierane i mogą używać konwencji formatowania Konwencji obudowy i ciąg porównywania i sortowania kolejności [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture).

   Aby włączyć tryb niezmiennej, kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań**i wybierz **Edytuj SCD.csproj** lub **Edytuj SCD.vbproj**. Następnie dodaj następujące wiersze wyróżnione do pliku:

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. Utworzenie kompilacja do debugowania aplikacji.

   W wierszu polecenia użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenia.

1. Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla.

   Użyj `dotnet publish` polecenia dla obu platform docelowych w następujący sposób:

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   Spowoduje to utworzenie wydania (zamiast debugowania) wersję aplikacji dla każdej platformy docelowej. Pliki wynikowe są umieszczane w podkatalogu nazwanym *publikowania* znajdujący się w podkatalogu projektu *.\bin\Release\netcoreapp2.1\<runtime_identifier >* podkatalogu. Należy pamiętać, że każdy podkatalogu zawiera kompletny zestaw plików (pliki aplikacji i wszystkich plików z platformy .NET Core) potrzebnych do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji. Plik jest przydatne głównie do debugowania wyjątków. Istnieje możliwość nie spakujesz ją z plikami aplikacji. Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.

Wdrażanie plików publikowanych w jakikolwiek sposób, który chcesz. Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

Poniżej przedstawiono pełne *csproj* pliku dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Niezależne wdrożenia przy użyciu zależności innych firm

Niezależna wdrożenie z co najmniej jeden zależności innych firm obejmuje dodawanie zależności. Wymagane są dwa dodatkowe kroki, aby można było uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:

1. Dodaj odwołania do żadnych bibliotek innych firm, aby `<ItemGroup>` części Twojej *csproj* pliku. Następujące `<ItemGroup>` sekcji używa struktury Json.NET jako biblioteki innej firmy.

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. Jeśli jeszcze nie, Pobierz pakiet NuGet zawierający zależności innych firm w systemie. Aby jednak udostępnić zależności aplikacji, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności. Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej narzędzia NuGet w czasu publikacji, musi on być dostępny w Twoim systemie.

Poniżej przedstawiono pełne *csproj* pliku dla tego projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

Podczas wdrażania aplikacji, wszelkie zależności innych firm używanych w aplikacji znajdują się również z plikami aplikacji. Bibliotek innych firm nie są wymagane w systemie, na którym działa aplikacja.

Należy pamiętać, że można wdrożyć tylko niezależna wdrożenia przy użyciu biblioteki innej firmy na platformach obsługiwanych przez tej biblioteki. Jest to podobne do mających zależności innych firm za pomocą natywnego zależności w ramach wdrożenia zależny od struktury, gdzie zależności natywnych musi być zgodny z platform, w której wdrażana jest aplikacja.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a>Zobacz także

* [Wdrożenie aplikacji programu .NET core](index.md)
* [Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)
