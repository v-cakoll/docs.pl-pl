---
title: polecenie publikowania dotnet
description: Polecenie publikowania dotnet publikuje projekt lub rozwiązanie programu .NET Core w katalogu.
ms.date: 02/24/2020
ms.openlocfilehash: c34618409c9a539043c84c7e03daa8aa249d64f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146558"
---
# <a name="dotnet-publish"></a>dotnet publish

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

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

`dotnet publish`kompiluje aplikację, odczytuje jej zależności określone w pliku projektu i publikuje wynikowy zestaw plików do katalogu. Dane wyjściowe obejmują następujące aktywa:

- Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll.*
- Plik *.deps.json,* który zawiera wszystkie zależności projektu.
- Plik *.runtimeconfig.json,* który określa udostępniony czas wykonywania, który oczekuje aplikacji, a także inne opcje konfiguracji dla czasu wykonywania (na przykład typ wyrzucania elementów bezużytecznych).
- Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu wyjściowego.

Dane `dotnet publish` wyjściowe polecenia są gotowe do wdrożenia w systemie hostingowym (na przykład serwer, komputer PC, Mac, laptop) do wykonania. Jest to jedyny oficjalnie obsługiwany sposób przygotowania aplikacji do wdrożenia. W zależności od typu wdrożenia, który określa projekt, system hostingu może lub nie może mieć zainstalowanego udostępnionego programu .NET Core.

## <a name="arguments"></a>Argumenty

- **`PROJECT|SOLUTION`**

  Projekt lub rozwiązanie do opublikowania.
  
  * `PROJECT`to ścieżka i nazwa pliku pliku projektu [Języka C#,](csproj.md)F# lub Visual Basic lub ścieżka do katalogu zawierającego plik projektu Języka C#, F# lub Visual Basic. Jeśli katalog nie jest określony, domyślnie jest to bieżący katalog.

  * `SOLUTION`to ścieżka i nazwa pliku pliku rozwiązania *(rozszerzenie sln)* lub ścieżka do katalogu zawierającego plik rozwiązania. Jeśli katalog nie jest określony, domyślnie jest to bieżący katalog. Dostępne od sdk .NET Core 3.0.

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Publikuje aplikację dla określonej [struktury docelowej](../../standard/frameworks.md). Należy określić platformę docelową w pliku projektu.

- **`--force`**

  Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zatrzymanie polecenia i oczekiwanie na wejście użytkownika lub akcję. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od sdk .NET Core 3.0.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Określa jeden lub kilka [manifestów docelowych,](../deploying/runtime-store.md) które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji. Plik manifestu jest częścią danych [ `dotnet store` ](dotnet-store.md)wyjściowych polecenia . Aby określić wiele manifestów, dodaj `--manifest` opcję dla każdego manifestu.

- **`--no-build`**

  Nie tworzy projektu przed opublikowaniem. To również niejawnie ustawia `--no-restore` flagę.

- **`--no-dependencies`**

  Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.

- **`--nologo`**

  Nie wyświetla banera startowego ani wiadomości o prawach autorskich. Dostępne od sdk .NET Core 3.0.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas uruchamiania polecenia.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Określa ścieżkę katalogu wyjściowego. Jeśli nie zostanie określony, domyślnie *./bin/[configuration]/[framework]/publish/* dla plików insynualnych zależnych od czasu wykonywania i plików binarnych między platformami. Domyślnie *./bin/[configuration]/[framework]/[runtime]/publish/* dla samodzielnego pliku wykonywalnego.

  Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie bieżącego katalogu roboczego.

- **`--self-contained [true|false]`**

  Publikuje program .NET Core w aplikacji, dzięki czemu czas wykonywania nie musi być zainstalowany na komputerze docelowym. Domyślnie `true` jest, jeśli określono identyfikator czasu wykonywania. Aby uzyskać więcej informacji, zobacz [publikowanie](../deploying/index.md) i [publikowanie aplikacji .NET Core w aplikacji .NET Core za pomocą interfejsu wiersza wiersza wiersza wiersza wiersza .NET Core](../deploying/deploy-with-cli.md).

- **`--no-self-contained`**

  Odpowiednik `--self-contained false`. Dostępne od sdk .NET Core 3.0.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publikuje aplikację dla danego czasu uruchomieniowego. Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md). Aby uzyskać więcej informacji, zobacz [publikowanie](../deploying/index.md) i [publikowanie aplikacji .NET Core w aplikacji .NET Core za pomocą interfejsu wiersza wiersza wiersza wiersza wiersza .NET Core](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartością `minimal`domyślną jest .

- **`--version-suffix <VERSION_SUFFIX>`**

  Definiuje sufiks wersji, aby zastąpić`*`gwiazdkę ( ) w polu wersji pliku projektu.

## <a name="examples"></a>Przykłady

- Utwórz [plik binarny zależny między platformami](../deploying/index.md#produce-a-cross-platform-binary) dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet publish
  ```

  Począwszy od .NET Core 3.0 SDK, w tym przykładzie tworzy również [plik wykonywalny zależny od czasu wykonywania](../deploying/index.md#publish-runtime-dependent) dla bieżącej platformy.

- Utwórz [samodzielny plik wykonywalny](../deploying/index.md#publish-self-contained) dla projektu w bieżącym katalogu dla określonego czasu wykonawczego:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  Rid musi znajdować się w pliku projektu.

- Utwórz [plik wykonywalny zależny od czasu wykonywania](../deploying/index.md#publish-runtime-dependent) dla projektu w bieżącym katalogu dla określonej platformy:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  Rid musi znajdować się w pliku projektu. W tym przykładzie dotyczy .NET Core 3.0 SDK i nowszych wersji.

- Opublikuj projekt w bieżącym katalogu dla określonej struktury wykonywania i docelowej:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Opublikuj określony plik projektu:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Opublikuj bieżącą aplikację, ale nie przywracaj odwołań projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Zobacz też

- [Omówienie publikowania aplikacji .NET Core](../deploying/index.md)
- [Publikowanie aplikacji .NET Core za pomocą wiersza wiersza wiersza wiersza wiersza .NET Core](../deploying/deploy-with-cli.md)
- [Platformy docelowe](../../standard/frameworks.md)
- [Katalog identyfikatora środowiska uruchomienigo (RID)](../rid-catalog.md)
- [Praca z systemem macOS Catalina Notariacja](../install/macos-notarization-issues.md) Aby uzyskać więcej informacji, zobacz on następujące zasoby:
- [Struktura katalogów opublikowanej aplikacji](/aspnet/core/hosting/directory-structure)
