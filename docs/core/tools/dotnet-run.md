---
title: polecenia DotNet, uruchom polecenie — interfejs wiersza polecenia platformy .NET Core
description: Polecenia dotnet, uruchom polecenie zapewnia wygodny sposób, aby uruchomić aplikację z kodu źródłowego.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f560e6f795f00488818647a4b5c711dcf9d59dcd
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324533"
---
# <a name="dotnet-run"></a>Uruchom polecenia DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet run` — Przebiegi źródła kodu, bez jawnego kompilowania i uruchamiania poleceń.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet run` Polecenie zapewnia wygodny sposób, aby uruchomić aplikację z kodu źródłowego za pomocą jednego polecenia. Jest to przydatne w przypadku szybkiego iteracyjne projektowanie z wiersza polecenia. Polecenie zależy od [ `dotnet build` ](dotnet-build.md) polecenie, aby skompilować kod. Wszelkie wymagania dotyczące kompilacji, takie jak, projekt musi zostać przywrócona najpierw dotyczą `dotnet run` także.

Pliki wyjściowe są zapisywane w domyślnej lokalizacji, czyli `bin/<configuration>/<target>`. Na przykład jeśli masz `netcoreapp2.1` aplikacji i uruchom `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp2.1`. Pliki zostaną zastąpione, zgodnie z potrzebami. Pliki tymczasowe są umieszczane w `obj` katalogu.

Jeśli projekt określa wiele struktur, wykonywanie `dotnet run` powoduje błąd, chyba że `-f|--framework <FRAMEWORK>` opcja służy do określania platformę.

`dotnet run` Polecenie jest używane w kontekście projektów, nie skompilowanych zestawów. Jeśli próbujesz zamiast tego uruchomić program zależny od struktury biblioteki DLL, należy użyć [dotnet](dotnet.md) bez polecenia. Na przykład, aby uruchomić `myapp.dll`, użyj:

```console
dotnet myapp.dll
```

Aby uzyskać więcej informacji na temat `dotnet` sterowników, zobacz [.NET Core wiersza polecenia narzędzia (CLI)](index.md) tematu.

Aby uruchomić aplikację, `dotnet run` polecenie usuwa zależności aplikacji, które znajdują się poza udostępnionego środowiska uruchomieniowego z pamięcią podręczną programu NuGet. Ponieważ używa ona zależności pamięci podręcznej, nie zaleca się używać `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym. Zamiast tego [Utwórz wdrożenie](../deploying/index.md) przy użyciu [ `dotnet publish` ](dotnet-publish.md) poleceń i wdrożyć opublikowane dane wyjściowe.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--`

Argumenty rozgranicza `dotnet run` na podstawie argumentów dla aplikacji, są uruchamiane. Wszystkie argumenty po tym ogranicznikiem są przekazywane do aplikacji, uruchom.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Kompiluje i uruchamia aplikację przy użyciu określonego [framework](../../standard/frameworks.md). Struktura należy określić w pliku projektu.

`--force`

Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie. Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--launch-profile <NAME>`

Nazwa uruchomienia profilu (jeśli istnieje) do użycia podczas uruchamiania aplikacji. Profile uruchamiania są zdefiniowane w *launchSettings.json* pliku i są zwykle nazywane `Development`, `Staging`, i `Production`. Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).

`--no-build`

Nie da się skompilować projekt przed uruchomieniem. Ustawia ona również niejawne `--no-restore` flagi.

`--no-dependencies`

Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca projektu głównego, a nie odwołania.

`--no-launch-profile`

Nie próbuj używać *launchSettings.json* do konfigurowania aplikacji.

`--no-restore`

Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.

`-p|--project <PATH>`

Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełną ścieżkę). Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.

`--runtime <RUNTIME_IDENTIFIER>`

Określa docelowe środowisko uruchomieniowe w celu przywrócenia pakietów dla. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--`

Argumenty rozgranicza `dotnet run` na podstawie argumentów dla aplikacji, są uruchamiane. Wszystkie argumenty po tym ogranicznikiem są przekazywane do aplikacji, uruchom.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Kompiluje i uruchamia aplikację przy użyciu określonego [framework](../../standard/frameworks.md). Struktura należy określić w pliku projektu.

`--force`

Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie. Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--launch-profile <NAME>`

Nazwa uruchomienia profilu (jeśli istnieje) do użycia podczas uruchamiania aplikacji. Profile uruchamiania są zdefiniowane w *launchSettings.json* pliku i są zwykle nazywane `Development`, `Staging`, i `Production`. Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).

`--no-build`

Nie da się skompilować projekt przed uruchomieniem. Ustawia ona również niejawne `--no-restore` flagi.

`--no-dependencies`

Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca projektu głównego, a nie odwołania.

`--no-launch-profile`

Nie próbuj używać *launchSettings.json* do konfigurowania aplikacji.

`--no-restore`

Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.

`-p|--project <PATH>`

Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełną ścieżkę). Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.

`--runtime <RUNTIME_IDENTIFIER>`

Określa docelowe środowisko uruchomieniowe w celu przywrócenia pakietów dla. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--`

Argumenty rozgranicza `dotnet run` na podstawie argumentów dla aplikacji, są uruchamiane. Wszystkie argumenty po tym ogranicznikiem są przekazywane do aplikacji, uruchom.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Kompiluje i uruchamia aplikację przy użyciu określonego [framework](../../standard/frameworks.md). Struktura należy określić w pliku projektu.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-p|--project <PATH/PROJECT.csproj>`

Określa ścieżkę i nazwę pliku projektu. (Zobacz Uwagi). Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.

> [!NOTE]
> Użyj ścieżkę i nazwę pliku projektu za pomocą `-p|--project` opcji. Regresja w interfejsie wiersza polecenia platformy zapobiega, podając ścieżkę folderu przy użyciu zestawu SDK programu .NET Core 1.x. Aby uzyskać więcej informacji na temat tego problemu, zobacz [dotnet, uruchom -p, nie można uruchomić projektu (/ interfejsu wiersza polecenia dotnet #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Przykłady

Uruchom projekt w bieżącym katalogu:

`dotnet run`

Uruchamia określony projekt:

`dotnet run --project ./projects/proj1/proj1.csproj`

Uruchom projekt w bieżącym katalogu ( `--help` argument w tym przykładzie jest przekazywany do aplikacji, ponieważ pustą `--` jest używana opcja):

`dotnet run --configuration Release -- --help`

Przywracanie zależności i narzędzia dla projektów w bieżącym katalogu, tylko wyświetlanie minimalne dane wyjściowe, a następnie uruchomić projekt: (.NET Core SDK 2.0 i nowsze wersje):

`dotnet run --verbosity m`