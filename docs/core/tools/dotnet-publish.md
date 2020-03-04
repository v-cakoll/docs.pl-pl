---
title: polecenie dotnet publish
description: Dotnet publish polecenie publikuje projekt .NET Core lub rozwiązanie w katalogu.
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157002"
---
# <a name="dotnet-publish"></a>dotnet publish

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet publish` — publikuje aplikację wraz z jej zależnościami w folderze do wdrożenia w systemie hostingu.

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

`dotnet publish` kompiluje aplikację, odczytuje ją z zależności określonych w pliku projektu i publikuje zestaw plików w katalogu. Dane wyjściowe obejmują następujące zasoby:

- Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll* .
- Plik *. deps. JSON* , który zawiera wszystkie zależności projektu.
- Plik *. runtimeconfig. JSON* , który określa udostępnione środowisko uruchomieniowe oczekiwane przez aplikację, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ wyrzucania elementów bezużytecznych).
- Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu danych wyjściowych.

Dane wyjściowe polecenia `dotnet publish` są gotowe do wdrożenia w systemie hostingu (na przykład serwer, komputer, Mac, laptop) do wykonania. Jest to jedyna oficjalnie obsługiwana metoda przygotowania aplikacji do wdrożenia. W zależności od typu wdrożenia, który jest określany przez projekt, system hostingu może lub nie ma zainstalowanego udostępnionego środowiska uruchomieniowego platformy .NET Core.

## <a name="arguments"></a>Argumenty

- **`PROJECT|SOLUTION`**

  Projekt lub rozwiązanie do opublikowania.
  
  * `PROJECT` jest ścieżką i nazwą pliku projektu [C#](csproj.md), F#lub Visual Basic lub ścieżką do katalogu, który zawiera plik projektu C#, F#lub Visual Basic. Jeśli katalog nie jest określony, domyślnie jest bieżącym katalogiem.

  * `SOLUTION` jest ścieżką i nazwą pliku rozwiązania (rozszerzeniem*sln* ) lub ścieżką do katalogu zawierającego plik rozwiązania. Jeśli katalog nie jest określony, domyślnie jest bieżącym katalogiem. **Dostępne począwszy od zestawu SDK platformy .NET Core 3,0.** 

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md). Należy określić platformę docelową w pliku projektu.

- **`--force`**

  Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`** **dostępne począwszy od zestawu SDK platformy .NET Core 3,0.**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji. Plik manifestu jest częścią danych wyjściowych [polecenia`dotnet store`](dotnet-store.md). Aby określić wiele manifestów, Dodaj opcję `--manifest` dla każdego manifestu.

- **`--no-build`**

  Nie kompiluje projektu przed opublikowaniem. Niejawnie ustawia również flagę `--no-restore`.

- **`--no-dependencies`**

  Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.

- **`--nologo`** **dostępne począwszy od zestawu SDK platformy .NET Core 3,0.**

  Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich. 

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Określa ścieżkę do katalogu wyjściowego. Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla plików wykonywalnych zależnych od środowiska uruchomieniowego i międzyplatformowych plików binarnych. Wartość domyślna to *./bin/[Konfiguracja]/[Framework]/[Runtime]/Publish/* dla samodzielnego pliku wykonywalnego.

  Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.

- **`--self-contained [true|false]`**

  Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym. Wartość domyślna to `true`, jeśli określono identyfikator środowiska uruchomieniowego. Aby uzyskać więcej informacji, zobacz Aplikacje [.NET Core](../deploying/index.md) i publikowanie aplikacji [platformy .net core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).

- **`--no-self-contained`** **dostępne począwszy od zestawu SDK platformy .NET Core 3,0.**

  Równoważne `--self-contained false`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publikuje aplikację dla danego środowiska uruchomieniowego. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). Aby uzyskać więcej informacji, zobacz Aplikacje [.NET Core](../deploying/index.md) i publikowanie aplikacji [platformy .net core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.

## <a name="examples"></a>Przykłady

- Utwórz [Międzyplatformowy plik binarny zależny od środowiska uruchomieniowego](../deploying/index.md#produce-a-cross-platform-binary) dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet publish
  ```

  Począwszy od zestawu SDK platformy .NET Core 3,0, w tym przykładzie tworzony jest również [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla bieżącej platformy.

- Utwórz [własny plik wykonywalny](../deploying/index.md#publish-self-contained) dla projektu w bieżącym katalogu dla określonego środowiska uruchomieniowego:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  Identyfikator RID musi znajdować się w pliku projektu.

- Utwórz [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla projektu w bieżącym katalogu dla określonej platformy:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  Identyfikator RID musi znajdować się w pliku projektu. Ten przykład dotyczy zestawu .NET Core 3,0 SDK i nowszych wersji.

- Opublikuj projekt w bieżącym katalogu dla określonego środowiska uruchomieniowego i platformy docelowej:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Publikuj określony plik projektu:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Opublikuj bieżącą aplikację, ale nie przywracaj odwołań z projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Zobacz też

- [Omówienie publikowania aplikacji .NET Core](../deploying/index.md)
- [Publikowanie aplikacji platformy .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md)
- [Platformy docelowe](../../standard/frameworks.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md)
- [Praca z MacOS Catalina Notarization](../install/macos-notarization-issues.md) Aby uzyskać więcej informacji, zobacz następujące zasoby:
- [Struktura katalogów opublikowanej aplikacji](/aspnet/core/hosting/directory-structure)
