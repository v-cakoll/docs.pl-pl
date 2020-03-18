---
title: dotnet msbuild, polecenie
description: Polecenie dotnet msbuild zapewnia dostęp do wiersza polecenia MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503675"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet msbuild`- Buduje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Opis

Polecenie `dotnet msbuild` umożliwia dostęp do w pełni funkcjonalnego MSBuild.

Polecenie ma dokładnie takie same możliwości jak istniejący klient wiersza polecenia MSBuild tylko dla projektów w stylu SDK. Opcje są takie same. Aby uzyskać więcej informacji na temat dostępnych opcji, zobacz [odwołanie wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Polecenie [dotnet build](dotnet-build.md) jest `dotnet msbuild -restore -target:Build`równoważne . [dotnet kompilacji](dotnet-build.md) jest powszechnie używany do tworzenia projektów, ale ponieważ zawsze `dotnet msbuild` uruchamia cel kompilacji, można użyć, gdy nie chcesz budować projekt. Na przykład jeśli masz określony cel, który chcesz uruchomić `dotnet msbuild` bez tworzenia projektu, użyj i określ miejsce docelowe.

## <a name="examples"></a>Przykłady

- Tworzenie projektu i jego zależności:

  ```dotnetcli
  dotnet msbuild
  ```

- Tworzenie projektu i jego zależności przy użyciu konfiguracji wersji:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Uruchom obiekt docelowy publikowania `osx.10.11-x64` i opublikuj dla rid:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- Zobacz cały projekt ze wszystkimi celami zawartymi w zestawie SDK:

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
