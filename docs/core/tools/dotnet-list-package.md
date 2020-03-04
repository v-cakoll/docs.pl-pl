---
title: polecenie pakietu list dotnet
description: Polecenie "pakiet listy dotnet" udostępnia wygodną opcję wyświetlania odwołań do pakietów dla projektu lub rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: 1cb52b8de10b2eef2ef7465f04316e9446318763
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157235"
---
# <a name="dotnet-list-package"></a>dotnet list package

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,2 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet list package` — wyświetla listę odwołań do pakietu dla projektu lub rozwiązania.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch]
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet list package` udostępnia wygodną opcję wyświetlania wszystkich odwołań do pakietów NuGet dla określonego projektu lub rozwiązania. Najpierw należy skompilować projekt w celu uzyskania zasobów potrzebnych do przetworzenia tego polecenia. Poniższy przykład przedstawia dane wyjściowe polecenia `dotnet list package` dla projektu [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**Żądana** kolumna odwołuje się do wersji pakietu określonej w pliku projektu i może być zakresem. W kolumnie **rozwiązane** są wyświetlane wersje, które są obecnie używane w projekcie i zawsze jest pojedyncza wartość. Pakiety wyświetlające `(A)` bezpośrednio obok ich nazw reprezentują [niejawne odwołania do pakietów](csproj.md#implicit-package-references) , które są wywnioskowane z ustawień projektu (typ`Sdk`, `<TargetFramework>` lub właściwość `<TargetFrameworks>` itp.)

Użyj opcji `--outdated`, aby dowiedzieć się, czy są dostępne nowsze wersje pakietów używanych w projektach. Domyślnie program `--outdated` wyświetla listę najnowszych stabilnych pakietów, chyba że rozpoznana wersja to również wersja wstępna. Aby uwzględnić wersje wstępne podczas wyświetlania listy nowszych wersji, należy również określić opcję `--include-prerelease`. Poniższe przykłady przedstawiają dane wyjściowe polecenia `dotnet list package --outdated --include-prerelease` dla tego samego projektu, co w poprzednim przykładzie:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

Jeśli chcesz dowiedzieć się, czy projekt zawiera zależności przechodnie, użyj opcji `--include-transitive`. Zależności przechodnie występują po dodaniu pakietu do projektu, który z kolei jest zależny od innego pakietu. Poniższy przykład przedstawia dane wyjściowe uruchamiania `dotnet list package --include-transitive` polecenie dla projektu [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) , który wyświetla pakiety najwyższego poziomu i pakiety, od których zależą:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Plik projektu lub rozwiązania do działania. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog. Jeśli znaleziono więcej niż jedno rozwiązanie lub projekt, zostanie zgłoszony błąd.

## <a name="options"></a>Opcje

- **`--config <SOURCE>`**

  Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów. Wymaga opcji `--outdated`.

- **`--framework <FRAMEWORK>`**

  Wyświetla tylko pakiety mające zastosowanie do określonej [platformy docelowej](../../standard/frameworks.md). Aby określić wiele struktur, Powtarzaj tę opcję wiele razy. Na przykład: `--framework netcoreapp2.2 --framework netstandard2.0`.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--highest-minor`**

  Podczas wyszukiwania nowszych pakietów uwzględnia tylko te pakiety, które pasują do numeru głównego. Wymaga opcji `--outdated`.

- **`--highest-patch`**

  Podczas wyszukiwania nowszych pakietów uwzględnia tylko te pakiety, które mają pasujące główne i pomocnicze numery wersji. Wymaga opcji `--outdated`.

- **`--include-prerelease`**

  Traktuje pakiety z wersjami wstępnymi podczas wyszukiwania nowszych pakietów. Wymaga opcji `--outdated`.

- **`--include-transitive`**

  Wyświetla listę pakietów przechodnich oprócz pakietów najwyższego poziomu. Po wybraniu tej opcji otrzymujesz listę pakietów, od których zależą pakiety najwyższego poziomu.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. Dostępne od wersji .NET Core 3,0 SDK.

- **`--outdated`**

  Wyświetla listę pakietów, które mają dostępne nowsze wersje.

- **`-s|--source <SOURCE>`**

  Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów. Wymaga opcji `--outdated`.

## <a name="examples"></a>Przykłady

- Utwórz listę odwołań do pakietów dla określonego projektu:

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- Wyświetl listę odwołań do pakietów, które mają dostępne nowsze wersje, w tym wersje wstępne:

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- Utwórz listę odwołań do pakietów dla konkretnej platformy docelowej:

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
