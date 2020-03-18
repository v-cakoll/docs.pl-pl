---
title: polecenie pakietu listy dotnet
description: Polecenie "pakiet listy dotnet" zapewnia wygodną opcję wystawiania odwołań do pakietu dla projektu lub rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: 1cb52b8de10b2eef2ef7465f04316e9446318763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157235"
---
# <a name="dotnet-list-package"></a>dotnet list package

**Ten artykuł dotyczy:** ✔️ .NET Core 2.2 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet list package`- Wyświetla listę odwołań do pakietu dla projektu lub rozwiązania.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch]
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet list package` zapewnia wygodną opcję do listy wszystkich odwołań nuget pakietu dla określonego projektu lub rozwiązania. Najpierw należy utworzyć projekt, aby mieć zasoby potrzebne do przetworzenia tego polecenia. W poniższym przykładzie przedstawiono `dotnet list package` dane wyjściowe polecenia dla projektu [SentimentAnalysis:](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

Żądana **kolumna** odnosi się do wersji pakietu określonej w pliku projektu i może być zakresem. Kolumna **Rozwiązana** zawiera listę wersji, z których aktualnie korzysta projekt i zawsze jest pojedynczą wartością. Pakiety wyświetlające `(A)` prawo obok ich nazw reprezentują [niejawne odwołania do pakietów,](csproj.md#implicit-package-references) `<TargetFramework>` które `<TargetFrameworks>` są wywnioskowane z ustawień projektu (typ`Sdk` lub właściwość itp.)

Użyj `--outdated` opcji, aby dowiedzieć się, czy są dostępne nowsze wersje pakietów, których używasz w swoich projektach. Domyślnie `--outdated` wyświetla listę najnowszych stabilnych pakietów, chyba że rozwiązana wersja jest również wersją w wersji wstępnej. Aby dołączyć wersje wstępne podczas wyświetlania `--include-prerelease` nowych wersji, należy również określić tę opcję. W poniższych przykładach przedstawiono `dotnet list package --outdated --include-prerelease` dane wyjściowe polecenia dla tego samego projektu, co w poprzednim przykładzie:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

Jeśli musisz dowiedzieć się, czy projekt ma zależności przechodnie, użyj `--include-transitive` tej opcji. Zależności przechodnie występują po dodaniu pakietu do projektu, który z kolei opiera się na innym pakiecie. W poniższym przykładzie przedstawiono `dotnet list package --include-transitive` dane wyjściowe z uruchamiania polecenia dla projektu [HelloPlugin,](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) który wyświetla pakiety najwyższego poziomu i pakiety, od których zależą:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Plik projektu lub rozwiązania do działania. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego. Jeśli zostanie znalezionych więcej niż jedno rozwiązanie lub projekt, zostanie zgłoszony błąd.

## <a name="options"></a>Opcje

- **`--config <SOURCE>`**

  Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` tej opcji.

- **`--framework <FRAMEWORK>`**

  Wyświetla tylko pakiety mające zastosowanie do określonej [struktury docelowej](../../standard/frameworks.md). Aby określić wiele struktur, powtórz tę opcję wiele razy. Na przykład: `--framework netcoreapp2.2 --framework netstandard2.0`.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--highest-minor`**

  Podczas wyszukiwania nowszych pakietów uwzględnia tylko pakiety z pasującym numerem wersji głównej. Wymaga `--outdated` tej opcji.

- **`--highest-patch`**

  Podczas wyszukiwania nowszych pakietów uwzględnia tylko pakiety z pasującymi numerami wersji głównych i pomocniczych. Wymaga `--outdated` tej opcji.

- **`--include-prerelease`**

  Bierze pod uwagę pakiety z wersjami wstępnymi podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` tej opcji.

- **`--include-transitive`**

  Wyświetla listę pakietów przechodnich, oprócz pakietów najwyższego poziomu. Podczas określania tej opcji, otrzymasz listę pakietów, które pakiety najwyższego poziomu zależą od.

- **`--interactive`**

  Umożliwia zatrzymanie polecenia i oczekiwanie na wejście użytkownika lub akcję. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od sdk .NET Core 3.0.

- **`--outdated`**

  Wyświetla listę pakietów, które mają nowsze wersje dostępne.

- **`-s|--source <SOURCE>`**

  Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` tej opcji.

## <a name="examples"></a>Przykłady

- Lista odwołań do pakietu określonego projektu:

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- Lista odwołań do pakietów, które mają nowsze wersje dostępne, w tym wersje wstępne:

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- Lista odwołań do pakietów dla określonych ram docelowych:

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
