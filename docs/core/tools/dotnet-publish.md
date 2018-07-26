---
title: polecenia — interfejs wiersza polecenia platformy .NET Core publikowania DotNet
description: Polecenia publikowania dotnet publikuje projekt .NET Core w katalogu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 38224aa8472f99df107e523667e18892384a20b0
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220675"
---
# <a name="dotnet-publish"></a>Publikowanie DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet publish` -Pakietów aplikacji oraz jego zależności w folderze w celu wdrożenia systemu macierzystego.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet publish` kompiluje aplikację, czyta za pośrednictwem jego zależności, które określono w pliku projektu i publikuje Wynikowy zestaw plików w katalogu. Dane wyjściowe obejmują następujące zasoby:

* Pośredni Language (IL) kod w zestawie przy użyciu *dll* rozszerzenia.
* *. deps.json* pliku, który zawiera wszystkie zależności projektu.
* *. runtime.config.json* pliku, który określa udostępnionego środowiska uruchomieniowego, która oczekuje aplikacji, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ kolekcji wyrzucania elementów).
* Zależności aplikacji, które są kopiowane z pamięcią podręczną programu NuGet do folderu wyjściowego.

`dotnet publish` Danych wyjściowych polecenia jest gotowa do wdrożenia systemu macierzystego (na przykład na serwerze, PC, Mac, laptop) do wykonania. Jest oficjalnie obsługiwana jedynie do przygotowania aplikacji do wdrożenia. W zależności od typu wdrożenia, który określa projektu systemu macierzystego może być lub może nie mieć platformy .NET Core udostępnionego środowiska uruchomieniowego na nim zainstalowany. Aby uzyskać więcej informacji, zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md). Struktura katalogów opublikowanej aplikacji, można zobaczyć [strukturę katalogów](/aspnet/core/hosting/directory-structure).

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT`

Projekt do opublikowania. Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md). W pliku projektu, należy określić platformę docelową.

`--force`

Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie. Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--manifest <PATH_TO_MANIFEST_FILE>`

Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji. Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu. Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.

`--no-build`

Nie da się skompilować projektu przed opublikowaniem. Ustawia ona również niejawne `--no-restore` flagi.

`--no-dependencies`

Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.

`--no-restore`

Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do katalogu wyjściowego. Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.
Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.

`--self-contained`

Publikuje środowisko uruchomieniowe platformy .NET Core za pomocą aplikacji, dzięki czemu środowisko uruchomieniowe nie muszą być zainstalowane na komputerze docelowym. Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`. Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikację dla danego środowiska uruchomieniowego. To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd). Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md). Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md). W pliku projektu, należy określić platformę docelową.

`--force`

Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie. Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--manifest <PATH_TO_MANIFEST_FILE>`

Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji. Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu. Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.

`--no-dependencies`

Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.

`--no-restore`

Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do katalogu wyjściowego. Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.
Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.

`--self-contained`

Publikuje środowisko uruchomieniowe platformy .NET Core za pomocą aplikacji, dzięki czemu środowisko uruchomieniowe nie muszą być zainstalowane na komputerze docelowym. Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`. Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikację dla danego środowiska uruchomieniowego. To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd). Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md). Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md). W pliku projektu, należy określić platformę docelową.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--manifest <PATH_TO_MANIFEST_FILE>`

Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji. Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu. Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do katalogu wyjściowego. Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.
Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikację dla danego środowiska uruchomieniowego. To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd). Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md). Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.

---

## <a name="examples"></a>Przykłady

Opublikuj projekt w bieżącym katalogu:

`dotnet publish`

Publikowanie aplikacji przy użyciu pliku projektu:

`dotnet publish ~/projects/app1/app1.csproj`

Opublikuj projekt w bieżącym katalogu przy użyciu `netcoreapp1.1` framework:

`dotnet publish --framework netcoreapp1.1`

Publikowanie bieżącej aplikacji przy użyciu `netcoreapp1.1` struktura i środowisko uruchomieniowe dla `OS X 10.10` (musi zawierać ten identyfikatorów RID w pliku projektu).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

Publikowanie bieżącej aplikacji, ale nie zostaną przywrócone do projektu (P2P) odwołań, po prostu projekt główny podczas operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):

`dotnet publish --no-dependencies`

## <a name="see-also"></a>Zobacz także

* [Platformy docelowe](../../standard/frameworks.md)
* [Katalog identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md)
