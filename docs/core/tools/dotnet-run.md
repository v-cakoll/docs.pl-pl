---
title: polecenie dotnet run
description: Polecenie dotnet run zapewnia wygodną opcję uruchamiania aplikacji z kodu źródłowego.
ms.date: 02/19/2020
ms.openlocfilehash: 77282fd8615ef01b7867c1bf0f741c834b6ddb30
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102774"
---
# <a name="dotnet-run"></a>dotnet run

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet run`- Uruchamia kod źródłowy bez żadnych jawnych poleceń kompilacji lub uruchamiania.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet run` zapewnia wygodną opcję uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia. Jest to przydatne do szybkiego rozwoju iteracyjnego z wiersza polecenia. Polecenie zależy od [`dotnet build`](dotnet-build.md) polecenia do tworzenia kodu. Wszelkie wymagania dotyczące kompilacji, takie jak, że projekt `dotnet run` musi zostać przywrócony w pierwszej kolejności, stosuje się również do.

Pliki wyjściowe są zapisywane w `bin/<configuration>/<target>`lokalizacji domyślnej, która jest . Na przykład, jeśli `netcoreapp2.1` masz aplikację `dotnet run`i uruchomisz `bin/Debug/netcoreapp2.1`, dane wyjściowe są umieszczane w pliku . Pliki są zastępowane w razie potrzeby. Pliki tymczasowe są `obj` umieszczane w katalogu.

Jeśli projekt określa wiele struktur, `dotnet run` wykonywanie powoduje błąd, `-f|--framework <FRAMEWORK>` chyba że opcja jest używana do określenia struktury.

Polecenie `dotnet run` jest używane w kontekście projektów, a nie zestawów. Jeśli próbujesz uruchomić bibliotekę DLL aplikacji zależnej od struktury, należy użyć [dotnet](dotnet.md) bez polecenia. Na przykład, `myapp.dll`aby uruchomić , użyj:

```dotnetcli
dotnet myapp.dll
```

Aby uzyskać więcej `dotnet` informacji na temat sterownika, zobacz temat [.NET Core Command Line Tools (CLI).](index.md)

Aby uruchomić aplikację, `dotnet run` polecenie rozwiązuje zależności aplikacji, które znajdują się poza udostępnionym środowiskom run z pamięci podręcznej NuGet. Ponieważ używa zależności w pamięci podręcznej, nie `dotnet run` jest zalecane do uruchamiania aplikacji w produkcji. Zamiast tego [utwórz](../deploying/index.md) wdrożenie [`dotnet publish`](dotnet-publish.md) za pomocą polecenia i wdrożyć opublikowane dane wyjściowe.

### <a name="implicit-restore"></a>Niejawne przywracanie

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Opcje

- **`--`**

  Rozgranicza `dotnet run` argumenty na argumenty dla uruchamianą aplikacji. Wszystkie argumenty po tym ogranicznik są przekazywane do uruchomienia aplikacji.

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Tworzy i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md). Struktura musi być określona w pliku projektu.

- **`--force`**

  Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania). Dostępne od .NET Core 3.0 SDK.

- **`--launch-profile <NAME>`**

  Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji. Profile uruchamiania są definiowane w pliku *launchSettings.json* i są zwykle nazywane `Development`, `Staging`i `Production`. Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).

- **`--no-build`**

  Nie tworzy projektu przed uruchomieniem. Również niejawne `--no-restore` ustawia flagę.

- **`--no-dependencies`**

  Podczas przywracania projektu z odwołaniami do projektu do projektu (P2P), przywraca projekt główny, a nie odwołania.

- **`--no-launch-profile`**

  Nie próbuje użyć *launchSettings.json,* aby skonfigurować aplikację.

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas uruchamiania polecenia.

- **`-p|--project <PATH>`**

  Określa ścieżkę pliku projektu do uruchomienia (nazwę folderu lub pełną ścieżkę). Jeśli nie zostanie określony, domyślnie jest to bieżący katalog.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy czas wykonywania do przywrócenia pakietów dla. Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md). `-r`dostępna od momentu sdk .NET Core 3.0.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartością domyślną jest `m`. Dostępne od .NET Core 2.1 SDK.

## <a name="examples"></a>Przykłady

- Uruchom projekt w bieżącym katalogu:

  ```dotnetcli
  dotnet run
  ```

- Uruchom określony projekt:

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- Uruchom projekt w bieżącym katalogu `--help` (argument w tym przykładzie jest przekazywany do aplikacji, ponieważ używana jest pusta `--` opcja):

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu tylko pokazując minimalne dane wyjściowe, a następnie uruchom projekt: (.NET Core SDK 2.0 i nowsze wersje):

  ```dotnetcli
  dotnet run --verbosity m
  ```
