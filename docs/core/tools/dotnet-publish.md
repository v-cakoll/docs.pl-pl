---
title: polecenie publikowania dotnetu
description: Polecenie publikowania dotnet publikuje projekt .NET Core lub rozwiązanie do katalogu.
ms.date: 02/24/2020
ms.openlocfilehash: ed5b87b3343210ca81486ef4b9a9d70d1b534464
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110974"
---
# <a name="dotnet-publish"></a>dotnet publish

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet publish`- Publikuje aplikację i jej zależności do folderu do wdrożenia w systemie hostingowym.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>Opis

`dotnet publish`kompiluje aplikację, odczytuje za pośrednictwem jej zależności określonych w pliku projektu i publikuje wynikowy zestaw plików do katalogu. Dane wyjściowe obejmują następujące zasoby:

- Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll.*
- Plik *deps.json,* który zawiera wszystkie zależności projektu.
- Plik *.runtimeconfig.json,* który określa udostępnione środowisko uruchomieniowe, które oczekuje aplikacja, a także inne opcje konfiguracji dla środowiska wykonawczego (na przykład typ wyrzucania elementów bezużytecznych).
- Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu wyjściowego.

Dane `dotnet publish` wyjściowe polecenia są gotowe do wdrożenia w systemie hostingowym (na przykład serwerze, komputerze PC, Mac, laptopie) do wykonania. Jest to jedyny oficjalnie obsługiwany sposób przygotowania aplikacji do wdrożenia. W zależności od typu wdrożenia, który określa projekt, system hostingu może lub nie może mieć .NET Core udostępnionego środowiska uruchomieniowego zainstalowanego na nim.

## <a name="arguments"></a>Argumenty

- **`PROJECT|SOLUTION`**

  Projekt lub rozwiązanie do opublikowania.
  
  * `PROJECT`jest ścieżką i nazwami plików pliku projektu [C#](csproj.md), F#lub Visual Basic lub ścieżką do katalogu zawierającego plik projektu C#, F#lub Visual Basic. Jeśli katalog nie jest określony, domyślnie jest to bieżący katalog.

  * `SOLUTION`jest ścieżką i nazwami pliku rozwiązania ( rozszerzenie *.sln)* lub ścieżką do katalogu zawierającego plik rozwiązania. Jeśli katalog nie jest określony, domyślnie jest to bieżący katalog. Dostępne od .NET Core 3.0 SDK.

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Publikuje aplikację dla określonej [struktury docelowej](../../standard/frameworks.md). Należy określić platformę docelową w pliku projektu.

- **`--force`**

  Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od .NET Core 3.0 SDK.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Określa jeden lub kilka [manifestów docelowych,](../deploying/runtime-store.md) które mają być używane do przycinania zestawu pakietów opublikowanych za pomocą aplikacji. Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, dodaj `--manifest` opcję dla każdego manifestu.

- **`--no-build`**

  Nie tworzy projektu przed opublikowaniem. Również niejawnie `--no-restore` ustawia flagę.

- **`--no-dependencies`**

  Ignoruje odwołania do projektu i przywraca tylko projekt główny.

- **`--nologo`**

  Nie wyświetla banera startowego ani wiadomości o prawach autorskich. Dostępne od .NET Core 3.0 SDK.

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas uruchamiania polecenia.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Określa ścieżkę dla katalogu wyjściowego. Jeśli nie zostanie określony, domyślnie ma *wartość ./bin/[configuration]/[framework]/publish/* dla plików binarnych wykonywalnych zależnych od środowiska uruchomieniowego i między platformami. Domyślnie wartość *./bin/[configuration]/[framework]/[runtime]/publish/* dla samodzielnego pliku wykonywalnego.

  Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.

- **`--self-contained [true|false]`**

  Publikuje środowisko uruchomieniowe .NET Core z aplikacją, więc środowisko wykonawcze nie musi być instalowane na komputerze docelowym. Wartość `true` domyślna to ustawienie, jeśli określono identyfikator środowiska uruchomieniowego. Aby uzyskać więcej informacji, zobacz [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).

- **`--no-self-contained`**

  Odpowiednik `--self-contained false`. Dostępne od .NET Core 3.0 SDK.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publikuje aplikację dla danego środowiska uruchomieniowego. Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md). Aby uzyskać więcej informacji, zobacz [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartością `minimal`domyślną jest .

- **`--version-suffix <VERSION_SUFFIX>`**

  Definiuje sufiks wersji, który ma`*`zastąpić gwiazdkę ( ) w polu wersji pliku projektu.

## <a name="examples"></a>Przykłady

- Utwórz [zależne od środowiska uruchomieniowego wieloplatformowe binarne](../deploying/index.md#produce-a-cross-platform-binary) dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet publish
  ```

  Począwszy od .NET Core 3.0 SDK, w tym przykładzie tworzy również [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla bieżącej platformy.

- Utwórz [samodzielny plik wykonywalny](../deploying/index.md#publish-self-contained) dla projektu w bieżącym katalogu dla określonego środowiska wykonawczego:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  Identyfikator RID musi znajdować się w pliku projektu.

- Utwórz [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla projektu w bieżącym katalogu dla określonej platformy:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  Identyfikator RID musi znajdować się w pliku projektu. W tym przykładzie stosuje się do .NET Core 3.0 SDK i nowszych wersji.

- Publikowanie projektu w bieżącym katalogu dla określonej platformy środowiska wykonawczego i docelowego:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Opublikuj określony plik projektu:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Opublikuj bieżącą aplikację, ale nie przywracaj odwołań do projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Zobacz też

- [Omówienie publikowania aplikacji .NET Core](../deploying/index.md)
- [Publikowanie aplikacji .NET Core za pomocą interfejsu wiersza polecenia .NET Core](../deploying/deploy-with-cli.md)
- [Platformy docelowe](../../standard/frameworks.md)
- [Katalog identyfikatorów IDentifier (RID)](../rid-catalog.md)
- [Praca z macOS Catalina Notarization](../install/macos-notarization-issues.md)
- [Struktura katalogów opublikowanej aplikacji](/aspnet/core/hosting/directory-structure)
