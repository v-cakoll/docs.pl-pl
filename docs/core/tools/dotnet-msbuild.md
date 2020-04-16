---
title: dotnet msbuild, polecenie
description: Polecenie dotnet msbuild zapewnia dostęp do wiersza polecenia MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463627"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet msbuild`- Buduje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a>Opis

Polecenie `dotnet msbuild` umożliwia dostęp do w pełni funkcjonalnego msbuild.

Polecenie ma dokładnie takie same możliwości jak istniejący klient wiersza polecenia MSBuild tylko dla projektów w stylu SDK. Opcje są takie same. Aby uzyskać więcej informacji na temat dostępnych opcji, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Polecenie [dotnet build](dotnet-build.md) jest `dotnet msbuild -restore -target:Build`równoważne . [dotnet kompilacja](dotnet-build.md) jest powszechnie używany do tworzenia projektów, ale ponieważ zawsze `dotnet msbuild` uruchamia miejsce docelowe kompilacji, można użyć, gdy nie chcesz tworzyć projektu. Na przykład jeśli masz określony cel, który chcesz uruchomić `dotnet msbuild` bez tworzenia projektu, użyj i określ cel.

## <a name="examples"></a>Przykłady

- Tworzenie projektu i jego zależności:

  ```dotnetcli
  dotnet msbuild
  ```

- Tworzenie projektu i jego zależności przy użyciu konfiguracji wydania:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Uruchom cel publikowania i `osx.10.11-x64` opublikuj dla rid:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- Zobacz cały projekt ze wszystkimi celami zawartymi w SDK:

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
