---
title: polecenie programu MSBuild programu dotnet
description: Polecenie MSBuild programu dotnet umożliwia dostęp do wiersza polecenia MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803175"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet msbuild`-Kompiluje projekt i wszystkie jego zależności. Uwaga: może być konieczne określenie rozwiązania lub pliku projektu, jeśli istnieje wiele.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a>Opis

`dotnet msbuild`Polecenie umożliwia dostęp do w pełni funkcjonalnego programu MSBuild.

Polecenie ma takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild tylko dla projektów w stylu zestawu SDK. Opcje są takie same. Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Polecenie [budowania dotnet](dotnet-build.md) jest równoważne z `dotnet msbuild -restore` . Gdy nie chcesz kompilować projektu i masz określony cel, który chcesz uruchomić, użyj `dotnet build` lub `dotnet msbuild` i określ cel.

## <a name="examples"></a>Przykłady

- Kompiluj projekt i jego zależności:

  ```dotnetcli
  dotnet msbuild
  ```

- Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Uruchom element docelowy publikowania i opublikuj go pod kątem `osx.10.11-x64` identyfikatora RID:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- Zobacz cały projekt ze wszystkimi obiektami docelowymi zawartymi w zestawie SDK:

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```
