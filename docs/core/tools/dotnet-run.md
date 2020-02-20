---
title: polecenie dotnet Run
description: Polecenie dotnet Run udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego.
ms.date: 02/19/2020
ms.openlocfilehash: 415d7079db6a3da80c4fcf2074307ea760e84982
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503611"
---
# <a name="dotnet-run"></a>dotnet run

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Name (Nazwa)

`dotnet run` — uruchamia kod źródłowy bez żadnych jawnych poleceń kompilacji lub uruchamiania.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] 
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] 
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet run` udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia. Jest to przydatne w przypadku szybkiego iteracyjnego programowania z poziomu wiersza polecenia. Polecenie jest zależne od polecenia [`dotnet build`](dotnet-build.md) do kompilowania kodu. Wszelkie wymagania dotyczące kompilacji, takie jak najpierw należy przywrócić projekt, należy zastosować również do `dotnet run`.

Pliki wyjściowe są zapisywane w domyślnej lokalizacji, która jest `bin/<configuration>/<target>`. Na przykład jeśli masz aplikację `netcoreapp2.1` i uruchomisz `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp2.1`. Pliki są zastępowane w razie konieczności. Pliki tymczasowe są umieszczane w katalogu `obj`.

Jeśli projekt określa wiele struktur, wykonywanie `dotnet run` powoduje błąd, chyba że zostanie użyta opcja `-f|--framework <FRAMEWORK>` do określenia struktury.

Polecenie `dotnet run` jest używane w kontekście projektów, nieskompilowanych zestawów. Jeśli próbujesz uruchomić bibliotekę DLL aplikacji zależnej od platformy, musisz użyć [dotnet](dotnet.md) bez polecenia. Na przykład aby uruchomić `myapp.dll`, użyj:

```dotnetcli
dotnet myapp.dll
```

Aby uzyskać więcej informacji na temat sterownika `dotnet`, zobacz temat [narzędzia wiersza polecenia (CLI) platformy .NET Core](index.md) .

Aby uruchomić aplikację, polecenie `dotnet run` rozwiązuje zależności aplikacji, które są poza udostępnionym środowiskiem uruchomieniowym z pamięci podręcznej NuGet. Ponieważ używa ona zależności buforowanych, nie zaleca się używania `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym. Zamiast tego [Utwórz wdrożenie](../deploying/index.md) przy użyciu [`dotnet publish`](dotnet-publish.md) polecenia i Wdróż opublikowane dane wyjściowe.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Opcje

- **`--`**

  Ogranicza argumenty do `dotnet run` z argumentów dla uruchamianej aplikacji. Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md). Struktura musi być określona w pliku projektu.

- **`--force`**

  Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania). Dostępne od wersji .NET Core 3,0 SDK.

- **`--launch-profile <NAME>`**

  Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji. Profile uruchamiania są zdefiniowane w pliku *profilu launchsettings. JSON* i są zwykle nazywane `Development`, `Staging`i `Production`. Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).

- **`--no-build`**

  Nie kompiluje projektu przed uruchomieniem. Również niejawne ustawia flagę `--no-restore`.

- **`--no-dependencies`**

  W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.

- **`--no-launch-profile`**

  Nie próbuje skonfigurować aplikacji przy użyciu pliku *profilu launchsettings. JSON* .

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

- **`-p|--project <PATH>`**

  Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka). Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). `-r` krótka opcja dostępna od wersji .NET Core 3,0 SDK.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartością domyślną jest `m`. Dostępne od wersji .NET Core 2,1 SDK. 

## <a name="examples"></a>Przykłady

- Uruchom projekt w bieżącym katalogu:

  ```dotnetcli
  dotnet run
  ```

- Uruchom określony projekt:

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- Uruchom projekt w bieżącym katalogu (`--help` argument w tym przykładzie jest przesyłany do aplikacji, ponieważ jest używana opcja pustej `--`):

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu, wyświetlając tylko minimalne dane wyjściowe, a następnie Uruchom projekt: (zestaw .NET Core SDK 2,0 i nowsze wersje):

  ```dotnetcli
  dotnet run --verbosity m
  ```
