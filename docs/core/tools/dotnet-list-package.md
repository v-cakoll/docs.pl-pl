---
title: polecenie pakiet listy dotnet
description: Polecenie "pakiet listy dotnet" zapewnia wygodną opcję listy odwołań do pakietu dla projektu lub rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: 12d64600d178ea8cf490a0d6917e67bd3d8c6d21
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463660"
---
# <a name="dotnet-list-package"></a>dotnet list package

**Ten artykuł dotyczy:** ✔️.NET Core 2.2 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet list package`- Wyświetla listę odwołań do pakietu dla projektu lub rozwiązania.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>]

dotnet list package -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet list package` zapewnia wygodną opcję, aby wyświetlić listę wszystkich odwołań do pakietu NuGet dla określonego projektu lub rozwiązania. Najpierw należy utworzyć projekt, aby mieć zasoby potrzebne do przetworzenia tego polecenia. W poniższym przykładzie `dotnet list package` przedstawiono dane wyjściowe polecenia dla projektu [SentimentAnalysis:](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

Kolumna **Requested** odnosi się do wersji pakietu określonej w pliku projektu i może być zakresem. Kolumna **Rozwiązana** zawiera listę wersji, z których obecnie korzysta projekt i która jest zawsze pojedynczą wartością. Pakiety wyświetlające `(A)` prawo obok ich nazw reprezentują odwołania do [pakietów niejawnych,](csproj.md#implicit-package-references) `<TargetFramework>` które `<TargetFrameworks>` są wywnioskowane z ustawień projektu (typ`Sdk` lub właściwość itp.)

Użyj `--outdated` tej opcji, aby dowiedzieć się, czy istnieją nowsze wersje pakietów, których używasz w projektach. Domyślnie `--outdated` wyświetla listę najnowszych pakietów stabilnych, chyba że wersja rozwiązana jest również wersją wstępną. Aby uwzględnić wersje wersji wstępnej podczas wyświetlania `--include-prerelease` nowszych wersji, należy również określić tę opcję. Poniższe przykłady pokazują dane `dotnet list package --outdated --include-prerelease` wyjściowe polecenia dla tego samego projektu, co w poprzednim przykładzie:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

Jeśli chcesz dowiedzieć się, czy projekt ma zależności `--include-transitive` przechodnie, użyj tej opcji. Zależności przechodnie występują podczas dodawania pakietu do projektu, który z kolei opiera się na innym pakiecie. Poniższy przykład przedstawia dane `dotnet list package --include-transitive` wyjściowe z uruchomienia polecenia dla projektu [HelloPlugin,](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) który wyświetla pakiety najwyższego poziomu i pakiety, od których zależą:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Plik projektu lub rozwiązania do działania. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego. Jeśli zostanie znalezione więcej niż jedno rozwiązanie lub projekt, zostanie zgłoszony błąd.

## <a name="options"></a>Opcje

- **`--config <SOURCE>`**

  Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` tej opcji.

- **`--framework <FRAMEWORK>`**

  Wyświetla tylko pakiety mające zastosowanie do określonej [struktury docelowej](../../standard/frameworks.md). Aby określić wiele struktur, powtórz tę opcję wiele razy. Na przykład: `--framework netcoreapp2.2 --framework netstandard2.0`.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--highest-minor`**

  Uwzględnia tylko pakiety z pasującym numerem wersji głównej podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` tej opcji.

- **`--highest-patch`**

  Uwzględnia tylko pakiety z pasującymi numerami wersji głównych i pomocniczych podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` tej opcji.

- **`--include-prerelease`**

  Uwzględnia pakiety z wersjami wstępnymi podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` tej opcji.

- **`--include-transitive`**

  Wyświetla listę pakietów przechodnich, oprócz pakietów najwyższego poziomu. Podczas określania tej opcji, otrzymasz listę pakietów, które zależą od pakietów najwyższego poziomu.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od .NET Core 3.0 SDK.

- **`--outdated`**

  Wyświetla listę pakietów, które mają nowsze wersje dostępne.

- **`-s|--source <SOURCE>`**

  Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów. Wymaga `--outdated` tej opcji.

## <a name="examples"></a>Przykłady

- Lista numerów numerów referencyjnych określonego projektu:

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- Lista odwołań do pakietów, które mają nowsze wersje dostępne, w tym wersje wstępnej wersji:

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- Numery do pakietu listy dla określonej struktury docelowej:

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
