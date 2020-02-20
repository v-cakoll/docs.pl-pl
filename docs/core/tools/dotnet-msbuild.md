---
title: polecenie programu MSBuild programu dotnet
description: Polecenie MSBuild programu dotnet umożliwia dostęp do wiersza polecenia MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503675"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Name (Nazwa)

`dotnet msbuild` — kompiluje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Opis

`dotnet msbuild` polecenie umożliwia dostęp do w pełni funkcjonalnego programu MSBuild.

Polecenie ma takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild tylko dla projektów w stylu zestawu SDK. Opcje są takie same. Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Polecenie [budowania dotnet](dotnet-build.md) jest równoważne `dotnet msbuild -restore -target:Build`. [kompilacja dotnet](dotnet-build.md) jest częściej używana do kompilowania projektów, ale ponieważ zawsze uruchamia element docelowy kompilacji, można użyć `dotnet msbuild`, gdy nie chcesz kompilować projektu. Na przykład jeśli masz konkretny cel, który chcesz uruchomić bez kompilowania projektu, użyj `dotnet msbuild` i określ element docelowy.

## <a name="examples"></a>Przykłady

- Kompiluj projekt i jego zależności:

  ```dotnetcli
  dotnet msbuild
  ```

- Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Uruchom element docelowy publikowania i Opublikuj dla `osx.10.11-x64` RID:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- Zobacz cały projekt ze wszystkimi obiektami docelowymi zawartymi w zestawie SDK:

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
