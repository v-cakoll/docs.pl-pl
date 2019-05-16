---
title: polecenie pakietu listy DotNet
description: Polecenia dotnet wyświetlenia listy pakietów zapewnia wygodny sposób, aby wyświetlić listę odwołania do pakietu dla projektu lub rozwiązania.
ms.date: 04/09/2019
ms.openlocfilehash: 88ef3302a955eadc4167384312e4eb721dd496fb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631772"
---
# <a name="dotnet-list-package"></a>polecenia DotNet wyświetlenia listy pakietów

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a>Nazwa

`dotnet list package` — Wyświetla listę odwołań do pakietów dla projektu lub rozwiązania.

## <a name="synopsis"></a>Streszczenie

```
dotnet list [<PROJECT | SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Opis

`dotnet list package` Polecenie zapewnia wygodny sposób, aby wyświetlić listę wszystkich odwołań do pakietów NuGet dla określonego projektu lub rozwiązania. Należy najpierw skompilować projekt, aby mogła mieć zasoby wymagane dla tego polecenia do przetworzenia. Poniższy przykład przedstawia dane wyjściowe `dotnet list package` polecenie, aby uzyskać [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projektu:

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**Żądana** kolumna odwołuje się do wersji pakietu, określone w pliku projektu i może być zakresem. **Rozwiązane** kolumna zawiera listę wersji, że projekt jest obecnie używany i zawsze jest wartość typu single. Pakiety wyświetlanie `(A)` reprezentują obok ich nazwy [odwołania do pakietu niejawne](csproj.md#implicit-package-references) , są dedukowane z ustawień projektu (`Sdk` typu `<TargetFramework>` lub `<TargetFrameworks>` właściwości itp.)

Użyj `--outdated` opcję, aby dowiedzieć się, jeśli dostępne są nowsze wersje pakietów używane w projektach. Domyślnie `--outdated` Wyświetla listę najnowszych pakietów stabilny, chyba że rozwiązane jest także wersja wstępna wersja. Aby dołączyć wstępnej wersji, podczas wyświetlania nowszych wersji, należy także określić `--include-prerelease` opcji. Następujące przykłady przedstawiają dane wyjściowe `dotnet list package --outdated --include-prerelease` polecenia dla tego samego projektu, jak w poprzednim przykładzie:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

Jeśli musisz sprawdzić, czy projekt ma przechodnie zależności, użyj `--include-transitive` opcji. Przechodnie zależności wystąpić, gdy dodasz pakiet do projektu, która z kolei zależy od innego pakietu. Poniższy przykład przedstawia dane wyjściowe uruchamianie `dotnet list package --include-transitive` polecenie, aby uzyskać [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projektu, który wyświetla najwyższego pakiety i pakiety, są one zależne od:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Plik projektu lub rozwiązania do wykonywania operacji. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego. Jeśli więcej niż jedno rozwiązanie lub projekt zostanie znaleziony, zostanie zgłoszony błąd.

## <a name="options"></a>Opcje

* **`--config <SOURCE>`**

  Źródła NuGet do użycia podczas wyszukiwania dla nowszych pakietów. Wymaga `--outdated` opcji.

* **`--framework <FRAMEWORK>`**

  Wyświetla tylko te pakiety, które są odpowiednie dla określonego [platformę docelową](../../standard/frameworks.md). Aby określić wiele struktur, powtórz opcję wiele razy. Na przykład: `--framework netcoreapp2.2 --framework netstandard2.0`.

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`--highest-minor`**

  Uwzględnia tylko pakiety za pomocą dopasowywania główny numer wersji, podczas wyszukiwania dla nowszych pakietów. Wymaga `--outdated` opcji.

* **`--highest-patch`**

  Uwzględnia tylko pakiety z pasującą główne i pomocnicze numery wersji podczas wyszukiwania dla nowszych pakietów. Wymaga `--outdated` opcji.

* **`--include-prerelease`**

  Uwzględnia pakiety z wersji wstępnych podczas wyszukiwania dla nowszych pakietów. Wymaga `--outdated` opcji.

* **`--include-transitive`**

  Zawiera listę pakietów przechodnich, oprócz pakietów najwyższego poziomu. Gdy użycie tej opcji, masz dostęp do listy pakietów, które zależą od pakietów najwyższego poziomu.

* **`--outdated`**

  Zawiera listę pakietów, które mają nowszych wersji będą dostępne.

* **`-s|--source <SOURCE>`**

  Źródła NuGet do użycia podczas wyszukiwania dla nowszych pakietów. Wymaga `--outdated` opcji.

## <a name="examples"></a>Przykłady

* Lista odwołania do pakietu z określonego projektu:

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* Lista odwołania do pakietu, które mają nowszych wersji będą dostępne wersje wstępne w tym:

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* Wyświetl odwołania do pakietu dla określonej platformy:

  ```console
  dotnet list package --framework netcoreapp3.0
  ```
