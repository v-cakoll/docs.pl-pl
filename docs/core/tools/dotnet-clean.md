---
title: czyszczenie polecenia — .NET Core wiersz polecenia DotNet
description: Polecenia dotnet clean czyści bieżącego katalogu.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 5553e4b4423a2d824c05caf7114c47b5f1c20477
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45988338"
---
# <a name="dotnet-clean"></a>Wyczyść DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet clean` -Czyści dane wyjściowe projektu.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet clean` Polecenia czyści dane wyjściowe poprzednią kompilację. Jest implementowany jako [programu MSBuild](/visualstudio/msbuild/msbuild-targets), więc projekt jest oceniany, jeśli polecenie jest wykonywane. Tylko dane wyjściowe, utworzony podczas kompilacji są czyszczone. Zarówno pośredni (*obj*) i końcowych danych wyjściowych (*bin*) foldery zostały wyczyszczone.

## <a name="arguments"></a>Argumenty

`PROJECT`

Projekt programu MSBuild do czyszczenia. Jeśli nie określono pliku projektu, MSBuild przeszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* i używa tego pliku.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`. Ta opcja jest tylko wymagane podczas czyszczenia, jeśli została określona w czasie kompilacji.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) , która została określona w czasie kompilacji. Struktura musi być zdefiniowany w [pliku projektu](csproj.md). Jeśli struktura jest określona w czasie kompilacji, należy określić platformę, podczas czyszczenia.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w której są umieszczane dane wyjściowe kompilacji. Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu danych wyjściowych, jeśli określona struktura podczas kompilowania projektu.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Czyści folderze wyjściowym określonym środowiska uruchomieniowego. Jest on używany podczas [niezależna wdrożenia](../deploying/index.md#self-contained-deployments-scd) został utworzony.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone poziomy są q [uiet], m [najmniej], [ormal] n, d [egółowy] i diag [Diagnostyka].

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`. Ta opcja jest tylko wymagane podczas czyszczenia, jeśli została określona w czasie kompilacji.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) , która została określona w czasie kompilacji. Struktura musi być zdefiniowany w [pliku projektu](csproj.md). Jeśli struktura jest określona w czasie kompilacji, należy określić platformę, podczas czyszczenia.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w której są umieszczane dane wyjściowe kompilacji. Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu danych wyjściowych, jeśli określona struktura podczas kompilowania projektu.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone poziomy są q [uiet], m [najmniej], [ormal] n, d [egółowy] i diag [Diagnostyka].

---

## <a name="examples"></a>Przykłady

Czyszczenie kompilacji domyślnego projektu:

`dotnet clean`

Wyczyść projekt, który został skompilowany przy użyciu konfiguracji wydania:

`dotnet clean --configuration Release`
