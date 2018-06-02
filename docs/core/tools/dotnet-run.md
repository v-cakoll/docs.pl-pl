---
title: 'Uruchom polecenie: .NET Core interfejsu wiersza polecenia platformy DotNet'
description: Dotnet, uruchom polecenie zapewnia to wygodny sposób do uruchamiania aplikacji z kodu źródłowego.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 82c6e44e52aa6af7044edf72fd6e57b7614a70f3
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696315"
---
# <a name="dotnet-run"></a>Uruchom DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet run` -Uruchamia źródła kodu bez jawnego kompilowania i uruchamiania poleceń.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)
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

`dotnet run` Polecenia oferuje wygodny sposób do uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia. Jest to przydatne w przypadku szybkiego iteracyjne programowanie z wiersza polecenia. Polecenie zależy od [ `dotnet build` ](dotnet-build.md) do kompilacji kodu. Wszelkie wymagania dotyczące kompilacji, takim jak projekt musi zostać przywrócona, dotyczą `dotnet run` również.

Pliki wyjściowe są zapisywane w domyślnej lokalizacji, która jest `bin/<configuration>/<target>`. Na przykład jeśli masz `netcoreapp1.0` aplikacji i uruchom `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp1.0`. Pliki zostaną zastąpione, zgodnie z potrzebami. Pliki tymczasowe są umieszczane w `obj` katalogu.

Jeśli projekt określa wielu struktur, wykonywania `dotnet run` powoduje błąd, chyba że `-f|--framework <FRAMEWORK>` opcja służy do określania platformę.

`dotnet run` Polecenie jest używane w kontekście projektów nie skompilowane zestawy. Jeśli zastanawiasz się do uruchomienia aplikacji zależnych od framework DLL zamiast tego należy użyć [dotnet](dotnet.md) bez polecenia. Na przykład, aby uruchomić `myapp.dll`, użyj:

```console
dotnet myapp.dll
```

Aby uzyskać więcej informacji na temat `dotnet` sterowników, zobacz [.NET Core wiersza polecenia narzędzia (CLI)](index.md) tematu.

Aby uruchomić aplikację, `dotnet run` polecenia rozpoznaje zależności aplikacji, które znajdują się poza udostępnionym środowiska uruchomieniowego z pamięci podręcznej NuGet. Ponieważ używa zależności w pamięci podręcznej, nie zalecamy używania `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym. Zamiast tego [tworzenia wdrożenia](../deploying/index.md) przy użyciu [ `dotnet publish` ](dotnet-publish.md) polecenia i wdrażanie publikowanych danych wyjściowych.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)

`--`

Argumenty rozgranicza `dotnet run` z argumentów uruchamiania aplikacji. Wszystkie argumenty po tym ogranicznikiem są przekazywane do uruchomienia aplikacji.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Tworzenie i działanie aplikacji przy użyciu określonego [framework](../../standard/frameworks.md). Platformę należy określić w pliku projektu.

`--force`

Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie. Określenie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--launch-profile <NAME>`

Nazwa uruchomienie profilu (jeśli istnieje) do użycia podczas uruchamiania aplikacji. Profile uruchamiania są zdefiniowane w *launchSettings.json* pliku i są zwykle nazywane `Development`, `Staging`, i `Production`. Aby uzyskać więcej informacji, zobacz [Praca w środowiskach wielu](/aspnet/core/fundamentals/environments).

`--no-build`

Nie Skompiluj projekt przed uruchomieniem. Niejawne także ustawia `--no-restore` flagi.

`--no-dependencies`

Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.

`--no-launch-profile`

Nie próbuje użyć *launchSettings.json* do skonfigurowania aplikacji.

`--no-restore`

Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.

`-p|--project <PATH>`

Określa ścieżkę pliku projektu do uruchomienia (folder lub ścieżka pełna). Jeśli nie zostanie określony, domyślnie do bieżącego katalogu.

`--runtime <RUNTIME_IDENTIFIER>`

Określa docelowe środowisko uruchomieniowe pod kątem przywracania pakietów dla. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--`

Argumenty rozgranicza `dotnet run` z argumentów uruchamiania aplikacji. Wszystkie argumenty po tym ogranicznikiem są przekazywane do uruchomienia aplikacji.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Tworzenie i działanie aplikacji przy użyciu określonego [framework](../../standard/frameworks.md). Platformę należy określić w pliku projektu.

`--force`

Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie. Określenie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--launch-profile <NAME>`

Nazwa uruchomienie profilu (jeśli istnieje) do użycia podczas uruchamiania aplikacji. Profile uruchamiania są zdefiniowane w *launchSettings.json* pliku i są zwykle nazywane `Development`, `Staging`, i `Production`. Aby uzyskać więcej informacji, zobacz [Praca w środowiskach wielu](/aspnet/core/fundamentals/environments).

`--no-build`

Nie Skompiluj projekt przed uruchomieniem. Niejawne także ustawia `--no-restore` flagi.

`--no-dependencies`

Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.

`--no-launch-profile`

Nie próbuje użyć *launchSettings.json* do skonfigurowania aplikacji.

`--no-restore`

Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.

`-p|--project <PATH>`

Określa ścieżkę pliku projektu do uruchomienia (folder lub ścieżka pełna). Jeśli nie zostanie określony, domyślnie do bieżącego katalogu.

`--runtime <RUNTIME_IDENTIFIER>`

Określa docelowe środowisko uruchomieniowe pod kątem przywracania pakietów dla. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--`

Argumenty rozgranicza `dotnet run` z argumentów uruchamiania aplikacji. Wszystkie argumenty po tym ogranicznikiem są przekazywane do uruchomienia aplikacji.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Tworzenie i działanie aplikacji przy użyciu określonego [framework](../../standard/frameworks.md). Platformę należy określić w pliku projektu.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-p|--project <PATH/PROJECT.csproj>`

Określa ścieżkę i nazwę pliku projektu. (Patrz Notatka). Jeśli nie zostanie określony, domyślnie do bieżącego katalogu.

> [!NOTE]
> Użyj ścieżka i nazwa pliku projektu z `-p|--project` opcji. Regresja w interfejsu wiersza polecenia uniemożliwia dostarczanie ścieżkę folderu zestawu SDK programu .NET Core 1.x. Aby uzyskać więcej informacji na temat tego problemu, zobacz [dotnet Uruchom -p, nie można uruchomić projektu (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Przykłady

Uruchom projekt w bieżącym katalogu:

`dotnet run`

Uruchamia określony projekt:

`dotnet run --project /projects/proj1/proj1.csproj`

Uruchom projekt w bieżącym katalogu ( `--help` argument w tym przykładzie jest przekazywany do aplikacji, ponieważ `--` argument jest używany):

`dotnet run --configuration Release -- --help`

Przywróć zależności i narzędzi dla projektu w bieżącym katalogu tylko przedstawiający minimalnego danych wyjściowych, a następnie uruchom projekt: (.NET Core SDK 2.0 i nowsze wersje):

`dotnet run --verbosity m`