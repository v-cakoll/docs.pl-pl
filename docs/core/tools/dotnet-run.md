---
title: polecenie dotnet run
description: Polecenie dotnet run zapewnia wygodną opcję uruchamiania aplikacji z kodu źródłowego.
ms.date: 02/19/2020
ms.openlocfilehash: e442ed56d676ffd189ef6d394d840cea671c2dc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157079"
---
# <a name="dotnet-run"></a>dotnet run

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet run`- Uruchamia kod źródłowy bez żadnych jawnych poleceń kompilacji lub uruchamiania.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile]
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project]
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet run` zapewnia wygodną opcję uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia. Jest to przydatne do szybkiego iteracyjnego rozwoju z wiersza polecenia. Polecenie zależy od [`dotnet build`](dotnet-build.md) polecenia do utworzenia kodu. Wszelkie wymagania dotyczące kompilacji, takie jak, że projekt `dotnet run` musi zostać przywrócony w pierwszej kolejności, stosuje się do, jak również.

Pliki wyjściowe są zapisywane w lokalizacji `bin/<configuration>/<target>`domyślnej, która jest . Na przykład, jeśli `netcoreapp2.1` masz aplikację `dotnet run`i uruchomisz, dane wyjściowe są umieszczane w pliku `bin/Debug/netcoreapp2.1`. Pliki są zastępowane zgodnie z potrzebami. Pliki tymczasowe są `obj` umieszczane w katalogu.

Jeśli projekt określa wiele struktur, `dotnet run` wykonywanie wyników w `-f|--framework <FRAMEWORK>` błąd, chyba że opcja jest używana do określenia struktury.

Polecenie `dotnet run` jest używane w kontekście projektów, a nie zestawy zbudowane. Jeśli próbujesz uruchomić dll aplikacji zależnej od struktury, należy użyć [dotnet](dotnet.md) bez polecenia. Na przykład, `myapp.dll`aby uruchomić , należy użyć:

```dotnetcli
dotnet myapp.dll
```

Aby uzyskać więcej `dotnet` informacji na temat sterownika, zobacz temat [.NET Core Command Line Tools (CLI).](index.md)

Aby uruchomić aplikację, `dotnet run` polecenie rozwiązuje zależności aplikacji, które znajdują się poza udostępnionym czasie wykonywania z pamięci podręcznej NuGet. Ponieważ używa buforowanych zależności, nie jest zalecane `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym. Zamiast tego należy utworzyć [`dotnet publish`](dotnet-publish.md) [wdrożenie](../deploying/index.md) przy użyciu polecenia i wdrożyć opublikowane dane wyjściowe.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Opcje

- **`--`**

  Rozgranicza `dotnet run` argumenty do argumentów dla uruchomionej aplikacji. Wszystkie argumenty po tym ograniczniku są przekazywane do uruchomienia aplikacji.

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Tworzy i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md). Struktura musi być określona w pliku projektu.

- **`--force`**

  Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie). Dostępne od sdk .NET Core 3.0.

- **`--launch-profile <NAME>`**

  Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji. Profile uruchamiania są zdefiniowane w pliku *launchSettings.json* `Development`i `Staging`są `Production`zwykle nazywane , i . Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).

- **`--no-build`**

  Nie tworzy projektu przed uruchomieniem. To również niejawne ustawia `--no-restore` flagę.

- **`--no-dependencies`**

  Podczas przywracania projektu z odwołaniami do projektu (P2P) przywraca projekt główny, a nie odwołania.

- **`--no-launch-profile`**

  Nie próbuje użyć *launchSettings.json* do skonfigurowania aplikacji.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas uruchamiania polecenia.

- **`-p|--project <PATH>`**

  Określa ścieżkę pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka). Jeśli nie zostanie określony, domyślnie jest to bieżący katalog.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy czas wykonywania, dla której ma zostać przywrócony pakiety. Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md). `-r`opcja krótka dostępna od czasu sdk .NET Core 3.0.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartością domyślną jest `m`. Dostępne od sdk .NET Core 2.1.

## <a name="examples"></a>Przykłady

- Uruchom projekt w bieżącym katalogu:

  ```dotnetcli
  dotnet run
  ```

- Uruchom określony projekt:

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- Uruchom projekt w bieżącym katalogu `--help` (argument w tym przykładzie jest przekazywany do aplikacji, ponieważ używana jest opcja puste): `--`

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu tylko z minimalnym wyjściem wyjściowym, a następnie uruchom projekt: (.NET Core SDK 2.0 i nowsze wersje):

  ```dotnetcli
  dotnet run --verbosity m
  ```
