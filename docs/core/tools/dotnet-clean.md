---
title: czyszczenie polecenia DotNet
description: Polecenia dotnet clean czyści bieżącego katalogu.
ms.date: 12/04/2018
ms.openlocfilehash: a25b7930794795e3dff5051a8ca1dd1b9c261dfd
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169862"
---
# <a name="dotnet-clean"></a>Wyczyść DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet clean` -Czyści dane wyjściowe projektu.

## <a name="synopsis"></a>Streszczenie

```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Opis

`dotnet clean` Polecenia czyści dane wyjściowe poprzednią kompilację. Jest implementowany jako [programu MSBuild](/visualstudio/msbuild/msbuild-targets), więc projekt jest oceniany, jeśli polecenie jest wykonywane. Tylko dane wyjściowe, utworzony podczas kompilacji są czyszczone. Zarówno pośredni (*obj*) i końcowych danych wyjściowych (*bin*) foldery zostały wyczyszczone.

## <a name="arguments"></a>Argumenty

`PROJECT`

Projekt programu MSBuild do czyszczenia. Jeśli nie określono pliku projektu, MSBuild przeszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* i używa tego pliku.

## <a name="options"></a>Opcje

* **`-c|--configuration {Debug|Release}`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`. Ta opcja jest tylko wymagane podczas czyszczenia, jeśli została określona w czasie kompilacji.

* **`-f|--framework <FRAMEWORK>`**

  [Framework](../../standard/frameworks.md) , która została określona w czasie kompilacji. Struktura musi być zdefiniowany w [pliku projektu](csproj.md). Jeśli struktura jest określona w czasie kompilacji, należy określić platformę, podczas czyszczenia.

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w której są umieszczane dane wyjściowe kompilacji. Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu danych wyjściowych, jeśli określona struktura podczas kompilowania projektu.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Czyści folderze wyjściowym określonym środowiska uruchomieniowego. Jest on używany podczas [niezależna wdrożenia](../deploying/index.md#self-contained-deployments-scd) został utworzony. Opcja dostępna od .NET Core 2.0 SDK.

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone poziomy są q [uiet], m [najmniej], [ormal] n, d [egółowy] i diag [Diagnostyka].

## <a name="examples"></a>Przykłady

* Czyszczenie kompilacji domyślnego projektu:

  ```console
  dotnet clean
  ```

* Wyczyść projekt, który został skompilowany przy użyciu konfiguracji wydania:

  ```console
  dotnet clean --configuration Release
  ```