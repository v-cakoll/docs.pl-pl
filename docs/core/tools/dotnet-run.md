---
title: polecenie dotnet Run
description: Polecenie dotnet Run udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego.
ms.date: 05/29/2018
ms.openlocfilehash: b21987ef9ee4dd7d8fdb93d0853b7faa93001688
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969750"
---
# <a name="dotnet-run"></a>dotnet run

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet run`-Uruchamia kod źródłowy bez żadnych jawnych poleceń kompilacji lub uruchamiania.

## <a name="synopsis"></a>Streszczenie

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet run` Polecenie udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia. Jest to przydatne w przypadku szybkiego iteracyjnego programowania z poziomu wiersza polecenia. Polecenie jest zależne od [`dotnet build`](dotnet-build.md) polecenia do kompilowania kodu. Wszelkie wymagania dotyczące kompilacji, takie jak najpierw należy przywrócić projekt, również zastosować do `dotnet run` .

Pliki wyjściowe są zapisywane w lokalizacji domyślnej, czyli `bin/<configuration>/<target>`. Na przykład jeśli masz `netcoreapp2.1` aplikację i uruchomisz `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp2.1`. Pliki są zastępowane w razie konieczności. Pliki tymczasowe są umieszczane w `obj` katalogu.

Jeśli projekt określa wiele struktur, wykonanie `dotnet run` powoduje błąd, `-f|--framework <FRAMEWORK>` chyba że opcja jest używana do określenia struktury.

`dotnet run` Polecenie jest używane w kontekście projektów, nieskompilowanych zestawów. Jeśli próbujesz uruchomić bibliotekę DLL aplikacji zależnej od platformy, musisz użyć [dotnet](dotnet.md) bez polecenia. Na przykład aby uruchomić `myapp.dll`polecenie, użyj:

```console
dotnet myapp.dll
```

Aby uzyskać więcej informacji na `dotnet` temat sterownika, zobacz temat [narzędzia wiersza polecenia (CLI) platformy .NET Core](index.md) .

Aby uruchomić aplikację, `dotnet run` polecenie rozwiązuje zależności aplikacji, które są poza udostępnionym środowiskiem uruchomieniowym z pamięci podręcznej NuGet. Ponieważ używa on buforowanych zależności, nie jest zalecane `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym. Zamiast tego [Utwórz wdrożenie](../deploying/index.md) przy użyciu [`dotnet publish`](dotnet-publish.md) polecenia i Wdróż opublikowane dane wyjściowe.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--`

Ogranicza argumenty `dotnet run` od argumentów dla uruchamianej aplikacji. Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md). Struktura musi być określona w pliku projektu.

`--force`

Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--launch-profile <NAME>`

Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji. Profile uruchamiania są zdefiniowane w pliku *profilu launchsettings. JSON* i są zwykle nazywane `Development`, `Staging`i `Production`. Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).

`--no-build`

Nie kompiluje projektu przed uruchomieniem. Również niejawne ustawia `--no-restore` flagę.

`--no-dependencies`

W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.

`--no-launch-profile`

Nie próbuje skonfigurować aplikacji przy użyciu pliku *profilu launchsettings. JSON* .

`--no-restore`

Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

`-p|--project <PATH>`

Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka). Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.

`--runtime <RUNTIME_IDENTIFIER>`

Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--`

Ogranicza argumenty `dotnet run` od argumentów dla uruchamianej aplikacji. Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md). Struktura musi być określona w pliku projektu.

`--force`

Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--launch-profile <NAME>`

Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji. Profile uruchamiania są zdefiniowane w pliku *profilu launchsettings. JSON* i są zwykle nazywane `Development`, `Staging`i `Production`. Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).

`--no-build`

Nie kompiluje projektu przed uruchomieniem. Również niejawne ustawia `--no-restore` flagę.

`--no-dependencies`

W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.

`--no-launch-profile`

Nie próbuje skonfigurować aplikacji przy użyciu pliku *profilu launchsettings. JSON* .

`--no-restore`

Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

`-p|--project <PATH>`

Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka). Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.

`--runtime <RUNTIME_IDENTIFIER>`

Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--`

Ogranicza argumenty `dotnet run` od argumentów dla uruchamianej aplikacji. Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md). Struktura musi być określona w pliku projektu.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`-p|--project <PATH/PROJECT.csproj>`

Określa ścieżkę i nazwę pliku projektu. (Zobacz uwagi). Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.

> [!NOTE]
> Użyj ścieżki i nazwy pliku projektu z `-p|--project` opcją. Regresja w interfejsie wiersza polecenia uniemożliwia podanie ścieżki folderu z zestaw .NET Core SDK 1. x. Aby uzyskać więcej informacji o tym problemie, zobacz polecenie [dotnet Run-p, nie można uruchomić projektu (#5992 dotnet/CLI)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Przykłady

Uruchom projekt w bieżącym katalogu:

`dotnet run`

Uruchom określony projekt:

`dotnet run --project ./projects/proj1/proj1.csproj`

Uruchom projekt w bieżącym katalogu ( `--help` argument w tym przykładzie jest przesyłany do aplikacji, ponieważ jest używana opcja pusta `--` ):

`dotnet run --configuration Release -- --help`

Przywróć zależności i narzędzia dla projektu w bieżącym katalogu, wyświetlając tylko minimalne dane wyjściowe, a następnie Uruchom projekt: (zestaw .NET Core SDK 2,0 i nowsze wersje):

`dotnet run --verbosity m`
