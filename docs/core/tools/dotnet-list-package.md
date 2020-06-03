---
title: polecenie pakietu list dotnet
description: Polecenie "pakiet listy dotnet" udostępnia wygodną opcję wyświetlania odwołań do pakietów dla projektu lub rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: 12d64600d178ea8cf490a0d6917e67bd3d8c6d21
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463660"
---
# <a name="dotnet-list-package"></a>dotnet list package

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,2 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet list package`-Wyświetla listę odwołań do pakietu dla projektu lub rozwiązania.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>]

dotnet list package -h|--help
```

## <a name="description"></a>Opis

`dotnet list package`Polecenie udostępnia wygodną opcję wyświetlania listy wszystkich odwołań pakietów NuGet dla określonego projektu lub rozwiązania. Najpierw należy skompilować projekt w celu uzyskania zasobów potrzebnych do przetworzenia tego polecenia. Poniższy przykład przedstawia dane wyjściowe `dotnet list package` polecenia dla projektu [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**Żądana** kolumna odwołuje się do wersji pakietu określonej w pliku projektu i może być zakresem. W kolumnie **rozwiązane** są wyświetlane wersje, które są obecnie używane w projekcie i zawsze jest pojedyncza wartość. Pakiety wyświetlające `(A)` prawo obok ich nazw reprezentują [niejawne odwołania do pakietów](csproj.md#implicit-package-references) , które są wywnioskowane z ustawień projektu ( `Sdk` Typ `<TargetFramework>` lub `<TargetFrameworks>` Właściwość itp.)

Użyj `--outdated` opcji, aby dowiedzieć się, czy są dostępne nowsze wersje pakietów używanych w projektach. Domyślnie program `--outdated` wyświetla listę najnowszych stabilnych pakietów, chyba że rozpoznana wersja stanowi również wersję wstępną. Aby uwzględnić wersje wstępne podczas wyświetlania listy nowszych wersji, należy również określić `--include-prerelease` opcję. Poniższe przykłady przedstawiają dane wyjściowe `dotnet list package --outdated --include-prerelease` polecenia dla tego samego projektu, co w poprzednim przykładzie:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

Jeśli chcesz dowiedzieć się, czy projekt zawiera zależności przechodnie, użyj `--include-transitive` opcji. Zależności przechodnie występują po dodaniu pakietu do projektu, który z kolei jest zależny od innego pakietu. Poniższy przykład przedstawia dane wyjściowe uruchamiania `dotnet list package --include-transitive` polecenia dla projektu [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) , w którym są wyświetlane pakiety najwyższego poziomu i pakiety, od których zależą:

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

  Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` opcji.

- **`--framework <FRAMEWORK>`**

  Wyświetla tylko pakiety mające zastosowanie do określonej [platformy docelowej](../../standard/frameworks.md). Aby określić wiele struktur, Powtarzaj tę opcję wiele razy. Na przykład: `--framework netcoreapp2.2 --framework netstandard2.0`.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--highest-minor`**

  Podczas wyszukiwania nowszych pakietów uwzględnia tylko te pakiety, które pasują do numeru głównego. Wymaga `--outdated` opcji.

- **`--highest-patch`**

  Podczas wyszukiwania nowszych pakietów uwzględnia tylko te pakiety, które mają pasujące główne i pomocnicze numery wersji. Wymaga `--outdated` opcji.

- **`--include-prerelease`**

  Traktuje pakiety z wersjami wstępnymi podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` opcji.

- **`--include-transitive`**

  Wyświetla listę pakietów przechodnich oprócz pakietów najwyższego poziomu. Po wybraniu tej opcji otrzymujesz listę pakietów, od których zależą pakiety najwyższego poziomu.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. Dostępne od wersji .NET Core 3,0 SDK.

- **`--outdated`**

  Wyświetla listę pakietów, które mają dostępne nowsze wersje.

- **`-s|--source <SOURCE>`**

  Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` opcji.

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
