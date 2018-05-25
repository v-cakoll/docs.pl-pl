---
title: polecenie - .NET Core interfejsu wiersza polecenia Opublikuj DotNet
description: Polecenie Publikuj dotnet publikuje projektu platformy .NET Core w katalogu.
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.openlocfilehash: 5e7ce5ce1240f03f53f6e120dfce53d15917425f
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="dotnet-publish"></a>Publikowanie DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet publish` -Pakietów aplikacji i jego zależności do folderu wdrożenia z systemem hostingu.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet publish` kompiluje aplikacji odczytuje za pośrednictwem jego zależności, określona w pliku projektu i publikuje Wynikowy zestaw plików w katalogu. Dane wyjściowe będą zawierać następujące informacje:

* Kod języka (IL) w zestawie z pośredniego *dll* rozszerzenia.
* *. deps.json* pliku, który zawiera wszystkie zależności projektu.
* *. runtime.config.json* pliku, który określa udostępnionego środowisko uruchomieniowe, które oczekuje aplikacji, a także innych opcji konfiguracji dla środowiska uruchomieniowego (na przykład typ kolekcji pamięci).
* Zależności aplikacji. Te są kopiowane z pamięci podręcznej NuGet do folderu wyjściowego.

`dotnet publish` Danych wyjściowych polecenia jest gotowy do wdrożenia do obsługi systemu (na przykład serwer, PC, Mac, laptop) do wykonania i jest jedynym oficjalnie obsługiwana sposobu przygotowania aplikacji do wdrożenia. W zależności od typu wdrożenia, który określa projekt system obsługujący może lub nie może być .NET Core współużytkowany środowiska uruchomieniowego na nim zainstalowany. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md). Do struktury katalogu opublikowanej aplikacji, zobacz [struktury katalogów](/aspnet/core/hosting/directory-structure).

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT`

Projekt do publikowania, domyślnie do bieżącego katalogu, jeśli nie zostanie określony.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Publikowanie aplikacji dla określonego [platformy docelowej](../../standard/frameworks.md). Należy określić w pliku projektu platformy docelowej.

`--force`

Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie. Jest to równoważne usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--manifest <PATH_TO_MANIFEST_FILE>`

Określa jeden lub kilka [target manifestów](../deploying/runtime-store.md) na potrzeby trim zestaw pakietów opublikowane z aplikacją. Plik manifestu jest częścią dane wyjściowe [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu. Ta opcja jest dostępna, począwszy od zestawu SDK programu .NET Core 2.0.

`--no-dependencies`

Ignoruje odwołania projektu do projektu i przywraca tylko projektu głównego.

`--no-restore`

Nie wykonać przywracanie niejawne, podczas uruchamiania polecenia.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do katalogu wyjściowego. Jeśli nie zostanie określony, domyślnie *./bin/[configuration]/[framework]/publish/* wdrożenia zależne od framework lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla Samodzielne wdrożenia.
W przypadku względną ścieżkę do katalogu wyjściowego, generowane jest względną wobec lokalizacji pliku projektu, aby bieżący katalog roboczy nie.

`--self-contained`

Publikuje środowiska uruchomieniowego .NET Core z aplikacji, więc środowisko uruchomieniowe nie musi być zainstalowany na komputerze docelowym. Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`. Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikowanie aplikacji dla danego środowiska uruchomieniowego. To jest używany podczas tworzenia [niezależne wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd). Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md). Domyślnie nie jest publikowanie [wdrożenia framework zależne (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definiuje sufiksem wersji, aby zastąpić gwiazdka (`*`) w polu wersja pliku projektu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Publikowanie aplikacji dla określonego [platformy docelowej](../../standard/frameworks.md). Należy określić w pliku projektu platformy docelowej.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--manifest <PATH_TO_MANIFEST_FILE>`

Określa jeden lub kilka [target manifestów](../deploying/runtime-store.md) na potrzeby trim zestaw pakietów opublikowane z aplikacją. Plik manifestu jest częścią dane wyjściowe [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu. Ta opcja jest dostępna, począwszy od zestawu SDK programu .NET Core 2.0.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do katalogu wyjściowego. Jeśli nie zostanie określony, domyślnie *./bin/[configuration]/[framework]/publish/* wdrożenia zależne od framework lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla Samodzielne wdrożenia.
W przypadku względną ścieżkę do katalogu wyjściowego, generowane jest względną wobec lokalizacji pliku projektu, aby bieżący katalog roboczy nie.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikowanie aplikacji dla danego środowiska uruchomieniowego. To jest używany podczas tworzenia [niezależne wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd). Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md). Domyślnie nie jest publikowanie [wdrożenia framework zależne (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definiuje sufiksem wersji, aby zastąpić gwiazdka (`*`) w polu wersja pliku projektu.

---

## <a name="examples"></a>Przykłady

Publikuj projekt w bieżącym katalogu:

`dotnet publish`

Publikowanie aplikacji przy użyciu pliku określonego projektu:

`dotnet publish ~/projects/app1/app1.csproj`

Opublikować projekt w bieżącym katalogu, używając `netcoreapp1.1` framework:

`dotnet publish --framework netcoreapp1.1`

Publikowanie bieżącej aplikacji przy użyciu `netcoreapp1.1` framework i środowiska uruchomieniowego dla `OS X 10.10` (musi zawierać ten identyfikatorów RID w pliku projektu).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

Publikowanie bieżącej aplikacji, ale nie należy przywracać projektu do projektu (P2P) odwołań, po prostu główny projekt podczas operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):

`dotnet publish --no-dependencies`

## <a name="see-also"></a>Zobacz także

* [Platformy docelowe](../../standard/frameworks.md)
* [Wykaz identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md)
