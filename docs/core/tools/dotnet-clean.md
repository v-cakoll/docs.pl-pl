---
title: czyszczenie polecenia DotNet
description: Polecenia dotnet clean czyści bieżącego katalogu.
ms.date: 04/14/2019
ms.openlocfilehash: fa19f1b041e4031082f928135395a5f06ce702e9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631821"
---
# <a name="dotnet-clean"></a>Wyczyść DotNet

**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet clean` -Czyści dane wyjściowe projektu.

## <a name="synopsis"></a>Streszczenie

```
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Opis

`dotnet clean` Polecenia czyści dane wyjściowe poprzednią kompilację. Jest implementowany jako [programu MSBuild](/visualstudio/msbuild/msbuild-targets), więc projekt jest oceniany, jeśli polecenie jest wykonywane. Tylko dane wyjściowe, utworzony podczas kompilacji są czyszczone. Zarówno pośredni (*obj*) i końcowych danych wyjściowych (*bin*) foldery zostały wyczyszczone.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Projektu programu MSBuild lub rozwiązanie do czyszczenia. Jeśli nie określono pliku projektu lub rozwiązania, MSBuild przeszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* lub *sln*oraz korzysta z tego pliku.

## <a name="options"></a>Opcje

* **`-c|--configuration {Debug|Release}`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`. Ta opcja jest tylko wymagane podczas czyszczenia, jeśli została określona w czasie kompilacji.

* **`-f|--framework <FRAMEWORK>`**

  [Framework](../../standard/frameworks.md) , która została określona w czasie kompilacji. Struktura musi być zdefiniowany w [pliku projektu](csproj.md). Jeśli struktura jest określona w czasie kompilacji, należy określić platformę, podczas czyszczenia.

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`--interactive`**

  Umożliwia polecenie, aby zatrzymać i czeka na dane wejściowe użytkownika lub akcji. Na przykład w celu ukończenia uwierzytelniania. Dostępne, ponieważ .NET Core SDK w wersji 3.0.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, który zawiera artefaktów kompilacji, aby wyczyścić. Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu danych wyjściowych, jeśli określona struktura podczas kompilowania projektu.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Czyści folderze wyjściowym określonym środowiska uruchomieniowego. Jest on używany podczas [niezależna wdrożenia](../deploying/index.md#self-contained-deployments-scd) został utworzony. Opcja dostępna od .NET Core 2.0 SDK.

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości MSBuild. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`. Wartość domyślna to `normal`.

## <a name="examples"></a>Przykłady

* Czyszczenie kompilacji domyślnego projektu:

  ```console
  dotnet clean
  ```

* Wyczyść projekt, który został skompilowany przy użyciu konfiguracji wydania:

  ```console
  dotnet clean --configuration Release
  ```
