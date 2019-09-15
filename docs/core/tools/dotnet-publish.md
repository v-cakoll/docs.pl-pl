---
title: polecenie dotnet publish
description: Dotnet publish polecenie publikuje projekt platformy .NET Core w katalogu.
ms.date: 05/29/2018
ms.openlocfilehash: f9fea1a30e349ef949078e881756e2520d79ccbf
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969828"
---
# <a name="dotnet-publish"></a>dotnet publish

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet publish`-Pakuje aplikację i jej zależności do folderu w celu wdrożenia w systemie hostingu.

## <a name="synopsis"></a>Streszczenie

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet publish`kompiluje aplikację, odczytuje ją z zależności określonych w pliku projektu i publikuje zestaw plików w katalogu. Dane wyjściowe obejmują następujące zasoby:

- Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll* .
- plik *. deps. JSON* zawiera wszystkie zależności projektu.
- plik *. runtimeconfig. JSON* określa współużytkowany środowisko uruchomieniowe oczekiwane przez aplikację, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ wyrzucania elementów bezużytecznych).
- Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu danych wyjściowych.

Dane `dotnet publish` wyjściowe polecenia są gotowe do wdrożenia w systemie hostingu (na przykład na serwerze, komputerze, Mac, laptopie) do wykonania. Jest to jedyna oficjalnie obsługiwana metoda przygotowania aplikacji do wdrożenia. W zależności od typu wdrożenia, który jest określany przez projekt, system hostingu może lub nie ma zainstalowanego udostępnionego środowiska uruchomieniowego platformy .NET Core. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md). Aby uzyskać strukturę katalogów opublikowanej aplikacji, zobacz [Struktura katalogów](/aspnet/core/hosting/directory-structure).

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT`

Projekt do opublikowania. Jest to ścieżka i nazwa pliku [C#](csproj.md)projektu, F#, lub Visual Basic, lub ścieżka do katalogu, który zawiera plik projektu C#, F#lub Visual Basic. Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md). Należy określić platformę docelową w pliku projektu.

`--force`

Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--manifest <PATH_TO_MANIFEST_FILE>`

Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji. Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, Dodaj `--manifest` opcję dla każdego manifestu. Ta opcja jest dostępna począwszy od zestawu SDK platformy .NET Core 2,0.

`--no-build`

Nie kompiluje projektu przed opublikowaniem. Również niejawnie ustawia `--no-restore` flagę.

`--no-dependencies`

Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.

`--no-restore`

Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do katalogu wyjściowego. Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla wdrożenia zależnego od platformy lub *./bin/[Konfiguracja]/[Framework]/[środowisko uruchomieniowe]/Publish/* do wdrożenia samodzielnego.
Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.

`--self-contained`

Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym. Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`. Aby uzyskać więcej informacji na temat różnych typów wdrożeń, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikację dla danego środowiska uruchomieniowego. Jest on używany podczas tworzenia [własnego wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd). Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). Wartość domyślna to opublikowanie [wdrożenia zależnego od platformy (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

`--version-suffix <VERSION_SUFFIX>`

Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md). Należy określić platformę docelową w pliku projektu.

`--force`

Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--manifest <PATH_TO_MANIFEST_FILE>`

Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji. Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, Dodaj `--manifest` opcję dla każdego manifestu. Ta opcja jest dostępna począwszy od zestawu SDK platformy .NET Core 2,0.

`--no-dependencies`

Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.

`--no-restore`

Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do katalogu wyjściowego. Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla wdrożenia zależnego od platformy lub *./bin/[Konfiguracja]/[Framework]/[środowisko uruchomieniowe]/Publish/* do wdrożenia samodzielnego.
Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.

`--self-contained`

Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym. Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`. Aby uzyskać więcej informacji na temat różnych typów wdrożeń, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikację dla danego środowiska uruchomieniowego. Jest on używany podczas tworzenia [własnego wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd). Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). Wartość domyślna to opublikowanie [wdrożenia zależnego od platformy (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

`--version-suffix <VERSION_SUFFIX>`

Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md). Należy określić platformę docelową w pliku projektu.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--manifest <PATH_TO_MANIFEST_FILE>`

Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji. Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, Dodaj `--manifest` opcję dla każdego manifestu. Ta opcja jest dostępna począwszy od zestawu SDK platformy .NET Core 2,0.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do katalogu wyjściowego. Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla wdrożenia zależnego od platformy lub *./bin/[Konfiguracja]/[Framework]/[środowisko uruchomieniowe]/Publish/* do wdrożenia samodzielnego.
Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikację dla danego środowiska uruchomieniowego. Jest on używany podczas tworzenia [własnego wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd). Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). Wartość domyślna to opublikowanie [wdrożenia zależnego od platformy (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

`--version-suffix <VERSION_SUFFIX>`

Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.

---

## <a name="examples"></a>Przykłady

Opublikuj projekt w bieżącym katalogu:

`dotnet publish`

Publikowanie aplikacji przy użyciu określonego pliku projektu:

`dotnet publish ~/projects/app1/app1.csproj`

Opublikuj projekt w bieżącym katalogu przy użyciu `netcoreapp1.1` struktury:

`dotnet publish --framework netcoreapp1.1`

Opublikuj bieżącą aplikację przy użyciu `netcoreapp1.1` struktury i środowiska uruchomieniowego dla `OS X 10.10` (należy wyświetlić listę tego identyfikatora RID w pliku projektu).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

Opublikuj bieżącą aplikację, ale nie przywracaj odwołań z projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania (zestaw .NET Core SDK 2,0 i nowsze wersje):

`dotnet publish --no-dependencies`

## <a name="see-also"></a>Zobacz także

- [Platformy docelowe](../../standard/frameworks.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md)
