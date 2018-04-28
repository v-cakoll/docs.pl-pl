---
title: Wdrażanie aplikacji .NET core za pomocą narzędzi interfejsu wiersza polecenia
description: Dowiedz się, wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia (CLI)
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 21e824e6092b0d30e0499ff05c5471a291c8d269
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>Wdrażanie aplikacji .NET Core za pomocą narzędzia interfejsu wiersza polecenia (CLI)

Możesz wdrożyć aplikację .NET Core albo jako *wdrożenia zależne od framework*, który zawiera pliki binarne z aplikacji, ale zależy od obecności .NET Core w systemie docelowym lub jako *niezależne wdrożenie*, który zawiera pliki binarne .NET Core i aplikacji. Aby uzyskać ogólne informacje, zobacz [wdrażanie aplikacji .NET Core](index.md).

W poniższych sekcjach przedstawiono sposób użycia [narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) można utworzyć następujące typy wdrożeń:

- Zależne od Framework wdrożenia
- Wdrożenie Framework zależne zależności innych firm
- Samodzielne wdrożenia
- Samodzielne wdrożenia zależności innych firm

Podczas pracy z poziomu wiersza polecenia, można użyć dowolnego edytora programu. Jeśli w edytorze programu [Visual Studio Code](https://code.visualstudio.com), można otworzyć konsoli poleceń w środowisku Visual Studio Code, wybierając **widoku** > **zintegrowane terminali**.

## <a name="framework-dependent-deployment"></a>Zależne od Framework wdrożenia

Po prostu wdrażanie wdrożenia zależne od framework bez zależności innych firm obejmuje tworzenie, testowanie i publikowanie aplikacji. Prosty przykład napisane w języku C# przedstawiono proces. 

1. Utwórz katalog projektu.

   Utwórz katalog projektu i stał się bieżącym katalogiem.

1. Tworzenie projektu.

   W wierszu polecenia wpisz [dotnet nowej konsoli](../tools/dotnet-new.md) Aby utworzyć nowy projekt console C# w tym katalogu.

1. Należy dodać kodu źródłowego aplikacji.

   Otwórz *Program.cs* plik w edytorze i Zastąp następujący kod automatycznie wygenerowany kod. Monituje użytkownika o wprowadzenie tekstu, a Wyświetla poszczególnych wyrazów wprowadzony przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w wejściowego tekstu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Zależności projektu i narzędzia do aktualizacji.
 
   Uruchom [przywracania dotnet](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenia, aby przywrócić zależności określony w projekcie.

1. Utwórz kompilację debugowania aplikacji.

   Użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenie, aby skompilować aplikację lub [dotnet Uruchom](../tools/dotnet-run.md) polecenie, aby skompilować i uruchomić go.

1. Wdrażanie aplikacji.

   Po utworzeniu debugowania i przetestowane programu, tworzenia wdrożenia za pomocą następującego polecenia:

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   Spowoduje to utworzenie zlecenia (zamiast debugowania) wersji aplikacji. Pliki wynikowe są umieszczane w katalogu o nazwie *publikowania* w podkatalogu projektu *bin* katalogu.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (.pdb) program, który zawiera informacje o debugowaniu aplikacji. Plik przydaje się głównie w celu debugowania wyjątków. Można pominąć rozpowszechnienie go z plikami aplikacji. Jednak należy go zapisać, w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Pełny zestaw plików aplikacji w dowolny sposób, który chcesz można wdrożyć. Na przykład można umieścić je w pliku Zip, użyć prostej `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika. Po zainstalowaniu użytkowników można uruchamiać aplikacji przy użyciu `dotnet` polecenia i podania nazwy pliku aplikacji, takich jak `dotnet fdd.dll`.

Oprócz plików binarnych aplikacji instalatorem należy również pakietu Instalatora udostępnionego framework albo wyszukać jako warunek wstępny jako część instalacji aplikacji.  Instalacja udostępnionego framework wymaga dostępu administratora/root.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Wdrożenie Framework zależne zależności innych firm

Wdrażanie wdrożenie zależne od framework z co najmniej jeden zależności innych firm wymaga tych zależności dostępne do projektu. Wymagane są dwa dodatkowe czynności, przed uruchomieniem `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:

1. Dodaj odwołania do wymaganych bibliotek innych firm do `<ItemGroup>` części Twojego *csproj* pliku. Następujące `<ItemGroup>` sekcja zawiera zależność na [Json.NET](http://www.newtonsoft.com/json) jako biblioteki innych firm:

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. Jeśli nie jest jeszcze, Pobierz pakiet NuGet zawierający zależności innych firm. Aby pobrać pakiet, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności. Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej NuGet w czasie publikacji, musi być dostępna w systemie.

Należy pamiętać, że wdrożenie framework zależne zależności innych firm tylko jako przenośne jako jego zależności innych firm. Na przykład jeśli biblioteka innych firm obsługuje tylko macOS, aplikacja nie jest przenośne z systemami Windows. Dzieje się tak, jeśli zależności innych firm, sama zależy od kodu natywnego. Dobrym przykładem jest [serwera Kestrel](/aspnet/core/fundamentals/servers/kestrel), co wymaga natywnego zależności na [libuv](https://github.com/libuv/libuv). Podczas tworzenia Dyskietki dla aplikacji z tego rodzaju zależności innych firm publikowanych danych wyjściowych zawiera folder dla każdej [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) obsługującego natywnego zależności (i znajdujące się w pakiecie NuGet).

## <a name="simpleSelf"></a> Samodzielne wdrożenia bez zależności innych firm

Wdrażanie niezależne wdrożenia bez zależności innych firm obejmuje tworzenie projektu, modyfikując *csproj* plików, tworzenie, testowanie i publikowanie aplikacji. Prosty przykład napisane w języku C# przedstawiono proces. W przykładzie przedstawiono sposób tworzenia niezależne wdrożenia przy użyciu [narzędzie dotnet](../tools/dotnet.md) z wiersza polecenia.

1. Utwórz katalog projektu.

   Utwórz katalog projektu i stał się bieżącym katalogiem.

1. Tworzenie projektu.

   W wierszu polecenia wpisz [dotnet nowej konsoli](../tools/dotnet-new.md) Aby utworzyć nowy projekt console C# w tym katalogu.

1. Należy dodać kodu źródłowego aplikacji.

   Otwórz *Program.cs* plik w edytorze i Zastąp następujący kod automatycznie wygenerowany kod. Monituje użytkownika o wprowadzenie tekstu, a Wyświetla poszczególnych wyrazów wprowadzony przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w wejściowego tekstu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Zdefiniuj platformy, dla których aplikacja będzie obowiązywać.

   Utwórz `<RuntimeIdentifiers>` tagów w `<PropertyGroup>` części Twojego *csproj* pliku, który definiuje platformy aplikacji elementów docelowych i podaj identyfikator środowiska uruchomieniowego (RID) dla każdej z platform docelowych. Należy pamiętać, że należy również dodać średnika do rozdzielenia identyfikatorów RID. Zobacz [katalogu identyfikator środowiska uruchomieniowego](../rid-catalog.md) dla identyfikatorów środowiska wykonawczego. 

   Na przykład następująca `<PropertyGroup>` sekcji wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X 10.11 wersji.

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   Należy pamiętać, że `<RuntimeIdentifiers>` element może występować w dowolnym `<PropertyGroup>` w Twojej *csproj* pliku. Kompletnego przykładu *csproj* plik pojawi się później w tej sekcji.

1. Zależności projektu i narzędzia do aktualizacji.

   Uruchom [przywracania dotnet](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenia, aby przywrócić zależności określony w projekcie.

1. Utwórz kompilację debugowania aplikacji.

   W wierszu polecenia użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenia.

1. Po debugowania i przetestować program, należy utworzyć plików do wdrożenia z aplikacją dla poszczególnych platform jej celem.

   Użyj `dotnet publish` polecenia dla obu platform docelowych w następujący sposób:

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   Spowoduje to utworzenie zlecenia (zamiast debugowania) wersji aplikacji dla każdej platformy docelowej. Pliki wynikowe są umieszczane w podkatalogu o nazwie *publikowania* w podkatalogu projektu *.\bin\Release\netcoreapp1.1\<runtime_identifier >* podkatalogu. Należy pamiętać, że każdy podkatalog zawiera pełny zestaw plików (pliki aplikacji i wszystkich plików .NET Core) potrzebne do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (.pdb) program, który zawiera informacje o debugowaniu aplikacji. Plik przydaje się głównie w celu debugowania wyjątków. Możesz nie można skopiować pliki aplikacji. Jednak należy go zapisać, w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Wdrażanie plików publikowanych w dowolny sposób, który chcesz. Na przykład można umieścić je w pliku Zip, użyć prostej `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

Poniżej przedstawiono pełną *csproj* pliku dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Samodzielne wdrożenia zależności innych firm

Wdrażanie niezależne wdrożenie z co najmniej jeden zależności innych firm obejmuje dodawanie zależności. Wymagane są dwa dodatkowe czynności, przed uruchomieniem `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:

1. Dodaj odwołania do bibliotek żadnych innych firm, które mają `<ItemGroup>` części Twojego *csproj* pliku. Następujące `<ItemGroup>` sekcji używa struktury Json.NET jako biblioteki innych firm.

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. Jeśli nie jest jeszcze, Pobierz pakiet NuGet zawierający zależności innych firm w systemie. Aby udostępnić zależności aplikacji, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności. Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej NuGet w czasie publikacji, musi być dostępna w systemie.

Poniżej przedstawiono pełną *csproj* pliku dla tego projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

Podczas wdrażania aplikacji, wszelkie zależności innych firm używane w aplikacji znajdują się również z plikami aplikacji. Biblioteki innych firm nie są wymagane na komputerze, na którym jest uruchomiona aplikacja.

Należy pamiętać, że można wdrożyć tylko autonomiczną wdrożenia z biblioteką innych firm na platformach obsługiwanych przez tej biblioteki. Przypomina o zależności innych firm z natywnego zależności w ramach wdrożenia zależne od framework gdzie zależności macierzysty musi być zgodny z platformy, na którym aplikacja jest wdrożona.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a>Zobacz także

[Wdrażanie aplikacji .NET core](index.md)   
[Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)   

